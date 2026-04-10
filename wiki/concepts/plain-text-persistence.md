---
title: Plain Text Persistence
created: 2026-04-09
updated: 2026-04-09
type: concept
tags: [plain-text-persistence, obsidian, wikilinks, agentic-pkm]
sources: [memory]
---

# Plain Text Persistence

## Overview
Using plain Markdown files as the primary storage medium for agent memory and knowledge. Files over apps. No database, no vendor lock-in, no special tooling required. Any LLM can read and write the same files.

## Why Plain Text Works for Agents
- **Interoperable** — any LLM (local or API) accesses the same vault
- **Human-editable** — users can modify notes directly without an agent
- **Version-controllable** — git handles history, rollback, sync
- **Future-proof** — no proprietary format to migrate
- **LLMs navigate it well** — wikilinks and folder structure act as a natural knowledge graph without vector embeddings

## Obsidian as the Interface
The same Markdown files render as an Obsidian vault:
- `[[wikilinks]]` become clickable graph edges
- Folder structure mirrors human mental models
- YAML frontmatter enables Dataview queries
- Graph View visualizes connections between concepts

## Community View (2026)
Described as a "superpower" for agent continuity. Part of the shift toward "agentic PKM" — AI handles the janitorial work (sorting, linking, summarizing) while the human owns the plain-text core. Wikilinks plus folder hierarchy often outperforms naive vector search for recall in benchmarks.

## Maintenance Risks
- Inconsistent writes create a "graveyard of experiments"
- Wikilinks can become stale if pages are renamed without updating links
- Without structured schemas, vaults grow chaotic over time

## Related
[[wikilinks-as-knowledge-graph]] | [[4-layer-memory-architecture]] | [[multi-agent-shared-vault]]
