# CONTENT RESEARCH SKILL

## Description

Use this skill when the user wants to research a topic for content — a blog post, a LinkedIn article, a newsletter issue, a video script, or any content that requires gathering information from multiple sources.

**Trigger:** Activate when the user says "research [topic]," "find sources on [topic]," "research brief for [content piece]," or when asked to "find what's being said about [topic]."

**What it produces:** A structured research brief saved to the user's vault, organized by theme, with source URLs and key data points pulled out.

---

## Instructions

### Step 1: Define the Research Goal

Ask (or use what the user has already provided):
- What content are you building this for? (blog post, newsletter, presentation, video)
- Who is the audience?
- What does success look like? (What should the reader/viewer take away?)

If the user has not specified these, use `AskUserQuestion` to clarify before proceeding.

### Step 2: Run Varied Searches

Do **at least 5 searches** using different angles:

1. **Trends and data** — What are the current numbers, growth rates, market size?
2. **Expert opinions** — What are respected voices saying? Any contrarian takes?
3. **Case studies** — Any real-world examples, specific implementations, documented results?
4. **Counterarguments** — What are the objections or criticisms? What doesn't work?
5. **Latest news** — Any recent developments, announcements, or shifts in the space?

Prioritize sources from 2025-2026. Flag any claims that rely on older data.

### Step 3: Review Against Success Criteria

- Compare your findings to the user's stated goal
- Identify gaps — areas where you couldn't find enough signal
- If gaps are critical, do 2-3 additional searches to fill them

### Step 4: Build the Research Brief

Save a structured brief to the user's vault. File name: `research-brief-[topic]-[date].md`

Structure:

```
# Research Brief: [TOPIC]
**Generated:** [Date] | **For:** [Content type] | **Audience:** [Who]
**Goal:** [What success looks like]

## Key Findings

### Theme 1: [Name]
- **Core point:** [One sentence summary]
- **Key data:** [Numbers, stats, specific claims — with source URLs]
- **Expert view:** [Quote or paraphrased insight with source]
- **Gaps/uncertainties:** [Flag anything thin or conflicting]

### Theme 2: [Name]
[same structure]

### Theme 3: [Name]
[same structure]

## Consensus View
[What most sources agree on — 2-3 sentences]

## Diverging Views
[Where experts disagree — and on what specific question]

## What's Missing / Needs More Research
[Any critical gaps that could affect the content]

## Source List
1. [Title](URL) — [One-line description of what this source adds]
2. [Title](URL) — [One-line description]
...
```

### Step 5: Deliver

- Confirm the brief is saved
- Summarize the top 3 most important findings in the chat
- Flag anything that might change the direction of the content

---

## Constraints

- Always prioritize 2025-2026 sources. Note when you're relying on older data.
- Flag where sources conflict or where data is thin. Do not paper over uncertainty.
- Do not write the content itself — this skill produces the research brief, not the final piece.
- If you can't find sufficient signal after 5+ searches, tell the user and recommend they provide source material directly.
- Never fabricate data, quotes, or sources. Verify everything you cite.

---

## Examples

**Good activation:**
User: "I need to write a blog post about AI agents for small businesses. Research brief please."
→ Skill activates, runs varied searches, builds structured brief, saves to vault.

**Bad activation:**
User: "summarize this article for me"
→ This is a summarization task, not research. Do not activate this skill.

---

## Author Notes

Built from the AI Agent Playbook framework.
For the slide deck version of this workflow, see the `slide-builder.md` skill.
