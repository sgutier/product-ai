# Product Initiative & AI-Assisted Workflow

This readme.md file has been created by Sergio Barguilla

This repository contains a **structured, end-to-end workflow** for defining, discovering, designing, and delivering product initiatives, with optional **AI assistance** (Cursor + Gemini) used in a **controlled, auditable way**.

The system is designed for **corporate product organizations** where:
- Traceability matters
- Scope must be controlled
- AI should assist, not invent

---

## High-Level Workflow Overview

```
Birth Certificate
→ Discovery Review (Thinking Agent)    ← challenges assumptions, surfaces decision points
→ Discovery Learning Plan              ← planned activities to validate assumptions
→ Discovery Summary                    ← validated/invalidated findings
→ PRD
→ Epics
→ User Stories
→ Design Intake (Phase 1 only)
→ AI-assisted Design (optional, constrained)
→ Delivery Decomposition
→ Jira Import CSV
```

Each step produces **explicit artifacts**, stored under the initiative directory.

---

## Core Directory Structure

```
/
├── readme.md                          ← this file
├── product-context/                   ← stable product knowledge (personas, strategy, metrics)
├── research/                          ← user research by persona and date
│   ├── master-summary.md             ← aggregated durable insights across all personas
│   ├── driver/                        ← driver research by date
│   ├── owner/                         ← owner research by date
│   ├── dispatcher/                    ← dispatcher research by date
│   └── Monetization/                  ← monetization models and analysis
├── design-knowledge/                  ← reusable UI reference screens (PNG + JSON)
├── design-ai-context/                 ← per-epic AI design context (briefs, prompts, references)
├── initiatives/
│   └── {YYYY-QX}/{initiative}/
│       ├── birth-certificate.md
│       ├── discovery-review.md        ← output of Discovery Thinking Agent
│       ├── discovery-learning-plan.md ← planned discovery activities
│       ├── discovery-summary.md       ← validated/invalidated findings
│       ├── prd/
│       │   └── prd.md
│       ├── epics/
│       │   └── epics.md
│       ├── stories/
│       │   └── user-stories.md
│       ├── jira/
│       │   └── jira-import.csv
│       ├── design/
│       │   └── design-intake.md
│       └── implementation/            ← reference implementations (optional)
└── .cursor/
    ├── agents/                        ← autonomous agents
    │   ├── product-discovery-thinking-agent.md
    │   └── delivery-decomposition-agent.md
    └── commands/                      ← step-by-step artifact generators
        ├── create-birth-certificate.md
        ├── create-discovery-learning-plan.md
        ├── create-discovery-summary.md
        ├── create-prd.md
        ├── create-epics.md
        ├── create-user-stories.md
        ├── create-jira-import-csv.md
        ├── design/
        │   ├── create-design-intake.md
        │   └── create-gemini-context.md
        └── research/
            └── create-research-summary.md
```

---

## Artifact Responsibilities

### 1. Birth Certificate (`birth-certificate.md`)
**Purpose:** Single mandatory entry point for any initiative.

**Defines:**
- Problem, hypothesis, and "because" logic
- Revenue impact (with explicit assumptions)
- Scope, non-scope, and phasing
- Dependencies with team codes, MDs, and owners
- Product risks (Value, Usability, Feasibility, Viability)
- Stakeholders
- Decision intent

**Created by:** `/create-birth-certificate` command (interactive questionnaire)

No discovery, PRD, or delivery work happens without this.

---

### 2. Discovery Review (`discovery-review.md`)
**Purpose:** Challenge assumptions and surface what must be learned before PRD.

**Defines:**
- Explicit and implicit assumptions (grouped by risk type)
- Hypothesis stress test (weak logic, hidden dependencies)
- Top 3 ranked risks
- **Decision points** — choices between mutually exclusive options that are embedded as givens but require deliberate resolution
- Discovery gaps by risk area
- Learning objectives (framed as questions, not solutions)
- Readiness signal (proceed / clarify / reconsider)

