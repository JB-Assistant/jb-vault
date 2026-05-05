# Claude Code Has Two Big Blind Spots. I Fixed Both.

**Source:** Akshay 🚀 (@akshay_pachaar) on X
**Date:** 2026-05-05
**Link:** https://x.com/akshay_pachaar/status/2051291922409603238

---

## Full Article

Claude Code Has Two Big Blind Spots. I Fixed Both.

No CLAUDE.md, no subagent, no rule file can fix them. But these 2 skills will.

Claude Code has two context gaps that fail in the same way: the agent can't see what it needs, and burns through tokens trying anyway.

The first is web scraping.

web_fetch doesn't return raw page content. It runs the page through a smaller model and returns a summary with a 125-character quote limit, so you can't use it to extract full tutorials, product specs, or thread content.

curl returns raw HTML but gets blocked by sites with anti-bot protection (Amazon, LinkedIn, most e-commerce), can't render JavaScript SPAs, and fails at scale due to rate limiting. Both truncate at around 100KB.

The second is backend integration.

When Claude Code talks to a backend like Supabase through MCP, it discovers state through multiple separate calls (list_tables, execute_sql, list_extensions), each returning a partial view.

Auth provider config isn't queryable at all. And when something fails, error messages don't distinguish between platform-level and code-level rejections, so the agent enters retry loops that burn tokens with every attempt. In our recent test, a single RAG app built on Supabase consumed 10.4M tokens and needed 10 manual fixes.

Bright Data solves the first problem.

InsForge solves the second. Both are open-source.

Today, let's look at how to set both of them up as skills in Claude Code and use them to build something interesting.

Bright Data adds scraping infrastructure that handles everything web_fetch and curl can't.

The agent gets a four-tier fallback that escalates based on what the target site requires, like native fetch, curl, browser automation, and a proxy network with residential IPs and automatic CAPTCHA solving.

For agent workflows, the more useful capability is structured data extraction.

Instead of raw HTML that the agent has to parse, Bright Data provides pre-built extractors for 40+ platforms (Amazon, LinkedIn, Instagram, TikTok, YouTube, Reddit) that return clean JSON with specific fields like product prices, review scores, profile data, and post content.

npx skills add brightdata/skills

This installs several skills covering scraping, search, structured data feeds, MCP orchestration, SDK best practices, and the bdata CLI.

The same RAG app that consumed 10.4M tokens on Supabase consumed 3.7M on InsForge with zero errors.

InsForge acts as the backend context engineering layer for agents using Skills and CLI.

Install all four Skills (primary documentation and diagnostic layer):

npx skills add insforge/insforge-skills

This installs insforge (SDK patterns), insforge-cli (infrastructure commands), insforge-debug (failure diagnostics), and insforge-integrations (third-party auth providers). Total metadata cost: ~714 tokens at session start.

Link the CLI to your project (primary execution layer):

npx @insforge/cli link --project-id <project-id>


---

## Summary

Akshay identifies two fundamental gaps in Claude Code that cause massive token waste: (1) web scraping limitations where web_fetch returns truncated summaries and curl gets blocked by anti-bot protection, and (2) backend integration pain where MCP-based discovery requires multiple partial calls and poor error messages trigger retry loops. He tested a Supabase RAG app that burned 10.4M tokens with 10 manual fixes. His solutions are Bright Data (open-source 4-tier scraping with structured extractors for 40+ platforms) and InsForge (backend context engineering layer with 4 skills + CLI that reduced the same RAG app to 3.7M tokens with zero errors).

---

## Key Takeaways

1. **web_fetch is useless for real extraction** — 125-char quote limit, runs through a smaller model. Can't extract full tutorials, specs, or threads.
2. **curl fails on modern web** — anti-bot blocks, no JS SPA rendering, rate limits, ~100KB truncation.
3. **Backend MCP discovery is expensive** — list_tables + execute_sql + list_extensions = multiple partial views. Auth config isn't queryable at all.
4. **Poor error messages = retry loops** — platform-level vs code-level rejections aren't distinguished. Single Supabase RAG app: 10.4M tokens, 10 manual fixes.
5. **Bright Data fix:** 4-tier fallback (native fetch → curl → browser automation → proxy network with residential IPs + CAPTCHA solving). Structured JSON extractors for 40+ platforms.
6. **InsForge fix:** 4 skills (SDK patterns, CLI, debug diagnostics, integrations) + CLI link. Metadata cost: ~714 tokens at session start. Same RAG app: 3.7M tokens, zero errors.
7. **Both are open-source** and installable as Claude Code skills via `npx skills add`.

---

## Hermes-Related Interest

- **Directly relevant to Hermes' browser/web tools** — we have browser_navigate, browser_snapshot, browser_console for DOM extraction, and curl for raw HTML. Akshay's critique of web_fetch maps to any agent scraping layer. Our multi-tool approach (curl → browser → jina.ai fallback) is similar to his 4-tier idea but less structured.
- **Backend context engineering** — Hermes talks to Supabase via MCP too. The token burn from discovery calls is real. InsForge's "metadata cost: ~714 tokens at session start" is a benchmark we should care about.
- **Skills architecture** — Akshay is pushing `npx skills add` as the distribution model for agent capabilities. This maps to Hermes' skill system. Could we package Bright Data / InsForge patterns as Hermes skills?
- **Token efficiency as competitive advantage** — 10.4M → 3.7M is a 64% reduction. For Hermes users on metered APIs (Claude, OpenRouter), this matters directly.
