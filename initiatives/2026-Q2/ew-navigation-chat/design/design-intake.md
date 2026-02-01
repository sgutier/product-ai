# Design Intake — EW Navigation Chat (Phase 1)

**Initiative:** EW Navigation Chat  
**Owner:** Sergio Barguilla  
**Design lead:** [[TBD]]  
**Last updated:** 2026-02-01

**Related artifacts:**
- PRD (`../prd/prd.md`)
- Epic Plan (`../epics/epics.md`)
- User Stories (`../stories/user-stories.md`)

---

## 1. Design Principles & Context

> Reference existing design system and product principles.

- Follow **EW Navigation design system** (mobile)
- Follow **EW Office design system** (web)
- **Driver safety first** — minimal distraction, accessible at stops only
- **Clarity over density** — readable typography, clear hierarchy
- **Consistency** — align with existing Navigation & Office flows
- **Accessibility** — meet platform accessibility standards

_Additional constraints from product context:_
- Drivers value "just works" experience with minimal interaction
- Dispatchers expect responsive, efficient interfaces
- Real-time updates must feel seamless

---

## 2. Stories Requiring Design (by Epic)

> Phase 1 only: EP-1, EP-2, EP-3, EP-4, EP-5

---

### EP-1 — Messaging Infrastructure

**Epic goal:** Establish backend messaging service enabling real-time bidirectional messaging with <5s latency.

_No design-required stories in this epic. All stories are backend/logic only._

---

### EP-2 — Driver Chat Experience

**Epic goal:** Drivers can view incoming messages from dispatchers and send replies within EW Navigation App.

**Platform:** iOS + Android (EW Navigation App)

---

#### US-EP2-01 — Driver views conversation list

**Persona(s):** Company Driver

**Design type:** New screen

**Problem to solve:**  
Drivers need a way to quickly see and access their conversations with dispatchers.

**Design intent:**
- Allow driver to quickly scan and access conversations
- Show unread indicator and most recent message preview

**Design constraints:**
- Minimal distraction — driver-first UX
- Must be accessible when vehicle is stopped
- Consistent with EW Navigation design system
- Empty state required for no conversations

**Out of scope for design:**
- Attachments (Phase 2)
- Search/filtering (Phase 2)

**Related PRD requirement(s):** FR-2

**Figma link:** [[TBD]]

_Open questions for design:_
- Where does chat entry point live in Navigation (tab, menu, icon)?
- How to indicate unread messages without distraction?

---

#### US-EP2-02 — Driver views message thread

**Persona(s):** Company Driver

**Design type:** New screen

**Problem to solve:**  
Drivers need to read the full conversation history with a dispatcher.

**Design intent:**
- Display messages in a clear, chronological thread
- Show sender identity and timestamps

**Design constraints:**
- Scrollable for long conversations
- Readable typography for in-vehicle use (large text, high contrast)
- Consistent with EW Navigation design system
- Performance: must handle 500+ messages smoothly

**Out of scope for design:**
- Attachments display (Phase 2)
- Read receipts display (Phase 2)

**Related PRD requirement(s):** FR-2

**Figma link:** [[TBD]]

---

#### US-EP2-03 — Driver sends a message

**Persona(s):** Company Driver

**Design type:** Existing screen update (add to message thread)

**Problem to solve:**  
Drivers need to reply to dispatchers with text messages.

**Design intent:**
- Add compose area to message thread screen
- Simple text input with send button

**Design constraints:**
- Keyboard handling for mobile
- Minimal interaction while driving (designed for use at stops)
- Clear send affordance
- Character limit indication (if any)

**Out of scope for design:**
- Attachments (Phase 2)

**Related PRD requirement(s):** FR-2

**Figma link:** [[TBD]]

---

#### US-EP2-04 — Driver sees dispatcher context

**Persona(s):** Company Driver

**Design type:** Component update

**Problem to solve:**  
Drivers need to know who is messaging them.

**Design intent:**
- Display dispatcher name in conversation header

**Design constraints:**
- Consistent with EW Navigation header patterns
- Truncation handling for long names

**Out of scope for design:**
- Dispatcher profile/details view

**Related PRD requirement(s):** FR-6

**Figma link:** [[TBD]]

