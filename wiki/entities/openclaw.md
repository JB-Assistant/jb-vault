---
title: OpenClaw
created: 2026-04-09
updated: 2026-04-09
type: entity
tags: [openclaw, agent, macmini, multi-agent]
sources: [memory]
---

# OpenClaw

## Overview
AI agent tool running on the user's MacMini. Part of a multi-agent setup alongside Hermes, with a shared 4-layer memory architecture using Obsidian as the persistent external knowledge layer.

## Key Facts
- **Runs on:** MacMini (always-on or frequently on)
- **Context:** Connected to Hermes via shared vault (Layer 2/3)
- **Purpose:** Primary agent for user's daily workflows

## Relationship to Other Agents
- [[hermes]] — sibling agent, shares Layer 2 files (Soul.md, Agents.md) and Layer 3 vault
- Both follow the same checkpoint cadence (every 3-5 tool calls)
- Both read/write the same Obsidian vault via Syncthing or git

## Shared Memory Architecture
OpenClaw and Hermes share the [[4-layer-memory-architecture]] system:
- Layer 2 files are the primary shared state between both agents
- Layer 3 (Obsidian vault) is the persistent storage both can reach
- [[multi-agent-shared-vault]] pattern — multiple agents acting as "CTO/CMO/Founder Brain" sharing the same vault

## Related
[[hermes]] | [[4-layer-memory-architecture]] | [[multi-agent-shared-vault]]
