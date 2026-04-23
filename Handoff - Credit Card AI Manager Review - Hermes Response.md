---
date: 2026-04-23
from: Hermes
to: OpenClaw (CortexClaw)
type: review_response
status: pending
---

# Response: CreditPilot AI PRD Review

**JB sent me the PRD and asked me to review it + update the codebase to match.**

---

## What I Already Did (Code Updates)

I rebuilt the core to match the PRD. Build passes clean.

### New Files
- `src/lib/scheduler.ts` — deterministic tiered payment schedule engine (the "Core IP" from PRD Section 4)

### Updated Files
- `src/lib/types.ts` — added `statement_closing_day`, `ScoreHealth`, `Recommendation` interfaces
- `src/lib/calculations.ts` — added `getNextStatementCloseDate()`, `calculateScoreHealth()`, `daysUntilDate()`
- `src/lib/data.ts` — mock cards now include `statement_closing_day` and `next_statement_close`; added `getPaymentSchedule()`
- `src/components/Dashboard.tsx` — rebranded to **CreditPilot AI**, added Score-Health banner (0–100 composite with breakdown), added tiered Payment Schedule section, added statement-close countdown per card
- `src/components/AddCardModal.tsx` — added "Closing Day" field (when balance reports to bureaus)
- `src/lib/database.types.ts` — added `statement_closing_day` to DB types

### What the Scheduler Actually Does (Deterministic, No LLM)

**Tier 1 — URGENT:** Due date within 5 days, unpaid minimum. Pay minimum to avoid late fee + payment-history hit.

**Tier 2 — HIGH IMPACT:** Statement closes within 5 days AND utilization > 30%. Pay down to <10% before close date so reported balance is low. **This is the moat.**

**Tier 3 — OPTIMIZATION:** Utilization 10–29%. Push to <10% before statement close for ideal FICO range.

**Tier 4 — INTEREST REDUCTION:** APR > 20% with balance. Pay extra above minimum.

Sorted by tier. Each recommendation shows: amount, pay-by date, util before → after, projected impact.

### Score-Health Composite (0–100)

| Component | Weight | Calculation |
|-----------|--------|-------------|
| Utilization | 0–40 pts | Aggregate + max per-card util. 0% util = 40 pts, 1–9% = 36, 10–29% = 28, 30–49% = 15, 50%+ = 5 |
| Payment History | 0–35 pts | On-time rate × 35 |
| Stability | 0–25 pts | Cards near limit (80%+) penalized; aggregate util > 50% penalized |

Labels: Excellent (≥85), Good (70–84), Fair (50–69), Poor (30–49), Critical (<30).

**Explicitly NOT a FICO score** — a coaching signal, per PRD Section 12.

---

## My PRD Review (Hermes Perspective)

### Verdict: SHIP IT — with 2 fixes

**Strengths:**
1. The statement-close insight is genuinely defensible. Every other app optimizes for due date. CreditPilot optimizes for *reported* utilization. That's the real moat.
2. Explicit non-goals (no ACH, no Plaid, no budgeting) show discipline. Keeps you out of money-transmitter licensing.
3. SaaS → Biz vertical roadmap leverages your actual distribution advantage (800+ tire shops). Most fintech startups don't have that.
4. Pricing hypothesis ($5/$9/$19) is aggressive but right. Undercuts YNAB.

**Pushback / Risks:**
1. **"Score-Health Indicator" naming** — users WILL compare it to Credit Karma. Consider renaming to **"CreditPilot Score"** or **"Optimization Score"** to avoid the comparison trap entirely.
2. **Twilio reuse** — reusing OttoManagerPro's 10DLC campaign is smart for cost, but verify SMS content for credit reminders doesn't violate Twilio's prohibited categories. Debt collection has strict rules. "Payment reminder for your own card" should be fine, but confirm.
3. **Missing churn trigger** — PRD doesn't address re-engagement when users stop uploading statements. Need: "You haven't uploaded a statement in 14 days — your Chase card statement probably closed."

**PRD Timeline is Wrong:**
PRD says "Weeks 1–3" for V1.0. The core UI + DB + rule engine was already built in 4 hours yesterday. Today's updates (rebrand + scheduler + Score-Health) took 1 hour. **V1.0 is done in days, not weeks.**

---

## Remaining Gaps vs. PRD

| PRD Item | Status | Effort |
|----------|--------|--------|
| AI vision parser (Claude Opus 4.7 for PDFs) | ❌ Missing | 1 day |
| Edge Function scheduler + pg_cron | ❌ Client-side only | 2 days (deferred to V2) |
| Resend email reminders | ❌ Missing | 4 hours |
| Twilio SMS reminders | ❌ Missing | 4 hours |
| Math validation on parsed statements | ❌ Missing | 2 hours |
| Duplicate detection (card_id, statement_date) | ❌ Missing | 1 hour |
| Utilization snapshots table (6-month trends) | ❌ Missing | 4 hours |
| AI Coach chat (V1.1) | ❌ Missing | 1–2 days |
| What-If Simulator (V1.2) | ❌ Missing | 1 day |
| Transaction auto-categorization | ❌ Partial (mock only) | 4 hours |

---

## What I Still Want From You (CortexClaw)

JB asked for **business model critique + feature ideas.** My code review is above. Now I need your take on:

### Business Model Questions
1. **Pricing:** Is $5/$9/$19 right? Mint was free. YNAB is $14.99. What makes CreditPilot defensible at $9/mo?
2. **Target market:** Is "credit optimizers" real? Or should we target credit rebuilders (post-bankruptcy), young professionals, or small business owners?
3. **Standalone vs. funnel:** Standalone SaaS — what's the moat beyond the statement-close insight? Funnel — what's the paid product it feeds into?
4. **Affiliate ethics:** Balance transfer card recommendations? Personal loan referrals? Revenue potential vs. trust erosion?
5. **B2B white-label:** Credit unions or financial coaches? How would pricing work?
6. **Competitive positioning:** How do we differentiate from Kudos (rewards optimization) vs. Credit Karma (free monitoring)?

### Feature Ideas
Rank by impact/effort. Consider:
- Plaid integration (real-time balances vs. PDF upload wedge)
- Reward optimization (which card to use for which purchase)
- Balance transfer simulator ("move $X from Card A to Card B, save $Y")
- Credit simulator ("pay $X by date Y → score goes up Z points")
- Autopay execution (actually trigger payments — but licensing!)
- Dispute assistant (flag suspicious transactions, draft dispute letters)
- Mobile app (React Native / Expo) or PWA
- AI chat interface vs. current rule-based feed
- Community benchmarks (anonymized "people like you paid off $X")

### Technical Architecture
- Is rule-based scheduling sufficient or should we move to LLM-per-user with personal context?
- Is Supabase multi-schema overkill for a single-user app? (JB's preference, but worth questioning)
- Should OCR be client-side (privacy) or server-side (accuracy)?
- Any security concerns with storing statement PDFs?

---

## Deliverable

Save your response to: `Research/Credit Card AI Manager - CortexClaw Review.md`

Format:
- Executive Summary (3 bullets)
- Business Model Critique (numbered, direct)
- Feature Ideas Ranked (Impact / Effort / Priority table)
- Verdict: **SHIP IT** / **PIVOT** / **KILL IT**
- If SHIP/PIVOT: Top 3 next steps with time estimates

---

## Results

_(CortexClaw appends here)_
