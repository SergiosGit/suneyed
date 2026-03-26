# SunEyed Monetization Strategy

*Working document — March 2026*

---

## Business Context

SunEyed is a free iOS app that lets homeowners calculate solar panel ROI using real local weather data, before talking to a salesperson. The trust proposition is explicit: no sign-up, no data harvesting, no sales pitch.

Two distinct user groups create two distinct monetization opportunities:

1. **Homeowners** — the app's primary audience. Must remain free and unmonetized to preserve trust.
2. **Solar installers** — want access to homeowners who are already educated and ready to buy.

---

## Revenue Stream 1: Installer App Subscription

### Concept
Installers who use SunEyed as a professional tool during customer visits pay a yearly subscription. The free version remains fully functional for homeowners; the subscription unlocks business-use features.

### Recommended price
**$149–199/year** (original proposal was $99 — too low for a B2B tool used in a $15k–40k sale).

### Required feature gate
The subscription only has value if there are clear features a professional needs that a homeowner doesn't. Without this, installers use the free version and you get nothing. Suggested pro-only features:

- Save and export customer scenarios as a PDF summary (branded, leave-behind)
- Multi-project management (multiple clients saved simultaneously)
- Company branding on exported reports
- Team/company account (multiple seats)

### Open questions
- Which features are technically feasible in the near term?
- Is the primary use case "in-home with the customer" or "back-office quoting"? This shapes which features matter most.
- How do you enforce business use vs. personal use? (Likely: honor system + feature value. Don't over-engineer enforcement.)

---

## Revenue Stream 2: Installer Lead Generation

### Concept
Installers sign up to be listed in the app's "Find an Installer" directory. Homeowners who are ready to get a quote can tap "Request Quote" — triggering a lead notification to the installer with the homeowner's full SunEyed summary (system size, annual savings, payback period, roof config, location).

### Recommended model: Two tiers

| Tier | Price | What they get |
|---|---|---|
| Directory Listing | Free | Name, city, phone, website in directory. No quote button. No leads. |
| Pay-per-Lead | First 3 free, then $35–50/lead | "Request Quote" button, full lead summary emailed on delivery, charged per lead |

### Why keep a free directory tier
There is a chicken-and-egg problem: homeowners won't tap "Find an Installer" if the directory is empty. Installers won't pay per lead if there are no homeowners yet. A zero-friction free tier builds installer supply before lead volume exists. It costs nothing and removes the barrier to getting listed.

### Why pay-per-lead (not monthly subscription)
A monthly flat fee requires enough app users in each installer's market to justify the cost. At launch, that density doesn't exist in most markets. Pay-per-lead scales naturally — installers only pay when leads arrive, making sign-up genuinely risk-free. This is the right model for the current stage.

### Lead pricing rationale
A closed residential solar deal generates $15,000–40,000 in revenue for the installer. Even at a 10% close rate, a $35–50 lead has a 30–80x return on investment. The original $20–50 range was likely underpriced. Start at $35–50 and test upward as lead quality is proven.

### Lead definition (critical — must be decided before launch)
A "lead" should be defined precisely to avoid billing disputes. **Recommended trigger: the moment the installer receives the homeowner's email with their SunEyed summary.** This is objective, verifiable, and tied to a real action by the homeowner.

Do not trigger on: homeowner viewing the installer's profile, homeowner copying a summary without contacting anyone.

### Open questions
- What payment infrastructure will handle per-lead billing? (Stripe Billing with metered usage is a natural fit.)
- How does the lead flow technically? Does the homeowner submit a form in-app, or is it an email handoff?
- What data is included in the lead summary sent to the installer?
- What happens if a homeowner contacts multiple installers? Is the lead charged to each? (Yes — each installer who receives the lead should be charged independently.)
- What's the refund/dispute policy for bad leads (e.g. wrong contact info)?

---

## How the Two Streams Interact

The two streams serve different installer personas but are not mutually exclusive:

- An installer who uses the **app subscription** is using SunEyed as a sales tool with existing customers.
- An installer who buys **pay-per-lead** is using SunEyed for inbound marketing.
- An installer could do both — and that is the ideal customer.

**Recommended acquisition funnel:**
1. Installer signs up for free directory listing (zero friction)
2. Installer activates pay-per-lead, gets first 3 leads free
3. Installer sees lead quality, converts to paid
4. Installer discovers the app, buys the pro subscription to use with clients

---

## What to Build First

Given limited development resources, prioritize in this order:

1. **Free directory listing + pay-per-lead sign-up form** — the website already has most of this. Needs payment integration and a defined lead delivery mechanism.
2. **"Request Quote" flow in the app** — the in-app touchpoint that generates leads. This is the critical path for lead revenue.
3. **Installer app subscription** — higher implementation complexity (App Store subscription, feature gating). Build this after lead flow is proven.

---

## Risks and Mitigations

| Risk | Mitigation |
|---|---|
| Low app user density in installer's market — no leads generated | Set expectations at sign-up. Free tier keeps installers listed through the ramp-up period. |
| Installers dispute lead quality | Define lead clearly (see above). Consider a simple refund policy for demonstrably bad data (bounced email, wrong number). |
| Installers use free app instead of paying for subscription | Only viable if pro features are genuinely valuable. Prioritize export/PDF feature — homeowners don't need it, installers do. |
| Pricing too low to be worth operating | Review pricing after first 50 leads. $35–50 is a floor, not a ceiling. |
