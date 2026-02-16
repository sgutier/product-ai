# Initiative Birth Certificate

**Initiative:** EW Office Navigation Fleet Licensing  
**Start quarter:** 2026 Q2  
**Planning horizon:** Q+0 to Q+2 (3 quarters)  
**Owner:** Sergio Barguilla  
**Status:** Draft  
**Last updated:** 2026-02-01

---

## General Description (≤ 200 words)

**One-liner:** Enable EW Office customers (dispatchers and fleet owners) to purchase navigation licenses for their fleet trucks directly from EW Office Web, unlocking premium navigation features for drivers connected to their Office account.

**Target customers / users:** Dispatchers and fleet owners using EW Office; Company drivers connected to EW Office customers

**Customer problem / opportunity:**  
Today, customers not connected to EW Office can purchase navigation subscriptions via traditional B2C workflow (App/Play Store). EW Office customers lack a centralized way to purchase and manage navigation licenses for their fleet trucks, missing an opportunity to provide premium navigation features to their drivers and strengthen the Office–Navigation integration value proposition.

**Proposed outcome:**  
Dispatchers and fleet owners can purchase navigation licenses per truck from EW Office Web, drivers receive premium features automatically, and both parties understand the value of the integrated Office + Navigation premium package.

**Business relevance:**  
- Creates direct EW Navigation revenue stream from EW Office customer base
- Strengthens EW Office value proposition and stickiness
- Enables fleet-level monetization vs. individual driver purchases
- Positions Navigation as a premium component of the Office ecosystem

**Constraints / assumptions:**  
- Only trucks already added to the fleet in EW Office are eligible
- Initial package matches individual driver purchase (offline maps, traffic, Android/CarPlay)
- Features will be extended in future phases
- Requires integration between EW Office web and Navigation licensing system

---

## Hypothesis

If we deliver **fleet navigation license purchase capability in EW Office Web**  
For **dispatchers and fleet owners using EW Office**  
We expect **they will purchase navigation licenses for their fleet trucks**  
Which will move **License Revenue and Conversion Rate** by **generating direct EW Navigation revenue from Office customers**  
By **end of Q4 2026**  
Because **fleet owners value centralized management and premium features for their drivers, and this creates a clear monetization path for the Office–Navigation integration**.

_Open question(s) / assumptions to validate:_  
- Will dispatchers/fleet owners see value in purchasing licenses vs. drivers purchasing individually?
- What is the optimal pricing model (per truck, bulk discounts, annual vs. monthly)?
- What is the minimum feature set required for adoption?

---

## Main Metrics / Key Results

**Primary metric (north star for this initiative):**  
**License Revenue** — Total revenue from fleet navigation license purchases via EW Office

**Baseline:** €0 (no fleet licensing capability exists)  
**Target:** €5,400+ by end of Q4 2026 (conservative estimate: 5% of eligible companies purchasing licenses)

**Secondary metrics:**
- **Conversion Rate** — % of eligible EW Office customers who purchase at least one license
- **Licenses Purchased** — Number of navigation licenses purchased via EW Office
- **Average Licenses per Customer** — Licenses purchased per purchasing company

**Guardrail metrics (must not degrade):**  
- Crash-Free Rate (CFR) ≥ current baseline
- App Store Rating ≥ current baseline
- EW Office customer satisfaction (no negative impact on Office experience)

**Post-runtime learning statement (to be completed after launch / experiment):**

After a runtime of **[[X weeks]]**, we saw **License Revenue** **[[increase/decrease]]** **[[significantly/not significantly]]**.  
This **[[validates / fails to validate]]** our hypothesis that **fleet navigation license purchase capability** will cause **dispatchers and fleet owners to purchase licenses for their drivers**.  
We also observed **[[Conversion Rate / Licenses Purchased]]** go **[[up/down]]**.

---

## 💰 Impact

> Estimates based on conservative adoption assumptions: 5% of eligible companies in Q4, scaling to 15% by Year 2.

**Revenue impact (by year or phase):**
- **Year 1 / Q4 2026:** €5,400–€10,800 (5–10% of ~600 companies, avg 3 trucks × €60/year)
- **Year 2:** €18,000–€36,000 (15–30% adoption, potential market expansion)
- **Year 3:** €36,000–€72,000 (30–60% adoption, feature expansion driving higher value)

**Key assumptions:**  
- €60/year per truck subscription price (matches individual driver purchase)
- ~600 EW Office companies with ~2,000 connected drivers (~3.3 trucks per company average)
- Conservative Q4 adoption: 5–10% of eligible companies
- Annual license model (revenue recognized over subscription period)
- No bulk discounts in initial phases

**Cost & investment (high level):**  
- Build cost (CapEx / MDs): [[TBD — requires scoping with EWO, MOBILE APP, CIAM, PAYMENTS]]  
- Run cost (Opex): [[TBD — licensing infrastructure, payment processing fees]]  
- Opportunity cost: [[TBD — other roadmap items deprioritized]]

---

## General Scope

**Customer-visible outcomes by end of initiative:**  
- Dispatchers/fleet owners can purchase navigation licenses per truck from EW Office Web
- Drivers connected to Office receive premium features automatically when license is purchased
- Both dispatchers and drivers understand what premium features they receive and the value of the Office + Navigation integration

**Key deliverables:**  
- License purchase UI in EW Office Web (per-truck selection and purchase)
- License entitlement system integration (Office → Navigation)
- Driver notification/onboarding for premium features
- Billing and payment processing integration

