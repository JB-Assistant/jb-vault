# Why Everyone Is Suddenly Building Their Own Agent Harness — Kartik (X Article)

**Source:** Kartik (@code_kartik) — eng @mem0ai, building @screenshotstdio  
**Date:** 2026-05-02  
**Link:** https://x.com/code_kartik/status/2050631735529095575

**Stats:** 911 likes · 98 reposts · 2299 bookmarks · 104,370 views · 28 replies

---

## Full Article

In February 2026, the LangChain team quietly published a result that should make every AI team rethink their roadmap. They took their open-source coding agent, deepagents-cli, from outside the Top 30 on Terminal-Bench 2.0 to the Top 5, a 13.7 point jump from 52.8% to 66.5%.

The underlying model never changed. It was GPT-5.2-Codex the entire time. They only changed the harness.

That single result captures the most important shift in applied AI right now: the model is no longer the product. The harness is.

**What's an agent harness?**

An agent harness is everything wrapping the LLM that turns it from a token generator into a working agent. The tool dispatch. The context management. The sandboxing. The planning loops. The sub-agent orchestration. The evals. The observability. The verification logic that decides when work is "done."

When Claude Code's source map briefly leaked in March, the codebase came in at roughly 513,000 lines of TypeScript. The actual model API call? A few lines. Everything else is the harness.

Mitchell Hashimoto, who coined the term in early 2026, defined it bluntly: anytime an agent makes a mistake, you engineer a solution so it never makes that mistake again. That fix lives in the harness.

**Why models are commoditizing and harnesses aren't**

Two things are happening at once.

Frontier models are converging. Tool use, long context, reasoning, structured output they all do these well now, and prices are collapsing. Cursor's Composer 2 is 10x cheaper than Opus 4.6 with comparable benchmarks. Andrej Karpathy publicly retired the term "vibe coding" in February and renamed the practice **agentic engineering**, because writing code stopped being the bottleneck.

Meanwhile, harnesses compound. Every failure becomes a permanent fix a lint rule, a hook, a sub-agent, a context pattern. That improvement applies to every future run with every future model. Model releases reset the playing field on raw intelligence. Harness investment doesn't.

The data backs this up everywhere you look. Stanford's IRIS Lab paired Claude Opus with an evolving harness and beat every hand-designed system on Terminal-Bench. Factory.ai's Droid hit state-of-the-art by beating the model labs at their own game same models, different harness. OpenAI's Frontier team shipped roughly a million lines of production code with three to seven engineers and zero hand-written code, with single agent runs working autonomously for six-plus hours. Their lead engineer's summary: "Humans steer. Agents execute." The hard problem became designing the environment, not writing the code.

**Why off-the-shelf frameworks aren't enough**

LangChain, CrewAI, AI SDK these are useful starting points, but every serious agent product has a custom harness sitting on top. **Claude Code, Cursor, Devin, Sourcegraph Amp, Factory Droid, Replit Agent, Vercel v0, Hermes Agent, OpenClaw** every one of them is opinionated, custom, and tuned to its specific domain.

The reasons are concrete. Context windows need careful management Cursor's team spends weeks tuning per-model behavior. Tools need to be designed for LLMs, not humans Replit found function calling hit ceilings around argument complexity and switched to a restricted Python DSL with a 90%+ valid call rate. Evals must be tied to your product, not generic benchmarks. Token costs matter at scale and frontier labs have a structural conflict here, because every harness optimization that uses fewer tokens hurts their unit economics.

And then there's lock-in. Building your harness on a single vendor's runtime is itself a vendor decision.

**The architecture, briefly**

A production harness has roughly seven planes: the agent loop (ReAct, plan-execute, generate-test-repair), the tool layer purpose-built for LLMs, context and memory management with progressive disclosure, sandboxed execution with permission gating, multi-agent coordination, evals and tracing, and prompt and model routing.

The pattern shared by every successful harness: trust the LLM at the reasoning layer, enforce strictly at the tool boundary.

So should you build one?

If you're prototyping, no. Use Claude Code or Cursor or Codex as-is and ship.

