# Claude Master Context — AI Automation MSP
_Read this at the start of every session to restore full context._
_Last updated: 2026-04-16_

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
- Email: **info@alsflow.cz** set up via seznam.cz ✓ (2026-04-16) — domain email propagation pending. Use info@alsflow.cz for all social media registrations once propagation completes (24–48h). Upgrade to Google Workspace (~€6/month) at first paying client.

**Current landing page headline:**
```
VÁŠ E-MAIL.
VÁŠ KALENDÁŘ.
VÁŠ AI.
```
*(Translation: YOUR EMAIL. YOUR CALENDAR. YOUR AI.)*

**Target value proposition framing (outcome-first):**
> *"Automate your emails and customer replies so you can focus on the work that actually pays."*

**Positioning vs. competitors:**
- Cheap tools (talabot, odpovidej): self-serve, no support — we win on managed + personal service
- Expensive managed services (šéfbot.cz, bezvabot.cz 20,000 CZK/month): priced out of small business — we win on price and focus
- Hiring a receptionist (15,000–25,000 CZK/month): we win on cost and 24/7 availability

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

**The gap:** Nobody in Prague serves small appointment-based businesses (vets, dentists, salons) with a managed, affordable, Czech-language AI assistant.

**Edge over šéfbot.cz (main threat):**
- They focus on lead gen and sales funnels, not service booking
- No visible hyper-focus on local service businesses
- No public pricing = self-qualification friction for small clients
- We can be more personal, local, and sharply focused

**To research further:**
- [ ] šéfbot.cz actual pricing — call or email for a quote
- [ ] Whether any competitor specifically targets vet/medical clinics
- [ ] Reservio / Bookio pricing as indirect baseline
- [ ] coworkers.ai — appeared in search, worth reviewing

**Full detailed profiles:** see `competition/competitors.md`

### Detailed Competitor Profiles

#### šéfbot.cz — HIGHEST THREAT
**Location:** Praha, Smíchov | **Clients:** 400+ | **Model:** Full managed service (same as us)
**Pricing:** Not public — "free solution proposal" entry point | **Tech:** DeepSeek
**Focus:** Lead gen, sales funnels, e-shops, recruitment — NOT local service booking
**Our edge:** No focus on vets/dentists/salons, no public pricing, we're more personal and hyper-focused

#### bezvabot.cz — MEDIUM THREAT
**Pricing:** ~20,000 CZK/month | **Does:** Appointment booking, Czech language
**Our edge:** 20,000 CZK/month is unaffordable for a solo vet — we can undercut massively and stay profitable

#### apertia.ai — LOW THREAT
**Target:** Medium/large companies, ERP/CRM, 100+ enterprise clients — completely different segment

#### talabot.cz — LOW THREAT
**Pricing:** From 399 CZK/month self-serve | **Target:** E-commerce only, not service businesses

#### BC4 / businesscom.cz — LOW THREAT
**Target:** Enterprise contact centers — irrelevant for small local businesses

### Market Pricing Intelligence

| Price point | Who it serves |
|---|---|
| Free – 399 CZK/month | Self-serve DIY tools |
| 2,000–5,000 CZK/month | **Our target zone** — affordable managed service |
| 20,000 CZK/month | bezvabot — medium businesses |
| 65,000–100,000+ CZK setup | Enterprise custom builds |

### The Real Competition (from a client's perspective)
1. **Doing nothing** — missing calls, losing bookings
2. **Hiring a part-time receptionist** — 15,000–25,000 CZK/month
3. **A basic booking SaaS** (Reservio, Bookio) — no AI, client must book themselves

We beat all three on price and convenience.

---

## 6. Active Projects

| Project | Location | Status |
|---|---|---|
| AI Automation MSP — business build | This file / `final_plan.md` | Active — building first 10 clients |
| Landing page (HTML) | `website/main_landing_page.html` in this repo | Updated — ALSflow brand, 3 features, pricing section, animations |
| PDF → Excel n8n workflow | `modelsals482-ops/Test-claude` repo | Built and deployed |
| Czech competitor analysis | `competition/competitors.md` | Complete |
| Business/financial learning | Learning Tracker section below | Ongoing |
| Budget / pricing spreadsheet | `Basic rozpocet.xlsx` in Firm_advisor dir | Complete — min/max scenarios, margins modelled |

---

## 7. Tools & Infrastructure

