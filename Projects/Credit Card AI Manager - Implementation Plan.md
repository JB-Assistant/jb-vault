---
title: "Credit Card AI Manager — Implementation Plan"
date: 2026-04-22
author: Hermes
status: draft
---

# Credit Card AI Manager — Implementation Plan

> **For Hermes:** Use subagent-driven-development skill to implement this plan task-by-task.

**Goal:** Build a personal credit card management system where users upload PDF statements, AI extracts data, schedules payments, and optimizes credit score strategy.

**Architecture:** Next.js web app + Supabase backend + OCR/AI extraction layer + Google Calendar integration. Reuses existing Next.js/Supabase/Claude stack from OttoManagerPro/TireManagerPro.

**Tech Stack:** Next.js 14 (App Router), TypeScript, Supabase (multi-schema), Clerk auth, Claude API, Google Calendar API, OCR (Tesseract/pdf2image or reuse existing PDF-TTS OCR pipeline).

---

## Credit Score Model (Built-In Knowledge)

The AI suggestions are based on FICO scoring weights:

| Factor | Weight | What We Track | Optimization Strategy |
|--------|--------|---------------|----------------------|
| **Payment History** | 35% | On-time payments, missed payments | Never miss due dates; auto-schedule payments 3 days before due |
| **Credit Utilization** | 30% | Balance / Limit per card, aggregate | Keep individual cards <30%, ideally <10%; pay down highest utilization first |
| **Length of History** | 15% | Account age, oldest account | Warn before closing old cards; track average age |
| **Credit Mix** | 10% | Types of credit (revolving, installment) | Flag if only one type; suggest diversification |
| **New Credit** | 10% | Hard inquiries, new accounts | Warn about inquiry impact before suggesting new applications |

**Key Rules the AI Enforces:**
1. Always pay at least minimum by due date (payment history = 35%)
2. Prioritize payments to cards with highest utilization ratio (utilization = 30%)
3. Pay more than minimum on highest-APR cards when possible (interest savings)
4. Never recommend closing oldest card (length of history = 15%)
5. Flag if aggregate utilization crosses 30% threshold
6. Suggest optimal payment distribution when cash is limited

---

## Database Schema (Supabase Multi-Schema)

### Schema: `credit_manager`

