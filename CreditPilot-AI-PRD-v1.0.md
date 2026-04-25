# CreditPilot AI
## AI-Powered Credit Card Management & Score Optimization Platform

**Version:** PRD v1.0
**Date:** April 2026
**Owner:** Junaid Burke (JBurke)
**Status:** Draft — Ready for Review
**Target Platform:** Web (Next.js) — Mobile-first responsive
**Schema:** `creditpilot` (new schema in CustomerTesting Supabase project)

---

## Document Control

| Field | Value |
|---|---|
| Product | CreditPilot AI |
| Document | Product Requirements Document (PRD) |
| Version | PRD v1.0 |
| Date | April 2026 |
| Owner | Junaid Burke (JBurke) |
| Status | Draft — Ready for Review |
| Target Platform | Web (Next.js) — Mobile-first responsive |
| Schema | `creditpilot` (new schema in CustomerTesting Supabase project) |

---

## 1. Executive Summary

CreditPilot AI is a personal credit-card command center that ingests credit card statements, extracts structured data using AI vision, and generates an optimized payment schedule designed to maximize FICO score impact. Unlike traditional budgeting tools which focus on spending, CreditPilot is optimized for one thing: raising the user's credit score through disciplined utilization management and strategic payment timing.

The core insight: FICO scores are calculated based on the balance reported on each card's statement closing date, not the due date. Most consumers pay on time but still carry high reported utilization because they don't know *when* to pay. CreditPilot solves this by reading each card's statement cycle and telling the user exactly when and how much to pay — card by card — to keep reported utilization under the ideal 10% threshold.

Version 1 is built as a personal tool for the founder, with architecture designed from day one to extend into a multi-tenant SaaS serving couples, families, and small-business owners juggling multiple cards.

### 1.1 Problem Statement

- Consumers have 3–10+ credit cards and no unified view of utilization across them.
- Paying the minimum or even the full statement balance on the due date often still reports high utilization, dragging down FICO scores by 20–100+ points.
- Each card's statement closing date differs — tracking this manually across cards is tedious and error-prone.
- Existing tools (Mint, Credit Karma, Experian) show scores and transactions but do not tell users what specific action to take, on which card, by what date, to actually improve the score.
- Credit-score improvement advice online is generic; it ignores the user's actual card limits, balances, APRs, and statement cycles.

### 1.2 Solution Overview

A web application where the user:

1. Adds each credit card once (limit, statement day, due day, APR, issuer).
2. Uploads PDF statements as they arrive. AI parses them into structured data — balance, min payment, transactions, fees, interest charged.
3. Views a unified dashboard: per-card utilization, aggregate utilization, projected reported utilization, score-health indicator.
4. Receives a prioritized payment schedule: "Pay $X on Card Y by date Z — reason: keeps reported utilization at N%."
5. Gets AI coaching: which card is hurting the score most, which to pay down first, which to stop using, which to request a limit increase on.

### 1.3 Why Now

- AI vision (Claude Opus, GPT-4o) can now parse credit card statement PDFs with >95% accuracy at near-zero cost.
- Consumer credit card debt hit an all-time high in 2025 — utilization management is increasingly urgent.
- The founder has existing platform infrastructure (Supabase multi-schema, Clerk, Next.js, Twilio, Resend) that makes this a weeks-not-months build.
- Feeds directly into the AI founder brand narrative on X/LinkedIn — a shippable personal-use product that doubles as content.

---

## 2. Target Users

### 2.1 Primary Persona (V1 — Personal)

**The Founder / Power User.** Tech-savvy, carries 5–10 cards strategically for rewards, cash flow, and credit-building. Wants to keep FICO above 800. Has no time to track statement cycles manually and is unwilling to trust Mint/Credit Karma with bank credentials.

**Jobs-to-be-Done:**

- Know before statement cuts: "How much do I need to pay on each card to report low utilization?"
- Never pay a late fee or miss a due date across any card.
- Identify which card is dragging the score down this month.
- Maintain a historical record of every statement in one searchable place.

### 2.2 Secondary Personas (SaaS Expansion)

**Couples / Households.** Two adults, 8–15 cards combined, some joint, some individual, some authorized-user. Needs shared visibility and per-person payment assignment.

**Small Business Owners** (incl. auto-shop owners in the Burke portfolio). Mixes personal and business cards, often with high monthly churn. Needs clean separation of personal vs. business utilization and tax-ready expense categorization. Overlap with OttoManagerPro / TireManagerPro / CleanBuddyPro user base is a natural distribution channel.

**Credit Counselors / Financial Coaches.** White-label opportunity. Coach manages a dashboard of clients, each with their own cards and payment plans. Pricing: per-client seat.

