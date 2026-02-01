# Design Brief — EP-2

**Initiative:** EW Navigation Chat  
**Epic:** EP-2 — Driver Chat Experience  
**Platform:** iOS  
**Phase:** Phase 1  
**Last updated:** 2026-02-01

---

## Objective

Enable drivers to view incoming messages from dispatchers and send replies within the EW Navigation App. This is the core driver-facing chat experience for Phase 1.

---

## Stories in Scope

| Story ID | Title | Design Type |
|----------|-------|-------------|
| US-EP2-01 | Driver views conversation list | New screen |
| US-EP2-02 | Driver views message thread | New screen |

**Note:** US-EP2-03 (Driver sends a message) and US-EP2-04 (Driver sees dispatcher context) are screen updates and component updates that will be incorporated into the above screens. The new screens must accommodate these requirements.

---

## User / Persona

**Company Driver**

- Professional truck driver linked to a fleet/company
- Uses EW Navigation for daily route guidance
- Values "just works" experience with minimal interaction
- Interacts with app primarily when vehicle is stopped
- Needs quick access to dispatcher communication during transport execution

---

## Design Intent

### US-EP2-01 — Conversation List
- Allow driver to quickly scan and access conversations
- Show unread indicator and most recent message preview
- Provide clear entry point from main navigation

### US-EP2-02 — Message Thread
- Display messages in a clear, chronological thread
- Show sender identity (dispatcher name) and timestamps
- Include compose area for replies (simple text input + send button)

---

## Constraints

### Safety & Interaction
- **Driver safety first** — minimal distraction
- **Accessible at stops only** — not for use while driving
- **Low interaction level** — large touch targets, clear affordances
- Must not interfere with active navigation (nav-navigating screen)

### Visual & Platform
- Consistent with **EW Navigation iOS design system**
- Readable typography for in-vehicle use (large text, high contrast)
- Scrollable for long conversations (500+ messages)
- Empty state required for no conversations

### Performance
- Must not impact app CFR (Crash-Free Rate) or increase ANR
- Smooth scrolling and real-time updates

---

## Out of Scope

- Attachments (images, PDFs) — Phase 2
- Read receipts display — Phase 2
- Search/filtering conversations — Phase 2
- Android platform — separate context
- Dispatcher-facing UI (EW Office) — separate context
- Admin or configuration flows

---

## Reference Screens (in `screens/` folder)

| # | Screen | Relevance to EP-2 |
|---|--------|-------------------|
| 01 | nav-landing-page | Baseline layout, entry point patterns |
| 02 | nav-search | List-based interaction, input patterns |
| 03 | nav-settings | Grouped list patterns, navigation depth |
| 04 | nav-settings-2 | Nested navigation, secondary content |
| 05 | nav-planned-route | Content screen layout, summary patterns |
| 06 | nav-navigating | Safety-critical reference (do not interfere) |

---

## Expected Output

1. **Conversation List Screen** — primary proposal
   - Entry point from navigation
   - List of conversations with unread indicators
   - Empty state variant

2. **Message Thread Screen** — primary proposal
   - Chronological message display
   - Dispatcher identity in header
   - Compose area with text input and send button

3. **Optional edge-case variants:**
   - Empty state (no conversations)
   - Long conversation (scroll behavior)
   - Keyboard open state (compose)

---

## Open Questions for Design

- Where does chat entry point live in Navigation (tab, menu, icon)?
- How to indicate unread messages without distraction?
- How to handle offline state or message send failure?
