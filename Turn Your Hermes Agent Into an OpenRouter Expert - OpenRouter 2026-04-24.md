# Turn Your Hermes Agent Into an OpenRouter Expert

**Source:** OpenRouter (@OpenRouter) — 90,281 followers, verified organization
**Date:** 2026-04-24
**Link:** https://x.com/OpenRouter/status/2047506176447783155
**Stats:** 32,719 views · 376 likes · 397 bookmarks · 31 reposts · 8 replies

---

## Full Article

If you use [Hermes](https://hermes-agent.nousresearch.com/) as your coding agent, connecting it to OpenRouter gives you a setup that improves over time rather than starting fresh every session. This guide walks you through the setup and teaches Hermes to be an OpenRouter expert.

# Why Hermes + OpenRouter

Hermes is a provider-agnostic agent framework with built-in memory, tool use, and a self-improving skills system. It learns how you work and gets better the more you use it. OpenRouter gives you access to hundreds of models across major providers through a single API with unified billing, automatic failover, and intelligent routing.

Together you have a powerful coding agent that does not depend on any one provider and gets smarter the more you use it.

The skill we'll create to teach Hermes how to build with OpenRouter also covers the OpenRouter [Agent SDK](https://openrouter.ai/docs/sdks/typescript/call-model/overview) (`@openrouter/agent`), the TypeScript toolkit for building agents on OpenRouter. Its `callModel` primitive handles multi-turn tool calling, stop conditions, streaming, state, and tool approval patterns, so you can focus on what your agent does instead of wiring the loop yourself.

Let's get them set up.

# Prerequisites

- An OpenRouter account and API key ([openrouter.ai](https://openrouter.ai))
- Python installed on your machine
- A terminal you are comfortable working in

# Step 1: Install Hermes

Follow the [Hermes Quickstart](https://hermes-agent.nousresearch.com/docs/getting-started/quickstart) to get it installed.

Then run `hermes setup` to configure your provider, API key, and model. Select OpenRouter as your provider and paste in your API key.

If you already have Hermes set up, run `hermes model` to switch to OpenRouter.

If the model you want is not in the predefined list, visit [openrouter.ai/models](https://openrouter.ai/models), click the model you want, and copy the exact model slug from the model page, not the display name. Add that slug as a custom model in Hermes.

# Step 2: Teach Hermes to be an OpenRouter expert

We're going to have Hermes build its own OpenRouter skill, leaning on referencing the docs. This way Hermes is always nudged toward looking at the current OpenRouter docs when building. The goal is to give it the principles it needs to build with OpenRouter directly within the new skill with references to docs links for specific implementation details.

Our docs index lives at https://openrouter.ai/docs/llms.txt. It is built for LLM consumption; a structured list of every docs page with descriptions. Hermes can read this once and create a skill that routes to the right docs for any OpenRouter task.

## The prompt

Paste [this prompt](https://gist.github.com/ping-Toven/2671af1cbcf1ffb1c03c311473ae683f) into Hermes:

[IMAGE: media_id 2047502495161745408]

The [prompt](https://gist.github.com/ping-Toven/2671af1cbcf1ffb1c03c311473ae683f) will have Hermes create a reusable openrouter-expert skill. Hermes will read the current OpenRouter docs index, check the supporting skill-creation guidance, and build a compact resolver skill that knows when to look up the right OpenRouter docs, when to fetch the models API, and how to choose between the OpenRouter API, SDKs, framework integrations, and the Agent SDK.

The skill is designed to keep Hermes from guessing about fast-changing details like model IDs, pricing, capabilities, SDK behavior, or docs URLs. Instead, it gives Hermes decision frameworks, routing tables, gotchas, and verification steps so future OpenRouter coding sessions start with the right current context. Hermes will read the docs index, check the supporting sources, and create the skill.

When it finishes, read the skill file at `~/.hermes/profiles/<your-profile>/skills/<category>/openrouter-expert/SKILL.md` and adjust anything that does not match your workflow. You can find the actual category with `hermes skills list` or by checking `~/.hermes/profiles/<your-profile>/skills/`. It does not need to be perfect, Hermes will refine it as you build.

## Smoke test the skill

Start a fresh Hermes session and try this:

> I want to build a small app that compares model latency and cost across providers. What should I use?

A good result should load the OpenRouter skill, check the docs index, avoid hardcoding model IDs, recommend a sensible SDK or API path, and point to relevant docs.

If Hermes gives a generic answer without checking docs, ask it to inspect the `openrouter-expert` skill it just created and strengthen the trigger description.

# What you get

After running the prompt you will have:

- Hermes connected to OpenRouter with your preferred model
- A skill that routes OpenRouter questions to the right docs
- Knowledge of the OpenRouter Agent SDK baked into the skill

Your Hermes agent is now an expert at building with OpenRouter. Time to go build!

For example, if you want to make something to help you keep up with what is happening in your state legislature, try this prompt and see what Hermes builds:

> Use OpenRouter to build a small agentic app that helps me track what is happening in my state legislature. It should fetch recent bills, summarize important changes, and let me ask follow-up questions.

---

**Media:**

![Article image](https://pbs.twimg.com/media/HGowq9TXgAAaVcj.jpg)

---

## Summary

OpenRouter published an official guide on connecting the Hermes agent framework (from Nous Research) to OpenRouter as its LLM provider. The article covers installing Hermes, configuring it to use OpenRouter via `hermes setup`, and — most importantly — creating an `openrouter-expert` skill that teaches Hermes to reference OpenRouter docs automatically. The skill is built by having Hermes read the docs index at `openrouter.ai/docs/llms.txt` (structured for LLM consumption) and creating a resolver skill with decision frameworks, routing tables, and verification steps. The guide also introduces the OpenRouter Agent SDK (`@openrouter/agent`) and its `callModel` primitive for multi-turn tool calling.

---

## Key Takeaways

1. **Provider-agnostic agent + unified API:** Hermes' self-improving skills system + OpenRouter's 500+ models with unified billing and failover = a coding agent that improves over time without provider lock-in.
2. **Docs index is LLM-optimized:** `https://openrouter.ai/docs/llms.txt` is a structured list of every docs page designed for LLM consumption — perfect for skill creation.
3. **Prompt-driven skill generation:** There's a specific prompt gist that instructs Hermes to create the `openrouter-expert` skill automatically by reading the docs index and applying skill-creation guidance.
4. **Agent SDK is first-class:** The `@openrouter/agent` TypeScript SDK has a `callModel` primitive that handles multi-turn tool calling, stop conditions, streaming, state, and tool approval patterns.
5. **Avoid hardcoding model IDs:** The skill teaches Hermes to fetch current model data via API rather than guessing IDs, pricing, or capabilities.
6. **Smoke test included:** Test the skill by asking for a latency/cost comparison app — a good response should reference docs, avoid hardcoded models, and recommend the right SDK path.
7. **Example use case:** The guide suggests building a state legislature tracker as a concrete demo — fetch bills, summarize changes, allow follow-up questions.

---

## Hermes-Related Interest

🔥 **DIRECTLY RELEVANT.** This is an official OpenRouter guide specifically about the Hermes agent framework (same name as this agent). Key relevance:

- **Skill creation workflow:** The exact prompt gist and process for creating an `openrouter-expert` skill is something we could replicate or adapt for our own Hermes instance.
- **Docs integration pattern:** The idea of using `llms.txt` as a structured docs index and building a resolver skill around it is a powerful pattern for any API-heavy work.
- **OpenRouter Agent SDK:** The `@openrouter/agent` SDK with its `callModel` primitive is worth evaluating — if we build agentic apps on OpenRouter, this could save significant wiring work.
- **Model routing:** The skill's approach to avoiding hardcoded model IDs and using live API data maps well to our multi-model workflows.
- **Prompt gist:** https://gist.github.com/ping-Toven/2671af1cbcf1ffb1c03c311473ae683f — worth reviewing to see if we should adopt the same openrouter-expert skill structure.