---

## 3. Core Features

Features are scoped into V1 (ship-to-self), V1.1 (within 30 days of V1), and V1.2 (deferred). Priority P0 = must have for V1 launch.

| Feature | Description | Priority |
|---|---|---|
| **Card Registry** | Add/edit/delete credit cards. Store: issuer, last 4, credit limit, statement day, due day, APR, nickname, color tag. | P0 (V1) |
| **PDF Statement Upload** | Drag-drop or file-picker upload of credit card statement PDFs. Supabase Storage with RLS. Duplicate detection by (card_id, statement_date). | P0 (V1) |
| **AI Statement Parser** | Claude vision API extracts: statement period, closing date, due date, new balance, previous balance, min payment, fees, interest, payments credited, and transaction list. Returns strict JSON. | P0 (V1) |
| **Utilization Dashboard** | Per-card utilization %, aggregate utilization %, color-coded thresholds (green <10%, yellow 10–29%, red ≥30%), trend over last 6 months. | P0 (V1) |
| **Payment Schedule Engine** | Generates ranked list of recommended payments: which card, how much, by what date, and the reason (avoid late fee / reduce reported utilization / reduce interest). | P0 (V1) |
| **Score-Health Indicator** | Composite 0–100 score based on: aggregate utilization, per-card utilization, on-time payment history, number of cards near limit. Not a FICO score — a coaching signal. | P0 (V1) |
| **Payment Reminders** | Email (Resend) and optional SMS (Twilio) reminders: 3 days before statement close, 5 days before due date. Configurable per card. | P0 (V1) |
| **AI Coach Chat** | Chat interface grounded in user's actual cards and statements. Ask: "Which card is hurting my score most?" "Can I afford to pay off Chase Freedom this month?" "Should I request a limit increase on Amex?" | P1 (V1.1) |
| **Transaction Tagging** | AI auto-categorizes parsed transactions. User can re-tag. Monthly category breakdown. | P2 (V1.2) |
| **What-If Simulator** | "If I pay $X on Card Y by date Z, what will my aggregate reported utilization be next cycle?" Sliders for each card. | P2 (V1.2) |

---

## 4. The Payment Schedule Engine (Core IP)

This is the differentiator. Every other credit-card tool shows data; CreditPilot prescribes action. The engine runs nightly and whenever a new statement is uploaded, producing a ranked queue of recommended payments.

### 4.1 Credit Score Model (Simplified)

FICO is a black box, but the inputs are public:

- **Payment History (35%)** — never miss a due date.
- **Credit Utilization (30%)** — reported balance ÷ credit limit. Per-card AND aggregate.
- **Length of Credit History (15%)** — out of scope; keep oldest cards open.
- **Credit Mix (10%)** — out of scope for V1.
- **New Credit (10%)** — track hard inquiries; out of scope for V1.

CreditPilot V1 optimizes the first two factors directly (payment timing + utilization).

### 4.2 The Statement Date Insight

FICO is fed by the balance each issuer reports to the bureaus, typically on or shortly after the statement closing date. A user can pay the full balance on the due date every month and still show 60% utilization on their credit report — because the statement already cut at 60%.

The payment scheduler therefore generates TWO payment recommendations per card per cycle:

1. **Pre-statement payment:** pay down the balance 3–5 days BEFORE the statement closing date, targeting <10% utilization on that card.
2. **Due-date payment:** pay the remaining statement balance by the due date to avoid interest and late fees.

### 4.3 Prioritization Logic

Recommended payments are ranked by score impact per dollar:

- **Tier 1 (critical):** Any card with a due date in the next 5 days and unpaid minimum. Missing these is catastrophic for payment history.
- **Tier 2 (high impact):** Any card where statement closes in the next 5 days AND projected utilization > 30%. Bring utilization to <10% if cash allows, otherwise to <30%.
- **Tier 3 (optimization):** Cards with utilization 10–29% — push to <10% if surplus cash available. Ideal FICO utilization is 1–9%.
- **Tier 4 (interest reduction):** High-APR cards carrying a revolving balance — pay above minimum to reduce interest cost.

### 4.4 Recommendation Output Shape

Each recommendation surfaced in the UI includes:

- Card name + last 4
- Recommended payment amount ($)
- Recommended pay-by date
- Reason, in plain English
- Projected impact (utilization before → after)
- Priority tier (color-coded)
- One-click "mark as paid" (logs the payment event; does NOT initiate ACH — see Section 9)

---

## 5. AI Architecture

