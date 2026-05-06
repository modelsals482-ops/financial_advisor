# ALSflow Master Context — Shared Core
_Both agents load this file at every session start._
_Last updated: 2026-05-06_

> **Edit policy:** Neither agent edits this file freely. Only update when a real business decision is made — new pricing, new vertical confirmed, first client signed, brand pivot. When making a change, note it here and also update your own context file.

---

## Agent Setup

This project uses two Claude agents:

| Agent | Role | Loads |
|---|---|---|
| **Claude Code** (technical) | n8n builds, deployment, infrastructure | MASTER_CONTEXT.md + TECHNICAL_CONTEXT.md |
| **Claude Cowork** (sales/marketing) | Czech copy, pitch docs, ICP research, outreach | MASTER_CONTEXT.md + SALES_CONTEXT.md |

Cross-agent rule: when one agent makes a decision that affects the other's work, it writes a one-liner update to §4 (Active Projects) in this file.

---

## 1. Business Overview

**What the business is:** An n8n-based AI Automation MSP. Deploys and fully manages AI bots for Czech small businesses — handling emails, appointment booking, and customer replies. Client pays a fixed monthly fee and never touches the infrastructure.

**Business model:**
| Component | Amount |
|---|---|
| Setup fee (one-time) | 8,000–10,000 CZK |
| AI Front Desk (booking + reminders + FAQ bot) | 4,500–5,000 CZK/month |
| Email Bot (AI email replies) | 2,500–3,000 CZK/month |
| PDF Extractor (invoices / forms → Excel) | 1,500–2,000 CZK/month |
| Full bundle (all three) | ~7,500 CZK/month |
| Fair-use cap | 1,500 automated emails + 750 AI-booked appointments/month |
| Usage overage | Cost + 30% |
| Gross margin | ~80–85% |
| Monthly infra cost per client | ~1,100–1,700 CZK |

**Infrastructure:** Shared n8n instance on Railway. Each client gets isolated workflows, credentials, and webhook paths. Dedicated instance as paid upgrade (+€30/month).

**Unit economics:**
| Metric | Value |
|---|---|
| Monthly cost per client | ~1,100–1,700 CZK |
| Monthly revenue (front desk only) | ~4,500–5,000 CZK |
| Monthly revenue (full bundle) | ~7,500 CZK |
| LTV (2-year, front desk only) | ~108,000–120,000 CZK + setup |
| CAC (currently) | ~0 CZK (personal network) |
| Break-even | 1 client |

**Personal financial situation:** Student. Father covers 12,000 CZK/month. Real monthly burn ~1,000 CZK. Runway at zero clients ~50 months. ~50,000 CZK available as growth capital (not survival capital).

---

## 2. Target Clients (ICP)

**Primary:** Appointment-based local businesses in Prague — veterinary clinics, dentists, hair/beauty salons, physiotherapists, wellness studios.

**Secondary:** Freelancers and small firms (2–10 people) with high admin burden.

**Shared characteristic:** Owner wears many hats, limited time, not technical, misses bookings due to missed calls or slow email replies.

**Best-fit qualifier:** Time-poor AND AI-positive. Persona-specific UI matters (35-year-old physio vs 60-year-old dentist need different interfaces).

**STRATEGIC DECISION (2026-05-04):** ICP-first before any outreach. Pick one vertical, research it deeply, tailor the pitch, then reach out. Do not pitch a generic booking bot.

---

## 3. Brand

**Name:** ALSflow | **Domain:** alsflow.cz (live on Vercel) | **Email:** info@alsflow.cz

**Personality:** Practical · Transparent · Outcome-first · Personal · No-jargon

**Positioning statement:**
> For Czech appointment-based small businesses who lose bookings because they can't pick up the phone while working, ALSflow is a managed AI service that handles their emails and calendar 24/7 — fully set up and run for them. Unlike hiring a receptionist, we cost 70% less and never call in sick.

**Key differentiator:** Hyper-specialisation in appointment booking for Czech local service businesses. šéfbot.cz serves e-shops and sales funnels — we don't.

---

## 4. Active Projects (Status Overview)

| Project | Status |
|---|---|
| Landing page (alsflow.cz) | Live — GA4 + Consent Mode v2 + contact form wired to n8n |
| Privacy policy page | Live — add IČO when registered |
| Cold email sequence | Complete — 5 templates ready to personalise |
| Faktura template | Complete — fill IČO + IBAN after OSVČ registration |
| Error-alerting workflow | Complete (2026-05-03) |
| Client acquisition path playbook | Complete (2026-05-03) |
| Czech competitor analysis | Complete |
| Physio vertical deep-dive + Top 5 problems | Complete (2026-05-06) |
| Salon vertical deep-dive + Top 5 problems | Complete (2026-05-06) |
| Bot catalogue (Physio / Salon / Vet) | Complete (2026-05-06) |
| n8n bot implementation spec | Complete (2026-05-06) |
| Context file restructure (3-file system) | Complete (2026-05-06) |

---

## 5. Client Profiles

_Duplicate this block for each client when onboarded._

```
## Client: [Name / Business]

- Business type: (vet / dentist / salon / physio / freelancer / other)
- Location: (Prague district or city)
- Services: (Front Desk / Email Bot / PDF Extractor / Bundle)
- Monthly retainer: CZK
- Setup fee paid: Yes / No / Partial
- Integration type: WhatsApp / Custom frontend / Other
- Railway instance: Shared / Dedicated
- Monthly infra cost: ~CZK
- Gross margin: %
- Active since:
- Fair-use status: Under / Over
- Acquisition channel:
- Notes:
- Status: [ ] Active  [ ] On hold  [ ] Delivered
```
