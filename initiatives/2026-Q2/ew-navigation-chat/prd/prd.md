# Product Requirements Document (PRD)

**Initiative:** EW Navigation Chat  
**Owner:** Sergio Barguilla  
**Status:** Ready with constraints  
**Assumption mode:** Assumption-based (MOCK)  
**Last updated:** 2026-02-01

**Related artifacts:**
- Birth Certificate (`../birth-certificate.md`)
- Discovery Summary (`../discovery-summary.md`)

---

> **Important:** This PRD is created on assumption-based planning. No real discovery activities have been executed. All key assumptions remain unvalidated. Discovery must be completed and validation gates passed before delivery commitment.

---

## 1. PRD Overview

**Purpose of this PRD:**  
Define requirements for the EW Navigation Chat feature to enable initial delivery planning, technical scoping, and dependency alignment. This PRD structures solution thinking and informs build estimates.

**Context:**  
Dispatchers and drivers currently lack a structured, auditable communication channel within the EW ecosystem. They rely on WhatsApp, phone calls, or fragmented tools — creating privacy risks, compliance gaps, and disconnected communication from transport context.

EW Navigation Chat introduces in-app messaging between drivers (EW Navigation App) and dispatchers (EW Office web), enabling secure, auditable communication during transport execution. This is a market-standard feature offered by all major competitors and is a core component of the future FMS entry-level / lightweight tablet proposition.

---

## 2. Goals & Non-Goals

### Goals
- Enable 1:1 real-time messaging between dispatchers (EW Office) and drivers (EW Navigation)
- Provide a secure, auditable communication channel that replaces WhatsApp/phone for operational communication
- Deliver push notifications to ensure timely message awareness
- Persist message history for reference and compliance
- Validate adoption with pilot customers before GA rollout

### Non-Goals (Explicit)
- This PRD does NOT cover voice/video calling
- This PRD does NOT cover driver-to-driver messaging
- This PRD does NOT include integration with external messaging platforms (WhatsApp, Telegram)
- This PRD does NOT target embedded/OEM navigation users
- This PRD does NOT require offline-first messaging (connectivity required)

---

## 3. Success Criteria

**Primary metric(s):**
- **Customer Adoption Rate** — % of EW Office customers with at least one active chat (message sent or received) per month

**Target(s):**
- 20% of EW Office customers with active chats by end of Q4 2026

**Guardrail metrics (must not degrade):**
- Crash-Free Rate (CFR) ≥ current baseline
- App Store Rating ≥ current baseline

**Qualitative success signals:**
- Dispatchers report reduced reliance on WhatsApp for driver communication
- Drivers find the chat accessible and non-distracting
- Support tickets related to driver communication decrease
- Pilot customers express willingness to expand usage

---

## 4. Scope Definition

### In Scope

**Phase 1 — MVP (Q2 2026):**
- 1:1 text messaging between dispatcher and driver
- Real-time message delivery (<5s target latency)
- Push notifications for new messages (both sides)
- Message history persistence (minimum 90 days)
- Chat UI in EW Navigation App (driver)
- Chat UI in EW Office web (dispatcher)
- Driver/vehicle context linked to conversation

**Phase 2 — Enrichment (Q3 2026):**
- Attachment support (images, PDFs)
- Read receipts / delivery status indicators
- Conversation search and filtering
- Broadcast messaging (dispatcher → multiple drivers)

**Phase 3 — Scale & Integration (Q4 2026):**
- Performance optimization for high-volume fleets
- Analytics dashboard (adoption metrics, message volume)
- Integration with FMS lightweight tablet proposition
- Support documentation and training materials

### Out of Scope
- Voice and video calling
- Driver-to-driver messaging
- WhatsApp / Telegram / external platform integration
- Offline-first messaging
- Embedded / OEM navigation users
- Message translation / localization (beyond standard app localization)

### Deferred / Future Considerations
- Integration with transport order context (linking messages to specific jobs)
- Automated messaging (bots, templates)
- Message reactions / quick replies
- Rich message formatting

---

## 5. Functional Requirements

### FR-1 — Dispatcher can initiate chat with driver

- **Description:**  
  The system must allow a dispatcher in EW Office (web) to select a driver and initiate a new chat conversation.

- **User(s) impacted:** Dispatcher
- **Priority:** Must
- **Assumption note:** Assumes dispatcher has visibility of drivers linked to their company in EW Office
- **Dependencies:** EWO (driver list), CIAM (identity)

---

### FR-2 — Driver can view and respond to messages

