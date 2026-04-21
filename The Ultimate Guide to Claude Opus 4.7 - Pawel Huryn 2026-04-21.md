# The Ultimate Guide to Claude Opus 4.7

**Source:** Paweł Huryn (@PawelHuryn) — Product Compass newsletter  
**Date:** 2026-04-21  
**Link:** https://x.com/PawelHuryn/status/2046197132105769065

---

## Full Article

*The ten moves to make your 4.6 prompts work on 4.7, leading with context, and why you don't need more instructions.*

4.6 guessed. 4.7 stopped guessing. Your old prompts still work, mostly. The ones that break need one of the ten moves below.

Anthropic shipped Claude Opus 4.7 on April 16. The official migration guide puts it plainly: 4.7 "takes the instructions literally" and "will not silently generalize."

It's not a uniform upgrade. Wins on coding, creative writing, and structured work. Losses on instruction following in vague prompts, multi-turn, and long-context retrieval. The benchmarks show a trade, not a regression. I sort real regressions from preference artifacts and cost mechanics in § 6.

> Boris Cherny, Claude Code lead at Anthropic, posted on release day: "It took a few days for me to learn how to work with it effectively."

## Why Read This, and Why Now

Reddit calls 4.7 a regression. Arena shows 4.6 winning on instruction following. Anthropic's migration guide says it's working as designed. Boris confirms it's more agentic and precise.

The takes don't agree because they're measuring different workflows.

I've had 16+ hours with 4.7 so far. By the end you'll know what's new, the ten moves to make your 4.6 prompts work on 4.7, and why you don't need more instructions.

## 1. What's New in Opus 4.7

4.6 filled the gaps when your instruction was unclear. 4.7 takes you at your word.

**For PMs:** if your 4.6 workflow relied on the model "figuring out what you meant," expect 4.7 to ask more questions, or to do less, or to do exactly what you asked for (which is not what you wanted).

## 2. Intent: The Universal Unlock

This is the principle: **4.7 rewards clear intent.** Everything else in this post is a tactic.

Not longer prompts, not more rules, not a bigger CLAUDE.md. Intent splits into two layers:

- **Strategic context is durable:** what you're building, who it's for, what's off-limits, what good looks like. Write it once. Put it in CLAUDE.md. It loads every session, progressive-disclosure style, so you're not paying to reintroduce the project on turn one.
- **Per-task intent is variable:** what specifically do I want Claude to do right now. You still write this every turn. The gain from CLAUDE.md is that you stop retyping the strategic context on top of it.

> Treat Claude as a partner. Help it understand what and why you're doing, your strategy, objectives, and success criteria. Strategic context — not micromanaging the agent.

The full version (seven components, how they compose) is in *The Intent Engineering Framework for AI Agents*, published three months before 4.7 shipped.

This approach is aligned with Karpathy's claude coding post, too:

> "LLMs are exceptionally good at looping until they meet specific goals and this is where most of the 'feel the AGI' magic is to be found. Don't tell it what to do, give it success criteria and watch it go (...) Change your approach from imperative to declarative to get the agents looping longer and gain leverage."

### 2.1 Anthropic and OpenAI convergence

Anthropic moved Opus 4.7 toward more literal instruction following. OpenAI updated their December 2025 Model Spec to say "consider not just the literal wording but the underlying intent."

They're converging from opposite directions. Anthropic is adding precision to its intent-first model. OpenAI is adding intent inference to its precision-first model. The same skill (engineering intent clearly) is becoming the unlock on both sides.

### 2.2 And Anthropic is already encoding it

Managed Agents (research preview) bakes success criteria and outcomes into the framework itself.

The skill of engineering clear intent is what transfers across vendors and models. That's why it has the longest shelf life right now.

## 3. The 10 Claude Opus 4.7 Migration Moves

### 3.1 Front-load intent in CLAUDE.md
You don't have to retype the strategic context every session. Put it in CLAUDE.md once. Every future session starts with the context already loaded. You still write per-task intent each turn, but you stop paying the "remember what we're building" tax.

Delegate information the agent doesn't have to read every session to other files, like strategy.md.

### 3.2 Default to Extra high (xhigh)
New effort level between high and max. Anthropic's own recommendation for coding and agentic work.

`max` is prone to overthinking. Most "4.7 feels slow" reports trace back to people running max by reflex. Use max only when the problem actually needs deep reasoning.

### 3.3 Toggle effort mid-task
Effort is per-call, not per-session. max for the hard subproblem. Drop back to high for the rest.

### 3.4 Regression-test old prompts
New tokenizer. **1.0 to 1.35× more tokens per input.** Your 4.6 workflows cost more on 4.7 before you've changed a line.

The offset to know about: Anthropic raised rate limits alongside the 4.7 launch.

My perspective: what matters most is **cost per correct output token.** Test it for your specific product before switching the model.

### 3.5 Batch questions. Stop drip-feeding.
If you have three questions, ask all three in one message.

On 4.6, clarifying across 3-4 turns worked. On 4.7, each turn adds reasoning overhead on top of literal interpretations from earlier turns.

Treat clarification as an exception, not a workflow.

### 3.6 Show what you want
Positive examples beat negative rules. According to Anthropic:

- "Like this: " followed by short examples works.
- "Don't do this: " rarely lands and burns tokens trying.

If your prompt has more than three "don't" or "never" lines, flip them. What does the ideal output look like? Show two examples and cut the rules.

### 3.7 Delete old progress scaffolding
"Summarize every 3 tool calls." "Give me a status update before moving on." "Explain your plan, then execute." **Delete these.**

Opus 4.7 emits high-quality progress updates natively in long agentic traces.

