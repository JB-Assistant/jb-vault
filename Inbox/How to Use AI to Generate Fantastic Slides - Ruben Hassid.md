# How to Use AI to Generate (Fantastic) Slides

**Author:** Ruben Hassid (@rubenhassid)
**Source:** X/Twitter
**Link:** https://x.com/rubenhassid/status/2030979882361008547
**Date:** March 2026
**Tags:** #AI #Slides #Presentations #Gamma #Claude #Workflow #Productivity

---

## Summary

Ruben Hassid's tested guide on 3 methods for AI slide generation, with a recommended workflow that combines Claude (research + thinking) and Gamma (design). **1.2M views**, 1,307 likes, 3,601 bookmarks. The key insight: Claude writes and structures well, but the visual side stays basic. Gamma makes things beautiful but content is only as smart as your prompt. Best approach = Claude + Gamma.

---

## Method 1: Claude Alone — Grade: 3/10

**Best for:** extreme speed, zero-effort design, internal team syncs

**How:**
1. Open Claude Cowork. Select your folder.
2. Prompt: "I need a 10-slide PowerPoint (.pptx) about [TOPIC] for [SUCCESS CRITERIA]. Start by using the tool AskUserQuestion, and ask enough context to get the full context. Then, and only then, create a .pptx."
3. Claude creates a .pptx in your folder. Open and edit.

**Also:** Claude add-in in PowerPoint (Insert > Get Add-ins > search "Claude by Anthropic") — edits slides directly from right sidebar.

**Catch:** Writes and structures well, has great research capabilities, but visual side stays basic. Too flat for client meetings. **Grade: 3/10**

---

## Method 2: Gamma Alone — Grade: 8/10

**Best for:** fast decks that look polished, explainers, when speed + design matter

**How:**
1. Go to gamma.app. Free account, no credit card.
2. Click "Create new" → "Generate."
3. Type your topic and success criteria (who is it for? why?).
4. Gamma shows an outline. Tweak it. Pick a theme. Hit generate.
5. 60 seconds. Done.

**What Gamma does well:**
- Beautiful layouts, spacing, typography — automatically
- AI-generated images from 20+ models
- Shareable web link with view analytics (who opened it, scroll depth, time spent)
- Export to PowerPoint, PDF, or Google Slides
- 70M users, 400M presentations. Free to start. Plus $8/month, Pro $15/month

**Catch:** Design is great. Content is only as smart as your one-line prompt. Vague prompt = pretty slides that say nothing. **Grade: 8/10**

---

## Method 3: Claude + Gamma (Recommended) — Grade: 10/10

**Best for:** anything that matters. Client decks. Board presentations. Strategy decks.

The insight: **Claude thinks. Gamma designs. You decide.**

### Fast way (not recommended):
Connect Gamma to Claude via Connectors and prompt Gamma inside Claude. Works but not optimal.

### Recommended workflow: Research → Brief → Generate

**Step 1 — Research**

Open Claude Cowork. Prompt:
> "I'm building a presentation. Do not generate slides yet. Research [topic] for [success criteria] so I have everything I need to build a presentation about it.
> 1. Read all the files in this folder.
> 2. Search the web using at least 5 varied searches (trends, data, expert opinions, case studies, counterarguments).
> 3. Review findings against the success criteria. Identify gaps. Search again to fill them.
> 4. Save a structured research brief to research-brief.md — organized by theme, with source URLs and key data points pulled out. Prioritize 2025-2026 sources. Flag anything where sources conflict or data is thin.
> Start by using AskUserQuestion to make sure you research the right information once you have enough context from me."

(Only include step 1 if you've dropped source material into the folder.)

**Step 2 — Brief**

Follow up with Claude:
> "Read research-brief.md and turn it into a Gamma-ready presentation outline.
> Presentation goal: [what it should accomplish]
> Audience: [who's watching]
> 1. Write a slide-by-slide outline. Each slide gets: a title, 2-3 key points, and any specific data/stats from the research that must appear on that slide.
> 2. Keep it to [X] slides max.
> 3. Do not write full paragraphs — Gamma will generate the final text. Just give it enough structure and data to work with.
> 4. Save the outline to gamma-outline.md.
> 5. Then pass the outline to Gamma as a presentation using textMode "generate"."

**Step 3 — Generate**

Claude passes the outline to Gamma. Gamma creates the presentation using Claude's research.

**Step 4 — Edit**

Open the Gamma link. Go card by card:
- Would I say this out loud? Rewrite if I wouldn't.
- Does this card earn its place? Cut it if it doesn't.
- Is the data right? Verify it.

10-15 minutes. The hard part already happened in Claude.

---

## Hermes Angle

- The **Claude + Gamma workflow** is essentially what Hermes skills do — Claude as the reasoning/research layer, Gamma as the output/presentation layer
- The research prompt structure (multi-search, gap analysis, structured brief) maps directly to how Hermes could approach research tasks
- The "Claude thinks, Gamma designs" split is a good mental model for task delegation: reasoning vs. presentation
- This workflow could be a Hermes skill: "presentation-builder" that takes a topic + audience and runs the full Research → Brief → Generate pipeline

---

## Source

> "It's 2026, so you better not make your slides manually. AI does it for you."
> — Ruben Hassid
