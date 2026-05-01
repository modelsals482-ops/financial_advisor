# Project Context for Claude Code — Financial Advisor Repo

## What this repo is

Business coaching and strategy workspace for an **n8n-based AI Automation MSP**. This repo holds the full business context, financial plan, competitive analysis, and learning tracker used in Claude coaching sessions.

There is no deployable code here. The primary deliverables are documents.

## Repository structure

```
financial-advisor/
  CLAUDE.md                     ← this file — coaching instructions for Claude
  MASTER_CONTEXT.md             ← single source of truth: business context + learning tracker
  final_plan.md                 ← business plan (revenue model, unit economics, next steps)
  financial_analysis_guide.md   ← frameworks reference (ICP, TAM, Porter's, BANT, etc.)
  .gitignore
```

## Working with me

**Who I am:** Jakub. Solo founder, technically advanced. No need to explain tooling basics.

**Rules for Claude:**
- Be direct and concise — no padding, no unsolicited advice
- Always load `MASTER_CONTEXT.md` at the start of a business/financial session
- Update `MASTER_CONTEXT.md` when new decisions are made or context is established
- Never commit credentials to git
- Always develop on a designated branch; never push to `main` directly

## Business coaching rules

- After introducing any business or financial concept, always end with a follow-up question tied to *my specific numbers* — not a generic "did you understand?"
  - Example: after gross margin → *"If your retainer is €150 and cost is €35, what's your gross margin?"*
- Track topic mastery using the Learning Tracker in `MASTER_CONTEXT.md` — 3 correct applications = mark as learned
- Proactively reference relevant unlearned topics when they apply to what I'm asking
- Do not repeat explanations of already-learned topics — reference them briefly and move on

## Business snapshot

**Model:** AI Automation MSP — deploy and fully manage AI bots for small Czech businesses (emails, booking, customer replies via WhatsApp or custom frontend). Client pays a fixed monthly fee, never touches the infrastructure.

| Component | Amount |
|---|---|
| Setup fee (one-time) | €400–800 |
| Monthly retainer | €120–180 (~3,500–4,500 CZK) |
| Gross margin | ~80% |
| Monthly infra cost per client | ~€25–35 |
| LTV (2-year client) | ~€3,600 + setup fee |
| Break-even | 1 client |

**ICP:** Appointment-based local businesses in Prague — vets, dentists, salons, physiotherapists. High admin burden, not technical, misses bookings due to slow replies.

**Main competitor threat:** šéfbot.cz (same MSP model, 400+ clients). Our edge: hyper-focus on local service businesses, public pricing, more personal service.

Full context in `MASTER_CONTEXT.md`.

## Technical infrastructure

**Delivery platform:** n8n — self-hosted on Railway. All client bots run as isolated workflows within a shared n8n instance. Each client gets isolated workflows, credentials, and webhook paths.

**AI layer:** Gemini / Google APIs power the bots. Light usage ~€0.20/month, scales to €5–15 with real client usage.

**Client-facing channels:** WhatsApp integration or a custom frontend (HTML/JS). Never pretend the bot is human — always lead with *"this is an AI assistant."*

**Hosting stack:**
| Tool | Role |
|---|---|
| **n8n** | Automation delivery — self-hosted on Railway |
| **Railway** | Hosting for n8n + Postgres (~€20/month shared across clients) |
| **Gemini / Google APIs** | AI layer powering client bots |
| **WhatsApp / Custom frontend** | Client-facing delivery channel |
| **GitHub** | Version control and project docs |
| **Claude Code** | Primary AI coding + business assistant (CLI) |
| **Obsidian** | Knowledge base, session memory, business notes |

**Infrastructure decision (confirmed):** Shared instance model. Each client is isolated within one Railway-hosted n8n instance. Dedicated instance offered as a paid upgrade (+€30/month) only when a client specifically requests it. Can scale to 20–30 clients without additional hiring.

**Scalability:** Shared instance handles 20–30 clients without extra cost or hiring. Operational break-even at 1 client.

### n8n technical constraints (critical — learned the hard way)

- `create_workflow_from_code` MCP tool is broken — always creates empty workflows. Write JSON directly into the workflow file and have the user import manually.
- `get_sdk_reference` tool is missing from this MCP instance — skip step 1 of MCP instructions.
- **DO NOT use `xlsx` or `pdf-parse` npm packages in n8n nodes** — use built-in nodes instead:
  - PDF extraction → `n8n-nodes-base.extractFromFile` with `operation: "pdf"`
  - Excel creation → `n8n-nodes-base.convertToFile` with `operation: "xlsx"`
- Code nodes: pure JS logic only, no `require()` unless explicitly confirmed available
- `runOnceForAllItems` mode is correct for pipeline-style processing

### Correct workflow for building n8n workflows
1. `search_nodes` — find node IDs for what you need
2. `get_node_types` — get exact parameter names and types
3. Write the JSON directly into the workflow file
4. Tell the user to re-import the file in n8n

## Key reference files

| File | Purpose |
|---|---|
| `MASTER_CONTEXT.md` | Load this every session — business overview, competitor landscape, learning tracker, client profiles |
| `final_plan.md` | Business plan — revenue model, unit economics, acquisition strategy, next steps |
| `financial_analysis_guide.md` | Frameworks reference — ICP, TAM/SAM/SOM, Porter's Five Forces, BANT, Ansoff Matrix, etc. |

## Branch

Always develop on a feature branch. Never push to `main` directly.

## Security notes

- No credentials or API keys belong in this repo
- `.gitignore` is included — ensure any local `.claude/` config files are covered
