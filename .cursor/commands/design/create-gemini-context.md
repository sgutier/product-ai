# design/create-gemini-context

You are helping the user prepare a **constrained, auditable design context** for AI-assisted design (e.g. Gemini).

This command:
- Assembles context
- Writes it into the **initiative**
- Prepares a **derivation-only** design prompt

It does NOT generate designs.

---

## Your Goal

1. Prepare a **design brief** for a single Epic (Phase 1 only)
2. Assemble a **bounded set of reference screens** (platform-specific)
3. Generate a **strict Gemini prompt** that forces derivation from references
4. Write everything into the initiative under `/design/{epic-id}/`

---

## Required Inputs (ask in ONE message)

Ask the user to confirm:

1. **Initiative name**
2. **Epic ID** (e.g. EP-2)
3. **Platform** (`android` or `ios`)
4. **Design output type**
   - New screen
   - Screen update
   - Component update
5. **Max reference screens** (default = 5)

Do not proceed until confirmed.

---

## Preconditions (HARD GATE)

Confirm access to:

- `design/design-intake.md`
- `epics/epics.md`
- `stories/user-stories.md`
- `/design-knowledge/{platform}/`
- `@product-context/00-index.md` (principles only)

If any are missing, STOP.

---

## Scope Rules (NON-NEGOTIABLE)

- Phase 1 ONLY
- Single Epic ONLY
- Single Platform ONLY
- 3–5 reference screens strongly preferred
- Absolute max = 6

Do NOT include:
- Other epics
- Other platforms
- Future phases
- Full PRD or discovery docs

---

## Folder & File Creation Rules

Create (if missing):

/initiatives/{YYYY-QX}/{initiative-name}/design/{epic-id}/
├── brief.md
├── gemini-prompt.md
├── reference-screens/
└── outputs/

- Copy selected screens + metadata into `reference-screens/`
- Do NOT modify `/design-knowledge`
- `outputs/` remains empty at this stage

---

## How to Build `brief.md`

Source of truth:
- `design-intake.md` (Epic section only)
- User stories (Phase 1 only)

Include:
- Epic goal
- Stories in scope
- Persona
- Design intent
- Constraints
- Out of scope
- Expected outputs

No invention allowed.

---

## How to Build `gemini-prompt.md` (CRITICAL)

The prompt MUST:
- Explicitly state that **reference screens are authoritative**
- Forbid invention
- Require citation of reference filenames
- Require admission if requirements cannot be met with existing patterns

---

## Output Rules (STRICT)

Produce ONLY:
- `brief.md`
- `gemini-prompt.md`

Do NOT generate designs.
Do NOT summarize.
Do NOT explain your reasoning.

---

<!-- ======================= -->
<!-- BRIEF TEMPLATE -->
<!-- ======================= -->

# Design Brief — [[Epic ID]]

**Initiative:** [[Initiative name]]  
**Epic:** [[Epic ID — Epic name]]  
**Platform:** [[Android / iOS]]  
**Phase:** Phase 1  
**Last updated:** [[YYYY-MM-DD]]

## Objective
[[What this epic enables for the user]]

## Stories in Scope
- [[US-…]] — [[Title]]
- [[US-…]] — [[Title]]

## Persona
[[Primary persona]]

## Design Intent
- [[Intent]]
- [[Intent]]

## Constraints
- Safety & interaction constraints
- Platform constraints
- Offline / CFR / ANR constraints (if applicable)

## Out of Scope
- Future phases
- Other platforms
- Advanced features

## Expected Output
- Primary screen proposal
- Optional edge-case variant
