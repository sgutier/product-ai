# Discovery Review — EW Office Navigation Fleet Licensing

## 1. Key Assumptions Identified

### Value
- Fleet owners and dispatchers will see enough value in centralized license purchasing to pay the same price (€60/year per truck) as the existing B2C individual driver purchase — the only incremental value over B2C is the purchase channel, not the feature set
- The current B2C feature set (offline maps, traffic, Android/CarPlay) is sufficiently compelling to drive fleet-level purchases, even though drivers can already access these features by purchasing individually
- 5–10% of the ~600 EW Office companies will adopt fleet licensing in Q4 2026 — no evidence supports this conversion rate; it is purely assumed
- Dispatchers/fleet owners are currently unable or unwilling to have drivers purchase individually, creating demand for fleet-level purchasing — no research validates this pain point
- Fleet owners will proactively invest in navigation for their drivers — owner research signals: "financially cautious," "tool-conservative," "time-poor," suggesting resistance to adding a new purchasing workflow
- ~600 companies and ~2,000 connected drivers are current, active numbers — these are stated without source or date

### Usability
- Dispatchers and fleet owners will find the purchase flow in EW Office Web intuitive despite this being a new transaction type in the platform
- Drivers will understand and value the premium features they receive automatically — no driver education or consent mechanism is described
- The "per truck" license model maps cleanly to driver experience — but navigation runs on a driver's device, not on a truck, creating a truck → driver mapping dependency
- Adding license purchase and management flows to EW Office Web will not degrade the existing Office experience or increase cognitive load for dispatchers

### Feasibility
- A license entitlement system can be built to connect Office-side purchases to Navigation-side feature activation on driver devices — no architecture exists, no spike has been done
- CIAM can reliably verify and maintain company → truck → driver relationships in real-time, so that purchasing a license for "truck X" activates features on "driver Y's phone"
- Payment processing can be integrated into EW Office Web — EW Office Web likely has no existing payment infrastructure, making this a greenfield build
- Five teams (EWO, MOBILE APP, CIAM, PAYMENTS, OPERATIONS) can coordinate delivery within Q2–Q3 — all dependencies are [[TBD]] with no scoping, no owners, and no man-day estimates
- Premium features can be activated and deactivated dynamically on driver devices based on fleet license state changes (purchase, expiry, truck reassignment)

### Viability
- Web-based direct payment for Navigation features complies with Apple App Store and Google Play Store policies — offering the same features outside the store at the same price may trigger policy violations or require careful structuring
- €60/year per truck minus payment processing costs generates viable margins — at this price point, payment processing fees consume a meaningful percentage of revenue
- The revenue (€5,400 Year 1, €72,000 Year 3 optimistic) justifies the cross-team investment across 5 teams — no cost estimate exists to compare against
- A company can legally purchase software licenses on behalf of individual drivers using their personal devices — legal review has not been done
- Annual-only billing is the right model — no validation that fleet owners prefer annual commitment over monthly flexibility

---

## 2. Hypothesis Stress Test

**What works in the logic**
- There is a genuine gap: no fleet-level license purchasing exists today. The baseline is €0, so any purchase is incremental revenue.
- The target audience is quantified (~600 companies, ~2,000 drivers), giving a bounded addressable market.
- The phased approach (pilot → GA → scale) is structurally sound and allows early validation before full commitment.
- The initiative aligns with stated strategic OKRs (strengthen Office ecosystem, improve Navigation monetization).
- Driver research signals "preference for company-provided tools over personal purchases" — which supports the direction, even if it doesn't validate the mechanism.

**What is weak or unproven**
- **The "because" is circular.** The hypothesis states: "Because fleet owners value centralized management and premium features for their drivers." This restates the desired outcome, not the causal mechanism. It does not explain *why* an owner would pay €60/truck/year for features drivers can already buy individually at the same price. The only delta is the purchase channel — and "centralized purchasing" is not a pain point surfaced in any research.
- **No value premium over B2C.** The initiative offers the exact same features at the exact same price as the individual B2C subscription, through a different channel. The only value-add is "the owner buys it centrally." For a financially cautious, time-poor owner, adding a new purchasing flow in Office is the opposite of simplification — it's a new management burden without a cost or feature advantage.
- **Owner and dispatcher research contradicts the mechanism.** Owner research: "Financially cautious — monitors prices, limits, transactions," "Tool-conservative — wants simple, reliable tools with minimal time investment," "Time-poor — limited ability to learn new tools." Dispatcher research: core jobs are keeping transports moving, documentation, and real-time operations — purchasing navigation licenses is not a dispatcher job. Neither persona's research surfaces "I wish I could buy navigation licenses for my fleet" as a pain point or job-to-be-done.
- **Revenue is extremely modest relative to investment.** €5,400 in Year 1 across 5 teams. Even at Year 3 optimistic (€72K), the cumulative 3-year revenue (€59,400–€118,800) may not cover the build cost of cross-system integration spanning EWO, MOBILE APP, CIAM, and PAYMENTS — before accounting for run costs.
- **The 5% adoption rate is unsupported.** No analog, benchmark, or signal supports 5% of Office companies purchasing fleet licenses in the first quarter of availability. This is not conservative — it is arbitrary.
- **Existing B2C subscriptions are completely unaddressed.** If a driver already has an individual subscription and the fleet owner purchases a license for that driver's truck, what happens? Duplicate billing? Override? Refund? This creates billing, legal, and UX conflicts that are not acknowledged.

