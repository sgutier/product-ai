# Initiative Birth Certificate

**Initiative:** Roll Out Subscription to 10 Markets  
**Start quarter:** 2026 Q2  
**Planning horizon:** Q2 2026 (single-quarter execution)  
**Owner:** Sergio Barguilla  
**Status:** Draft  
**Last updated:** 2026-02-02

---

## General Description

**One-liner:** Roll out the lightweight freemium subscription model to 10 European markets after validating conversion in Q1 A/B tests.

**Target customers / users:** Independent drivers (owner-operators and standalone users of EW Navigation App, not linked to EW Office)

**Customer problem / opportunity:**  
EW Navigation has a large active user base (~220K across 10 target markets) generating near-zero direct revenue. Q1 2026 tested two monetization models — lightweight freemium and hard paywall. With test results confirming the lightweight freemium path, this initiative scales the subscription to all 10 markets simultaneously to capture revenue from willing-to-pay drivers while preserving the free user base for B2B lead generation.

**Proposed outcome:**  
Independent drivers in 10 markets can subscribe to EW Navigation premium features at €69.99/year via Play Store. Free users retain access to core navigation with a soft upsell to premium. The large retained free-user base (70% D30 retention) continues to serve as a B2B pipeline for EW Office.

**Business relevance:**  
Pure growth monetization activity. Directly addresses the strategic theme of transitioning from freemium to selective monetization. Year 1 model projects €378.6K total annual value (€267.2K subscription + €111.5K B2B). Delay means continued zero direct monetization from ~220K active users.

**Constraints / assumptions:**  
- Assumes lightweight freemium is the chosen model based on Q1 test results
- Subscription price: €69.99/year (uniform across markets)
- Conversion rate: 3.5% (from Q1 test baseline — may be updated with final test data)
- App Store/Play Store fee: 30%
- VAT rates vary by market (19%–27%)
- All 10 markets go live simultaneously in Q2 2026
- No phased rollout — single deployment wave

---

## Hypothesis

If we deploy the **lightweight freemium subscription model at €69.99/year**  
For **independent drivers across 10 European markets (PL, FR, GB, DE, IT, UA, ES, CZ, RO, HU)**  
We expect **3.5% of active users to convert to paid subscribers while retaining 70% of free users at D30**  
Which will move **Conversion Rate and ARPU** by **generating ~€267K net subscription revenue and ~€111K in B2B pipeline revenue in Year 1**  
By **end of Q3 2026 (first full quarter post-launch)**  
Because **Q1 A/B testing validated that lightweight freemium preserves the free-user base (70% D30 retention vs 5% for hard paywall) while achieving comparable subscription conversion (3.5%), and the retained free users generate 14x more B2B value than the hard paywall alternative**.

_Open question(s) / assumptions to validate:_  
- Final Q1 test conversion rate may differ from the 3.5% model assumption
- B2B funnel assumptions (30% eligible, 10% engagement, 40% activation) are model estimates — not yet validated in production
- Price sensitivity may vary across markets — uniform €69.99 pricing is an assumption

---

## Main Metrics / Key Results

**Primary metric (north star for this initiative):**  
Subscription Conversion Rate — % of active users converting to paid subscription within 15 days of exposure

**Baseline:** 3.5% (Q1 test data)  
**Target:** ≥3.5% sustained across all 10 markets by end of Q3 2026

**Secondary metric:**  
ARPU — Average revenue per active user across the 10 markets

**Guardrail metrics (must not degrade):**  
- CFR ≥ pre-launch baseline
- ANR ≤ pre-launch baseline
- App Store Rating ≥ pre-launch baseline
- D30 Free User Retention ≥ 70% (lightweight freemium benchmark)

**Post-runtime learning statement (to be completed after launch):**

After a runtime of **[[X weeks]]**, we saw **Conversion Rate** **[[increase/decrease]]** **[[significantly/not significantly]]**.  
This **[[validates / fails to validate]]** our hypothesis that the lightweight freemium model will sustain 3.5% conversion at scale.  
We also observed **D30 free-user retention** go **[[up/down]]** and **App Store Rating** **[[stable/changed]]**.

---

