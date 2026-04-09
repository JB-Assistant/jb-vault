# How to Set Up Claude Cowork (the April 2026 Update)

**Source:** Ruben Hassid (@rubenhassid)  
**Date:** 2026-04-09  
**Link:** https://x.com/rubenhassid/status/2042105069550932138

---

## Full Article

I've been begging you to switch from ChatGPT to Claude for months.

So I wrote countless Claude guides, getting millions of reactions.

But only recently, everyone actually switched:

Claude is all the rage right now because of Cowork: it's the best thing to happen to AI since ChatGPT. If you don't code, you must be using Claude Cowork now.

Some of you read my guide in March, and spent an hour setting up Cowork. That's a good start. But you're using it the way I taught you on March 5. And a lot has changed since then. This free guide shows you exactly what & how.

Before starting, I want you to do two things:

1. Save this guide & block 20 minutes this week to test Cowork.
2. Send it to anyone who still hasn't tried Cowork (or Claude).

Skip this if you already use Claude Cowork.

## Quick reminder on how to access Claude Cowork:

- Go to claude.com/download. Download the app on your computer.
- You must have a Pro account ($20/month). I pay for the $100/month plan.
- Open the app. Click on the Cowork tab at the top between Chat & Code.
- Select a folder from your computer.
- Make sure to always select "Opus 4.6" for complex tasks. It's the smart model.

## I - My Cowork folder (updated)

Claude Cowork is all about how you set up your folder inside your computer. Because each session on Cowork starts like this: [folder selection interface]

### Create folder structure:

Create a new folder named Claude Cowork. Inside it, create 3 subfolders:

1. ABOUT ME
2. OUTPUTS
3. TEMPLATES

### Step 1: Three core files in the ABOUT ME folder

These are the only files Cowork reads automatically.

**File #1 — about-me**

Who you are. How you think. How you want Claude to write for you.

A few months ago, I wrote an extremely long and complex about-me file. I asked Claude to interview me through 100 questions. But that single file was eating 22,000+ words of Cowork's context window.

So I trimmed it to under 2,000 words by extracting the patterns and throwing away the raw transcripts. Almost the same, but 10x less noise.

**IF YOU ALREADY HAVE IT, trim it. Here's how:**

Go to Claude Cowork. Upload your previous about-me file. Then simply ask Cowork this prompt:

"This is my about-me file and I need to save tokens. Ask me questions on how to trim effectively until we have the perfect document."

**NOW IF YOU DON'T HAVE ANY FILE, here's how to make yours from scratch:**

1. Open a new Cowork session.
2. Prompt it:

"You are building my about-me.md file for my Cowork folder. This file will be read by Claude at the start of every session to help you do my job with me. It needs to be concise and high-signal.

Your job: interview me using AskUserQuestion (20 questions), then compile the answers into a condensed about-me.md under 2,000 tokens.

## How to interview me

- Use AskUserQuestion for every question. One question at a time.
- If I give a vague answer, push back. Ask for a specific example or rephrase.
- Follow interesting threads. If something unexpected comes up, go deeper before moving on.

## What to cover (15-20 questions)

**WHO I AM** (3 questions)
- What do I do? What's my role, my company, my industry?
- Who do I work with or work for?
- What does a good week of work look like for me?

**HOW I WORK** (4 questions)
- What tools do I use every day and how?
- Walk me through how I start a typical task from zero to done.
- What does my review/editing/QA process look like?
- When I hand something off, what does "done" look like?

**WHAT GOOD LOOKS LIKE** (4 questions)
- Show me or describe the best output you've produced recently. What made it good?
- What separates great work from average work in your field?
- When you look at someone else's work and think "this is good," what are you reacting to?

**WHAT YOU HATE** (4 questions)
- What's an example of bad work in your field? What specifically makes it bad?
- What patterns, shortcuts, or habits in your industry make you cringe?
- When Claude writes something for you and it's wrong, what's usually off?

**YOUR RULES** (3 questions)
- What do you never do in your work? Hard lines you won't cross.
- What are the 2-3 non-negotiables that every piece of your work must have?

**YOUR OPINIONS** (3 questions)
- What do you believe about your field that most of your peers would push back on?
- What tools, methods, or trends do you think are overrated? What's underrated?

## Output format

After the interview, compile everything into a single markdown file. Do NOT save raw Q&A transcripts. Extract the patterns.

Structure:

# ABOUT ME: [My Name]

## Who I am
[2-3 sentences]

## How I work
[My daily tools, my process]

## What good looks like
[What I value]

## What I hate
[Patterns and mistakes]

