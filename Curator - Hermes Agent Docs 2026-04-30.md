# Curator - Hermes Agent Docs

**Source:** Hermes Agent Docs  
**Date:** 2026-04-30  
**Link:** https://hermes-agent.nousresearch.com/docs/user-guide/features/curator

---

## Full Article

Curator 

The curator is a background maintenance pass for agent-created skills . It tracks how often each skill is viewed, used, and patched, moves long-unused skills through 
active → stale → archived states, and periodically spawns a short auxiliary-model review that proposes consolidations or patches drift. 

It exists so that skills created via the self-improvement loop don't pile up forever. Every time the agent solves a novel problem and saves a skill, that skill lands in 
~/.hermes/skills/ . Without maintenance, you end up with dozens of narrow near-duplicates that pollute the catalog and waste tokens. 

The curator never touches bundled skills (shipped with the repo) or hub-installed skills (from agentskills.io ). It only reviews skills the agent itself authored. It also never auto-deletes — the worst outcome is archival into 
~/.hermes/skills/.archive/ , which is recoverable. 

Tracks issue #7816 . 

How it runs ​ 

The curator is triggered by an inactivity check, not a cron daemon. On CLI session start, and on a recurring tick inside the gateway's cron-ticker thread, Hermes checks whether: 

Enough time has passed since the last curator run ( 
interval_hours , default 7 days ), and 

The agent has been idle long enough ( 
min_idle_hours , default 2 hours ). 

If both are true, it spawns a background fork of 
AIAgent — the same pattern used by the memory/skill self-improvement nudges. The fork runs in its own prompt cache and never touches the active conversation. 

A run has two phases: 

Automatic transitions (deterministic, no LLM). Skills unused for 
stale_after_days (30) become 
stale ; skills unused for 
archive_after_days (90) are moved to 
~/.hermes/skills/.archive/ . 

LLM review (single aux-model pass, 
max_iterations=8 ). The forked agent surveys the agent-created skills, can read any of them with 
skill_view , and decides per-skill whether to keep, patch (via 
skill_manage ), consolidate overlapping ones, or archive via the terminal tool. 

Pinned skills are off-limits to both the curator's auto-transitions and the agent's own 
skill_manage tool. See Pinning a skill below. 

Configuration ​ 