## 💰 Impact

> Revenue figures derived from `research/monetization/EW_Navigation_Monetization_Impact_Model_2026.xlsx` — Lightweight Freemium sheet.

**Revenue impact (Year 1 — from impact model):**

| Market | Active Users | Subscribers (3.5%) | Gross Revenue (€) | Net Subscription Revenue (€) | B2B Revenue (€) | Total Value (€) |
|--------|-------------|--------------------|--------------------|------------------------------|------------------|-----------------|
| PL | 44,869 | 1,570 | 109,913 | 52,962 | 22,750 | 75,712 |
| FR | 39,623 | 1,387 | 97,062 | 48,808 | 20,090 | 68,898 |
| GB | 31,541 | 1,104 | 77,264 | 38,852 | 15,992 | 54,844 |
| DE | 26,636 | 932 | 65,249 | 33,267 | 13,505 | 46,772 |
| IT | 18,105 | 634 | 44,351 | 21,681 | 9,180 | 30,861 |
| ES | 17,621 | 617 | 43,165 | 21,403 | 8,934 | 30,338 |
| UA | 12,835 | 449 | 31,441 | 15,810 | 6,508 | 22,318 |
| CZ | 10,883 | 381 | 26,660 | 13,219 | 5,518 | 18,737 |
| RO | 10,794 | 378 | 26,442 | 13,481 | 5,473 | 18,954 |
| HU | 6,912 | 242 | 16,932 | 7,685 | 3,505 | 11,189 |
| **Total** | **219,819** | **7,694** | **538,479** | **267,168** | **111,455** | **378,623** |

**Revenue summary:**
- **Year 1:** ~€378,600 total annual value (€267K net subscription + €112K B2B pipeline)
- **Year 2:** [[TBD — dependent on renewal rates, user growth, and conversion optimization]]
- **Year 3:** [[TBD — dependent on market expansion beyond 10 markets]]

**Key assumptions (from impact model):**
- Subscription price: €69.99/year (uniform)
- Conversion rate: 3.5% at D15
- App Store fee: 30%
- VAT: 19%–27% by market
- TTM (translation/transaction/marketing) cost: varies per market (€967–€6,282)
- D30 free-user retention: 70% (lightweight freemium)
- Monthly free-user retention: 95%
- Avg free-user lifetime: ~20 months
- B2B funnel: 30% eligible → 50% exposed → 10% engaged → 30% registered → 40% activated
- Avg annual value per B2B customer: €417
- B2B revenue / subscription revenue ratio: ~41.7%

**Cost & investment (high level):**
- Build cost (CapEx / MDs): [[TBD — dependent on Mobile App and backend estimates]]
- Run cost (OpEx): TTM costs ~€30,856/year across all markets (from model)
- Opportunity cost: [[TBD]]

---

## General Scope

**Customer-visible outcomes by end of initiative:**
- Subscription paywall and premium upgrade flow visible in all 10 markets
- Premium navigation features accessible after subscription purchase
- Clear, transparent upgrade path within the app with soft upsell (no hard blocking)

**Key deliverables:**
- Lightweight freemium paywall UI deployed to 10 markets
- Play Store / App Store subscription product configured per market
- Payment processing and entitlement management live
- Market-specific localisation and pricing compliance

**Definition of Done (high level):**  
Subscription is live, purchasable, and functional in all 10 markets (PL, FR, GB, DE, IT, UA, ES, CZ, RO, HU) with payment processing working, entitlements granted correctly, and conversion tracking reporting to dashboards.

---

## 🗓️ Phased Scope & Milestones

### Phase 1 — Simultaneous Rollout to 10 Markets (Q2 2026)
**Intended outcome(s):**
- Subscription live in all 10 markets: PL, FR, GB, DE, IT, UA, ES, CZ, RO, HU
- Conversion rate tracking active per market
- Free-user retention monitoring active

**Key deliverables / milestones:**
- Store product configuration for all 10 markets
- Lightweight freemium paywall deployed (iOS + Android)
- Entitlement backend and payment reconciliation operational
- Market-specific legal/T&C compliance cleared
- Dashboards: conversion rate, ARPU, retention, B2B funnel tracking

