# Discovery Review — EW Office Navigation Fleet Licensing

## 1. Key Assumptions Identified

### Value
- Dispatchers/fleet owners will see value in purchasing licenses centrally vs. drivers purchasing individually
- Fleet owners value centralized management enough to pay €60/year per truck
- The premium features (offline maps, traffic, Android/CarPlay) are sufficient to drive adoption
- 5–10% of eligible companies will purchase licenses in Q4 (conservative estimate)
- Drivers will perceive value from company-purchased licenses and engage with premium features
- The Office–Navigation integration value proposition is clear enough to justify fleet-level purchase

### Usability
- Purchase flow in EW Office Web will be intuitive for dispatchers/fleet owners
- Drivers will understand they have premium features without confusion about entitlements
- License entitlement system integration (Office → Navigation) will work seamlessly
- Driver notification/onboarding for premium features will be effective
- No negative impact on EW Office customer satisfaction from adding purchase capability

### Feasibility
- License entitlement system can integrate Office → Navigation reliably
- Payment processing integration is straightforward
- CIAM can verify identity and company linkage for license eligibility
- Technical implementation can be completed within Q2–Q3 timeline
- All required teams (EWO, MOBILE APP, CIAM, PAYMENTS) can coordinate delivery

### Viability
- €60/year per truck pricing is acceptable to fleet owners (matches individual driver purchase)
- Payment processing costs and infrastructure costs are acceptable
- No App Store / Play Store policy violations from fleet licensing model
- Legal/compliance review will approve license terms
- Support operations can handle fleet licensing inquiries
- Revenue model aligns with existing Navigation monetization strategy

---

## 2. Hypothesis Stress Test

**What works in the logic**
- Clear customer segment (EW Office customers with connected drivers)
- Existing infrastructure (Office web, Navigation app, CIAM, payment systems)
- Direct revenue opportunity from ~600 companies, ~2,000 drivers
- Strategic alignment with Office ecosystem strengthening

**What is weak or unproven**
- **Missing causal step:** The hypothesis assumes "fleet owners value centralized management" but provides no evidence that this is true. The birth certificate acknowledges this as an open question but treats it as a given in the hypothesis.
- **Pricing assumption untested:** €60/year per truck matches individual driver purchase, but fleet owners may expect bulk discounts or different pricing models. No validation that this price point works for fleet purchases.
- **Adoption rate assumption:** 5–10% Q4 adoption is labeled "conservative" but has no basis. Could be 1% or 20% — we don't know.
- **Value perception gap:** Drivers may not recognize or value premium features if they didn't request them. Company-purchased licenses may feel like "nice to have" rather than essential.
- **Timeline assumption:** Q4 revenue target assumes purchase capability launches early enough, but Phase 1 is Q2–Q3 and Phase 2 is Q3–Q4. If Phase 2 GA is late Q4, revenue recognition may be delayed.

**Hidden dependencies**
- **Driver adoption of premium features:** Even if licenses are purchased, drivers must actually use premium features for value to be realized. No mechanism to ensure driver engagement.
- **Office customer readiness:** Assumes Office customers are ready to purchase now, but no evidence of purchase intent or budget allocation.
- **Competitive response:** If competitors offer similar capabilities or better pricing, adoption may be lower.
- **Technical complexity:** License entitlement integration between Office and Navigation may be more complex than assumed, delaying delivery.

---

## 3. Top Risks (Ranked)

1. **Value Risk: Dispatchers/fleet owners may not see value in centralized purchase**
   - Why it matters: If fleet owners don't see value vs. drivers purchasing individually, conversion will be near zero and the initiative fails.
   - What would invalidate it: Interviews with 5+ fleet owners show "we'll let drivers buy their own" or "not worth the hassle" or "we don't manage driver apps."
   - Consequence if ignored: Build a feature nobody buys, waste engineering resources, damage credibility with Office customers.