If you're moving to production in a single domain, customize via extension points AGENTS.md, hooks, MCP servers, sub-agent definitions. Build your eval suite *before* you write custom code.

Build your own when the math gets serious: when you see a sustained 15+ point gap between stock and custom on your evals, when per-task economics matter, when you need permissions and audit trails stock harnesses don't provide, or when your domain needs tools that just don't exist yet.

The bottom line

In 2025, every team was racing to build agents. In 2026, the teams winning are the ones investing in the scaffolding around them.

The model gives you intelligence. The harness gives you a product.

Build accordingly.

---

## Summary

Kartik argues that in 2026, the competitive moat in AI has shifted from models to "agent harnesses" — the scaffolding that wraps LLMs (tool dispatch, context management, sandboxing, planning loops, sub-agent orchestration, evals, observability). He cites LangChain's deepagents-cli jumping from outside Top 30 to Top 5 on Terminal-Bench 2.0 (52.8% → 66.5%) without changing the underlying model (GPT-5.2-Codex) — only the harness changed.

The article traces how frontier models are commoditizing (converging capabilities, collapsing prices) while harnesses compound value over time — every failure becomes a permanent fix that applies across all future models. He references Mitchell Hashimoto's definition, Stanford IRIS Lab's results, Factory.ai's Droid, and OpenAI's Frontier team shipping ~1M lines of production code with 3-7 engineers and zero hand-written code.

Key advice: prototype with off-the-shelf tools (Claude Code, Cursor, Codex), customize via extension points for production, but build your own harness only when you see a sustained 15+ point gap on your evals, when per-task economics matter, or when you need permissions/audit trails stock harnesses don't provide.

---

## Key Takeaways

1. **The model is no longer the product. The harness is.** — Claude Code's codebase is ~513K lines of TypeScript; the actual model API call is a few lines.
2. **Models commoditize; harnesses compound.** — Every failure becomes a permanent fix (lint rule, hook, sub-agent, context pattern) that improves all future runs with all future models.
3. **LangChain's deepagents-cli jumped 13.7 points (52.8% → 66.5%) on Terminal-Bench 2.0** — same model, only harness changed.
4. **Andrej Karpathy retired "vibe coding"** — renamed it "agentic engineering" because writing code stopped being the bottleneck.
5. **OpenAI Frontier team:** ~1M lines of production code, 3-7 engineers, zero hand-written code, single agent runs autonomously for 6+ hours.
6. **Production harness has ~7 planes:** agent loop, tool layer, context/memory management, sandboxed execution, multi-agent coordination, evals/tracing, prompt/model routing.
7. **Pattern:** Trust the LLM at the reasoning layer, enforce strictly at the tool boundary.
8. **When to build your own:** Sustained 15+ point gap on evals, per-task economics matter, need permissions/audit trails, or domain needs tools that don't exist yet.

---

## Hermes-Related Interest

**🔥 HIGH RELEVANCE — Directly validates the Hermes Agent approach.**

This article is essentially a manifesto for everything we're building with Hermes:

- **Hermes Agent is explicitly named** alongside Claude Code, Cursor, Devin, Factory Droid, Replit Agent, Vercel v0, OpenClaw as "opinionated, custom, and tuned to its specific domain."
- **The 7-plane harness architecture** maps directly to Hermes' design: agent loop (ReAct/plan-execute), tool layer (50+ tools), context management (4-layer memory), sandboxed execution (terminal + file tools), multi-agent coordination (delegate_task), evals/tracing (built-in), prompt/model routing (config.yaml).
- **The "15+ point gap" rule** validates our decision to build custom harnesses for TireManagerPro, OttoManagerPro, etc. rather than using off-the-shelf frameworks.
- **The OpenAI Frontier team's "Humans steer. Agents execute."** mirrors our FieldAgent AI dispatch model.
- **Mitchell Hashimoto's definition** ("anytime an agent makes a mistake, engineer a solution so it never makes that mistake again") is exactly the AGENTS.md / skill pattern we use.

**Action item:** This article should be referenced in our investor pitch / product positioning. It frames Hermes as part of the winning 2026 strategy, not just a tool.