---

---

### EP-3 — Dispatcher Chat Experience

**Epic goal:** Dispatchers can initiate and manage chats with drivers within EW Office web.

**Platform:** Web (EW Office)

---

#### US-EP3-01 — Dispatcher views driver list for chat

**Persona(s):** Dispatcher

**Design type:** Existing screen update

**Problem to solve:**  
Dispatchers need to see which drivers they can message.

**Design intent:**
- Add chat entry point to existing driver list or new chat panel
- Allow quick driver selection for messaging

**Design constraints:**
- Consistent with EW Office design system
- Accessible and filterable for large driver lists (100+ drivers)
- Works with existing driver list component if possible

**Out of scope for design:**
- Driver management (CRUD)
- Broadcast selection (Phase 2)

**Related PRD requirement(s):** FR-1

**Figma link:** [[TBD]]

_Open questions for design:_
- Is chat a standalone section or integrated into existing driver list?
- How to handle offline/unavailable drivers?

---

#### US-EP3-02 — Dispatcher initiates a new chat

**Persona(s):** Dispatcher

**Design type:** Component update

**Problem to solve:**  
Dispatchers need to start a conversation with a driver.

**Design intent:**
- Add "Start Chat" action to driver list/card
- Open chat panel or modal for new conversation

**Design constraints:**
- Consistent with EW Office interaction patterns
- Clear affordance for starting chat vs. other driver actions

**Out of scope for design:**
- Broadcast initiation (Phase 2)

**Related PRD requirement(s):** FR-1

**Figma link:** [[TBD]]

---

#### US-EP3-03 — Dispatcher views conversation list

**Persona(s):** Dispatcher

**Design type:** New screen

**Problem to solve:**  
Dispatchers need to see and manage all their active conversations.

**Design intent:**
- Display conversation list with unread indicators and previews
- Enable quick navigation to active conversations

**Design constraints:**
- Real-time updates when new messages arrive
- Consistent with EW Office design system
- Sortable by most recent message

**Out of scope for design:**
- Search/filtering (Phase 2)
- Broadcast history (Phase 2)

**Related PRD requirement(s):** FR-1

**Figma link:** [[TBD]]

---

#### US-EP3-04 — Dispatcher views message thread

**Persona(s):** Dispatcher

**Design type:** New screen

**Problem to solve:**  
Dispatchers need to read the full conversation with a driver.

**Design intent:**
- Display messages in chronological thread format
- Include compose area for replies

**Design constraints:**
- Scrollable for long conversations
- Real-time updates when new messages arrive
- Consistent with EW Office design system

**Out of scope for design:**
- Attachments (Phase 2)
- Read receipts (Phase 2)

**Related PRD requirement(s):** FR-1

**Figma link:** [[TBD]]

---

#### US-EP3-05 — Dispatcher sends a message

**Persona(s):** Dispatcher

**Design type:** Existing screen update (add to message thread)

**Problem to solve:**  
Dispatchers need to send text messages to drivers.

**Design intent:**
- Add compose area with text input and send button

**Design constraints:**
- Keyboard shortcuts for efficiency (Enter to send, Shift+Enter for newline)
- Clear send affordance
- Multiline input support

**Out of scope for design:**
- Attachments (Phase 2)

**Related PRD requirement(s):** FR-1

**Figma link:** [[TBD]]

---

#### US-EP3-06 — Dispatcher sees driver/vehicle context

**Persona(s):** Dispatcher

**Design type:** Component update

**Problem to solve:**  
Dispatchers need context about who they are messaging.

**Design intent:**
- Display driver name and vehicle info in conversation header or sidebar

**Design constraints:**
- Use existing driver/vehicle data components where possible
- Handle missing vehicle data gracefully

**Out of scope for design:**
- Driver profile editing
- Vehicle management

**Related PRD requirement(s):** FR-6

**Figma link:** [[TBD]]

---

---

### EP-4 — Push Notifications

**Epic goal:** Deliver real-time push notifications for new messages to both drivers and dispatchers.

**Platforms:** iOS, Android (driver), Web (dispatcher)

---

#### US-EP4-01 — Driver receives push notification for new message

**Persona(s):** Company Driver

**Design type:** Component update

