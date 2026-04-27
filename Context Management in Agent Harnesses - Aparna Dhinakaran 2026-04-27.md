# Context Management in Agent Harnesses
**Source:** Aparna Dhinakaran (X: @aparnadhinak)
**Date:** 2026-04-27
**Link:** https://x.com/aparnadhinak/status/2048492731929149929
---
## Full Article
Every agent harness runs into the same limit: the context window is too small for everything the model might want to remember. As sessions grow, file reads expand, subagent calls multiply, and tool outputs pile up, the harness has to decide what stays in the working set, what gets compressed, and what gets retrieved later.

We've spent the last two years building Alyx, Arize's in-product agent, and we have hit every version of this problem. We saw sessions grow until the model lost track of the task, file reads consume half the context window with boilerplate, and tool results crowd out the actual conversation.

The important question is no longer just what goes into the prompt. It is how the harness manages context over time. The best systems do not treat the context window like a passive transcript buffer. They manage it actively: keeping high-value state close, paging through data on demand, building indexes to find what's needed (grep does this), and truncating content in a way that hints at what else can be accessed.

Pi, OpenClaw, Claude Code, and Letta all make different choices here, but they are converging on a similar underlying pattern. Context is no longer just whatever fits in the transcript. It is something the system has to manage actively. The real design question is how much of that management happens inside the harness, and how much the model is expected to do for itself.

The bet: trust the model to manage its own context
Every context management decision encodes an assumption about model behavior. The key question is whether the harness should proactively constrain context usage or rely on the model to manage that budget correctly on its own.

Large File Context Management
File reads make this concrete. When a model needs to read a file larger than what fits in context, someone has to decide what to keep. All four harnesses support offset and limit parameters for pagination.

Pi (pi-mono)
Pi reads files with a hard cap of 2,000 lines or 50KB, whichever hits first, even if the model doesn't ask for a slice. Content is head-truncated, and the tool output appends an explicit continuation nudge: [Showing lines 1-2000 of 50000. Use offset=2001 to continue.] The tool description reinforces this.
Pi's approach is harness-first: the harness protects you, then teaches the model to paginate.

OpenClaw
OpenClaw inherits Pi's read tool and its 2K line / 50KB truncation. It acts the same on normal file reads. On top of that, it layers additional caps for bootstrap files, one-time context files loaded at session start: 12,000 chars per file and 60,000 chars total. When a bootstrap file exceeds its budget, it uses a 75% head / 25% tail split.
Tool results get a separate budget: 16,000 chars or 30% of the context window, whichever is smaller. When the tail looks 'important' (errors, JSON close braces, summary keywords), it switches to head+tail mode.
OpenClaw's approach is defense in depth.

Claude Code
Claude Code applies a two-layer defense on file reads. The first gate is a 256KB byte cap checked via a stat call before the file is even opened. The second gate runs after the read: the output is token-counted against a 25,000 token budget. Both limits are remotely tunable by Anthropic via GrowthBook feature flags.
The file dedup system avoids duplicate tokens in context by returning a stub for re-reads of unchanged files.
Claude Code's approach is harness-first with remote tunability.

Letta
Letta takes a fundamentally different approach. Every uploaded file is parsed, chunked, and embedded into a vector store, so the agent gets both exact and semantic search. Three file tools: open_files, grep_files, and semantic_search_files.
When a file is 'open,' its visible content is truncated to a per-file character limit that scales with the model's context window across five tiers: 5,000 chars for 8K context up to 40,000 for 200K+. An LRU policy evicts least-recently-accessed files.
Letta's approach is memory-first.

Session Pruning
As conversations grow, every harness has to decide what to keep and what to throw away.

Pi uses compaction: LLM-powered summarization triggered by a token threshold. Walks backward, keeps most recent ~20,000 tokens, summarizes the rest. Never cuts at an orphaned tool result.

OpenClaw runs two distinct mechanisms on top of Pi's compaction. History exceeds 50% of context window -> oldest chunk dropped, staged multi-pass LLM summarization with merge step. Pre-compaction flush lets the agent persist state to memory files. Second layer: non-destructive in-memory pruning of tool results on a 5-minute cache TTL.

