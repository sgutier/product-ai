# User Stories — EW Navigation Chat

**Initiative:** EW Navigation Chat  
**Owner:** Sergio Barguilla  
**Last updated:** 2026-02-01

**Related artifacts:**
- Birth Certificate (`../birth-certificate.md`)
- Discovery Summary (`../discovery-summary.md`)
- PRD (`../prd/prd.md`)
- Epic Plan (`../epics/epics.md`)

---

## 1. Story Map Overview

> Stories grouped by epic. Sequencing follows the Epic Plan.

| Phase | Epics | Stories |
|-------|-------|---------|
| **Phase 1 (MVP)** | EP-1, EP-2, EP-3, EP-4, EP-5 | Foundation + core chat experience |
| **Phase 2 (Enrichment)** | EP-6, EP-7, EP-8, EP-9 | Attachments, receipts, broadcast, search |
| **Phase 3 (Scale)** | EP-10 | Performance optimization, analytics |

---

## 2. Stories by Epic

---

### EP-1 — Messaging Infrastructure

**Epic goal:** Establish backend messaging service enabling real-time bidirectional messaging with <5s latency.  
**PRD coverage:** FR-3, NFR (Performance, Security)

**Instrumentation / measurement notes (epic-level):**
- Track: Message delivery latency (P95), message send/receive success rate
- Guardrails: Latency <5s, no impact on navigation runtime
- Reporting: Engineering dashboard (real-time monitoring)

---

#### US-EP1-01 — Architecture spike for messaging infrastructure

- **User story:**  
  As a **technical lead**, I want to evaluate messaging infrastructure options (WebSocket, Firebase, custom), so that we can select an approach that meets latency and cost requirements.

- **Scope notes:** Spike only; no production code. Deliverable is a recommendation memo.
- **PRD requirement(s):** FR-3
- **Priority:** Must
- **Owner:** [[TBD — API MNG Lead]]
- **Dependencies:** INFRA (infrastructure options)

- **Design required:** No
- **Design type:** No UI (logic / backend)
- **Design intent:** N/A
- **Design constraints:** N/A
- **Figma link:** N/A

**Acceptance criteria (Given/When/Then):**
- Given the need for real-time messaging  
  When the spike is completed  
  Then a recommendation memo documents infrastructure options, latency benchmarks, cost estimates, and a recommended approach

- Given the recommendation  
  When reviewed by stakeholders  
  Then a decision is made and documented before full build begins

---

#### US-EP1-02 — Messaging backend service setup

- **User story:**  
  As a **backend engineer**, I want to implement the messaging backend service, so that messages can be routed between dispatchers and drivers in real-time.

- **Scope notes:** Core routing logic; no UI, no persistence, no push notifications.
- **PRD requirement(s):** FR-3
- **Priority:** Must
- **Owner:** [[TBD — API MNG]]
- **Dependencies:** Architecture spike (US-EP1-01)

- **Design required:** No
- **Design type:** No UI (logic / backend)
- **Design intent:** N/A
- **Design constraints:** N/A
- **Figma link:** N/A

**Acceptance criteria (Given/When/Then):**
- Given a dispatcher sends a message  
  When the message is submitted to the backend  
  Then it is routed to the target driver's session in <5s (P95)

- Given a driver sends a reply  
  When the reply is submitted  
  Then it is routed to the dispatcher's session in <5s (P95)

---

#### US-EP1-03 — API contracts for send/receive

- **User story:**  
  As a **frontend developer**, I want documented and versioned API contracts for sending and receiving messages, so that I can integrate the chat UI reliably.

- **Scope notes:** API documentation, versioning, error handling.
- **PRD requirement(s):** FR-3
- **Priority:** Must
- **Owner:** [[TBD — API MNG]]
- **Dependencies:** US-EP1-02

- **Design required:** No
- **Design type:** No UI (logic / backend)
- **Design intent:** N/A
- **Design constraints:** N/A
- **Figma link:** N/A

**Acceptance criteria (Given/When/Then):**
- Given the messaging backend is implemented  
  When API contracts are published  
  Then send/receive endpoints are documented with request/response schemas, error codes, and versioning

- Given the API documentation  
  When reviewed by mobile and web teams  
  Then integration can proceed without ambiguity

---

#### US-EP1-04 — Security: TLS and encryption in transit

- **User story:**  
  As a **security engineer**, I want all messages transmitted over HTTPS/TLS, so that communication is secure in transit.

- **Scope notes:** Encryption in transit only; encryption at rest covered in EP-5.
- **PRD requirement(s):** NFR (Security)
- **Priority:** Must
- **Owner:** [[TBD — INFRA]]
- **Dependencies:** US-EP1-02

