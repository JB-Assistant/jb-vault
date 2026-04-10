---
title: Agents
description: Shared project state, task log, and checkpoint tracking for Hermes and OpenClaw. Both agents read and write this file.
last_updated: 2026-04-09
---

# Agents

## Session State

**Last session:** 2026-04-09 (today)
**Active context:** Building Layer 2 files for multi-agent shared memory

## Hermes

- **Status:** Active this session
- **Platform:** VPS/Linux, connected via Telegram
- **Last checkpoint:** 2026-04-09

## OpenClaw

- **Status:** Not confirmed active yet today
- **Platform:** MacMini
- **Last sync:** Needs to be confirmed — MacMini should be writing Layer 2 files

## Project State

### PDF TTS App
| Field | Value |
|-------|-------|
| Status | Running on VPS |
| URL | http://167.235.240.164:8000 |
| Next action | Verify iPhone access works |
| Blocking issue | None |

### Multi-Agent Memory Setup
| Field | Value |
|-------|-------|
| Status | Building Layer 2 files |
| Layer 2 files | Soul.md (done), Agents.md (this file) |
| Layer 3 | wiki/ folder inside JB Vault (done) |
| Layer 2 sync | Pending — need Syncthing or git approach confirmed |
| OpenClaw setup | Pending — need to confirm OpenClaw reads Layer 2 |

## Today's Log

### 2026-04-09
- **10:00 AM:** Discussed 4-layer memory architecture with user
- **10:15 AM:** Created wiki/ inside JB Vault — 10 pages covering Claude Managed Agents, Karpathy LLM Wiki, OpenClaw, Hermes, etc.
- **10:30 AM:** Started building Layer 2 files (Soul.md, Agents.md)
- **Article saves:** 5 Claude Managed Agents articles pushed to vault (Sharbel, Corey Ganem, Nick Spisak, AI Edge, Karpathy)
- **Next:** Build checkpointing into session workflow (every 3-5 tool calls)

## Pending Tasks

- [ ] Confirm OpenClaw can read/write Layer 2 files — **scheduled for tomorrow**
- [ ] Set up Syncthing or git-based sync for Layer 2 between MacMini and VPS — **OpenClaw setup first**
- [ ] Test that Hermès reads Soul.md/Agents.md on session start — **verified, working**
- [ ] Add checkpoint writing to Hermès session workflow — **active, in progress**
- [ ] Verify iPhone access to PDF TTS app — **pending**

## Checkpoint Log

- **2026-04-09 | Hermes** — Layer 2 files created: Soul.md + Agents.md. OpenClaw setup deferred to tomorrow.

---

*This file is the shared brain between Hermes and OpenClaw. Both agents write here on checkpoints.*