**Definition of Done (high level):**  
- A dispatcher in EW Office can select trucks from their fleet and purchase navigation licenses
- Drivers receive premium features automatically and are notified of the upgrade
- Both parties understand what features are included and the value proposition

---

## 🗓️ Phased Scope & Milestones

### Phase 1 — MVP / Pilot (2026 Q2–Q3)
**Intended outcome(s):**
- Basic license purchase flow works end-to-end
- Validates adoption with 5–10 pilot customers
- Establishes baseline conversion and revenue metrics

**Key deliverables / milestones:**
- License purchase UI in EW Office Web
- Per-truck license selection and checkout
- License entitlement integration (Office → Navigation)
- Driver notification of premium features
- Pilot launch with select EW Office customers

---

### Phase 2 — General Availability (2026 Q3–Q4)
**Intended outcome(s):**
- Full rollout to all EW Office customers
- Optimized purchase flow based on pilot learnings
- Clear value communication and onboarding

**Key deliverables / milestones:**
- GA launch to all EW Office customers
- Enhanced onboarding and value communication
- Analytics dashboard for license sales
- Support documentation and training

---

### Phase 3 — Scale & Optimization (2026 Q4+)
**Intended outcome(s):**
- Feature expansion (beyond initial package)
- Bulk purchase options and pricing tiers
- Advanced analytics and reporting

**Key deliverables / milestones:**
- Extended feature package (beyond offline maps, traffic, Android/CarPlay)
- Bulk purchase and pricing optimization
- Fleet-level analytics and reporting
- Integration with Office subscription bundles

---

## 🔗 Dependencies

**Team codes:** EWO, MOBILE APP, CIAM, PAYMENTS, OPERATIONS

### Phase 1
- **EWO** — [[TBD]] MDs — License purchase UI in EW Office Web, truck selection, checkout flow — Owner: [[TBD]]
- **MOBILE APP** — [[TBD]] MDs — License entitlement integration, driver notification, premium feature activation — Owner: [[TBD]]
- **CIAM** — [[TBD]] MDs — Identity and company linkage verification for license eligibility — Owner: [[TBD]]
- **PAYMENTS** — [[TBD]] MDs — Payment processing integration, billing system — Owner: [[TBD]]

### Phase 2
- **EWO** — [[TBD]] MDs — GA rollout, onboarding improvements, analytics dashboard — Owner: [[TBD]]
- **OPERATIONS** — [[TBD]] MDs — Support documentation, training, customer enablement — Owner: [[TBD]]

### Phase 3
- **MOBILE APP** — [[TBD]] MDs — Extended feature package implementation — Owner: [[TBD]]
- **EWO** — [[TBD]] MDs — Bulk purchase options, pricing tiers, advanced analytics — Owner: [[TBD]]

---

## Not in Scope

- Individual driver purchase flow (existing B2C workflow remains)
- Embedded / OEM navigation users
- Custom pricing or enterprise contracts (initial phases)
- Offline purchase or manual license assignment
- License transfer between trucks (initial phases)

---

## Why Now?

**Trigger / context:**  
- Opportunity to monetize the existing EW Office customer base (~600 companies, ~2,000 drivers)
- Strengthens EW Office value proposition and ecosystem integration
- Creates direct Navigation revenue stream vs. indirect value capture
- Market timing: Office customers are actively seeking integrated solutions

**Cost of delay:**  
- Missed revenue opportunity from existing Office customer base
- Competitors may offer similar fleet licensing capabilities
- Weaker Office–Navigation integration value proposition
- Continued reliance on individual driver purchases limits fleet-level value

**Strategic alignment:**  
- Supports OKR: "Strengthen EW Office ecosystem"
- Supports OKR: "Improve Navigation monetization"
- Enables transition from "standalone navigation" to "integrated Office component"
- Foundation for future Office subscription bundles

---

## 📎 Documentation Links

### Product Risks

| Risk Area | Evidence / Link | Notes / Mitigation |
|---------|----------------|--------------------|
| **Value** | [[TBD]] | Status: Hypothesis only. Mitigation: Pilot validation with 5–10 customers; dispatcher interviews to validate purchase intent |
| **Usability** | [[TBD]] | Status: Hypothesis only. Mitigation: UX testing of purchase flow; driver onboarding testing |
| **Feasibility** | [[TBD]] | Status: Hypothesis only. Mitigation: Technical spike for license entitlement system integration; payment processing integration assessment |
| **Viability** | [[TBD]] | Status: Hypothesis only. Mitigation: Pricing model validation; payment processing cost analysis; legal review of license terms |

---

## Discovery Artifacts

| Artifact | Evidence / Link |
|--------|-----------------|
| Lean Product Canvas | [[TBD]] |
| Opportunity–Solution Tree | [[TBD]] |
| High-level solution architecture | [[TBD]] |
| Lo-fi design | [[TBD]] |
| Customer Journey (as-is / to-be) | [[TBD]] |
| User research | [[TBD]] |

---

## 👥 Stakeholders

**Product owner:** Sergio Barguilla  
**Marketing lead:** Rafaelle Gricinella  
**Operations lead:** [[TBD]]  
**Commercial lead:** [[TBD]]  
**Finance:** [[TBD]]

---

## Decision Intent

After reviewing this birth certificate, the expected decision is:

- [ ] Proceed to Discovery  
- [ ] Request changes  
- [ ] Park  
- [ ] Kill
