# Karpathy Built a Second Brain for Humans. Here's One for Your AI Agent.

**Source:** Paweł Huryn (@PawelHuryn) — AI PM, Deep Research, 130K+ subscribers at productcompass.pm  
**Date:** 2026-04-10  
**Link:** https://x.com/pawelhuryn/status/2041519394254176581  
**Views:** 15K | Likes: 108 | Reposts: 12  

---

## Full Article

**Karpathy Built a Second Brain for Humans. Here's One for Your AI Agent.**

The same architecture works for agents. And it compounds faster, because agents run every session, every day. His pattern: wiki/ + index.md + health checks. Plain markdown files. The LLM ingests sources, maintains cross-references, runs health checks. Human curates. No databases, no vector stores. Just files. One modification: you don't need Obsidian. Karpathy uses it because the human is the reader. When the agent is the reader, the interface disappears. Clean markdown files in context. That's it.

---

**Why agents need this**

Most people configure their agent by writing a CLAUDE.md with rules and tone preferences. Static config. Works for simple tasks. The problem: config decays. You write a rule in month one. By month three, you've learned three exceptions and the rule is wrong. Nobody updates it. The agent enforces a rule that lost its validity.

> "A knowledge system evolves. Hypotheses get tested. Rules graduate from evidence. Wrong beliefs get logged so the system doesn't repeat them. The agent loads only what it needs for the task at hand, not everything at once."

The result: an agent that gets better at your specific work over time. Not because you keep editing its instructions. Because the system has a mechanism for being wrong and correcting itself.

---

**Case study: X Content System**

Paweł has been building this system since February 2026. First publication — March 16, 2026. He started by pasting screenshots, asking "what makes this post work?" Raw, unstructured. But Claude started noticing patterns he missed — for example, data experiments get 3x more bookmarks than opinion posts.

Over weeks, the system grew. Claude suggested reorganizing files into a knowledge hierarchy. Then it suggested building a Python script to fetch tweet data cheaper. Then it started proposing edits to its own knowledge base.

Now the system has:
- 26 content templates
- 13 active hypotheses being tested with real data
- 50+ catalogued false beliefs (things conventional wisdom says hurt but data shows don't)
- 7 topic lanes with energy tracking
— all maintained by Claude, all improving with each use.

"I decide every editorial call — what to post, what to kill, what angle to take, which facts need checking twice. Claude handles research, verification, structural options, and pattern-matching against the knowledge base."

---

**The architecture**

Karpathy's layers translate directly:

Key files and directories:
- **CLAUDE.md** — holds the agent's identity, a routing table that maps task types to knowledge files, and step-by-step procedures for each task type
- **INDEX.md** — the master router loaded at every conversation start
- **hypotheses/** — where uncertain beliefs live until evidence promotes or kills them
- **rejected.md** — the graveyard: beliefs proven wrong, kept so the agent never re-tests them

This addresses four capabilities most agent setups are missing:
1. **perception** (what to load)
2. **reasoning** (how to route)
3. **learning** (hypotheses that graduate to rules)
4. **immunity** (rejected beliefs as institutional memory)

GitHub: https://github.com/phuryn/agent-second-brain

---

## Summary

Paweł extends Karpathy's human LLM-Wiki concept to AI agents themselves. Most agent configs are static and decay over time — rules written in month one become wrong by month three. The fix: a self-correcting knowledge system where beliefs live as hypotheses, get tested with evidence, and either graduate to rules or get logged as false. The architecture (CLAUDE.md + INDEX.md + hypotheses/ + rejected.md) gives agents perception, reasoning, learning, and immunity — making them improve over time through a mechanism, not manual edits. His case study: an X content system with 26 templates, 13 active hypotheses, and 50+ catalogued false beliefs, all maintained by Claude.

---

## Key Takeaways

1. **Static config decays** — rules written in month one are wrong by month three, but nobody updates them
2. **The fix: hypothesis-driven knowledge** — beliefs start as uncertain, get tested, graduate to rules or get logged as false
3. **Architecture:** CLAUDE.md (identity + routing + procedures) + INDEX.md (master router) + hypotheses/ (test beliefs) + rejected.md (graveyard of disproven beliefs)
4. **Four missing capabilities:** perception (what to load), reasoning (how to route), learning (hypotheses → rules), immunity (rejected beliefs as institutional memory)
5. **Compounding is faster for agents** — humans run the system occasionally; agents run every session, every day
6. **No Obsidian needed for agents** — when the agent is the reader, clean markdown files in context suffice
7. **Case study results:** 26 templates, 13 hypotheses, 50+ false beliefs catalogued, 7 topic lanes with energy tracking — all maintained by Claude

---

## Hermes-Related Interest

This is directly relevant to Hermes's skill and memory system. Hermes already has a skill-writing mechanism (every ~15 calls it writes skills from experience), but the hypotheses/rejected.md layer is new — a formal way to track what the agent got wrong and prevent re-testing. The article's four capabilities (perception, reasoning, learning, immunity) map well to Hermes's existing architecture: perception (what to load from vault), reasoning (skill routing), learning (skill-writing from checkpoints), immunity (rejected beliefs). This could inform how we structure the JB Vault wiki/ layer to support hypothesis tracking alongside the existing memory system.