- **Design required:** No
- **Design type:** No UI (logic / backend)
- **Design intent:** N/A
- **Design constraints:** N/A
- **Figma link:** N/A

**Acceptance criteria (Given/When/Then):**
- Given a message is sent from client to server  
  When transmitted  
  Then it uses HTTPS/TLS

- Given a message is delivered from server to client  
  When transmitted  
  Then it uses HTTPS/TLS (or WSS for WebSocket)

---

---

### EP-2 — Driver Chat Experience

**Epic goal:** Drivers can view incoming messages from dispatchers and send replies within EW Navigation App.  
**PRD coverage:** FR-2, FR-6 (partial)

**Instrumentation / measurement notes (epic-level):**
- Track: % of drivers who view chat, % who send at least one message, conversation open time
- Guardrails: CFR ≥ baseline, ANR ≤ baseline
- Reporting: Product dashboard (weekly), Firebase/Crashlytics (daily)

---

#### US-EP2-01 — Driver views conversation list

- **User story:**  
  As a **Company Driver**, I want to see a list of my conversations with dispatchers, so that I can quickly find and access messages.

- **Scope notes:** List view only; individual thread view in US-EP2-02.
- **PRD requirement(s):** FR-2
- **Priority:** Must
- **Owner:** [[TBD — MOBILE APP]]
- **Dependencies:** EP-1 (messaging backend)

- **Design required:** Yes
- **Design type:** New screen
- **Design intent:**
  - Allow driver to quickly scan and access conversations
  - Show unread indicator and most recent message preview
- **Design constraints:**
  - Minimal distraction — driver-first UX
  - Must be accessible when vehicle is stopped
  - Consistent with EW Navigation design system
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I am logged into EW Navigation with a company linkage  
  When I open the chat section  
  Then I see a list of conversations sorted by most recent message

- Given I have no conversations  
  When I open the chat section  
  Then I see an empty state indicating no messages yet

---

#### US-EP2-02 — Driver views message thread

- **User story:**  
  As a **Company Driver**, I want to open a conversation and see the full message history, so that I can read what the dispatcher sent.

- **Scope notes:** Read-only view; compose in US-EP2-03.
- **PRD requirement(s):** FR-2
- **Priority:** Must
- **Owner:** [[TBD — MOBILE APP]]
- **Dependencies:** US-EP2-01

- **Design required:** Yes
- **Design type:** New screen
- **Design intent:**
  - Display messages in a clear, chronological thread
  - Show sender identity and timestamps
- **Design constraints:**
  - Scrollable for long conversations
  - Readable typography for in-vehicle use
  - Consistent with EW Navigation design system
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I select a conversation from the list  
  When the thread opens  
  Then I see all messages in chronological order with timestamps

- Given the conversation has many messages  
  When I scroll  
  Then older messages load without performance issues

---

#### US-EP2-03 — Driver sends a message

- **User story:**  
  As a **Company Driver**, I want to compose and send a text message to the dispatcher, so that I can reply or ask questions.

- **Scope notes:** Text only; attachments in EP-6.
- **PRD requirement(s):** FR-2
- **Priority:** Must
- **Owner:** [[TBD — MOBILE APP]]
- **Dependencies:** US-EP2-02, EP-1

- **Design required:** Yes
- **Design type:** Existing screen update
- **Design intent:**
  - Add compose area to message thread screen
  - Simple text input with send button
- **Design constraints:**
  - Keyboard handling for mobile
  - Minimal interaction while driving (designed for use at stops)
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I am in a conversation thread  
  When I type a message and tap send  
  Then the message is submitted and appears in the thread

- Given I send a message  
  When it is delivered  
  Then the dispatcher receives it in <5s (P95)

---

#### US-EP2-04 — Driver sees dispatcher context

- **User story:**  
  As a **Company Driver**, I want to see who is messaging me (dispatcher name/role), so that I know who I am communicating with.

- **Scope notes:** Display dispatcher identity; derived from CIAM.
- **PRD requirement(s):** FR-6 (partial)
- **Priority:** Should
- **Owner:** [[TBD — MOBILE APP]]
- **Dependencies:** CIAM, US-EP2-02

- **Design required:** Yes
- **Design type:** Component update
- **Design intent:**
  - Display dispatcher name in conversation header
- **Design constraints:**
  - Consistent with EW Navigation header patterns
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I open a conversation  
  When the thread loads  
  Then I see the dispatcher's name or identifier in the header

---

---

### EP-3 — Dispatcher Chat Experience

**Epic goal:** Dispatchers can initiate and manage chats with drivers within EW Office web.  
**PRD coverage:** FR-1, FR-6

**Instrumentation / measurement notes (epic-level):**
- Track: % of dispatchers who initiate chat, chats per dispatcher per week, message volume
- Guardrails: UI responsiveness <2s load
- Reporting: Product dashboard (weekly)

