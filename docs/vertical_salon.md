# Vertical Deep-Dive: Hair & Beauty Salons
_Last updated: 2026-05-06_

> **Validation status:** This document is a hypothesis built from general market knowledge, not from direct interviews with salon owners. Sections marked ⚠️ need to be validated with a real salon owner before pitching.

---

## 1. Business Profile

**Typical setup:**
- 1–5 stylists. Two common models:
  - **Owner-operated:** Owner does the work + runs the business solo
  - **Chair rental:** Owner rents chairs to freelance stylists who keep their own clients
- Services: haircut, colour, styling, treatments, nails (if beauty salon)
- Session lengths vary widely: haircut 30–45 min, colour 2–3 hours, full treatment 3–4 hours
- Revenue per visit: 350–2,500 CZK depending on service ⚠️
- Busy hours: weekdays 9–19:00, weekends 9–15:00
- Cannot answer phone during colour application or complex cuts

**Key difference vs. physio:** Salons are more likely to already use a booking app (Fresha, Reservio, Bookio). This is the main objection to prepare for.

---

## 2. ICP Qualifier

**Best-fit salon:**
- 1–3 stylists, owner-operated or with 1–2 employees
- Still running bookings through phone, WhatsApp, or Instagram DMs
- Does NOT already have a functioning, actively used booking tool
- Owner age 25–40, already uses Instagram for marketing, open to automation
- Located in Prague or large Czech city

**Disqualifying signals:**
- Already actively using Fresha or Reservio with client self-booking enabled and working ⚠️ (need to understand how often this actually works well for them)
- Chain salon with central booking system
- Very low volume (e.g., 2–3 clients/day)

---

## 3. What a Bad Day Looks Like ⚠️

_Hypothesis — validate with real salon owner._

The stylist starts a 2.5-hour colour job at 10:00. During that time:

- WhatsApp: 5 messages asking for availability. Some want specific times, one asks who does balayage. All go unanswered.
- Instagram DM: 2 booking requests. Also unanswered.
- Phone rings twice. Not answered.
- At 12:30, colour done. Owner now has 9 messages to respond to while prepping for the next client.
- One person who messaged at 10:15 already booked elsewhere.
- A client booked for 14:00 for a "trim" actually wants highlights. Not enough time. Conflict.
- End of day: 30–45 minutes of admin and message catch-up.

**Emotional cost:** Constant anxiety about missed messages. Frustration when clients book the wrong service and throw off the schedule.

---

## 4. What Missing a Booking Costs ⚠️

_Numbers are estimates — validate Prague salon pricing before pitching._

| Scenario | Value |
|---|---|
| Average haircut value (Prague) | ~400–600 CZK |
| Average colour service value | ~1,200–2,000 CZK |
| No-show on a 2.5h colour slot | ~1,500–2,000 CZK wasted |
| Missed bookings per week (estimate) | 3–5 |
| ALSflow retainer | 4,500–5,000 CZK/month |
| Break-even | Capture **3–4 extra bookings/month** |

**Important:** The upsell feature (add-on services at confirmation) creates a second revenue lever. If 20% of confirmed bookings add a 200–400 CZK treatment, on 50 bookings/month that's 2,000–4,000 CZK additional monthly revenue — enough to cover half the retainer just from upsells.

---

## 5. Booking Patterns ⚠️

| Type | Share (estimate) | Notes |
|---|---|---|
| Recurring regulars | ~60% | Colour clients every 6–8 weeks, cut clients every 4–6 weeks |
| New clients | ~40% | Often via Instagram or word of mouth |

**Seasonal peaks:** Before holidays (Christmas, Easter, graduations), summer — expect volume spikes where missing a booking is even more costly.

**Implication for the bot:** Recurring client recognition matters. A colour client who comes every 6 weeks should get a proactive reminder at week 5: *"Hi, it's been 6 weeks since your last visit — would you like to book your next appointment?"*

---

## 6. Tools They Use Today ⚠️

| Tool | Usage |
|---|---|
| Mobile phone | Primary channel — but unavailable during sessions |
| WhatsApp | Very common for booking — informal, mixes personal and business |
| Instagram DM | Significant source of booking requests, especially for new clients |
| Fresha (formerly Shedul) | Free booking software — popular in Czech salons |
| Reservio / Bookio | Paid alternatives — some salons use these |
| Facebook | Older clients may still message here |
| Google Calendar / paper | Backup or primary for less tech-forward owners |

