# How to QUICKLY Set Up Claude Cowork (The Right Way)

**Author:** Corey Ganim (@coreyganim)
**Source:** X/Twitter
**Link:** https://x.com/coreyganim/status/2043695225697124478
**Date:** April 2026
**Tags:** #AI #Claude #Cowork #Setup #Workflow

---

## Summary

Corey Ganim's step-by-step guide to setting up Claude Cowork properly — turning it from a novelty into something you rely on daily. 26K views, 200 bookmarks.

> "Most people download Claude Desktop, open Cowork, ask it to organize their Google Drive, and get frustrated when the output is generic. That's an onboarding problem, not a problem with Cowork itself."

---

## Step 1: Connect Your Tools Before You Type a Single Prompt

Open Claude Desktop → Connectors. Connect everything you use daily:

- **Google Workspace** (Drive, Gmail, Calendar) — non-negotiable, most business context lives here
- **Slack or Teams** — if your team communicates there, Claude needs access
- **Notion, Asana, Linear, Monday** — wherever projects/docs live
- **Zoom** — new as of April 2026, can pull meeting context and recordings

**Why first:** When you build context files in Step 2, Claude can pull from existing docs instead of you typing everything. Quick test: ask Claude to find a recent document in Drive. If it finds it, move on.

---

## Step 2: Build Three Context Files (Let Claude Do Most of the Work)

Context files load automatically every session — how Claude knows who you are without re-explaining.

### File 1: about-me.md
Cover in plain language:
- What you do (one sentence)
- What businesses/projects you're running
- Who your customers are
- What tools you use daily
- Key people Claude should know (co-founder, assistant, key clients)

**Shortcut:** If you connected Google Drive, tell Claude to scan existing docs for company info, bios, about pages. It will draft 80% for you.

### File 2: voice.md
How Claude stops sounding like a robot:
- Your communication style (direct? warm? conversational?)
- Words/phrases you hate ("synergy" makes you cringe? say so)
- How you communicate differently by context (client emails vs. team Slack vs. social)
- 2-3 writing samples that sound like you

**Tip:** Paste actual writing. A good email you sent. A social post that performed. Claude reverse-engineers patterns better than any style guide.

### File 3: preferences.md
Tell Claude how to work with you:
- Ask clarifying questions or just execute?
- Default output format? (bullet points, paragraphs, tables)
- How detailed should first drafts be?
- Any hard rules? ("Never use em dashes." "Always include pricing." "Keep responses under 300 words.")

**Save:** All three in one folder. Select this folder at the start of every Cowork session.

---

## Step 3: Set Global Instructions (Your Always-On Brief)

Global instructions run in every session, even before you select a folder — your executive brief Claude reads before doing anything.

**Condense key points from the 3 context files into ~800 words:**

1. Who I am (2-3 sentences)
2. How I work (preferences for task approach and communication)
3. Output defaults (format by task type: emails → bullets, content → paragraphs, research → tables)
4. Voice (3-4 most important characteristics)
5. Key business context (what I'm working on right now, what matters most)
6. Rules (always do X, never do Y)

**Activate:** Claude Desktop → Settings → Cowork → Edit next to Global Instructions → paste → save

---

## Step 4: Install 3-5 Skills That Match Your Actual Work

Skills turn Claude from a general assistant into a specialist. Without skills, Claude can chat. With skills, it can:

- Research and profile potential partners or podcast guests
- Draft content that matches your voice and format preferences
- Prep for meetings by scanning attendee backgrounds
- Process data and generate reports from connected tools
- Run multi-step workflows end to end

---

## Hermes Angle

This setup process is highly relevant to Hermes:
- **Context files** (about-me, voice, preferences) = similar to Hermes Layer 2/3 memory (Agents.md, Soul.md, vault)
- **Global Instructions** = analogous to Hermes system prompt / personality config
- **Skills** = the skill system in Hermes is exactly this concept
- The "connect tools first" philosophy aligns with Hermes tool integrations (MCP, etc.)
- Voice/profile reverse-engineering from writing samples → could be an interesting Hermes skill

---

## Source

> "PS: Every week I break down workflows like this inside the Build With AI newsletter. Agents, automations, and step-by-step setups you can run yourself or sell to clients."
> — Corey Ganim
