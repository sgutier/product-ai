# Discovery Review — Roll Out Subscription to 10 Markets

## 1. Key Assumptions Identified

### Value
- Q1 A/B test conversion rate (3.5%) will hold uniformly across all 10 markets, despite the test likely covering only a subset of markets
- Uniform €69.99/year pricing works across markets with vastly different purchasing power (UA, RO, HU vs DE, FR, GB — PPP differences are enormous)
- Independent drivers (owner-operators and standalone users) are willing to pay personally for premium navigation features — driver research explicitly lists "willingness to pay for premium features" as an **open question** and signals "preference for company-provided tools over personal purchases"
- The premium features behind the paywall are sufficiently compelling to justify €69.99/year — the feature set is now documented (`research/Monetization/Subs_definition.pdf`) and includes: **offline maps** (hybrid mode + downloadable European maps), **full live traffic** (layer, notifications, route progress coloring), **dynamic lane guidance**, **voice instructions**, **7 vehicle profiles** with full parameters (ADR, tunnel codes, emission, hazardous load), and **driving restriction notifications**. This is a strong tier with clear differentiation from freemium. The remaining assumption is whether the target persona *perceives* this value as worth €69.99/year
- Retained free users (70% at D30) will generate meaningful B2B pipeline value despite being independent drivers not linked to EW Office

### Usability
- The Q1 paywall UX will function effectively across 10 markets with different languages, payment norms, and cultural expectations around upselling
- The soft upsell approach will not degrade the free experience enough to push retention below 70% D30 at scale (test environment ≠ production across 10 markets)
- Play Store / App Store subscription flows are sufficiently intuitive for independent truck drivers across all markets without additional UX support

### Feasibility
- Q1 subscription infrastructure scales to 10 simultaneous markets without significant rework
- Store product configuration, localisation, legal compliance, and entitlement management can all be completed for 10 markets within a single quarter (Q2 2026)
- No phased rollout is feasible — all 10 markets can go live simultaneously without overwhelming support, monitoring, or incident response capacity
- Build cost is [[TBD]] — the initiative is scoped without knowing whether engineering capacity exists

### Viability
- App Store / Play Store policies are consistent and compliant across all 10 markets (including UA, which has unique regulatory and sanctions-related complexity)
- VAT handling (19%–27% by market) can be implemented correctly and does not create revenue recognition issues
- B2B funnel conversion assumptions (30% eligible → 50% exposed → 10% engaged → 30% registered → 40% activated) are realistic — none of these rates are validated in production
- €417 average annual value per B2B customer is achievable and stable
- €111K B2B revenue (29% of total projected value) is real revenue, not just modeled potential

---

## 2. Hypothesis Stress Test

**What works in the logic**
- The strategic rationale is sound: lightweight freemium preserves the free-user base (70% D30 vs 5% for hard paywall) while capturing revenue from willing-to-pay users. This is the right model choice if the test confirms it.
- The A/B test methodology (lightweight freemium vs hard paywall) provides a legitimate evidence framework — the initiative is at least grounded in experimentation, not pure assumption.
- The revenue model is unusually detailed and transparent: per-market breakdowns with explicit VAT, store fees, and TTM costs allow the business case to be challenged precisely.
- Guardrail metrics (CFR, ANR, App Store Rating, D30 retention) are well-defined and appropriate.

