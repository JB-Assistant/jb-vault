# Claude Code + Obsidian Ultimate Guide (build an AI second brain)

**Source:** AI Edge (@aiedge_)  
**Date:** 2026-04-09  
**Link:** https://x.com/aiedge_/status/2041908011078447222

---

## Full Article

Claude Code + Obsidian is the most powerful AI combo I've ever used. I literally built an AI second brain that contains everything I think, read, write, research online, and more. It contains my business plans, all my YouTube videos (ever), articles I've written, and anything else that is important to me.

This might look complicated, but it literally only takes 5 minutes to set up, and the crazy part is, it improves over time with a built-in memory system.

Inspired by Andrej Karpathy's viral tweet about LLM Knowledge Bases.

---

## The Problem This Solves

Current AI tools require constant re-prompting, adding context, and starting from scratch anytime you start a new chat or migrate to a new AI tool. By pairing Karpathy's system prompt with Obsidian + Claude Code, you eliminate that problem completely.

## How This System Works (4 Moving Parts)

1. **Your data** — articles, notes, transcripts, ideas, etc.
2. **Organization** — done by Claude Code in Obsidian
3. **Instant Prompting** — ask your new database anything at any time
4. **Evolving Memory** — the ability to get smarter over time

## Setting Up Your AI Brain (5 Minutes)

1. **Download Obsidian** — https://obsidian.md/
2. **Set up your Vault** — think of this as a desktop folder. Name it whatever you want. This is where all your MD files live.
3. **Claude Code setup** — use the desktop app. In the main chatbox, click "Select Folder" and find your Obsidian Vault.
4. **System Prompt** — paste Andrej Karpathy's system prompt into the main chatbox. Get it here: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
5. **Building your database** — Claude Code will ask for data points to start. Think: notes, CSV files, MD/text, articles, bookmarks, ideas. The more initial data, the faster your second brain becomes useful.

Tip: You never need to touch Obsidian directly if you don't want to. Just give Claude Code access to the MD folder and input data — Claude Code will modify the folder and data appears in your Obsidian second brain automatically.

## Pro Tips

### Obsidian Chrome Extension
Use the Obsidian Chrome Extension to easily input data — click "add to Obsidian" on any data source. Then tell Claude Code: "Hey, I just input [x] into Obsidian; please ingest the data into my Wiki." Claude Code will make connections and links to other data sources.

### Separate Folders
Karpathy recommends two separate Vaults:
- One for business/work
- One for personal/goals

### Most Practical Use Case
Using the second brain to create more accurate mega prompts. With access to your entire life, business plans, writing context, etc., Claude Code can create far more curated and up-to-date prompts than you could manually.

### Orphans in Obsidian
"Orphans" show which data points lack connections to other notes. Useful for identifying ideas to build on or weak points in your database. Find it via the 3 dots menu.

## Potential Cons

1. **Not a visual person** — one main benefit is data visualization; if you don't benefit from that, this may not be for you.
2. **Maintenance** — without actually inputting data, the second brain is useless. Some maintenance required.
3. **Storage** — MD files take up device storage.

## Final Thoughts

As a thank you, grab the free cheatsheet at https://www.aiedgehq.co/

---

## Summary

AI Edge walks through building an AI second brain using Claude Code + Obsidian in 5 minutes, inspired by Karpathy's LLM Wiki pattern. The 4-part system: your data → Claude Code organizes it in Obsidian → instant prompting → evolving memory. Key insight: you never need to touch Obsidian directly — just give Claude Code access to the MD folder and input data; Claude Code writes to both. Karpathy recommends two separate vaults (work/personal). The most practical use case is using the accumulated context for far better mega prompts. Maintenance and storage are the main tradeoffs.

---

## Key Takeaways

1. **5-minute setup** — Obsidian vault + Claude Code folder access + Karpathy system prompt
2. **4-part system** — data → organization (by Claude Code) → instant prompting → evolving memory
3. **Claude Code writes to vault** — you never need to touch Obsidian directly if you don't want to
4. **Karpathy's system prompt** — the foundation: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
5. **Separate vaults** — work/business vs personal/goals recommended
6. **Chrome extension** — easy data input + Claude Code ingests and links
7. **Orphans feature** — flag data points with no connections
8. **Best practical use** — mega prompts with full life/business context
9. **Maintenance required** — second brain is useless without actual data input

---

## Hermes-Related Interest

This is exactly the architecture Hermes + OpenClaw are implementing. The 4-layer memory (built-in → Layer 2 files → Obsidian vault → session search) mirrors this system's progressive disclosure. The "Claude Code writes to vault, not just reads" pattern is key — Hermes should be checkpoint-writing to the vault autonomously, not waiting for user prompts. The orphan detection and wiki linting concept (from the llm-wiki skill) is the self-maintaining version of this system. This article validates the approach from a third independent source.