---

#### US-EP3-01 — Dispatcher views driver list for chat

- **User story:**  
  As a **Dispatcher**, I want to see a list of drivers linked to my company, so that I can select one to message.

- **Scope notes:** Uses existing EW Office driver list; no new driver management.
- **PRD requirement(s):** FR-1
- **Priority:** Must
- **Owner:** [[TBD — EWO]]
- **Dependencies:** CIAM (company linkage), existing driver list API

- **Design required:** Yes
- **Design type:** Existing screen update
- **Design intent:**
  - Add chat entry point to existing driver list or new chat panel
  - Allow quick driver selection for messaging
- **Design constraints:**
  - Consistent with EW Office design system
  - Accessible and filterable for large driver lists
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I am logged into EW Office  
  When I open the chat section  
  Then I see a list of drivers linked to my company

- Given I have many drivers  
  When I scroll or search  
  Then the list loads and filters responsively

---

#### US-EP3-02 — Dispatcher initiates a new chat

- **User story:**  
  As a **Dispatcher**, I want to select a driver and start a new conversation, so that I can send them a message.

- **Scope notes:** 1:1 chat only; broadcast in EP-8.
- **PRD requirement(s):** FR-1
- **Priority:** Must
- **Owner:** [[TBD — EWO]]
- **Dependencies:** US-EP3-01, EP-1

- **Design required:** Yes
- **Design type:** Component update
- **Design intent:**
  - Add "Start Chat" action to driver list/card
  - Open chat panel or modal for new conversation
- **Design constraints:**
  - Consistent with EW Office interaction patterns
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I select a driver from the list  
  When I click "Start Chat" (or equivalent)  
  Then a new conversation is created and I can compose a message

- Given I start a chat with a driver I've messaged before  
  When the conversation opens  
  Then I see the existing conversation history

---

#### US-EP3-03 — Dispatcher views conversation list

- **User story:**  
  As a **Dispatcher**, I want to see a list of my active conversations, so that I can manage ongoing communication with drivers.

- **Scope notes:** List view with recent message preview.
- **PRD requirement(s):** FR-1
- **Priority:** Must
- **Owner:** [[TBD — EWO]]
- **Dependencies:** EP-1, EP-5

- **Design required:** Yes
- **Design type:** New screen
- **Design intent:**
  - Display conversation list with unread indicators and previews
  - Enable quick navigation to active conversations
- **Design constraints:**
  - Real-time updates when new messages arrive
  - Consistent with EW Office design system
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I open the chat section  
  When conversations exist  
  Then I see a list sorted by most recent message with preview text

- Given a new message arrives  
  When I am viewing the list  
  Then the list updates in real-time

---

#### US-EP3-04 — Dispatcher views message thread

- **User story:**  
  As a **Dispatcher**, I want to open a conversation and see the full message history with a driver, so that I can read their responses.

- **Scope notes:** Read + compose.
- **PRD requirement(s):** FR-1
- **Priority:** Must
- **Owner:** [[TBD — EWO]]
- **Dependencies:** US-EP3-03

- **Design required:** Yes
- **Design type:** New screen
- **Design intent:**
  - Display messages in chronological thread format
  - Include compose area for replies
- **Design constraints:**
  - Scrollable for long conversations
  - Real-time updates when new messages arrive
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I select a conversation  
  When the thread opens  
  Then I see all messages in chronological order

- Given the conversation updates while open  
  When a new message arrives  
  Then it appears in the thread in real-time

---

#### US-EP3-05 — Dispatcher sends a message

- **User story:**  
  As a **Dispatcher**, I want to compose and send a text message to a driver, so that I can give instructions or updates.

- **Scope notes:** Text only; attachments in EP-6.
- **PRD requirement(s):** FR-1
- **Priority:** Must
- **Owner:** [[TBD — EWO]]
- **Dependencies:** US-EP3-04, EP-1

- **Design required:** Yes
- **Design type:** Existing screen update
- **Design intent:**
  - Add compose area with text input and send button
- **Design constraints:**
  - Keyboard shortcuts for efficiency (Enter to send, etc.)
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I am in a conversation thread  
  When I type a message and click send  
  Then the message is submitted and appears in the thread

- Given I send a message  
  When it is delivered  
  Then the driver receives it in <5s (P95)

---

#### US-EP3-06 — Dispatcher sees driver/vehicle context

- **User story:**  
  As a **Dispatcher**, I want to see driver name and associated vehicle in the conversation, so that I have context for my communication.

- **Scope notes:** Display only; no editing of driver/vehicle data.
- **PRD requirement(s):** FR-6
- **Priority:** Should
- **Owner:** [[TBD — EWO]]
- **Dependencies:** EWO driver/vehicle data

