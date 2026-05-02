# How to Build a Multi-Agent Team in Hermes

**Author:** Neo (@NeoAIForecast)  
**Source:** X/Twitter Note Article  
**Date:** April 12, 2026  
**URL:** https://x.com/NeoAIForecast/status/2043455838459920718  
**Tags:** #hermes #multi-agent #workflow #profiles

---

## Summary

Hermes profiles are isolation units, not cosmetic personas. The path to a more powerful setup isn't better prompting — it's building a real team with distinct roles, clean handoffs, and separated state. The article lays out a 4-role team structure (orchestrator, research, writer, builder), explains how SOUL.md shapes identity vs AGENTS.md for project context, and gives step-by-step CLI commands for setting it up. Gateway/messaging turns profiles from a local feature into a live multi-agent control surface.

---

## Key Takeaways

1. **Single generalist agents blur over time.** Context gets messy, memory becomes noisy, workflows stop being deliberate. Isolation prevents this.

2. **Profiles separate: memory, sessions, skills, personality, cron state, gateway state.** Each can specialize without contaminating the others.

3. **SOUL.md = identity. AGENTS.md = shared project context.** Don't mix them. SOUL.md defines who the agent is; AGENTS.md defines what they're working on.

4. **4-role team pattern:** Hermes (orchestrator/planning), Alan (research/sourcing), Mira (writer/communication), Turing (builder/debugger). Mirrors real functional org structure.

5. **Messaging + profiles = live control surface.** Run different profiles as different Telegram identities, route work, supervise remotely — not locked in one terminal.

6. **Start with one specialist, prove the handoff, expand.** The smartest team is not the biggest — it's the one with the clearest role boundaries.

---

## Article Text

*Source: X Note Article by Neo (@NeoAIForecast)*

### Most people use one AI assistant and then try to force it to become a researcher, writer, coder, project manager, and operator all at once.

That usually works for a while. Then the personalities blur together. The context gets messy. The memory becomes noisy. The workflows stop feeling deliberate. Hermes gives you a better path: build a team instead of overloading a single generalist.

Hermes profiles are one of the most underrated features in the whole system. They are not just cosmetic personas. They are isolated agent environments that can separate memory, sessions, skills, personality, configuration, cron state, and gateway behavior.

That means you are not merely renaming one assistant four times. You are creating role-based agents with cleaner boundaries and more durable specialization.

**Takeaway: the leap from one agent to a real multi-agent team starts with isolation, not with better prompting.**

### The right mental model

The wrong mental model is: "I need one genius AI that does everything."

The better mental model is: "I need a small team with distinct roles, clear handoffs, and less context pollution."

That is exactly what Hermes profiles make possible. One profile can think like a strategist. Another can stay research-first. Another can optimize for communication. Another can live in implementation and debugging mode. Because their memory, sessions, and identity stay separate, each one can become more coherent over time instead of turning into a confused blend.

**Takeaway: Hermes profiles are best understood as role boundaries for AI work, not as novelty character skins.**

### What profiles actually separate

A profile can isolate: configuration, sessions, memory, skills, personality, cron state, gateway state. That matters because multi-agent systems fail when everything shares the same memory and tone. You do not want your coding agent inheriting the same defaults, priorities, and stylistic habits as your research or writing agent. You want clean lines between them.

**Takeaway: specialization only becomes durable when state stays separated.**

### The simplest team structure

Hermes > orchestrator  
Alan > research specialist  
Mira > narrative architect  
Turing > debugger and systems engineer

This is a strong pattern because it mirrors real work. The orchestrator handles planning, decomposition, sequencing, and final synthesis. The research agent gathers sources, validates claims, and turns raw information into decision-ready findings. The writer turns validated material into clear, structured communication. The engineer turns plans into working systems, tests, fixes, and reliable output.

**Takeaway: most useful AI teams map to real functional roles, not arbitrary personalities.**

### Role 1: The orchestrator

Your orchestrator profile is the command center. Its job is not to do every task personally. Its job is to define the goal, split the work, route tasks to the right specialists, and synthesize the final result. This profile should optimize for: planning, prioritization, dependency management, quality control, synthesis. It should think in workstreams, not just answers.

**Takeaway: the orchestrator is the traffic controller of the system, not the bottleneck.**

### Role 2: The research specialist

A research profile should feel skeptical, source-first, and structured. Its purpose is to gather evidence, compare sources, flag uncertainty, and separate what is verified from what is merely plausible. This is the profile you want for literature review, market research, product comparisons, source verification, trend tracking. The point is not just "good research." The point is protecting the rest of the team from bad assumptions.

