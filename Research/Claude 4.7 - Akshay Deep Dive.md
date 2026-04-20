# How Opus 4.7 Changes Prompting, Delegation & Session Management
**Source:** [Akshay 🚀 @akshay_pachaar](https://x.com/akshay_pachaar/status/2045910818450182526) | 40.9K views
**Date:** April 2026

> "You just upgraded to Claude Opus 4.7. Your prompts are the same. Your harness is the same. But your token bill doubled, and your code review recall dropped. What happened?"

---

## The Core Shift

Opus 4.7 is not a drop-in replacement for 4.6. It thinks differently, follows instructions more literally, spawns fewer subagents, and reasons more aggressively after every user turn.

---

## The Delegation Mindset

**The single biggest shift:** Treat Claude like a capable engineer you delegate to, not a pair programmer you guide line by line.

Every user turn in an interactive session triggers reasoning overhead. With 4.6, you could spread instructions across multiple turns without much penalty. With 4.7, that pattern inflates token usage because the model reasons deeply after each message.

**Three concrete fixes:**

1. **Specify the task upfront in the first turn** — include intent, constraints, acceptance criteria, and relevant file paths. Ambiguous prompts across many turns reduce both token efficiency and output quality.
2. **Batch your questions** — give the model enough context to keep moving without checking in.
3. **Use auto mode for trusted tasks** — for long-running work where you've already provided full context, auto mode (Shift+Tab) cuts cycle time by removing unnecessary check-ins.

Bonus: Ask Claude to play a sound when it finishes a task — it creates its own hook-based notifications.

---

## The 5 Effort Levels — xhigh Is the New Default

| Level | Use Case |
|-------|---------|
| **low** | Latency-sensitive, tightly scoped. Still outperforms Opus 4.6 at same effort. |
| **medium** | Cost-sensitive tasks, willing to trade intelligence for speed. |
| **high** | Good for concurrent sessions or budget-conscious work. |
| **xhigh** | **Default.** Sweet spot for coding and agentic tasks. |
| **max** | Genuinely hard problems. Diminishing returns. Prone to overthinking. |

> "Start at xhigh for the complex design phase, drop to high for straightforward implementation, and bump to max for a tricky debugging session."

> "Opus 4.7 respects effort levels more strictly than 4.6. If a task at low or medium feels under-thought, raise the effort instead of prompting around it."

---

## Adaptive Thinking Replaces Fixed Budgets

**If you were using `budget_tokens` on 4.6, that's gone.** Opus 4.7 uses adaptive thinking.

- **Fixed budgets:** Allocated thinking tokens upfront. Model used them whether it needed to or not.
- **Adaptive thinking:** Model decides when and how much to think at each step. Simple queries get fast responses, complex steps get deep thought, steps that don't benefit skip it entirely.

**Migration:**
```
# Old (4.6)
thinking: {type: "enabled", budget_tokens: N}

# New (4.7)
thinking: {type: "adaptive"}
```

**Steering:**
- More thinking: *"Think carefully and step-by-step before responding; this problem is harder than it looks."*
- Less thinking: *"Prioritize responding quickly rather than thinking deeply. When in doubt, respond directly."*

**At max or xhigh effort:** Set max output tokens to 64k so the model has room to think and act across subagents and tool calls.

---

## Behavior Changes That Will Bite You

### Response Length
4.7 calibrates to task complexity. Simple lookups get short answers. If you need specific length/style, state it explicitly. Positive examples beat negative "don't do this" instructions.

### Fewer Tool Calls
4.7 calls tools less often and reasons more. For more aggressive tool use: raise effort to high/xhigh, or add explicit guidance: *"Use [tool] when it would enhance your understanding."*

### Fewer Subagents
4.7 is more judicious about delegating. Spell it out:
> "Do not spawn a subagent for work you can complete directly in a single response. Spawn multiple subagents in the same turn when fanning out across items or reading multiple files."

### More Literal Instruction Following
**This is the change most likely to break existing setups.** 4.7 interprets prompts more literally, especially at lower effort. Won't silently generalize or infer requests you didn't make.

Example: *"Apply this formatting to every section, not just the first one."*

### Tone Shift
4.7 is more direct and opinionated. Less validation-forward phrasing. Fewer emoji. If your product relies on a specific voice, re-evaluate style prompts.

### Code Review — The Catch
4.7 is meaningfully better at finding bugs (11 percentage points better recall on hardest bug-finding eval). **But:**

> "If your review harness says 'only report high-severity issues,' Opus 4.7 follows that instruction more faithfully than 4.6. It may investigate thoroughly, identify bugs, then not report findings below your stated bar."

**Fix — separate finding from filtering:**
> "Report every issue you find, including ones you are uncertain about or consider low-severity. Do not filter for importance or confidence at this stage. For each finding, include your confidence level and estimated severity."

Or be concrete: *"Report any bugs that could cause incorrect behavior, a test failure, or a misleading result; only omit pure style or naming preferences."*

---

## Session Management with 1M Context

Claude Code now has a **1 million token context window.** But more context doesn't always mean better results.

### Context Rot
As context grows, attention spreads. Older, irrelevant content distracts. Model gets less intelligent as the window fills.

### 5 Options at Every Turn

| Action | When to Use |
|--------|------------|
| **Continue** | Everything in the window is still relevant. |
| **Rewind (double-Esc)** | Jump back to a previous message. Failed attempts get dropped — often better than "try X instead." Keeps useful file reads, drops failed approach. |
| **/compact** | Summarizes session and keeps going. Lossy but low-effort. Steer it: `/compact focus on the auth refactor, drop the test debugging.` |
| **/clear** | Fresh session. You write down what matters. Zero rot, full control. |
| **Subagents** | Work generating lots of intermediate output. Subagent gets its own fresh context. Only final result comes back. |

> "The mental test: will you need the tool output again, or just the conclusion? If just the conclusion, use a subagent."

### Bad Auto-Compaction
Auto-compaction fires when nearing context limit — exactly when the model is least intelligent due to context rot.

> "With 1M context, you have more time to compact proactively with a description of what matters. Don't wait for auto-compaction to kick in."

---

## Prompting Techniques That Still Matter

- **XML tags** — wrap instructions, context, examples, inputs in their own tags (`<instructions>`, `<context>`, `<input>`)
- **Give Claude a role** — even one sentence focuses behavior and tone
- **3-5 examples** in `<example>` tags, covering edge cases
- **Long-form data at top** of prompt, above your query. Queries at end can improve response quality by up to 30% on complex multi-document inputs.
- **Ground responses in quotes** — for long document tasks, ask Claude to quote relevant parts before carrying out its task

### Controlling Tool Use
4.7 calls tools less frequently by default. Raise effort or add: *"Use [tool] when it would enhance your understanding."*

Parallel tool calling is a strength. Boost to near 100% with explicit XML guidance.

### Overthinking Mitigation
At higher effort, 4.7 can overthink and inflate thinking tokens. Add:
> "When you're deciding how to approach a problem, choose an approach and commit to it. Avoid revisiting decisions unless you encounter new information that directly contradicts your reasoning."

---

## Agentic Systems: State, Safety, Multi-Window

### Multi-Context Window Workflows
Use first context window to set up a framework (write tests, create setup scripts). Use future windows to iterate on a todo list. Output in structured formats (`tests.json`, `init.sh`) so fresh contexts can pick up where the last one left off.

### State Management
Match format to data:
- **JSON** — structured data (test results, task status)
- **Freeform text** — progress notes
- **Git** — checkpoints that can be restored

### Reversibility Prompt
> "You are encouraged to take local, reversible actions like editing files or running tests, but for actions that are hard to reverse or affect shared systems, ask the user before proceeding."

### Reducing Overengineering
> "Only make changes that are directly requested or clearly necessary. A bug fix doesn't need surrounding code cleaned up."

### Minimizing Hallucinations
> "Never speculate about code you have not opened. If the user references a specific file, you MUST read the file before answering."

---

## Migration Checklist

- [ ] Replace `thinking: {type: "enabled", budget_tokens: N}` with `thinking: {type: "adaptive"}`
- [ ] Set effort to `xhigh` (new default for coding)
- [ ] Set max output tokens to 64k at xhigh or max effort
- [ ] Update code review prompts — separate finding from filtering
- [ ] Reduce user turns by front-loading context into first message
- [ ] Add explicit subagent guidance for fan-out
- [ ] Specify design preferences concretely
- [ ] Migrate away from prefilled responses (deprecated since 4.6, returns 400 on Mythos Preview)

### Computer Use
- Works up to 2576px / 3.75MP
- 1080p = best balance of performance and cost
- 720p or 1366x768 = strong lower-cost options

---

## The Bottom Line

> "Opus 4.7 rewards upfront specification and punishes incremental, multi-turn prompting. The model is more capable, more literal, and more autonomous than 4.6."
>
> "Give it a well-specified task, set effort to xhigh, and let it run. The developers who will get the most out of this model are the ones who stop guiding it step by step and start delegating like they would to a senior engineer."

**Try this today:** Take your next coding task, write a single detailed prompt with intent, constraints, and acceptance criteria, and send it in one turn at xhigh. Compare the result and token usage to your old multi-turn pattern.

---

**Credit:** [@akshay_pachaar](https://x.com/akshay_pachaar)
**Original thread:** https://x.com/akshay_pachaar/status/2045910818450182526