- **Design required:** Yes
- **Design type:** Component update
- **Design intent:**
  - Display driver name and vehicle info in conversation header or sidebar
- **Design constraints:**
  - Use existing driver/vehicle data components where possible
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I open a conversation with a driver  
  When the thread loads  
  Then I see the driver's name and associated vehicle (if available) in the header or sidebar

---

---

### EP-4 — Push Notifications

**Epic goal:** Deliver real-time push notifications for new messages to both drivers and dispatchers.  
**PRD coverage:** FR-4

**Instrumentation / measurement notes (epic-level):**
- Track: Push delivery rate, push open rate, time from message send to notification delivery
- Guardrails: Delivery rate ≥95%, delivery within 10s
- Reporting: Engineering dashboard (daily)

---

#### US-EP4-01 — Driver receives push notification for new message

- **User story:**  
  As a **Company Driver**, I want to receive a push notification when a dispatcher sends me a message, so that I am aware of new communication even when the app is in background.

- **Scope notes:** iOS (APNs) and Android (FCM).
- **PRD requirement(s):** FR-4
- **Priority:** Must
- **Owner:** [[TBD — MOBILE APP]]
- **Dependencies:** EP-1, INFRA (notification service)

- **Design required:** Yes
- **Design type:** Component update
- **Design intent:**
  - Design notification content (title, body, icon)
  - Define deep link behavior to conversation
- **Design constraints:**
  - Follow iOS and Android notification guidelines
  - Clear, actionable notification text
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given my device has push notifications enabled  
  When a dispatcher sends me a message  
  Then I receive a push notification within 10s

- Given I receive a notification  
  When I tap it  
  Then the app opens to the relevant conversation

---

#### US-EP4-02 — Driver push notification permission handling

- **User story:**  
  As a **Company Driver**, I want to be prompted to enable push notifications, so that I don't miss important messages.

- **Scope notes:** In-app prompt; graceful handling if denied.
- **PRD requirement(s):** FR-4
- **Priority:** Should
- **Owner:** [[TBD — MOBILE APP]]
- **Dependencies:** None

- **Design required:** Yes
- **Design type:** Component update
- **Design intent:**
  - Design permission prompt UI with clear value proposition
  - Design fallback state if permission denied
- **Design constraints:**
  - Follow platform permission best practices
  - Non-intrusive timing
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I am using chat for the first time  
  When I open the chat section  
  Then I am prompted to enable push notifications (if not already enabled)

- Given I deny notification permission  
  When I continue using chat  
  Then the app works without notifications (degraded experience noted)

---

#### US-EP4-03 — Dispatcher receives web notification for new message

- **User story:**  
  As a **Dispatcher**, I want to receive a browser notification when a driver replies, so that I am aware of new messages while working in EW Office.

- **Scope notes:** Browser notification API; optional enhancement.
- **PRD requirement(s):** FR-4
- **Priority:** Could
- **Owner:** [[TBD — EWO]]
- **Dependencies:** EP-1

- **Design required:** Yes
- **Design type:** Component update
- **Design intent:**
  - Design browser notification content
  - Add in-app indicator for new messages (badge, sound, etc.)
- **Design constraints:**
  - Follow browser notification best practices
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I have granted notification permission in my browser  
  When a driver sends me a message  
  Then I receive a browser notification

- Given I click the notification  
  When EW Office is open  
  Then I am navigated to the relevant conversation

---

---

### EP-5 — Message Persistence & History

**Epic goal:** Persist all messages and enable retrieval for at least 90 days.  
**PRD coverage:** FR-5, NFR (Compliance)

**Instrumentation / measurement notes (epic-level):**
- Track: Message storage success rate, retrieval latency, retention compliance
- Guardrails: 100% messages persisted, encryption at rest
- Reporting: DATA team dashboard

---

#### US-EP5-01 — Messages are persisted on send

- **User story:**  
  As a **system**, I want to persist every message when it is sent, so that conversation history is available for retrieval.

- **Scope notes:** Backend storage; encrypted at rest.
- **PRD requirement(s):** FR-5
- **Priority:** Must
- **Owner:** [[TBD — DATA]]
- **Dependencies:** EP-1

- **Design required:** No
- **Design type:** No UI (logic / backend)
- **Design intent:** N/A
- **Design constraints:** N/A
- **Figma link:** N/A

**Acceptance criteria (Given/When/Then):**
- Given a message is sent  
  When the backend processes it  
  Then it is stored in the message database with timestamp, sender ID, receiver ID, and content

- Given storage  
  When data is at rest  
  Then it is encrypted

---

#### US-EP5-02 — Conversation history retrieval API

- **User story:**  
  As a **frontend developer**, I want an API to retrieve conversation history, so that users can view past messages.

