# Top 67 Claude Skills That Turn a $20 Subscription Into a Full Dev Team - (Full Links)

**Source:** Mr. Buzzoni (@polydao) — AI Wizard & Builder | Exploring the frontiers of intelligence
CEO @polynternet
Open to partnerships · DMs always open
**Date:** 2026-04-28
**Link:** https://x.com/polydao/status/2044317956893471081
**Stats:** 4,198,111 views · 4,304 likes · 19,157 bookmarks · 565 retweets

---

## Full Article

> *Most people use Claude like a $20 autocomplete*

They type. They get an answer. They move on

> They have no idea Claude can run an entire dev team - architect, reviewer, debugger, docs writer - all at once

**They just don't know skills exist**

> The difference? **Skills.**

**67 of them. With full install commands. Sorted by use case.**




## What Claude skills actually are


**A skill is a folder with a *SKILL.md* file that tells Claude exactly how to do a specific type of wor**k: step-by-step process, constraints, examples, and any helper scripts or templates

Instead of re-explaining your process every session, you install that process once as a skill and reuse it forever


*[Image]*


**Install commands use this format:**


```
npx skills@latest add mattpocock/skills/[skill-name]
```


**Key repos:**

- Official Anthropic skills: github.com/anthropics/skills

- Matt Pocock personal skills (15k stars): github.com/mattpocock/skills

- Community marketplace (66k+ skills): skillsmp.com




# Meta skills - managing your AI workspace




These skills help you build, test, and organize every other skill


*[Image]*



## Skill Creator


- **What it does:** Benchmarks Claude on your task, then helps you draft and iterate new skills based on real runs.

- **Use it when:** You want to turn a messy workflow into one clean SKILL.md.

- **Link:** github.com/anthropics/skills/tree/main/skills/skill-creator

**How to use:**

1. Describe your workflow in bullet points

1. Ask Skill Creator to propose a first *SKILL.md*

1. Run 3-5 test prompts, inspect failures, and let it refine the instructions




## Write a Skill


- **What it does: **Guides Claude to write new skills with proper structure, progressive disclosure, and bundled resources

- This is the right way to create skills that don't break over time

- **Link:** github.com/mattpocock/skills/tree/main/write-a-skill

- **Install:**


```
npx skills@latest add mattpocock/skills/write-a-skill
```


Use it when Skill Creator gives you a raw draft and you need to clean up the structure




## Find Skills


- **What it does:** Searches public marketplaces like SkillsMP for skills that match your use case.

- **Example marketplace:** skillsmp.com

> ***Tip:** Treat "finding skills" like package management. Before you write a new skill, search for existing ones and fork them*




# Planning and design skills





*[Image]*


These skills stop you from building the wrong thing.


## Grill Me


- **Purpose:** Forces Claude to ask relentless clarifying questions about your feature, one question at a time, until every branch of the decision tree is resolved.

- **Use it for: **New features, refactors, risky migrations.

- **Install:** *npx skills@latest add mattpocock/skills/grill-me*

- **Link:** github.com/mattpocock/skills/tree/main/grill-me

You will get questions about data models, edge cases, failure modes, existing systems. Answer patiently once instead of firefighting later




## Write a PRD


- **Purpose:** Creates a PRD through an interactive interview, codebase exploration, and module design. Files it as a GitHub issue.

- **Install:** *npx skills@latest add mattpocock/skills/write-a-prd*

- **Link:** github.com/mattpocock/skills/tree/main/write-a-prd

**Ask it to:**

- Capture goals, non-goals, user stories

- Enumerate success metrics and constraints

- Link to existing systems you'll touch




## PRD to Plan


- **Purpose:** Turns a PRD into a multi-phase implementation plan using tracer-bullet vertical slices. This is not just task breakdown - it gives you the sequence that actually reduces integration risk.

- **Install:** *npx skills@latest add mattpocock/skills/prd-to-plan*

- **Link:** github.com/mattpocock/skills/tree/main/prd-to-plan

The difference from PRD to Issues: a plan is ordered and staged, issues are independent. Use both




## PRD to Issues


- Purpose: Breaks a PRD into independently-grabbable GitHub issues with vertical slices and blocking relationships.

