# Claude Master Context — AI Automation MSP
_Read this at the start of every session to restore full context._
_Last updated: 2026-05-03_

---

## How to Use This File

This is the single source of truth for any Claude session — business, technical, or strategic. Load it at session start. Update it when new decisions are made, clients are added, or knowledge progresses.

---

## 1. Working With Me

**Who I am:** Jakub. Solo founder, technically advanced. Comfortable with git CLI, APIs, raw JSON, curl, Python, n8n internals. No need to explain tooling basics.

**Rules for Claude:**
- Be direct and concise — no padding, no unsolicited refactoring or advice
- Never commit credentials to git (`.claude/settings.json`, `.claude/settings.local.json` are always gitignored)
- Always develop on a designated branch; never push to `main` directly
- Update this file when new context is established in a session
- Pre-approved bash/MCP commands live in `.claude/settings.local.json` — do not re-ask for permission on those

**Rules for business/financial coaching sessions:**
- After introducing any business or financial concept, always end with a follow-up question tied to *my specific numbers* — not a generic "did you understand?" Example: after gross margin → *"If your retainer is €150 and cost is €35, what's your gross margin?"*
- Track topic mastery using the Learning Tracker below — 3 correct applications = mark as learned
- Proactively reference relevant unlearned topics when they apply to what I'm asking
- Do not repeat explanations of already-learned topics — reference them briefly and move on

---

## 2. Business Overview

**What the business is:** An n8n-based AI Automation MSP (Managed Service Provider). I deploy and fully manage AI bots for small businesses — handling their emails, appointment booking, and customer replies via WhatsApp or a custom frontend. The client pays a fixed monthly fee and never touches the infrastructure.

**Business model:**
| Component | Amount |
|---|---|
| Setup fee (one-time) | 8,000–10,000 CZK |
| **AI Front Desk** (booking + reminders + FAQ bot) | 4,500–5,000 CZK/month |
| **Email Bot** (AI email replies) | 2,500–3,000 CZK/month |
| **PDF Extractor** (invoices / intake forms / price lists → Excel) | 1,500–2,000 CZK/month |
| **Full bundle** (all three services) | ~7,500 CZK/month |
| Fair-use cap (included) | 1,500 automated emails + 750 AI-booked appointments/month |
| Usage overage | Cost + 30% |
| Gross margin | ~80–85% |
| Monthly infra cost per client | ~1,100–1,700 CZK (shared instance model) |

**Product notes:**
- AI Front Desk bundles booking + appointment reminders + FAQ bot — all run in the same n8n workflow, no marginal cost to include them
- PDF Extractor fits primary ICP only for intake forms (vets/physios with scanned paper forms) and supplier price lists — invoice volume too low for salons/vets to justify it
- PDF Extractor is a stronger fit for secondary ICP: small firms (5–10 people) and freelancers with high invoice volume

**Infrastructure decision (confirmed):** Shared n8n instance. Each client gets isolated workflows, credentials, and webhook paths within one Railway-hosted instance. Offer dedicated instance as a paid upgrade (+€30/month) only when a client specifically requests it.

**Unit economics:**
| Metric | Value |
|---|---|
| Monthly cost per client | ~1,100–1,700 CZK |
| Monthly revenue per client (front desk only) | ~4,500–5,000 CZK |
| Monthly revenue per client (full bundle) | ~7,500 CZK |
| LTV (2-year client, front desk only) | ~108,000–120,000 CZK + setup |
| CAC (currently) | ~0 CZK (personal network) |

**Personal financial situation:** Student. Father covers 12,000 CZK/month (food). Real monthly burn = ~1,000 CZK (Claude 500 + Railway 500). Food is fully offset.

**Break-even:** Operational break-even at **1 client**. First 10 clients = substantial recurring profit on top.

**Funding:** ~50,000 CZK available from friends as investment. This is **pure growth capital** (not survival capital) — runway at zero clients is ~50 months. Can be deployed on ads, content, or tooling to accelerate acquisition. No pressure to discount to close first client.

---

## 3. Target Clients (ICP)

**Primary target:** Appointment-based local businesses in Prague (and Czech Republic broadly)
- Veterinary clinics
- Dentists and medical practices
- Hair/beauty salons
- Physiotherapists and wellness studios

**Secondary target:** Freelancers and small firms (2–10 people) with high admin burden

