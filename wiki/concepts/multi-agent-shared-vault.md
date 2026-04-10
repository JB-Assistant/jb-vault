---
title: Multi-Agent Shared Vault
created: 2026-04-09
updated: 2026-04-09
type: concept
tags: [multi-agent, shared-vault, obsidian, syncthing, openclaw, hermes]
sources: [memory]
---

# Multi-Agent Shared Vault

## Overview
Pattern where multiple AI agents (e.g., OpenClaw + Hermes) share the same Obsidian vault as a persistent knowledge layer. Both agents read and write Layer 2 files (Soul.md, Agents.md) and Layer 3 articles/context, enabling true continuity across different agent instances.

## Architecture
```
[OpenClaw on MacMini] ←→ [Layer 2: Soul.md, Agents.md] ←→ [Layer 3: Vault/]
[Hermes on VPS/Linux] ←→ [Layer 2: Soul.md, Agents.md] ←→ [Layer 3: Vault/]
```

**Layer 2 files (actual):**
- `/home/hermes/JB Vault/Soul.md` — identity, user profile, long-term memory, technical context
- `/home/hermes/JB Vault/Agents.md` — project state, session log, pending tasks, checkpoint log

Both agents:
- Read Layer 2 on session start
- Write Layer 2 at checkpoints (every 3-5 tool calls)
- Flush to Layer 3 on session end

## Sync Options

### Syncthing (P2P)
- Peer-to-peer real-time sync, no server needed
- Both machines need to be online briefly for initial handshake
- Encrypted by default
- Risk: simultaneous writes from both agents → conflict resolution needed

### Git (via GitHub)
- Already configured for Hermes
- OpenClaw would also push/pull to the same repo
- Better conflict resolution than Syncthing
- Requires internet for sync

### Syncthing + Git Hybrid
- Syncthing for real-time local sync between machines
- Git as the backup/version control layer
- Best of both worlds if both machines are on the same network

## Shared Brain Pattern
Some users run "CTO/CMO/Founder Brain" agents — different agents with different personas sharing the same vault. The vault becomes a true shared memory between multiple specialized agents.

## Related
[[4-layer-memory-architecture]] | [[openclaw]] | [[hermes]] | [[syncthing-setup]]
