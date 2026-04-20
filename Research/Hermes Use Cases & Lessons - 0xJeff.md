# My 2-Week Hermes Use Cases, Learnings & Mistakes
**Source:** [0xJeff @0xJeff](https://x.com/0xJeff/status/2046164193326628880) | 10.7K views
**Date:** April 2026

---

## The Core Value Prop

> "The coolest thing about Hermes is that it learns things about you — your preference, your way of doing things, your workflows. It synthesizes all of that and create skills out of them (usually proactively, without you having to do anything)."
>
> "Self-learning + self-remembering make Hermes very useful, the agent gets better every time it interacts with you."

**But:** The number of skills and cron jobs can expand fast. Changing config with 30+ skills gets messy. Debugging errors becomes a time sink.

---

## Use Case 1 — Fetch & Analyze X Insights

Runs multiple cron jobs every morning following X accounts in macro, geopolitics, tech, and AI.

**Stack:** Bird CLI + EditThisCookie Chrome Extension

**Mistake made:** Bird CLI has both read AND write permissions. Hermes hallucinated multiple times and posted "test" / random numbers to his timeline. Tried wrapping it to read-only — didn't work, still posted.

**Fix:** Switched to official X API. Costs ~$0.50/day but has clear permission settings. Peace of mind >省钱.

> "Despite having to pay $0.5 each day for X API credits, I can sleep much more soundly now cuz X API has clear permission settings."

---

## Use Case 2 — Break Down X Bookmarks

**Problem:** Bookmarks 10-20 posts/day. Before AI, revisited maybe 1-2. The rest went stale.

**New workflow:**
1. X API → fetch bookmarks list with tweet text + linked URLs
2. Browser Harness → navigate to each article URL → extract full text
3. LLM → summarize each article
4. Output → daily report + store insights in wiki

**Note:** X API v2 can't read X articles — only fetches `t.co` links. Browser Harness fills that gap by controlling Chrome like a human, clicking into articles.

---

## Use Case 3 — Reflect

> "One of the coolest thing you could do with Hermes is 'Reflect' — the agent can synthesize past information, preferences, connects relationships, detect patterns, and provides you with actionable analysis."

**Requires:** External memory provider

**Jeff's pick:** [Hindsight](https://agentnews.beehiiv.com/p/hindsight) — #1 for recall accuracy on long-horizon, multi-session, large-scale memory tasks.

**Output:** Top 5 Daily insights with signals + why it matters for him.

---

## Other Tools & Learnings

### Tools
| Tool | Purpose |
|------|---------|
| **last30dayskill** | Get last 30 days of activity on X, TikTok, IG, Reddit. No API needed. |
| **Coingecko + Defillama** | Real-time DeFi/market data |
| **Built-in `delegate_task`** | Long-running tasks |
| **Opencode Go** | $5 first month, enough credits to set things up |

### Critical Lessons (What NOT to Do)

> "Don't link Hindsight to Openrouter, I did this and connected it to Claude Sonnet 4.6. It burned through $50+ worth of tokens in a day. RIP"

> "If you're using Bird CLI, make sure to enable only read function. Tells it to remove write function to avoid it hallucinating and posting things for you"

> "If you're using Browser Harness, practice extreme cautions. Use isolated/fresh browser, don't share sensitive credentials with it. Don't let it browse thru the internet randomly"

---

## What's Next

1. **Pre-call context** — context on a project/team before calls. Plugs into social media, past transcripts & notes. 30-60 mins before the call.
2. **Prediction markets strategy** — low-risk, compounding strat for better R/R on DeFi lending positions.

---

## The Takeaway

> "The longer I use Hermes, the more the important of tokens management became clear. I don't know if it's really worth it to plug into GPT5.4 or Opus 4.7 at all given the prices. Open models work well so far and their subscriptions have been great. There's no block/ban on agent harnesses so I could freely try things."
>
> "Part of the challenge of using AI is making sure I don't burn too much money for nothing. It's balancing what I get (which is productivity boost + more learning) to what I pay for (which is inference cost + time/headaches fixing bugs)."
>
> "Claude is getting so expensive man. It's fast, it's useful, it's great design but it burns so much tokens. I've been using Claude Code to ship websites for dashboards, for my travels, to find activities. It feels good for one-off tasks so I'll probably keep the subs around but already downgraded to $20 package."

---

**Credit:** [@0xJeff](https://x.com/0xJeff)
**Original thread:** https://x.com/0xJeff/status/2046164193326628880
