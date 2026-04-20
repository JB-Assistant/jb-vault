# The Ultimate Hermes Guide
**Source:** [Nyk 🌱 @nyk_builderz](https://x.com/nyk_builderz/status/2044472463279710344) | 1,211 bookmarks, 33K views

> "I ran one hermes agent as researcher, writer, coder, and orchestrator for 14 days on a single claude-sonnet-4.6 profile before everything blurred into the same voice. Most operators blame the prompt when this happens, but it is not prompting and not the model - it is one agent carrying five roles on shared memory, and everyone says 'better prompts' while nobody talks about the Hermes primitive that actually fixes it: isolated profiles."

Credit to [@neoaiforecast](https://x.com/@neoaiforecast) for naming the canonical split.

---

## The Mental Model — Roles, Not Personas

**The wrong mental model:** I need one genius AI that does everything.
**The better mental model:** I need a small team with distinct roles, clear handoffs, and less context pollution.

Hermes profiles are the primitive that makes this real. They are not character skins. Each profile isolates **seven pieces of state** at once:
1. Configuration
2. Sessions
3. Memory
4. Skills
5. Personality
6. Cron state
7. Gateway state

That matters because multi-agent setups fail when everything shares the same memory and tone. Your coding agent should not inherit the defaults of your research agent. The research agent should not carry the writer's stylistic habits. Specialization becomes durable only when the state remains separated.

---

## The 4-Role Team

Four profiles, mapped to real functional work:

| Profile | Role | Specialty |
|---------|------|-----------|
| **Hermes** | Orchestrator | Plans, decomposes, routes, synthesizes. The traffic controller, not the bottleneck. |
| **Alan** | Research Specialist | Source-first, skeptical, uncertainty-aware. Protects the team from hallucinated confidence. |
| **Mira** | Narrative Architect | Clarity, structure, audience awareness. Turns validated material into communication. |
| **Turing** | Builder & Debugger | Implementation, logs, diffs, reproducibility. Cares about tests, not narrative polish. |

This split works because it mirrors real work. The orchestrator never has to be a good writer. The writer never has to debug. The engineer never has to convince anyone. Each role gets cleaner every week because its memory stays on-topic.

---

## The 7-Step Build

### Step 1 — Start from a Working Hermes
Make sure your base Hermes installation is healthy before cloning. Model provider configured, auth working, normal session usable. You clone from this base, so anything broken here breaks four times.

### Step 2 — Create the Specialist Profiles
```bash
hermes profile create alan --clone
hermes profile create mira --clone
hermes profile create turing --clone
```
`--clone` copies `config.yaml`, `.env`, and `SOUL.md` from your working base. Each new profile still gets its own isolated memory and session history.

### Step 3 — Verify on Disk and in the CLI
```bash
hermes profile list
ls ~/.hermes/profiles/
```
You should see `alan/`, `mira/`, `turing/` under `~/.hermes/profiles/`. Your main Hermes stays the orchestrator.

### Step 4 — Write a Real SOUL.md Per Role
This is the step that turns profiles into agents. Edit each `SOUL.md` to carry a durable identity: tone, default behavior, strengths, priorities, and what the agent must avoid.

**A strong split:**
- **Hermes (orchestrator):** planning, delegation, synthesis, final QA. Sounds structured and decisive.
- **Alan (research):** evidence, verification, depth, uncertainty. Sounds source-first and skeptical.
- **Mira (writer):** clarity, structure, audience. Sounds clear and audience-aware.
- **Turing (engineer):** implementation, debugging, tests, reproducibility. Sounds precise and test-oriented.

> If you only change the name and not the SOUL.md, you do not have a team — you have four clones with labels.

### Step 5 — Keep Project Context in AGENTS.md, Not SOUL.md
`SOUL.md` defines who the agent is. `AGENTS.md` defines what project it is working on **right now**. Never mix the two.

- **Project-specific context lives in AGENTS.md:** repo structure, coding conventions, workflow rules, current priorities.
- **Identity stays stable; project context rotates.**

### Step 6 — Add a Team Reference File
One shared file that documents the roster and how profiles hand off to each other. (Template at bottom of this guide.)

### Step 7 — Run Profiles Separately
Each runs in an isolated state. Alan does not inherit Mira's drafts. Turing does not inherit Alan's research sessions. The benefit only shows up if you actually use them separately.

---

## The Operator Layer — What Neo's Guide Stops At

> "If you ignore the operator layer, your team collapses into a single blurry agent within a month."

This section covers:
- **Handoff contracts** — how profiles pass work to each other
- **Memory-KPI per profile** — what each agent is responsible for remembering
- **Policy gates per role** — what each agent is allowed to do autonomously
- **The four failure modes nobody posts screenshots of**

*(Full operator runbook content was truncated in source — accessible via original X thread)*

---

## Day-30 Failures

*(Section content truncated in source — accessible via original X thread)*

---

## Copy-Paste: team-agents.md Template

*(Template content truncated in source — accessible via original X thread)*

---

**Original thread:** https://x.com/nyk_builderz/status/2044472463279710344
**Credit:** [@nyk_builderz](https://x.com/nyk_builderz) | Inspired by [@neoaiforecast](https://x.com/@neoaiforecast)
