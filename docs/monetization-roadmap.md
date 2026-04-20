# Monetization Roadmap — The Condenser / BuildCore

**Audience:** internal. Paige + future operator.
**Status:** v1 · 2026-04-20 · locked through launch
**Revisited:** quarterly

---

## Guiding principles

1. **Paid tiers must feel like the free tier, just less constrained.** No feature amputation for Starter. Caps, not cripples.
2. **Price the pain, not the feature.** A CM closing 6 houses a week saves 8–10 hours of desk time. $39 is priced against that labor, not against "the market rate for SaaS."
3. **Annual discount is modest on purpose.** 18% off — enough to reward commitment, not so aggressive it trains people to wait for discounts. Never run sitewide promotions.
4. **Team pricing is per-seat, not per-company.** Multi-seat behavior differs from single-CM behavior. The jump from Pro → Team is a workflow change, not a feature unlock.
5. **Enterprise is real procurement.** SSO, SLA, dedicated onboarding. It starts at a floor of $2k/mo. We do not chase 5-seat "enterprise" deals.

---

## Current tiers (locked for launch)

| Tier | Monthly | Annual | Target user |
|---|---|---|---|
| Starter | Free | Free | Solo CM testing the tool or using it on 1–2 lots |
| Pro | $39/mo | $32/mo (annual) | Solo CM running a full book of work |
| Team | $29/seat/mo | $24/seat/mo (annual) | Builder with 2+ CMs sharing contacts/templates |
| Enterprise | Custom (≥ $2k/mo floor) | Custom | Production builder, 10+ seats, SSO required |

**Trial:** 7 days. No credit card. Trial applies to Pro + Team. Starter stays free forever.

**Billing:** Stripe (not yet wired — manual invoicing through founding phase).

---

## Upgrade path (what actually makes someone move tiers)

### Starter → Pro

- Hit the 5-project cap on Starter (hard cap, shown in UI when you try to create the 6th)
- Need priority/aging flags (invisible on Starter, revealed in UI at the upgrade prompt)
- Send to a homeowner (gated — "Upgrade to send homeowner updates")

**Expected timing:** week 2–3 of real use. If they're still under 5 projects at week 4, they're not the ICP and shouldn't upgrade. Don't force it.

### Pro → Team

- A second person at their office signs up with the same company email (domain match triggers a "looks like you work together — Team is built for this" prompt)
- The user tries to share a contact list across two Pros and realizes they can't
- The builder's office manager wants oversight of punch data

**Expected timing:** month 3+ for organic growth. Most Team sales will come from direct outreach to builders, not Pro-upgrade conversion.

### Team → Enterprise

- Seat count crosses 10 (auto-flag — Paige reaches out)
- Request for SSO, SAML, or procurement process
- Request for a signed MSA or custom SLA

---

## Founding-user economics

- 50 spots at founding pricing (whatever plan they pick, locked forever at current rates)
- Grandfather clause means if we raise Pro to $49 in 2027, founding users still pay $39. That's the cost of their early trust.
- Assumption: 50 founding users at avg $25/mo = ~$15k ARR. This is a truth-telling number, not a growth number. Don't over-index.

---

## What we will NOT do (for at least 12 months)

- **Freemium with ads.** Never.
- **Lifetime deals.** Kills LTV and signals desperation.
- **AppSumo / stackable deals.** Wrong audience.
- **Usage-based pricing on punch items.** Psychologically discourages the exact behavior we need (lots of items captured).
- **Consumption pricing on AI.** Absorbed into tier cost. We eat Anthropic costs as a function of price. If we miscalculate, we raise prices at renewal, not mid-term.

---

## Future pricing moves (post-launch, in priority order)

1. **Month 3:** Add Startup/Builder plan between Pro and Team at $79/mo flat for up to 3 seats. Captures the 2-CM shop that's too big for Pro, too small for Team.
2. **Month 6:** Introduce an "Office" add-on for Pro/Team ($19/mo) — admin view, bulk operations, weekly rollup report. Unbundles the admin-oriented features for builders who only have 1–2 CMs but an office person.
3. **Month 9:** SSO as an Enterprise-only feature (still no SAML on Team).
4. **Month 12:** Evaluate whether Team's per-seat model is still correct vs per-home or per-active-project model. Per-home aligns with builder P&L — CFOs understand it — but per-seat is simpler to operate in year one.

---

## Metrics that matter

- **Time-to-first-walkthrough** (signup → first project with ≥ 5 items). Under 48 hours = healthy. Over 7 days = the onboarding is broken.
- **Week-2 retention.** If week 1 retention is 90%+ (which it will be during founding) but week 2 drops to 40%, it's an onboarding problem not a product problem.
- **Closeout time saved** (self-reported via email #3 in the welcome sequence). Real benchmark, not a vanity metric.
- **Team expansion rate** (Pro users who invite a coworker, even if that coworker doesn't upgrade). Signal of internal product love.

---

## What nobody asks about yet but will

- **White-label / builder-branded instance.** Will come up from production builders in month 6. Price at $500/mo add-on per builder, on top of per-seat pricing. Don't do it for < 10 seats.
- **API access.** Will come up from PM-software companies wanting to integrate. Pause — do not ship an API until Enterprise customers request it specifically. APIs compound support cost.
- **Mobile app vs PWA.** A native app is an option, not a goal. PWA serves the field use case well. Revisit only if PWA push notifications remain unreliable on iOS.

---

## Reminders to future Paige

- Do not discount the first contract Paige signs with a builder. Price is a story. Discounts rewrite the story.
- When a CM says "I'd pay $100/mo for this" — raise your price, don't pocket the data point.
- Enterprise deals that need legal review before month 9 are a trap. Decline politely. Revisit when SSO + SLA infrastructure exists.
- This doc is a living doc. Every quarter, re-read it. Cross out what stopped being true. Don't preserve opinions that stopped serving the business.

---

**Last reviewed:** 2026-04-20
**Next review:** 2026-07-20
