# n8n Bot Implementation Spec
_Last updated: 2026-05-06_

This document is the technical build guide for all three ALSflow bot products. Use it when building in n8n. Read the relevant vertical doc alongside this for business context.

---

## Architecture Overview

All three bots share the same core loop:

```
Inbound message (email / WhatsApp)
    ↓
Parse intent (AI classification)
    ↓
Route by intent
    ↓
[booking] → Check calendar → Offer slots → Confirm → Write to calendar → Schedule reminders
[cancellation] → Free slot → Notify waitlist
[FAQ] → Look up answer → Respond
[escalate] → Forward to owner
```

The bots differ in:
- How many calendars they read (1 for physio, N for salon)
- Whether upsell logic runs after confirmation (salon only)
- Whether a post-visit trigger exists (vet only)

---

## Shared Infrastructure

| Component | Tool | Notes |
|---|---|—|
| Workflow host | n8n on Railway | Self-hosted instance |
| Calendar | Google Calendar API | One calendar per staff member |
| AI classification | Google Gemini API (existing) | Classify intent + extract entities |
| Email | Gmail or SMTP | Inbound via webhook or polling |
| WhatsApp | WhatsApp Business API (Meta) | Requires Meta Business verification |
| Error alerting | Existing ALSflow alerting workflow | Triggers on any workflow failure |
| Reminders | n8n Schedule/Wait node | Fires at 24h and 1h before appointment |

---

## Bot 1: Physio Front Desk Bot

### Workflow: `physio_front_desk`

#### Nodes (in order)

**1. Trigger: Email Webhook**
- Type: `n8n-nodes-base.webhook`
- Method: POST
- Path: `/physio-inbound-email`
- Fires when email forwarding rule sends to this endpoint
- Alternatively: use Gmail node in polling mode (every 2 min)

**2. Trigger: WhatsApp Inbound** _(separate branch, merges at node 3)_
- Type: `n8n-nodes-base.webhook`
- Method: POST
- Path: `/physio-inbound-whatsapp`
- Payload: standard WhatsApp Business webhook format

**3. Code Node: Parse & Normalise Message**
- Input: raw webhook payload from either channel
- Output: `{ channel, sender_id, sender_name, message_text, timestamp }`
- Normalises both email and WhatsApp into the same shape for downstream nodes

**4. HTTP Request: Classify Intent (Gemini API)**
- Endpoint: Gemini API
- System prompt:
  ```
  You are a classifier for a physiotherapy clinic booking system.
  Classify the message into one of: BOOKING_REQUEST, CANCELLATION, FAQ, CLINICAL_QUESTION, OTHER.
  Also extract: preferred_date (if mentioned), preferred_time (if mentioned), patient_name.
  Return JSON only.
  ```
- Output: `{ intent, preferred_date, preferred_time, patient_name }`

**5. Switch Node: Route by Intent**
- BOOKING_REQUEST → node 6
- CANCELLATION → node 11
- FAQ → node 13
- CLINICAL_QUESTION → node 15
- OTHER → node 15 (escalate to owner)

---

#### Branch A: Booking Request

**6. Google Calendar Node: Get Available Slots**
- Operation: Get Events
- Calendar: physio owner's Google Calendar
- Time range: next 7 days
- Output: list of existing events (blocked times)

**7. Code Node: Calculate Free Slots**
- Input: existing events + working hours config (e.g., Mon-Fri 8:00-18:00, 60-min sessions)
- Logic: iterate through working hours, exclude existing events, return list of free 60-min slots
- Output: `[{ date, start_time, end_time }]` (max 6 slots to offer)

**8. HTTP Request: Generate Offer Message (Gemini API)**
- System prompt:
  ```
  You are a booking assistant for a physiotherapy practice.
  Write a warm, professional reply in Czech offering the following available slots.
  Ask the patient to confirm one. Sign off as the practice name.
  Never discuss clinical matters.
  ```
- Input: free slots list + patient name
- Output: natural language message in Czech

**9. Send Reply (Email or WhatsApp)**
- IF channel == email: use Gmail/SMTP node to reply to thread
- IF channel == whatsapp: use HTTP Request to WhatsApp Business API send endpoint

**10. Wait for Confirmation + Second Webhook**
- Patient replies with chosen slot
- Second trigger catches the reply, routes back to classification
- On re-classification as BOOKING_CONFIRM: proceed to node 10a

