# Epic Plan — EW Navigation Chat

**Initiative:** EW Navigation Chat  
**Owner:** Sergio Barguilla  
**Last updated:** 2026-02-01

**Related artifacts:**
- Birth Certificate (`../birth-certificate.md`)
- Discovery Summary (`../discovery-summary.md`)
- PRD (`../prd/prd.md`)
- Delivery Decomposition (inline, 2026-02-01)

---

## 1. Epic Overview

| Epic ID | Epic Name | Outcome / Goal | PRD Coverage | Primary Owner | Depends On |
|-------|-----------|----------------|-------------|--------------|------------|
| EP-1 | Messaging Infrastructure | Backend service enabling real-time bidirectional messaging | FR-3, NFR (Performance, Security) | [[TBD — API MNG Lead]] | None (foundation) |
| EP-2 | Driver Chat Experience | Drivers can receive and respond to messages in Navigation | FR-2, FR-6 (partial) | [[TBD — MOBILE APP Lead]] | EP-1 |
| EP-3 | Dispatcher Chat Experience | Dispatchers can initiate and manage chats in EW Office | FR-1, FR-6 | [[TBD — EWO Lead]] | EP-1 |
| EP-4 | Push Notifications | Real-time notifications for new messages on both platforms | FR-4 | [[TBD — MOBILE APP Lead]] | EP-1, EP-2, EP-3 |
| EP-5 | Message Persistence & History | Messages stored and retrievable for 90+ days | FR-5, NFR (Compliance) | [[TBD — DATA Lead]] | EP-1 |
| EP-6 | Attachments & Media | Send/receive images and PDFs in chat (Phase 2) | FR-7 | [[TBD — MOBILE APP Lead]] | EP-1, EP-2, EP-3, EP-5 |
| EP-7 | Read Receipts & Status | Display delivery and read status (Phase 2) | FR-8 | [[TBD — API MNG Lead]] | EP-1, EP-2, EP-3 |
| EP-8 | Broadcast Messaging | Dispatcher can message multiple drivers (Phase 2) | FR-9 | [[TBD — EWO Lead]] | EP-3, EP-5 |
| EP-9 | Search & Filtering | Search message history and filter conversations (Phase 2) | FR-10 | [[TBD — EWO Lead]] | EP-3, EP-5 |
| EP-10 | Scale & Analytics | Performance optimization and adoption dashboard (Phase 3) | Phase 3 scope | [[TBD — DATA Lead]] | EP-1–EP-5 |

---

## 2. Epic Details

### EP-1 — Messaging Infrastructure

**Outcome / Goal:**  
Establish the backend messaging service that enables real-time, bidirectional communication between EW Office and EW Navigation App with <5s latency.

**Problem slice addressed:**  
No messaging infrastructure exists today. This epic creates the foundation that all chat functionality depends on.

**Scope (in):**
- Messaging backend service (API MNG)
- Real-time delivery mechanism (WebSocket, SSE, or equivalent)
- Message routing between dispatcher and driver
- API contracts for send/receive
- Security (HTTPS/TLS, encryption in transit)

**Scope (out):**
- UI implementation (EP-2, EP-3)
- Push notifications (EP-4)
- Message storage beyond in-flight (EP-5)
- Attachments (EP-6)

**PRD requirements covered:**
- FR-3 (Real-time message delivery)
- NFR: Performance (<5s latency)
- NFR: Security (HTTPS/TLS)

**Non-functional considerations:**
- Target latency: <5s under normal network conditions
- Must not introduce high-latency calls that block navigation runtime

**Key dependencies:**
- API MNG — Messaging backend implementation — Owner: [[TBD]]
- INFRA — Real-time infrastructure provisioning — Owner: [[TBD]]

**Risks / assumptions carried into delivery:**
- Architecture spike required to select infrastructure approach (WebSocket, Firebase, custom)  
  _Mitigation: Timebox spike to 2 weeks before full build commitment_
