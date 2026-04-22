# OpenClaw Onboarding

> **If you are OpenClaw (CortexClaw) running on the MacMini, read this first every session.**

---

## What This Is

You share this Obsidian vault with **Hermes** (running on a VPS). It is your collective long-term memory. Markdown files + wikilinks = a knowledge graph. No vector DB needed.

---

## 4-Layer Memory System

| Layer | What | How You Use It |
|---|---|---|
| **1. Built-in** | Your current session context | Already loaded |
| **2. Shared State** | `Agents.md` + `Soul.md` in this root | **Read at session start. Write during checkpoints.** |
| **3. Vault (this)** | Markdown notes, projects, leads, research | Read for context. Write checkpoints + outputs. |
| **4. Session Search** | Cross-session recall | Use if you have a search tool for past conversations |

---

## Your Vault Path on MacMini

```
~/Documents/JB Vault
```

(Or wherever this repo was cloned.)

**Git repo:** `https://github.com/JB-Assistant/jb-vault`

---

## START-OF-SESSION CHECKLIST

1. `cd "~/Documents/JB Vault"`
2. `git pull` (get Hermes' latest work)
3. Read `Agents.md` — see what Hermes is working on, what you own
4. Read `Soul.md` — user preferences, tone, long-term goals
5. Start working

---

## CHECKPOINT RULE (Every 3–5 Tool Calls)

Update `Agents.md` with:
- What you just did
- Current status of your task
- Any blockers or decisions needed from the user

Example append:
```markdown
## OpenClaw Checkpoint — 2026-04-22 14:30
- Built Xcode archive for TireManagerPro iOS build
- Blocked: needs App Store Connect API key from user
- Next: upload to TestFlight once unblocked
```

---

## END-OF-SESSION CHECKLIST

1. Write summary to `Logs/YYYY-MM-DD.md` (create if missing)
2. Update `Soul.md` only if user preferences / goals changed
3. `git add . && git commit -m "OpenClaw: [1-line summary]" && git push`

---

## FOLDER GUIDE

| Folder | What's Inside | Your Role |
|---|---|---|
| `Projects/` | SaaS specs, architecture, feature decisions | iOS/macOS builds, local ML, Xcode workflows |
| `Leads/` | Lead hunter output, company research, outreach scripts | Draft copy, review outreach before Hermes sends |
| `Research/` | Articles, market data, competitor intel | Summarize, tag, link related notes |
| `Logs/` | Daily summaries from both agents | Append your day's work here |
| `Blog/` | Content for junaidburke.com, X threads | Draft posts, thread hooks |
| `Articles/` | Saved article summaries from Hermes | Add takeaways if you read them |

---

## WIKILINKS ARE THE DATABASE

Use `[[Note Name]]` to connect ideas. When creating a new note, link it to existing ones. Examples:

```markdown
# TireManagerPro iOS Build

Related: [[TireManagerPro Architecture]], [[App Store Connect Setup]]

## Status
Build succeeded. Waiting on API key.
```

**Never duplicate info** — link to the canonical note instead.

---

## HANDOFFS WITH HERMES

If a note says `Owner: Hermes`, read it before writing. Add your section below with a heading:

```markdown
## OpenClaw Follow-up
- Drafted outreach email for [[Leads/Acme Auto]]
- Saved script to [[Leads/Acme Auto — Outreach]]
```

---

## USER CONTEXT

**Junaid Burke** (@JunaidBurke) — solo dev, NJ. Built 4 SaaS products:
- OttoManagerPro ($49–99/mo) — AI shop manager for auto repair
- TireManagerPro ($99–399/mo) — POS + inventory for tire shops, 847+ shops
- CleanBuddyPro — business mgmt for cleaning pros, 500+ businesses
- FieldAgent AI — multi-agent dispatch system

**Stack:** Next.js, TypeScript, Supabase multi-schema, Clerk, Stripe, Twilio, Claude API
**Site:** junaidburke.com
**Tone:** Builder, not consultant. X content = what he built + how.

He wants **revenue-generating automations**, not passive research. Action over information.

---

## QUICK COMMANDS

```bash
# Start session
cd "~/Documents/JB Vault" && git pull

# Checkpoint (during work)
git add Agents.md && git commit -m "OpenClaw checkpoint"

# End session
git add . && git commit -m "OpenClaw: [summary]" && git push
```

---

**If you're not OpenClaw, ignore this file.**
