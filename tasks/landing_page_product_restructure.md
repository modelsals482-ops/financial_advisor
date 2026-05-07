# Task: Landing Page Product Restructure
_Written by Claude Cowork — 2026-05-06_
_For Claude Code to implement on `modelsals482-ops/app_deployment`_

---

## Context

The product lineup on alsflow.cz is being restructured. Three changes:

1. **PDF Extractor is removed** from the landing page entirely (kept as backend capability, not marketed)
2. **"Email Bot" → renamed to "E-mailové odpovědi"** (same product, clearer name)
3. **"AI Recepce" → renamed to "Rezervace & Připomínky"** (same product, clearer name)
4. **New third product added: "Zpětná vazba & Opakované rezervace"** — replaces PDF Extractor in all three-product layouts

The umbrella framing is **ALSflow AI Asistent** — three modular functions, client picks what they need, full bundle is the anchor.

---

## Product Definitions (new)

### Product 1 — E-mailové odpovědi
_Was: Email Bot_

- **Headline:** `E-mailové odpovědi` (was "Email Bot")
- **Subline:** `Vaše schránka, řízená AI` (keep as is)
- **Price:** 2 500 Kč/měsíc (no change)
- **Bullet points:** keep existing 4 bullets, no change
- **CTA button:** `Chci E-mailové odpovědi →` (was "Chci Email Bot →")
- **Pricing card emoji:** ✉️ (keep)
- **Nav/anchor label:** update any reference from "Email Bot" to "E-mailové odpovědi"

---

### Product 2 — Rezervace & Připomínky
_Was: AI Recepce_

- **Headline:** `Rezervace & Připomínky` (was "AI Recepce")
- **Subline:** `Rezervace bez telefonování` (keep as is)
- **Price:** 4 500 Kč/měsíc (no change)
- **Bullet points:** keep existing 5 bullets, no change
- **CTA button:** `Chci Rezervace & Připomínky →` (was "Chci AI Recepci →")
- **Pricing card emoji:** 📅 (keep)
- **Badge:** "Nejoblíbenější" stays on this card
- **Nav/anchor label:** update any reference from "AI Recepce" to "Rezervace & Připomínky"

---

### Product 3 — Zpětná vazba & Opakované rezervace
_New product — replaces PDF Extractor everywhere_

- **Headline:** `Zpětná vazba & Opakované rezervace`
- **Subline:** `Klienti se vrací sami`
- **Price:** 2 500 Kč/měsíc
- **Pricing card label below price:** `za měsíc · neomezený počet zpráv`
- **Pricing card emoji:** 🔁
- **CTA button:** `Chci Zpětnou vazbu →`

**Feature section body copy (replaces PDF Extractor section):**

> Po každém dokončeném termínu AI automaticky kontaktuje klienta — poděkuje, zeptá se na spokojenost a nabídne rezervaci dalšího termínu. Vy se nemusíte o nic starat.

**Bullet points (4 items):**
- Automatická zpráva po každé návštěvě
- Nabídka opakované rezervace ve správný čas
- Sběr zpětné vazby bez ručního dotazování
- Funguje přes WhatsApp nebo e-mail

**Feature section mock UI element** (replace PDF Extractor mock):
Show a simple WhatsApp-style message thread:
```
ALSflow AI
Dobrý den, Kateřino! Jak jste byla spokojená s dnešní návštěvou?
⭐⭐⭐⭐⭐  Výborně, děkuji!
Skvělé! Příští termín obvykle rezervujete za 6 týdnů —
chcete rovnou zarezervovat?
Ano, prosím.
✓ Rezervováno! Úterý 17. 6. v 10:00. Těšíme se na vás.
```

---

## Bundle Section

Update bundle description line:

**Old:** `Email Bot + AI Recepce + PDF Extractor · Ideální pro ordinace a salony s vyšším provozem`

**New:** `E-mailové odpovědi + Rezervace & Připomínky + Zpětná vazba · Vše co potřebujete pro plný diář`

Price stays: ~7 500 Kč / měsíc

---

## Nav Menu