**Problem to solve:**  
Drivers need to be alerted to new messages when not actively using the app.

**Design intent:**
- Design notification content (title, body, icon)
- Define deep link behavior to conversation

**Design constraints:**
- Follow iOS and Android notification guidelines
- Clear, actionable notification text
- EW Navigation branding/icon
- Privacy: don't expose full message content in notification preview (optional consideration)

**Out of scope for design:**
- Notification preferences/settings

**Related PRD requirement(s):** FR-4

**Figma link:** [[TBD]]

_Open questions for design:_
- How much message preview to show in notification?
- Should notification group multiple messages from same dispatcher?

---

#### US-EP4-02 — Driver push notification permission handling

**Persona(s):** Company Driver

**Design type:** Component update

**Problem to solve:**  
Drivers need to understand why notifications are important and grant permission.

**Design intent:**
- Design permission prompt UI with clear value proposition
- Design fallback state if permission denied

**Design constraints:**
- Follow platform permission best practices
- Non-intrusive timing (e.g., after first chat action, not on app launch)
- Clear benefit statement

**Out of scope for design:**
- System permission dialogs (platform-controlled)

**Related PRD requirement(s):** FR-4

**Figma link:** [[TBD]]

---

#### US-EP4-03 — Dispatcher receives web notification for new message

**Persona(s):** Dispatcher

**Design type:** Component update

**Problem to solve:**  
Dispatchers need to be alerted to driver replies while working in EW Office.

**Design intent:**
- Design browser notification content
- Add in-app indicator for new messages (badge, sound, etc.)

**Design constraints:**
- Follow browser notification best practices
- Consistent with EW Office notification patterns (if any exist)
- Unread badge on chat section/icon

**Out of scope for design:**
- Notification preferences/settings

**Related PRD requirement(s):** FR-4

**Figma link:** [[TBD]]

---

---

### EP-5 — Message Persistence & History

**Epic goal:** Persist all messages and enable retrieval for at least 90 days.

_No design-required stories in this epic. All stories are backend/logic only._

---

---

## 3. Cross-Cutting Design Considerations

> Apply across multiple stories or epics.

- **Navigation consistency:** Chat entry point and navigation should follow existing patterns in both Navigation and Office
- **Empty states:** All list views need empty state designs (no conversations, no messages)
- **Loading states:** Skeleton loaders or spinners for async data (conversation list, message thread, send in progress)
- **Error states:** Network errors, send failures, offline behavior
- **Real-time updates:** Visual indication when new messages arrive (both platforms)
- **Internationalization:** All strings must support localization
- **Accessibility:** Screen reader support, sufficient contrast, touch target sizes (mobile)

---

## 4. Design Dependencies & Handoffs

| Dependency | Affected Stories | Notes |
|----------|------------------|-------|
| EW Navigation design system | EP-2 (all) | Ensure alignment with existing mobile patterns |
| EW Office design system | EP-3 (all), EP-4 (US-EP4-03) | Ensure alignment with existing web patterns |
| Content / copy | All stories | Notification text, empty states, error messages need copywriting |
| Platform notification guidelines | US-EP4-01, US-EP4-02, US-EP4-03 | iOS HIG, Android Material, Web Notifications API |

---

## 5. Design Completion Criteria

Design work for Phase 1 is considered complete when:

- [ ] All listed stories have linked Figma frames
- [ ] Designs meet stated intent and constraints
- [ ] Empty states, loading states, and error states are covered
- [ ] Mobile designs reviewed for driver safety (minimal distraction)
- [ ] Web designs reviewed for EW Office consistency
- [ ] Notification designs reviewed for platform compliance
- [ ] Open design questions are resolved or documented
- [ ] Designs are ready for handoff to MOBILE APP and EWO teams

---

## 6. Open Questions & Follow-Ups

- **Design lead:** Who is assigned as UX designer for this initiative?
- **Chat entry point (mobile):** Where does chat live in EW Navigation? (tab, menu, icon)
- **Chat entry point (web):** Is chat a standalone section or integrated into driver list?
- **Unread indicators:** How to show unread without distracting drivers?
- **Notification preview:** How much message content to show in push notifications?
- **Driver research:** Will driver contextual inquiry inform UX before finalization?
