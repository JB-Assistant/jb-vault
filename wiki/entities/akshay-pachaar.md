---
title: Akshay 🚀 (akshay_pachaar)
created: 2026-04-13
updated: 2026-05-05
type: entity
tags: [person, content-creator, ai-agents, memory-systems, twitter, claude-code, token-efficiency]
sources: [raw/articles/Article - Build Agents that never forget - Akshay 2026-04-13.md, raw/articles/Claude Code Has Two Big Blind Spots - Akshay 2026-05-05.md]
---

# Akshay 🚀 (akshay_pachaar)

## Overview
AI agent educator and technical content creator on X/Twitter. Posts in-depth, first-principles technical threads about agent architecture, memory systems, and LLM engineering. Known for thorough explanations grounded in cognitive science and systems thinking.

## Key Content
- **Article:** "Build Agents that never forget" — A first-principles deep-dive into agent memory architecture: 7 failure modes of stateless agents, cognitive science framing (sensory/working/long-term memory), Lilian Weng's 4-pillar agent framework, and evolution of memory layers from Python lists through vector search to graph-vector hybrids. Link: https://x.com/akshay_pachaar/status/2043745099792953508
- **Article:** "Claude Code Has Two Big Blind Spots. I Fixed Both." — Identifies two fundamental gaps in Claude Code: (1) web scraping limitations (web_fetch truncated summaries, curl blocked by anti-bot) and (2) backend integration pain (MCP discovery = multiple partial calls, poor error messages = retry loops). Tested a Supabase RAG app that burned 10.4M tokens with 10 manual fixes. Solutions: Bright Data (4-tier scraping with structured extractors for 40+ platforms) and InsForge (backend context engineering layer with 4 skills + CLI, reduced same app to 3.7M tokens, zero errors). Both installable via `npx skills add`. Link: https://x.com/akshay_pachaar/status/2051291922409603238

## Notes
- Focuses on memory systems and agent architecture
- Technical, systems-thinking approach to AI agent content
- Now also covering Claude Code tooling gaps, token efficiency, and agent skill distribution (npx skills add model)

## Related
[[4-layer-memory-architecture]] | [[karpathy-llm-wiki]] | [[claude-managed-agents]]