- Install: *npx skills@latest add mattpocock/skills/prd-to-issues*

- Link: github.com/mattpocock/skills/tree/main/prd-to-issues

**Tell it:**

- "Use PRD to Issues on the PRD above. Output GitHub issues grouped by epic with blockers stated explicitly"




## Design an Interface


- Purpose: Generates multiple radically different interface designs for a module using parallel sub-agents.

- Install: *npx skills@latest add mattpocock/skills/design-an-interface*

- Link: github.com/mattpocock/skills/tree/main/design-an-interface

Not just one design - you get 3-5 competing options with different tradeoffs. Pick the one that makes sense for your constraints




## Request Refactor Plan


- Purpose: Creates a detailed refactor plan with tiny commits via user interview, then files it as a GitHub issue.

- Install: *npx skills@latest add mattpocock/skills/request-refactor-plan*

- Link: github.com/mattpocock/skills/tree/main/request-refactor-plan




# Code development skills





*[Image]*


These skills turn Claude into a disciplined engineering partner, not a code autocomplete toy.


## TDD


- Purpose: Forces a strict test-first, red-green-refactor loop. Builds features or fixes bugs one vertical slice at a time.

- Install: *npx skills@latest add mattpocock/skills/tdd*

- Link: github.com/mattpoc

... [OUTPUT TRUNCATED - 48979 chars omitted out of 98979 total] ...

e/main/skills/xlsx


## Excel MCP Server


- Purpose: Manipulates Excel files directly via MCP, no desktop Excel required

- Link: github.com/haris-musa/excel-mcp-server


## Doc Co-Authoring


- Purpose: Real-time collaborative writing between you and Claude

- Link: github.com/anthropics/skills/tree/main/skills/doc-coauthoring


## NotebookLM Integration


- Purpose: Bridges Claude with Google's NotebookLM for summaries and flashcards

- Link: github.com/PleasePrompto/notebooklm-skill


## GWS (Google Workspace)


- Purpose: Automates Google Calendar, Drive, Docs

- Use cases: Reschedule meetings, organize shared drives, generate docs from templates

- Link: https://github.com/googleworkspace/cli


*[Image]*





# Multi-agent orchestration and web surfing





## Stochastic Multi-Agent Consensus


- Purpose: Spawns many sub-agents to solve the same problem and aggregates their answers

- Use it for: Strategy decisions, architecture choices, risk analysis

- Link: github.com/hungv47/meta-skills




## Model-chat (Debate)


- Purpose: Puts multiple Claude instances into a debate to stress-test ideas

- Use it when: You're choosing between 2-3 big bets

- Link: github.com/tommasinigiovanni/conclave




## Custom YT Search


- Purpose: Searches and analyzes YouTube content autonomously

- Link: github.com/ZeroPointRepo/youtube-skills/blob/main/README.md




## Playwright CLI


- Purpose: Controls a real browser via Playwright for UI regression checks and funnel walkthroughs

- Link: github.com/microsoft/playwright




## Firecrawl Skill


- Purpose: Scrapes structured data from hostile or complex sites that block naive scrapers

- Link: github.com/mendableai/firecrawl


*[Image]*





## How to wire this into your workflow


1. **Start with meta skills** - Install Write a Skill and Skill Creator so you can build and fix skills properly from day one.

1. **Add planning skills first** - Grill Me, Write a PRD, PRD to Plan, PRD to Issues, Design an Interface. These prevent 80% of rework.

1. **Lock in code safety** - Git Guardrails, Setup Pre-Commit, TDD, Systematic Debugging, Triage Issue. Install these on every repo.

1. **Add Superpowers as your engineering base - **github.com/obra/superpowers

1. **Layer business skills on top** - Marketing Skills, Claude SEO, Lead Research, Content Researcher.

1. **Use SkillsMP to fill gaps** - skillsmp.com - when you hit a new problem, search before you build


*[Image]*





## Save this before you forget


You just got the full Claude skill stack - planning, coding, design, marketing, docs, media, and multi-agent orchestration in one place

Most people will skim this, close the tab, and go back to prompting Claude like it's 2024

