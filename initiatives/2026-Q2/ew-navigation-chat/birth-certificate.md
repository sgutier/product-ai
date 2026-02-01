# Initiative Birth Certificate

**Initiative:** EW Navigation Chat  
**Start quarter:** 2026 Q2  
**Planning horizon:** Q+0 to Q+2 (3 quarters)  
**Owner:** Sergio Barguilla  
**Status:** Draft  
**Last updated:** 2026-02-01

---

## General Description (≤ 200 words)

**One-liner:** In-app messaging between drivers (EW Navigation) and dispatchers (EW Office) for communication during transport execution.

**Target customers / users:** Company drivers, dispatchers, fleet owners/managers

**Customer problem / opportunity:**  
Dispatchers and drivers lack a structured, auditable communication channel within the EW ecosystem. Today, they rely on WhatsApp, phone calls, or fragmented tools—leading to lost messages, privacy risks (personal numbers exposed), and no link between communication and transport context.

**Proposed outcome:**  
Drivers and dispatchers can exchange messages and documents within a secure, auditable channel integrated with EW Office and EW Navigation—improving coordination during transport execution without exposing personal contact information.

**Business relevance:**  
- Enables integrated use cases between EW Office and EW Navigation
- Core component of future FMS entry-level / lightweight tablet proposition
- Builds stickiness and differentiation vs. competitors who offer messaging as standard
- Supports customer migration from legacy platforms

**Constraints / assumptions:**  
- Dispatcher must use EW Office (web)
- Driver must use EW Navigation App
- Initial scope focuses on 1:1 messaging; group/broadcast in later phases

---

## Hypothesis

If we deliver **in-app dispatcher-driver messaging integrated between EW Office and EW Navigation**  
For **company drivers and dispatchers using EW Office + EW Navigation**  
We expect **dispatchers and drivers to adopt in-app chat as their primary communication channel during transport execution**  
Which will move **Customer Adoption (% of EW Office customers actively using Chat)** by **20%+ of active EW Office customers within 6 months of launch**  
By **end of Q4 2026**  
Because **research shows this is one of the most requested features by transportation companies, and it is table-stakes for the FMS entry-level proposition**.

_Open question(s) / assumptions to validate:_  
- Will dispatchers shift from WhatsApp/phone to in-app chat?
- What is the minimum feature set required for adoption (text only vs. attachments vs. read receipts)?

---

## Main Metrics / Key Results

**Primary metric (north star for this initiative):**  
**Customer Adoption Rate** — % of EW Office customers with at least one active chat (message sent or received) per month

**Baseline:** 0% (feature does not exist)  
**Target:** 20% of EW Office customers with active chats by end of Q4 2026

**Secondary metrics:**
- **Chats initiated** — Number of new chat threads started per month
- **Messages per transport** — Average messages exchanged during active transports
- **Driver adoption** — % of EW Navigation users (linked to Office) with active chats

**Guardrail metrics (must not degrade):**  
- Crash-Free Rate (CFR) ≥ current baseline
- App Store Rating ≥ current baseline

**Post-runtime learning statement (to be completed after launch / experiment):**

After a runtime of **[[X weeks]]**, we saw **Customer Adoption Rate** **[[increase/decrease]]** **[[significantly/not significantly]]**.  
This **[[validates / fails to validate]]** our hypothesis that **in-app messaging** will cause **shift from external tools and improved dispatcher-driver coordination**.  
We also observed **[[secondary metric(s)]]** go **[[up/down]]**.

---

## 💰 Impact

> Estimates based on strategic value as enabler; direct revenue attribution is indirect.

**Revenue impact (by year or phase):**
- **Year 1:** €50K–100K (retention of at-risk customers during migration; enabler for 2–3 new contracts)
- **Year 2:** €200K–400K (part of FMS entry-level bundle; contributes to tablet proposition upsell)
- **Year 3:** €500K+ (scaled adoption across EW Office base; reduced churn from feature parity)

**Key assumptions:**  
- Chat is a prerequisite/enabler, not a standalone revenue driver
- Revenue realized through: (1) retained customers, (2) unblocked migrations, (3) new contracts requiring messaging
- FMS entry-level proposition bundles Chat + Navigation + basic fleet features
- 10–15% of EW Office customers adopt within Year 1; scales to 30–40% by Year 3

**Cost & investment (high level):**  
- Build cost (CapEx / MDs): [[TBD — requires scoping with MOBILE APP, EWO, API MNG]]
- Run cost (OpEx): [[TBD — messaging infrastructure, storage, push notifications]]
- Opportunity cost: [[TBD — other roadmap items deprioritized]]

---

## General Scope

**Customer-visible outcomes by end of initiative:**  
- Dispatchers can send and receive messages to/from drivers directly within EW Office
- Drivers can send and receive messages from dispatchers within EW Navigation App
- Messages are linked to driver/vehicle context and persist for reference
- Push notifications alert both sides of new messages in real-time

