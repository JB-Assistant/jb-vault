# The Ultimate Hermes Guide
**Source:** [Nyk 🌱 @nyk_builderz](https://x.com/nyk_builderz/status/2044472463279710344) | 1,227 bookmarks, 34.5K views
**Date:** April 15, 2026

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

Credit to @neoaiforecast for naming the canonical split. Four profiles, mapped to real functional work:

| Profile | Role | Specialty |
|---------|------|-----------|
| **Hermes** | Orchestrator | Plans, decomposes, routes, synthesizes. The traffic controller, not the bottleneck. |
| **Alan** | Research Specialist | Source-first, skeptical, uncertainty-aware. Protects the team from hallucinated confidence. |
| **Mira** | Narrative Architect | Clarity, structure, audience awareness. Turns validated material into communication. |
| **Turing** | Builder & Debugger | Implementation, logs, diffs, reproducibility. Cares about tests, not narrative polish. |

This split works because it mirrors real work. The orchestrator never has to be a good writer. The writer never has to debug. The engineer never has to convince anyone. Each role gets cleaner every week because its memory stays on-topic.

---

## The 7-Step Build

The table-stakes sequence. If you have already run this from @neoaiforecast's post, skip to the operator layer.

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
One shared file that documents the roster and how profiles hand off to each other. Template at the bottom of this guide.

### Step 7 — Run Profiles Separately
Each runs in an isolated state. Alan does not inherit Mira's drafts. Turing does not inherit Alan's research sessions. The benefit only shows up if you actually use them separately.

---

## The Operator Layer — What Neo's Guide Stops At

This is where the guide stops being a setup post and starts being an ops runbook. Most multi-agent teams look great on day one and feel blurry by day 30. The operator layer is the difference.

### Handoff Contracts Between Profiles

Profiles specialize, which means they also have to hand work off cleanly. A handoff without a contract becomes "Alan dumped 40kb of raw research into Mira's session, and now Mira is also a researcher again."

**A handoff contract is one file per role pair, stored at `~/.hermes/team/handoffs/` with four fields:**

1. **Input shape** — what the receiving profile expects (e.g., Alan → Mira: A ranked list of validated claims with source URLs, not raw excerpts)
2. **Output shape** — what the receiving profile will return (Mira → Hermes: A drafted section with a change log, not a finished article)
3. **Failure action** — what happens if the input is malformed (block, require-human-review, retry with adjusted prompt)
4. **Verification gate** — one assertion that must be true before the handoff completes (for Alan → Mira: every claim carries a source URL; for Turing → Hermes: every fix has a passing test)

With handoff contracts, you can watch the boundary and see when it rots. Without them, specialization dissolves in two weeks.

### Memory-KPI Per Profile

Hermes profiles isolate memory, which is necessary but not sufficient. Memory rots inside each profile the same way a single wiki rots past 100 pages. Alan's research notes go stale. Mira's draft fragments pile up. Turing's debugging sessions accumulate dead branches.

**Run a weekly memory audit per profile:**
```
hermes memory audit --profile alan --stale-threshold 15%
```

> If you run LACP alongside Hermes, you get the same primitive at the control-plane layer: `lacp memory-kpi --profile alan --json | jq`. Either way, the number you watch is `stale_notes`. Once it crosses 15% of total notes in a profile, schedule a brain-resolve pass before that profile starts quoting itself from an obsolete context.

### Policy Gates Per Role

Different roles carry different risks. Research reads. Writing drafts. Engineering executes. Orchestration decides. A single policy cannot be right for all four.

**Per-role policy, in plain shape:**

- **Alan (research):** risk class `safe`. Can read web, read repo, write to `research/` only. Cannot run shell commands. Cannot write outside its sandbox.
- **Mira (writer):** risk class `safe`. Can read research outputs, write to `drafts/` only. Cannot read secrets, cannot execute code.
- **Turing (engineer):** risk class `review`. Can read repo, run sandboxed tests, write to a feature branch. Every commit to main requires explicit orchestrator approval.
- **Hermes (orchestrator):** risk class `critical`. The only profile that can approve Turing's commits, merge branches, or trigger paid API calls above a budget ceiling.

Encode this in each profile's `config.yaml` under a `policy:` block. **No profile gets more permission than its role needs, and the orchestrator is the only one who can widen any other profile's scope.**

### Gateway Messaging for Remote Supervision

The profile system is a local org chart. The gateway turns it into an operational system you can supervise from a phone.

Wire each profile to its own messaging identity:
- Alan posts research findings to a `#research` channel
- Mira drops drafts to a `#writing` channel
- Turing posts test results and PR links to `#engineering`
- Hermes synthesizes into `#ops` and asks for human approval on critical actions

Now you can walk to lunch and come back knowing which profile did what, in what order, and where it stopped. Messaging is what turns four local profiles into a live multi-agent control surface.

---

## Day-30 Failure Modes — The Four Things That Break

Every 4-profile team hits at least one of these. All four are preventable.

### Failure 1 — Profile Drift
SOUL.md edits accumulate. A week ago, Mira was "clear and audience-aware." Today, Mira is "clear, audience-aware, technically precise, and willing to draft implementation notes." Congratulations — Mira is slowly becoming Turing.

**Patch:** Diff each SOUL.md weekly against its day-one version. Any new responsibility gets an explicit approval log entry, or it gets reverted.

### Failure 2 — Handoff Rot
The contract file exists, but nobody enforces it. Alan starts sending raw transcripts to Mira again. Mira starts asking Turing to "just check this one thing." Boundaries dissolve.

**Patch:** Wire each handoff file into the harness. If the input does not match the declared shape, fail the handoff and require human review. The contract is only real if it can block.

### Failure 3 — SOUL.md Bloat
Each role grows edge cases. Turing gets a paragraph about "how we handle Python 2 legacy code." Alan gets three paragraphs about "when to skip peer-reviewed sources." Within a month, each SOUL.md is 2kb of special cases, and the agent loses the original identity in the noise.

**Patch:** Cap SOUL.md at 400 words. Anything beyond that goes into AGENTS.md or a per-domain reference file. Identity stays stable; context rotates.

### Failure 4 — Cron Collision
Profiles run cron jobs. Alan pulls a weekly research digest. Mira regenerates a weekly draft. Turing runs nightly test sweeps. Hermes runs a daily orchestration pass. By week four, two of them are colliding at 3am because nobody coordinated the schedule.

**Patch:** One shared `~/.hermes/team/cron.md` file listing every scheduled task across every profile with its exact time, duration, and dependency. Stagger collisions. Check the file before adding a new cron to any profile.

---

## The Team Reference File — Copy-Paste Template

One file, one purpose: explain your team to yourself and anyone else using the system six months from now.

```markdown
# Team: Hermes Multi-Agent
Objective: run a 4-profile Hermes team that stays coherent past day 30

## Roster
| Profile | Role | Risk Class |
|---------|------|------------|
| Hermes | Orchestrator | Critical |
| Alan | Research Specialist | Safe |
| Mira | Narrative Architect | Safe |
| Turing | Builder & Debugger | Review |

## Handoff Contracts
- `~/.hermes/team/handoffs/alan-to-mira.md`
- `~/.hermes/team/handoffs/mira-to-hermes.md`
- `~/.hermes/team/handoffs/turing-to-hermes.md`

## Cron Schedule
- `~/.hermes/team/cron.md`

## Policy Gates
Encoded in each profile's `config.yaml` under `policy:` block.

## SOUL.md Day-One References
- `~/.hermes/profiles/hermes/SOUL.md.day0`
- `~/.hermes/profiles/alan/SOUL.md.day0`
- `~/.hermes/profiles/mira/SOUL.md.day0`
- `~/.hermes/profiles/turing/SOUL.md.day0`

## Messaging Routes
- Alan → #research
- Mira → #writing
- Turing → #engineering
- Hermes → #ops (human approval gate)

## Guardrails
- No SOUL.md edit without a logged reason
- No handoff accepted without the declared input shape
- No role widened without orchestrator approval
- No cron added without checking the shared schedule
```

> Keep this file under source control. Every team member's edit goes through a commit. You will thank yourself on day 90.

---

## Agent Extraction Layer

**Objective:** Run a 4-profile Hermes team that stays coherent past day 30

**Inputs:** Working Hermes base, profile CLI, SOUL.md + AGENTS.md split, handoff contracts, per-role policy, gateway messaging

**Process:**
1. Build the 4 profiles with `--clone`
2. Write a distinct SOUL.md per role
3. Keep project context in AGENTS.md
4. Encode handoff contracts at `~/.hermes/team/handoffs/`
5. Encode per-role policy in each `config.yaml`
6. Run weekly memory-KPI per profile
7. Diff each SOUL.md against day-one
8. Stagger cron across profiles
9. Enforce team-agents.md via commits

**Outputs:**
- Four isolated profiles
- Per-role policy blocks
- Handoff contract files
- Staggered cron schedule
- Messaging routes
- Versioned team reference

**Guardrails:**
- No SOUL.md edit without a logged reason
- No handoff accepted without the declared input shape
- No role widened without orchestrator approval
- No cron added without checking the shared schedule

---

## Closing

> "Most multi-agent setups fail quietly. Everything looks fine on day one, works well on day seven, and blurs together by day thirty. The profile system is not what fails - it is the operator layer on top of it that nobody writes about."
>
> "Profiles are the feature. Boundaries are the moat."

**Credit:** [@nyk_builderz](https://x.com/nyk_builderz) | Inspired by [@neoaiforecast](https://x.com/@neoaiforecast)
**Original thread:** https://x.com/nyk_builderz/status/2044472463279710344
