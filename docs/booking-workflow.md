# Booking Workflow Reference

This site runs two separate mechanics. Keep them separate in how you talk about them, price them, and build them — mixing the language is what creates FTC/compliance risk (see `README.md`).

## The two mechanics

**1. Affiliate offers** (The Daily Plan, on both Performance and Hair)
Visitor clicks → leaves the site → lands directly in the partner's (Hims/BlueChew/Keeps) own consult/checkout flow. You never touch payment, never touch "consultation" language — that's entirely between the visitor and the telehealth provider. Your job is the click-through and the commission.

**2. Voucher/booking offers** (P-Shot, GAINSWave, PRP Restoration, Transplant Priority Access)
Visitor books through you, pays a deposit to you, gets a confirmation with the partner name/appointment info, pays the rest at the partner. This is the Groupon-style flow.

## The 6 offers

| Page | Offer | Mechanic | Destination |
|---|---|---|---|
| Performance | The Daily Plan | Affiliate | Hims / BlueChew checkout |
| Performance | The P-Shot | Voucher | Your Stripe/Square checkout |
| Performance | GAINSWave Therapy | Voucher | Your Stripe/Square checkout |
| Hair | The Daily Plan | Affiliate | Keeps / Hims Hair checkout |
| Hair | PRP Restoration | Voucher | Your Stripe/Square checkout |
| Hair | Transplant Priority Access | Voucher | Your Stripe/Square checkout |

## Booking workflow (voucher offers only)

1. Visitor clicks the offer's CTA ("Claim This Offer," "Reserve My Session," "Request Priority Access") — never "book consultation."
2. That button should point straight at a **Stripe Payment Link** or **Square Checkout link**, one per offer. Both let you collect name/email/phone (and a preferred date/time as a custom question) right on the hosted checkout page — no custom form or backend needed on this site.
3. Stripe/Square collects the deposit (you set the amount per offer).
4. Configure an automatic confirmation email/SMS through Stripe/Square (or a Zapier/Make automation triggered off the payment) using the templates below.
5. That same automation should notify the partner medspa/clinic of the new booking (template below).

**Where the 4 voucher CTA buttons live right now**: `performance/index.html` (P-Shot, GAINSWave) and `hair/index.html` (PRP Restoration, Transplant Priority Access), each marked with an HTML comment:
`<!-- PLACEHOLDER — replace with your Stripe Payment Link or Square Checkout URL for this offer -->`
Swap the `href="#"` on each for your real Payment Link once it exists.

## CTA copy reference (already built into the site)

| Offer | Mechanic | Button | Subtext |
|---|---|---|---|
| The Daily Plan (Performance) | Affiliate | Get Started → | Redirects to our licensed treatment partner |
| The P-Shot | Voucher | Claim This Offer → | $XX deposit secures your spot — balance due at appointment |
| GAINSWave Therapy | Voucher | Reserve My Session → | $XX deposit — limited monthly availability |
| The Daily Plan (Hair) | Affiliate | Start My Plan → | Redirects to our licensed treatment partner |
| PRP Restoration | Voucher | Claim This Offer → | $XX deposit — 3-session series with our partner provider |
| Transplant Priority Access | Voucher | Request Priority Access → | $XX deposit — vetted provider, priority scheduling |

The affiliate/voucher button language is intentionally distinct ("Get Started/Start My Plan" vs. "Claim/Reserve/Request") — it signals the different next step to the visitor without you having to explain it, and keeps the copy accurate to what's actually happening in each flow.

## Confirmation templates — voucher/booking offers only

### Email

```
Subject: You're Confirmed — [Offer Name]

Hey [First Name],

You're locked in for [Offer Name] through [Your Brand Name].

Partner Provider: [Medspa/Clinic Name]
Deposit Paid: $[XX]
Balance Due at Appointment: $[XX]
Confirmation Code: [XXXX]

[Partner Name] will reach out directly at [phone number provided] within 24-48 hours to schedule your exact appointment time.

Questions in the meantime? Just reply to this email or reach us at [your contact].

— [Your Brand Name]
```

### Text (SMS)

```
You're confirmed for [Offer Name] w/ [Partner Name]. Deposit: $[XX] paid. They'll text/call within 24-48 hrs to book your time. Code: [XXXX]. Questions? Reply here. — [Brand Name]
```

### Partner notification (goes to the medspa/clinic, not the client)

```
Subject: New Referral — [Offer Name]

New client booked through [Your Brand Name]:

Name: [Client Name]
Phone: [Client Phone]
Email: [Client Email]
Offer: [Offer Name]
Deposit collected: $[XX] (held by us / [payment terms per your agreement])

Please contact the client within 24-48 hrs to schedule. Let us know once the appointment is set — [confirmation.email@yourbrand.com]
```

## Build notes

- Stripe Payment Links or Square Checkout can handle steps 2–4 above with zero custom code — one link per offer, pasted into the matching CTA `href`.
- The confirmation code gives you a simple way to track/reconcile bookings without a database at launch — a spreadsheet with codes, names, and partner names is enough to start.
- Loop the partner notification into whatever you're using for booking (Stripe/Square can trigger this via a Zapier/Make automation, or into Airtable if you want it automated instead of manual).
- Fill in every `$XX`, `[XXXX]`, `[Your Brand Name]`, `[Medspa/Clinic Name]`, and contact placeholder above with real values before wiring this up — see `README.md` → "Before you go live" for the full placeholder list.