- **Scope notes:** Paginated retrieval; supports both driver and dispatcher clients.
- **PRD requirement(s):** FR-5
- **Priority:** Must
- **Owner:** [[TBD — API MNG]]
- **Dependencies:** US-EP5-01

- **Design required:** No
- **Design type:** No UI (logic / backend)
- **Design intent:** N/A
- **Design constraints:** N/A
- **Figma link:** N/A

**Acceptance criteria (Given/When/Then):**
- Given a user requests conversation history  
  When the API is called with conversation ID  
  Then messages are returned in chronological order with pagination support

- Given a conversation has 500+ messages  
  When retrieved  
  Then pagination ensures acceptable response times (<2s)

---

#### US-EP5-03 — 90-day retention policy implementation

- **User story:**  
  As a **compliance officer**, I want messages retained for at least 90 days, so that audit and reference needs are met.

- **Scope notes:** Retention policy; deletion after 90 days TBD with Legal.
- **PRD requirement(s):** FR-5, NFR (Compliance)
- **Priority:** Must
- **Owner:** [[TBD — DATA]]
- **Dependencies:** Legal review

- **Design required:** No
- **Design type:** No UI (logic / backend)
- **Design intent:** N/A
- **Design constraints:** N/A
- **Figma link:** N/A

**Acceptance criteria (Given/When/Then):**
- Given a message is stored  
  When 90 days have passed  
  Then the message is still retrievable (retention met)

- Given the retention policy  
  When reviewed by Legal  
  Then deletion policy beyond 90 days is documented and implemented

_Open question:_ What is the deletion policy after 90 days? Requires Legal input.

---

#### US-EP5-04 — Audit trail logging

- **User story:**  
  As a **compliance officer**, I want an audit trail of all messages (timestamp, sender, receiver), so that communication can be reviewed if needed.

- **Scope notes:** Logging only; no admin UI in this story.
- **PRD requirement(s):** NFR (Compliance)
- **Priority:** Should
- **Owner:** [[TBD — DATA]]
- **Dependencies:** US-EP5-01

- **Design required:** No
- **Design type:** No UI (logic / backend)
- **Design intent:** N/A
- **Design constraints:** N/A
- **Figma link:** N/A

**Acceptance criteria (Given/When/Then):**
- Given a message is sent  
  When stored  
  Then timestamp, sender ID, and receiver ID are logged for audit purposes

- Given an audit request  
  When logs are queried  
  Then relevant message metadata is retrievable

---

---

### EP-6 — Attachments & Media (Phase 2)

**Epic goal:** Enable sending/receiving images and PDFs in chat.  
**PRD coverage:** FR-7

**Instrumentation / measurement notes (epic-level):**
- Track: % of messages with attachments, attachment upload/download success rate
- Guardrails: Upload time <10s for files under limit, no crashes on large files
- Reporting: Product dashboard (weekly)

---

#### US-EP6-01 — Driver sends image attachment

- **User story:**  
  As a **Company Driver**, I want to attach and send an image in a message, so that I can share photos (e.g., delivery proof, damage).

- **Scope notes:** Images only; PDFs in US-EP6-03.
- **PRD requirement(s):** FR-7
- **Priority:** Should
- **Owner:** [[TBD — MOBILE APP]]
- **Dependencies:** EP-2, INFRA (storage)

- **Design required:** Yes
- **Design type:** Existing screen update
- **Design intent:**
  - Add attachment button to compose area
  - Image picker and preview before send
- **Design constraints:**
  - File size limit indication
  - Camera and gallery access
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I am composing a message  
  When I tap attach and select an image  
  Then the image is attached and uploaded when I send

- Given file size limits  
  When I attach an image exceeding the limit  
  Then I see an error message and cannot send

---

#### US-EP6-02 — Driver views received attachment

- **User story:**  
  As a **Company Driver**, I want to view attachments (images, PDFs) sent by the dispatcher, so that I can see documents or instructions.

- **Scope notes:** Inline preview for images; download for PDFs.
- **PRD requirement(s):** FR-7
- **Priority:** Should
- **Owner:** [[TBD — MOBILE APP]]
- **Dependencies:** US-EP6-01

- **Design required:** Yes
- **Design type:** Existing screen update
- **Design intent:**
  - Display image thumbnails inline in thread
  - Full-screen image viewer on tap
  - PDF download/open action
- **Design constraints:**
  - Performance with large images
  - Offline handling (if applicable)
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given a message contains an image  
  When I view the message  
  Then I see a thumbnail and can tap to view full-size

- Given a message contains a PDF  
  When I tap it  
  Then it downloads or opens in a viewer

---

#### US-EP6-03 — Dispatcher sends attachment

- **User story:**  
  As a **Dispatcher**, I want to attach and send images or PDFs in a message, so that I can share documents with drivers.