- Latency may exceed target under poor network  
  _Mitigation: Validate with PoC; define acceptable degradation_

**How we measure success (one metric max):**
- P95 message delivery latency <5s in pilot

**Epic exit criteria (high level):**
- Messages can be sent from Office and received in Navigation (and vice versa) in real-time
- API contracts documented and tested
- Security requirements met (TLS, encryption in transit)

---

### EP-2 — Driver Chat Experience

**Outcome / Goal:**  
Drivers can view incoming messages from dispatchers and send replies within EW Navigation App.

**Problem slice addressed:**  
Drivers currently have no way to receive structured messages from dispatchers within the EW ecosystem.

**Scope (in):**
- Chat UI in EW Navigation App (iOS + Android)
- Conversation list view
- Message thread view
- Compose and send message
- Display dispatcher context

**Scope (out):**
- Push notification handling (EP-4)
- Attachments (EP-6)
- Read receipts display (EP-7)

**PRD requirements covered:**
- FR-2 (Driver can view and respond to messages)
- FR-6 (partial — driver side context)

**Non-functional considerations:**
- CFR/ANR guardrails: Chat must not degrade navigation stability
- UI must be responsive (<2s load, <1s open conversation)
- Minimal driver distraction — chat accessible at stops

**Key dependencies:**
- MOBILE APP — Chat UI implementation — Owner: [[TBD]]
- EP-1 — Messaging backend available
- CIAM — Driver identity and company linkage

**Risks / assumptions carried into delivery:**
- Driver logged into Navigation with company linkage (assumed)  
  _Mitigation: Validate login flow during implementation_
- Usability concerns (distraction during driving)  
  _Mitigation: Driver contextual inquiry recommended before UX finalization_

**How we measure success (one metric max):**
- % of pilot drivers who send at least one message

**Epic exit criteria (high level):**
- Driver can view conversation list and message threads
- Driver can compose and send text messages to dispatcher
- UI does not degrade CFR/ANR metrics

---

### EP-3 — Dispatcher Chat Experience

**Outcome / Goal:**  
Dispatchers can initiate conversations with drivers and manage ongoing chats within EW Office web.

**Problem slice addressed:**  
Dispatchers have no structured way to message drivers within EW Office today.

**Scope (in):**
- Chat UI in EW Office web
- Driver selection / list integration
- Conversation list and thread view
- Compose and send message
- Display driver/vehicle context

**Scope (out):**
- Broadcast messaging (EP-8)
- Search and filtering (EP-9)
- Attachments (EP-6)

**PRD requirements covered:**
- FR-1 (Dispatcher can initiate chat with driver)
- FR-6 (Driver/vehicle context in conversation)

**Non-functional considerations:**
- WebSocket or polling for real-time updates
- UI responsive and consistent with EW Office design system

**Key dependencies:**
- EWO — Chat UI implementation — Owner: [[TBD]]
- EP-1 — Messaging backend available
- CIAM — Dispatcher identity

**Risks / assumptions carried into delivery:**
- Dispatcher has visibility of drivers linked to their company (assumed)  
  _Mitigation: Verify driver list API availability_
- Integration complexity with existing EW Office UI  
  _Mitigation: Early alignment with EWO team_

**How we measure success (one metric max):**
- % of pilot dispatchers who initiate at least one chat

**Epic exit criteria (high level):**
- Dispatcher can select a driver and initiate a new chat
- Dispatcher can view conversation list and message threads
- Driver/vehicle context displayed in conversation

---

### EP-4 — Push Notifications

**Outcome / Goal:**  
Deliver real-time push notifications for new messages to both drivers (mobile) and dispatchers (web/desktop).

**Problem slice addressed:**  
Users need to be alerted to new messages even when the app is in background or not actively focused.

**Scope (in):**
- Push notification infrastructure (APNs, FCM)
- Notification triggers on new message
- Notification content and deep linking
- Background delivery handling (mobile)
- Web notifications for dispatchers (optional)

