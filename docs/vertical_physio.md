# Vertical Deep-Dive: Physiotherapists (Fyzioterapeuti)
_Last updated: 2026-05-06_

---

## 1. Business Profile

**Typical setup:**
- Solo practitioner or small practice (2–5 people)
- Works from a rented room in a health center, private studio, or home office
- Sessions: 45–60 minutes each, back-to-back throughout the day
- Revenue: 800–1,500 CZK per session (Prague average ~1,000–1,200 CZK)
- Typical daily load: 6–8 sessions = 6,000–9,600 CZK/day revenue potential
- Cannot answer phone or emails during active sessions

---

## 2. ICP Qualifier

**Best-fit physio:**
- Solo or 2-person practice (no dedicated admin staff)
- Fully or near-fully booked schedule
- Uses phone + WhatsApp + email as primary communication channels
- Age 28–45, open to tech tools
- Based in Prague or large Czech city

**Disqualifying signals:**
- Has a receptionist or admin — pain point already solved
- Practice management software already in place with booking integration
- Very low session volume (e.g., part-time, <3 sessions/day)

---

## 3. What a Bad Day Looks Like

The physio starts at 8:00. Back-to-back sessions until 18:00. During that time:

- Phone rings 4x. None answered. Two callers don't leave a voicemail — they call a competitor.
- WhatsApp: 3 messages asking about availability. Physio sees them at 19:00 when already exhausted.
- Email: 2 booking requests sit unanswered for 9 hours. One person already found someone else.
- One patient no-shows with no warning. The slot is wasted — no revenue, no way to fill it last minute.
- End of day: 45 minutes of admin — responding to messages, confirming tomorrow's schedule, sending reminders manually.

**Emotional cost:** Constant guilt about unanswered messages. Stress of not knowing who's waiting. Exhaustion from clinical work and admin combined.

---

## 4. What Missing a Booking Costs

| Scenario | Value |
|---|---|
| Missed calls per day | ~2–4 |
| Working days per month | 20 |
| Potential missed bookings per month | 20–40 |
| Average session value (Prague) | ~1,000–1,200 CZK |
| Lost revenue if 50% of missed calls = lost bookings | 10,000–24,000 CZK/month |
| ALSflow retainer (Front Desk) | 4,500–5,000 CZK/month |
| Break-even point | **4–5 extra captured bookings/month** |

Even the most conservative estimate (2 missed bookings captured per month) covers 40–50% of the retainer. Capturing 5 = bot pays for itself.

---

## 5. Booking Patterns

| Type | Share | Notes |
|---|---|---|
| Recurring | ~70% | Rehab patients: weekly for 4–8 weeks (back pain, post-surgery, sports injury) |
| One-time | ~30% | Acute injury check, sports massage, one-off consultation |

**Implication for the bot:** Must understand recurring booking context. A patient who books every Tuesday at 10:00 should be offered to rebook automatically — not start from scratch each time.

---

## 6. Client Demographics (Physio's Patients)

| Segment | Age | Communication preference |
|---|---|---|
| Sports injuries | 20–40 | WhatsApp, email — tech-savvy |
| Post-surgery rehab | All ages | Phone or referred directly by hospital |
| Chronic pain (back, neck) | 35–60 | Phone or email |
| Elderly mobility | 65+ | Phone — may struggle with digital booking |

**Key takeaway:** Bot must handle email + WhatsApp fluently. Phone remains important for elderly patients — bot cannot fully replace phone, but handles the majority of inbound volume.

---

## 7. Tools They Use Today

| Tool | Usage |
|---|---|
| Mobile phone | Primary booking channel — useless during sessions |
| WhatsApp | Informal booking and patient communication — often mixed with personal use |
| Email | Secondary booking channel — slow response times |
| Google Calendar | Most physios use this for scheduling |
| Reservio / Bookio | Some use — only the more tech-forward practitioners |
| Paper notebook | Some older practitioners still use these |

**ALSflow integration target:** Google Calendar (universal) + email. WhatsApp is a strong second channel.

---

## 8. AI Attitude by Owner Profile

| Owner profile | Attitude | Pitch approach |
|---|---|---|
| Age 25–40, urban, solo | Positive — looking for efficiency tools | Lead with time saved |
| Age 40–55, established | Cautious — open if ROI is clear | Lead with missed revenue |
| Age 55+, traditional | Skeptical — fears impersonal feel | Lead with "patients still talk to you, bot just confirms the booking" |