2. **Viability Risk: Pricing model may not align with fleet owner expectations**
   - Why it matters: €60/year per truck may be too high for bulk purchases, or fleet owners may expect discounts. If pricing is wrong, adoption fails even if value exists.
   - What would invalidate it: Pricing research shows fleet owners expect 20–30% discount for bulk purchases, or competitors offer better pricing, or legal/compliance requires different pricing structure.
   - Consequence if ignored: Low conversion even if value proposition is sound, potential customer complaints, need to adjust pricing post-launch.

3. **Feasibility Risk: License entitlement integration complexity may delay delivery**
   - Why it matters: Complex integration between Office web, Navigation app, CIAM, and payment systems could delay Phase 1 beyond Q3, pushing GA to 2027 and missing Q4 revenue target.
   - What would invalidate it: Technical spike reveals integration requires 2x estimated effort, or CIAM/PAYMENTS teams cannot commit to timeline, or architectural constraints prevent seamless entitlement flow.
   - Consequence if ignored: Missed Q4 revenue target, delayed strategic value, potential scope cuts to meet timeline.

---

## 4. Discovery Gaps by Risk Area

| Risk Area | Current Confidence | What Is Missing |
|----------|-------------------|-----------------|
| Value | Hypothesis only | Direct validation that fleet owners want centralized purchase. Evidence: Dispatcher/fleet owner interviews (5–8 interviews) to understand current behavior, pain points, purchase intent, willingness to pay. Competitive analysis of how competitors handle fleet licensing. |
| Usability | Hypothesis only | UX testing of purchase flow with dispatchers. Driver testing of premium feature onboarding/notification. Evidence: Lo-fi prototype testing, usability sessions with 3–4 dispatchers, driver interviews about entitlement clarity. |
| Feasibility | Hypothesis only | Technical architecture spike for license entitlement integration. Payment processing integration assessment. Evidence: Architecture spike document, integration PoC, dependency team commitment confirmation, effort estimates from EWO/MOBILE APP/CIAM/PAYMENTS. |
| Viability | Hypothesis only | Pricing model validation with fleet owners. Legal/compliance review of license terms. Payment processing cost analysis. Evidence: Pricing research/interviews, Legal sign-off, Finance cost modeling, App Store policy review. |

---

## 5. Recommended Learning Objectives

- We need to learn whether dispatchers and fleet owners see value in purchasing navigation licenses centrally vs. letting drivers purchase individually
- We need to validate that €60/year per truck is an acceptable price point for fleet owners, or if bulk discounts/pricing tiers are required
- We need to understand if the current premium feature set (offline maps, traffic, Android/CarPlay) is sufficient to drive adoption, or if additional features are required
- We need to validate that drivers will recognize and value premium features when purchased by their company, and that entitlement/onboarding is clear
- We need to confirm technical feasibility of license entitlement integration between EW Office and Navigation, including effort estimates and timeline risks
- We need to understand legal/compliance requirements for fleet licensing, including license terms, data handling, and App Store policy compliance
- We need to assess payment processing integration complexity and costs to ensure viability

---

## 6. Readiness Signal

Based on current information, this initiative is:

- [ ] Ready to move to Discovery Learning Plan
- [x] Requires significant clarification before discovery
- [ ] High risk — reconsider or narrow scope

**Rationale:** The birth certificate identifies key assumptions but provides no evidence to support them. All four risk areas (Value, Usability, Feasibility, Viability) are marked as "Hypothesis only" with no validation. The hypothesis contains weak causal logic (assumes fleet owners value centralized management without evidence) and has multiple hidden dependencies (driver adoption, technical complexity, pricing alignment). Discovery is required before PRD commitment, but the birth certificate needs clarification on baseline metrics, current Office customer behavior, and existing license entitlement infrastructure.

---

## 7. Suggested Next Step

Select **one**:

- [x] Create Discovery Learning Plan
- [ ] Clarify Birth Certificate
- [ ] Stakeholder alignment required
- [ ] Park / kill initiative
