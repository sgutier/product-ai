# Discovery Learning Plan — Roll Out Subscription to 10 Markets

**Initiative:** Roll Out Subscription to 10 Markets  
**Owner:** Sergio Barguilla  
**Related artifact(s):**  
- Birth Certificate (`birth-certificate.md`)  
- Discovery Review (`discovery-review.md`)  
- Subscription Feature Tiers (`research/Monetization/Subs_definition.pdf`)

**Discovery window:** 3–4 weeks (early Q2 2026, triggered by Q1 test results availability)  
**Last updated:** 2026-02-02

---

## 1. Discovery Objectives

> What must we learn before moving to PRD?

- **LO-1:** Whether the Q1 A/B test confirms lightweight freemium as the winning model (and at what conversion rate)
- **LO-2:** Whether 3.5% conversion holds per market — particularly in lower-PPP markets (UA, RO, HU, CZ) — or whether the rate varies significantly by geography
- **LO-3:** Whether €69.99/year uniform pricing is viable across all 10 markets, or whether purchasing power differences require price tiering
- **LO-4:** Whether independent drivers (owner-operators / standalone users) are willing to pay personally for premium navigation features, given contradictory research signals
- **LO-5:** Whether the defined premium features (offline maps, voice instructions, lane guidance, full traffic, 7 vehicle profiles with ADR/tunnel parameters — per `Subs_definition.pdf`) are perceived as worth €69.99/year by the target persona, and which features drive conversion
- **LO-6:** Whether the B2B funnel assumptions have any empirical basis, and whether €111K should remain in or be removed from the core business case
- **LO-7:** Whether simultaneous 10-market deployment is operationally feasible within Q2 (engineering capacity, legal clearance, support readiness)

---

## 2. Assumptions Being Tested

| Assumption | Risk Area | Why It Matters |
|----------|-----------|----------------|
| Q1 test confirms lightweight freemium with ≥3.5% conversion | Value | Entire initiative depends on this. If hard paywall wins or results are inconclusive, the initiative has no foundation. |
| 3.5% conversion rate applies uniformly across 10 markets | Value | Revenue model extrapolates a single rate to 219K users. If lower-PPP markets convert at <1%, projected revenue drops 40–60%. |
| €69.99/year works at uniform price across all markets | Value | PPP difference between UA (~$4,500 GDP/cap) and DE (~$51,000) is ~11x. Price that works in DE may be prohibitive in UA. |
| Independent drivers will pay personally for premium navigation | Value | Research signals "preference for company-provided tools" and "financially cautious." The target persona may be the least likely to convert. |
| Premium features are perceived as worth €69.99/year by independent drivers | Value | Feature set is now defined (`Subs_definition.pdf`): offline maps, voice instructions, lane guidance, full traffic, 7 vehicle profiles with ADR parameters. Objectively strong. Remaining risk: perceived value by price-sensitive owner-operators may not match objective feature quality — especially if they haven't experienced these features before. |
| B2B funnel (30% → 50% → 10% → 30% → 40%) produces €111K | Viability | 5-step funnel with zero production validation. B2B outreach is explicitly not in scope. 29% of business case depends on unbuilt pipeline. |
| Q1 paywall UX works across 10 languages and payment cultures | Usability | Test may have covered limited markets. Localisation and payment norms vary significantly. |
| 10-market simultaneous launch is feasible in one quarter | Feasibility | Build cost is [[TBD]]. Legal effort for 10 markets (especially UA) is unconfirmed. No phased fallback. |

---

## 3. Planned Discovery Activities

### Activity 1 — Q1 A/B Test Results Analysis

- **Learning objective(s):** LO-1, LO-2, LO-4
- **Risk area:** Value
- **Method:** Data analysis
- **Description:** Analyse final Q1 A/B test results. Extract: (a) overall conversion rate for lightweight freemium vs hard paywall, (b) per-market conversion if test covered multiple markets, (c) conversion by user segment (owner-operator vs company driver vs standalone), (d) D30 and D60 retention curves for free users, (e) subscriber churn/cancellation within test period. Compare actual results against the 3.5% model assumption. Determine whether the test population matches the 10-market rollout population in profile.
- **Participants / data source:** Q1 test analytics dashboard; DATA team
- **Owner:** Sergio Barguilla
- **Estimated effort:** 3–5 days (once data is available)
- **Dependencies:** Q1 test must have concluded with sufficient sample size

**Key questions to answer:**
- What is the actual conversion rate? Per market? Per user segment?
- Does the test population include lower-PPP markets (UA, RO, HU, CZ)?
- Is there a statistically significant difference between markets?
- What does the D30→D60 retention curve look like for free users?

---

### Activity 2 — Price Sensitivity & PPP Analysis