**What is weak or unproven**
- **The Q1 test results do not yet exist.** The birth certificate was written 2026-02-02. Test results are "expected early Q2." The entire initiative, including the revenue model, market-by-market projections, and the €378K business case, is built on data that has not been collected yet. This initiative is planning execution before validation.
- **3.5% conversion is extrapolated, not validated, at 10-market scale.** The Q1 test was run in an unspecified number of markets. Applying a single conversion rate across PL, FR, GB, DE, IT, UA, ES, CZ, RO, and HU ignores purchasing power parity, payment method preferences, and competitive landscape differences. €69.99 in Ukraine is a fundamentally different proposition than €69.99 in Germany.
- **The target persona contradicts the research evidence.** The initiative targets "independent drivers (owner-operators and standalone users)" for personal B2C subscription purchases. But driver research signals: "Preference for company-provided tools over personal purchases" and "Willingness to use premium features if provided by company." Owner research signals: "Financially cautious — monitors prices, limits, transactions" and "Tool-conservative — wants simple, reliable tools with minimal time investment." The persona most targeted is the one least likely to pay out of pocket. This is a critical tension the birth certificate does not address.
- **Premium feature set is now documented but perceived value is untested.** The subscription feature tiers are defined in `research/Monetization/Subs_definition.pdf`. Premium includes: offline maps (hybrid + downloadable), full live traffic (layer, notifications, route progress), dynamic lane guidance, voice instructions, 7 vehicle profiles with full ADR/tunnel/emission parameters, and driving restriction notifications. Freemium retains core navigation but loses voice instructions, lane guidance, offline maps, full traffic, and advanced vehicle parameters. This is a genuinely strong differentiation — offline maps and voice instructions are high-value for professional drivers. However, the Q1 test must confirm that this feature set drives the claimed 3.5% conversion. The remaining risk is whether independent, price-sensitive drivers perceive enough value to pay €69.99/year for features they previously had for free (if migrating from legacy Sygic Truck) or never experienced (if new users).
- **B2B revenue is not revenue — it is a model.** €111K (29% of projected total value) comes from a 5-step funnel (30% × 50% × 10% × 30% × 40%) applied to retained free users. None of these rates are validated. The B2B pipeline infrastructure is explicitly "not a deliverable of this initiative" (per Not in Scope). This means 29% of the business case depends on a pipeline that this initiative does not build and has never been measured.
- **D30 retention is an insufficient signal for annual subscription viability.** 70% D30 retention says nothing about D90, D180, or D365 retention. An annual subscription at €69.99 requires users to find enough value to renew after 12 months. No renewal rate assumption exists. If retention curves decay steeply after D30, the Year 1 revenue holds but Year 2+ collapses.

**Hidden dependencies**
- **Q1 test must confirm lightweight freemium.** If the hard paywall wins, or if results are inconclusive, this initiative has no foundation. The birth certificate treats lightweight freemium as the chosen model, but it is still an assumption.
- **Premium features must be perceived as compelling by the target persona.** The feature set is now documented and objectively strong (offline maps, voice instructions, lane guidance, full traffic, ADR parameters). However, perceived value depends on the user's context: an owner-operator doing long-haul with ADR cargo values tunnel codes and offline maps highly; a local driver doing short routes may not. Q1 test must show which premium features drive conversion.
- **B2B pipeline infrastructure must exist to capture the €111K.** The initiative models B2B revenue but explicitly excludes B2B outreach automation from scope. If no pipeline exists to convert free users to B2B leads, 29% of the business case is notional.
- **Per-market legal and compliance clearance must happen for all 10 markets within Q2.** Legal owner is named (Jennifer) but effort is [[TBD]]. Simultaneous 10-market legal clearance in one quarter is operationally ambitious, especially for UA (sanctions/regulatory complexity) and newer EU markets.
- **Engineering capacity is unknown.** Build cost is [[TBD]] across all dependencies. The initiative is scoped as a single-quarter execution with no phased rollout, but there is no confirmation that Mobile App, Legal, and Finance teams have capacity.

---

## 3. Top Risks (Ranked)

1. **Cross-market conversion rate collapse**
   - Why it matters: The entire revenue model (€267K net subscription) assumes 3.5% conversion applied uniformly to 219,819 users across 10 markets. If the Q1 test was run in 2–3 markets, extrapolating to 10 markets with vastly different purchasing power (UA GDP per capita is ~$4,500 vs DE ~$51,000) is a 10x assumption stretch. Conversion in lower-PPP markets could be dramatically lower at €69.99 uniform pricing.
   - What would invalidate it: If average conversion across 10 markets falls below ~2%, net subscription revenue drops below €150K and the initiative's ROI may not justify the build + legal + operational investment. If markets like UA, RO, HU convert at <1%, they generate near-zero revenue while consuming the same legal/compliance effort.
   - Consequence if ignored: Revenue projections will be missed. The narrative of "€378K total value" will be used to justify priority and resource allocation, but actual returns could be 40–60% lower. Worse, a failed launch in price-sensitive markets damages trust and rating without meaningful revenue.

2. **Independent driver willingness to pay is unvalidated and contradicted by research**
   - Why it matters: The target persona — independent, owner-operator drivers — is described in research as "financially cautious," "price-sensitive," with "preference for company-provided tools over personal purchases." The driver research explicitly lists "willingness to pay for premium navigation features" as an open question. The birth certificate does not address this tension. A 3.5% conversion rate is meaningless if the test population does not match the 10-market rollout population in willingness-to-pay profile.
   - What would invalidate it: If the Q1 test audience skewed toward a different profile (e.g., higher-PPP markets, company-provided devices, or users already embedded in EW ecosystem), the 3.5% baseline may not transfer to independent drivers in markets like UA, RO, CZ, or HU.
   - Consequence if ignored: The initiative launches with confidence anchored in test data that may not represent the rollout population. Low conversion in most markets would make the subscription feel like a failed product, not a scaling success.