CreditPilot uses AI where it adds unique value (parsing unstructured statement PDFs, natural-language coaching) and deterministic code everywhere else (scheduling, math, reminders). This keeps the critical path predictable and cheap.

| Stage | Model / Service | Purpose |
|---|---|---|
| **Ingestion** | Supabase Storage (PDF) → Base64 encoder | Upload PDF, encode to base64, enqueue for parsing. Max 10MB per file. |
| **Extraction** | Claude Opus 4.7 (vision) | Parse PDF into strict JSON: statement_date, due_date, new_balance, min_payment, fees, interest, transactions[]. |
| **Validation** | Zod schema + rule checks | Validate JSON shape, check math (previous + charges − payments = new), flag for human review if off. |
| **Scheduling** | Deterministic TypeScript engine | Rule-based priority queue — no LLM in the critical path. Predictable, testable, auditable. |
| **Coaching** | Claude Opus (chat) | AI Coach answers user questions grounded in their actual card + statement data via RAG. |

### 5.1 Statement Parser Prompt Contract

The parser returns strict JSON matching the `creditpilot.statements` schema. Prompt enforces:

- No prose. JSON only, no code fences.
- All dollar amounts as numbers (not strings with $).
- All dates as ISO-8601.
- Missing fields return null, never empty strings.
- Transactions array preserves original order.
- If parsing confidence is low, return an error object with reason.

### 5.2 Why Not Use an LLM for Scheduling

The scheduling engine is deterministic on purpose. Three reasons:

1. **Auditability** — the user can see exactly why a recommendation was made.
2. **Cost** — scheduling runs on every statement + nightly; LLM calls would add up.
3. **Reliability** — money decisions should not hallucinate. Rules only.

The LLM is used only for the AI Coach feature (natural-language Q&A), and there it is grounded in the user's actual data through retrieval, never free-form.

---

## 6. Data Model (Supabase: `creditpilot` schema)

Follows the Burke multi-schema platform pattern: new schema `creditpilot` in the CustomerTesting Supabase project, RLS enforced on every table with `user_id = auth.uid()` or (for child tables) via a join to a parent row owned by the user.

| Table | Key Fields | Notes |
|---|---|---|
| **cards** | id, user_id, issuer, last4, credit_limit, statement_day, due_day, apr, nickname | One row per card per user. statement_day/due_day are day-of-month ints (1–31). |
| **statements** | id, card_id, statement_date, due_date, new_balance, min_payment, fees, interest, pdf_url, parsed_json | Unique on (card_id, statement_date). Full parsed JSON stored for re-processing. |
| **transactions** | id, statement_id, date, merchant, amount, category, raw_description | Denormalized from statements.parsed_json for query convenience. |
| **payments** | id, card_id, amount, paid_on, confirmation_ref, note | User-logged payment events. No ACH; this is a record, not an action. |
| **recommendations** | id, card_id, tier, recommended_amount, recommended_by_date, reason, status, generated_at | Output of the scheduler. Regenerated on each run; historical kept for audit. |
| **utilization_snapshots** | id, user_id, snapshot_date, per_card_jsonb, aggregate_pct, health_score | Daily snapshot for trend charts. Enables 6-month utilization history views. |
| **notifications** | id, user_id, channel, type, sent_at, payload_jsonb | Audit log of all reminders sent (email + SMS). Supports dedup. |

### RLS Policy Template

Every table has four policies: SELECT, INSERT, UPDATE, DELETE — all scoped to `user_id = auth.uid()`. Child tables (statements, transactions, recommendations) use a security-definer function that validates parent ownership. Storage buckets for PDF uploads use a folder-per-user pattern: `/user_id/card_id/statement_date.pdf`.

### Sensitive Data Handling

- Never store full card numbers. last4 only.
- PDF originals encrypted at rest via Supabase Storage default.
- No bank login credentials stored (V1 is manual upload; SaaS V2 Plaid evaluation deferred).
- `parsed_json` scrubbed of any full PAN or CVV if accidentally present.

---

## 7. User Experience & Key Screens

### 7.1 Onboarding (≤ 3 minutes)

1. Sign up with Clerk (email / Google).
2. Add first card — issuer, nickname, last 4, credit limit, statement day, due day, APR.
3. Upload first statement PDF — optional but recommended during onboarding.
4. Preview parsed data, confirm.
5. Land on dashboard with first recommendation ready.

### 7.2 Dashboard (Home)

- Top banner: Score-Health indicator (0–100) + aggregate utilization %.
- Top-priority recommendation card (Tier 1/2) — large, one action.
- Grid of card tiles: each shows nickname, last 4, current balance, limit, utilization %, next due date.
- Utilization trend chart (6 months).
- Upcoming statement closings + due dates timeline.