**10a. Google Calendar Node: Create Event**
- Operation: Create Event
- Title: `[Pacient: {patient_name}]`
- Start/end: confirmed slot
- Description: booking source (email/whatsapp), phone number if available

**10b. Send Confirmation Message**
- Confirmation template (Czech):
  > "Dobrý den {name}, Váš termín je potvrzen na {date} v {time}. Připomenu Vám jej den předem. V případě zrušení nás prosím informujte alespoň 24 hodin předem. Na shledanou!"

**10c. Schedule Reminder: 24h Before**
- Type: `n8n-nodes-base.wait` (wait until 24h before appointment datetime)
- On fire: send reminder message via original channel
- Reminder text: "Připomínáme Vám zítrší termín v {time}. Těšíme se na Vás!"

**10d. Schedule Reminder: 1h Before**
- Same pattern, fires 1h before appointment

---

#### Branch B: Cancellation

**11. Google Calendar Node: Find and Delete Event**
- Find event matching sender + approximate date
- Delete or mark as cancelled

**12. Code Node: Check Waitlist**
- Query n8n data store or Google Sheet for any waitlisted patients for that time slot
- If waitlist entry exists: trigger outbound message to waitlisted patient offering the slot
- Send cancellation acknowledgement to original patient

---

#### Branch C: FAQ

**13. HTTP Request: Generate FAQ Answer (Gemini)**
- System prompt includes: practice name, address, phone, price list, cancellation policy, parking info
- Gemini generates a natural, Czech-language answer
- Hard rule in prompt: if question is clinical → respond with escalation message regardless

**14. Send Reply**

---

#### Branch D: Escalate to Owner

**15. Send Notification to Owner**
- Forward original message + sender info to owner's WhatsApp or email
- Include context: "This message needs your attention — couldn't be handled automatically."
- Send holding reply to patient: "Děkujeme za zprávu. Ozveme se Vám co nejdříve."

---

### Physio Bot: Config Object (set in n8n environment variables or workflow settings node)

```json
{
  "practice_name": "",
  "google_calendar_id": "",
  "working_hours": { "start": "08:00", "end": "18:00" },
  "working_days": ["Mon", "Tue", "Wed", "Thu", "Fri"],
  "session_duration_minutes": 60,
  "owner_whatsapp": "",
  "owner_email": "",
  "cancellation_policy_hours": 24,
  "faq": {
    "address": "",
    "price": "",
    "parking": "",
    "payment_methods": ""
  }
}
```

---

## Bot 2: Salon Front Desk Bot

### Workflow: `salon_front_desk`

Builds on Bot 1 with these additions:

#### Additional Complexity vs. Physio Bot

1. **Multi-staff calendar** — must read N calendars (one per stylist) and match service to stylist capability
2. **Service duration mapping** — each service has a defined duration; bot must book the right length slot
3. **Upsell logic** — fires after booking confirmation, offers one relevant add-on
4. **Service clarification step** — for ambiguous requests, ask before booking

---

#### Modified / Additional Nodes

**3a. Code Node: Detect Requested Service**
- After normalisation, extract service type from message: `{ service_requested, stylist_preference }`
- Map to service catalogue: `{ service: "colour", duration_minutes: 150, eligible_stylists: ["Jana", "Petra"] }`

**3b. IF Node: Is Service Ambiguous?**
- If message is too vague to determine duration → ask clarifying question before proceeding
- Example trigger: client says "something nice" or "colour" without specifics
- Clarifying question (Czech): "Abyšchom pro Vás našli správný čas — jde o barvení, střížení, nebo obojí?"

**6a. Google Calendar Node: Get Events for ALL Stylists**
- Loop over each stylist's calendar ID
- Merge results into one blocked-times list per stylist

**7a. Code Node: Calculate Free Slots (Multi-Staff)**
- For each eligible stylist (based on requested service), calculate their free slots
- Match slot duration to service duration
- Output: `[{ stylist, date, start_time, end_time }]`
- If client requested specific stylist: filter to that stylist only

**8a. Generate Offer Message**
- Same as physio but includes stylist name in the offer
- Example: "Jana má volné úterý 12. května ve 14:00 (2,5 hodiny). Petra má volné čtvrtek 14. května v 10:00. Který termín Vám vyhovuje?"

