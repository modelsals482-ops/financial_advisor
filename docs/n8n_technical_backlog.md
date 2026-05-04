# n8n Technical Backlog
_Added: 2026-05-04 — sourced from product review session with professional software sales advisor_

These are technical items that need to be built or designed in n8n. Each section describes the problem, the expected behaviour, and the implementation approach.

---

## 1. Edge Case Handling — Booking Failures, Dual Appointments, Undelivered Messages

**Problem:** Solving the client's booking problem must not introduce new ones. The three most likely failure modes are:

1. **Dual / conflicting appointments** — A time slot is confirmed by the AI but gets double-booked because two requests arrive nearly simultaneously, or the calendar write fails after the confirmation message is sent.
2. **Undelivered messages** — The bot sends a confirmation or reminder but the WhatsApp/email delivery fails silently. The client is never notified.
3. **Booking write failure** — Google Calendar API error, timeout, or auth expiry means the appointment is confirmed to the customer but never actually written.

**Expected behaviour:**
- Check slot availability immediately before writing to calendar (not just at start of conversation)
- If slot is taken between confirmation and write: apologise, re-offer next available slot
- On delivery failure: retry once, then alert the business owner via email/WhatsApp
- On calendar write failure: do not confirm to the customer; surface the error to the owner immediately
- Log all failures to a Google Sheet or n8n data store for audit

**Implementation notes:**
- Add an explicit "is slot still free?" check as the final step before calendar write
- Every response node should have an error branch wired to an owner-alert node
- Use n8n's built-in error workflow trigger for unhandled exceptions
- See also: error-alerting workflow already deployed (2026-05-03)

---

## 2. Recurring vs One-Time Appointment Infrastructure

**Problem:** Recurring appointments (weekly physio, monthly salon visit, quarterly vet check-up) require fundamentally different workflow logic than one-time bookings. The current infrastructure is designed for one-time only.

**Key differences:**

| Aspect | One-time booking | Recurring booking |
|---|---|---|
| Calendar write | Single event | Event series (RRULE) or multiple events |
| Reminder logic | One reminder per event | Per-occurrence reminder cadence |
| Cancellation | Cancel the event | Cancel one occurrence vs. entire series |
| Client data | Basic contact info | Preference history, frequency, last visit |
| Rescheduling | Rebook from scratch | Shift one occurrence or shift entire series |
| Infra complexity | Low | Medium-High |
| Pricing implication | Base price | Higher — charge more |

**Implementation notes:**
- Build recurring booking as a **separate workflow variant**, not a branch of the one-time workflow
- Store recurrence preference in client profile (Google Sheet or n8n data store)
- Use Google Calendar's `recurrence` field with RRULE for series creation
- Cancellation handler must ask: "Cancel just this visit or all future visits?"
- Recurring clients are stickier — flag them in the client profile

**Pricing note:** Recurring appointment handling is more complex and more valuable. Price the recurring variant higher than one-time. This is a separate line item or a premium tier.

---

## 3. Waitlist / Cancellation Fill Feature

**Problem:** When a client cancels, the freed slot goes to waste. Other clients who wanted that time but couldn't get it have no way to be notified automatically.

**Expected behaviour:**
1. Client cancels an appointment (via bot conversation or direct message)
2. Bot detects the cancellation
3. Bot queries the waitlist for that business (stored in Google Sheet or n8n data store)
4. Bot sends a message to the first N waitlisted clients: *"A slot opened on [date] at [time] — reply YES to book it"*
5. First client to confirm gets the slot; all others receive a polite decline
6. If no waitlisted clients, owner is notified of the open slot

**Implementation notes:**
- Waitlist data store: Google Sheet (one per client business) with columns: name, contact, requested date range, timestamp added
- Cancellation trigger: Google Calendar webhook (preferred) or a "cancel my appointment" intent in the bot conversation
- Fan-out send: n8n HTTP node or WhatsApp node to send to top N (start with N=3)
- Race condition: use a "claimed" flag in the sheet — first write wins; subsequent confirmations get declined
- Timeout: if no reply within 2 hours, move to next person on waitlist

**This is an optional add-on** — not all clients will want it. Offer it as part of the full bundle or as a paid add-on.

---

## 4. Landing Page Performance — Lightweight Version

**Problem:** alsflow.cz has heavy animations that may cause poor performance on lower-end devices or slow mobile connections. Some target clients (60-year-old dentist, rural vet) may be on older hardware or slower networks.

**Steps to take:**
1. Run a Lighthouse audit on alsflow.cz — identify which animations/assets are heaviest
2. Check `prefers-reduced-motion` CSS media query — respect it if already not handled
3. Lazy-load any below-the-fold animations
4. Consider a `?lite=1` query param version that strips animations entirely (useful for demos on slow connections)
5. Compress all images if not already done (WebP format)
6. Check Time to Interactive (TTI) — target < 3s on 4G

**Note:** This is a frontend task (app_deployment repo), not an n8n task — listed here because it was flagged in the same review session.

---

## 5. Post-Appointment Upsell Module (Add-on)

**Problem:** After an appointment is completed, there is an opportunity to recommend a relevant product or service and earn a margin on it.

**Expected behaviour:**
- After appointment completion (triggered by calendar event end time or manual signal), bot sends a follow-up message
- Message includes a personalised recommendation based on the appointment type (e.g., after vet visit → recommend flea treatment; after physio → recommend exercise band)
- Recommendation links to a product with a tracked affiliate or referral margin
- Client can reply to buy, get more info, or decline

**Implementation notes:**
- Product catalogue: per-business Google Sheet with product name, description, link, margin
- Trigger: Google Calendar event end + buffer time (e.g., 30 min after)
- Recommendation logic: rule-based first (appointment type → product category), upgrade to AI-generated later
- This is a separate workflow, not part of the booking flow
- **Price this as a separate add-on** — it generates revenue for the client, so value-based pricing applies

---

## 6. Persona-Specific UI Variants

**Problem:** A generic bot UI does not serve all clients equally. A 60-year-old dentist's patients expect different language, font size, and interaction patterns than a 35-year-old physio's patients.

**Considerations:**
- Older users: larger touch targets, simpler language, fewer steps, explicit confirmation screens
- Younger users: faster flow, more casual tone, inline suggestions
- Per-vertical customisation checklist needed (vet vs. dentist vs. salon vs. physio)
- UI skin / theme should be configurable per client without rebuilding the workflow

**Implementation notes:**
- Store per-client config in a Google Sheet or n8n variable: `tone` (formal/casual), `confirm_steps` (1/2), `language_level` (simple/standard)
- Pass config into the AI system prompt at workflow start
- Do not hard-code tone into the workflow — make it a parameter

---
_For business-side context, see `MASTER_CONTEXT.md §8` open questions._
