# Technical Context — Claude Code
_Load alongside MASTER_CONTEXT.md at every session start._
_Last updated: 2026-05-06_

> **This file is owned by Claude Code.** Only the technical agent edits this. Cowork reads MASTER_CONTEXT.md §4 for project status updates.

---

## Working With Me

**Who I am:** Jakub. Solo founder, technically advanced. Comfortable with git CLI, APIs, raw JSON, curl, Python, n8n internals. No need to explain tooling basics.

**Rules:**
- Be direct and concise — no padding, no unsolicited refactoring or advice
- Never commit credentials to git (`.claude/settings.json`, `.claude/settings.local.json` are always gitignored)
- Always develop on a designated branch; never push to `main` directly
- Update MASTER_CONTEXT.md §4 when a project's build status changes
- Pre-approved bash/MCP commands live in `.claude/settings.local.json` — do not re-ask for permission on those

---

## Tools & Infrastructure

| Tool | Role |
|---|---|
| **n8n** | Automation delivery — self-hosted on Railway |
| **Railway** | Hosting for n8n + Postgres (~€20/month, shared across clients) |
| **Gemini / Google APIs** | AI layer powering client bots |
| **Vercel** | Static hosting for alsflow.cz (free tier, auto-deploy from GitHub) |
| **Google Analytics** | GA4 property G-CEX6XVFWD7 — Consent Mode v2 active |
| **GitHub** | Version control, project docs |
| **Claude Code** | Primary AI coding + business assistant (CLI) |

**n8n MCP critical notes:**
- `create_workflow_from_code` is broken — always creates empty workflows. Build via UI or import JSON directly.
- `get_sdk_reference` tool is missing — skip step 1 of MCP instructions
- DO NOT use `xlsx` or `pdf-parse` npm packages — use built-in `extractFromFile` (PDF) and `convertToFile` (xlsx) nodes
- Code nodes: pure JS only, no `require()` unless explicitly confirmed available on the instance
- After 2 failed `validate_workflow` attempts → cut losses and fall back to UI instructions

---

## Deployment Stack

| Component | Detail |
|---|---|
| Business context repo | `modelsals482-ops/financial_advisor` (main branch) |
| Website repo | `modelsals482-ops/app_deployment` (main branch) |
| Hosting | Vercel (free tier) — auto-deploys on push to main |
| Domain | alsflow.cz via Wedos — A record `76.76.21.21` + CNAME `www` → `16012d20c360ac1a.vercel-dns-017.com` |
| Local website path | `C:\Users\Jakub\Desktop\html.websites\COMPLETE_PRODUCT\finalized_products\` |
| Git push note | Local branch is `master`, remote is `main` — push with `git push origin HEAD:main --force` |

---

## Git & Repo Conventions

- **Never push to `main` directly**
- **Gitignored (credentials):** `.claude/settings.json`, `.claude/settings.local.json`
- **Website git note:** local branch is `master`, remote is `main` — push with `git push origin HEAD:main --force`

---

## Open Technical Tasks

**Build queue (in order):**
- [ ] Build Bot 1: Physio Front Desk in n8n — spec in `docs/n8n_bot_implementation.md`
- [ ] Build Bot 2: Salon Front Desk in n8n
- [ ] Bot 3 (Vet Upsell) — concept only, do not build until Bots 1 and 2 are live with paying clients

**Infrastructure:**
- [ ] WhatsApp Business API — Meta Business verification required (allow 1–2 weeks)
- [ ] Edge case handling: dual bookings, undelivered messages, booking failures — define failure mode policies
- [ ] Recurring vs one-time appointment workflow variant
- [ ] Waitlist feature: auto-notify waitlisted clients when slot opens
- [ ] Landing page: audit animation weight, build lightweight version for slower connections

**Admin (unblock with OSVČ registration):**
- [ ] Add IČO to `ochrana_dat.html` + `faktura_sablona.html` once registered

---

## Key Docs (in financial_advisor repo)

| File | Purpose |
|---|---|
| `docs/n8n_bot_implementation.md` | Node-by-node build spec for all 3 bots |
| `docs/bot_catalogue.md` | Bot product catalogue with pricing and status |
| `docs/vertical_physio.md` | Physio ICP + Top 5 problems |
| `docs/vertical_salon.md` | Salon ICP + Top 5 problems |
| `docs/n8n_technical_backlog.md` | Full n8n technical backlog |
| `docs/client_acquisition_path.md` | Client acquisition playbook |