- **Learning objective(s):** LO-3
- **Risk area:** Value
- **Method:** Data analysis + desk research
- **Description:** Analyse whether uniform €69.99 pricing is realistic across all 10 markets. Compare: (a) €69.99 as % of average monthly income per market, (b) competitor pricing for navigation/utility apps per market, (c) Play Store subscription benchmarks per market, (d) Q1 test conversion broken down by market (if available). Model revenue impact of 2–3 price tiering scenarios (e.g., €69.99 for Western EU, €39.99 or €49.99 for Eastern EU) vs uniform pricing.
- **Participants / data source:** Public PPP/income data; Play Store pricing benchmarks; impact model xlsx; Q1 per-market data
- **Owner:** Sergio Barguilla + Raffaele Gricinella (Marketing)
- **Estimated effort:** 3–4 days
- **Dependencies:** None (can run in parallel with Activity 1)

---

### Activity 3 — Premium Feature Perceived Value Validation

- **Learning objective(s):** LO-5, LO-4
- **Risk area:** Value
- **Method:** Data analysis (Q1 feature usage) + research cross-reference
- **Description:** The premium feature set is now defined (`research/Monetization/Subs_definition.pdf`). Premium tier includes: offline maps (hybrid + downloadable European maps), full live traffic (layer, notifications, route progress coloring, delays in route planner), dynamic lane guidance, voice instructions, 7 vehicle profiles with full parameters (ADR, tunnel codes, emission, hazardous load), and driving restriction notifications. Freemium retains core online navigation but loses voice, lane guidance, offline maps, full traffic, and advanced vehicle parameters. This activity validates *perceived value*, not feature definition. Specifically: (a) extract Q1 test feature-level usage analytics — which premium features do subscribers actually use most? (b) cross-reference the premium tier against driver research pain points: offline maps addresses "navigation anxiety" and connectivity concerns; ADR/tunnel parameters address "avoid restrictions" job; voice instructions and lane guidance are safety-critical during navigation; full traffic addresses time-pressure pain points. (c) Identify whether any premium features are irrelevant to the independent driver persona (e.g., ADR parameters only matter to hazmat carriers). Output: a 1-page premium feature value map ranking features by relevance to target persona and actual usage data.
- **Participants / data source:** Q1 test feature analytics; driver research (`research/master-summary.md`); `Subs_definition.pdf`
- **Owner:** Sergio Barguilla
- **Estimated effort:** 2 days
- **Dependencies:** Access to Q1 test feature usage data

---

### Activity 4 — B2B Revenue Assumption Stress Test

- **Learning objective(s):** LO-6
- **Risk area:** Viability
- **Method:** Data analysis + stakeholder review
- **Description:** Challenge each step of the B2B funnel model (30% eligible → 50% exposed → 10% engaged → 30% registered → 40% activated → €417 ACV). For each step: (a) is there any historical data or proxy metric, (b) what is the realistic range, (c) what infrastructure exists to execute the step. Determine whether B2B revenue should remain in the core business case, be separated as "upside potential," or be removed entirely. Output: a recommendation on how to present B2B revenue in the updated birth certificate.
- **Participants / data source:** CRM/B2B team (if exists); EW Office commercial data; impact model xlsx
- **Owner:** Sergio Barguilla + Commercial lead [[TBD]]
- **Estimated effort:** 2–3 days
- **Dependencies:** Access to CRM / B2B pipeline data (if any exists)

---

### Activity 5 — Operational Feasibility Assessment (10-Market Simultaneous Launch)

- **Learning objective(s):** LO-7
- **Risk area:** Feasibility
- **Method:** Stakeholder interviews / capacity check
- **Description:** Confirm with each dependency team whether simultaneous 10-market launch in Q2 is realistic. Specifically: (a) MOBILE APP (Michal): estimated MDs for store configuration, localisation, paywall deployment across iOS + Android × 10 markets; (b) LEGAL (Jennifer): estimated effort for T&C review, VAT compliance, and store policy clearance across all 10 markets — with specific flag on UA regulatory complexity; (c) FINANCE: revenue recognition and payment reconciliation readiness. Determine whether phased rollout (e.g., top 5 markets first, remaining 5 two weeks later) is a better operational strategy.
- **Participants / data source:** Michal (MOBILE APP), Jennifer (LEGAL), Finance lead [[TBD]]
- **Owner:** Sergio Barguilla
- **Estimated effort:** 3–5 days (interview scheduling + synthesis)
- **Dependencies:** Availability of Michal, Jennifer, Finance lead

---

## 4. Success & Failure Signals