- **Scope notes:** Images and PDFs.
- **PRD requirement(s):** FR-7
- **Priority:** Should
- **Owner:** [[TBD — EWO]]
- **Dependencies:** EP-3, INFRA (storage)

- **Design required:** Yes
- **Design type:** Existing screen update
- **Design intent:**
  - Add attachment button to compose area
  - File picker and preview
- **Design constraints:**
  - File type and size validation
  - Drag-and-drop support (web)
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I am composing a message  
  When I click attach and select a file  
  Then the file is attached and uploaded when I send

- Given file type restrictions  
  When I attach an unsupported file type  
  Then I see an error message

---

#### US-EP6-04 — Dispatcher views received attachment

- **User story:**  
  As a **Dispatcher**, I want to view attachments sent by drivers, so that I can see photos or documents they share.

- **Scope notes:** Inline preview for images; download for PDFs.
- **PRD requirement(s):** FR-7
- **Priority:** Should
- **Owner:** [[TBD — EWO]]
- **Dependencies:** US-EP6-03

- **Design required:** Yes
- **Design type:** Existing screen update
- **Design intent:**
  - Display image thumbnails inline
  - Lightbox for full-size images
  - Download link for PDFs
- **Design constraints:**
  - Consistent with EW Office file handling patterns
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given a message contains an image  
  When I view the message  
  Then I see a thumbnail and can click to view full-size

- Given a message contains a PDF  
  When I click it  
  Then it downloads

---

---

### EP-7 — Read Receipts & Status (Phase 2)

**Epic goal:** Display delivery and read status (sent, delivered, read) to senders.  
**PRD coverage:** FR-8

**Instrumentation / measurement notes (epic-level):**
- Track: Read receipt accuracy, status update latency
- Guardrails: Accuracy ≥99%
- Reporting: Engineering dashboard

---

#### US-EP7-01 — Message delivery status tracking

- **User story:**  
  As a **system**, I want to track when a message is delivered to the recipient's device, so that senders can see delivery status.

- **Scope notes:** Backend tracking; UI display in US-EP7-03/04.
- **PRD requirement(s):** FR-8
- **Priority:** Should
- **Owner:** [[TBD — API MNG]]
- **Dependencies:** EP-1

- **Design required:** No
- **Design type:** No UI (logic / backend)
- **Design intent:** N/A
- **Design constraints:** N/A
- **Figma link:** N/A

**Acceptance criteria (Given/When/Then):**
- Given a message is sent  
  When it reaches the recipient's device  
  Then the status is updated to "delivered"

---

#### US-EP7-02 — Message read status tracking

- **User story:**  
  As a **system**, I want to track when a message is read by the recipient, so that senders can see read status.

- **Scope notes:** Triggered when message is displayed in thread.
- **PRD requirement(s):** FR-8
- **Priority:** Should
- **Owner:** [[TBD — API MNG]]
- **Dependencies:** US-EP7-01

- **Design required:** No
- **Design type:** No UI (logic / backend)
- **Design intent:** N/A
- **Design constraints:** N/A
- **Figma link:** N/A

**Acceptance criteria (Given/When/Then):**
- Given a message is delivered  
  When the recipient views the message  
  Then the status is updated to "read"

---

#### US-EP7-03 — Driver sees message status

- **User story:**  
  As a **Company Driver**, I want to see the status of messages I send (sent, delivered, read), so that I know if the dispatcher received my message.

- **Scope notes:** Status indicators in UI.
- **PRD requirement(s):** FR-8
- **Priority:** Should
- **Owner:** [[TBD — MOBILE APP]]
- **Dependencies:** US-EP7-01, US-EP7-02

- **Design required:** Yes
- **Design type:** Component update
- **Design intent:**
  - Add status indicators (checkmarks, icons) to sent messages
- **Design constraints:**
  - Clear, universally understood iconography
  - Subtle, non-distracting
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I send a message  
  When viewing the thread  
  Then I see status indicators (sent → delivered → read)

---

#### US-EP7-04 — Dispatcher sees message status

- **User story:**  
  As a **Dispatcher**, I want to see the status of messages I send (sent, delivered, read), so that I know if the driver received my message.

- **Scope notes:** Status indicators in UI.
- **PRD requirement(s):** FR-8
- **Priority:** Should
- **Owner:** [[TBD — EWO]]
- **Dependencies:** US-EP7-01, US-EP7-02

- **Design required:** Yes
- **Design type:** Component update
- **Design intent:**
  - Add status indicators to sent messages in web UI
- **Design constraints:**
  - Consistent with mobile status indicators
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I send a message  
  When viewing the thread  
  Then I see status indicators (sent → delivered → read)

---

---

### EP-8 — Broadcast Messaging (Phase 2)