Claude Code manages context through pre-query optimization and LLM-powered compaction. Compaction fires around 167K tokens for a 200K model. A structured 9-section prompt for summarization. Post-compact, up to 5 recently-read files are re-attached. Pre-query pipeline: oversized tool results persisted to disk and replaced with 2KB previews.

Letta: Compaction fires at 90% of context window. Sliding window eviction starting at 30% of messages. Self-compact mode uses the agent's own model. Two-stage fallback on summarizer overflow.

Sub-agent context management
Sub-agents are generally isolated from the parent session. None copies the full parent conversation into the child.
- Pi: new process per task, child receives task string only
- OpenClaw: fresh isolated sessions by default, fork mode exists for same-agent spawns, minimal workspace context allowlist
- Claude Code: default typed-agent path creates blank conversation; newer fork path passes entire parent message history for prompt cache sharing
- Letta: does not fork, tools run within main agent loop, historical context via search tools

Where the designs converge
All four harnesses: hard-cap file reads, support offset/limit pagination, cap tool result sizes, isolate sub-agent sessions, run LLM-powered compaction triggered by token threshold, estimate context usage and detect pressure.

The convergence runs deeper: Pi and OpenClaw both head-truncate and append continuation nudges. Claude Code and OpenClaw both persist oversized tool results to disk. Three of four enforce tool-call/result boundary safety during compaction.

Arize's own Alyx assistant independently arrived at the same designs for data exploration.

50 years of computing taught us that the best memory management is the kind the program never thinks about. Agent harnesses are moving in the same direction. The goal is not to show the model everything. It is to give it the right working set at the right time and allow it to dynamically make decisions to manage its own context.
---
## Summary
Aparna Dhinakaran provides a deep dive into the evolving strategies for context management within leading agent harnesses like Pi, OpenClaw, Claude Code, and Letta. The article argues that the context window should no longer be viewed as a passive buffer, but as a limited resource that requires active management by the harness. This includes strategies for handling large file reads through pagination, truncation, and semantic search, as well as session pruning techniques like LLM-powered compaction and staged summarization.

The core design challenge lies in balancing how much management is handled by the harness versus the model itself. While different architectures take varying approaches—from Pi's hard-capped safeguards to Letta's memory-first vector store approach—there is a clear convergence toward automated memory management. This includes common practices like capping tool results, isolating sub-agent sessions, and using token thresholds to trigger cleanup, ultimately aiming for a "working set" that allows models to operate efficiently without losing track of their tasks.

---
## Key Takeaways
1. **Active Management:** Context windows shouldn't be passive transcripts; they require active intervention to ensure high-value state remains accessible.
2. **File Pagination Converge:** Leading harnesses (Pi, OpenClaw, Claude Code, Letta) all use offset/limit parameters to manage file reads that exceed context limits.
3. **Compaction Strategies:** LLM-powered summarization (triggered by token thresholds) is the standard method for preventing session overflow.
4. **Tool Result Capping:** Oversized tool outputs are a major source of context bloat; systems now persist these to disk or use previews and TTL caches to mitigate the impact.
5. **Sub-agent Isolation:** To prevent prompt injection or irrelevance, sub-agents typically start with fresh sessions or minimal, filtered context from the parent.
6. **Hardware/Software Analogy:** Agent memory management is evolving much like traditional computing memory management, moving toward abstraction where the "program" (model) doesn't have to manual manage it.

---
## Hermes-Related Interest
This article is highly relevant to the development and optimization of Hermes-based agents. It highlights specific thresholds (e.g., 2K line caps, 25K token read budgets) and techniques (head+tail truncation, continuation nudges) that can be directly applied to Hermes's own "harness" and tool-calling implementation. The discussion of sub-agent context isolation is particularly critical for complex automation workflows to ensure multi-step stability and performance.

---
## Related Notes
- [[How to Build a One-Person Services-as-Software Company - Alex Vacca - 2026-04-27]]
- [[The Anatomy of a Perfect Skill - darkzodchi 2026-04-27]]
- [[Skill Writing Guide - Hermes]]
- [[How to Make 1000 per Hour Selling AI Audits - Corey Ganim 2026-04-27]]