### 3.8 Tell it to fan out explicitly
Opus 4.7 spawns fewer subagents by default and makes fewer tool calls per task. For parallel exploration, you now have to ask.

Phrasings that work: "spawn subagents in the same turn to investigate X, Y, Z." Autonomy went up. Default delegation went down.

### 3.9 Review plans, not diffs
Two different primitives. Don't confuse them.

- **Plan mode** (Shift+Tab twice in the Claude Code CLI): inline, surfaces the plan before any code exists in the current session. Use for any change that touches more than one file.
- **/ultraplan** (CLI only, doesn't work in VS Code extension): cloud-based plan drafting from the CLI, review in the browser.

Why this matters more on 4.7: because 4.7 takes intent literally, a small misread in the plan becomes a large misread in the diff. Reviewing a 10-line plan for intent drift takes 30 seconds. Reviewing a 200-line diff for the same drift takes 15 minutes.

**Intent drift compounds. Catch it in the plan.**

### 3.10 Adaptive thinking only
Fixed thinking budgets are gone. Use `thinking: {type: 'adaptive'}` plus the effort parameter. Old API calls with `budget_tokens` return HTTP 400. Find and replace before flipping the model flag.

If you're not an engineer, just give your agent this documentation: https://platform.claude.com/docs/en/build-with-claude/adaptive-thinking.md

## 4. Closing

**4.6 felt smart. 4.7 is honest.** What looks like less intelligence is 4.7 refusing to guess.

Your leverage is clear intent. Not reviewing every line of code, writing endless instructions, or retyping the same context every session. The more of your intent and expectations you push up to CLAUDE.md, the less you pay (in money and attention) to run the thing.

---

## Summary

Paweł Huryn argues Claude Opus 4.7 (shipped April 16, 2026) isn't a regression — it's a deliberate shift from "filling in gaps" (4.6) to "taking you at your word" (4.7). Old vague prompts break because 4.7 refuses to silently generalize. The universal unlock is **clear intent**, split into durable strategic context (put it in CLAUDE.md once) and per-task intent (written each turn). Huryn lays out ten specific migration moves — from defaulting to the new `xhigh` effort level, to batching questions instead of drip-feeding, to explicitly asking for subagent fan-out, to reviewing plans not diffs.

The deeper framing: Anthropic and OpenAI are converging on "intent engineering" as the transferable skill. 4.7 costs 1.0–1.35× more tokens per input (new tokenizer) but offers higher output quality when intent is clear. The real metric is **cost per correct output token.**

---

## Key Takeaways

1. **4.7 is literal-minded by design** — if 4.6 guessed your meaning, 4.7 will either ask or do exactly what you said (which may not be what you wanted).
2. **Split intent into two layers:** strategic (CLAUDE.md, written once) + per-task (each turn). Stop retyping context.
3. **Default to `xhigh` effort, not `max`** — most "4.7 feels slow" reports are users reflexively running max.
4. **Batch questions instead of clarifying across 3-4 turns** — multi-turn now adds reasoning overhead on top of literal interpretations.
5. **Show examples, don't list rules** — "Like this:" with 2 examples beats 5 "don't" lines.
6. **Delete old scaffolding** like "summarize every 3 tool calls" — 4.7 emits progress natively.
7. **Ask explicitly for parallel subagent fan-out** — default delegation went down.
8. **Review plans (10 lines, 30s) not diffs (200 lines, 15min)** — intent drift compounds when 4.7 takes prompts literally.
9. **New tokenizer = 1.0–1.35× more tokens per input.** Regression-test cost-per-correct-output-token before switching.
10. **Adaptive thinking is mandatory** — old `budget_tokens` returns HTTP 400.

---

## Hermes-Related Interest

**Highly relevant — direct application to multi-agent work:**

- **CLAUDE.md pattern ↔ JB Vault 4-layer memory:** Huryn's "strategic context in CLAUDE.md, loaded every session" is *exactly* the Layer 2 (Agents.md/Soul.md) pattern Junaid and Hermes use. This validates the architecture — durable strategic context separated from per-task intent. The Hermes memory tool already does this (user profile = strategic; session = per-task).
- **"Tell it to fan out explicitly" ↔ Hermes multi-agent team skill:** 4.7 spawns fewer subagents by default. Junaid's FieldAgent AI (6 parallel agents) and Hermes `delegate_task` workflows need explicit fan-out language now. Consider updating the `hermes-multi-agent-team` skill to include fan-out phrasings.
- **"Review plans, not diffs" ↔ `plan` skill + `writing-plans` skill:** Hermes already has plan-mode skills. Huryn's 30s-vs-15min argument is a strong justification for defaulting to plan-first on any multi-file change.
- **Delete progress scaffolding:** Hermes system prompts often have "checkpoint every 3-5 calls" — on 4.7 this may be redundant and actively costs tokens. Worth testing whether to trim.
- **Cost per correct output token:** For Junaid's SaaS products (OttoManagerPro, TireManagerPro) that call Claude API in production — the 1.35× tokenizer hit matters for unit economics. Worth auditing prompts before upgrading production workloads to 4.7.
- **Karpathy alignment:** "Don't tell it what to do, give it success criteria and watch it go." Declarative > imperative. This is the same principle behind well-structured Hermes skills.

**Action items for the JB platform:**
1. Audit CLAUDE.md files across OttoManagerPro / TireManagerPro / CleanBuddyPro / FieldAgent AI for strategic-vs-per-task split.
2. Test 4.7 on a real shop-management prompt and measure cost-per-correct-output.
3. Update FieldAgent AI dispatch prompts with explicit "spawn subagents in parallel" phrasing.