**Epic goal:** Enable dispatchers to send a single message to multiple drivers simultaneously.  
**PRD coverage:** FR-9

**Instrumentation / measurement notes (epic-level):**
- Track: Number of broadcast messages sent, recipients per broadcast
- Guardrails: Delivery to all recipients
- Reporting: Product dashboard (weekly)

---

#### US-EP8-01 — Dispatcher selects multiple drivers for broadcast

- **User story:**  
  As a **Dispatcher**, I want to select multiple drivers from the driver list, so that I can send them all the same message.

- **Scope notes:** Multi-select UI; broadcast send in US-EP8-02.
- **PRD requirement(s):** FR-9
- **Priority:** Could
- **Owner:** [[TBD — EWO]]
- **Dependencies:** US-EP3-01

- **Design required:** Yes
- **Design type:** Existing screen update
- **Design intent:**
  - Add multi-select mode to driver list
  - Show selection count and "Compose Broadcast" action
- **Design constraints:**
  - Clear differentiation from 1:1 chat initiation
  - Efficient for large selections
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I am in the chat section  
  When I enable broadcast mode  
  Then I can select multiple drivers via checkboxes or multi-select

- Given I have selected drivers  
  When I view my selection  
  Then I see the count and list of selected drivers

---

#### US-EP8-02 — Dispatcher sends broadcast message

- **User story:**  
  As a **Dispatcher**, I want to compose and send a message to all selected drivers, so that I can announce information or updates efficiently.

- **Scope notes:** One-way broadcast; no group replies.
- **PRD requirement(s):** FR-9
- **Priority:** Could
- **Owner:** [[TBD — EWO]]
- **Dependencies:** US-EP8-01, EP-1

- **Design required:** Yes
- **Design type:** Existing screen update
- **Design intent:**
  - Compose area for broadcast message
  - Confirmation before send (showing recipient count)
- **Design constraints:**
  - Clear indication that this is a broadcast, not a group chat
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I have selected multiple drivers  
  When I compose a message and click send  
  Then the message is delivered to all selected drivers

- Given a broadcast is sent  
  When drivers receive it  
  Then each driver sees it as a 1:1 message from the dispatcher (not a group thread)

---

---

### EP-9 — Search & Filtering (Phase 2)

**Epic goal:** Enable dispatchers to search message history and filter conversations.  
**PRD coverage:** FR-10

**Instrumentation / measurement notes (epic-level):**
- Track: Search query count, search result click-through, query response time
- Guardrails: Response time <2s (P95)
- Reporting: Product dashboard (weekly)

---

#### US-EP9-01 — Dispatcher searches messages by keyword

- **User story:**  
  As a **Dispatcher**, I want to search message history by keyword, so that I can find specific conversations or information.

- **Scope notes:** Keyword search across all conversations.
- **PRD requirement(s):** FR-10
- **Priority:** Should
- **Owner:** [[TBD — EWO]]
- **Dependencies:** EP-5, DATA (indexing)

- **Design required:** Yes
- **Design type:** Existing screen update
- **Design intent:**
  - Add search input to chat section
  - Display search results with message context
- **Design constraints:**
  - Responsive for large result sets
  - Clear indication of which conversation contains the result
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I enter a keyword in the search box  
  When I submit the search  
  Then I see a list of messages containing that keyword

- Given many results  
  When displayed  
  Then results are paginated and load within 2s

---

#### US-EP9-02 — Dispatcher filters conversations by driver

- **User story:**  
  As a **Dispatcher**, I want to filter conversations by driver, so that I can quickly find chats with a specific person.

- **Scope notes:** Filter in conversation list.
- **PRD requirement(s):** FR-10
- **Priority:** Should
- **Owner:** [[TBD — EWO]]
- **Dependencies:** US-EP3-03

- **Design required:** Yes
- **Design type:** Existing screen update
- **Design intent:**
  - Add driver filter dropdown or search to conversation list
- **Design constraints:**
  - Quick access without disrupting list view
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I am viewing the conversation list  
  When I select a driver filter  
  Then only conversations with that driver are shown

---

#### US-EP9-03 — Dispatcher filters conversations by date range

- **User story:**  
  As a **Dispatcher**, I want to filter messages by date range, so that I can find communication from a specific period.

- **Scope notes:** Date picker UI.
- **PRD requirement(s):** FR-10
- **Priority:** Should
- **Owner:** [[TBD — EWO]]
- **Dependencies:** US-EP9-01

- **Design required:** Yes
- **Design type:** Existing screen update
- **Design intent:**
  - Add date range picker to search/filter controls
- **Design constraints:**
  - Standard date picker component
  - Works in combination with keyword search
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given I select a date range  
  When I apply the filter  
  Then only messages within that range are shown