**Hidden dependencies**
- **Truck → driver mapping must work in real-time.** License is "per truck" but premium features activate on a driver's phone. This requires: (a) Office knowing which driver is assigned to which truck at any given time, (b) the mobile app receiving and acting on this mapping, (c) handling edge cases — driver switches trucks, multiple drivers share one truck, driver uses multiple trucks. If this mapping is unreliable, the entire entitlement system breaks.
- **Payment infrastructure in EW Office Web.** EW Office Web is a fleet management tool, not a commerce platform. Adding payment processing (card capture, billing, invoicing, refunds, renewals) is a significant capability to build from scratch. The birth certificate treats this as a line item; it is closer to a sub-initiative.
- **App Store / Play Store policy compliance.** If Navigation premium features are available via in-app purchase (current B2C flow) AND via web purchase (new fleet flow) at the same price, store policies may require that web purchases not circumvent store payment mechanisms. Apple in particular has strict rules about this. If the web flow must use App Store billing, the 30% commission applies and the already-thin margin shrinks further.
- **Driver consent and data implications.** A fleet owner purchases a license that activates features on a driver's personal device. This may have GDPR or privacy implications — the driver may need to consent to the company controlling feature state on their device. The birth certificate assumes this is frictionless.

---

## 3. Top Risks (Ranked)

1. **Value Risk: No evidence fleet owners will pay for something drivers can already buy themselves at the same price**
   - Why it matters: The initiative's entire value proposition rests on "centralized fleet license management." But the feature set and price are identical to B2C. The only incremental value is that the owner pays centrally instead of each driver paying individually. Owner research describes a persona that is financially cautious, tool-conservative, and time-poor — adding a new cost line and management flow is the opposite of what this persona seeks. No research, interview, or signal validates that fleet owners want to buy navigation licenses for their drivers.
   - What would invalidate it: If fleet owners, when presented with the offer, do not see sufficient value in paying €60/truck/year for features their drivers could buy individually — or choose not to buy at all because drivers already get by without premium features.
   - Consequence if ignored: The initiative launches with a purchase flow that no one uses. Five teams invest in building cross-system integration for €0–€2,000 in actual revenue. The initiative becomes a cautionary tale about building supply without validating demand.

2. **Viability Risk: Revenue does not justify the cross-team investment**
   - Why it matters: Year 1 target is €5,400. The initiative requires coordination across 5 teams (EWO, MOBILE APP, CIAM, PAYMENTS, OPERATIONS), greenfield payment processing infrastructure, and a new license entitlement system. All costs are [[TBD]]. Even at generous assumptions, the build cost for cross-system integration over Q2–Q3 likely exceeds the initiative's 3-year cumulative revenue. This creates a negative-ROI initiative that consumes engineering capacity that could be deployed elsewhere.
   - What would invalidate it: If the total build + run cost exceeds €50,000–€80,000, the initiative does not break even within 3 years even under optimistic adoption scenarios.
   - Consequence if ignored: Resources are allocated to an initiative with structurally negative economics. Opportunity cost compounds — the same teams could be building features with stronger revenue potential or clearer demand signals.

3. **Feasibility Risk: License entitlement architecture is undefined and architecturally non-trivial**
   - Why it matters: The core technical mechanism — "owner purchases license in Office Web → driver's phone gets premium features" — spans 4 systems (EW Office, CIAM, licensing/entitlement, mobile app) with real-time state dependencies. The "per truck" model adds a truck → driver mapping layer that must be accurate and current. No architecture exists. No spike has been done. No team has scoped the effort. The birth certificate lists all dependencies as [[TBD]].
   - What would invalidate it: If the technical integration proves significantly more complex or costly than assumed — particularly the real-time truck → driver → device entitlement chain — the build cost could blow out timelines and make the already-thin business case untenable.
   - Consequence if ignored: Discovery proceeds without understanding what is being built. PRD is written against a hand-waving architecture. Delivery reveals integration complexity that pushes GA past Q4 2026, further delaying the already-modest revenue.

