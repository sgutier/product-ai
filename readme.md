# Product Initiative & AI-Assisted Design Workflow

This repository contains a **structured, end-to-end workflow** for defining, discovering, designing, and delivering product initiatives, with optional **AI assistance** (Cursor + Gemini) used in a **controlled, auditable way**.

The system is designed for **corporate product organizations** where:
- Traceability matters
- Scope must be controlled
- AI should assist, not invent

---

## High-Level Workflow Overview

Birth Certificate
→ Discovery Summary
→ PRD
→ Epics
→ User Stories
→ Design Intake (Phase 1 only)
→ AI-assisted Design (optional, constrained)
→ Delivery Decomposition

Each step produces **explicit artifacts**, stored under the initiative directory.

---

## Core Directory Structure

/
├── README.md                     ← this file
├── product-context/              ← stable product knowledge
├── design-knowledge/              ← reusable UI reference screens
├── initiatives/
│   └── {YYYY-QX}/{initiative}/
│       ├── birth-certificate.md
│       ├── discovery/
│       │   └── discovery-summary.md
│       ├── prd/
│       │   └── prd.md
│       ├── epics/
│       │   └── epics.md
│       ├── stories/
│       │   └── user-stories.md
│       └── design/
│           ├── design-intake.md
│           └── {EP-ID}/
│               ├── brief.md
│               ├── gemini-prompt.md
│               ├── reference-screens/
│               └── outputs/
└── .cursor/
└── commands/
└── design/

---

## Artifact Responsibilities

### 1. Birth Certificate (`birth-certificate.md`)
**Purpose:**  
Single mandatory entry point for any initiative.

**Defines:**
- Problem & hypothesis
- Business impact
- Scope & non-scope
- Phasing
- Dependencies
- Decision intent

No discovery, PRD, or delivery work happens without this.

---

### 2. Discovery Summary (`discovery-summary.md`)
**Purpose:**  
Capture validated (or invalidated) assumptions from discovery.

**Defines:**
- What was learned
- What assumptions hold
- What risks remain
- What is explicitly NOT validated

Used as the main input for PRD creation.

---

### 3. PRD (`prd/prd.md`)
**Purpose:**  
Translate discovery into **clear, testable requirements**.

**Defines:**
- Functional requirements (FRs)
- Non-functional requirements
- Constraints
- Success metrics
- Explicit in/out scope

PRD is authoritative for Epics and Stories.

---

### 4. Epics (`epics/epics.md`)
**Purpose:**  
Break the PRD into **delivery-sized problem chunks**.

**Defines:**
- Epic goals
- Phase alignment
- Dependencies
- Success criteria

Epics do not design or implement — they structure intent.

---

### 5. User Stories (`stories/user-stories.md`)
**Purpose:**  
Make work executable by delivery teams.

**Defines:**
- User-facing outcomes
- Acceptance criteria (Given / When / Then)
- Dependencies
- Instrumentation notes
- Explicit flag: **Design required (Yes/No)**

Stories are Jira-ready.

---

### 6. Design Intake (`design/design-intake.md`)
**Purpose:**  
Aggregate **Phase 1 only** design work.

**Defines:**
- Which stories require design
- Design intent & constraints
- Safety considerations
- Platform scope

This document is **tool-agnostic** and does NOT assume Figma or AI.

---

## Design Knowledge (Reusable)

### `design-knowledge/`
**Purpose:**  
Stable, long-lived repository of **reference UI screens**.

**Structure:**

design-knowledge/
├── android/
│   └── navigation/
│       ├── screen.png
│       └── screen.json
└── ios/
└── navigation/
├── screen.png
└── screen.json

Each screen has:
- PNG image (visual reference)
- JSON metadata (semantic meaning, constraints, patterns)

These files are **never modified by initiatives**.

---

## AI-Assisted Design (Optional, Constrained)

AI is used **only after intent is fully defined** and **only for Phase 1**.

### Per-Epic Design Folder

/design/{EP-ID}/
├── brief.md
├── gemini-prompt.md
├── reference-screens/
└── outputs/

#### `brief.md`
- Epic goal
- Stories in scope
- Persona
- Design intent
- Constraints
- Out of scope
- Expected outputs

Authoritative input for any design work.

---

#### `gemini-prompt.md`
A **strict, derivation-only prompt** that:

- Forces reuse of reference screens
- Forbids invention
- Requires citation of reference filenames
- Requires explicit admission if requirements cannot be met

AI outputs are treated as **proposals**, not decisions.

---

#### `reference-screens/`
Small, curated subset (3–5 max) copied from `design-knowledge/`:
- PNG + JSON
- Platform-specific
- Relevant to the epic

---

#### `outputs/`
Stores:
- AI-generated proposals
- Design notes
- Review artifacts

Nothing here is considered final until reviewed.

---

## Cursor Commands

All automation lives under:

.cursor/commands/

Key commands created today include:

- `create-birth-certificate`
- `create-discovery-summary`
- `create-prd`
- `create-epics`
- `create-user-stories`
- `design/create-design-intake`
- `design/create-gemini-context`

Commands:
- Never contain product data
- Only generate or structure artifacts
- Enforce scope, discipline, and sequencing

---

## Key Principles of the System

- **Intent before execution**
- **Phase 1 only for design**
- **AI derives, never invents**
- **Design knowledge is reusable**
- **Outputs are auditable**
- **Context is minimized intentionally**

This system favors **clarity, control, and learning speed** over automation for its own sake.

---

## How to Use This README

- As onboarding for collaborators
- As a guardrail against process drift
- As documentation for why artifacts exist
- As justification for AI usage in a corporate environment

---

_End of README_