- **Description:**  
  The system must allow a driver in EW Navigation App to view incoming messages from dispatchers and send replies.

- **User(s) impacted:** Company Driver
- **Priority:** Must
- **Assumption note:** Assumes driver is logged into EW Navigation with company linkage
- **Dependencies:** MOBILE APP (chat UI), API MNG (messaging backend)

---

### FR-3 — Real-time message delivery

- **Description:**  
  The system must deliver messages in real-time with target latency <5 seconds under normal network conditions.

- **User(s) impacted:** Dispatcher, Driver
- **Priority:** Must
- **Assumption note:** Requires architecture spike to validate infrastructure approach
- **Dependencies:** API MNG, INFRA

---

### FR-4 — Push notifications for new messages

- **Description:**  
  The system must send push notifications to the recipient (driver or dispatcher) when a new message is received, even if the app is in background.

- **User(s) impacted:** Dispatcher, Driver
- **Priority:** Must
- **Assumption note:** Driver device must have push notifications enabled
- **Dependencies:** MOBILE APP (push handling), INFRA (notification service)

---

### FR-5 — Message history persistence

- **Description:**  
  The system must persist all messages and make conversation history retrievable for at least 90 days.

- **User(s) impacted:** Dispatcher, Driver
- **Priority:** Must
- **Assumption note:** GDPR/data retention policy review required before go-live
- **Dependencies:** DATA (storage), API MNG (retrieval API)

---

### FR-6 — Driver/vehicle context in conversation

- **Description:**  
  The system must display driver identity and associated vehicle context within the chat interface for dispatcher reference.

- **User(s) impacted:** Dispatcher
- **Priority:** Should
- **Assumption note:** Context derived from existing EW Office driver/vehicle data
- **Dependencies:** EWO (driver/vehicle data)

---

### FR-7 — Attachment support (Phase 2)

- **Description:**  
  The system must allow sending and receiving attachments (images, PDFs) within chat conversations.

- **User(s) impacted:** Dispatcher, Driver
- **Priority:** Should (Phase 2)
- **Assumption note:** File size and type restrictions TBD based on infrastructure capacity
- **Dependencies:** MOBILE APP, EWO, INFRA (storage)

---

### FR-8 — Read receipts and delivery status (Phase 2)

- **Description:**  
  The system must display message delivery and read status (sent, delivered, read) to the sender.

- **User(s) impacted:** Dispatcher, Driver
- **Priority:** Should (Phase 2)
- **Assumption note:** None
- **Dependencies:** API MNG

---

### FR-9 — Broadcast messaging (Phase 2)

- **Description:**  
  The system must allow a dispatcher to send a single message to multiple drivers simultaneously.

- **User(s) impacted:** Dispatcher
- **Priority:** Could (Phase 2)
- **Assumption note:** Scope limited to company announcements; not a group chat
- **Dependencies:** EWO, API MNG

---

### FR-10 — Conversation search and filtering (Phase 2)

- **Description:**  
  The system must allow dispatchers to search message history and filter conversations by driver, date, or keyword.

- **User(s) impacted:** Dispatcher
- **Priority:** Should (Phase 2)
- **Assumption note:** None
- **Dependencies:** EWO, DATA

---

## 6. Non-Functional Requirements

### Reliability & Quality

- Navigation app stability must not degrade:
  - CFR: ≥ current baseline (guardrail)
  - ANR: ≤ current baseline (guardrail)
- Chat feature must not impact navigation core functionality (routing, map rendering)

### Performance

- Message delivery latency: <5 seconds under normal network conditions
- Chat UI must be responsive (load conversation list <2s, open conversation <1s)
- Push notification delivery: within 10 seconds of message send (dependent on device/OS)

### Security & Compliance

- All messages transmitted over HTTPS/TLS
- Message content stored encrypted at rest
- GDPR compliance required: data retention policy, right to deletion, user consent
- No personal phone numbers exposed — communication is identity-based (company driver ID)
- Audit trail: message timestamps, sender/receiver IDs logged

### Platform Constraints

- iOS: Push notifications require user permission; background delivery via APNs
- Android: Push notifications via FCM; battery optimization may delay delivery
- EW Office web: WebSocket or polling for real-time updates
- No offline-first requirement — connectivity required for send/receive

---

## 7. Dependencies & Constraints

**Internal dependencies:**

