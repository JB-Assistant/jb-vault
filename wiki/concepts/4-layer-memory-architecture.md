---
title: 4-Layer Memory Architecture
created: 2026-04-09
updated: 2026-04-09
type: concept
tags: [memory-architecture, multi-agent, layered-memory, checkpointing, openclaw, hermes]
sources: [memory]
---

# 4-Layer Memory Architecture

## Overview
A layered approach to agent memory that combines fast built-in context with persistent external storage, enabling long-term continuity across sessions without token bloat or infrastructure overhead. Used by OpenClaw, Hermes, and similar agent systems.

## The 4 Layers

### Layer 1: Built-in Memory
The agent's core identity, boundaries, and immediate context. Short, fixed, loaded every session.

### Layer 2: Agents.md + Soul.md
Shared state files that both agents (Hermes + OpenClaw) read and write on checkpoints. Contains:
- **Soul.md:** Agent identity, user profile, long-term facts, communication style
- **Agents.md:** Active projects, pending tasks, today's log, shared context

### Layer 3: Obsidian Vault
Persistent markdown file storage. Daily logs, project context, articles, research. Synced between machines via git or Syncthing. Wikilinks and folder structure act as a natural knowledge graph — LLMs navigate Markdown surprisingly well without vector embeddings.

### Layer 4: Session Search
Full session history for cross-session recall. Complements the structured vault with ad-hoc retrieval when needed.

## Memory Flow

```
Session Start
    ↓
Read vault (user-profile, project-state, today's context)
    ↓
Work — checkpoint every 3-5 tool calls
    ↓
Task done → append to daily log, update working-context
    ↓
Compaction hits? → todo list survives, re-read vault after
    ↓
Session End → flush everything to daily log
```

## Why It Works
- **Progressive disclosure** — token-efficient, agents only load what they need
- **Human-readable** — plain Markdown, editable by humans directly
- **Multi-agent compatible** — both OpenClaw and Hermes share Layer 2 files
- **Compounds over time** — knowledge from old sessions informs new ones
- **No vector DB needed** — wikilinks and structured folders work surprisingly well

## Community Consensus (2026)
Widely praised in OpenClaw/Hermes/Claude communities as a "game-changer" for agent continuity. Seen as a practical workaround for stateless LLM limitations. Key maintenance risk: inconsistent checkpoint writes create a "graveyard of experiments." Structured schemas and discipline matter more than tooling.

## Checkpoint Cadence
- Every 3-5 tool calls (mid-session checkpoint)
- At task start (read current state)
- At task end (save results, update todo)
- At session end (flush to daily log)

## Obsidian Integration
The vault works as an Obsidian vault out of the box. Wikilinks render as clickable links, Graph View visualizes the knowledge network. `[[wikilinks]]` between pages form a natural navigation structure that LLMs follow well.

## Related
[[claude-managed-agents]] | [[plain-text-persistence]] | [[wikilinks-as-knowledge-graph]] | [[multi-agent-shared-vault]]