| Tool | Role |
|---|---|
| **n8n** | Automation delivery platform — self-hosted on Railway |
| **Railway** | Hosting for n8n + Postgres (~€20/month, shared across clients) |
| **Gemini / Google APIs** | AI layer powering client bots |
| **Obsidian** | Knowledge base, session memory, business notes (MCP-connected via `npx mcp-obsidian`, port 27124) |
| **GitHub** | Version control, project docs (branch-per-feature workflow) |
| **VS Code** | Editor (Python HTTP server on port 8000 for local file serving) |
| **Claude Code** | Primary AI coding + business assistant (CLI) |
| **WhatsApp / Custom frontend** | Client-facing delivery channel for bots |

**n8n MCP notes (critical):**
- `create_workflow_from_code` is broken — always creates empty workflows. Write JSON directly into the workflow file and have the user import manually.
- `get_sdk_reference` tool is missing — skip step 1 of MCP instructions
- DO NOT use `xlsx` or `pdf-parse` npm packages in n8n nodes — use built-in `extractFromFile` (PDF) and `convertToFile` (xlsx) nodes instead
- Code nodes: pure JS only, no `require()` unless explicitly confirmed available

---

## 8. Open Questions to Resolve

- [x] Purchase alsflow.cz via Wedos.cz — DONE (2026-04-16)
- [x] Set up info@alsflow.cz email via seznam.cz — DONE (2026-04-16). Domain email propagation pending — wait 24–48h before registering social accounts.
- [ ] Upgrade to Google Workspace (info@alsflow.cz) at first paying client
- [ ] Finalise landing page body copy — outcome-focused, one target client in mind
- [ ] Build cold email sequence (3–5 emails: problem → solution → demo → CTA)
- [ ] Set up LinkedIn content calendar (1–2 posts/week)
- [ ] Set up Instagram account — first 3 posts planned (use info@alsflow.cz once email propagates)
- [ ] Close first paying client (even at a discount — LTV justifies it)
- [ ] Build error-alerting workflow for client monitoring

---

## 9. Business & Financial Learning Tracker

Topics mastered so far (mark at 3 correct applications):

### Understanding Your Own Firm
- [ ] Value Proposition Canvas — what you offer vs. customer pains/gains (0/3)
- [ ] Business Model Canvas — full picture of how your firm operates (0/3)
- [~] Unit Economics — CAC vs. LTV (2/3) ← *next correct use = LEARNED*
- [~] Profit margins — gross margin vs. net margin (1/3)
- [ ] Cash flow vs. profit — why a profitable firm can still go broke (0/3)

### Client Selection
- [ ] ICP (Ideal Customer Profile) — defining who your best client looks like (0/3)
- [ ] TAM / SAM / SOM — sizing your total market vs. realistic target (0/3)
- [ ] RFM Analysis — ranking clients by Recency, Frequency, Monetary value (0/3)
- [ ] Jobs to Be Done (JTBD) — what "job" does your client hire you to do? (0/3)
- [ ] Lead qualification: BANT — Budget, Authority, Need, Timeline (0/3)

### Segmentation & Approach
- [ ] Market segmentation — by size, industry, maturity, behavior (0/3)
- [ ] Ansoff Matrix — grow via existing/new clients × existing/new products (0/3)
- [ ] Positioning — how you are perceived vs. competitors (0/3)
- [ ] Sales motion differences — SMB vs. mid-market vs. enterprise (0/3)

### Competitive Analysis
- [ ] Porter's Five Forces — competitive pressure from all directions (0/3)
- [ ] Competitor positioning map — plot rivals on price vs. value axes (0/3)
- [ ] Win/loss analysis — why you win deals, why you lose them (0/3)
- [ ] Differentiation vs. cost leadership — which strategy you are pursuing (0/3)

### Financial Analysis
- [ ] Income statement basics — revenue, COGS, gross profit, EBITDA, net income (0/3)
- [ ] Balance sheet basics — assets, liabilities, equity (0/3)
- [ ] Key ratios — current ratio, debt/equity, ROE, ROA (0/3)
- [x] Break-even analysis — how much you need to sell to cover costs [LEARNED]
- [ ] Pricing strategy — cost-plus vs. value-based vs. competitive pricing (0/3)

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

- **This repo:** `modelsals482-ops/financial_advisor`
- **Active branch:** `claude/update-docs-cleanup-CPade`
- **Never push to `main` directly**
- **Gitignored (credentials):** `.claude/settings.json`, `.claude/settings.local.json`
- **Allowed pre-approved commands:** see `.claude/settings.local.json` (local disk only)