```sql
-- Credit cards table
create table credit_manager.cards (
  id uuid primary key default gen_random_uuid(),
  user_id uuid references auth.users not null,
  card_name text not null,              -- "Chase Freedom Unlimited"
  issuer text not null,                 -- "Chase"
  last_four text not null,              -- "4242"
  credit_limit decimal(12,2) not null,
  apr decimal(5,2) not null,            -- 24.99
  annual_fee decimal(12,2) default 0,
  statement_day integer not null,       -- 15th of month
  due_day integer not null,             -- 10th of next month
  autopay_enabled boolean default false,
  autopay_amount text default 'minimum', -- 'minimum' | 'statement_balance' | 'full_balance'
  is_primary boolean default false,     -- longest-held card (protect this)
  opened_at date,                       -- account opening date
  closed_at date,                       -- null = active
  created_at timestamptz default now(),
  updated_at timestamptz default now()
);

-- Statements (one per card per month)
create table credit_manager.statements (
  id uuid primary key default gen_random_uuid(),
  card_id uuid references credit_manager.cards not null,
  statement_date date not null,
  statement_pdf_url text,               -- storage path
  statement_balance decimal(12,2) not null,
  minimum_payment decimal(12,2) not null,
  payment_due_date date not null,
  transactions_count integer,
  ocr_raw_text text,                    -- extracted text from PDF
  extracted_at timestamptz default now(),
  created_at timestamptz default now()
);

-- Individual transactions from statements
create table credit_manager.transactions (
  id uuid primary key default gen_random_uuid(),
  statement_id uuid references credit_manager.statements not null,
  transaction_date date not null,
  description text not null,
  category text,                        -- auto-categorized by AI
  amount decimal(12,2) not null,
  is_interest_charge boolean default false,
  is_late_fee boolean default false,
  is_annual_fee boolean default false,
  created_at timestamptz default now()
);

-- Payment history (track what was paid, when, and impact)
create table credit_manager.payments (
  id uuid primary key default gen_random_uuid(),
  card_id uuid references credit_manager.cards not null,
  statement_id uuid references credit_manager.statements,
  amount decimal(12,2) not null,
  paid_at date not null,
  scheduled_for date,                   -- if future-scheduled
  is_autopay boolean default false,
  status text default 'scheduled',      -- 'scheduled' | 'completed' | 'missed' | 'cancelled'
  impact_on_utilization decimal(5,2),   -- % reduction in utilization
  created_at timestamptz default now()
);

-- Credit score tracking (user enters periodically, AI analyzes trends)
create table credit_manager.score_snapshots (
  id uuid primary key default gen_random_uuid(),
  user_id uuid references auth.users not null,
  score integer not null,               -- 300-850
  source text not null,                 -- 'experian' | 'transunion' | 'equifax' | 'credit_karma'
  snapshot_date date not null,
  factors jsonb,                        -- {utilization: 25, payment_history: 98, ...}
  created_at timestamptz default now()
);

-- AI suggestions / recommendations
create table credit_manager.ai_suggestions (
  id uuid primary key default gen_random_uuid(),
  user_id uuid references auth.users not null,
  type text not null,                   -- 'payment_strategy' | 'utilization_alert' | 'spending_insight' | 'score_improvement' | 'card_closure_warning'
  priority text default 'medium',       -- 'low' | 'medium' | 'high' | 'critical'
  title text not null,
  description text not null,
  recommended_action text,
  projected_impact text,                -- "+15 points in 30 days" or "Save $47 interest"
  is_read boolean default false,
  is_actioned boolean default false,
  created_at timestamptz default now()
);

-- RLS policies
alter table credit_manager.cards enable row level security;
alter table credit_manager.statements enable row level security;
alter table credit_manager.transactions enable row level security;
alter table credit_manager.payments enable row level security;
alter table credit_manager.score_snapshots enable row level security;
alter table credit_manager.ai_suggestions enable row level security;

-- Each user only sees their own data
create policy "Users own their cards" on credit_manager.cards for all using (auth.uid() = user_id);
create policy "Users own their statements" on credit_manager.statements for all using (card_id in (select id from credit_manager.cards where user_id = auth.uid()));
create policy "Users own their transactions" on credit_manager.transactions for all using (statement_id in (select s.id from credit_manager.statements s join credit_manager.cards c on s.card_id = c.id where c.user_id = auth.uid()));
create policy "Users own their payments" on credit_manager.payments for all using (card_id in (select id from credit_manager.cards where user_id = auth.uid()));
create policy "Users own their scores" on credit_manager.score_snapshots for all using (auth.uid() = user_id);
create policy "Users own their suggestions" on credit_manager.ai_suggestions for all using (auth.uid() = user_id);
```

---

## Implementation Tasks

### Phase 1: Foundation (Database + Auth)

#### Task 1: Create Supabase schema and tables
**Objective:** Set up the `credit_manager` schema with all tables and RLS.

**Files:**
- Create: `supabase/migrations/20260422_credit_manager_schema.sql`

**Step 1: Write migration file**
(See schema above — copy-paste complete SQL)

**Step 2: Apply migration**
```bash
supabase db push
```

**Step 3: Verify tables exist**
```sql
select * from information_schema.tables where table_schema = 'credit_manager';
-- Expected: 6 tables listed
```

**Step 4: Commit**
```bash
git add supabase/migrations/
git commit -m "feat(credit): add credit_manager schema with 6 tables and RLS"
```

---

#### Task 2: Create TypeScript types from schema
**Objective:** Generate Zod schemas and TypeScript types for type safety.

**Files:**
- Create: `apps/credit-manager/lib/types.ts`

