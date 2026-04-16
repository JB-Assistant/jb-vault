# Claude + Obsidian: The Memory Stack That Compounds

**Source:** https://x.com/nyk_builderz/status/2030904887186514336
**Author:** @nyk_builderz
**Date:** April 2026
**Tag:** #memory #claude #obsidian #context-windows

## Core Thesis

Teams burn 30-40 minutes per Claude session re-explaining what they already knew yesterday. The real failure isn't reasoning — it's drift. A three-tier memory system fixes this.

## Key Insight: Context Amnesia

A 200k context window doesn't change the constraint that humans can only hold ~4 chunks of meaningful structure in active attention at once. Scanning is not knowing. LLMs have no continuity between sessions.

## The Three-Layer Memory Stack

### Layer 1: CLAUDE.md (Who You Are)

First thing Claude reads every session. Not a config file — a teaching document. Contains:
- Who you are / what you care about
- Your conventions and patterns
- Edge cases already solved

### Layer 2: MEMORY.md + Obsidian Vault

**MEMORY.md** — routing document, stays under 200 lines. Detailed notes go in topic files and get linked.

**Obsidian as a persistence layer** — wikilinks as semantic connections, atomic composable notes, maps of content for navigation. The graph is what matters.

**Key principles:**
- Prose-as-title: notes named as claims, not categories
  - Not `memory-systems.md` but `memory graphs beat giant memory files`
- Wikilinks-as-prose: links that read as sentences
  - `[[memory graphs beat giant memory files]]`

**Retrieval filters (4 levels):**
1. Query → relevant depth on first pass

### Layer 3: Brain-Ingest (Feed the Brain)

Captures knowledge from the real world: YouTube videos, conference talks, voice memos, podcasts.

```
brain-ingest "https://youtube.com/watch?v=..." --apply
```

Extracts structured notes from raw transcripts — fills the gap between "I watched something useful" and "Claude can find it."

## The Agent Loop

Agents can handle maintenance tasks without getting bored:
- Notices when notes contradict
- Flags specs out of sync with codebase
- Proposes structural changes when drag accumulates
- Refactors its own instructions

## Key Quotes

> "An Obsidian vault is not a note-taking app. It's a persistence layer your AI can query at runtime. The system IS the files."

> "Memory is not a feature. It's an operating system for attention."

> "Agents live in context windows like humans live in lifespans. They need externalized knowledge for the same reason we needed writing."

> "Your AI is already a graph traverser. The question is whether you gave it a graph worth traversing."

## Relationship to Your Setup

You already have this architecture:
- **Layer 1:** `Agents.md` + `Soul.md` (shared state files)
- **Layer 2:** Obsidian vault with wikilinks
- **Layer 3:** Article workflow (send link → save full + summary + takeaways)

The NYK thread validates your 4-layer approach and adds brain-ingest as a missing piece for Layer 3.

## Action Items

- [ ] Explore `brain-ingest` tool for feeding YouTube/音频 content into vault
- [ ] Ensure CLAUDE.md is framed as teaching doc, not config
- [ ] Review MEMORY.md stays under 200 lines
