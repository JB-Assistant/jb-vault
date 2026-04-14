# CLIENT BRIEF SKILL

## Description

Use this skill when the user needs to turn a topic, request, or raw brief into a structured, client-ready document — a formal brief, a strategy outline, a project scope, or a proposal foundation.

**Trigger:** Activate when the user says "brief for [project]," "create a brief for [client]," "scope this out," "turn this into a [document type]," or when asked to "prepare a [proposal/strategy/brief]."

**What it produces:** A structured brief that can be handed to a client or used as the foundation for a formal proposal.

---

## Instructions

### Step 1: Clarify the Ask

If the user has given you raw input (an email, a messy description, a voice note), first make sure you understand:

- **Who is this for?** (Client name, industry, company size)
- **What do they need?** (The actual deliverable — a strategy, a design, a report, a plan)
- **What does success look like?** (What does good look like for them specifically?)
- **What's the timeline?** (When is it due? Is there flexibility?)
- **What's the budget or scope?** (If known — if not, flag it)

Use `AskUserQuestion` to fill gaps if the user hasn't provided these details.

### Step 2: Read Existing Context

Before generating anything:
- Check the user's vault for any relevant previous work, client notes, or templates
- Check the user's `about-me.md` and `preferences.md` if available — understand their voice and working style
- If source documents are in a connected folder, read them first

### Step 3: Build the Brief

Use this structure:

```
# [Project Title] — Client Brief
**Client:** [Name] | **Prepared by:** [Your name] | **Date:** [Date]
**Deadline:** [Date or "TBD"]

## Situation
[2-3 sentences on where the client is now and what brought them here]

## Problem or Opportunity
[What the client has identified as the issue, need, or opportunity]
[If the brief came from an email or conversation, pull the actual language they used]

## Objectives
[What success looks like — be specific and measurable if possible]
1. [Objective 1]
2. [Objective 2]
3. [Objective 3 — optional]

## Constraints
[Any known limitations — budget, timeline, internal politics, technical limits]

## Key Stakeholders
- **[Name]:** [Role and their specific concern or interest in this project]
- **[Name]:** [Same]

## Proposed Approach
[Your recommended approach — 3-5 sentences on how to solve this]
[If the user has a preferred methodology or framework, reference it here]

## Deliverables
- [Deliverable 1 — what it is, in what format, by when]
- [Deliverable 2]

## Open Questions
- [Question 1 — something that needs client input before finalizing]
- [Question 2]

## Next Steps
1. [Immediate next step]
2. [What happens after]
3. [How this leads to a formal proposal]

---

## Internal Notes
[Anything from the user's context files that should inform this brief but shouldn't go directly to the client]
```

### Step 4: Deliver

- Save the brief to the user's vault with filename: `brief-[client]-[short-title]-[date].md`
- Display the brief in the chat
- Ask the user: "Does this capture what you need, or should we adjust before you send it to the client?"

---

## Constraints

- Do not pad or add fluff. Write in the user's voice (check `voice.md` if available).
- Do not commit to specific timelines, deliverables, or pricing unless the user has explicitly provided those.
- Flag where the client brief has gaps — don't fill in unknowns with assumptions.
- If the "client" is internal (the user's own team), adapt the format to be more direct — less formal, more action-oriented.
- This brief is a foundation, not the final proposal. Do not over-engineer it at this stage.

---

## Examples

**Good activation:**
User: "I just got off a call with a prospect who wants help with their content strategy. Can you brief this out before I send a proposal?"
→ Skill activates, pulls context, asks clarifying questions, produces structured brief.

**Bad activation:**
User: "can you proofread this email for me"
→ Proofreading is not a brief. Do not activate this skill.

---

## Author Notes

Built from the AI Agent Playbook framework.
The output of this skill feeds directly into proposals, scopes of work, and project plans.
