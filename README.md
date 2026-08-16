# The Full Reset

Static site, no build step. Structure:

```
/                  → home / hub
/performance/      → ED funnel (Hims + BlueChew)
/hair/             → Hair funnel (Keeps + local PRP medspa)
/the-full-reset/   → signature bundle page
/about/            → your story / trust page
/contact/          → DM/text CTAs + PRP consult booking form (Netlify Forms)
```

## Deploy to Netlify

1. Drag this folder onto [app.netlify.com/drop](https://app.netlify.com/drop), **or**
2. Push it to a GitHub repo and connect it in Netlify (Build command: none, Publish directory: `.`)
3. Netlify auto-detects the booking form in `/contact/index.html` (it's a plain `data-netlify="true"` HTML form — no extra config needed). Submissions show up under **Site → Forms** in the Netlify dashboard. Turn on email notifications there so you get pinged per submission.

## Before you go live — replace these placeholders

- **Affiliate links** — marked with `<!-- PLACEHOLDER AFFILIATE LINK -->` comments in `/performance/index.html` and `/hair/index.html`. Swap in your real Hims, BlueChew, and Keeps affiliate/partner URLs.
- **`$XXX` / `$X,XXX` value-stack numbers** on `/the-full-reset/index.html` — placeholders in the "here's what's inside" offer card and value table. Fill in real, defensible figures (see compliance note below).
- **"3-night curated experience"** on `/the-full-reset/index.html` — this line item (flights/stay coordination) is new scope beyond ED/hair/PRP. Only keep it if you can actually deliver it; otherwise cut the line and its `$XXX value` entry.
- **`[next quarter]`** in the Full Reset cta-band — spell out the actual next application window.
- **Phone number** — `tel:+10000000000` appears in every footer and on the Contact page. Replace with your real number.
- **Email** — `hello@thefullreset.com` throughout. Replace with your real inbox.
- **Social / DM link** — the Instagram placeholder on the Contact page.
- **About page** — the bio, story, and photo are placeholders (`[Your Name]`, `[Your Photo]`). This is the highest-priority page to personalize — it's what makes people trust the affiliate links.
- **Domain** — once you have a custom domain in Netlify, update the `og:url`/canonical tags if you add them, and double check the disclosure language still matches your actual affiliate relationships.

## Compliance notes (read before publishing)

- Every page carries an **FTC affiliate disclosure** in the footer — required by law when you earn commissions on links. Keep it accurate to whichever programs you're actually enrolled in.
- Copy is written to avoid making specific medical claims or guaranteeing outcomes/prescriptions — it routes users to licensed providers for evaluation instead. Keep new copy in that lane; FTC and FDA both scrutinize ED/hair-loss marketing claims.
- The PRP booking form explicitly states it's a scheduling request, not a medical intake or a charge — keep that distinction if you edit it, since collecting health information directly would introduce HIPAA considerations.
- **Scarcity/urgency claims are flagged inline with `<!-- COMPLIANCE -->` HTML comments** on `/performance/index.html`, `/hair/index.html`, and `/the-full-reset/index.html` — lines like "spots limited weekly," "guarantees priority placement," and "applications reviewed weekly / next quarter." The FTC treats manufactured scarcity as a deceptive dark pattern when it isn't true. If you don't have a real, checkable limit behind one of these lines (actual provider capacity, actual weekly review cadence), soften or remove it rather than publish a fabricated constraint.
- The **"$X,XXX value" vs. "$X,XXX price" comparison** on the Full Reset page is standard direct-response structure and is fine *only* if the standalone values are numbers you could show receipts for. An inflated or invented "value" next to a real price is the kind of claim the FTC has pursued as false advertising — price the line items honestly.