---

---

### EP-10 — Scale & Analytics (Phase 3)

**Epic goal:** Performance optimization for high-volume fleets and adoption analytics dashboard.  
**PRD coverage:** Phase 3 scope

**Instrumentation / measurement notes (epic-level):**
- Track: Customer adoption rate, message volume, system performance under load
- Guardrails: Latency targets maintained at scale
- Reporting: Analytics dashboard (live)

---

#### US-EP10-01 — Performance optimization for high-volume fleets

- **User story:**  
  As an **engineer**, I want to optimize messaging performance for customers with large fleets, so that latency targets are maintained at scale.

- **Scope notes:** Load testing, tuning, infrastructure scaling.
- **PRD requirement(s):** Phase 3 scope
- **Priority:** Should
- **Owner:** [[TBD — API MNG / INFRA]]
- **Dependencies:** EP-1, EP-5

- **Design required:** No
- **Design type:** No UI (logic / backend)
- **Design intent:** N/A
- **Design constraints:** N/A
- **Figma link:** N/A

**Acceptance criteria (Given/When/Then):**
- Given a customer with 500+ drivers  
  When message volume is high  
  Then P95 latency remains <5s

- Given load testing  
  When simulating peak traffic  
  Then system handles load without degradation

---

#### US-EP10-02 — Adoption analytics dashboard

- **User story:**  
  As a **Product Manager**, I want an analytics dashboard showing chat adoption metrics, so that I can track feature success.

- **Scope notes:** Dashboard with key metrics; not a self-service BI tool.
- **PRD requirement(s):** Phase 3 scope
- **Priority:** Should
- **Owner:** [[TBD — DATA]]
- **Dependencies:** EP-5

- **Design required:** Yes
- **Design type:** New screen
- **Design intent:**
  - Display key adoption metrics (Customer Adoption Rate, Chats Initiated, Messages per Week, Active Users)
  - Enable trend analysis
- **Design constraints:**
  - Internal tool; can use existing dashboard framework
  - Refresh at least daily
- **Figma link:** [[TBD]]

**Acceptance criteria (Given/When/Then):**
- Given the dashboard is live  
  When I access it  
  Then I see: Customer Adoption Rate, Chats Initiated, Messages per Week, Active Users

- Given metrics  
  When updated  
  Then dashboard refreshes at least daily

---

---

## 3. Non-Functional Stories

#### NFR-01 — CFR/ANR guardrail monitoring for chat feature

- **Statement:** The chat feature must not degrade Crash-Free Rate (CFR) or increase ANR rates in EW Navigation App.
- **Related to:** EP-2, NFR (Reliability)
- **Owner:** [[TBD — MOBILE APP]]
- **Design required:** No

**Acceptance criteria:**
- Given the chat feature is released  
  When monitoring CFR/ANR  
  Then CFR ≥ pre-release baseline and ANR ≤ pre-release baseline

- Given a regression is detected  
  When CFR drops or ANR increases significantly  
  Then rollback or hotfix is triggered

---

#### NFR-02 — GDPR compliance sign-off

- **Statement:** Message storage and retention must be reviewed and approved by Legal before go-live.
- **Related to:** EP-5, NFR (Compliance)
- **Owner:** [[TBD — Legal / Sergio Barguilla]]
- **Design required:** No

**Acceptance criteria:**
- Given the data retention policy is defined  
  When reviewed by Legal  
  Then sign-off is documented

- Given GDPR requirements  
  When implemented  
  Then right-to-deletion and consent mechanisms are in place (or documented as out of scope for MVP)

---

---

## 4. Dependency & Integration Stories

#### INT-01 — CIAM integration for driver/dispatcher identity

- **Statement:** Chat must use CIAM for driver and dispatcher identity and company linkage.
- **Depends on:** CIAM team
- **Related epics:** EP-2, EP-3
- **Owner:** [[TBD — CIAM]]
- **Design required:** No

**Acceptance criteria:**
- Given a driver opens chat  
  When identity is resolved  
  Then company linkage is confirmed via CIAM

- Given a dispatcher opens chat  
  When driver list is fetched  
  Then only drivers linked to the dispatcher's company are shown (via CIAM)

---

---

## 5. Open Questions & Follow-Ups

- **Story owners:** Who are the leads for MOBILE APP, EWO, API MNG, DATA, INFRA, CIAM?
- **File size limits:** What are the file size and type limits for attachments (EP-6)?
- **Deletion policy:** What happens to messages after 90 days? (Legal input needed for EP-5)
- **Driver research:** Will driver contextual inquiry inform EP-2 UX before finalization?
- **Broadcast scope:** Confirm broadcast is one-way (no group replies) for EP-8.
- **Design resources:** Who is the UX designer assigned to this initiative?