---

## 9. Top 5 Expected Problems (Objections + Solutions)

### Problem 1: "My patients want to talk to a real person"

**Why they say it:** Physio-patient relationships are personal and trust-based. Many patients have been coming for years.

**The reality:** Most patients don't want a conversation — they want a booking confirmed quickly. A bot that responds in 30 seconds beats a physio who responds in 6 hours. Personal rapport is built in the session, not in the booking exchange.

**How to handle it:**
- Bot handles only logistics: availability, confirmation, reminders, FAQ (price, location, cancellation policy)
- Clinical questions → "For questions about your treatment, please call us directly."
- Tone is set by the physio's own wording, which we build into the bot during setup — patients see a fast, professional response, not a generic chatbot

---

### Problem 2: "What if the bot double-books me?"

**Why they say it:** A scheduling mistake in a solo practice is a disaster — two patients show up at the same time.

**The reality:** Calendar sync is the core of the product. The bot reads from Google Calendar in real time — it only offers slots that are confirmed as free.

**How to handle it:**
- Google Calendar integration is read + write: when a booking is confirmed, the slot is immediately blocked
- No slot is offered twice
- If the physio manually adds an appointment in Google Calendar, the bot knows within seconds
- We demonstrate this live during onboarding

---

### Problem 3: "I don't have time to set this up / it sounds complicated"

**Why they say it:** They're exhausted. Any new system feels like more work before it becomes less work.

**The reality:** They don't set anything up. That's the entire ALSflow value proposition.

**How to handle it:**
- "You answer three questions: your services, your prices, and your working hours. We do everything else."
- Onboarding call: 30 minutes. We gather everything we need.
- Live within 5–7 business days.
- If anything needs adjusting, they message us and we fix it — they never touch the system

---

### Problem 4: "It's too expensive / I can't justify this cost"

**Why they say it:** 5,000 CZK/month feels like a big fixed cost for a solo practitioner watching every expense.

**The reality:** Break-even is 4–5 captured bookings per month — likely achieved in the first week.

**How to handle it:**
- "One session is 1,000–1,200 CZK. You need 4–5 extra bookings a month to break even. You're probably missing more than that every single week."
- Offer a 30-day trial if needed to reduce commitment anxiety
- Show the math: even at 2 extra bookings/month, they're recouping 40–50% of the cost

---

### Problem 5: "What if it tells my patients the wrong thing?"

**Why they say it:** A health context raises stakes. They're worried about liability — bot says something wrong, patient acts on it.

**The reality:** The bot has a hard scope. It handles logistics only. No diagnosis, no clinical advice, no treatment recommendations.

**How to handle it:**
- Bot scope is defined and locked: availability, booking, confirmation, reminders, FAQ (address, price, cancellation, payment)
- Any out-of-scope question → "For questions about your treatment, please call [practice name] directly."
- This is built into the system prompt as a hard guardrail — not a suggestion
- We provide written documentation of exactly what the bot can and cannot say, before they sign

---

## 10. Pitch for this Vertical

**Opening line:**
> "You're probably losing 10,000 CZK a month in missed bookings — not because you're not good at your job, but because you can't pick up the phone while you're doing it."

**One-liner:**
> ALSflow handles your bookings, confirmations, and reminders while you're with patients. You set your hours and prices once. We do the rest.

**Proof point to build once first client is live:**
> "Physio in [Prague district] captured 8 extra bookings in the first month."

---

## 11. Outreach Message (Research Phase)

Use this before pitching — for the Mom Test call or short form.

> "Ahoj, jmenuji se Jakub a stavím nástroje pro automatizaci pro malé podnikání. Nezkoumám, co prodat — sbírám podklady přímo od lidí jako vy. Bylo by možné si dát 10 minut call? Rád se dozím, co vám v ordinaci denně komplikuje den — žádný prodej, žádné follow-upy."

**English version:**
> "Hi, my name is Jakub and I build automation tools for small businesses. I'm not researching what to sell — I'm gathering real insight from people like you. Would you have 10 minutes for a quick call? I'd love to learn what makes your day harder than it needs to be — no pitch, no follow-up."