Current nav: `Funkce | Ceny | Jak to funguje | Ukázka`

No structural change needed — just ensure any in-page anchor links that reference old product names are updated to match new names.

---

## Contact Form — "Zájem o službu" dropdown

**Old options:**
- Email Bot (2 500 Kč/měs)
- AI Recepce (4 500 Kč/měs)
- PDF Extractor (1 500 Kč/měs)
- Bundle — vše (~7 500 Kč/měs)
- Ještě nevím, chci poradit

**New options:**
- E-mailové odpovědi (2 500 Kč/měs)
- Rezervace & Připomínky (4 500 Kč/měs)
- Zpětná vazba & Opakované rezervace (2 500 Kč/měs)
- Bundle — vše (~7 500 Kč/měs)
- Ještě nevím, chci poradit

---

## Contact Form — "Největší problém" dropdown

Add one new option after existing options (before "Jiné"):

`Klienti se nevracejí / chybí opakované rezervace`

---

## Interactive Demo Section

The demo section has two tabs: `✉ Email Bot` and `📅 AI Recepce`.

**Update tab labels:**
- `✉ Email Bot` → `✉ E-mailové odpovědi`
- `📅 AI Recepce` → `📅 Rezervace & Připomínky`

Add a third tab: `🔁 Zpětná vazba`

**Tab 3 content (Zpětná vazba):**
Three example conversations in the same style as existing tabs:

```
KH — Kateřina Horáčková
AI: Jak jste byla spokojená s dnešní návštěvou?
◆ AI zpráva

MS — Marek Škoda
AI: Chcete zarezervovat příští termín?
◆ AI zpráva

LP — Lenka Procházková
AI: Děkujeme za hodnocení! Rezervujeme znovu?
◆ AI zpráva
```

Content of the AI replies (shown on expand/click, same pattern as other tabs) can be placeholder — Claude Code can copy the pattern from existing tab content.

---

## Stats Bar (the 3 big numbers)

Current: `< 2 min | 24/7 | 2–3h`

Update third stat label only:
- **Old:** `UŠETŘENO DENNĚ NA E-MAILECH A REZERVACÍCH`
- **New:** `UŠETŘENO DENNĚ NA KOMUNIKACI SE ZÁKAZNÍKY`

Other two stats unchanged.

---

## What NOT to change

- Hero headline: `VÁŠ E-MAIL. VÁŠ KALENDÁŘ. VÁŠ AI.` — keep exactly as is
- Hero subline — keep exactly as is
- Hero rotating badge (`AI ASISTENT PRO VETERINÁŘE` etc.) — keep as is
- Dashboard mock UI (the activity feed) — keep as is
- `VYTVOŘENO PRO ŽIVNOSTNÍKY` section (icons for salons, vets, dentists, physios) — keep as is
- `POSTUP` section (3 steps) — keep as is
- `POSTAVENO NA TECHNOLOGIÍCH` logo bar — keep as is
- Pricing: all prices unchanged
- Setup fee line: `Jednorázové nastavení: 8 000 – 10 000 Kč` — keep as is
- Privacy policy, cookie banner, footer — keep as is

---

## File locations (from TECHNICAL_CONTEXT.md)

- Local website path: `C:\Users\Jakub\Desktop\html.websites\COMPLETE_PRODUCT\finalized_products\`
- Repo: `modelsals482-ops/app_deployment` (main branch)
- Deploy: Vercel auto-deploys on push to main
- Git push: `git push origin HEAD:main --force` (local branch is `master`)

---

## Done when

- [ ] All three product names updated everywhere (feature sections, pricing cards, nav anchors, CTA buttons, contact form, demo tabs)
- [ ] PDF Extractor section removed from feature list
- [ ] PDF Extractor pricing card removed
- [ ] New "Zpětná vazba & Opakované rezervace" feature section added with mock UI
- [ ] New pricing card added for new product
- [ ] Bundle description updated
- [ ] Contact form dropdowns updated
- [ ] Demo section has third tab
- [ ] Stats bar label updated
- [ ] Site deploys successfully on Vercel with no broken anchors