## My rules
[Numbered list]

## Instructions for Claude
[10 numbered rules for how to work with me]

Target: under 2,000 tokens total."

3. Click where you need to click.
4. Dictate your answers. Make sure to use Wispr Flow instead of typing.

**File #2 — anti-ai-writing-style**

You hate AI writing. I hate AI writing. You want your taste as a set of rules. The words you hate. The sentence patterns that make you cringe.

Mine bans 80+ AI words (delve, harness, tapestry, the usual suspects), kills reframe patterns, and limits paragraphs to 3 sentences.

**File #3 — my-company**

Your targets. Your strategy. What you're focused on. What you're saying no to.

Mine has my audience targets per platform, my consulting service lines, and a "what I'm saying no to" section.

Prompt to build it:

"You are building my my-company.md file for my Cowork folder.

Your job: interview me using AskUserQuestion (6-8 questions), then compile the answers into a condensed my-company.md under 1,000 tokens.

## What to cover

**GOALS** (3-4 questions)
- What are your top 2-3 goals for this year?
- What platforms, channels, or markets matter most right now?
- What's the one metric that would tell you this year was a success?

**DECISIONS** (3-4 questions)
- What are you actively saying no to right now?
- What did you recently stop doing? Why?
- Where are you spending most of your time and energy this quarter?

## Output format

# MY COMPANY

## Goals
[Bullet points]

## Focus right now
[2-3 bullet points max]

## Saying no to
[Bullet points]

Target: under 1,000 tokens."

### Step 2: The OUTPUTS folder

This is simply where Cowork will work and save documents. One subfolder per project. Cowork organizes everything itself.

### Step 3: The TEMPLATES folder

Cowork fills this folder automatically. When Cowork builds something you like, you say: "Save this as a template in TEMPLATES/."

## II - How to set up Global Instructions

Go to: Settings → Cowork → Edit Global Instructions.

Paste this:

