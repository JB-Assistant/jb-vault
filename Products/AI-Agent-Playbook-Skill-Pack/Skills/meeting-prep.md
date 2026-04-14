# MEETING PREP SKILL

## Description

Use this skill whenever you need to prepare for a meeting — before every calendar event, before a call with a new contact, before a client session, or when asked to "prep for" any meeting.

**Trigger:** Activate when the user says "prep for meeting," "meeting prep," "brief me for [meeting/event]," or when a calendar event is approaching.

**What it produces:** A one-page briefing with talking points, context on attendees, and follow-up items from any previous interactions.

---

## Instructions

When this skill activates, do the following in order:

### Step 1: Pull Calendar and Attendee Context

- Check the user's calendar for the upcoming meeting (via connected Google Calendar)
- Identify all attendees
- For each attendee, pull whatever context is available:
  - From connected CRM (notes, history, past interactions)
  - From email (recent exchanges, attachments shared)
  - From the user's vault or notes folder (previous meeting notes, context files)
  - From LinkedIn or web (if it's a new contact — brief professional background)

### Step 2: Build the Briefing

Create a structured briefing document. Use this exact structure:

```
# Meeting Prep: [MEETING TITLE]
**Date:** [Date] | **Time:** [Time]
**Attendees:** [List with one-line descriptions]

## Context
[2-3 sentences on what this meeting is about based on the calendar invite and your research]

## Talking Points
- [Point 1 — something the user wants to cover]
- [Point 2 — something the attendee might care about based on their background]
- [Point 3 — a question to ask or an insight to share]

## Attendee Backgrounds
**[Name]:** [One sentence on their role and why they're in this meeting]
**[Name]:** [Same]

## Previous Interactions
[If there's history: last time you met, what was discussed, any outstanding items]

## Questions to Ask
- [A question you want answered]
- [A question they might ask you]

## Follow-Up Items from Last Time
[Only if there's a previous meeting in the user's notes]
[What was committed to, what's pending]

## Notes
[Any other relevant context — red flags, opportunities, stakes]
```

### Step 3: Save and Deliver

- Save the briefing to the user's designated output folder (or desktop if no folder is set)
- File name format: `meeting-prep-YYYY-MM-DD-[short-title].md`
- Display the briefing in the chat so the user can read it immediately

---

## Constraints

- Keep the briefing to one page. If you have more material, prioritize the most important items.
- Only pull information that's already available in connected tools. Do not fabricate context.
- If calendar access is not connected, ask the user to confirm the meeting details manually.
- If you can't find any history on an attendee, say so and focus on what the user tells you about them.
- Do not include anything the user hasn't explicitly shared or approved. Respect confidentiality.

---

## Examples

**Good activation:**
User: "prep for my meeting with Sarah tomorrow at 2pm about the Q2 campaign"
→ Skill activates, pulls Sarah's CRM notes, recent emails, any previous meeting notes, builds the briefing.

**Bad activation:**
User: "write me a report on our Q2 performance"
→ This is a different skill. Do not activate meeting prep for a deliverable request.

---

## Author Notes

Built from the AI Agent Playbook framework.
Customize the briefing template based on the user's preferences (see their `preferences.md`).