3. **B2B pipeline revenue (€111K) has zero production evidence**
   - Why it matters: Nearly 30% of the initiative's projected value comes from a modeled B2B funnel that has never been measured in production. The funnel has 5 sequential conversion steps, each an assumption. The initiative explicitly excludes B2B outreach automation from scope — so no mechanism will be built to actually capture this value.
   - What would invalidate it: If any step in the funnel (30% eligible → 50% exposed → 10% engaged → 30% registered → 40% activated) is off by even 50%, the €111K drops to ~€28K–€55K. If no B2B pipeline infrastructure exists, the revenue is purely notional.
   - Consequence if ignored: Stakeholders plan against a €378K business case. If the real number is closer to €267K (subscription only) or lower, the initiative's strategic weight is overstated. Resource allocation and opportunity cost decisions are made on inflated projections.

---

## 4. Discovery Gaps by Risk Area

| Risk Area | Current Confidence | What Is Missing |
|----------|-------------------|-----------------|
| Value | Low–Medium | Q1 test results do not yet exist. Conversion rate is projected, not measured. No per-market conversion data. Uniform pricing not tested against PPP differences. Premium feature set is now defined and strong (offline maps, voice, lane guidance, full traffic, ADR parameters — see `Subs_definition.pdf`), which upgrades confidence from Low to Low–Medium. Remaining gap: target persona's willingness to pay contradicts research signals, and perceived value at €69.99 is untested across all 10 markets. |
| Usability | Medium | Q1 paywall UX was tested but likely in limited markets. No evidence that UX performs well across 10 languages, payment cultures, and Play Store norms. No data on how subscription flow performs on diverse Android devices common in lower-PPP markets. |
| Feasibility | Medium–High | Q1 infrastructure was validated end-to-end. Scaling to 10 markets is primarily configuration, not new architecture. However: simultaneous 10-market deployment with no phased rollout is operationally risky. Build cost is entirely [[TBD]]. Engineering capacity is unconfirmed. |
| Viability | Low | B2B funnel is 100% modeled with zero production validation. Legal compliance for 10 markets (especially UA) is not confirmed. VAT implementation for all markets is not verified. Revenue model overstates total value by including non-deliverable B2B pipeline as revenue. |

---

## 5. Recommended Learning Objectives

- We need to learn whether the Q1 A/B test confirms lightweight freemium as the winning model before committing to 10-market rollout planning
- We need to validate that 3.5% conversion holds (or what the actual rate is) per market, not just in aggregate — particularly in lower-PPP markets (UA, RO, HU, CZ)
- We need to understand if €69.99/year is viable as a uniform price point across all 10 markets, or whether price-sensitivity in lower-PPP markets will collapse conversion
- We need to learn whether independent drivers (the target persona) are willing to pay personally for premium navigation, given research signals indicating preference for company-provided tools
- We need to validate that the premium features (offline maps, voice instructions, lane guidance, full traffic, 7 vehicle profiles with ADR/tunnel parameters — as defined in `Subs_definition.pdf`) are perceived as worth €69.99/year by independent drivers, and which specific features drive conversion vs. which are ignored
- We need to understand if the B2B funnel assumptions (30% eligible → 50% exposed → 10% engaged → 30% registered → 40% activated) have any empirical basis, or whether the €111K should be removed from the business case until validated
- We need to learn whether simultaneous 10-market deployment is operationally feasible within Q2 given that build cost, legal effort, and engineering capacity are all [[TBD]]

---

## 6. Readiness Signal

Based on current information, this initiative is:

- [ ] Ready to move to Discovery Learning Plan
- [x] Requires significant clarification before discovery
- [ ] High risk — reconsider or narrow scope

**Rationale:** The premium feature set is now documented (`Subs_definition.pdf`) and is objectively strong — offline maps, voice instructions, lane guidance, full traffic, and ADR parameters represent clear value for professional drivers. This resolves one of the original blockers. However, the initiative is still built on Q1 test data that does not yet exist (results expected early Q2), targets a persona whose willingness to pay contradicts available research, applies a single conversion rate and price point across 10 economically diverse markets without per-market evidence, and includes €111K in B2B revenue from an entirely unvalidated funnel. The birth certificate should be updated once Q1 test results are available, with per-market conversion data, premium feature usage analytics, and a decision on whether B2B revenue belongs in the business case or should be tracked separately as upside.

---

## 7. Suggested Next Step

Select **one**:

- [ ] Create Discovery Learning Plan
- [x] Clarify Birth Certificate
- [ ] Stakeholder alignment required
- [ ] Park / kill initiative