All settings live in 
config.yaml under 
curator: (not 
.env — this isn't a secret). Defaults: 

curator : 
enabled : true 
interval_hours : 168 # 7 days 
min_idle_hours : 2 
stale_after_days : 30 
archive_after_days : 90 

To disable entirely, set 
curator.enabled: false . 

Running the review on a cheaper aux model ​ 

The curator's LLM review pass is a regular auxiliary task slot — 
auxiliary.curator — alongside Vision, Compression, Session Search, etc. "Auto" means "use my main chat model"; override the slot to pin a specific provider + model for the review pass instead. 

Easiest — 
hermes model : 

hermes model # → "Auxiliary models — side-task routing" 
# → pick "Curator" → pick provider → pick model 

The same picker is available in the web dashboard under the Models tab. 

Direct config.yaml (equivalent): 

auxiliary : 
curator : 
provider : openrouter 
model : google/gemini - 3 - flash - preview 
timeout : 600 # generous — reviews can take several minutes 

Leaving 
provider: auto (the default) routes the review pass through whatever your main chat model is, matching the behavior of every other auxiliary task. 
Legacy config 
Earlier releases used a one-off 
curator.auxiliary.{provider,model} block. That path still works but emits a deprecation log line — please migrate to 
auxiliary.curator above so the curator shares the same plumbing ( 
hermes model , dashboard Models tab, 
base_url , 
api_key , 
timeout , 
extra_body ) as every other aux task. 

CLI ​ 

hermes curator status # last run, counts, pinned list, LRU top 5 
hermes curator run # trigger a review now (background by default) 
hermes curator run --sync # same, but block until the LLM pass finishes 
hermes curator pause # stop runs until resumed 
hermes curator resume 
hermes curator pin < skill > # never auto-transition this skill 
hermes curator unpin < skill > 
hermes curator restore < skill > # move an archived skill back to active 

hermes curator status also lists the five least-recently-used skills — a quick way to see what's likely to become stale next. 

The same subcommands are available as the 
/curator slash command inside a running session (CLI or gateway platforms). 

What "agent-created" means ​ 

A skill is considered agent-created if its name is not in: 

~/.hermes/skills/.bundled_manifest (skills copied from the repo on install), and 

~/.hermes/skills/.hub/lock.json (skills installed via 
hermes skills install ). 

Everything else in 
~/.hermes/skills/ is fair game for the curator. This includes: 

Skills the agent saved via 
skill_manage(action="create") during a conversation. 

Skills you created manually with a hand-written 
SKILL.md . 

Skills added via external skill directories you've pointed Hermes at. 

If you want to protect a specific skill from ever being touched — for example a hand-authored skill you rely on — use 
hermes curator pin <name> . See the next section. 

Pinning a skill ​ 

Pinning is a hard fence against both automated and agent-driven changes. Once a skill is pinned: 

The curator skips it during auto-transitions ( 
active → stale → archived ), and its LLM review pass is instructed to leave it alone. 

The agent's 
skill_manage tool refuses every write action on it. Calls to 
edit , 
patch , 
delete , 
write_file , and 
remove_file return a refusal that tells the model to ask the user to run 
hermes curator unpin <name> . This prevents the agent from silently rewriting a skill mid-conversation. 

Pin and unpin with: 

hermes curator pin < skill > 
hermes curator unpin < skill > 

The flag is stored as 
"pinned": true on the skill's entry in 
~/.hermes/skills/.usage.json , so it survives across sessions. 

Only agent-created skills can be pinned — bundled and hub-installed skills are never subject to curator mutation in the first place, and 
hermes curator pin will refuse with an explanatory message if you try. 

If you need to update a pinned skill yourself, edit 
~/.hermes/skills/<name>/SKILL.md directly with your editor. The pin only guards the agent's tool path, not your own filesystem access. 

Usage telemetry ​ 

The curator maintains a sidecar at 
~/.hermes/skills/.usage.json with one entry per skill: 

{ 
"my-skill" : { 
"use_count" : 12 , 
"view_count" : 34 , 
"last_used_at" : "2026-04-24T18:12:03Z" , 
"last_viewed_at" : "2026-04-23T09:44:17Z" , 
"patch_count" : 3 , 
"last_patched_at" : "2026-04-20T22:01:55Z" , 
"created_at" : "2026-03-01T14:20:00Z" , 
"state" : "active" , 
"pinned" : false , 
"archived_at" : null 
} 
} 

Counters increment when: 

view_count : the agent calls 
skill_view on the skill. 

use_count : the skill is loaded into a conversation's prompt. 

patch_count : 
skill_manage patch/edit/write_file/remove_file runs on the skill. 

Bundled and hub-installed skills are explicitly excluded from telemetry writes. 

Per-run reports ​ 

Every curator run writes a timestamped directory under 
~/.hermes/logs/curator/ : 

~/.hermes/logs/curator/ 
└── 20260429-111512/ 
├── run.json # machine-readable: full fidelity, stats, LLM output 
└── REPORT.md # human-readable summary 

REPORT.md is a quick way to see what a given run did — which skills transitioned, what the LLM reviewer said, which skills it patched. Good for auditing without having to grep 
agent.log . 

Restoring an archived skill ​ 

If the curator archived something you still want: 

hermes curator restore < skill-name > 

This moves the skill back from 
~/.hermes/skills/.archive/ to the active tree and resets its state to 
active . The restore refuses if a bundled or hub-installed skill has since been installed under the same name (would shadow upstream). 

Disabling per environment ​ 

The curator is on by default. To turn it off: 

For one profile only: edit 
~/.hermes/config.yaml (or the active profile's config) and set 
curator.enabled: false . 

For just one run: 
hermes curator pause — the pause persists across sessions; use 
resume to re-enable. 

The curator also refuses to run if 
min_idle_hours hasn't elapsed, so on an active dev machine it naturally only runs during quiet stretches. 

See also ​ 

Skills System — how skills work in general and the self-improvement loop that creates them 

Memory — a parallel background review that maintains long-term memory 

Bundled Skills Catalog 

Issue #7816 — original proposal and design discussion

---

## Summary

Hermes Curator is a background maintenance system for agent-created skills. It tracks usage telemetry, marks unused skills as stale, archives long-unused skills, and periodically launches an auxiliary-model review to recommend patches, consolidation, or archival.

It does **not** mutate bundled or hub-installed skills, and it never hard-deletes skills. The important operational controls are `curator.enabled`, curator timing thresholds, `auxiliary.curator` model routing, CLI/slash commands like `hermes curator status`, `run`, `pause`, `pin`, `restore`, and the hard protection provided by pinning.

---

## Key Takeaways

1. Curator prevents self-authored skills from accumulating forever and polluting the skill catalog.
2. It only applies to agent-created/manual/external skills, not bundled repo skills or hub-installed skills.
3. Automatic transitions are deterministic: unused skills become stale after 30 days and archived after 90 days by default.
4. LLM review runs as a background fork using the `auxiliary.curator` model slot.
5. Pinned skills are protected from both curator transitions and `skill_manage` write actions.
6. Every run writes auditable reports under `~/.hermes/logs/curator/`.
7. Archived skills can be restored with `hermes curator restore <skill-name>`.

---

## Hermes-Related Interest

Directly relevant. This explains how Hermes keeps the self-improvement loop clean: skills can be created aggressively without turning the catalog into token bloat, because Curator handles stale/archive/review cycles. For Junaid's workflow, pin hand-authored/core business skills and let Curator manage narrow experimental skills.