**Created by:** `product-discovery-thinking-agent` (autonomous agent)

The agent reads the birth certificate, product context, and research, then produces a structured critical review. It does not propose solutions — it identifies what could go wrong and what decisions remain unmade.

**Decision Point Mapping** (added Feb 2026): The agent now identifies decisions that the birth certificate treats as resolved but are actually open choices (e.g., "per truck" vs "per driver" licensing). For each decision point, it surfaces the options, what depends on the choice, and how to inform it.

---

### 3. Discovery Learning Plan (`discovery-learning-plan.md`)
**Purpose:** Translate discovery gaps into a focused plan of learning activities.

**Defines:**
- Learning objectives (from discovery review)
- Assumptions being tested (with risk area and impact if wrong)
- Planned activities (method, participants, owner, effort, dependencies)
- Success and failure signals per learning objective
- Decision criteria (proceed / narrow / iterate / park)

**Created by:** `/create-discovery-learning-plan` command

This is the last mandatory step before PRD creation.

---

### 4. Discovery Summary (`discovery-summary.md`)
**Purpose:** Capture validated (or invalidated) assumptions from discovery.

**Defines:**
- What was learned
- What assumptions hold
- What risks remain
- What is explicitly NOT validated

**Created by:** `/create-discovery-summary` command

Used as the main input for PRD creation.

---

### 5. PRD (`prd/prd.md`)
**Purpose:** Translate discovery into clear, testable requirements.

**Defines:**
- Functional requirements (FRs)
- Non-functional requirements
- Constraints
- Success metrics
- Explicit in/out scope

**Created by:** `/create-prd` command

PRD is authoritative for Epics and Stories.

---

### 6. Epics (`epics/epics.md`)
**Purpose:** Break the PRD into delivery-sized problem chunks.

**Defines:**
- Epic goals and outcomes
- Phase alignment
- Dependencies and cross-team matrix
- Success criteria and exit criteria
- Sequencing and parallelization opportunities

**Created by:** `/create-epics` command

Epics do not design or implement — they structure intent.

---

### 7. User Stories (`stories/user-stories.md`)
**Purpose:** Make work executable by delivery teams.

**Defines:**
- User-facing outcomes
- Acceptance criteria (Given / When / Then)
- Dependencies
- Instrumentation notes
- Design required flag (Yes/No) with design type, intent, and constraints

**Created by:** `/create-user-stories` command

Stories are Jira-ready.

---

### 8. Jira Import (`jira/jira-import.csv`)
**Purpose:** Export stories to Jira for delivery tracking.

**Created by:** `/create-jira-import-csv` command

---

### 9. Design Intake (`design/design-intake.md`)
**Purpose:** Aggregate **Phase 1 only** design work.

**Defines:**
- Which stories require design (by epic)
- Design intent and constraints per story
- Safety considerations
- Platform scope
- Cross-cutting design considerations (empty states, loading, error, accessibility)
- Design completion criteria

This document is **tool-agnostic** and does NOT assume Figma or AI.

**Created by:** `/design/create-design-intake` command

---

## Research (`research/`)

### `research/master-summary.md`
Aggregated durable insights across all personas. Append-only — never delete historical insights.

### Per-persona folders
```
research/
├── driver/{date}/
│   ├── summary.md
│   └── structured-insights.md
├── owner/{date}/
│   └── ...
├── dispatcher/{date}/
│   └── ...
└── Monetization/
    └── *.xlsx, *.pdf (impact models, feature definitions)
```

Research is referenced by the discovery thinking agent and by commands that create artifacts. If no research exists for a persona, agents flag this explicitly.

**Created by:** `/research/create-research-summary` command

---

## Design Knowledge (Reusable)

### `design-knowledge/`
Stable, long-lived repository of reference UI screens.

Each screen has:
- PNG image (visual reference)
- JSON metadata (semantic meaning, constraints, UI patterns)

These files are **never modified by initiatives**.

### `design-ai-context/{platform}-{epic-id}/`
Per-epic design context for AI-assisted design:

```
design-ai-context/ios-ep-2/
├── brief.md               ← epic goal, stories, constraints, expected outputs
├── gemini-prompt.md        ← strict derivation-only prompt
├── reference-screens/      ← curated subset (3–5) from design-knowledge/
└── design-response.md      ← AI-generated design proposal
```

**Created by:** `/design/create-gemini-context` command

---

## AI-Assisted Design (Optional, Constrained)

AI is used **only after intent is fully defined** and **only for Phase 1**.

#### `brief.md`
- Epic goal, stories in scope, persona
- Design intent and constraints
- Out of scope
- Expected outputs

Authoritative input for any design work.

#### `gemini-prompt.md`
A strict, derivation-only prompt that:
- Forces reuse of reference screens
- Forbids invention of new patterns
- Requires citation of reference filenames
- Requires explicit admission if requirements cannot be met

AI outputs are treated as **proposals**, not decisions.

---

## Agents

Autonomous agents that read context and produce structured thinking.

### `product-discovery-thinking-agent`
**Role:** Critical reviewer. Challenges assumptions, surfaces risks, identifies decision points.

**Reads:** Birth certificate, product context, research (mandatory).

**Produces:** `discovery-review.md` with:
- Assumption mapping (Value, Usability, Feasibility, Viability)
- Hypothesis stress test
- Top 3 ranked risks
- Decision point mapping (choices between mutually exclusive options)
- Discovery gaps
- Learning objectives
- Readiness signal

**Principle:** Treat every initiative as guilty until proven viable.

### `delivery-decomposition-agent`
**Role:** Break validated initiatives into delivery structure.

---

## Commands

All automation lives under `.cursor/commands/`. Commands:
- Never contain product data
- Only generate or structure artifacts
- Enforce scope, discipline, and sequencing
- Reference product context and research before generating output

| Command | Input | Output |
|---------|-------|--------|
| `/create-birth-certificate` | Interactive questionnaire | `birth-certificate.md` |
| `/product-discovery-thinking-agent` | Birth certificate + context | `discovery-review.md` |
| `/create-discovery-learning-plan` | Birth certificate + discovery review | `discovery-learning-plan.md` |
| `/create-discovery-summary` | Learning plan + evidence | `discovery-summary.md` |
| `/create-prd` | Discovery summary | `prd/prd.md` |
| `/create-epics` | PRD | `epics/epics.md` |
| `/create-user-stories` | PRD + epics | `stories/user-stories.md` |
| `/create-jira-import-csv` | User stories | `jira/jira-import.csv` |
| `/design/create-design-intake` | User stories (Phase 1) | `design/design-intake.md` |
| `/design/create-gemini-context` | Design intake + design knowledge | `design-ai-context/{epic}/` |

---

## Current Initiatives

### 2026-Q2

| Initiative | Status | Artifacts |
|-----------|--------|-----------|
| **EW Navigation Chat** | Full workflow complete | Birth certificate, discovery learning plan, discovery summary, PRD, epics, user stories, design intake, Jira CSV |
| **Roll Out Subscription 10 Markets** | Discovery in progress | Birth certificate, discovery review, discovery learning plan |
| **EW Office Navigation Fleet Licensing** | Discovery review complete | Birth certificate, discovery review |

---

## Key Principles

- **Intent before execution** — no building without a birth certificate
- **Discovery before commitment** — validate assumptions before PRD
- **Decisions before design** — resolve model choices before specifying solutions
- **Phase 1 only for design** — design what you're building now, not later
- **AI derives, never invents** — constrained to existing patterns and evidence
- **Research grounds everything** — agents and commands reference persona research
- **Design knowledge is reusable** — reference screens are stable, not per-initiative
- **Outputs are auditable** — every artifact traces to its inputs

This system favors **clarity, control, and learning speed** over automation for its own sake.

---

## How to Use This README

- As onboarding for collaborators
- As a guardrail against process drift
- As documentation for why artifacts exist
- As justification for AI usage in a corporate environment

---

_Last updated: 2026-02-02_