### 7.3 Card Detail Screen

- Card header with issuer, limit, APR.
- Statements history list (most recent first) — click any statement for full detail.
- All transactions across statements, filterable by category.
- Payment history log.
- Card-specific recommendations.

### 7.4 Upload Flow

- Drag-drop zone or file picker.
- Upload progress → parsing progress (realtime via Supabase Realtime).
- Preview screen: extracted fields on the right, PDF render on the left. User confirms or corrects.
- Save → triggers scheduler re-run → updated dashboard.

### 7.5 AI Coach (V1.1)

- Chat-style interface in a side drawer.
- Suggested prompts: "Which card hurts my score most?", "Can I pay off Chase this month?", "Should I close my oldest card?"
- Responses cite the specific card and statement data used.

---

## 8. Technical Architecture

| Layer | Technology | Rationale |
|---|---|---|
| **Frontend** | Next.js 15 (App Router), TypeScript, Tailwind, shadcn/ui | Founder's existing stack; portfolio consistency. |
| **Auth** | Clerk | Already integrated in other Burke products; zero-config MFA. |
| **Database + Storage** | Supabase (CustomerTesting → creditpilot schema) | Multi-schema platform pattern. RLS, realtime, storage bundled. |
| **AI — Parsing** | Anthropic Claude Opus 4.7 (vision, PDF input) | Best-in-class PDF parsing; structured JSON output reliable. |
| **AI — Coach** | Anthropic Claude Opus 4.7 (chat) | Grounded Q&A over user's card + statement data. |
| **Scheduler** | Supabase Edge Function (Deno) + Postgres cron | Runs nightly; also triggered on statement upload. No LLM in path. |
| **Email** | Resend | Already proven on Burke's Tire site. |
| **SMS** | Twilio (A2P 10DLC via OttoManagerPro brand) | Reuse approved 10DLC campaign for cost + speed. |
| **Hosting** | Vercel | Zero-config Next.js deploy; edge functions for low latency. |
| **Observability** | Vercel Analytics + Supabase logs | Sufficient for V1; add Sentry if error rate warrants. |

### 8.1 Reuse From Existing Platform

- **Supabase project:** CustomerTesting (existing). Add new `creditpilot` schema.
- **Clerk tenant:** reuse Burke Family portal Clerk instance.
- **Twilio:** reuse approved OttoManagerPro A2P 10DLC campaign for SMS reminders.
- **Resend:** reuse existing domain and templates.
- **CLAUDE.md / AGENTS.md hierarchy:** inherit from platform root.

### 8.2 New Components

- **PDF parsing Edge Function** — stateless, idempotent, retries on vision API failure.
- **Scheduling Edge Function** — runs on cron (Postgres pg_cron, daily 06:00 local) and on statement insert trigger.
- **Notification dispatcher** — reads due reminders, sends via Resend/Twilio, writes to notifications table.

---

## 9. Out of Scope for V1 (Explicit Non-Goals)

The MVP-first discipline encoded in CLAUDE.md applies. The following are explicitly NOT in V1:

- **ACH / Bill Pay initiation** — CreditPilot never moves money. It tells the user what to pay; the user pays via their bank. This sidesteps money-transmitter licensing entirely.
- **Plaid / live bank feed integration** — evaluated for V2 SaaS, not V1. Manual PDF upload is the wedge.
- **Credit report / FICO score pull** — no Experian / TransUnion / Equifax integration. The score-health indicator is a coaching signal, not a FICO score.
- **Investment / savings / budgeting** — this is not Mint. Focus is credit cards only.
- **Multi-user / household support** — V1 is single-user. SaaS V2 adds shared households.
- **Tax / business expense export** — deferred to the small-business SaaS vertical.
- **Mobile native apps** — responsive web only for V1. PWA if justified.
- **Card recommendation / affiliate marketplace** — no "apply for this card" upsells in V1.

---

## 10. Roadmap

| Phase | Timing | Scope |
|---|---|---|
| **V1.0** | Weeks 1–3 | Card registry, PDF upload, AI parser, utilization dashboard, deterministic scheduler, email reminders, score-health indicator. Personal use only. |
| **V1.1** | Weeks 4–6 | AI Coach chat, SMS reminders, utilization trend charts, manual payment logging, what-if sliders (basic). |
| **V1.2** | Weeks 7–10 | Transaction tagging, category breakdown, CSV export, what-if simulator (full), statement search. |
| **V2.0 (SaaS)** | Months 3–6 | Multi-user households, shared cards, couples mode, Stripe billing, freemium tier, onboarding marketing site. Plaid integration evaluation. |
| **V2.1 (Biz)** | Months 6–9 | Small-business vertical: personal+business card separation, expense categorization, tax-ready exports. Cross-sell to Burke SaaS portfolio customers. |

