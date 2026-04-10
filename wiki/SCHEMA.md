# Wiki Schema

## Domain
AI Agent Memory Systems — architectures, tools, and patterns for building persistent, compounding knowledge bases for AI agents. Covers OpenClaw, Hermes, Claude Managed Agents, Obsidian vault patterns, multi-agent shared memory, checkpoint systems, and knowledge management techniques.

## Conventions
- File names: lowercase, hyphens, no spaces (e.g., `claude-managed-agents.md`)
- Every wiki page starts with YAML frontmatter (see below)
- Use `[[wikilinks]]` to link between pages (minimum 2 outbound links per page)
- When updating a page, always bump the `updated` date
- Every new page must be added to `index.md` under the correct section
- Every action must be appended to `log.md`
- raw/ layer is immutable — corrections go in wiki pages, never raw sources

## Frontmatter
```yaml
---
title: Page Title
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: entity | concept | comparison | query | summary
tags: [from taxonomy below]
sources: [raw/articles/source-name.md]
---
```

## Tag Taxonomy
Add new tags here BEFORE using them. Current tags:

**Systems/Products:** openclaw, hermes, claude-managed-agents, obsidian, claude-code, openai-agents
**Concepts:** memory-architecture, checkpointing, session-persistence, wikilinks, multi-agent, agentic-pkm
**Techniques:** plain-text-persistence, layered-memory, permission-scoping
**People/Orgs:** anthropic, alex-finn, karpathy, corey-ganem, nick-spisak
**Meta:** comparison, timeline, setup-guide, business-model

## Page Thresholds
- **Create a page** when an entity/concept appears in 2+ sources OR is central to one source
- **Add to existing page** when a source mentions something already covered
- **DON'T create a page** for passing mentions, minor details, or things outside the domain
- **Split a page** when it exceeds ~200 lines — break into sub-topics with cross-links
- **Archive a page** when its content is fully superseded — move to `_archive/`, remove from index

## Entity Pages
One page per notable entity. Include:
- Overview / what it is
- Key facts and dates
- Relationships to other entities ([[wikilinks]])
- Source references

## Concept Pages
One page per concept or topic. Include:
- Definition / explanation
- Current state of knowledge
- Open questions or debates
- Related concepts ([[wikilinks]])

## Comparison Pages
Side-by-side analyses. Include:
- What is being compared and why
- Dimensions of comparison (table format preferred)
- Verdict or synthesis
- Sources

## Update Policy
When new information conflicts with existing content:
1. Check the dates — newer sources generally supersede older ones
2. If genuinely contradictory, note both positions with dates and sources
3. Mark the contradiction in frontmatter: `contradictions: [page-name]`
4. Flag for user review in the lint report

## Log Rotation
When log.md exceeds 500 entries, rename to `log-YYYY.md` and start fresh.
