# Reset Him

Static site, no build step. Site is branded "Reset Him" throughout (logo, page titles, footer, disclosures) — "The Full Reset" is kept only as the name of the signature bundle offer/page (`/the-full-reset/`), which is a distinct product name, not the site brand. If you'd rather rename the bundle too, say so and I'll update its copy, nav label, and (optionally) its URL.

Structure:

```
/                       → home / hub
/performance/           → 3 offers: The Daily Plan (affiliate), The P-Shot (voucher), GAINSWave (voucher)
/hair/                  → 3 offers: The Daily Plan (affiliate), PRP Restoration (voucher), Transplant Priority Access (voucher)
/the-full-reset/        → signature bundle page
/about/                 → your story / trust page
/contact/               → DM/text CTAs + general pre-booking question form (Netlify Forms)
/terms/                 → Terms & Conditions (template — needs legal review before launch)
docs/booking-workflow.md → the two booking mechanics, CTA copy reference, and confirmation/notification templates
```

Two different mechanics run on the Performance and Hair pages — see `docs/booking-workflow.md` for the full breakdown:
- **Affiliate (The Daily Plan on each page)**: visitor clicks through and completes everything — consult, payment, fulfillment — on the partner's own site. You just earn a commission.
- **Voucher/booking (the other 4 offers)**: visitor pays a deposit to you via a Stripe Payment Link or Square Checkout, gets an instant confirmation, and the partner clinic/medspa follows up to schedule. This is the Groupon-style flow, and it's not built yet — see "Before you go live" below.

## Deploy to Netlify

1. Drag this folder onto [app.netlify.com/drop](https://app.netlify.com/drop), **or**
2. Push it to a GitHub repo and connect it in Netlify (Build command: none, Publish directory: `.`)
3. Netlify auto-detects the booking form in `/contact/index.html` (it's a plain `data-netlify="true"` HTML form — no extra config needed). Submissions show up under **Site → Forms** in the Netlify dashboard. Turn on email notifications there so you get pinged per submission.

## Before you go live — replace these placeholders

- **Affiliate links** — marked with `<!-- PLACEHOLDER AFFILIATE LINK -->` comments in `/performance/index.html` and `/hair/index.html` (The Daily Plan cards, both the primary button and the secondary "instead" link). Swap in your real Hims, BlueChew, and Keeps/Hims Hair affiliate/partner URLs.
- **Voucher checkout links** — the P-Shot, GAINSWave, PRP Restoration, and Transplant Priority Access buttons currently point to `href="#"`, marked `<!-- PLACEHOLDER — replace with your Stripe Payment Link or Square Checkout URL -->`. Nothing will happen when a visitor clicks these until you create a Stripe Payment Link or Square Checkout page per offer (with your real deposit amount) and paste the URL in. This can't be automated on my end — it requires your own Stripe/Square account. See `docs/booking-workflow.md`.
- **`$XX` deposit amounts** — shown in the offer-card subtext under each voucher CTA on `/performance/index.html` and `/hair/index.html`. Set these to match whatever amount your Stripe/Square link actually charges.
- **Confirmation templates** — `docs/booking-workflow.md` has the email, SMS, and partner-notification templates with `[Offer Name]`, `[Partner Name]`, `[XXXX]`, etc. placeholders. Wire these into Stripe/Square's automatic receipt/confirmation settings, or a Zapier/Make automation, once the checkout links exist.
- **`$XXX` / `$X,XXX` value-stack numbers** on `/the-full-reset/index.html` — placeholders in the "here's what's inside" offer card and value table. Fill in real, defensible figures (see compliance note below).
- **"3-night curated experience"** on `/the-full-reset/index.html` — this line item (flights/stay coordination) is new scope beyond ED/hair/PRP. Only keep it if you can actually deliver it; otherwise cut the line and its `$XXX value` entry.
- **`[next quarter]`** in the Full Reset cta-band — spell out the actual next application window.
- **Phone number** — `tel:+10000000000` appears in every footer and on the Contact page. Replace with your real number.
- **Email** — `hello@resethim.com` throughout. Replace with your real inbox.
- **`/terms/index.html`** — every `[Your Business Legal Name]`, `[yourdomain.com]`, `[Your State]`, `[Your County/State]`, and the refund policy in Section 4. This page is a template, not legal advice — see the note at the bottom of the page itself, and get it reviewed by a licensed attorney before launch given the business collects payments and refers to health-adjacent services.
- **Social / DM link** — the Instagram placeholder on the Contact page.
- **About page** — the bio, story, and photo are placeholders (`[Your Name]`, `[Your Photo]`). This is the highest-priority page to personalize — it's what makes people trust the affiliate links.
- **Domain** — once you have a custom domain in Netlify, update the `og:url`/canonical tags if you add them, and double check the disclosure language still matches your actual affiliate relationships.

## Compliance notes (read before publishing)

- Every page carries an **FTC affiliate disclosure** in the footer — required by law when you earn commissions on links. Keep it accurate to whichever programs you're actually enrolled in.
- Copy is written to avoid making specific medical claims or guaranteeing outcomes/prescriptions — it routes users to licensed providers for evaluation instead. Keep new copy in that lane; FTC and FDA both scrutinize ED/hair-loss marketing claims.
- The Contact page form is now a general pre-booking question form, not a scheduling or payment form — keep that distinction if you edit it, since collecting health information directly would introduce HIPAA considerations.
- **Keep the affiliate/voucher language boundary intact.** The Daily Plan cards must never use "consultation," "book," or payment language — that flow belongs entirely to Hims/BlueChew/Keeps. The P-Shot/GAINSWave/PRP/Transplant cards must never claim we perform, prescribe, or guarantee any procedure or outcome — we only collect a deposit and hand off to the partner. The footer disclosures on `/performance/`, `/hair/`, and `/contact/` already spell out this split; keep any new copy consistent with it.
- **Scarcity/urgency claims are flagged inline with `<!-- COMPLIANCE -->` HTML comments** on `/the-full-reset/index.html` — lines like "applications reviewed weekly / next quarter." The FTC treats manufactured scarcity as a deceptive dark pattern when it isn't true. If you don't have a real, checkable limit behind a line like this (actual provider capacity, actual weekly review cadence), soften or remove it rather than publish a fabricated constraint. The equivalent scarcity lines on `/performance/` and `/hair/` were removed in the offer-menu rewrite; if you add new urgency copy (e.g. "limited monthly availability" on GAINSWave) hold it to the same bar.
- The **"$X,XXX value" vs. "$X,XXX price" comparison** on the Full Reset page is standard direct-response structure and is fine *only* if the standalone values are numbers you could show receipts for. An inflated or invented "value" next to a real price is the kind of claim the FTC has pursued as false advertising — price the line items honestly.