**Scope (out):**
- Notification preferences / mute (future)
- Notification history (future)

**PRD requirements covered:**
- FR-4 (Push notifications for new messages)

**Non-functional considerations:**
- Delivery within 10s of message send (dependent on device/OS)
- iOS: APNs, user permission required
- Android: FCM, battery optimization may delay

**Key dependencies:**
- MOBILE APP — iOS/Android push handling — Owner: [[TBD]]
- INFRA — Notification service — Owner: [[TBD]]
- EP-1, EP-2, EP-3 — Messaging flow triggers

**Risks / assumptions carried into delivery:**
- Driver device has push notifications enabled (assumed)  
  _Mitigation: In-app prompt for permission; fallback messaging_
- Android battery optimization may delay delivery  
  _Mitigation: Platform-specific testing; document limitations_

**How we measure success (one metric max):**
- Push notification delivery rate ≥95%

**Epic exit criteria (high level):**
- New message triggers push notification to recipient
- Notification deep links to conversation
- Works on iOS, Android, and web (dispatcher)

---

### EP-5 — Message Persistence & History

**Outcome / Goal:**  
Persist all messages and enable retrieval of conversation history for at least 90 days.

**Problem slice addressed:**  
Messages need to be stored for reference, compliance, and audit purposes.

**Scope (in):**
- Message storage (DATA team)
- Retrieval API (API MNG)
- Retention policy (90 days minimum)
- Audit trail (timestamps, sender/receiver IDs)
- Encryption at rest

**Scope (out):**
- Search/filtering (EP-9)
- Export functionality (future)

**PRD requirements covered:**
- FR-5 (Message history persistence)
- NFR: Security (encrypted at rest)
- NFR: Compliance (GDPR, audit trail)

**Non-functional considerations:**
- GDPR compliance: data retention policy, right to deletion, user consent
- Encryption at rest required
- Audit trail: timestamps, sender/receiver IDs logged

**Key dependencies:**
- DATA — Message storage implementation — Owner: [[TBD]]
- API MNG — Retrieval API — Owner: [[TBD]]
- Legal — GDPR/compliance review — Owner: [[TBD]]

**Risks / assumptions carried into delivery:**
- GDPR/data retention policy review completed before go-live (critical)  
  _Mitigation: Initiate Legal review in Week 1_
- Data residency requirements unclear  
  _Mitigation: Clarify with Legal early_

**How we measure success (one metric max):**
- 100% of messages retrievable for 90 days post-send

**Epic exit criteria (high level):**
- All messages persisted with encryption at rest
- Conversation history retrievable via API
- Retention policy implemented and documented
- Legal sign-off obtained

---

### EP-6 — Attachments & Media (Phase 2)

**Outcome / Goal:**  
Enable dispatchers and drivers to send and receive attachments (images, PDFs) within chat.

**Problem slice addressed:**  
Operational communication often requires sharing documents, photos, or permits.

**Scope (in):**
- Image upload/download (mobile + web)
- PDF upload/download
- File size and type validation
- Attachment storage

**Scope (out):**
- Video attachments
- Audio messages

**PRD requirements covered:**
- FR-7 (Attachment support)

**Non-functional considerations:**
- File size limits TBD based on infrastructure capacity
- Mobile performance with large attachments

**Key dependencies:**
- MOBILE APP — Attachment UI — Owner: [[TBD]]
- EWO — Attachment UI — Owner: [[TBD]]
- INFRA — Attachment storage — Owner: [[TBD]]
- EP-1, EP-2, EP-3, EP-5 — Foundation

**Risks / assumptions carried into delivery:**
- Storage cost scaling with attachment volume  
  _Mitigation: Define file size limits; monitor storage costs_

**How we measure success (one metric max):**
- % of messages with attachments (Phase 2 baseline)