**10c. Upsell Node (NEW — fires after confirmation)**
- Trigger: booking confirmed
- Code node: look up upsell map based on booked service
  ```json
  {
    "colour": "toning treatment (+300 CZK)",
    "cut": "deep conditioning mask (+200 CZK)",
    "highlights": "hair gloss treatment (+250 CZK)"
  }
  ```
- Generate upsell message (Gemini): soft, one-time offer
- Send via original channel
- IF client says yes → update event duration + send updated confirmation
- IF client says no / ignores → set flag `upsell_declined = true`, do not repeat for 90 days

---

### Salon Bot: Config Object

```json
{
  "salon_name": "",
  "stylists": [
    {
      "name": "Jana",
      "google_calendar_id": "",
      "services": ["cut", "colour", "highlights", "balayage"]
    }
  ],
  "services": [
    { "name": "cut", "duration_minutes": 45, "price_czk": 500 },
    { "name": "colour", "duration_minutes": 150, "price_czk": 1800 },
    { "name": "highlights", "duration_minutes": 120, "price_czk": 2200 }
  ],
  "upsell_map": {
    "colour": { "name": "toning treatment", "price_czk": 300 },
    "cut": { "name": "conditioning mask", "price_czk": 200 }
  },
  "working_hours": { "start": "09:00", "end": "19:00" },
  "working_days": ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat"]
}
```

---

## Bot 3: Vet Clinic Upsell Bot

> **Status: Concept only.** Do not build until Bot 1 and Bot 2 are live with paying clients. Architecture below is a planning reference.

### Core Difference vs. Bots 1 and 2

This bot adds a **post-visit outbound trigger** — it fires after an appointment ends, not in response to an inbound message.

### Workflow: `vet_post_visit_followup`

#### Trigger Options (choose one during implementation)
- **Option A:** Webhook from clinic management system when appointment is marked complete
- **Option B:** Schedule node that fires 30 min after each appointment end time (requires knowing appointment schedule)
- **Option C:** Manual trigger via a simple form the vet fills in after each visit (lowest tech barrier for first client)

_Option C recommended for first client — lowest integration complexity, proves concept before building full automation._

#### Nodes

**1. Trigger** (per option above)

**2. Code Node: Enrich Visit Data**
- Input: `{ pet_name, owner_name, owner_contact, visit_type, vet_notes_if_any }`
- Map visit type to recommendation template:
  ```json
  {
    "dental_cleaning": "dental chews or water additive",
    "joint_exam": "joint supplement",
    "weight_check": "weight management food",
    "annual_checkup": "general health supplement or parasite prevention"
  }
  ```

**3. HTTP Request: Generate Follow-Up Message (Gemini)**
- System prompt:
  ```
  You are a caring follow-up assistant for a veterinary clinic.
  Write a warm, personal message to the pet owner in Czech.
  Address the pet by name. Reference the visit type.
  Recommend one product naturally. Include a link placeholder.
  Never give clinical advice beyond what the vet has already said.
  ```

**4. Send Message (WhatsApp or Email)**

**5. Schedule Vaccination / Checkup Reminder**
- Calculate next reminder date based on visit type:
  - Annual checkup → remind in 11 months
  - Dental cleaning → remind in 6 months
  - Post-surgery follow-up → remind in 2 weeks
- Store in n8n data table: `{ pet_name, owner_contact, reminder_date, reminder_type }`
- Separate workflow `vet_reminder_trigger` polls this table daily and fires reminders

---

## Build Order

Build in this order to minimise risk and get to a paying client fastest:

1. **Bot 1 (Physio)** — simpler single-calendar, single-staff workflow. First client target.
2. **Bot 2 (Salon)** — multi-staff extension of Bot 1. Second client target.
3. **Bot 3 (Vet)** — new trigger paradigm (outbound post-visit). Build after first two are live and earning.

---

## Known Constraints (n8n on Railway)

- `create_workflow_from_code` MCP tool creates empty workflows — do not use. Build via UI or import JSON directly.
- No `require()` in Code nodes unless package is pre-confirmed available on the instance.
- Do not use `xlsx` or `pdf-parse` npm packages — use n8n built-in `convertToFile` and `extractFromFile` nodes.
- WhatsApp Business API requires Meta Business verification — allow 1–2 weeks for approval before first salon/physio client goes live on WhatsApp channel.
