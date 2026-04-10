---
title: Karpathy LLM Wiki
created: 2026-04-09
updated: 2026-04-09
type: concept
tags: [karpathy, llm-wiki, knowledge-base, plain-text, agentic-pkm, rag-alternative]
sources: [raw/articles/how-to-set-up-claude-managed-agents-sharbel-2026-04-09.md, raw/articles/claude-code-plus-obsidian-ultimate-guide-aiedge-2026-04-09.md, raw/papers/llm-knowledge-bases-andrej-karpathy.md]
---

# Karpathy LLM Wiki

## Overview
Andrej Karpathy's viral pattern for using LLMs to build personal knowledge bases that compound over time. Published as a GitHub Gist: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f

This is the foundational concept behind the 4-layer memory architecture used by OpenClaw, Hermes, and many other agent systems.

## The Core Insight

Large fraction of token throughput going less into manipulating code, more into manipulating knowledge stored as markdown and images. The latest LLMs are quite good at it. No fancy RAG needed at small-to-medium scale — the LLM auto-maintains index files and navigates the wiki directly.

## The 5-Part Workflow

### 1. Data Ingest
- Index source documents (articles, papers, repos, datasets, images) into `raw/` directory
- Use Obsidian Web Clipper to convert web articles to .md files
- Download related images locally so the LLM can reference them
- raw/ is immutable — the LLM never modifies it

### 2. IDE (Obsidian as Frontend)
- Obsidian is the viewer for: raw data, compiled wiki, derived visualizations
- Marp plugin for slide rendering
- Important: **the LLM writes and maintains all wiki data; humans rarely touch it directly**

### 3. Q&A Against the Wiki
- Once wiki is large enough (~100 articles, ~400K words), ask complex questions
- LLM agent goes off and researches answers across the wiki
- No RAG pipeline needed — LLM reads all important related data directly at context-window scale
- LLM auto-maintains index files and brief summaries of all documents

### 4. Output
- Instead of text/terminal answers: render markdown files, Marp slide shows, matplotlib images
- All outputs viewable in Obsidian
- **Key:** outputs get filed back into the wiki — queries always "add up" in the knowledge base
- The wiki compounds over time

### 5. Linting / Health Checks
- LLM runs health checks over the wiki: find inconsistent data, impute missing data (via web search), find interesting connections for new article candidates
- Incrementally clean up and enhance overall data integrity
- LLM suggests further questions to ask

## Extra Tools
- Custom search engines over the wiki (naive but effective)
- Handed to LLM via CLI as a tool for larger queries
- Karpathy: "I vibe coded a small and naive search engine over the wiki"

## Further Explorations
- As the repo grows: synthetic data generation + finetuning to have the LLM "know" the data in its weights
- The knowledge base as training data for a specialized model

## Karpathy's Product Vision
> "I think there is room here for an incredible new product instead of a hacky collection of scripts."

## Why This Is Different From RAG
- RAG rediscovers knowledge from scratch per query
- LLM Wiki: knowledge is already compiled, cross-referenced, and current
- No embedding models, no vector search, no similarity queries needed at this scale
- Plain text + wikilinks + LLM navigation outperforms naive vector setups for recall

## Relationship to This System
Karpathy's pattern is the theoretical foundation for:
- [[4-layer-memory-architecture]] (OpenClaw + Hermes implementation)
- [[plain-text-persistence]] (plain MD files as memory)
- [[aiedge]]'s beginner guide (practical walkthrough)
- [[claude-managed-agents]] (Anthropic's hosted agent infrastructure supporting this pattern)

## Related
[[4-layer-memory-architecture]] | [[plain-text-persistence]] | [[aiedge]] | [[claude-managed-agents]]
