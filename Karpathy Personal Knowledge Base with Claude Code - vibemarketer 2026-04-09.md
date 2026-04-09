# Karpathy Personal Knowledge Base with Claude Code

**Source:** @vibemarketer_  
**Date:** 2026-04-09  
**Link:** https://x.com/vibemarketer_/status/2042226854271099342

---

## Full Article

Andrej Karpathy just showed everyone how to build a personal knowledge base with Claude Code and markdown files. Here's the exact setup so you can do it in 5 minutes.

The core idea is simple: you dump raw sources into a folder — articles, transcripts, PDFs, meeting notes — and Claude Code reads everything, creates wiki pages, and builds relationships between them automatically. You don't tag anything. You don't organize anything. The LLM figures out the structure on its own.

Your vault looks like this:
- `raw/` → where you drop sources
- `wiki/` → where Claude Code puts organized output
- `index.md` → maps everything
- `log.md` → tracks updates
- `claude.md` → tells Claude Code how the project works

The LLM finds info by reading indexes and following links. Not similarity search. Actual structured relationships between concepts.

**Why this actually matters:**

Every time you close a conversation with an LLM, the context dies. That research you did last Tuesday? Gone. The strategy you worked through for 45 minutes? You'd have to rebuild it from scratch.

Most people treat AI like a search engine — ask a question, get an answer, move on. But the people getting disproportionate value from these tools are the ones who figured out how to make knowledge persist between sessions.

That's what this is. A system where every article you read, every meeting you take, every research rabbit hole you go down gets absorbed into a structured wiki that your LLM can reference any time.

And it compounds. Article one creates 10 wiki pages. Article two creates 12 more, but now some of those pages link back to concepts from article one. By article twenty, you've got a dense web of relationships that surfaces insights you'd never find by searching your notes manually.

**How to set it up:**

1. Download Obsidian from obsidian.md (free — optional but the graph view is worth it)
2. Create a new vault and open the folder in your terminal
3. Fire up Claude Code
4. Grab Karpathy's gist: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
5. Paste the full gist into Claude Code and add: "you are my LLM wiki agent. implement this as my complete second brain. create the folder structure, the claude.md schema, and prep everything for source ingestion."
6. Claude Code builds the raw/, wiki/, index, and log structure for you
7. Drop your first source into raw/ and say "ingest this"
8. That's it — Claude Code reads the source, creates wiki pages for key concepts, people, organizations, and themes, then wires up relationships between them automatically

**The knowledge base as a layer:**

Your knowledge base becomes a layer other tools can read. You can point any Claude Code project at your wiki folder. An executive assistant project that needs context about your business? It reads the wiki. A content strategy project that needs to reference your past research? It reads the wiki. You build the knowledge once and every AI workflow you run gets smarter.

**Relationships > Search:**

This is the key difference between this approach and traditional RAG. RAG finds chunks that seem similar to your query. The wiki approach follows actual structured links between concepts. When you ask a question, the LLM traces the connections between ideas rather than just pattern matching on keywords. Deeper answers, better context.

The tradeoff is scale. This works beautifully up to hundreds of pages with good indexes. If you're dealing with millions of documents at an enterprise level, you still need a proper RAG pipeline with embeddings and a vector database.

But for personal research? A second brain? A small team's knowledge hub? The wiki approach handles it and the cost is essentially just tokens.

Karpathy himself said he thought he'd need fancy RAG. At ~100 articles and 500k words, well-maintained markdown indexes just work.

---

## Summary

This article describes Andrej Karpathy's system for building a personal knowledge base using Claude Code and Obsidian. The approach replaces traditional note-taking with an LLM-driven wiki: drop raw sources (articles, PDFs, meeting notes) into a folder, and Claude Code automatically creates structured wiki pages, maps relationships between concepts, and builds indexes. The key insight is that persistence between LLM sessions is the real value — instead of rebuilding context from scratch every conversation, your knowledge compounds into a navigable web of ideas. For personal use at scale (hundreds of pages), structured wikis outperform RAG because they follow actual concept relationships rather than keyword similarity.

---

## Key Takeaways

1. **LLM-first knowledge management** — Don't organize manually; let the LLM structure your notes by creating wiki pages and wiring up relationships automatically.
2. **Vault structure is simple** — raw/ (sources), wiki/ (organized output), index.md (map), log.md (changelog), claude.md (agent instructions).
3. **Knowledge compounds** — Each new source adds pages that link back to existing concepts, building a denser web of relationships over time.
4. **Relationships > RAG for personal use** — Structured wiki links beat similarity search because the LLM traces actual conceptual connections, not keyword matches.
5. **Works at human scale** — Karpathy runs ~100 articles / 500k words on well-maintained markdown indexes. Enterprise-scale still needs vector databases.
6. **One knowledge base, many AI workflows** — Build it once, reference it from any Claude Code project (assistant, content strategy, research, etc.).

---

## Hermes-Related Interest

This is directly relevant to Hermes's article workflow. Currently articles go to Obsidian with summary + takeaways, but this approach suggests a richer model: instead of a single summary note per article, ingest the full source into a `raw/` folder and let Claude Code build out wiki pages for entities, concepts, and themes across articles. This would create a compounding knowledge graph rather than isolated per-article notes. The article-summarizer skill could evolve to support both modes: "save as summary" (current) and "ingest as wiki" (full wiki-style relationship building).