| Team | Dependency | Phase |
|------|-----------|-------|
| MOBILE APP | Chat UI in EW Navigation App, push notification handling | Phase 1 |
| EWO | Chat UI in EW Office web, driver list, vehicle context | Phase 1 |
| API MNG | Messaging backend, real-time delivery, message APIs | Phase 1 |
| INFRA | Real-time messaging infrastructure, push notification service | Phase 1 |
| DATA | Message storage, audit logs, analytics | Phase 1–2 |
| CIAM | Driver/dispatcher identity, company linkage | Phase 1 |
| FMS | Lightweight tablet proposition integration | Phase 3 |
| OPERATIONS | Support documentation, training | Phase 3 |

**External dependencies:**
- Push notification services (APNs, FCM)
- Cloud messaging infrastructure (to be determined in architecture spike)

**Key constraints:**
- Chat must not depend on high-latency Office calls at runtime (per architecture constraints)
- Mobile performance is critical — chat must not degrade navigation experience
- Validation gates must be passed before delivery commitment (see Discovery Summary)

---

## 8. Risks & Open Questions

| Risk Area | Risk | Mitigation / Monitoring |
|---------|------|--------------------------|
| Value | Dispatchers may not shift from WhatsApp | Validate via dispatcher interviews before delivery commitment; monitor adoption post-launch |
| Value | Text-only MVP may be insufficient | Validate minimum feature set with users; accelerate Phase 2 if attachments required earlier |
| Usability | Chat may distract drivers during transport | Driver-first UX; chat accessible at stops only; minimal interaction design; user research |
| Usability | Drivers may not notice/respond to messages | Push notification reliability; clear notification UI; driver contextual inquiry |
| Feasibility | Real-time messaging latency may exceed target | Architecture spike before build commitment; infrastructure selection critical |
| Feasibility | Cross-team coordination delays delivery | Explicit dependency tracking; early alignment with MOBILE APP, EWO, API MNG, INFRA |
| Viability | GDPR / data privacy blockers | Legal review before go-live; data retention policy defined |
| Viability | Infrastructure cost exceeds budget | Cost modeling in architecture spike; scaling considerations |

---

## 9. Rollout & Measurement (High Level)

**Rollout approach:**
1. **Internal dogfooding** — Team uses chat for internal testing (Q2)
2. **Pilot** — 2–3 selected EW Office customers (end of Q2)
3. **Controlled rollout** — Expand to additional customers (Q3)
4. **GA** — Available to all EW Office customers (Q4)

**Measurement plan:**

| Metric | Definition | Owner | Cadence |
|--------|-----------|-------|---------|
| Customer Adoption Rate | % of EW Office customers with active chats | Product | Weekly |
| Chats initiated | New chat threads per week | Product | Weekly |
| Messages per transport | Avg messages during active transports | Product | Weekly |
| Message delivery latency | P95 latency for message delivery | Engineering | Daily (automated) |
| CFR (guardrail) | Crash-free rate for Navigation app | Engineering | Daily (automated) |
| Push notification delivery rate | % of push notifications delivered | Engineering | Weekly |

**Review cadence:** Weekly during pilot; bi-weekly post-GA

---

## 10. Open Decisions

> Decisions intentionally left open for delivery or later phases.

- Messaging infrastructure selection (WebSocket, Firebase, custom) — pending architecture spike
- File size and type limits for attachments (Phase 2)
- Message retention period beyond 90 days (compliance-driven)
- Broadcast messaging scope and limits (Phase 2)
- Integration with transport order context (future consideration)

---

## 11. Appendices & References

### Glossary

- **Chat** — A conversation thread between one dispatcher and one driver
- **Message** — A single text (or attachment, in Phase 2) sent within a chat
- **Broadcast** — A message sent by a dispatcher to multiple drivers simultaneously
- **CFR** — Crash-Free Rate: % of sessions without app crash
- **ANR** — App Not Responding: % of sessions with ANR events

### References

- Birth Certificate: `../birth-certificate.md`
- Discovery Summary: `../discovery-summary.md`
- Discovery Learning Plan: `../discovery-learning-plan.md`
- Product Context: `/product-context/`
- Business Case: Márton Szabó (2025-08-25)

---

## PRD Readiness Check

This PRD is considered:

- [ ] Ready for delivery planning
- [x] Ready with constraints
- [ ] Blocked pending clarification

**Constraints:**
- All key assumptions are unvalidated (MOCK discovery)
- Validation gates must be passed before delivery commitment:
  1. Dispatcher interviews — adoption intent validated
  2. Driver contextual inquiry — usability validated
  3. Architecture spike — feasibility confirmed
  4. Legal review — compliance confirmed

**Decision owner:** Sergio Barguilla  
**Decision date:** 2026-02-01