---

## 4. Decision Points

> Decisions that must be made before PRD. These are choices between mutually exclusive options, not assumptions to validate.

### DP-1: Should the license be tied to a truck, a driver, or a company?
- **Options:** (a) Per truck — license is purchased for a specific vehicle in the fleet (b) Per driver — license is purchased for a specific driver in the company (c) Per company — flat fee or tiered fee covering all drivers/trucks in the fleet
- **What depends on this:** Architecture (truck → driver mapping is only needed for option a), pricing model (per-unit vs flat), UX (truck picker vs driver picker vs company toggle), entitlement logic (how does the mobile app know this driver has premium?), edge case handling (driver switching trucks, shared trucks, part-time drivers). Option (a) is the most complex technically and the least intuitive — trucks don't use apps, drivers do. Option (b) is simpler to implement but conflicts with "truck as unit." Option (c) simplifies everything but changes the revenue model entirely.
- **Current default:** Per truck (stated as a given in the birth certificate, not justified)
- **How to inform:** Customer interviews (5–10 fleet owners: "If you could give your drivers premium navigation, how would you want to manage it — per truck, per driver, or for the whole company?"); technical spike on entitlement architecture for each option
- **Decide by:** Before PRD

### DP-2: Should fleet pricing match B2C (€60/year) or offer a fleet incentive?
- **Options:** (a) Same price as B2C (€60/year per unit) — no volume incentive (b) Fleet discount (e.g., €48/year per unit for 5+) — volume incentive to buy more (c) Bundled with Office subscription — navigation included as Office tier upgrade (d) Freemium for fleet with paid premium tier — different model entirely
- **What depends on this:** Revenue projections (all current numbers assume €60/year), value proposition (identical-to-B2C pricing removes any fleet-specific incentive), competitive positioning, margin calculation, sales motion. If there is no price advantage over B2C, the fleet licensing value proposition is solely "centralized management" — which may not be enough for financially cautious owners.
- **Current default:** €60/year per truck, matching individual B2C price (stated in birth certificate)
- **How to inform:** Customer interviews (willingness to pay at different price points), competitive analysis (what do fleet management tools charge for add-on navigation?), margin analysis (what discount is sustainable after payment processing costs?)
- **Decide by:** Before PRD

### DP-3: What is the payment channel — direct web payment, store-mediated, or invoice-based?
- **Options:** (a) Direct web payment in EW Office (card capture, Stripe/Adyen) — bypasses store commission but requires greenfield payment infrastructure (b) Store-mediated (App Store / Play Store purchase triggered from Office) — proven infrastructure but 30% commission on already-modest revenue (c) Invoice-based (B2B invoicing) — fits fleet purchasing patterns but adds operational complexity and delayed revenue recognition
- **What depends on this:** Gross margin (30% store commission on €60 = €18 lost per license per year), technical scope (building payment processing vs using existing store infrastructure), App Store / Play Store policy compliance, accounting and revenue recognition, refund handling, renewal automation. This is not a minor UX decision — it determines the economic model of the initiative.
- **Current default:** Web payment in EW Office (implied by "purchase from EW Office Web")
- **How to inform:** Technical spike (what does it take to add payment processing to EW Office Web?), legal/policy review (App Store/Play Store rules on bypassing in-app purchase for same features), finance input (invoice vs card vs store billing)
- **Decide by:** Before PRD

### DP-4: What happens when a driver already has an individual B2C subscription?
- **Options:** (a) Fleet license overrides individual subscription (requires B2C refund/cancellation mechanism) (b) Fleet license coexists — driver keeps personal subscription, fleet license applies to truck (creates duplicate billing risk) (c) Fleet license replaces at renewal — no mid-term disruption (delays fleet value) (d) Individual subscription is credited toward fleet license (complex billing logic)
- **What depends on this:** Billing system design, customer communication, legal terms, driver experience (will they be confused by two entitlements?), revenue recognition (crediting/refunding existing subscriptions reduces net new revenue). If a meaningful percentage of the ~2,000 connected drivers already have B2C subscriptions, this directly impacts the addressable market and revenue model.
- **Current default:** Not addressed in the birth certificate
- **How to inform:** Data analysis (how many of the ~2,000 connected drivers currently have B2C subscriptions?), legal review (refund/cancellation obligations), billing system design spike
- **Decide by:** Before PRD

