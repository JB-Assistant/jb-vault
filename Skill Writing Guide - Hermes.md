# Hermes Skill Writing Guide

This guide distills best practices for writing effective Hermes skills, based on the patterns identified in [[The Anatomy of a Perfect Skill - darkzodchi 2026-04-27]]. Following these patterns will improve skill invocation rates, output consistency, and overall agent performance.

## Quick-Reference Checklist (Fixing Broken Skills)

Before deploying or auditing a skill, run through this checklist:

1.  **Description:** Does it have at least 3 trigger keywords?
2.  **Description:** Is the use case and "when to trigger" context in the first 250 characters?
3.  **Instructions:** Are they imperative verbs in numbered steps?
4.  **Output:** Is the output format specified explicitly?
5.  **Project Awareness:** Does it include a "read first" step to inspect existing files/code?
6.  **Scope:** Does it clearly list what the skill does NOT do (Out of Scope)?
7.  **Length:** Is the primary `SKILL.md` under 500 lines? (Use progressive disclosure for longer skills).

## SKILL.md Template Skeleton

```markdown
---
name: <your_skill_name>
description: |
  <Describe WHAT the skill does AND WHEN to trigger it.>
  Use when [use case 1], [use case 2]. Listen for keywords like "[keyword1]", "[keyword2]".
  Front-load the most important context within the first 250 characters.
---

## Purpose
Provide a concise, high-level overview of the skill's main function.

## Process / Instructions
Use imperative verbs and numbered steps for clarity.

1.  **Read First:**
    *   Examine existing files in the current directory relevant to the task. (e.g., `git status`, `git diff`, check relevant config files).
    *   Identify [project-specific context, e.g., coding language, framework, existing patterns].
    *   Determine the exact scope of the current request.

2.  **Core Logic:**
    *   [Directive step 1]
    *   [Directive step 2]
    *   ...

3.  **Output Formatting:**
    *   Generate the output in the following explicit format:
    *   ```
    *   <Example of required output format>
    *   Type: [feat|fix|chore|docs|refactor|test]
    *   Scope: <affected module/component>
    *   Subject: <short description, less than 50 chars, present tense>
    *
    *   - Body: <detailed explanation of the change>
    *   - Why: <reason for the change, if not obvious>
    *   ```
    *   Ensure all constraints are met (e.g., character limits, keyword requirements).

4.  **Final Action:**
    *   [e.g., Stage changes with `git add` and commit with `git commit`, Present summary, etc.]

## Rules & Constraints
*   [Rule 1: e.g., Type must be one of: feat, fix, refactor, docs, test, chore]
*   [Rule 2: e.g., Subject must be under 50 characters.]
*   [Rule 3: e.g., Bullet points should be concise.]

## Out of Scope
This skill does NOT:
*   [Action the skill does not perform, e.g., Push to remote]
*   [Action the skill does not perform, e.g., Create Pull Requests]
*   [Action the skill does not perform, e.g., Handle binary files]

## Progressive Disclosure
For advanced functionalities or different contexts, refer to:
*   See [[ADVANCED_PATTERNS.md]] for complex scenarios.
*   See [[REFERENCE.md]] for full API details.
*   See [[EXAMPLES.md]] for more practical examples.
```

## What Kills Skills (Anti-Patterns)

Avoid these common pitfalls that lead to ineffective skills:

**Description Failures:**
*   Under 50 characters, lacking context.
*   Vague, not specifying *when* to trigger.
*   Missing trigger keywords.
*   Inconsistent point of view ("I help" vs. "Use this for...").

**Content Failures:**
*   Conversational or question-based instructions.
*   No explicit output format specified.
*   Missing a "read first" step for project context.
*   Lacking an "Out of Scope" section.
*   Exceeding 500 lines in `SKILL.md` (leading to context loss).

**Design Failures:**
*   Trying to accomplish too many distinct tasks in one skill.
*   Hardcoded to a specific project, lacking generalizability.
*   No versioning or clear update strategy.
*   Never updated or iterated upon.

## Related Resources
*   [[The Anatomy of a Perfect Skill - darkzodchi 2026-04-27]]
*   [[How to Build a One-Person Services-as-Software Company - Alex Vacca - 2026-04-27]]

## Hermes-Specific Application

These patterns directly inform how Hermes skills are written and how the `skill_view()` and `skill_manage()` functions process them for routing and execution:

*   **Description Matching:** Hermes heavily relies on the skill description to match user intent. A well-crafted description (Pattern 1) with clear use cases and keywords is crucial for automatic invocation. Vague descriptions mean the skill will rarely be chosen.
*   **Directive & Formatting:** Hermes executes structured, imperative instructions reliably. Explicit output formats (Pattern 3 & 2) ensure that the results are consistent and usable by subsequent tools or agent steps.
*   **Progressive Disclosure:** Hermes supports `linked_files` within a skill's directory. This aligns perfectly with Pattern 6, allowing for complex skills to be broken down into smaller, manageable Markdown files that are loaded only when needed, keeping the primary `SKILL.md` concise.
*   **Contextual Awareness:** The "read first" step (Pattern 4) is vital for Hermes when interacting with a project. It instructs the agent to gather necessary context before acting, preventing generic outputs and errors.
*   **Scope Management:** Clearly defining "Out of Scope" (Pattern 5) helps Hermes avoid attempting actions it cannot perform, leading to more predictable behavior and fewer failed tasks.

By adhering to these 6 patterns, you will create more robust, reliable, and discoverable skills for the Hermes agent.
