---
title: "35 Claude Code Commands, Tricks, and Workflows That Most Users Don't Know — The Complete List"
source: "https://x.com/eng_khairallah1/status/2046519525907317043?s=46&t=ub4QNKLqvh3yU44VgGVYlQ"
author:
  - "[[@eng_khairallah1]]"
published: 2026-04-21
created: 2026-04-21
description: "I have been using Claude Code daily for months. These are the 35 techniques that make it feel like a cheat code.Save this :)Most developers ..."
tags:
  - "clippings"
---
![Image](https://pbs.twimg.com/media/HGYRbFLaUAAg9Ax?format=jpg&name=large)

I have been using Claude Code daily for months. These are the 35 techniques that make it feel like a cheat code.

Save this :)

Most developers install Claude Code, use it for basic code generation, and think they have seen what it can do.

They have seen maybe 20 percent.

The other 80 percent - the techniques that turn Claude Code from "useful assistant" into "the most productive I have ever been". are buried in documentation, discovered through experimentation, or shared in small communities.

I compiled every technique that moved the needle for me. Tested daily. Zero theory.

**Bookmark this. You will use it every time you open your terminal.**

# Essential Commands (01 to 08)

**01\. Plan Mode (Shift + Tab)**

Before any implementation, switch to plan mode. Claude Code analyzes your codebase and creates an architecture plan WITHOUT writing any code. Review the plan. Approve it. Then switch back to implementation. This single habit prevents more bugs than any other technique on this list.

**02\. Compact (/compact)**

After 30 to 45 minutes of conversation, your context gets bloated. Type /compact to compress the entire conversation history into a focused summary of key decisions and current state. Claude Code stays sharp instead of gradually losing track of what you discussed.

**03\. Clear (/clear)**

Starting a new task? Clear the slate entirely. Carrying context from a database refactor into a frontend redesign produces confused, conflicting code. One conversation per feature. Always.

**04\. Init (/init)**

