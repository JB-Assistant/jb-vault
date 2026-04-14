# SLIDE BUILDER SKILL

## Description

Use this skill when the user wants to build a presentation — for a client, a team, a board, or any audience. This skill runs the full pipeline: research → brief → outline → generate.

**Trigger:** Activate when the user says "build slides for [topic]," "create a presentation about [topic]," "make a deck on [topic]," or "I need a PowerPoint."

**What it produces:** A Gamma presentation (or .pptx if preferred) generated from structured research and a slide outline.

---

## Overview of the Pipeline

This skill has 4 stages:

1. **Research** → Structured brief saved to vault
2. **Brief** → Gamma-ready slide outline saved to vault
3. **Generate** → Agent passes outline to Gamma (or generates .pptx)
4. **Review** → User reviews in Gamma and edits

---

## Stage 1: Research

Follow the same process as the `content-research.md` skill.

**Prompt the user:**
> "I'm building a presentation. Do not generate slides yet. Research [topic] for [success criteria] so I have everything I need to build a presentation about it.
> 1. Read all the files in this folder. [If the user has dropped source material into a folder]
> 2. Search the web using at least 5 varied searches (trends, data, expert opinions, case studies, counterarguments).
> 3. Review findings against the success criteria. Identify gaps. Search again to fill them.
> 4. Save a structured research brief to `research-brief.md` — organized by theme, with source URLs and key data points pulled out. Prioritize 2025-2026 sources. Flag anything where sources conflict or data is thin."

**Ask clarifying questions** (via `AskUserQuestion`) if the audience, goal, or success criteria are unclear.

**Output:** `research-brief.md` saved to the user's vault.

---

## Stage 2: Brief

Once the research brief is ready, prompt:

> "Read `research-brief.md` and turn it into a presentation outline.
> Presentation goal: [what the presentation should accomplish]
> Audience: [who's watching]
> 1. Write a slide-by-slide outline. Each slide gets: a title, 2-3 key points, and any specific data/stats from the research that must appear on that slide.
> 2. Keep it to [X] slides max.
> 3. Do not write full paragraphs — the presentation tool will generate the final text. Just give it enough structure and data to work with.
> 4. Save the outline to `gamma-outline.md`.
> 5. If using Gamma: pass the outline to Gamma as a presentation using the textMode "generate" command."

**Output:** `gamma-outline.md` saved to the user's vault.

---

## Stage 3: Generate

**If using Gamma:**
Pass the outline to Gamma via the Gamma Connector inside Claude Cowork. The agent should use the connector to generate the presentation directly.

**If using PowerPoint (.pptx):**
Generate the .pptx file directly and save it to the user's vault. Use the slide outline as the content layer — title, bullet points, and data per slide.

**Output:** A Gamma share link or a .pptx file saved to the vault.

---

## Stage 4: Review

Tell the user:

> "The presentation is ready. Here's what to do next:
> 1. Open [Gamma link or .pptx file]
> 2. Go through it card by card:
>    - Would I say this out loud? Rewrite if I wouldn't.
>    - Does this slide earn its place? Cut it if it doesn't.
>    - Is the data right? Verify it.
> 3. 10-15 minutes of editing. The hard part already happened in the research."

---

## Constraints

- **Never skip the research stage.** A presentation with beautiful slides and no substance is worse than no presentation. If the user asks to skip research, remind them that Gamma's design is only as smart as the brief it starts from.
- If the user hasn't connected Gamma, generate a .pptx instead. Don't let missing tools stop the workflow.
- Keep the outline to the requested slide count. If the research has enough for 20 slides but the user asked for 10, prioritize the strongest themes.
- Flag any critical data that couldn't be verified in the research — don't let thin data onto a slide without a flag.
- Do not write full paragraph content for slides at the outline stage. The value of Gamma is in its design + its ability to generate. Give it structure, not prose.

---

## Slide Count Guidance

| Audience | Recommended Slides | Tone |
|---|---|---|
| Team sync / internal | 5-8 | Direct, bullet-heavy |
| Client presentation | 10-15 | Structured, data-backed |
| Board / investor | 12-18 | Narrative arc, metrics front-loaded |
| Conference / public | 20-30 | Story-driven, visual |

---

## Examples

**Good activation:**
User: "I have a board meeting in 2 weeks. I need a deck on our competitive position. Let me drop some files in a folder first."
→ Skill activates, reads files, researches, builds outline, generates in Gamma. User reviews.

**Bad activation:**
User: "make me a 5-slide deck on why our product is great"
→ Do not generate slides without research. Activate the research stage first, even if abbreviated.

---

## Author Notes

Built from the AI Agent Playbook framework.
Requires: Google Drive connection (for source files), web search access, and Gamma connector (optional but recommended).
For research-only tasks, use the `content-research.md` skill instead.