**Key insight:** Instagram DM as a booking channel is unique to salons vs. physios. If the salon owner does any marketing on Instagram, they get booking requests there. A bot that handles Instagram DMs would be a strong differentiator — but this is a roadmap item, not current capability.

**Fresha risk:** Fresha is free and has a client-facing booking page. If a salon is using it well, the pain point is already partially solved. The ALSflow pitch here shifts to: *"Fresha requires your client to find the link and book themselves. We handle the back-and-forth on WhatsApp and email so clients don't have to go anywhere."*

---

## 7. AI Attitude ⚠️

| Owner profile | Attitude | Pitch approach |
|---|---|---|
| Age 22–35, active on Instagram | Positive — already uses tech for marketing | Lead with time saved and upsell revenue |
| Age 35–50, established clientele | Cautious — values personal relationships | Lead with "your clients still talk to you, bot just handles the logistics" |
| Age 50+, traditional | Skeptical | Focus on WhatsApp specifically — frame as "auto-reply when you're busy" |

---

## 8. Top 5 Pitch Objections (Before Signing)

### Objection 1: "I already use Reservio / Fresha / Bookio"

**Why they say it:** They've already solved the booking problem. Why pay for something they have for free?

**The reality:** These tools are passive — the client must find the link and book themselves. They don't handle the WhatsApp message, the Instagram DM, or the back-and-forth about availability. Most salons use Reservio *alongside* WhatsApp because clients don't use the self-booking page.

**How to handle it:**
- "How often do clients actually book through your Reservio page vs. messaging you directly?"
- If they say "half and half" or "mostly message me" — that's the gap ALSflow fills
- We integrate with their existing calendar — we don't replace the tool, we handle the conversations that bypass it

---

### Objection 2: "My clients are loyal regulars — they don't need AI to talk to them"

**Why they say it:** Salon relationships are personal. Long-term clients feel like friends.

**The reality:** Regular clients are the easiest case for automation — they follow a predictable pattern and need simple reminders, not conversation. The personal relationship happens in the chair.

**How to handle it:**
- "The bot doesn't replace the relationship. It sends the reminder, confirms the time, and handles the rebooking. You still do the consultation and the work."
- "Your regulars will appreciate getting a fast response at 22:00 when they suddenly remember they need a colour before their holiday."

---

### Objection 3: "What if it books the wrong stylist or wrong service duration?"

**Why they say it:** Colour takes 2.5 hours. A cut takes 45 minutes. Booking the wrong one ruins the schedule.

**The reality:** This is a real operational concern — it's the most technically valid objection. Our answer needs to be specific.

**How to handle it:**
- The bot is built with your exact service menu and duration for each service
- During onboarding we map every service to its duration and to which stylist can perform it
- If a client asks for something ambiguous ("something with colour") — bot asks a clarifying question before booking
- "We spend 30 minutes during setup making sure the bot knows your menu exactly. If something changes, you message us and we update it same day."

---

### Objection 4: "It's too expensive for what I get"

**Why they say it:** Salons are price-sensitive. Margins are tighter than physio. 5,000 CZK/month is significant.

**The reality:** Two revenue levers — captured missed bookings AND upsell revenue. Both need to be in the pitch.

**How to handle it:**
- Missed bookings: "3–4 extra bookings a month covers the entire retainer."
- Upsell: "If 1 in 5 clients adds a 300 CZK treatment at confirmation, and you do 50 bookings a month, that's 3,000 CZK extra revenue just from the upsell. The bot pays for itself from that alone."
- Frame as two income streams, not one cost

---

### Objection 5: "I don't want clients to feel like they're talking to a robot"

**Why they say it:** Salon culture is warm and personal. A corporate-sounding bot would feel out of place.

**The reality:** The tone is entirely customisable. We write the bot's messages in the owner's voice during setup.

**How to handle it:**
- "During setup you tell us how you normally talk to clients — formal, casual, with emojis, whatever feels like you. The bot writes exactly like that."
- Show an example: a warm, casual confirmation message vs. a generic one
- "If you wouldn't send it yourself, we change it until you would."

---

## 9. Top 5 Post-Deployment Problems (After Going Live)

