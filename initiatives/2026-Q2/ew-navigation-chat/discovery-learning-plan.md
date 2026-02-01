# Discovery Learning Plan — EW Navigation Chat

**Initiative:** EW Navigation Chat  
**Owner:** Sergio Barguilla  
**Related artifact(s):**  
- Birth Certificate (`birth-certificate.md`)

**Discovery window:** 3–4 weeks  
**Last updated:** 2026-02-01

---

## 1. Discovery Objectives

> What must we learn before moving to PRD?

1. **Validate adoption intent** — Will dispatchers and drivers actually shift from WhatsApp/phone to in-app chat?
2. **Define MVP feature set** — What is the minimum feature set required for dispatchers and drivers to adopt (text only? attachments? read receipts?)
3. **Validate technical feasibility** — Can we deliver real-time messaging at acceptable latency and scale with current infrastructure?
4. **Understand viability constraints** — What are the infrastructure costs, and are there data privacy or compliance implications?
5. **Map dispatcher workflows** — How does chat fit into the dispatcher's daily workflow in EW Office?

---

## 2. Assumptions Being Tested

| Assumption | Risk Area | Why It Matters |
|----------|-----------|----------------|
| Dispatchers will shift from WhatsApp/phone to in-app chat | Value | If they don't shift, feature delivers no value and won't drive adoption |
| Drivers will respond to in-app messages during transport | Value / Usability | If drivers ignore notifications or find it distracting, adoption fails |
| Text-only messaging is sufficient for MVP | Value | Over-scoping MVP delays launch; under-scoping leads to rejection |
| Attachments (images, PDFs) are required for Phase 2 adoption | Value | If not needed, we can simplify scope; if needed earlier, we under-deliver |
| Real-time delivery (<5s latency) is technically achievable | Feasibility | Poor latency will make chat unusable and damage trust |
| Messaging infrastructure cost is acceptable at scale | Viability | Unexpected cost could kill the initiative post-launch |
| No major data privacy / GDPR blockers | Viability | Legal issues could delay or block rollout |

---

## 3. Planned Discovery Activities

### Activity 1 — Dispatcher Interviews

- **Learning objective(s):** Validate adoption intent; Map dispatcher workflows; Define MVP feature set
- **Risk area:** Value
- **Method:** Semi-structured interviews
- **Description:** Interview 6–8 dispatchers from EW Office customers to understand current communication tools, pain points, and what would make them switch to in-app chat. Probe for must-have features vs. nice-to-have.
- **Participants / data source:** Dispatchers from 3–4 existing EW Office customers (mix of fleet sizes)
- **Owner:** [[TBD — Product or UX researcher]]
- **Estimated effort:** 1.5 weeks (recruiting + interviews + synthesis)
- **Dependencies:** Customer Success / Commercial to facilitate introductions

---

### Activity 2 — Driver Contextual Inquiry

- **Learning objective(s):** Validate driver adoption intent; Understand usability constraints during driving
- **Risk area:** Value / Usability
- **Method:** Contextual inquiry (ride-along or remote observation + interview)
- **Description:** Observe 4–6 company drivers during transport execution to understand when/how they communicate with dispatch today, willingness to use in-app chat, and usability concerns (distraction, device handling).
- **Participants / data source:** Company drivers (employed, using EW Navigation)
- **Owner:** [[TBD — UX researcher or PM]]
- **Estimated effort:** 1.5 weeks
- **Dependencies:** Fleet access via Customer Success

---

### Activity 3 — Competitive Feature Audit

- **Learning objective(s):** Define MVP feature set; Benchmark against market expectations
- **Risk area:** Value
- **Method:** Desk research / product teardown
- **Description:** Audit messaging features in 3–4 competitor products (Webfleet, Samsara, Teletrac Navman, Verizon Connect). Document: feature set, UX patterns, attachment support, notification model.
- **Participants / data source:** Competitor apps / demos / documentation
- **Owner:** [[TBD — PM or Analyst]]
- **Estimated effort:** 3–4 days
- **Dependencies:** None

---

### Activity 4 — Architecture Spike

- **Learning objective(s):** Validate technical feasibility; Estimate infrastructure cost
- **Risk area:** Feasibility / Viability
- **Method:** Technical spike / proof-of-concept
- **Description:** Engineering spike to evaluate real-time messaging options (e.g., WebSocket, Firebase, custom). Assess latency, scalability, cost per message, integration with EW Office and Navigation. Produce recommendation memo.
- **Participants / data source:** API MNG + INFRA engineers
- **Owner:** [[TBD — Tech Lead / Architect]]
- **Estimated effort:** 1–2 weeks
- **Dependencies:** None (can run in parallel with user research)

