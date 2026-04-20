# 10 Moves to Make Your 4.6 Prompts Work on 4.7
**Source:** [Paweł Huryn @PawelHuryn](https://x.com/PawelHuryn/status/2046197132105769065) | 3.7K views
**Date:** April 2026

> "4.6 guessed. 4.7 stopped guessing. Your old prompts still work, mostly. The ones that break need one of the ten moves below."

---

## The Core Shift

**4.6:** Filled the gaps when your instruction was unclear.
**4.7:** Takes you at your word.

> "For PMs: if your 4.6 workflow relied on the model 'figuring out what you meant,' expect 4.7 to ask more questions, or to do less, or to do exactly what you asked for (which is not what you want)."

---

## The Universal Unlock: Intent

Everything else in this post is a tactic. **Intent** is the principle.

**Strategic context** (durable): What you're building, who's it for, what's off-limits, what good looks like. Write it once in CLAUDE.md. Loads every session, progressive-disclosure style.

**Per-task intent** (variable): What specifically you want Claude to do right now. Written every turn.

> "Don't tell it what to do, give it success criteria and watch it go. Change your approach from imperative to declarative to get the agents looping longer and gain leverage." — Karpathy

---

## The 10 Migration Moves

### 3.1 — Front-Load Intent in CLAUDE.md
Put strategic context in CLAUDE.md once. Stop retyping it every session. Delegate secondary details to `strategy.md`.

### 3.2 — Default to Extra High (xhigh)
New effort level between `high` and `max`. Anthropic's own recommendation for coding and agentic work.

> "max is prone to overthinking. Most '4.7 feels slow' reports trace back to people running max by reflex. Use max only when the problem actually needs deep reasoning."

### 3.3 — Toggle Effort Mid-Task
Effort is per-call, not per-session. `max` for the hard subproblem. Drop back to `high` for the rest.

### 3.4 — Regression-Test Old Prompts
New tokenizer: 1.0 to 1.35× more tokens per input. Your 4.6 workflows cost more on 4.7 before you've changed a line.

Note: Anthropic raised rate limits alongside the 4.7 launch. Test cost-per-correct-output-token for your specific use case.

### 3.5 — Batch Questions. Stop Drip-Feeding.
3 questions → ask all 3 in one message.

> "On 4.6, clarifying across 3-4 turns worked. On 4.7, each turn adds reasoning overhead on top of literal interpretations from earlier turns."

Treat clarification as an exception, not a workflow.

### 3.6 — Show What You Want
Positive examples beat negative rules.

- `"Like this: "` + short examples → works
- `"Don't do this: "` → rarely lands, burns tokens

> "If your prompt has more than three 'don't' or 'never' lines, flip them. What does the ideal output look like? Show two examples and cut the rules."

### 3.7 — Delete Old Progress Scaffolding
Delete:
- "Summarize every 3 tool calls."
- "Give me a status update before moving on."
- "Explain your plan, then execute."

Opus 4.7 emits high-quality progress updates natively in long agentic traces.

### 3.8 — Tell It to Fan Out Explicitly
Opus 4.7 spawns fewer subagents by default and makes fewer tool calls per task. For parallel exploration, you now have to ask.

Phrasing that works: **"spawn subagents in the same turn to investigate X, Y, Z."**

Autonomy went up. Default delegation went down.

### 3.9 — Review Plans, Not Diffs
Two different primitives. Don't confuse them.

**Plan mode** (Shift+Tab twice in Claude Code CLI): Surfaces the plan before any code exists. Use for any change touching more than one file.

**Why this matters more on 4.7:** Small misread in the plan → large misread in the diff. Reviewing a 10-line plan for intent drift takes 30 seconds. Reviewing a 200-line diff for the same drift takes 15 minutes.

> "Intent drift compounds. Catch it in the plan."

### 3.10 — Adaptive Thinking Only
Fixed thinking budgets are gone. Use `thinking: {type: 'adaptive'}` plus the effort parameter.

Old API calls with `budget_tokens` return HTTP 400. Find and replace before flipping the model flag.

---

## Key Insight

> "4.6 felt smart. 4.7 is honest. What looks like less intelligence is 4.7 refusing to guess."

**Your leverage is clear intent.** Not reviewing every line of code, writing endless instructions, or retyping the same context every session. The more of your intent and expectations you push up to CLAUDE.md, the less you pay (in money and attention) to run the thing.

---

**Credit:** [@PawelHuryn](https://x.com/PawelHuryn)
**Original thread:** https://x.com/PawelHuryn/status/2046197132105769065
