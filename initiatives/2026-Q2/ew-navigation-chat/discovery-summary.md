# Discovery Summary — EW Navigation Chat

**Initiative:** EW Navigation Chat  
**Discovery owner:** Sergio Barguilla  
**Discovery window:** MOCK (no real dates — assumptions-based)  
**Last updated:** 2026-02-01

**Related artifacts:**
- Birth Certificate (`birth-certificate.md`)
- Discovery Learning Plan (`discovery-learning-plan.md`)
- Discovery Review (Thinking Agent output — inline)

---

> **Note:** This is an assumptions-based summary created to unblock PRD creation and test the product workflow. No real discovery activities have been executed. Discovery must be completed before delivery commitment.

---

## 1. Discovery Objectives Recap

> What we set out to learn.

- Validate that dispatchers will shift from WhatsApp/phone to in-app chat
- Define the minimum feature set required for MVP adoption (text only vs. attachments)
- Validate that drivers will engage with chat during transport execution
- Confirm technical feasibility of real-time messaging at acceptable latency and cost
- Understand GDPR / compliance implications for message storage

---

## 2. Activities Completed

| Activity | Method | Owner | Status |
|--------|--------|-------|--------|
| Dispatcher Interviews | Semi-structured interviews | [[TBD]] | Not done (MOCK) |
| Driver Contextual Inquiry | Ride-along / observation | [[TBD]] | Not done (MOCK) |
| Competitive Feature Audit | Desk research | [[TBD]] | Not done (MOCK) |
| Architecture Spike | Technical spike / PoC | [[TBD]] | Not done (MOCK) |
| Data Privacy & Compliance Review | Legal consultation | [[TBD]] | Not done (MOCK) |
| Lo-Fi Prototype Test | Clickable prototype | [[TBD]] | Not done (MOCK) |

---

## 3. Key Learnings (Evidence-Based)

> Only include learnings supported by evidence.

### Value
- Dispatchers will adopt in-app chat over WhatsApp → **Inconclusive** (assumption based on market research and strategic intent)
- Chat is "one of the most requested features" → **Some evidence** (cited in business case, but quantification missing)

**Evidence:** Business case document (Márton Szabó, 2025-08-25); competitive landscape analysis (desk research, not yet executed)

### Usability
- Drivers can safely engage with chat during transport → **Inconclusive**
- Chat UI can be simple enough for drivers who value "just works" experience → **Inconclusive**

**Evidence:** None (requires driver contextual inquiry)

### Feasibility
- Real-time messaging at <5s latency is achievable → **Inconclusive**
- Push notifications work reliably across driver devices → **Inconclusive**
- Cross-team dependencies can be coordinated → **Inconclusive**

**Evidence:** None (requires architecture spike)

### Viability
- Messaging infrastructure cost is acceptable at scale → **Inconclusive**
- No major GDPR / data privacy blockers → **Inconclusive**

**Evidence:** None (requires Legal review)

---

## 4. Assumptions Status

| Assumption | Risk Area | Status | Evidence |
|-----------|-----------|--------|----------|
| Dispatchers will shift from WhatsApp/phone to in-app chat | Value | Inconclusive | Business case (qualitative); no direct user validation |
| Drivers will respond to in-app messages during transport | Value / Usability | Inconclusive | None |
| Text-only messaging is sufficient for MVP | Value | Inconclusive | None |
| Attachments are required for Phase 2 adoption | Value | Inconclusive | None |
| Real-time delivery (<5s latency) is technically achievable | Feasibility | Inconclusive | None |
| Messaging infrastructure cost is acceptable at scale | Viability | Inconclusive | None |
| No major GDPR / data privacy blockers | Viability | Inconclusive | None |

---

## 5. Impact on Hypothesis

**Original hypothesis (summary):**  
If we deliver in-app dispatcher-driver messaging integrated between EW Office and EW Navigation, dispatchers and drivers will adopt it as their primary communication channel during transport execution, driving 20%+ customer adoption by end of Q4 2026.

**What changed:**
- Nothing changed — hypothesis remains unchanged

**Updated hypothesis (if applicable):**  
Unchanged. No evidence to validate or invalidate at this stage.

---

## 6. Impact on Scope & Direction

> What we are now more confident about — and what changed.

**In scope (confirmed):**
- 1:1 text messaging between dispatcher (Office) and driver (Navigation)
- Push notifications for new messages
- Message history persistence (90 days)
- Phase 1 MVP: text-only; Phase 2: attachments, read receipts, broadcast

**Out of scope (confirmed or newly added):**
- Video calling / voice messages
- Driver-to-driver messaging
- WhatsApp / Telegram integration
- Offline-first messaging
- Embedded / OEM navigation users

**New constraints or considerations:**
- None identified (discovery not executed)

---

## 7. Metrics & Success Criteria Revisited

**Primary metric:** Customer Adoption Rate — % of EW Office customers with at least one active chat per month  
- Baseline: 0% (feature does not exist)
- Target: 20% of EW Office customers with active chats by end of Q4 2026

**Guardrails:**
- Crash-Free Rate (CFR) ≥ current baseline
- App Store Rating ≥ current baseline

**Changes after discovery:**  
- None — targets remain aspirational pending validation

---

## 8. Residual Risks

> Risks that remain after discovery.

| Risk Area | Risk | Why It Remains | Next Mitigation |
|---------|------|----------------|-----------------|
| Value | Dispatchers may not shift from WhatsApp | No user validation conducted | Execute dispatcher interviews before delivery commitment |
| Value | MVP scope may be wrong (text vs. attachments) | No user validation conducted | Validate minimum viable feature set with users |
| Usability | Drivers may find chat distracting or inaccessible | No driver research conducted | Execute driver contextual inquiry |
| Feasibility | Real-time messaging latency/scalability unknown | No architecture spike conducted | Complete technical spike before build commitment |
| Viability | GDPR / data privacy implications unknown | No Legal review conducted | Complete Legal consultation before go-live |

---

## 9. Readiness Assessment

Based on discovery outcomes, this initiative is:

- [ ] Ready for PRD
- [x] Ready for PRD with constraints
- [ ] Requires additional discovery
- [ ] Should be parked
- [ ] Should be killed

**Rationale (1–2 sentences):**  
This PRD is created to structure solution thinking and delivery options. All key assumptions remain unvalidated — discovery must be executed before delivery commitment. PRD proceeds on assumption-based planning; validation gates must be built into delivery phases.

---

## 10. Required Updates to Birth Certificate

> Explicitly list what must be updated.

- Section(s) to update:
  - Product Risks table (add links once discovery artifacts exist)
  - Discovery Artifacts table (add links once produced)
  - Dependencies section (add owners and MDs once scoped)
  - Stakeholders section (add names once confirmed)
- Owner(s): Sergio Barguilla
- Deadline: Before Phase 1 delivery commitment

---

## 11. Decision & Ownership

**Decision owner:** Sergio Barguilla  
**Decision date:** 2026-02-01

**Final decision:**
- [x] Proceed to PRD (non-committal, planning-only)
- [ ] Narrow scope and re-review
- [ ] Continue discovery
- [ ] Park
- [ ] Kill

---

## Appendix: Validation Gates Required Before Delivery

Before committing to delivery, the following must be completed:

1. **Dispatcher interviews** — Validate adoption intent (≥5/8 express intent to switch)
2. **Driver contextual inquiry** — Validate driver willingness to engage with chat
3. **Architecture spike** — Confirm <5s latency, acceptable cost, infrastructure approach
4. **Legal review** — Confirm no GDPR / compliance blockers
5. **MVP scope confirmation** — Text-only sufficient, or attachments required earlier