**Step 1: Write types file**
```typescript
export interface Card {
  id: string;
  user_id: string;
  card_name: string;
  issuer: string;
  last_four: string;
  credit_limit: number;
  apr: number;
  annual_fee: number;
  statement_day: number;
  due_day: number;
  autopay_enabled: boolean;
  autopay_amount: 'minimum' | 'statement_balance' | 'full_balance';
  is_primary: boolean;
  opened_at?: string;
  closed_at?: string;
  created_at: string;
}

export interface Statement {
  id: string;
  card_id: string;
  statement_date: string;
  statement_pdf_url?: string;
  statement_balance: number;
  minimum_payment: number;
  payment_due_date: string;
  transactions_count?: number;
  ocr_raw_text?: string;
  extracted_at?: string;
}

export interface Transaction {
  id: string;
  statement_id: string;
  transaction_date: string;
  description: string;
  category?: string;
  amount: number;
  is_interest_charge: boolean;
  is_late_fee: boolean;
  is_annual_fee: boolean;
}

export interface Payment {
  id: string;
  card_id: string;
  statement_id?: string;
  amount: number;
  paid_at: string;
  scheduled_for?: string;
  is_autopay: boolean;
  status: 'scheduled' | 'completed' | 'missed' | 'cancelled';
  impact_on_utilization?: number;
}

export interface ScoreSnapshot {
  id: string;
  user_id: string;
  score: number;
  source: 'experian' | 'transunion' | 'equifax' | 'credit_karma';
  snapshot_date: string;
  factors?: Record<string, number>;
}

export interface AISuggestion {
  id: string;
  user_id: string;
  type: 'payment_strategy' | 'utilization_alert' | 'spending_insight' | 'score_improvement' | 'card_closure_warning';
  priority: 'low' | 'medium' | 'high' | 'critical';
  title: string;
  description: string;
  recommended_action?: string;
  projected_impact?: string;
  is_read: boolean;
  is_actioned: boolean;
}

// Derived metrics
export interface CardMetrics {
  utilization_rate: number;      // balance / limit
  interest_per_month: number;    // estimated
  available_credit: number;      // limit - balance
  days_until_due: number;
  status: 'healthy' | 'warning' | 'critical'; // based on utilization
}
```

**Step 2: Commit**
```bash
git add apps/credit-manager/lib/types.ts
git commit -m "feat(credit): add TypeScript types for credit_manager schema"
```

---

#### Task 3: Create Supabase client helpers
**Objective:** Set up typed Supabase client for credit_manager schema.

**Files:**
- Create: `apps/credit-manager/lib/supabase.ts`

```typescript
import { createClient } from '@supabase/supabase-js';
import { Database } from './database.types'; // generated from schema

export const supabase = createClient<Database>(
  process.env.NEXT_PUBLIC_SUPABASE_URL!,
  process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY!
);
```

**Step 2: Commit**
```bash
git add apps/credit-manager/lib/supabase.ts
git commit -m "feat(credit): add typed Supabase client"
```

---

### Phase 2: Core UI — Cards & Dashboard

#### Task 4: Create dashboard page layout
**Objective:** Main dashboard showing all cards with utilization meters and upcoming payments.

**Files:**
- Create: `apps/credit-manager/app/dashboard/page.tsx`
- Create: `apps/credit-manager/app/dashboard/layout.tsx`

**Key UI elements:**
- Cards grid with:
  - Card name, last four digits
  - Circular progress: utilization % (red if >30%, yellow 10-30%, green <10%)
  - Current balance / credit limit
  - APR
  - Days until due date
  - Quick "Pay" button
- Summary cards at top:
  - Total credit limit across all cards
  - Total balance
  - Aggregate utilization %
  - Next payment due (closest date)
  - Credit score (last entered)
- Suggestions feed sidebar

**Step 1: Build page with mock data**
```tsx
// Mock 3 cards for dev
const mockCards: Card[] = [
  { id: '1', card_name: 'Chase Freedom', last_four: '4242', credit_limit: 10000, apr: 24.99, statement_balance: 3500, minimum_payment: 105, due_date: '2026-05-10', ... },
  ...
];
```

