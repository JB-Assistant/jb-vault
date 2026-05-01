# 60 Claude Cowork Commands, Skills, and Workflows That Most Users Don't Know

**Source:** [Nav Toor (@heynavtoor)](https://x.com/heynavtoor)  
**Date:** 2026-04-30  
**Original Published:** 2026-04-30  
**Link:** https://x.com/heynavtoor/status/2049804650904498501?s=46&t=ub4QNKLqvh3yU44VgGVYlQ  
**Tweet stats at capture:** 167 likes, 699 bookmarks, 25 reposts, 6 replies, 101995 views

---

## Full Article

I have been running Claude Cowork as my full operating system since January 2026.

Save this. You will need it later this week.

These 60 moves are the ones that turned Cowork from "AI assistant I open sometimes" into the thing I open before my email. Most people use maybe 6 of them. The other 54 are sitting right there, waiting.

Cowork has 6 layers most users never touch: slash commands, custom skills, scheduled tasks, connector chains, sub-agent patterns, and the .claude/ folder convention. Each one alone is useful. Stack them together and Cowork stops feeling like a chatbot and starts feeling like an operating system that runs your work while you focus on the part only you can do.

Every item below is labeled by skill level. Beginner means you can do it tonight. Intermediate means 30 minutes of setup. Pro means you have done this before. Elite means almost nobody is doing this yet, but they will be in 6 months.

---

# If you only learn 3 things from this list

Most readers will scroll. If you do, at minimum learn these three. They are the highest leverage moves in the entire article.

- Number 8 (/plan): Saves you from token disasters on complex tasks. The single most important command in Cowork.

- Number 31 (Custom Skills folder): The hidden feature that turns Cowork into your personal AI. Once you learn this, you will use Cowork twice as often.

- Number 46 (Daily 7am inbox automation): The first scheduled task you should set up. Pays for the entire $20/month plan in week one.

Now the full list.

---

# Section 1: Slash Commands That Most Users Don't Know (1 to 12)

01. /schedule [Beginner]. The single most underused feature in Cowork. Type /schedule, describe the task, set the cadence. The task runs in the background even when your laptop is closed (Max plan) or when Cowork is open (Pro). Your 7am inbox triage. Your Friday status report. Your Monday calendar prep. Set them once, never set them again.

/schedule> Every weekday 7:30am: triage Gmail, summarize calendar, save to /Daily/[date].md

02. /loop [Beginner]. The lighter cousin of /schedule. Polls something at an interval inside your current session. Stops when the session ends. Use it when you want Claude watching one specific thing while you work on another. "Every 3 minutes, check if the deploy log shows green and tell me." No more babysitting builds.

03. /plan [Beginner]. Forces Cowork to write a step-by-step plan before touching anything. Review it. Approve it. Then execute. The cost of typing /plan is 3 seconds. The cost of skipping it is sometimes a corrupted folder. Always /plan if a task touches more than 3 files.

04. /compact [Beginner]. When the conversation drags and Claude starts hallucinating earlier context, /compact compresses the chat while keeping the meaningful parts. Saves 40 to 60% of your context window. Run it before Claude starts repeating mistakes, not after.

05. /clear [Beginner]. Nuclear reset. Wipes the thread. Use when context is so polluted that Claude is fighting you. Do not be sentimental about a long thread. Start clean.

06. /resume [Intermediate]. Pick up exactly where you left a previous conversation. Pair with /rename so you can find it later by something other than "New chat 47." This is how you make Cowork feel persistent across days.

07. /rename [Intermediate]. Auto-renames the current thread based on its content. Without this, your sidebar fills up with identical "New chat" entries. With it, your sidebar becomes a searchable index of your work.

08. /cost [Intermediate]. Shows estimated token cost before you run a task. On Pro plan, this is the difference between finishing your week and burning out your allocation by Wednesday. If a task shows 3x normal cost, scope it down before you run it.

09. /memory [Intermediate]. Shows which memory files and context Claude has loaded. The first thing to check when Claude is acting weird. If the context you assumed was loaded is not, you found your bug.

10. /doctor [Intermediate]. Diagnostic command. Lists connected apps, loaded skills, available commands, current permissions. Run this when something is broken and you do not know why. Faster than asking on Reddit.

11. /voice [Pro]. Push-to-talk dictation directly into the Cowork input. Hold Space, talk, release. Your speech becomes text live as you speak. Mix typing and voice in the same prompt. The fastest input method on the platform. Once you try it, you stop typing long prompts forever.

12. /agents [Pro]. Spawns a project-specific sub-agent that lives inside your repo or folder. Example: a "test writer" agent that knows your testing conventions, or a "PR reviewer" agent that knows your team's code style. Type /agents inside any project, generate-with-Claude, and you get a focused specialist that Cowork uses automatically when relevant.

---

# Section 2: Custom Skills That Replace Entire Workflows (13 to 24)

Skills are reusable mini-programs Cowork loads automatically when relevant. Drop a SKILL.md into your /skills folder and Claude uses it whenever the request matches. Smart loading means skills do not eat your context window. The Claude Skills marketplace now hosts 2,300+ free skills. Most users have installed zero. The opportunity gap is enormous.

13. Brand voice skill [Beginner]. Drop 5 to 10 of your best articles into /skills/brand-voice/examples. Add a SKILL.md that says "match the tone of these examples." Now every writing task sounds like you, not Claude. The single highest-leverage skill for anyone who writes online.

14. Email triage skill [Beginner]. Defines your personal triage rules: what counts as urgent, what gets a one-line reply, what gets archived without reading. Once installed, every email task uses your judgment, not Claude's defaults.

15. Meeting transcript skill [Beginner]. Takes any raw transcript and outputs structured notes: decisions made, action items with owners and deadlines, open questions, follow-ups. Triggers automatically whenever you upload a transcript file.

16. PDF report generator skill [Beginner]. Generates branded PDF reports from markdown with title page, table of contents, and footer. Pair with your brand-voice skill and every report looks like your team produced it.

17. Code review skill [Intermediate]. A SKILL.md that encodes your team's coding standards, naming conventions, and common review comments. Every PR review uses it automatically. Replaces the senior engineer's monthly "remember our style guide" reminder.

18. Customer support response skill [Intermediate]. Trained on your past Zendesk or Intercom replies. Drafts every new response in your team's voice with your team's solutions. Saves the average support agent 4+ hours per week.

19. Proposal generator skill [Intermediate]. Reads a client brief and your proposal template. Generates a customized proposal in your tone, with your pricing logic. Train it on 3 winning proposals. Now every new proposal takes 10 minutes instead of 3 hours.

20. Investor update skill [Pro]. Encodes your KPIs, your narrative arc, your structure. Every monthly investor update follows the same logic. Pull metrics from your dashboard, format the update, attach the right context. 2-hour task becomes 15 minutes.

21. Contract review skill [Pro]. Reads any contract PDF and flags key terms, deadlines, auto-renewals, liability caps, and unusual clauses. Not legal advice. A first-pass review that saves 1 to 2 hours per contract before you send it to your lawyer.

22. Hiring screen skill [Pro]. Reads any resume against your role description and outputs a structured assessment: strengths, gaps, red flags, suggested interview questions. Replaces the hour you spent on each first-pass screen.

23. Stakeholder communication skill [Elite]. One skill, four output formats: 50-word summary for the CEO, 200-word version for your manager, 500-word technical version for engineering, public-facing version for the blog. Every announcement gets all four versions in one prompt.

24. Pricing skill [Elite]. Reads any product description, generates 3 pricing tiers with rationale, anchored to comparable products in the market. Used by SaaS founders to price-test before launch.

---

# Section 3: File System Power Moves (25 to 33)

25. Screenshot library organizer [Beginner]. "Read every screenshot in /Screenshots. Use OCR to detect what each one is: a code error, a chart, a UI design, a meeting slide. Move each into the matching subfolder. Add a description as the filename." Turns the 800-screenshot pile into a searchable archive in 5 minutes.

26. Smart attachment processor [Beginner]. "Look in /Attachments. Group emails-attachments by sender, contracts-attachments into /Legal, invoices into /Finance/[year]/[month], everything else into /Misc. Rename invoices with vendor + amount + date." Inbox attachments stop being a black hole.

27. Code repo cleanup [Intermediate]. "Read all my project repos in /Code. Identify dead branches, unused dependencies, abandoned experiments older than 90 days. Move abandoned repos to /Code/archive. Generate a cleanup report." Reclaims tens of GB and zero mental load.

28. PDF metadata extractor [Intermediate]. "For every PDF in /Research, extract: title, authors, publication date, abstract, key findings. Save as a CSV index. When I ask for research on [topic], use this index first." Turns a 200-PDF dump into an instantly searchable knowledge base.

29. Photo library curator [Intermediate]. "Look at every photo in /Photos taken this year. Find blurry duplicates and near-duplicates. Identify the best version of each shot using sharpness and composition heuristics. Move the rest to /Photos/cull-review for final approval." Replaces the 4 hours you would spend culling manually.

30. Voice note to article pipeline [Pro]. "Read all transcripts in /Voice-Notes from this week. For each, draft a 1,500-word article in my brand voice. Keep my natural cadence but cut rambling and add structure. Save publication-ready drafts to /Drafts." Solo content shop, fully voice-driven.

31. Custom skill folder setup [Pro]. Create ~/skills with subfolders for each skill: brand-voice, email-triage, pdf-report, etc. Each subfolder has a SKILL.md describing when and how Claude should use it. Cowork auto-discovers and uses them whenever the request matches. This single setup turns Cowork from a chat app into your personal AI. The most underrated configuration on the platform.

~/skills/brand-voice/SKILL.md~/skills/email-triage/SKILL.md~/skills/pdf-report/SKILL.md~/skills/proposal/SKILL.md

32. Git history miner [Pro]. "Read the last 90 days of git history across all my projects. Identify which features I shipped, which bugs I fixed, what skills I used most. Generate a quarterly engineering self-review I can paste into my performance doc." Annual review writes itself.

33. Backup audit with intelligence [Elite]. "Compare /Documents to my last backup. Show me which files changed, which are new, which were deleted. Flag any deletion of files modified in the last 30 days as suspicious. Estimate how long a full backup will take given my files are X size." Backup hygiene without thinking about it.

---

# Section 4: Connector Workflows That Replace Real Jobs (34 to 45)

34. Calendar conflict resolver [Beginner]. "Look at my Google Calendar for next week. Identify meeting conflicts, back-to-back meetings with no buffer, and meetings I should probably decline based on relevance. Suggest reschedules with proposed alternative times." Replaces the 30 minutes you spend on calendar Tetris every Sunday.

35. Slack thread to executive brief [Beginner]. "Read this Slack thread. Identify the decision being debated, the positions of each participant, the emerging consensus, and the open questions. Output a 1-paragraph brief I can forward to my boss." Long threads become decisions in seconds.

36. Gmail to CRM logger [Intermediate]. "Scan my Gmail for emails sent to or received from any contact in our HubSpot CRM. Log each email as an activity against the matching contact record. Include subject, snippet, and timestamp. Skip anything already logged." Sales rep activity logging on autopilot.

37. Drive to data warehouse pipeline [Intermediate]. "Read every Google Sheet in /Drive/Reports. For each, infer the schema, normalize column names, and append the data to the matching table in BigQuery. Note any sheets that do not match an existing table." Replaces the data engineer's ETL ticket queue.

38. Notion to Linear ticket pipeline [Intermediate]. "Read this Notion PRD. Generate Linear tickets for each requirement. Group by component, assign by team based on our team-component mapping, add to the current sprint. Output a summary of tickets created." Specs become work in 90 seconds.

39. Multi-source weekly status report [Pro]. "Pull this week's sales numbers from Salesforce. Pull product metrics from Mixpanel. Pull customer feedback from Intercom. Pull team activity from GitHub. Combine into a 1-page weekly status report. Save as PDF." Replaces a full-time RevOps coordinator.

40. Cross-platform context retrieval [Pro]. "I am about to start a meeting with [client]. Pull all relevant context: recent emails from them, related Drive docs, mentions in Slack, open Linear tickets they care about, last call notes. Compile a 1-page meeting prep doc." Walk in fully briefed every time.

41. Salesforce pipeline hygiene [Pro]. "Query opportunities in Salesforce. If stage is Proposal Sent and last activity was 14+ days ago with no response logged, move to Needs Review. Show preview of all changes before executing." 3 hours of manual cleanup becomes 8 minutes.

42. GitHub PR auto-review [Pro]. "Watch our GitHub repo. When a new PR opens, run our code-review skill against it. Post structured review comments. Approve if it passes our checklist. Tag a senior engineer if it fails." First-pass review, automated.

43. Stripe to bookkeeping reconciliation [Elite]. "Pull all Stripe transactions from last month. Match each to an invoice in our Google Sheet. Flag mismatches: payments without invoices, invoices without payments. Update the bookkeeping sheet with reconciliation status." Replaces a part-time bookkeeper.

44. Customer churn early warning [Elite]. "Cross-reference Intercom support tickets, Mixpanel usage data, and Stripe payment history. Identify accounts showing 3+ churn signals (declining usage, support friction, payment delays). Output a list ranked by ARR at risk." A retention team in one prompt.

45. Investor pipeline tracker [Elite]. "Read every email I have exchanged with investors in the last 6 months. Categorize each conversation by stage: cold intro, first meeting, second meeting, due diligence, term sheet, closed, passed. Identify investors who have gone quiet for 21+ days and draft a follow-up. Output a CRM-style pipeline view." Replaces a fundraising-ops hire.

---

# Section 5: Scheduled Automations That Run While You Sleep (46 to 53)

46. Daily 7am inbox processor [Beginner]. Schedule daily 7am: "Triage Gmail. Categorize unread. Draft responses for routine emails. Flag urgent ones. Save the summary to /Daily/inbox-[date].md." Wake up to a triaged inbox every single day. The first automation everyone should set up.

47. Sunday week-ahead brief [Beginner]. Schedule Sunday 6pm: "Pull next week's calendar. For every meeting, attach the relevant prep docs from Drive. Flag any meeting where I have no context yet. Generate a 1-page weekly brief with priorities, prep gaps, and outstanding action items. Save to /Weekly/brief-[date].md." Walk into Monday already informed.

48. Daily metric snapshot [Intermediate]. Schedule daily 8am: "Pull yesterday's key metrics from Mixpanel, Stripe, and our database. Calculate week-over-week and month-over-month deltas. Flag anything outside expected ranges. Save to /Metrics/[date].md and post a summary to our #metrics Slack channel." Replaces the daily metrics standup.

49. Weekly content recycler [Intermediate]. Schedule Friday 5pm: "Read every article I published this week. Generate 8 standalone tweets, 2 LinkedIn posts, 3 short-form video scripts, and 1 newsletter teaser per article. Save to /Content/recycled/[week]." One article becomes 14 distribution assets, automatically.

50. Monthly competitor scan [Pro]. Schedule first of every month: "Search news, ProductHunt, Crunchbase, and X for updates on [3 named competitors]. Track pricing changes, product launches, hiring, and funding. Compare to last month. Output a competitive landscape brief saved to /Intelligence/[month].md." Strategic intelligence on autopilot.

51. Quarterly OKR self-review [Pro]. Schedule first day of each quarter: "Read all Q[X] OKRs. Pull progress data from Notion, Linear, and Drive. For each OKR, calculate completion percentage, identify blockers, recommend Q[X+1] adjustments. Save to /OKRs/Q[X]-review.md." Replaces the consultant.

52. Annual highlights compiler [Elite]. Schedule December 28: "Read every weekly status doc, every quarterly review, and every shipped feature from the year. Identify the 10 highest-impact moves I made. Generate a year-end wrap that I can use for performance review, social posts, and personal reflection. Save to /Annual/[year].md." Year ends with the highlight reel already done.

53. Birthday and relationship maintenance [Elite]. Schedule weekly Sunday 4pm: "Look up everyone in my contacts whose birthday or work anniversary falls in the next 14 days. Draft a personal message for each one based on our last conversation. Save to /Relationships/[week].md for me to review and send." The hardest soft skill, automated.

---

# Section 6: Pro Patterns Most People Don't Know Exist (54 to 60)

54. Sub-agent parallelization [Pro]. Spawn sub-agents for any task that would pollute your main thread. "Run 3 sub-agents in parallel: one researches competitor pricing, one drafts the strategy memo, one prepares the slide outline. Return only the final outputs to me." Massive parallel work, clean main context.

55. Connector chains for compound output [Pro]. Chain multiple connectors in one command. "Read the latest email from [client]. Search Drive for related contracts. Check Slack for any team discussion of them. Pull their open Linear tickets. Compile a complete client status doc." 4 tools, 1 prompt, 1 deliverable.

56. Skill stacking for compounding leverage [Pro]. Combine multiple skills in a single task. "Use the brand-voice skill plus the email-triage skill plus the meeting-notes skill to draft a follow-up email to yesterday's call." Skills compose like Lego. Stack 3 skills and you have a function nobody else has built.

57. Plan mode for token discipline [Pro]. Always /plan before tasks on Pro plan. The plan output shows you the full token budget upfront. Adjust scope before execution. The single move that saves the most token allocation each week.

58. The .claude/ folder convention [Elite]. Every serious Cowork user keeps a .claude/ folder in each project. Inside: commands/, skills/, agents/, and CLAUDE.md (project context). When you open Cowork in this project, all of it loads automatically. Your .claude/ folder is your real resume now. Hiring managers in 2026 will check it before checking your LinkedIn.

59. Off-peak scheduling for 2x throughput [Elite]. Anthropic doubled off-peak usage limits in March 2026. Schedule heavy automations for evenings and weekends. You get 2x throughput on the same plan. Most users do not know this and waste their best automations on peak hours.

60. Persistent Dispatch threads across devices [Elite]. Cowork Dispatch (March 2026) keeps a persistent thread that survives across devices. Start a task on your laptop. Pick it up on your phone during your commute. Finish it on your tablet at home. The thread retains all context, all memory, all skill state. The closest thing to a real personal AI yet built.

---

# 5 Pro Tips That Multiply Everything Above

1. Treat Cowork like a junior employee, not a search box. Junior employees need context, examples, and clear acceptance criteria. So does Cowork. The 30 seconds you spend setting context save the 5 minutes of bad output you would otherwise correct.

2. Build your skill library in the first month, not as you go. Spending 4 hours on day 1 setting up 5 to 8 personal skills returns hundreds of hours over the next year. Most people build skills only when they are already overloaded. Do it before.

3. /plan is free insurance. The cost of typing /plan is 3 seconds. The cost of skipping it on a complex task is sometimes a corrupted folder, a deleted file, or a wasted day. Type /plan.

4. Schedule the boring stuff first. Your 7am inbox triage, your Friday status report, your Sunday week-ahead brief. These are not glamorous. They are the foundation. Once they run automatically, you have hours each week to do work only you can do.

5. The .claude/ folder is your new resume. Every serious project should have one. Hiring managers in 2026 already check for it. Your Cowork setup signals how you work better than any LinkedIn bio.

---

# Where to Start Based on Your Level

Beginner (this week): Pick 5 commands from Section 1. Use them daily. Once they are automatic, move up.

Intermediate (next 3 weeks): Set up your /skills folder. Build 3 custom skills for your most repeated tasks. Schedule the daily 7am inbox processor and the Sunday week-ahead brief.

Pro (month 2): Set up connector chains. Run weekly automations across multiple tools. Use /agents to specialize Cowork for each project. Track your token budget with /cost.

Elite (month 3+): Build the .claude/ folder convention into every project. Use Dispatch for persistent threads across devices. Schedule heavy work off-peak. Stack skills for compound output.

---

# TL;DR

60 commands, skills, and workflows. Tested daily for 4 months. Most users know maybe 8 of them.

Cowork is not a chatbot with file access. It is an autonomous operating system. The people who win in 2026 are the ones who treat it that way.

Save this list. Bookmark the 3 you will try this week. Come back when you have learned them. There are 57 more waiting.

I post stuff like this every week. Real workflows, real numbers, real results from daily use. No fluff. Follow if you want the next one.

---

## Summary

Nav Toor lists 60 Claude Cowork commands, skills, scheduled automations, connector workflows, and pro patterns that turn Cowork from a chatbot into a work operating system. The central point is that most users only use a small surface area, while the real leverage comes from stacking slash commands, custom skills, schedules, connector chains, sub-agents, and project-level `.claude/` conventions.

The article’s highest-leverage moves are `/plan` for token/task discipline, a custom skills folder for reusable personal workflows, and scheduled automations like daily inbox triage. The larger pattern is treating Claude/Cowork like an operating layer for repeated knowledge work, not a one-off Q&A interface.

---

## Key Takeaways

1. The key Cowork layers are slash commands, custom skills, scheduled tasks, connector chains, sub-agent patterns, and `.claude/` project folders.
2. `/plan` is framed as the most important command because it prevents messy execution and token waste on complex tasks.
3. Custom skills turn repeated workflows into reusable behavior: brand voice, email triage, meeting notes, code review, support replies, proposals, contracts, hiring, pricing, and more.
4. File-system workflows can organize screenshots, attachments, repos, PDFs, photos, voice notes, git history, and backups.
5. Connector workflows combine apps like Gmail, Calendar, Slack, Drive, Notion, Linear, Salesforce, Mixpanel, Intercom, GitHub, Stripe, and BigQuery.
6. Scheduled tasks are the compounding layer: inbox processing, week-ahead briefs, metric snapshots, content recycling, competitor scans, OKR reviews, yearly highlights, and relationship reminders.
7. Pro patterns include sub-agent parallelization, connector chains, skill stacking, token discipline, `.claude/` folders, off-peak scheduling, and persistent dispatch threads.
8. The practical ramp: learn commands first, then build skills, then schedule workflows, then use connectors/agents/project conventions.

---

## Hermes-Related Interest

Very high. This maps almost directly to Hermes as JB’s personal operating system:

- Hermes cron jobs = scheduled automations.
- Hermes skills = Cowork custom skills, but reusable across sessions/tools.
- JB Vault = `.claude/` + memory layer across Hermes/OpenClaw.
- delegate_task/subagents = Cowork sub-agent patterns.
- tool connectors = Gmail/Calendar/Drive/Notion/Linear/GitHub-style workflows.

Best implementation idea for JB: create a “daily operating system” around Hermes first — 7am inbox/business brief, lead-hunter runs, SaaS metrics snapshot, customer follow-up queue, and weekly content recycler. This is more revenue-relevant than passive AI research.
