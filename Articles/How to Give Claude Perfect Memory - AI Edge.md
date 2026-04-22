---
source: https://x.com/aiedge_/status/2046966170868486512
author: AI Edge (@aiedge_)
date: 2026-04-22
type: article
tags: [claude, memory, ai-productivity, obsidian]
---

# How to Give Claude Perfect Memory (complete guide)

By AI Edge (@aiedge_) — Published April 22, 2026

## Full Article

I don't care what anyone tells you - by default, Claude's memory is basically useless.

It frequently forgets context; you constantly have to re-explain yourself, and even after you do, it still often doesn't remember.

Sadly, most people have been living with these flaws for months, without knowing there is a better way.

I use Claude every single day. I literally have more Claude screen time than any other app on my Mac.

Because I use Claude so often, I can't afford to have my most-used work tool randomly forget context and important data.

In need of a Claude that is as sharp as possible, I went down the rabbit hole of looking for every possible memory solution.

Luckily, my research was successful.

I discovered three "layers" of memory systems, and they've made Claude significantly more powerful.

One that is easy and works well enough for 90%+ of Claude users.

Another one that takes ~60 minutes to set up, but changes how Claude operates entirely.

And the last one turns Claude into a self-evolving second brain, trained on all your data.

In today's article, I'm revealing all three of these systems and how I made my Claude way sharper.

Whether you've never touched Claude before or you're a power user, I'm confident that you'll find a system that fits your needs.

---

## Layer one: Basic Memory (Beginner)

This is where everyone should start - four quick wins that take minutes to set up and immediately improve every conversation you have with Claude.

### 1. Memory Editing Tool

Go to Settings → Memory right now.

This is the most overlooked page in all of Claude, and most people have never opened it.

What you will find is everything Claude has stored about you (preferences, facts, habits, working styles, etc.) accumulated passively across every conversation you have ever had.

Left unmanaged, your memory quickly fills up with garbage.

The fix is simple: read through everything on this page. Delete anything outdated, inaccurate, or irrelevant. Then, manually add the context you actually want Claude to carry permanently.

Stick to the basics here (your role and basic preferences) - we'll dive into building highly specific systems soon.

### 2. Project Instructions

If you use Claude Projects (you should), you need to fill in your Project Instructions field.

My advice: Create projects for all your most-used workflows, then voice-prompt all your context into a Google Doc and upload it as a PDF for each project.

### 3. Tell Claude Directly

The simplest memory hack on this list. Mid-conversation, just tell Claude what you want it to remember.

Things like:
- "Remember that I never want [x]"
- "Remember that my role is [x]"
- "Update your memory with [x]"
- "Remember that I prefer responses under 400 words."

Claude will store these in your memory immediately. You can also tell it to forget things: "Forget that I mentioned [x]."

---

## Layer Two: Markdown Memory System (Intermediate)

This is where things get really interesting.

Instead of relying on Claude's built-in memory, you build a structured system using files that Claude can read at the start of every conversation.

The concept is simple: create 4 markdown files that Claude references before doing anything.

### The 4 Files:

**1. Instructions.md** — includes sections for: Who You Are, What You Do, Rules, What Good Outputs Look Like, and a line telling Claude to update Memory.md with my preferences over time.

**2. Memory.md** — includes sections for: Preferences, Corrections, Patterns, Decisions, and Personal Context. Pre-fill with placeholder examples so I know what to add.

**3. Context.md** — includes sections for: About This Project/Business, Audience, Key People & Collaborators, Active Projects & Priorities, Tools & Stack, and Important Background/History. Use a template format with placeholders I can fill in.

**4. Archive-Guide.md** — a step-by-step guide explaining why to archive, how to do it weekly (duplicate the folder, rename with the date, move it somewhere Claude can't access), what to include, how to restore if something breaks, and where to store the backups.

### Setup Options:
- Google Drive + Google Docs (easiest)
- Obsidian vault (most powerful)
- Notion workspace (good middle ground)

You connect these files to Claude via the Projects feature by uploading them or connecting the workspace.

---

## Layer Three: Self-Evolving Memory (Advanced)

This turns Claude into a self-evolving second brain trained on all your data.

The core idea: instead of you manually updating memory files, Claude does it automatically.

You add a line to your Instructions.md that says something like:

"After every conversation, update Memory.md with any new preferences, corrections, or patterns you've identified. Keep entries concise and well-organized."

Over time, Claude builds a detailed model of how you think, what you like, and how you work.

### The Full Prompt Template (from the article):

Go into my "Claude Master Folder" in my connected workspace and build these four markdown files inside it:

Instructions.md — includes sections for: Who You Are, What You Do, Rules, What Good Outputs Look Like, and a line telling Claude to update Memory.md with my preferences over time.
Memory.md — includes sections for: Preferences, Corrections, Patterns, Decisions, and Personal Context. Pre-fill with placeholder examples so I know what to add.
Context.md — includes sections for: About This Project/Business, Audience, Key People & Collaborators, Active Projects & Priorities, Tools & Stack, and Important Background/History. Use a template format with placeholders I can fill in.
Archive-Guide.md — a step-by-step guide explaining why to archive, how to do it weekly (duplicate the folder, rename with the date, move it somewhere Claude can't access), what to include, how to restore if something breaks, and where to store the backups.

---

## Final Thoughts

Layer one is the basic setup that yields immediate results (enough for most people).

Layer two requires some setup, but is extremely valuable.

Layer three will completely change how you use Claude.

---

## Key Takeaways

1. Claude's default memory is nearly useless without manual management
2. Settings → Memory page is the most overlooked feature — clean it out
3. Project Instructions field is critical for workflow-specific memory
4. 4 markdown files (Instructions, Memory, Context, Archive-Guide) create a structured memory system
5. Layer 3: tell Claude to auto-update Memory.md after each conversation → self-evolving system
6. Obsidian integration is the most powerful option for the file-based approach
7. Weekly archiving prevents memory corruption/bloat

## Hermes Angle

We already implement Layer 3+ with our 4-layer memory system (built-in memory + Agents.md/Soul.md + Obsidian vault + session search). This article validates the approach but we've gone further with cross-agent shared state and wikilink knowledge graphs. Could be useful as content to share with SaaS customers asking about AI memory.