---

### Activity 5 — Data Privacy & Compliance Review

- **Learning objective(s):** Understand viability constraints
- **Risk area:** Viability
- **Method:** Policy review / Legal consultation
- **Description:** Review GDPR and data retention implications for storing message content. Clarify: data residency, retention policies, user consent requirements, right to deletion.
- **Participants / data source:** Legal, DPO, Compliance
- **Owner:** [[TBD — PM + Legal contact]]
- **Estimated effort:** 1 week
- **Dependencies:** Legal availability

---

### Activity 6 — Lo-Fi Prototype Test (optional, if time permits)

- **Learning objective(s):** Validate MVP feature set; Test usability assumptions
- **Risk area:** Usability
- **Method:** Clickable prototype + usability test
- **Description:** Create a lo-fi prototype of chat UI in Navigation (driver) and Office (dispatcher). Test with 3–4 users to validate information hierarchy, notification model, and core flows.
- **Participants / data source:** Mix of dispatchers and drivers
- **Owner:** [[TBD — UX Designer]]
- **Estimated effort:** 1 week (design) + 0.5 week (testing)
- **Dependencies:** Findings from Activities 1–2 inform prototype

---

## 4. Success & Failure Signals

| Learning Objective | Success Signal | Failure Signal |
|-------------------|----------------|----------------|
| Dispatchers will shift to in-app chat | ≥5/8 dispatchers express clear intent to switch; cite specific pain points with WhatsApp | <3/8 express interest; "WhatsApp is fine" |
| Drivers will respond to in-app messages | Drivers confirm they would check/respond during stops or breaks; no strong objections | Drivers cite distraction, device access, or "I'll just call" as blockers |
| Text-only is sufficient for MVP | Majority of dispatchers say text is enough to start; attachments are "nice to have" | Attachments cited as must-have by majority; "useless without docs" |
| Real-time delivery is achievable | Spike shows <3s latency achievable at projected scale; cost within budget | Latency >10s or cost prohibitive |
| No major compliance blockers | Legal confirms no blockers with standard consent and retention policy | Legal flags GDPR, data residency, or consent issues requiring major work |

---

## 5. Metrics & Evidence to Capture

- **Quantitative proxies (where available):**
  - Current driver app push notification engagement rates (baseline)
  - EW Office customer count eligible for Chat (addressable market)
  - Message volume benchmarks from competitors (if available)

- **Qualitative signals:**
  - Repeated objections or enthusiasm patterns
  - Specific feature requests (e.g., "I need to send photos of damage")
  - Workflow context (when do dispatchers need to reach drivers?)

- **Artifacts to produce:**
  - Interview summary (dispatchers)
  - Contextual inquiry summary (drivers)
  - Competitive feature matrix
  - Architecture recommendation memo
  - Legal/compliance summary
  - Lo-fi prototype + test findings (if run)

---

## 6. Risks & Mitigations (Discovery Phase)

| Risk | Impact on Discovery | Mitigation |
|----|---------------------|------------|
| Difficulty recruiting dispatchers/drivers | Delays user research | Start recruitment early; leverage Customer Success relationships |
| Bias toward positive feedback | False confidence in adoption | Use neutral prompts; probe for objections; triangulate with behavioral data |
| Architecture spike blocked by other priorities | Feasibility remains unknown | Timebox spike; escalate early if blocked |
| Legal review delayed | Viability risk unresolved before PRD | Initiate Legal request in Week 1; flag as time-sensitive |

---

## 7. Decision Criteria

> What decision will this discovery enable?

At the end of discovery, we expect to decide:

- [ ] **Proceed to PRD as planned** — Adoption intent validated, MVP scope clear, feasibility confirmed, no blockers
- [ ] **Narrow or change scope** — e.g., defer attachments, simplify notification model
- [ ] **Iterate discovery** — Key assumptions still unvalidated; need more evidence
- [ ] **Park or kill the initiative** — Low adoption intent, major technical/legal blockers

**Decision owner:** Sergio Barguilla

---

## 8. Outputs & Where They Will Live

- Discovery summary: `initiatives/2026-Q2/ew-navigation-chat/discovery-summary.md`
- Evidence links (Figma, Miro, Docs): [[TBD — add as produced]]
- Updates to Birth Certificate:
  - Product Risks table (update status and links)
  - Discovery Artifacts table (add links)
  - Hypothesis refinement (if scope changes)

---

## 9. Next Step After Discovery

Select **one**:

- [ ] Create PRD
- [ ] Run additional discovery
- [ ] Escalate decision
- [ ] Park / kill initiative