**Shared ICP characteristic:** Owner wears many hats, limited time, not technical, misses bookings due to missed calls or slow email replies.

**ICP not yet finalised** — keeping broad for now. Revisit when first 2–3 clients are onboarded to see which vertical converts best.

**Acquisition channels:**
| Client type | Channel |
|---|---|
| Local businesses | Instagram + WhatsApp demo |
| Freelancers | LinkedIn + cold email |
| Small firms | LinkedIn + cold email + referral |

**Key rule on demos:** Never pretend the bot is human and reveal it later. Always lead with *"this is an AI assistant."* The demo sells itself — deception kills trust and violates EU compliance.

---

## 4. Brand & Positioning

**Personality words:** Practical · Transparent · Outcome-first · Personal · No-jargon

**Business name: ALSflow (decided ✓)**
- Domain: **alsflow.cz** — purchased via Wedos.cz ✓ (2026-04-16)
- Email: **info@alsflow.cz** set up via seznam.cz ✓ (2026-04-16)

**Positioning statement:**
> For Czech appointment-based small businesses who lose bookings because they can't pick up the phone while working, ALSflow is a managed AI service that handles their emails and calendar 24/7 — fully set up and run for them. Unlike hiring a receptionist, we cost 70% less and never call in sick.

**Key differentiator:** Hyper-specialisation in appointment booking for Czech local service businesses. šéfbot.cz serves e-shops and sales funnels — we don't. That's the moat.

**Current landing page headline:**
```
VÁŠ E-MAIL.
VÁŠ KALENDÁŘ.
VÁŠ AI.
```

**Hero sub (updated 2026-04-22):**
> *"Váš telefon zvoní, vy jste u zákazníka. AI odpoví, termín zarezervuje, připomínku pošle. Vy nastavení neřešíte — my se postaráme o vše."*

**Positioning vs. competitors:**
- Cheap tools (talabot, odpovidej): self-serve, no support — we win on managed + personal service
- Expensive managed services (šéfbot.cz, bezvabot.cz 20,000 CZK/month): priced out of small business — we win on price and focus
- Hiring a receptionist (15,000–25,000 CZK/month): we win on cost and 24/7 availability
- Reservio/Bookio: passive booking pages — client must find it and book themselves. We handle the conversation.

**Objection handlers:**
- Reservio objection: "Reservio is passive — client must find it and book. We handle the back-and-forth while you're busy."
- šéfbot.cz objection: "They serve e-shops and recruiters. We only work with appointment-based service businesses — the product fits your exact problem."

---

## 5. Competitive Landscape (Czech Market)

| Competitor | Threat | Why |
|---|---|---|
| šéfbot.cz | **HIGH** | Same MSP model, 400+ clients, Prague, managed service |
| bezvabot.cz | Medium | Does appointment booking but 20,000 CZK/month — unaffordable for small biz |
| chatbuilders.cz | Medium | Broad automation, unclear pricing, no ICP |
| apertia.ai | Low | Medium/large companies, ERP/CRM focus |
| talabot.cz | Low | E-commerce only, self-serve, 399 CZK/month |
| Reservio / Bookio | Indirect | Booking SaaS — no AI, client must book themselves |
| Hiring a receptionist | Indirect | 15,000–25,000 CZK/month — we are cheaper and 24/7 |

**Full detailed profiles:** see `competition/competitors.md`

### Market Pricing Intelligence

| Price point | Who it serves |
|---|---|
| Free – 399 CZK/month | Self-serve DIY tools |
| 2,000–5,000 CZK/month | **Our target zone** — affordable managed service |
| 20,000 CZK/month | bezvabot — medium businesses |
| 65,000–100,000+ CZK setup | Enterprise custom builds |

---

## 6. Active Projects

| Project | Location | Status |
|---|---|---|
| AI Automation MSP — business build | This file / `final_plan.md` | Active — building first 10 clients |
| Landing page (HTML) | GitHub: `modelsals482-ops/app_deployment` → `index.html` | **Live at alsflow.cz** — deployed via Vercel (2026-04-20). GA4 + Consent Mode v2 + cookie banner. Copy improved 2026-04-22. Contact form wired to n8n webhook. |
| Privacy policy page | GitHub: `modelsals482-ops/app_deployment` → `ochrana_dat.html` | **Live** — add IČO when registered. |
| Cold email sequence | Local: `C:\Users\Jakub\Desktop\Pracovni dokumenty\AI_Suite_Emaily.docx` | **Complete** — 5 templates ready to personalise. |
| Faktura template | Local: `C:\Users\Jakub\Desktop\Pracovni dokumenty\faktura_sablona.html` | **Complete** — open in browser, print to PDF. Fill IČO + IBAN after registration. |
| PDF → Excel n8n workflow | `modelsals482-ops/Test-claude` repo | Built and deployed |
| Czech competitor analysis | `competition/competitors.md` | Complete |
| Business/financial learning | Learning Tracker section below | Ongoing |
| Budget / pricing spreadsheet | `Basic rozpocet.xlsx` in Firm_advisor dir | Complete |
| Error-alerting workflow | n8n / Railway | **Complete** (2026-05-03) |

