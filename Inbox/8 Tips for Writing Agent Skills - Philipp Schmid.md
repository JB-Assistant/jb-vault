# 8 Tips for Writing Agent Skills

**Author:** Philipp Schmid (@_philschmid)
**Source:** X/Twitter
**Link:** https://x.com/_philschmid/status/2043705157850951699
**Date:** April 2026 (from tweet ID 2043705157850951699)
**Tags:** #AI #Agents #Skills #Hermes #AI-agents

---

## Summary

Philipp Schmid shares 8 hard-won tips for writing effective agent skills — the reusable extension points used across AI agents like Claude Code. Skills are powerful but easy to get wrong; this thread distills what makes the difference.

---

## Key Takeaways

### 1. Know What a Skill Is
- A skill = a folder with `SKILL.md` (required) + optional `scripts/`, `references/`, `assets/`
- **3 layers:** name+description (frontmatter), body instructions, optional assets
- **2 types:**
  - **Capability skills** —弥补 base model gaps (may become obsolete as models improve)
  - **Preference skills** — encode your workflow (durable but must stay in sync)

### 2. Nail the Description
- Description = trigger mechanism. Vague = no firing. Too broad = constant firing.
- Must include both **what** it does AND **when** to use it
- Tip: improving descriptions has yielded 50% performance improvements

### 3. Write Instructions, Not Essays
- Longer context actually hurts performance
- Use directives: "Always use X" beats "The recommended approach is X"
- Lead with examples: 5-line code snippet > 5-paragraph explanation
- Explain the **why**: helps agent generalize, not just memorize
- Don't overfit to your 3 test prompts

### 4. Keep It Lean
- Layered loading: frontmatter always, body when triggered, refs/scripts on demand
- Split topics into separate reference files — agent only reads what's needed
- If a reference file > 500 lines, add a table of contents with line hints

### 5. Set the Right Level of Freedom
- Don't write step-by-step workflows — you remove the agent's ability to adapt/recover
- Describe **what** to achieve, not the path to get there
- Provide **constraints**, not procedures
- If exact steps matter → write a script, not a skill

### 6. Don't Skip Negative Cases
- Think about when the skill should **NOT** fire
- "Use for any coding task" will hijack every request

### 7. Test Across Diverse Inputs
- Skills that only work for your specific 3 test prompts = overfitted
- Write skills that work across millions of invocations

### 8. Version and Audit Skills Regularly
- Preference skills drift from reality if processes change
- Capability skills become obsolete as models improve

---

## Hermes Angle

This is directly relevant to Hermes:
- **Hermes skills system** uses the same `SKILL.md` structure
- Tips 1-5 map directly to how Hermes skills work (frontmatter triggers, layered loading, scripts/references)
- Tip 5 on "right level of freedom" is especially relevant — Hermes skill instructions should describe goals, not dictate procedures
- The 50% improvement from better descriptions is a strong signal to review Hermes skill descriptions

---

## Source

> Skills have become one of the most used extension points in agents. They're flexible, easy to make, and simple to distribute. But this flexibility also makes it hard to know what good and what works.
> — Philipp Schmid