---

### Phase 2 — N/A

---

### Phase 3 — N/A

---

## 🔗 Dependencies

**Team codes used:** MOBILE APP, LEGAL, FINANCE

### Phase 1

- **MOBILE APP** — [[TBD]] MDs — Paywall UI implementation, subscription purchase flow, entitlement gating, market-specific configuration — Owner: **Michal**
- **LEGAL** — [[TBD]] MDs — Market-specific Terms & Conditions, App Store / Play Store compliance review for all 10 markets, VAT compliance — Owner: **Jennifer**
- **FINANCE** — [[TBD]] MDs — Revenue recognition setup, payment reconciliation, reporting per market — Owner: [[TBD]]

_Open question: Are there additional dependencies on API MNG (entitlements backend), DATA (analytics/dashboards), or CRM (B2B outreach pipeline)?_

---

## Not in Scope

- Hard paywall model (tested in Q1 but not selected for rollout)
- Markets beyond the 10 listed above
- B2C price differentiation by market (uniform €69.99 for now)
- B2B outreach automation (modeled as revenue potential, not a deliverable of this initiative)
- Subscription management UI (cancellation, plan changes) beyond platform defaults
- Android tablet / FMS-specific subscription flows

---

## Why Now?

**Trigger / context:**  
Q1 2026 A/B tests (lightweight freemium vs hard paywall) will conclude in early Q2 with sufficient data to select the winning model. The lightweight freemium model is the assumed choice — it matches the 3.5% conversion target while retaining 70% of free users at D30 (vs 5% for hard paywall), preserving the B2B pipeline worth €111K/year.

**Cost of delay:**  
Every quarter without monetization activation means ~€95K in forgone net subscription revenue (quarterly run-rate) and continued zero direct revenue from ~220K active users. Competitor navigation apps with premium tiers are already monetizing.

**Strategic alignment:**  
- Directly supports OKR: "Increase value captured from EW Navigation users" (KRs: conversion to paid, Navigation-attributed revenue)
- Aligns with strategic theme: "Transition from pure freemium to selective monetization"
- Preserves the free-user base as a B2B growth channel for EW Office (strategic role #3: Monetization surface)

---

## 📎 Documentation Links

### Product Risks

| Risk Area | Evidence / Link | Notes / Mitigation |
|---------|----------------|--------------------|
| **Value** | Q1 A/B test data (lightweight freemium vs hard paywall) — results expected early Q2 | Some evidence. Q1 test validated 3.5% conversion and 70% D30 retention. Final results may adjust assumptions. Mitigation: monitor conversion per market in first 2 weeks post-launch; per-market kill switch if conversion drops below 2%. |
| **Usability** | Q1 lightweight freemium paywall UX tested in-app | Some evidence. Paywall UI was tested as part of Q1 experiment. Mitigation: monitor App Store rating and user feedback post-rollout; iterate on paywall copy/design if rating drops >0.1 stars. |
| **Feasibility** | Q1 infrastructure validated subscription flow end-to-end | Known evidence. Tech stack for subscription purchase, entitlement, and payment processing was built and tested in Q1. Scaling to 10 markets requires store configuration and localisation, not new infrastructure. |
| **Viability** | App Store / Play Store subscription policies reviewed for Q1 launch | Some evidence. Store policies were cleared for Q1 test markets. Mitigation: Legal review (Jennifer) must confirm compliance for all 10 markets before go-live, particularly VAT handling in UA and HU. |

---

## Discovery Artifacts

| Artifact | Evidence / Link |
|--------|-----------------|
| Impact Model (xlsx) | `research/monetization/EW_Navigation_Monetization_Impact_Model_2026.xlsx` |
| Q1 A/B Test Design | [[TBD — link to test plan]] |
| Q1 A/B Test Results | [[TBD — available early Q2]] |
| Lean Product Canvas | [[TBD]] |
| Customer Journey (as-is / to-be) | [[TBD]] |

---

## 👥 Stakeholders

**Marketing lead:** Raffaele Gricinella  
**Operations lead:** [[TBD]]  
**Commercial lead:** [[TBD]]  
**Finance:** [[TBD]]