"Before every task, read every file in ABOUT ME/:
- about-me: [describe what's in yours]
- anti-ai-writing-style: [describe what's in yours]
- my-company: [describe what's in yours]

Never read OUTPUTS/ or TEMPLATES/ unless I specifically point you to a file.

Save all deliverables in OUTPUTS/ under a subfolder named after the project.

If the brief is unclear, use AskUserQuestion. Don't fill gaps with filler."

**Why this matters:** Cowork reads your ABOUT ME files before every task. If those 3 files are small (under 6,000 tokens total), it reads all of them completely. If your files are too big, Cowork starts summarizing them loosely instead of reading them carefully.

## III - Your Cowork has a bottleneck. It's you.

Typical Cowork session:

- You type a prompt. 30 seconds.
- Cowork reads your files. 5 seconds. Generates a plan. 20 seconds. Asks clarifying questions. 5 seconds.
- You answer those questions. 60 seconds per answer. Maybe 2 minutes.
- Across 8 questions, that's 8-15 minutes of you being the slow part.

But you could be faster. Because you speak at 150 words per minute. You type at 60.

**How to set up Wispr Flow:**

1. Go to wispr.ai. Download Wispr Flow. Install it.
2. The free tier is capped at 2,000 words/week.
3. Choose your favorite keystroke to activate. Ruben uses "Shift".
4. Hold your keystroke and talk. Your words appear wherever your cursor is.

**How to use Wispr + Cowork:**

1. **The initial prompt:** Speak it. The point isn't to be faster, but to give much more context when we talk rather than with a lazy typed prompt.
2. **AskUserQuestion answers:** Speak those too. When you need to add context, dictate it instead of typing.
3. **Feedback and pivots:** Spoken. "The tone is too stiff. I want it to sound like I'm texting a friend who happens to run a 200-person company."

## IV - How to save credits in Cowork

The $20 paid plan gives you tokens. But you will use them up fast.

**1. Restart your conversation. Don't send a follow-up.**

Claude doesn't count messages. It counts tokens. Every time you send a message, Claude re-reads the entire conversation history.

Message 30 costs 31x more tokens than message 1.

When Cowork gets something wrong, you want to type "No, I meant..." and send another message. Don't. Every follow-up stacks.

Instead: click "Restart the conversation from here" on a previous message.

**2. Start a fresh session every 20 messages.**

Long conversations are token furnaces. One developer tracked his usage and found 98.5% of tokens were spent re-reading history. Only 1.5% went to the actual output.

When a Cowork session gets long: ask Claude to summarize everything, copy it, start a new session, paste the summary as your first message.

**3. Batch your tasks into one message.**

Three separate prompts = three full context reloads. One prompt with three tasks = one reload.

**4. Use Sonnet (not Opus) for quick tasks.**

Grammar checks, brainstorming, formatting, short answers. Sonnet handles all of this at a fraction of the cost. Save Opus + Extended thinking for the work that actually needs it.

**5. Keep your ABOUT ME files small.**

Cowork reads your folder before every single task. If your files are bloated, that's thousands of tokens burned before any real work starts. My about-me.md used to be 22,000 tokens. Now it's under 2,000.

**6. Spread your work across the day.**

Claude uses a rolling 5-hour window. If you burn your entire limit in one morning session, most of your daily capacity goes unused.

Split into 2-3 sessions: morning, afternoon, evening. Avoid peak hours (5-11 AM Pacific on weekdays) when the same query costs more against your limit.

## V - Your first 20 minutes with Claude Cowork

**Minutes 0-5: Set up the folder**

- Download the Claude desktop app and get the paid plan ($20 or $100).
- Create the folder structure: ABOUT ME/ with your 3 files, plus empty OUTPUTS/ and TEMPLATES/ folders.
- For about-me: open a Cowork session, ask it to interview you, dictate your answers. Then ask it to condense everything to under 2 pages.
- For anti-ai-writing-style: write the words and patterns you hate.
- For my-company: your targets, your platforms, your strategy.

**Minutes 5-6: Paste the global instructions**

Go to Settings > Cowork > Edit Global Instructions. Paste the version from this newsletter.

**Minutes 6-8: Install Wispr Flow**

Go to wispr.ai. Download. Install. Select your favorite keystroke. Test it in Cowork.

**Minutes 8-15: Run your first voice session**

Open Cowork. Speak a task: "I want you to read my folder and help me write [something you actually need this week]. Ask me questions before you start."

**Minutes 15-20: Feel comfortable with your folder**

Ask Cowork to create a template from the conversation. Check all subfolders. You are a Claude Cowork pro now!

---

## Summary

Ruben Hassid walks through the April 2026 update to his Claude Cowork setup guide. The core insight: Cowork's effectiveness is bottlenecked by the user, not the technology. Speaking (via Wispr Flow at 150wpm) instead of typing (60wpm) closes that gap. Key setup includes a 3-folder structure (ABOUT ME, OUTPUTS, TEMPLATES) with three lean files in ABOUT ME totaling under 6,000 tokens, plus Global Instructions to tie it together. Token savings strategies include restarting conversations instead of follow-ups, fresh sessions every 20 messages, batching tasks, using Sonnet for quick work, and spreading sessions across the day.

---

## Key Takeaways

1. **Folder structure:** Claude Cowork/ → ABOUT ME/ (3 core files), OUTPUTS/ (for deliverables), TEMPLATES/ (auto-filled by Cowork)
2. **Three ABOUT ME files:** about-me.md (under 2,000 tokens), anti-ai-writing-style.md (banned words/patterns), my-company.md (under 1,000 tokens)
3. **Global Instructions:** Paste into Settings → Cowork → Edit Global Instructions so Cowork knows when to read which files
4. **Wispr Flow is the bottleneck fix:** Speak at 150wpm instead of typing at 60wpm. Holds a key, talks, words appear. Free tier: 2,000 words/week
5. **Token saving:** Restart conversation instead of follow-up; fresh session every ~20 messages; batch tasks into one message; use Sonnet for quick tasks; keep files lean
6. **Don't over-configure upfront:** 20 minutes to set up and test is enough. Build the files through actual use, not upfront perfection
7. **Speaking > typing for feedback:** Dictate answers and pivots rather than typing — more context, more natural, keeps you in flow state
8. **Trim existing about-me files:** If you already have one that's bloated, use Cowork to interview you and condense it to under 2,000 tokens

---

## Hermes-Related Interest

This is directly applicable to how you work with Hermes Cowork. The about-me/anti-ai-writing-style/my-company file structure maps cleanly to what a "user profile" and "workflow context" would look like for me. The token math is a useful frame — keeping context lean is a recurring theme (same as the Rasmic article above). The idea that "the model already knows everything except your specific workflow/taste/strategy" is essentially what the user profile in memory is trying to codify.

The "bottleneck is you" framing is also worth internalizing — Hermes can process and respond much faster than a typed conversation allows. Voice input would close that gap similarly to Wispr Flow.

Worth considering: should you build a Hermes Cowork equivalent folder structure? An "ABOUT HERMES" or "HERMES CONTEXT" file that I read at the start of every session with your taste, rules, and strategy?