These are problems that arise after the client signs up. Use this section to prepare your support response and build trust during onboarding.

---

### Problem 1: Client books a "trim" but means a full restyle — slot is too short

**What happens:** Bot books a 45-minute slot based on what the client typed. Client arrives wanting a full transformation. Whole schedule derailed.

**Root cause:** Bot can only book based on what the client says. It can't see hair length, colour history, or current style.

**Solution:**
- Build a clarifying question into the booking flow for any service that has variable duration: *"Is this a regular trim or something more involved? (e.g., colour, major restyle)"*
- Add a note field in the confirmation: client can describe what they want
- Owner reviews next-day appointments each morning — this is their quality check, not eliminated by automation

---

### Problem 2: Salon runs a promotion or changes prices — bot quotes old prices

**What happens:** Owner puts up a 20% off colour promotion on Instagram. Bot keeps quoting full price. Clients are confused.

**Root cause:** Bot's knowledge base is static until we update it.

**Solution:**
- Establish a clear update protocol during onboarding: owner messages us (or a designated number) when anything changes — prices, services, promotions, hours
- We commit to updating within 4 business hours
- Long term: build a simple "bot settings" interface so owner can update FAQs themselves (roadmap item)

---

### Problem 3: New stylist joins — bot doesn't know their schedule or specialties

**What happens:** Owner hires a new nail technician. Clients ask about nail services. Bot either says "we don't offer that" or books incorrectly.

**Root cause:** Bot's staff knowledge is set during onboarding and doesn't auto-update.

**Solution:**
- Same update protocol as Problem 2 — any change to staff = owner notifies us
- We add the new staff member's calendar integration and service mapping within 24 hours
- "Think of us as your IT team for the bot — any change to your business, you tell us and we handle it."

---

### Problem 4: Upsell message feels pushy — client complains or opts out

**What happens:** Client confirms a simple haircut. Bot immediately suggests an add-on. Client replies "please stop sending me offers." Owner feels embarrassed.

**Root cause:** Upsell tone or timing was too aggressive, or the offer wasn't relevant to the booked service.

**Solution:**
- Upsell is triggered only for services where an add-on genuinely makes sense (e.g., colour → toning treatment, cut → conditioning mask)
- Tone is soft and optional: *"If you'd like to add X — just let me know and I'll include it. Otherwise see you on [date]!"*
- One upsell attempt per booking, never repeated
- Opt-out flag: if client declines, they're not offered again for 3 months

---

### Problem 5: Calendar sync breaks — bot offers already-booked slots

**What happens:** Google Calendar API has a temporary outage or permission expires. Bot loses access to the calendar and starts offering any slot as "available."

**Root cause:** Technical failure in the calendar integration.

**Solution:**
- Build a fallback: if calendar read fails, bot responds with *"I'm having trouble checking the schedule right now — please message us directly and we'll confirm within 2 hours."* Never offer slots when calendar status is unknown.
- Set up an error alert (already in place via ALSflow error-alerting workflow) — owner and Jakub are notified immediately when calendar sync fails
- Calendar API token refresh is automated — permission expiry handled proactively, not reactively

---

## 10. Pitch for This Vertical

**Opening line:**
> "You're losing bookings every time you're doing someone's colour. The messages pile up and half of them don't wait."

**One-liner:**
> ALSflow replies to your WhatsApp and email bookings while you're working, books the right service with the right stylist, and asks clients if they'd like to add anything — so you earn more per visit without doing more.

**Upsell angle (unique to this vertical):**
> "Most of our salon clients find the bot pays for itself just from the add-on suggestions. You do 50 bookings a month — if 10 clients add a 300 CZK treatment, that's 3,000 CZK in extra revenue. The retainer effectively costs you nothing."

---

## 11. What Needs Validation Before Pitching

| Claim | Confidence | How to validate |
|---|---|---|
| Prague haircut price 400–600 CZK | Medium | Check 5 Prague salon websites |
| Colour price 1,200–2,000 CZK | Medium | Check 5 Prague salon websites |
| Most salons use WhatsApp as primary channel | Medium | Ask salon owner directly |
| Fresha/Reservio used but clients bypass it | Low | Ask salon owner: "how do most clients actually book with you?" |
| 60% recurring / 40% new client split | Low | Ask salon owner |
| Upsell conversion rate 1 in 5 | Low | Test with first client — no data yet |