**Epic exit criteria (high level):**
- Users can send and receive images and PDFs
- File size and type validation enforced
- Attachments stored and retrievable

---

### EP-7 — Read Receipts & Status (Phase 2)

**Outcome / Goal:**  
Display message delivery and read status (sent, delivered, read) to the sender.

**Problem slice addressed:**  
Senders need confirmation that their message was delivered and read.

**Scope (in):**
- Delivery status tracking (sent → delivered)
- Read status tracking (delivered → read)
- Status display in UI (both platforms)

**Scope (out):**
- Typing indicators

**PRD requirements covered:**
- FR-8 (Read receipts and delivery status)

**Non-functional considerations:**
- Status updates should be near real-time

**Key dependencies:**
- API MNG — Status tracking logic — Owner: [[TBD]]
- MOBILE APP — Status display — Owner: [[TBD]]
- EWO — Status display — Owner: [[TBD]]
- EP-1, EP-2, EP-3 — Foundation

**Risks / assumptions carried into delivery:**
- None significant — standard messaging pattern

**How we measure success (one metric max):**
- Read receipt accuracy ≥99%

**Epic exit criteria (high level):**
- Messages display sent/delivered/read status
- Status updates in near real-time

---

### EP-8 — Broadcast Messaging (Phase 2)

**Outcome / Goal:**  
Enable dispatchers to send a single message to multiple drivers simultaneously.

**Problem slice addressed:**  
Dispatchers need to communicate company announcements or shift changes to multiple drivers at once.

**Scope (in):**
- Multi-driver selection in EW Office
- Broadcast send functionality
- Message delivery to multiple recipients

**Scope (out):**
- Group chat (replies visible to all)
- Driver-to-driver messaging

**PRD requirements covered:**
- FR-9 (Broadcast messaging)

**Non-functional considerations:**
- Scope limited to one-way broadcast, not group chat

**Key dependencies:**
- EWO — Broadcast UI — Owner: [[TBD]]
- API MNG — Broadcast delivery logic — Owner: [[TBD]]
- EP-3, EP-5 — Foundation

**Risks / assumptions carried into delivery:**
- Scope creep toward group chat  
  _Mitigation: Clearly define broadcast as one-way; defer group chat_

**How we measure success (one metric max):**
- Number of broadcast messages sent per week

**Epic exit criteria (high level):**
- Dispatcher can select multiple drivers and send one message
- All selected drivers receive the message

---

### EP-9 — Search & Filtering (Phase 2)

**Outcome / Goal:**  
Enable dispatchers to search message history and filter conversations by driver, date, or keyword.

**Problem slice addressed:**  
Dispatchers need to find past conversations and messages for reference or audit.

**Scope (in):**
- Search by keyword
- Filter by driver
- Filter by date range
- Results display in EW Office

**Scope (out):**
- Search on mobile (driver app)

**PRD requirements covered:**
- FR-10 (Conversation search and filtering)

**Non-functional considerations:**
- Performance with large message volumes

**Key dependencies:**
- EWO — Search UI — Owner: [[TBD]]
- DATA — Search indexing — Owner: [[TBD]]
- EP-5 — Message storage

**Risks / assumptions carried into delivery:**
- Search performance at scale  
  _Mitigation: Index messages for efficient search_

**How we measure success (one metric max):**
- Search query response time <2s (P95)

**Epic exit criteria (high level):**
- Dispatcher can search messages by keyword
- Dispatcher can filter by driver and date range
- Results display within acceptable latency

---

### EP-10 — Scale & Analytics (Phase 3)

**Outcome / Goal:**  
Optimize performance for high-volume fleets and deliver an adoption analytics dashboard.

**Problem slice addressed:**  
As usage scales, performance must be maintained; product team needs visibility into adoption.

**Scope (in):**
- Performance tuning for high-volume customers
- Adoption metrics dashboard (customer adoption rate, message volume)
- FMS tablet proposition integration readiness