### DP-5: Annual-only billing or monthly option?
- **Options:** (a) Annual only (€60/year) — simpler billing, higher upfront commitment, lower churn management overhead (b) Monthly option (e.g., €6.99/month) — lower entry barrier, but higher churn risk and more complex billing (c) Annual with monthly payment (€5/month billed monthly but committed annually) — hybrid approach
- **What depends on this:** Revenue recognition, churn dynamics, pricing strategy, billing infrastructure complexity. Owner research signals: "financially cautious — monitors prices, limits, transactions." A €60 annual commitment from a financially cautious persona is a harder sell than €6.99/month. But monthly billing adds infrastructure complexity for an initiative already struggling with ROI.
- **Current default:** Annual (stated in birth certificate: "€60/year per truck subscription price")
- **How to inform:** Customer interviews (preference for annual vs monthly commitment), competitive analysis, billing infrastructure spike
- **Decide by:** Before Phase 1

---

## 5. Discovery Gaps by Risk Area

| Risk Area | Current Confidence | What Is Missing |
|----------|-------------------|-----------------|
| Value | Hypothesis only | No user research validates that fleet owners want to purchase navigation licenses for their drivers. No evidence that "centralized management" is a pain point. No evidence that the B2C-identical feature set at B2C-identical pricing creates sufficient fleet-level value. No data on how many connected drivers already have B2C subscriptions (which directly reduces the addressable need). Owner and dispatcher research signals actively contradict the purchase motivation. |
| Usability | Hypothesis only | No UX concept exists for the purchase flow. No testing of the truck → license → driver activation experience. No understanding of how drivers will perceive "my company activated premium features on my phone" (consent, awareness, comprehension). No assessment of the management burden on dispatchers/owners (license renewal, truck reassignment, new driver onboarding). |
| Feasibility | Hypothesis only | No architecture for the license entitlement system (Office → CIAM → mobile app). No spike on payment processing integration in EW Office Web. No scoping from any of the 5 dependent teams. All man-day estimates are [[TBD]]. The truck → driver mapping mechanism is undefined. No assessment of the real-time state management required for dynamic entitlement activation/deactivation. |
| Viability | Hypothesis only | No cost estimate exists to compare against the €5,400 Year 1 / €72,000 Year 3 revenue projections. No legal review of fleet-level license purchasing, App Store/Play Store policy compliance, or GDPR implications of company-controlled feature activation on personal devices. No payment processing cost analysis. No assessment of whether the initiative is ROI-positive at any adoption level. |

---

## 6. Recommended Learning Objectives

- We need to learn whether fleet owners and dispatchers actually want to purchase navigation licenses centrally, or whether this is a supply-side assumption with no demand signal — specifically, would they pay for something their drivers can already buy individually?
- We need to validate that there is a willingness-to-pay at €60/year per truck (or any price point) for the current B2C feature set when purchased through Office — given that owner research describes a financially cautious, tool-conservative persona
- We need to understand how many of the ~2,000 connected drivers already have individual B2C navigation subscriptions, as this directly reduces the addressable market and creates billing conflicts
- We need to learn whether the "per truck" licensing model makes sense to fleet owners, or whether per-driver or per-company models better match their mental model and management workflows
- We need to validate that the technical architecture for Office → licensing → mobile app entitlement is feasible within a single quarter, by running a spike with EWO, MOBILE APP, CIAM, and PAYMENTS teams
- We need to understand the total build cost across all 5 teams and compare it to the revenue projections — specifically, whether this initiative is ROI-positive within 2 years under realistic adoption assumptions
- We need to learn whether direct web payment for Navigation features complies with App Store and Play Store policies, or whether store-mediated billing is required (which changes the margin structure fundamentally)
- We need to validate that fleet owners see "navigation premium" as a value-add worth paying for, vs. a cost they would resist because drivers are "getting by" with free navigation or no navigation

---

## 7. Readiness Signal

Based on current information, this initiative is:

- [ ] Ready to move to Discovery Learning Plan
- [ ] Requires significant clarification before discovery
- [x] High risk — reconsider or narrow scope

**Rationale:** All four risk areas are at "Hypothesis only" confidence. The core value proposition — paying the same price for the same features through a different channel — lacks a compelling demand signal. Owner and dispatcher research actively contradicts the assumed purchase motivation. The revenue projections (€5,400 Year 1) are extremely modest relative to the 5-team cross-system investment required, and no cost estimate exists to determine ROI. Five critical decision points (licensing model, pricing, payment channel, B2C overlap, billing cadence) are embedded as assumptions rather than acknowledged as open choices. Before investing in a full Discovery Learning Plan, the initiative should validate the fundamental demand question: will fleet owners pay for fleet navigation licenses at all? A lightweight demand signal (5–10 customer interviews focused on purchase intent, not feature requests) should precede any further investment.

---

## 8. Suggested Next Step

Select **one**:

- [ ] Create Discovery Learning Plan
- [x] Clarify Birth Certificate
- [ ] Stakeholder alignment required
- [ ] Park / kill initiative