| Learning Objective | Success Signal | Failure Signal |
|-------------------|----------------|----------------|
| LO-1: Q1 test confirms lightweight freemium | Lightweight freemium wins with ≥3% conversion and statistical significance; D30 retention ≥65% | Hard paywall wins, results are inconclusive, or conversion is <2% |
| LO-2: Per-market conversion holds | Conversion ≥2.5% in ≥8 of 10 markets; no market below 1.5% | 3+ markets convert below 1.5%; average conversion <2.5% |
| LO-3: Uniform pricing viable | Q1 data shows no statistically significant conversion difference by market PPP tier | Lower-PPP markets (UA, RO, HU) convert at <50% of the rate of higher-PPP markets (DE, FR, GB) |
| LO-4: Independent drivers willing to pay | ≥3% conversion among owner-operators / standalone users specifically | Conversion among independent drivers is <2%, or heavily skewed toward company-linked users |
| LO-5: Premium features perceived as worth €69.99 | ≥3 premium features (offline maps, voice, lane guidance, traffic, ADR) show high usage among Q1 subscribers AND map to researched driver pain points | Q1 subscribers rarely use premium-exclusive features; usage concentrated on features also available in freemium |
| LO-6: B2B funnel has empirical basis | ≥2 of 5 funnel steps have historical proxy data; funnel survives 50% pessimistic adjustment | No historical data for any funnel step; pessimistic scenario drops B2B below €30K |
| LO-7: 10-market simultaneous launch feasible | All three teams confirm capacity; total effort ≤ available Q2 bandwidth; legal clearance timeline ≤6 weeks | Any team flags capacity conflict; legal clearance for UA or HU estimated at >8 weeks; total MDs exceed available bandwidth |

---

## 5. Metrics & Evidence to Capture

- **Metrics to observe:**
  - Q1 test conversion rate (overall + per market + per user segment)
  - D30, D60 free-user retention curves
  - Subscriber cancellation rate within test period
  - Feature usage among subscribers vs free users
  - €69.99 as % of average monthly income per market

- **Qualitative signals:**
  - App Store review sentiment related to paywall / subscription
  - Q1 test user feedback (if captured)
  - Stakeholder confidence levels on capacity (from Activity 5)

- **Artifacts to produce:**
  - Q1 test results summary (per market, per segment)
  - Price sensitivity analysis (PPP-adjusted scenarios)
  - Premium feature value map (feature × pain point × Q1 usage data)
  - B2B funnel stress test memo (recommendation on inclusion in business case)
  - Operational feasibility memo (capacity confirmation or phased rollout recommendation)
  - Updated birth certificate (revised revenue projections, resolved assumptions)

---

## 6. Risks & Mitigations (Discovery Phase)

| Risk | Impact on Discovery | Mitigation |
|----|---------------------|------------|
| Q1 test results delayed beyond early Q2 | Blocks Activity 1, delays all downstream decisions | Set hard deadline: if results not available by Week 3 of Q2, escalate. In parallel, run Activities 2, 4, 5 which don't depend on test data. |
| Q1 test did not cover lower-PPP markets | Cannot validate per-market conversion for UA, RO, HU, CZ | Use PPP analysis (Activity 2) as proxy. Recommend phased rollout starting with tested markets, adding untested markets 4 weeks later with monitoring. |
| No CRM / B2B pipeline data exists | Cannot validate any B2B funnel step | Recommend removing B2B revenue from core business case. Track as separate upside metric. Reduces projected value to ~€267K (subscription only). |
| Key stakeholders unavailable for Activity 5 | Cannot confirm operational feasibility | Provide written assessment template; allow async response within 5 business days. Escalate if no response. |
| Q1 test did not capture per-feature usage analytics | Cannot determine which premium features drive conversion vs which are ignored | Use driver research pain points as proxy for feature value ranking. Recommend adding per-feature analytics to rollout dashboards as a post-launch requirement. |

---

## 7. Decision Criteria

> What decision will this discovery enable?

At the end of discovery, we expect to decide:

- [ ] **Proceed to PRD as planned** — Q1 test confirms ≥3% conversion, per-market data is acceptable, pricing is viable, feature set is defined, teams have capacity
- [ ] **Narrow or change scope** — e.g., launch in top 5–6 markets only; introduce price tiering; separate B2B from business case
- [ ] **Iterate discovery** — Q1 data is inconclusive; need extended test or additional markets
- [ ] **Park or kill the initiative** — Q1 test fails; persona willingness to pay disproven; no viable feature set

**Decision owner:** Sergio Barguilla

---

## 8. Outputs & Where They Will Live

- Discovery summary: `initiatives/2026-Q2/roll-out-subscription-10-markets/discovery-summary.md`
- Evidence links (dashboards, analysis): [[to be added during discovery]]
- Updates to Birth Certificate:
  - Impact section: revised with actual Q1 conversion data (replace 3.5% assumption)
  - Impact section: B2B revenue reclassified or removed based on Activity 4
  - Constraints section: pricing strategy updated (uniform vs tiered)
  - General Description: premium feature set referenced (`Subs_definition.pdf`), value rationale added
  - Dependencies: MD estimates and capacity confirmed

---

## 9. Next Step After Discovery

Select **one**:

- [ ] Create PRD
- [ ] Run additional discovery
- [ ] Escalate decision
- [ ] Park / kill initiative

_To be determined after discovery activities are completed._