**Key deliverables:**  
- Chat UI in EW Navigation App (driver side)
- Chat UI in EW Office web (dispatcher side)
- Backend messaging service (real-time delivery, persistence)
- Push notification infrastructure
- Message history and retrieval API

**Definition of Done (high level):**  
- A dispatcher in EW Office can select a driver and send a text message
- The driver receives a push notification, opens EW Navigation, reads the message, and replies
- Both parties see the conversation history
- Messages are stored and retrievable for at least 90 days

---

## 🗓️ Phased Scope & Milestones

### Phase 1 — MVP (2026 Q2)
**Intended outcome(s):**
- Basic 1:1 text messaging works end-to-end between dispatcher (Office) and driver (Navigation)
- Validates adoption with pilot customers

**Key deliverables / milestones:**
- Chat UI in driver app + Office web
- Real-time message delivery
- Push notifications
- Internal dogfooding + 2–3 pilot customers

---

### Phase 2 — Enrichment (2026 Q3)
**Intended outcome(s):**
- Feature parity with market expectations
- Supports document exchange and operational workflows

**Key deliverables / milestones:**
- Attachment support (images, PDFs)
- Read receipts / delivery status
- Conversation search and filtering
- Broadcast messaging (dispatcher → multiple drivers)

---

### Phase 3 — Scale & Integration (2026 Q4)
**Intended outcome(s):**
- GA rollout to all EW Office customers
- Integrated into FMS entry-level proposition

**Key deliverables / milestones:**
- Performance optimization for high-volume fleets
- Analytics dashboard (adoption, message volume)
- Bundled into FMS lightweight tablet offering
- Documentation and support enablement

---

## 🔗 Dependencies

**Team codes:** MOBILE APP, EWO, API MNG, INFRA, DATA, FMS, OPERATIONS

### Phase 1
- **MOBILE APP** — [[TBD]] MDs — Chat UI in EW Navigation App + push handling — Owner: [[TBD]]
- **EWO** — [[TBD]] MDs — Chat UI in EW Office web — Owner: [[TBD]]
- **API MNG** — [[TBD]] MDs — Messaging backend / API — Owner: [[TBD]]
- **INFRA** — [[TBD]] MDs — Real-time messaging infrastructure — Owner: [[TBD]]

### Phase 2
- **MOBILE APP** — [[TBD]] MDs — Attachments, read receipts — Owner: [[TBD]]
- **EWO** — [[TBD]] MDs — Attachments, broadcast, search — Owner: [[TBD]]
- **DATA** — [[TBD]] MDs — Message storage, audit logs — Owner: [[TBD]]

### Phase 3
- **FMS** — [[TBD]] MDs — Integration with lightweight tablet proposition — Owner: [[TBD]]
- **OPERATIONS** — [[TBD]] MDs — Rollout support, training, documentation — Owner: [[TBD]]

---

## Not in Scope

- Video calling / voice messages
- Driver-to-driver messaging
- Integration with external messaging platforms (WhatsApp, Telegram, etc.)
- Embedded / OEM navigation users
- Offline-first messaging (requires connectivity)

---

## Why Now?

**Trigger / context:**  
- Chat is a core component of the future FMS entry-level / lightweight tablet proposition
- Opportunity to build integrated use cases between EW Office and EW Navigation
- Market expectation: all leading competitors (Webfleet, Samsara, Teletrac Navman) include in-app messaging as standard
- Research confirms this is one of the most requested features by transportation companies

**Cost of delay:**  
- FMS entry-level proposition incomplete without messaging
- Continued reliance on WhatsApp/phone creates compliance and privacy gaps
- Competitive disadvantage in product evaluations
- Slower adoption of EW Office + Navigation integrated workflows

**Strategic alignment:**  
- Supports OKR: "Strengthen EW Office ecosystem"
- Supports OKR: "Improve transport execution experience"
- Enables transition from "standalone navigation" to "execution surface for EW Office workflows"
- Foundation for FMS entry-level commercial proposition

---

## 📎 Documentation Links

### Product Risks

| Risk Area | Evidence / Link | Notes / Mitigation |
|---------|----------------|--------------------|
| **Value** | [[TBD]] | Status: Some evidence (research). Mitigation: Pilot validation with 2–3 customers |
| **Usability** | [[TBD]] | Status: Hypothesis only. Mitigation: Lo-fi prototype testing with drivers |
| **Feasibility** | [[TBD]] | Status: Hypothesis only. Mitigation: Architecture spike in Phase 1 |
| **Viability** | [[TBD]] | Status: Hypothesis only. Mitigation: Cost modeling for messaging infra |

---

## Discovery Artifacts

| Artifact | Evidence / Link |
|--------|-----------------|
| Lean Product Canvas | [[TBD]] |
| Opportunity–Solution Tree | [[TBD]] |
| High-level solution architecture | [[TBD]] |
| Lo-fi design | [[TBD]] |
| Customer Journey (as-is / to-be) | [[TBD]] |
| User research | "One of the most required features by transportation companies" |

---

## 👥 Stakeholders

**Product owner:** Sergio Barguilla  
**Marketing lead:** [[TBD]]  
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
