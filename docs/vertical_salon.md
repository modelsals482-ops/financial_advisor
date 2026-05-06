# Vertical Deep-Dive: Hair & Beauty Salons
_Last updated: 2026-05-06_

> **Validation status:** Pricing data validated from 4 real Prague salon websites (2026-05-06). Sections still marked ⚠️ need direct salon owner interview before pitching.

---

## 1. Business Profile

**Typical setup:**
- 1–5 stylists. Two common models:
  - **Owner-operated:** Owner does the work + runs the business solo
  - **Chair rental:** Owner rents chairs to freelance stylists who keep their own clients
- Services: haircut, colour, styling, treatments, nails (if beauty salon)
- Session lengths vary widely: haircut 30–45 min, colour 2–3 hours, full treatment 3–4 hours
- Revenue per visit: 500–3,500 CZK depending on service ✅ validated
- Busy hours: weekdays 9–19:00, weekends 9–15:00
- Cannot answer phone during colour application or complex cuts

**Key difference vs. physio:** Salons are more likely to already use a booking app (Fresha, Reservio, Bookio). This is the main objection to prepare for.

---

## 2. Real Prague Salon Pricing (Validated 2026-05-06)

Data from 4 Prague salons: Studio Hair Design, Kadeřnictví LUNA Praha 2, Hairborn, Cutegory.