---

## 11. Success Metrics

### 11.1 V1 (Personal) Success

- Founder uploads every statement for 90 consecutive days.
- Aggregate reported utilization drops below 10% within 2 full statement cycles.
- Zero missed due dates across all cards over 90 days.
- Measurable FICO score movement (+20 points target) within 3 cycles.

### 11.2 V2 (SaaS) Leading Indicators

- Week 1 retention ≥ 60% of signups.
- Activation rate (first statement parsed) ≥ 70% of signups.
- ≥ 40% of users uploading 2+ statements within 30 days.
- Free-to-paid conversion ≥ 5% by month 3.

### 11.3 Product Health

- Statement parse accuracy ≥ 95% (field-level F1).
- Scheduler runs complete in < 2 seconds per user.
- Reminder delivery success rate ≥ 99%.
- Zero data incidents involving card numbers.

---

## 12. Risks & Mitigations

| Risk | Likelihood / Impact | Mitigation |
|---|---|---|
| PDF parser misreads a statement | Medium / Medium | Math validation (prev+charges−payments=new). Low-confidence parses flagged for user review before saving. |
| User perceives score-health score as a FICO score | Medium / High (trust) | Clear labeling everywhere: "Not a FICO score". Link to "How this is calculated". |
| Regulatory scope creep (money transmitter) | Low / High | No ACH, no money movement. Product strictly records and recommends. Revisit with counsel before V2 Plaid. |
| Vision API cost blows up | Low / Low | Parse once, cache JSON. Typical user uploads ~10 PDFs/month. Budget < $1/user/month. |
| Feature creep (TireManagerPro pattern) | Medium / High | Explicit out-of-scope list (Section 9). CLAUDE.md MVP discipline. Weekly scope review. |
| Privacy concerns (statements contain sensitive data) | Medium / High (trust) | Per-user storage folders with RLS. PDF encryption at rest. last4-only card storage. Public security statement before V2 launch. |

---

## 13. Open Questions

- Should V1 support business cards or personal-only? *(Recommendation: personal only; defer business to V2.1.)*
- Is the score-health indicator specific enough to be useful, or does it need to tie to a real bureau pull in V1.1? *(Recommendation: keep it a coaching signal for V1.)*
- Should reminders be opt-in per card or global? *(Recommendation: global default, per-card override.)*
- How far back should users be able to upload statements? *(Recommendation: unlimited, but scheduler only acts on last 3 cycles.)*
- Should the AI Coach have write access (e.g., "log this payment")? *(Recommendation: read-only in V1.1; add write with confirm-before-action in V1.2.)*
- What pricing for V2 SaaS? *(Working hypothesis: $5/mo personal, $9/mo household, $19/mo small-business.)*

---

## Appendix A — Sample Scheduler Output

*Illustrative example of what the user sees on the dashboard on a given day:*

**Tier 1 — URGENT**
- Amex Platinum (…1234) — Pay **$147 min** by **Apr 26** (4 days). Reason: avoid $40 late fee and payment-history hit.

**Tier 2 — HIGH IMPACT**
- Chase Sapphire Preferred (…5678) — Pay **$1,820** by **May 2** (before statement closes May 5). Reason: drops reported utilization 62% → 8%. Estimated score impact: significant.

**Tier 3 — OPTIMIZATION**
- Citi Double Cash (…9012) — Pay **$340** by **May 8**. Reason: drops this card's reported utilization 22% → 4%.

**Tier 4 — INTEREST REDUCTION**
- Store Card (…3456) — Pay **$200 extra** on next due date. Reason: 28.99% APR; paying above minimum saves $46 interest next cycle.

---

## Appendix B — Glossary

- **Statement Closing Date** — The last day of a billing cycle; balance on this date is typically what gets reported to credit bureaus.
- **Due Date** — Payment deadline. Paying by this date avoids late fees but does NOT affect reported utilization.
- **Utilization** — Balance divided by credit limit. Tracked per-card and aggregate across all cards.
- **Reported Utilization** — The utilization figure actually sent to credit bureaus — usually based on statement closing date balance.
- **A2P 10DLC** — Application-to-Person 10-Digit Long Code; the US SMS compliance framework Twilio uses. CreditPilot reuses the OttoManagerPro-approved brand.

---

*End of Document — CreditPilot AI PRD v1.0*
*Burke Family AI Portfolio*
