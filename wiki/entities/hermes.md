---
title: Hermes
created: 2026-04-09
updated: 2026-04-09
type: entity
tags: [hermes, agent, telegram, multi-agent]
sources: [memory]
---

# Hermes

## Overview
The primary conversational agent connected to the user via Telegram. Running on Linux (VPS or local). Part of a multi-agent setup alongside OpenClaw on MacMini, with a shared [[4-layer-memory-architecture]] using Obsidian as the persistent external knowledge layer.

## Key Facts
- **Connected to:** Telegram (primary communication channel)
- **Access to:** JB Vault at `/home/hermes/JB Vault` on GitHub
- **Shared with:** [[openclaw]] (MacMini) via Layer 2 files and Layer 3 vault
- **Prefers:** concise responses

## Shared Memory Architecture
Hermes and OpenClaw share the 4-layer memory system:
- **Layer 2:** Agents.md and Soul.md — both agents read/write on checkpoints
- **Layer 3:** Obsidian vault synced via Syncthing or git
- Both follow checkpoint cadence: every 3-5 tool calls

## Tools & Integrations
- Reads/writes markdown files to JB Vault
- Git push/pull for vault sync with GitHub
- FXTwitter API for X/Twitter content extraction
- Browser for web scraping
- Article summarization skill for saving articles to vault
- PDF TTS pipeline (RapidOCR + Piper TTS) on VPS

## Related
[[openclaw]] | [[4-layer-memory-architecture]] | [[multi-agent-shared-vault]] | [[plain-text-persistence]]