**Step 2: Verify layout renders**
Run: `npm run dev`, visit `http://localhost:3000/dashboard`

**Step 3: Commit**
```bash
git add apps/credit-manager/app/dashboard/
git commit -m "feat(credit): add dashboard with cards grid and utilization meters"
```

---

#### Task 5: Add Card form
**Objective:** Form to add a new credit card with all fields.

**Files:**
- Create: `apps/credit-manager/components/AddCardForm.tsx`
- Create: `apps/credit-manager/app/dashboard/add-card/page.tsx`

**Fields:**
- Card name (text)
- Issuer (dropdown: Chase, Amex, Citi, Capital One, Discover, Other)
- Last four digits (4 chars, validated)
- Credit limit (number, $)
- APR (number, %)
- Annual fee (number, $, default 0)
- Statement day (1-31)
- Due day (1-31)
- Autopay enabled (toggle)
- Autopay amount (radio: minimum / statement balance / full balance)
- Is primary card? (toggle — warn if they already have one marked primary)
- Opened date (date picker)

**Step 1: Build form with validation**
```tsx
const schema = z.object({
  card_name: z.string().min(1),
  issuer: z.string().min(1),
  last_four: z.string().length(4).regex(/^\d{4}$/),
  credit_limit: z.number().positive(),
  apr: z.number().min(0).max(100),
  annual_fee: z.number().min(0).default(0),
  statement_day: z.number().min(1).max(31),
  due_day: z.number().min(1).max(31),
  autopay_enabled: z.boolean().default(false),
  autopay_amount: z.enum(['minimum', 'statement_balance', 'full_balance']).default('minimum'),
  is_primary: z.boolean().default(false),
  opened_at: z.string().optional(),
});
```

**Step 2: Connect to Supabase insert**
```typescript
const { data, error } = await supabase.from('cards').insert(values).select().single();
```

**Step 3: Commit**
```bash
git add apps/credit-manager/components/AddCardForm.tsx apps/credit-manager/app/dashboard/add-card/
git commit -m "feat(credit): add card creation form with validation"
```

---

### Phase 3: Statement Upload & OCR

#### Task 6: Build PDF upload component
**Objective:** Drag-and-drop PDF upload for credit card statements.

**Files:**
- Create: `apps/credit-manager/components/StatementUpload.tsx`
- Create: `apps/credit-manager/app/api/upload-statement/route.ts`

**Flow:**
1. User selects card from dropdown
2. User drops/selects PDF
3. Upload to Supabase Storage: `statements/{user_id}/{card_id}/{filename}`
4. Return public URL
5. Trigger OCR extraction (next task)

**Step 1: Upload component**
```tsx
// Uses react-dropzone or native input
drag-and-drop zone with:
- "Drop statement PDF here"
- Select card dropdown
- Progress bar
- Preview of extracted data (after OCR)
```

**Step 2: API route**
```typescript
export async function POST(req: Request) {
  const formData = await req.formData();
  const file = formData.get('file') as File;
  const cardId = formData.get('card_id') as string;
  
  // Upload to Supabase Storage
  const { data, error } = await supabase.storage
    .from('statements')
    .upload(`${userId}/${cardId}/${uuidv4()}.pdf`, file);
  
  // Return path, trigger OCR queue job
  return Response.json({ path: data.path });
}
```

**Step 3: Commit**
```bash
git add apps/credit-manager/components/StatementUpload.tsx apps/credit-manager/app/api/upload-statement/
git commit -m "feat(credit): add PDF statement upload with Supabase Storage"
```

---

#### Task 7: OCR extraction service
**Objective:** Extract text from PDF statements using Tesseract/OCR or existing PDF pipeline.

**Files:**
- Create: `apps/credit-manager/lib/ocr.ts`
- Create: `apps/credit-manager/app/api/extract-statement/route.ts`

**Options:**
- **Option A:** Reuse existing PDF-TTS app OCR pipeline (Tesseract + pdf2image)
- **Option B:** Use a commercial API (Document AI, AWS Textract) — more accurate for tables