**Deployment stack:**
- **GitHub repo:** `modelsals482-ops/app_deployment` (main branch)
- **Hosting:** Vercel (free tier) — auto-deploys on every push to main
- **Domain:** alsflow.cz via Wedos DNS — A record `76.76.21.21` + CNAME `www` → `16012d20c360ac1a.vercel-dns-017.com`
- **Local path:** `C:\Users\Jakub\Desktop\html.websites\COMPLETE_PRODUCT\finalized_products\`
- **Git note:** local branch is `master`, remote is `main` — push with `git push origin HEAD:main --force`

---

## 7. Tools & Infrastructure

| Tool | Role |
|---|---|
| **n8n** | Automation delivery platform — self-hosted on Railway |
| **Railway** | Hosting for n8n + Postgres (~€20/month, shared across clients) |
| **Gemini / Google APIs** | AI layer powering client bots |
| **Vercel** | Static site hosting for alsflow.cz (free tier, auto-deploy from GitHub) |
| **Google Analytics** | GA4 property G-CEX6XVFWD7 — Consent Mode v2 active, cookie banner live |
| **Obsidian** | Knowledge base, session memory, business notes |
| **GitHub** | Version control, project docs |
| **Claude Code** | Primary AI coding + business assistant (CLI) |

**n8n MCP notes (critical):**
- `create_workflow_from_code` is broken — always creates empty workflows. Write JSON directly into the workflow file and have the user import manually.
- `get_sdk_reference` tool is missing — skip step 1 of MCP instructions
- DO NOT use `xlsx` or `pdf-parse` npm packages in n8n nodes — use built-in `extractFromFile` (PDF) and `convertToFile` (xlsx) nodes instead
- Code nodes: pure JS only, no `require()` unless explicitly confirmed available

---

## 8. Open Questions to Resolve

- [x] Purchase alsflow.cz — DONE (2026-04-16)
- [x] Set up info@alsflow.cz — DONE (2026-04-16)
- [x] Build landing page with contact form and privacy policy — DONE (2026-04-16)
- [x] Security-harden landing page — DONE (2026-04-16)
- [x] Cold email sequence — DONE (2026-04-16)
- [x] Set up Instagram account — DONE (2026-04-20)
- [x] Set up LinkedIn page — DONE (2026-04-20)
- [x] Deploy alsflow.cz — DONE (2026-04-20)
- [x] Add llms.txt — DONE (2026-04-20)
- [x] Add Google Analytics + Consent Mode v2 + cookie banner — DONE (2026-04-20)
- [x] Finalise landing page body copy — DONE (2026-04-22)
- [x] Build faktura template — DONE (2026-04-22)
- [x] Wire contact form to real endpoint (n8n webhook) — DONE (2026-05-03)
- [x] Build error-alerting workflow for client monitoring — DONE (2026-05-03)
- [ ] Add IČO to ochrana_dat.html + faktura_sablona.html once registered
- [ ] Register as OSVČ — živnostenský list (1,000 CZK, one trip to živnostenský úřad)
- [ ] Open Fio bank account for business income
- [ ] Notify ČSSZ + health insurer within 8 days of first invoice
- [ ] Add to client contract: setup fee paid before work begins + monthly auto-payment on the 1st
- [ ] Personalise and send cold emails to first 5 warm contacts
- [ ] Set up LinkedIn content calendar (1–2 posts/week)
- [ ] Close first paying client

---

## 9. Business & Financial Learning Tracker

### Understanding Your Own Firm
- [x] Value Proposition Canvas — what you offer vs. customer pains/gains [LEARNED — 2026-04-22]
- [ ] Business Model Canvas — full picture of how your firm operates (0/3)
- [x] Unit Economics — CAC vs. LTV [LEARNED — 2026-04-20]
- [x] Profit margins — gross margin vs. net margin [LEARNED — 2026-04-22]
- [x] Cash flow vs. profit — why a profitable firm can still go broke [LEARNED — 2026-04-22]

### Client Selection
- [~] ICP (Ideal Customer Profile) — defining who your best client looks like (0/3) — revisit after first clients
- [ ] TAM / SAM / SOM — sizing your total market vs. realistic target (0/3)
- [ ] RFM Analysis — ranking clients by Recency, Frequency, Monetary value (0/3)
- [x] Jobs to Be Done (JTBD) — what "job" does your client hire you to do? [LEARNED — 2026-04-22]
- [x] Lead qualification: BANT — Budget, Authority, Need, Timeline [LEARNED — 2026-04-22]

### Segmentation & Approach
- [ ] Market segmentation — by size, industry, maturity, behavior (0/3)
- [ ] Ansoff Matrix — grow via existing/new clients × existing/new products (0/3)
- [x] Positioning — how you are perceived vs. competitors [LEARNED — 2026-04-22]
- [ ] Sales motion differences — SMB vs. mid-market vs. enterprise (0/3)

### Competitive Analysis
- [ ] Porter's Five Forces — competitive pressure from all directions (0/3)
- [ ] Differentiation vs. cost leadership — which strategy you are pursuing (0/3)
- [ ] Competitor positioning map — plot rivals on price vs. value axes (0/3)
- [ ] Win/loss analysis — why you win deals, why you lose them (0/3)

### Financial Analysis
- [ ] Income statement basics — revenue, COGS, gross profit, EBITDA, net income (0/3)
- [ ] Balance sheet basics — assets, liabilities, equity (0/3)
- [ ] Key ratios — current ratio, debt/equity, ROE, ROA (0/3)
- [x] Break-even analysis [LEARNED — 2026-04-20]
- [ ] Pricing strategy — cost-plus vs. value-based vs. competitive pricing (0/3)

### Czech Business & Tax (practical)
- [x] OSVČ structure — vedlejší vs. hlavní, živnostenský list, IČO, DIČ [LEARNED — 2026-04-22]
- [x] Czech income tax — výdajový pausál (60%), slevy, 15% rate [LEARNED — 2026-04-22]
- [x] Paušální daň — 3 pásma, when it makes sense (not until ~1M+ CZK as vedlejší student) [LEARNED — 2026-04-22]
- [x] Cash flow management — payment terms, upfront setup fee, auto-payment contracts [LEARNED — 2026-04-22]
- [ ] VAT (DPH) — registration threshold, when to register, invoicing rules (0/3)
- [ ] Invoicing as OSVČ — required fields on faktura, numbering, record-keeping (0/3)

**Recommended books (priority order):**
1. *The Mom Test* — Rob Fitzpatrick
2. *Crossing the Chasm* — Geoffrey Moore
3. *Playing to Win* — Roger Martin
4. *Predictable Revenue* — Aaron Ross
5. *Good Strategy / Bad Strategy* — Richard Rumelt

---

## 10. Client Profiles

*Duplicate this block for each client when onboarded.*

```
## Client: [Name / Business]

- **Business type:** (vet / dentist / salon / physio / freelancer / other)
- **Location:** (Prague district or city)
- **Services:** (Front Desk / Email Bot / PDF Extractor / Bundle)
- **Monthly retainer:** CZK
- **Setup fee paid:** Yes / No / Partial
- **Integration type:** WhatsApp / Custom frontend / Other
- **Railway instance:** Shared / Dedicated
- **Monthly infra cost:** ~CZK
- **Gross margin on this client:** %
- **Active since:**
- **Fair-use status:** Under / Over threshold
- **Acquisition channel:** (Instagram / LinkedIn / Referral / Cold email)
- **Notes / quirks:**
- **Status:** [ ] Active  [ ] On hold  [ ] Delivered
```

---

## 11. Git & Repo Conventions

- **Business context repo:** `modelsals482-ops/financial_advisor`
- **Website repo:** `modelsals482-ops/app_deployment` (deploys to Vercel → alsflow.cz)
- **Never push to `main` directly**
- **Website git note:** local branch is `master`, remote is `main` — push with `git push origin HEAD:main --force`
- **Gitignored (credentials):** `.claude/settings.json`, `.claude/settings.local.json`
