# Prompt Caching in LLMs, Clearly Explained

**Source:** https://x.com/_avichawla/status/2044670188998803855
**Author:** @_avichawla
**Date:** April 16, 2026
**Tag:** #llm #caching #inference #cost-optimization #claude

## Core Problem

Every agent request sends the entire conversation history back to the LLM — system instructions, tool definitions, project context — all re-read, re-processed, and re-billed on every turn.

A 20,000-token system prompt over 50 turns = 1M tokens of redundant computation at full price.

## Two Types of Content

Every agent request has:
1. **Static prefix** — system prompt, tool definitions, project context (changes rarely)
2. **Dynamic suffix** — conversation history, tool outputs (changes every turn)

This split makes caching possible.

## How KV Caching Works

**Prefill phase:** transformer computes Query, Key, Value vectors for each token. K+V tensors depend only on preceding tokens and never change once computed.

**Without caching:** K+V tensors discarded after every request, recomputed from scratch.

**With caching:** KV tensors persisted on inference servers, indexed by cryptographic hash of token sequence. Matching hash = tensors loaded from memory, prefill computation skipped.

Result: O(n²) → O(n) per generated token.

## Pricing

| Operation | Cost |
|-----------|------|
| Cache read | 0.1x base input (90% discount) |
| Cache write | 1.25x (25% premium) |
| Extended 1-hour cache | 2.0x |

## Central Constraint

> "1 + 2 = 3" works but "2 + 1" is a cache miss.

Hash includes the full token sequence from the beginning. Any change — even element order — causes a full recompute.

**Cache breakers:**
- Timestamps in system prompts
- Shuffled tool definitions
- Model switching mid-session
- Mutations upstream of cache breakpoint

## Three Rules

1. Put static content at the top, dynamic at the bottom
2. Never mutate anything upstream of the cache breakpoint
3. Use cache-safe forking for context compaction

## Cache-Safe Forking

When approaching context limit: keep same system prompt + tools + conversation history, append compaction instruction as new message. Only the compaction instruction itself is new tokens.

## Monitoring

Track in API response: `cache_read_input_tokens / (cache_read_input_tokens + cache_creation_input_tokens)`

## Claude Code Case Study

- Session: 30 minutes, 2M tokens total
- Without caching: $6.00
- With 92% cache hit rate: $1.15 (81% reduction)
- Static 20k-token foundation paid for once, read for $0.30/MTok instead of $3.00/MTok

## Key Quote

> "If you're building agents and not designing around prompt caching, you're leaving most of your margin on the table."

## Action Items

- [ ] Audit your agent prompts: is static content at top, dynamic at bottom?
- [ ] Remove any timestamps or mutable content from system prompts
- [ ] Monitor cache efficiency metrics in production