**Recommendation:** Start with Option A (Tesseract), upgrade if accuracy is poor.

**Step 1: OCR function**
```typescript
import { createWorker } from 'tesseract.js';
import pdf from 'pdf-parse';

export async function extractStatementText(pdfBuffer: Buffer): Promise<{
  rawText: string;
  statementBalance?: number;
  minimumPayment?: number;
  dueDate?: string;
  transactions: Array<{
    date: string;
    description: string;
    amount: number;
  }>;
}> {
  // Try pdf-parse first (text-based PDFs)
  const pdfData = await pdf(pdfBuffer);
  let text = pdfData.text;
  
  // If text is sparse, use OCR
  if (text.length < 500) {
    // Convert PDF pages to images, OCR each
    const worker = await createWorker('eng');
    // ... extract images from PDF, run OCR
    text = await extractWithOCR(pdfBuffer, worker);
    await worker.terminate();
  }
  
  // Parse extracted text with regex/AI
  return parseStatementText(text);
}
```

**Step 2: AI-powered parsing**
Instead of fragile regex, send OCR text to Claude with a structured prompt:

```typescript
const prompt = `Extract the following from this credit card statement text:
- Statement date
- Statement balance (total)
- Minimum payment due
- Payment due date
- List of transactions: date, description, amount

Return ONLY valid JSON in this format:
{
  "statement_date": "YYYY-MM-DD",
  "statement_balance": 1234.56,
  "minimum_payment": 50.00,
  "due_date": "YYYY-MM-DD",
  "transactions": [
    {"date": "YYYY-MM-DD", "description": "...", "amount": -45.67}
  ]
}

Statement text:
${ocrText}`;

const result = await anthropic.messages.create({
  model: 'claude-sonnet-4-20250514',
  max_tokens: 4000,
  messages: [{ role: 'user', content: prompt }],
});

const parsed = JSON.parse(result.content[0].text);
```

**Step 3: Store extracted data**
```typescript
// Insert statement
const { data: statement } = await supabase.from('statements').insert({
  card_id: cardId,
  statement_date: parsed.statement_date,
  statement_balance: parsed.statement_balance,
  minimum_payment: parsed.minimum_payment,
  payment_due_date: parsed.due_date,
  statement_pdf_url: storagePath,
  ocr_raw_text: ocrText,
}).select().single();

// Insert transactions
const transactions = parsed.transactions.map(t => ({
  statement_id: statement.id,
  ...t,
}));
await supabase.from('transactions').insert(transactions);
```

**Step 4: Commit**
```bash
git add apps/credit-manager/lib/ocr.ts apps/credit-manager/app/api/extract-statement/
git commit -m "feat(credit): add OCR + AI extraction for PDF statements"
```

---

### Phase 4: AI Payment Strategy Engine

#### Task 8: Build credit utilization calculator
**Objective:** Calculate utilization per card and aggregate, with status indicators.

**Files:**
- Create: `apps/credit-manager/lib/calculations.ts`

```typescript
export function calculateUtilization(balance: number, limit: number): number {
  return Math.round((balance / limit) * 100);
}

export function getUtilizationStatus(rate: number): 'healthy' | 'warning' | 'critical' {
  if (rate < 10) return 'healthy';
  if (rate < 30) return 'warning';
  return 'critical';
}

export function calculateAggregateUtilization(cards: Array<{ balance: number; limit: number }>): number {
  const totalBalance = cards.reduce((sum, c) => sum + c.balance, 0);
  const totalLimit = cards.reduce((sum, c) => sum + c.limit, 0);
  return Math.round((totalBalance / totalLimit) * 100);
}

export function estimateInterest(balance: number, apr: number): number {
  return Math.round((balance * (apr / 100)) / 12 * 100) / 100; // monthly interest
}

export function daysUntilDue(dueDate: string): number {
  const today = new Date();
  const due = new Date(dueDate);
  const diff = due.getTime() - today.getTime();
  return Math.ceil(diff / (1000 * 60 * 60 * 24));
}
```