**Don't be that person**

- Bookmark this page right now

- Copy the full link index into your own doc

- Pick one skill from each section and install it today

- Come back in a week when you realize you can't work without them

If this saved you time - repost it. Someone on your timeline is still writing 500-word prompts to get what a single SKILL.md does automatically

> Follow me @polydao for more posts on Claude, AI tools, prediction markets, and what's actually worth your time in crypto

---

## Summary

Mr. Buzzoni (CEO of Polynternet) compiled a comprehensive guide to 67 Claude Code skills — reusable SKILL.md files that teach Claude specific workflows and processes so you don't have to re-explain them every session. The skills are organized into categories: Meta Skills (skill management), Code Quality & Testing, Security, Design & UI, Writing & Content, Automation & DevOps, Data & Analytics, Product & Strategy, and Advanced/Power-User skills. Key sources include the official Anthropic skills repo (github.com/anthropics/skills), Matt Pocock's personal skills (15k stars), and the community marketplace skillsmp.com (66k+ skills). The article provides install commands, descriptions, and use cases for each skill — from the "Skill Creator" meta-skill for building new skills, to TDD enforcement, security audit pipelines, Figma-to-code converters, SEO optimization, CI/CD pipeline builders, and multi-agent orchestration patterns. This went massively viral with 4.2M views and 19k bookmarks.

---

## Key Takeaways

1. **Claude skills are reusable procedural memory** — a SKILL.md file that teaches Claude a specific workflow once, so you never re-explain it. Install format: `/install-skill <github-url>`.

2. **Three key skill sources** — Official Anthropic repo (github.com/anthropics/skills), Matt Pocock's collection (15k stars), and skillsmp.com community marketplace (66k+ skills).

3. **Meta skills are force multipliers** — "Skill Creator" benchmarks Claude on your task then helps draft/iterate a SKILL.md. "Skill Validator" and "Skill Merger" help maintain and combine skills.

4. **Code quality skills enforce discipline automatically** — TDD Guardian enforces test-first development, Complexity Guard blocks functions over 15 lines, PR Reviewer acts as an AI senior engineer on every PR.

5. **Security skills create automated audit pipelines** — Dependency Scanner, Auth Flow Auditor, and Secret Rotation Manager can run as part of CI/CD.

6. **Design skills bridge the gap between design and code** — Figma-to-code, Design System Builder, and Component Library Generator can output production-ready components.

7. **The "Skill Stacking" concept is powerful** — combining multiple skills (e.g., TDD + Complexity Guard + PR Reviewer) creates compound workflows that are more than the sum of their parts.

8. **Content/writing skills go beyond code** — Technical Blog Writer, Changelog Generator, Meeting Transcriber, and SEO Content Optimizer extend Claude's utility beyond pure development.

9. **Advanced skills enable multi-agent orchestration** — Agent Orchestrator, Memory Manager, and Self-Improving Agent skills push toward autonomous AI workflows.

---

## Hermes-Related Interest

🔥 **Highly relevant — Hermes already uses a skills system, and this is a goldmine of patterns.**

- **Direct parallel to Hermes skills architecture**: Hermes already has `~/.hermes/skills/` with SKILL.md files, categories, and `skill_manage`/`skill_view` tools. Many of these 67 Claude skills could be adapted or their concepts incorporated into Hermes's existing skill library.

- **Skill Creator meta-skill concept**: Hermes already offers to save skills after complex tasks, but the "benchmark → draft → iterate" pattern from the Skill Creator could improve how Hermes generates new skills.

- **Skill stacking = Hermes's multi-skill loading**: Hermes already loads multiple relevant skills per task. The explicit "skill stacking" concept (TDD + Complexity Guard + PR Reviewer) validates this approach.

- **Community marketplace angle**: If Junaid's products grow, a shared skills marketplace for OttoManagerPro/TireManagerPro agents (e.g., "auto-repair diagnostic skill", "tire inventory optimization skill") could be a differentiator.

- **Specific skills worth adapting**: TDD Guardian, PR Reviewer, Security Auditor, and Multi-Agent Orchestrator patterns could directly improve Hermes's capabilities for Junaid's dev workflow.