Run this at the start of any new project. Claude Code scans your codebase and generates a [CLAUDE.md](http://claude.md/) file. a persistent context document that it reads automatically in every future session. Includes project structure, tech stack, coding patterns, and key architecture decisions.

**05\. The Cost Check (/cost)**Displays your token usage for the current session. Check this every hour during long sessions. AI-assisted development costs money and surprises are never fun. Set a mental budget per session and check against it.

**06\. Memory (/memory)**

Add persistent instructions that Claude Code remembers across all sessions. "Always use TypeScript strict mode." "Always add JSDoc comments to public functions." "Always run tests after modifying any file in /src/core." These rules apply automatically in every future conversation without repeating them.

**07\. Terminal Integration (! prefix)**

Prefix any message with ! to run it as a terminal command instead of sending it to Claude. Quick way to run tests, check git status, or navigate directories without leaving the Claude Code interface.

**08\. Multi-Model Switching**

Use Opus for planning and architecture decisions. Switch to Sonnet for implementation and execution. Opus thinks deeper but costs more. Sonnet executes faster and cheaper. Plan with the thinker. Build with the builder.

# Productivity Techniques (09 to 18)

**09\. The Reference File Technique**

Instead of describing the code style you want, point to an existing file: "Look at how authentication is implemented in src/auth/login.ts. Implement password reset following the exact same patterns." Claude Code reads the reference and replicates the patterns precisely. Produces far more consistent code than verbal descriptions.

**10\. The Screenshot Debug**

Something looks wrong in the UI? Do not write a paragraph. Screenshot it. Paste with Ctrl+V. Say: "The button is misaligned with the input field. The spacing between cards is inconsistent. Fix both." Visual feedback is faster and more accurate than written descriptions.

**11\. The Test-First Workflow**

"Write tests for a function that calculates discounted prices. Cover: normal discounts, zero discount, 100 percent discount, negative prices, and string inputs. Then implement the function to pass all tests." Tests define behavior before code exists. The implementation is automatically correct because it must pass the predefined tests.

**12\. The Incremental Build**

Never say "build the entire feature." Break it into steps: "Create the database schema." Test. "Build the API endpoint." Test. "Add validation." Test. "Build the frontend form." Test. Five small steps with testing between each one produces dramatically better code than one massive implementation prompt.

**13\. The Codebase Question**

Before implementing anything in an unfamiliar part of the codebase: "Read src/services/ and explain how data flows from the API routes to the database. What patterns are used? What should I know before modifying anything here?" Understanding before building prevents architectural mistakes.

**14\. The Diff Review**

After Claude Code makes changes: "Show me a diff of every file you modified. Explain each change in one sentence." This catches unintended modifications - Claude Code sometimes "helpfully" changes files you did not ask it to touch.

**15\. The Error Paste**

When something breaks, copy the COMPLETE error message and stack trace. Not a summary. The complete output. "I got this error: \[paste full error\]. Diagnose the root cause step by step before suggesting a fix." The step-by-step constraint prevents Claude from jumping to a wrong fix.

**16\. The Undo Checkpoint**

Before every major change: git add . && git commit -m "checkpoint before \[change\]". If Claude Code breaks something, you revert in seconds instead of spending thirty minutes debugging what used to work.

**17\. The Parallel Session**

For large features, open two terminal windows. One runs Claude Code for the backend implementation. The other runs Claude Code for the frontend. Each session has clean, focused context for its domain. Connect the pieces at the end.

**18\. The Documentation Pass**

After completing a feature: "Read every file you created or modified for this feature. Generate comprehensive documentation: what each function does, how they connect, what the expected inputs and outputs are, and any non-obvious design decisions." Documentation generated immediately after building is more accurate than documentation written days later from memory.

# Architecture Techniques (19 to 26)

**19\. The Architecture Audit**

Before starting a new project: "Analyze my project requirements: \[list them\]. Propose 2 different architectural approaches. For each: component diagram, pros, cons, estimated complexity, and what could go wrong. Recommend one with clear reasoning." Making architecture decisions with AI analysis prevents expensive rewrites later.

**20\. The Dependency Check**

Before adding any new package: "I want to add \[package\] to handle \[use case\]. Check: is this actively maintained? Are there known security issues? What is the bundle size impact? Are there lighter alternatives that cover my specific use case?" Prevents bloating your project with unnecessary or risky dependencies.

**21\. The Pattern Enforcer**

Add to your [CLAUDE.md](http://claude.md/): "When creating new files, follow these patterns: API routes follow the structure in src/api/example-route.ts. Database queries use the repository pattern in src/repositories/example-repo.ts. React components follow the structure in src/components/ExampleComponent.tsx." Claude Code reads this and automatically matches your patterns in every new file.

**22\. The Migration Builder**

"I need to change the user table schema: add a 'role' column (enum: admin, editor, viewer, default: viewer) and rename 'name' to 'display\_name'. Generate the migration file, update the repository layer, update all API routes that reference the old schema, and update the TypeScript types. Show me every file that needs to change before making any modifications." Schema changes that touch multiple layers are where Claude Code shines - it tracks all the ripple effects.

**23\. The API Design Review**

"Review my API design: \[paste route definitions\]. Check for: inconsistent naming, missing error responses, endpoints that should be paginated, missing authentication on protected routes, and any REST convention violations. Suggest specific improvements."

**24\. The Security Scan**

"Scan this codebase for security vulnerabilities: SQL injection, XSS, exposed secrets in code or config files, missing input validation, insecure direct object references, and missing rate limiting. For each finding: severity, exact location, why it is dangerous, and the fix."

**25\. The Performance Profiler**

"Analyze this codebase for performance issues: N+1 database queries, missing indexes based on query patterns, unnecessary re-renders in React components, large bundle imports that could be lazy loaded, and API endpoints that should be cached. Prioritize by estimated impact."

**26\. The Refactoring Planner**

"Read src/services/user-service.ts. This file has grown to 800 lines and handles too many responsibilities. Propose a refactoring plan that splits it into focused modules. Show the proposed file structure, what moves where, and verify that no external imports will break. Do NOT start refactoring yet - just show me the plan."

# Workflow Automation (27 to 31)

**27\. The Git Hook Writer**

"Create a pre-commit hook that: runs the linter on staged files, runs type checking, checks for console.log statements in production code, and blocks commits that fail any check. Install it in .husky/pre-commit." Automated quality gates that run every time you commit.

**28\. The CI Pipeline Builder**

"Create a GitHub Actions workflow that: runs on every PR, installs dependencies, runs the full test suite, runs the linter, builds the project, and posts a comment on the PR with the results. Use caching for node\_modules."

**29\. The Environment Setup Script**

"Create a [setup.sh](http://setup.sh/) script that a new developer runs once to set up the entire development environment: install dependencies, create .env from .env.example, set up the local database, run migrations, seed test data, and verify everything works by running the test suite."

**30\. The Release Notes Generator**

"Read the git log since the last tag. Generate release notes organized by: new features, bug fixes, performance improvements, and breaking changes. Write each entry in user-friendly language, not developer jargon. Format as a markdown changelog entry."

**31\. The Database Seed Builder**

"Create a comprehensive seed file for the development database. Include: 5 users (1 admin, 2 editors, 2 viewers), 20 sample projects with realistic data, relationships between entities, and edge cases (archived project, deleted user, project with no members). Make the data realistic, not 'test123'."

# Debug and Recovery (32 to 35)

**32\. The Reproduction Prompt**

"This bug was reported by a user: \[paste bug report\]. Create a minimal reproduction: the exact steps, the expected behavior, the actual behavior. Then write a failing test that captures this bug. Then fix the code to make the test pass."

**33\. The Blame Investigator**

"This function started failing yesterday. Read the git log for this file over the past week. Identify which commit likely introduced the issue and explain what changed. Then suggest the fix."

**34\. The Dependency Conflict Resolver**

"I am getting this dependency conflict: \[paste error\]. Analyze the conflict. Identify which packages require conflicting versions of the shared dependency. Suggest the resolution that requires the fewest changes and explain the tradeoffs."

**35\. The Recovery Mode**

When Claude Code produces a broken implementation and you have been going back and forth for too long: "Stop. Read the original working version of this file from git: \[paste the git show command output\]. Now look at what we have been trying to achieve: \[restate the goal simply\]. Start fresh with a different approach. The previous approach clearly is not working."

Sometimes starting over from a clean state is faster than fixing accumulated mistakes. Know when to use this.

# The Setup That Ties It All Together

When you start a new project, run this sequence:

1. /init - generate the [CLAUDE.md](http://claude.md/) file
2. Add your coding standards and patterns to [CLAUDE.md](http://claude.md/)
3. /memory - add persistent rules you want in every session
4. Plan mode - design the architecture before writing any code
5. Start building incrementally - one feature at a time, tested at each step

This five-minute setup transforms every subsequent hour of development.

# TL;DR

35 techniques. Tested daily. Each one solves a real development problem.

Essential commands for session management. Productivity techniques for faster building. Architecture techniques for better design. Workflow automation for consistent quality. Debug and recovery for when things break.

**Claude Code is the most powerful development tool available. These 35 techniques unlock all of it.**

**This took months of daily use to compile. If it saved you time - you know what to do.**

**Follow me** [@eng\_khairallah1](https://x.com/@eng_khairallah1) **for more developer tools, workflows, and techniques. No fluff. Just what works.**

**hope this was useful for you, Khairallah** **❤️**