### Haircuts
| Service | Low-end | Mid | High-end |
|---|---|---|---|
| Dámský střih (women's cut, wash, blowdry) | 790 CZK | 960–1,310 CZK | 1,390–2,000 CZK |
| Pánský střih (men's cut) | 550 CZK | 610–870 CZK | 800–990 CZK |
| Dětský střih (children's) | 400 CZK | 460–560 CZK | — |

### Colour
| Service | Low-end | Mid | High-end |
|---|---|---|---|
| Barvení odrost (root colour) | 750 CZK | 1,300–1,600 CZK | 1,700 CZK |
| Barvení komplet (full colour) | 850–990 CZK | 2,000–2,600 CZK | 2,750 CZK |
| Melír folie (highlights) | 2,000 CZK | 2,800–3,200 CZK | 4,800–5,800 CZK |
| Balayage / AirTouch | 2,900 CZK | 5,800 CZK | 8,800 CZK |
| Average full visit with colour + cut | — | ~3,500 CZK | — |

### Treatments & Extras
| Service | Price |
|---|---|
| Foukaná / blowdry only | 690–1,200 CZK |
| Keratinové narovnání | 1,760–3,290 CZK |
| Trvalá (perm) | 1,900–3,800 CZK |
| Olaplex treatment | 700–1,550 CZK |
| Společenský / svatební účes | 1,770–5,000 CZK |

### Key pricing insight
- **Budget salons:** women's cut 470–790 CZK, colour 750–990 CZK
- **Mid-range (ALSflow ICP):** women's cut 960–1,390 CZK, colour 1,300–2,600 CZK
- **Premium:** women's cut 1,400–2,000 CZK, colour 2,600–8,800 CZK
- **Average visit value (mid-range, colour + cut):** ~3,500 CZK ✅ confirmed by Hairborn
- **ALSflow retainer break-even:** 1.5 extra colour bookings/month covers the entire 5,000 CZK retainer

**Correction to earlier estimate:** Previous estimate of 400–600 CZK for average visit was too low. Mid-range Prague salons earn 1,000–3,500 CZK per visit. This makes the ROI pitch significantly stronger than originally modelled.

---

## 3. ICP Qualifier

**Best-fit salon:**
- 1–3 stylists, owner-operated or with 1–2 employees
- Still running bookings through phone, WhatsApp, or Instagram DMs
- Does NOT already have a functioning, actively used booking tool
- Owner age 25–40, already uses Instagram for marketing, open to automation
- Located in Prague or large Czech city
- Mid-range positioning (not budget, not luxury)

**Disqualifying signals:**
- Already actively using Fresha or Reservio with client self-booking enabled and working ⚠️
- Chain salon with central booking system
- Very low volume (e.g., 2–3 clients/day)

---

## 4. What a Bad Day Looks Like ⚠️

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

## 5. What Missing a Booking Costs (Updated with Real Prices)

| Scenario | Value |
|---|---|
| Average women's cut + blowdry (mid-range) | ~1,100 CZK |
| Average colour visit (mid-range) | ~3,500 CZK |
| No-show on a 2.5h colour slot | ~3,500 CZK wasted |
| Missed bookings per week (estimate) | 3–5 ⚠️ |
| ALSflow retainer | 4,500–5,000 CZK/month |
| Break-even | Capture **1–2 extra colour bookings/month** |

**Updated ROI pitch:** At 3,500 CZK average colour visit, capturing just 2 extra bookings/month = 7,000 CZK recovered. The retainer (5,000 CZK) pays for itself 1.4× over. This is a much stronger number than the original 400–600 CZK estimate.

**Upsell potential:** If 20% of 50 monthly bookings add a 300–500 CZK treatment, that's 3,000–5,000 CZK extra revenue/month — enough to cover the entire retainer from upsells alone.

---

## 6. Booking Patterns ⚠️

| Type | Share (estimate) | Notes |
|---|---|---|
| Recurring regulars | ~60% | Colour clients every 6–8 weeks, cut clients every 4–6 weeks |
| New clients | ~40% | Often via Instagram or word of mouth |

**Seasonal peaks:** Before holidays (Christmas, Easter, graduations), summer — expect volume spikes where missing a booking is even more costly.

**Implication for the bot:** Recurring client recognition matters. A colour client who comes every 6 weeks should get a proactive reminder at week 5: *"Hi, it's been 6 weeks since your last visit — would you like to book your next appointment?"*

---

## 7. Tools They Use Today ⚠️

| Tool | Usage |
|---|---|
| Mobile phone | Primary channel — but unavailable during sessions |
| WhatsApp | Very common for booking — informal, mixes personal and business |
| Instagram DM | Significant source of booking requests, especially for new clients |
| Fresha (formerly Shedul) | Free booking software — popular in Czech salons |
| Reservio / Bookio | Paid alternatives — some salons use these |
| Facebook | Older clients may still message here |
| Google Calendar / paper | Backup or primary for less tech-forward owners |

**Key insight:** Instagram DM as a booking channel is unique to salons vs. physios. A bot that handles Instagram DMs would be a strong differentiator — but this is a roadmap item, not current capability.

**Fresha risk:** Fresha is free and has a client-facing booking page. If a salon is using it well, the pain point is already partially solved. The ALSflow pitch here shifts to: *"Fresha requires your client to find the link and book themselves. We handle the back-and-forth on WhatsApp and email so clients don't have to go anywhere."*

---

## 8. AI Attitude ⚠️

| Owner profile | Attitude | Pitch approach |
|---|---|---|
| Age 22–35, active on Instagram | Positive — already uses tech for marketing | Lead with time saved and upsell revenue |
| Age 35–50, established clientele | Cautious — values personal relationships | Lead with "your clients still talk to you, bot just handles the logistics" |
| Age 50+, traditional | Skeptical | Focus on WhatsApp specifically — frame as "auto-reply when you're busy" |

---

## 9. Top 5 Pitch Objections (Before Signing)

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

**How to handle it:**
- The bot is built with your exact service menu and duration for each service
- During onboarding we map every service to its duration and to which stylist can perform it
- If a client asks for something ambiguous — bot asks a clarifying question before booking
- "We spend 30 minutes during setup making sure the bot knows your menu exactly. If something changes, you message us and we update it same day."

---

### Objection 4: "It's too expensive for what I get"

**Updated answer with real prices:** At 3,500 CZK average colour visit, capturing 2 extra bookings/month = 7,000 CZK recovered vs. 5,000 CZK retainer. Net gain: +2,000 CZK even before upsells.

**How to handle it:**
- "2 extra colour bookings a month covers the entire retainer and you're still up 2,000 CZK."
- "If 10 clients a month add a 400 CZK treatment at confirmation, that's 4,000 CZK extra revenue — the bot effectively costs you nothing."

---

### Objection 5: "I don't want clients to feel like they're talking to a robot"

**How to handle it:**
- "During setup you tell us how you normally talk to clients — formal, casual, with emojis, whatever feels like you. The bot writes exactly like that."
- "If you wouldn't send it yourself, we change it until you would."

---

## 10. Top 5 Post-Deployment Problems (After Going Live)

### Problem 1: Client books a "trim" but means a full restyle — slot is too short
**Solution:** Build clarifying question into flow for variable-duration services. Owner reviews next-day appointments each morning as quality check.

### Problem 2: Salon runs a promotion — bot quotes old prices
**Solution:** Owner messages us when anything changes. We update within 4 business hours.

### Problem 3: New stylist joins — bot doesn't know their schedule
**Solution:** Same update protocol. We add new staff within 24 hours of notification.

### Problem 4: Upsell message feels pushy
**Solution:** One soft upsell per booking, only for relevant services. Opt-out flag — if client declines, not offered again for 3 months.

### Problem 5: Calendar sync breaks — bot offers already-booked slots
**Solution:** Fallback message if calendar read fails. Error alert fires immediately to owner + Jakub.

---

## 11. Pitch for This Vertical

**Opening line:**
> "You're losing bookings every time you're doing someone's colour. The messages pile up and half of them don't wait."

**One-liner:**
> ALSflow replies to your WhatsApp and email bookings while you're working, books the right service with the right stylist, and asks clients if they'd like to add anything — so you earn more per visit without doing more.

**Updated ROI line (use real numbers):**
> "A colour visit in your price range is around 3,500 CZK. If we capture 2 extra bookings a month that would've gone unanswered, that's 7,000 CZK recovered. The retainer is 5,000. You're ahead by 2,000 CZK — before any upsells."

---

## 12. What Still Needs Validation

| Claim | Confidence | How to validate |
|---|---|---|
| Prague haircut price 960–1,390 CZK (mid-range) | ✅ HIGH — checked 4 salons | Done |
| Colour price 1,300–3,500 CZK (mid-range) | ✅ HIGH — checked 4 salons | Done |
| Most salons use WhatsApp as primary channel | Medium ⚠️ | Ask salon owner directly |
| Fresha/Reservio used but clients bypass it | Low ⚠️ | Ask salon owner: "how do most clients actually book?" |
| 60% recurring / 40% new client split | Low ⚠️ | Ask salon owner |
| Missed bookings: 3–5/week | Low ⚠️ | Ask salon owner |
| Upsell conversion rate 1 in 5 | Low ⚠️ | Test with first client |