**Step 2: Commit**
```bash
git add apps/credit-manager/lib/calculations.ts
git commit -m "feat(credit): add utilization and interest calculations"
```

---

#### Task 9: Build AI suggestion engine
**Objective:** Generate personalized payment and credit score suggestions using Claude API.

**Files:**
- Create: `apps/credit-manager/lib/ai-suggestions.ts`
- Create: `apps/credit-manager/app/api/generate-suggestions/route.ts`

**Prompt design:**
```typescript
function buildSuggestionPrompt(cards: Card[], payments: Payment[], scoreSnapshots: ScoreSnapshot[]): string {
  const cardDetails = cards.map(c => ({
    name: c.card_name,
    balance: c.statement_balance,
    limit: c.credit_limit,
    utilization: calculateUtilization(c.statement_balance, c.credit_limit),
    apr: c.apr,
    minimum_due: c.minimum_payment,
    days_until_due: daysUntilDue(c.due_date),
    is_primary: c.is_primary,
  }));

  return `You are a credit card optimization expert. Given the user's current credit cards and payment history, generate 3-5 specific, actionable suggestions to improve their credit score and minimize interest payments.

FICO scoring weights:
- Payment History: 35% (never miss payments)
- Credit Utilization: 30% (keep under 30%, ideally under 10%)
- Length of History: 15% (don't close old cards)
- Credit Mix: 10%
- New Credit: 10%

Current cards:
${JSON.stringify(cardDetails, null, 2)}

Generate suggestions as JSON array:
[
  {
    "type": "payment_strategy" | "utilization_alert" | "spending_insight" | "score_improvement" | "card_closure_warning",
    "priority": "low" | "medium" | "high" | "critical",
    "title": "Short title",
    "description": "Detailed explanation with numbers",
    "recommended_action": "What to do specifically",
    "projected_impact": "e.g., '+20 points in 30 days' or 'Save $45/month interest'"
  }
]`;
}
```

**Step 1: API route**
```typescript
export async function POST(req: Request) {
  const { userId } = await auth();
  
  // Fetch user's cards
  const { data: cards } = await supabase.from('cards').select('*').eq('user_id', userId);
  const { data: payments } = await supabase.from('payments').select('*').in('card_id', cards.map(c => c.id));
  
  const prompt = buildSuggestionPrompt(cards, payments, []);
  
  const aiResponse = await anthropic.messages.create({
    model: 'claude-sonnet-4-20250514',
    max_tokens: 4000,
    messages: [{ role: 'user', content: prompt }],
  });
  
  const suggestions = JSON.parse(aiResponse.content[0].text);
  
  // Store in database
  const { data } = await supabase.from('ai_suggestions').insert(
    suggestions.map(s => ({ ...s, user_id: userId }))
  );
  
  return Response.json({ suggestions: data });
}
```

**Step 2: Commit**
```bash
git add apps/credit-manager/lib/ai-suggestions.ts apps/credit-manager/app/api/generate-suggestions/
git commit -m "feat(credit): add AI suggestion engine with Claude API"
```

---

#### Task 10: Payment scheduler UI
**Objective:** Allow users to schedule payments with AI-recommended amounts.

**Files:**
- Create: `apps/credit-manager/components/PaymentScheduler.tsx`

**UI flow:**
1. Card selector (dropdown)
2. Statement balance display
3. Minimum payment display
4. AI-recommended amount (with explanation tooltip)
5. Custom amount input (default = AI recommendation)
6. Payment date picker (default = 3 days before due date)
7. "Schedule Payment" button
8. Payment history table below

**AI recommendation logic (server-side):**
```typescript
function getRecommendedPayment(card: Card, allCards: Card[]): number {
  const utilization = calculateUtilization(card.statement_balance, card.credit_limit);
  const aggregateUtil = calculateAggregateUtilization(allCards);
  
  // Rule 1: If any card > 30%, pay down highest utilization first
  if (utilization > 30) {
    // Pay enough to get under 30%
    const targetBalance = card.credit_limit * 0.25; // aim for 25%
    return Math.max(card.statement_balance - targetBalance, card.minimum_payment);
  }
  
  // Rule 2: If aggregate > 30%, contribute to this card proportionally
  if (aggregateUtil > 30) {
    return Math.max(card.minimum_payment * 2, card.statement_balance * 0.1);
  }
  
  // Rule 3: If high APR (>20%), pay more than minimum
  if (card.apr > 20) {
    return Math.max(card.statement_balance * 0.2, card.minimum_payment * 3);
  }
  
  // Rule 4: Default = statement balance (avoid interest entirely)
  return card.statement_balance;
}
```

**Step 1: Build component**
```tsx
export function PaymentScheduler({ cards }: { cards: Card[] }) {
  const [selectedCard, setSelectedCard] = useState(cards[0]);
  const recommendation = getRecommendedPayment(selectedCard, cards);
  
  return (
    <div className="payment-scheduler">
      <CardSelector cards={cards} onSelect={setSelectedCard} />
      <BalanceDisplay card={selectedCard} />
      <AIRecommendation amount={recommendation} reason={...} />
      <AmountInput defaultValue={recommendation} />
      <DatePicker defaultValue={getDateBeforeDue(selectedCard.due_date, 3)} />
      <Button onClick={schedulePayment}>Schedule Payment</Button>
    </div>
  );
}
```

**Step 2: Commit**
```bash
git add apps/credit-manager/components/PaymentScheduler.tsx
git commit -m "feat(credit): add payment scheduler with AI recommendations"
```

---

### Phase 5: Google Calendar Integration

#### Task 11: Connect Google Calendar for payment reminders
**Objective:** Sync payment due dates to Google Calendar with reminders.

**Files:**
- Create: `apps/credit-manager/lib/google-calendar.ts`
- Create: `apps/credit-manager/app/api/calendar/sync/route.ts`

**Setup:**
1. Google Cloud Console → enable Calendar API
2. OAuth 2.0 credentials
3. Store tokens in Supabase `user_integrations` table

**Sync function:**
```typescript
export async function syncPaymentToCalendar(payment: Payment, card: Card, accessToken: string) {
  const event = {
    summary: `💳 Pay ${card.card_name} ••• ${card.last_four}`,
    description: `Statement balance: $${payment.amount}\nMinimum: $${card.minimum_payment}\nRecommended: $${payment.recommended_amount}`,
    start: {
      date: payment.scheduled_for,
    },
    end: {
      date: payment.scheduled_for,
    },
    reminders: {
      useDefault: false,
      overrides: [
        { method: 'email', minutes: 24 * 60 }, // 1 day before
        { method: 'popup', minutes: 60 },      // 1 hour before
      ],
    },
  };
  
  const res = await fetch('https://www.googleapis.com/calendar/v3/calendars/primary/events', {
    method: 'POST',
    headers: {
      Authorization: `Bearer ${accessToken}`,
      'Content-Type': 'application/json',
    },
    body: JSON.stringify(event),
  });
  
  return await res.json();
}
```

**Step 1: Build calendar integration**
```bash
git add apps/credit-manager/lib/google-calendar.ts apps/credit-manager/app/api/calendar/
git commit -m "feat(credit): add Google Calendar payment reminder sync"
```

---

### Phase 6: Spending Insights

#### Task 12: Transaction categorization and spending analysis
**Objective:** Auto-categorize transactions and show spending breakdown.

**Files:**
- Create: `apps/credit-manager/lib/categorize.ts`
- Create: `apps/credit-manager/app/api/categorize/route.ts`

**Categories:**
- groceries, dining, gas, travel, entertainment, shopping, healthcare, utilities, insurance, interest, fees, other

**AI categorization prompt:**
```typescript
const prompt = `Categorize these credit card transactions into one of: groceries, dining, gas, travel, entertainment, shopping, healthcare, utilities, insurance, interest, fees, other.

Transactions:
${transactions.map(t => `- ${t.description}: $${t.amount}`).join('\n')}

Return JSON array: [{ "transaction_id": "...", "category": "...", "confidence": 0.95 }]`;
```

**Step 1: Build categorization**
```bash
git add apps/credit-manager/lib/categorize.ts
git commit -m "feat(credit): add AI transaction categorization"
```

---

#### Task 13: Spending insights dashboard
**Objective:** Charts showing spending by category, month-over-month trends, top merchants.

**Files:**
- Create: `apps/credit-manager/components/SpendingInsights.tsx`
- Create: `apps/credit-manager/app/dashboard/spending/page.tsx`

**Charts:**
- Pie chart: spending by category (this month)
- Bar chart: month-over-month spending trend
- Top 10 merchants by spend
- Interest paid over time (highlight savings potential)
- "You spent $X on interest this year — paying statement balances would save $Y"

**Step 1: Build insights page**
```bash
git add apps/credit-manager/components/SpendingInsights.tsx apps/credit-manager/app/dashboard/spending/
git commit -m "feat(credit): add spending insights dashboard with charts"
```

---

### Phase 7: Polish & Launch

#### Task 14: Add credit score tracker
**Objective:** Simple form to log credit scores, AI analyzes trends.

**Files:**
- Create: `apps/credit-manager/components/ScoreTracker.tsx`

**Features:**
- Enter score from any bureau
- Track over time with line chart
- AI insight: "Your score dropped 15 points — likely due to utilization spike on Chase Freedom"

**Step 1: Build score tracker**
```bash
git add apps/credit-manager/components/ScoreTracker.tsx
git commit -m "feat(credit): add credit score tracker with trend analysis"
```

---

#### Task 15: Landing page + auth
**Objective:** Public landing page with Clerk auth integration.

**Files:**
- Create: `apps/credit-manager/app/page.tsx` (landing)
- Modify: `apps/credit-manager/middleware.ts` (auth routes)

**Landing page sections:**
1. Hero: "AI-Powered Credit Card Management"
2. Problem: missed payments, high utilization, interest waste
3. Solution: upload statements, AI optimizes payments, calendar reminders
4. Features grid: Smart Payments, Utilization Alerts, Interest Savings, Score Tracking
5. CTA: "Get Started Free"

**Step 1: Build landing**
```bash
git add apps/credit-manager/app/page.tsx
git commit -m "feat(credit): add landing page with Clerk auth"
```

---

#### Task 16: End-to-end test
**Objective:** Walk through full user flow — add card, upload statement, get suggestions, schedule payment.

**Test script:**
```bash
# 1. Sign up
# 2. Add Chase Freedom card ($10,000 limit, 24.99% APR)
# 3. Upload statement PDF
# 4. Verify extracted balance, due date, transactions
# 5. Check AI suggestions appear
# 6. Schedule payment with AI recommendation
# 7. Verify Google Calendar event created
# 8. Check dashboard utilization meter updated
```

**Step 1: Run manual test, fix issues**

**Step 2: Commit fixes**
```bash
git commit -m "fix(credit): e2e test fixes"
```

---

## Summary

| Phase | Tasks | Est. Time |
|-------|-------|-----------|
| 1: Foundation | 1-3 | 2h |
| 2: Core UI | 4-5 | 3h |
| 3: Upload & OCR | 6-7 | 4h |
| 4: AI Engine | 8-10 | 4h |
| 5: Calendar | 11 | 1.5h |
| 6: Insights | 12-13 | 3h |
| 7: Polish | 14-16 | 3h |
| **Total** | **16 tasks** | **~20.5h** |

---

## Revenue Model Suggestion

**Freemium:**
- Free: 2 cards, manual entry, basic dashboard
- Pro ($9/mo): Unlimited cards, PDF upload + OCR, AI suggestions, calendar sync, spending insights
- Family ($15/mo): Up to 4 users, shared dashboard

**Why this works:**
- High pain point (credit score anxiety is real)
- Low price point = easy impulse buy
- AI suggestions feel like having a financial advisor
- Recurring value (new statements every month)

---

*Plan written by Hermes — 2026-04-22*