**Takeaway: a good research agent reduces hallucinated confidence across the whole system.**

### Role 3: The writer

A writing profile should optimize for clarity, structure, readability, and audience awareness. This is where you turn raw findings into articles, briefings, product copy, threads, scripts, explainers. The writer should not need to hold the entire research process or implementation context in its head all the time. It should receive cleaner inputs and focus on communication quality.

**Takeaway: writing gets better when the agent is not also trying to be the researcher and debugger at the same time.**

### Role 4: The builder/debugger

Your engineering profile should be direct, evidence-driven, and implementation-focused. This is the profile for building features, debugging failures, reviewing code, validating fixes, running tests, operational problem-solving. This profile should care about reproducibility, logs, diffs, and verified outcomes more than broad narrative polish.

**Takeaway: implementation quality improves when one profile is allowed to stay deeply technical.**

### Use SOUL.md to make each role real

One of the easiest mistakes in multi-agent setups is changing only the name. If every profile has the same underlying voice, priorities, and operating style, you do not have a real team. You have clones with labels. Hermes gives you a stronger foundation through SOUL.md, which defines who the agent is and how it behaves. That is where you shape each profile's default identity.

For example: the orchestrator should sound structured and decisive; the researcher should sound evidence-first and skeptical; the writer should sound clear and audience-aware; the engineer should sound precise and test-oriented.

Then use AGENTS.md for project-specific context rather than identity.

**Takeaway: SOUL.md creates distinct agents; AGENTS.md gives them shared mission context.**

### The actual setup, step by step

**Step 1: Start from a working Hermes setup**

Before creating specialist agents, make sure your main Hermes setup already works. That means: your model/provider is configured, your API keys or auth are already working, your normal Hermes environment is usable. This matters because the easiest way to build a team is to clone from a working setup.

**Takeaway: start from a working base so you do not have to configure every agent from scratch.**

**Step 2: Create the specialist profiles**

Create each new profile by cloning the current working one:

```
hermes profile create alan --clone
hermes profile create mira --clone
hermes profile create turing --clone
```

Using --clone copies the useful base setup: config.yaml, .env, SOUL.md. But each new profile still gets its own isolated memory and session history.

**Takeaway: use --clone when you want specialized agents that inherit your working setup without sharing the same internal state.**

**Step 3: Verify that the profiles exist**

```
hermes profile list
```

On disk, they live under `~/.hermes/profiles/<name>/`. Your main Hermes profile can remain the orchestrator while the others act as specialists.

**Step 4: Give each profile a real identity with SOUL.md**

```
~/.hermes/profiles/alan/SOUL.md
~/.hermes/profiles/mira/SOUL.md
~/.hermes/profiles/turing/SOUL.md
```

Use SOUL.md to define durable identity: tone, default behavior, strengths, priorities, what the agent should avoid.

**Step 5: Keep shared context separate from identity**

Once each profile has a distinct identity, keep shared operating context in project-level files such as AGENTS.md. Use that for repository structure, coding conventions, workflow rules, tool usage expectations, project-specific instructions. Do not overload SOUL.md with temporary project details.

**Takeaway: stable teams need stable identities and shared context, not one giant mixed instruction blob.**

**Step 6: Add a shared team reference file**

Maintain one shared reference file that documents the roster and how the agents work together. For example `~/.hermes/team-agents.md`. This file can describe each agent's role, handoff rules, when to use which profile, what good output looks like from each one.

**Step 7: Run each profile directly**

```
hermes -p alan
hermes -p mira
hermes -p turing
```

Each one runs as its own profile with isolated state. Alan does not inherit Mira's writing sessions. Turing does not inherit Alan's research memory. Each agent gets cleaner long-term specialization.

**Takeaway: the benefit comes from actually using the profiles separately, not just creating them once.**

### Pair profiles with messaging

Profiles get even more powerful when you combine them with the Hermes gateway. Now your team is not locked inside one local terminal session. You can run different profiles as different messaging identities, supervise them remotely, route work through Telegram, and keep role boundaries intact across chats and tasks.

**Takeaway: messaging turns profiles from a local organization feature into a live multi-agent control surface.**

### Conclusion

If you want Hermes to feel more powerful, stop trying to make one agent do everything. Build a team. Start with an orchestrator, add one specialist, prove the handoff, and only then expand. That is where Hermes profiles stop feeling like a feature and start feeling like infrastructure.

**The smartest multi-agent team is not the biggest one. It is the one with the clearest role boundaries.**