**Scope (out):**
- New features beyond optimization

**PRD requirements covered:**
- Phase 3 scope: Performance optimization, analytics dashboard

**Non-functional considerations:**
- Scaling for 228K+ HCV base (future)

**Key dependencies:**
- All prior epics — Foundation
- DATA — Analytics dashboard — Owner: [[TBD]]
- FMS — Tablet integration — Owner: [[TBD]]

**Risks / assumptions carried into delivery:**
- Scaling issues discovered late  
  _Mitigation: Load testing during Phase 2; proactive monitoring_

**How we measure success (one metric max):**
- Customer Adoption Rate tracked and visible in dashboard

**Epic exit criteria (high level):**
- Performance validated for high-volume fleets
- Adoption dashboard live with key metrics
- FMS tablet integration readiness confirmed

---

## 3. Sequencing & Milestones (High Level)

**Proposed execution order:**

1. **EP-1 (Messaging Infrastructure)** — Foundation; all other epics depend on this. Architecture spike must complete first.
2. **EP-5 (Message Persistence)** — Required for any message to be stored; needed before UI epics can fully function.
3. **EP-2 (Driver Chat Experience)** — Core driver-facing value; can start once EP-1 underway.
4. **EP-3 (Dispatcher Chat Experience)** — Core dispatcher-facing value; can start in parallel with EP-2.
5. **EP-4 (Push Notifications)** — Can start once EP-2/EP-3 have basic send/receive.
6. **EP-6, EP-7, EP-8, EP-9 (Phase 2)** — After MVP validated; can run in parallel.
7. **EP-10 (Phase 3)** — After Phase 2; optimization and measurement.

**Parallelization opportunities:**
- **EP-2 (Driver)** and **EP-3 (Dispatcher)** can run in parallel because they are independent UI implementations consuming the same backend (EP-1).
- **EP-6, EP-7, EP-8, EP-9** can run in parallel in Phase 2 because they are independent feature additions.

**Key milestone points:**
- **MVP Complete** — EP-1, EP-2, EP-3, EP-4, EP-5 delivered; pilot ready
- **Phase 2 Complete** — EP-6, EP-7, EP-8, EP-9 delivered; feature parity
- **GA Ready** — EP-10 complete; scaled and measured

---

## 4. Cross-Team Dependency Matrix

| Team / System | Dependent Epics | Dependency Summary | Owner |
|--------------|----------------|--------------------|-------|
| API MNG | EP-1, EP-5, EP-7, EP-8 | Messaging backend, APIs, status tracking, broadcast logic | [[TBD]] |
| INFRA | EP-1, EP-4, EP-6 | Real-time infrastructure, push service, attachment storage | [[TBD]] |
| MOBILE APP | EP-2, EP-4, EP-6, EP-7 | Driver app UI, push handling, attachments, status display | [[TBD]] |
| EWO | EP-3, EP-6, EP-8, EP-9 | Dispatcher UI, attachments, broadcast, search | [[TBD]] |
| DATA | EP-5, EP-9, EP-10 | Message storage, search indexing, analytics | [[TBD]] |
| CIAM | EP-2, EP-3 | Driver/dispatcher identity, company linkage | [[TBD]] |
| Legal | EP-5 | GDPR/compliance review for message retention | [[TBD]] |
| FMS | EP-10 | Tablet proposition integration | [[TBD]] |

---

## 5. Open Questions

- **Epic owners:** Who are the leads for API MNG, MOBILE APP, EWO, DATA, INFRA?
- **Architecture spike timeline:** When can the spike for EP-1 be scheduled and completed?
- **Legal review timeline:** When can the GDPR/compliance review for EP-5 be initiated?
- **Driver research:** Will driver contextual inquiry be conducted before EP-2 UX finalization?
- **Attachment limits:** What file size and type limits should be enforced in EP-6?
- **FMS integration scope:** What specific integration is required for EP-10?
