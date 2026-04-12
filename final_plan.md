# Business Plan — AI Automation MSP

_Last updated: 2026-04-12_
_Read this file at the start of each session to restore context._

---

## 1. What the Business Is

An **n8n-based AI automation service** delivered as a managed service. The product is a deployed bot (integrated via a custom frontend or WhatsApp/other messaging apps) that handles emails, paperwork, and customer support for the client — freeing up their time for revenue-generating work.

The client does not need technical skills. Everything is managed remotely by the founder.

---

## 2. Target Clients (ICP)

**Best fit:**
- Appointment-based local businesses in Prague: vets, dentists, salons, physios
- Freelancers
- Small firms (2–10 people)

**Shared characteristic:** high admin burden, owner wears many hats, limited time, not technical, misses bookings due to missed calls or slow replies.

**Segmentation by channel:**
| Client type | Best acquisition channel |
|---|---|
| Local businesses | Instagram + WhatsApp demo |
| Freelancers | LinkedIn + cold email |
| Small firms | LinkedIn + cold email + referral |

---

## 3. Business Model

**MSP (Managed Service Provider) model:**
- Founder owns and manages all infrastructure
- Client pays a fixed monthly fee — no technical involvement required
- Founder has margin on underlying API/usage costs

**Revenue structure:**
| Component | Amount | Notes |
|---|---|---|
| Setup fee (one-time) | €400–800 | Covers deployment, workflow build, integration |
| Monthly retainer | €120–180 (~3,500–4,500 CZK) | Hosting, API costs, monitoring, support |
| Fair-use cap (included) | 1 500 automaticky zodpovězených e-mailů + 750 rezervací přes AI sekretářku/měsíc | Naprostá většina ordinací tohoto limitu nikdy nedosáhne |
| Usage overage | Cost + 30% | Above fair-use threshold |

**Infrastructure decision:** Shared n8n instance. Each client gets isolated workflows, credentials, and webhook paths. Dedicated instance offered as premium upgrade (+€30/month) only on request.

---

## 4. Unit Economics

| Metric | Value |
|---|---|
| Monthly cost per client | ~€25–35 |
| Monthly revenue per client | ~€150 (~3,750 CZK) |
| Gross margin | ~80% |
| LTV (2-year client) | ~€3,600 + setup fee (~270,000 CZK for 3 clients) |
| CAC (currently) | ~€0 (personal network) |
| LTV:CAC ratio | ~18:1 |

**At 10 clients:** ~€1,200/month recurring profit + setup fees.

---

## 5. Personal Finances & Runway

| Item | CZK/month |
|---|---|
| Father's support (student) | +12,000 |
| Food | −12,000 |
| Claude Code | −500 |
| Railway (own instance) | −500 |
| **Net personal burn** | **~−1,000** |

**Operational break-even:** 1 client (~3,750 CZK in vs. ~1,000 CZK burn = net +2,750/month)
**Investment available:** ~50,000 CZK from friends = **pure growth capital** (~50 months runway at zero clients)
**No pressure to discount** — student situation means living costs are covered independently.

**Ad spend example:** 20,000 CZK on Instagram ads → 3 clients → 8,250 CZK/month net → payback in ~2.4 months → LTV of those 3 clients = ~270,000 CZK.

---

## 6. Infrastructure & Operations

- **Hosting:** Railway (n8n + Postgres) — ~€20/month shared instance
- **AI/API:** Gemini / Google APIs — ~€0.20/month light use, scales to €5–15 with real usage
- **Support:** Automated error workflow alerts both founder and client before client notices
- **Scalability:** Can handle 20–30 clients without additional hiring

---

## 7. Acquisition Strategy

**Phase 1 (first 10 clients):**
1. Cold email local businesses → link to landing page with live demo
2. LinkedIn posts targeting freelancers and small business owners
3. Instagram content showing "time saved" outcomes (not tech features)
4. Personal network referrals

**Landing page headline:**
```
VÁŠ E-MAIL.
VÁŠ KALENDÁŘ.
VÁŠ AI.
```

**Key rule on WhatsApp demo:** Never pretend the bot is human. Always lead with *"this is an AI assistant"* — the demo sells itself, and deception risks trust and EU legal compliance.

**Value proposition (target framing):**
> *"Automate your emails and customer replies so you can focus on the work that actually pays."*

---

## 8. Next Steps (Prioritised)

- [ ] Finalise landing page body copy — outcome-focused, one target client in mind
- [ ] Build cold email sequence (3–5 emails: problem → solution → demo → CTA)
- [ ] Set up LinkedIn content calendar (1–2 posts/week)
- [ ] Set up Instagram account — first 3 posts planned
- [ ] Close first paying client (no need to discount — LTV justifies patience)
- [ ] Build error-alerting workflow for client monitoring

---

## 9. Open Questions to Resolve

1. Landing page body copy — what does it say beyond the headline?
