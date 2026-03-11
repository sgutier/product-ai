# SERGIO_AGENT_ARCHITECTURE.md

Agent topology and model routing for Sergio Barguilla’s AI system (OpenClaw / Cursor / local + frontier models).

Purpose:
Define an agent architecture that:
- scales across many workflows (product, research, content, automation)
- minimizes token burn (especially on frontier models)
- enforces consistent quality and writing style
- keeps “research” and “reasoning” cleanly separated

This document is implementation-agnostic: it can be adapted to OpenClaw, Cursor workflows, Discord-based coordination, or other agent orchestrators.

---

# 0. Operating Principles

1) Separate concerns:
- Research ≠ reasoning
- Reasoning ≠ drafting
- Drafting ≠ publishing

2) Optimize for token efficiency:
- Use small/cheap models for extraction + summarization
- Escalate to premium models only for synthesis or complex reasoning
- Never pass raw dumps into premium models; pass compressed summaries

3) Standardize outputs:
- Use Sergio’s writing style and decision frameworks by default
- Produce reusable artifacts (Markdown, Jira-ready, Confluence-ready)

4) Prefer deterministic pipelines:
- “Plan → Collect → Compress → Decide → Draft → Review → Publish”
- Keep each stage small and testable

---

# 1. Recommended Agent Topology

## A. Orchestrator Layer (1 agent)

### 1) Chief-of-Staff (CoS) Agent
Role:
- interprets Sergio’s request
- decomposes into tasks
- assigns to specialists
- integrates outputs into final deliverable

Key behaviors:
- ask clarifying questions only if absolutely necessary
- otherwise proceed with best-effort assumptions, clearly labeled
- enforce the “compressed handoff” rule (see Section 4)

Inputs:
- Sergio’s request
- existing knowledge files (Profile, OS, Writing Style, Decision Frameworks, Prompt Library)

Outputs:
- final answer / artifact
- (optional) execution plan + task list
- (optional) a “next steps” short list

---

## B. Specialist Layer (4–8 agents)

### 2) Research Agent
Role:
- gather external information (X, LinkedIn, web, docs)
- extract relevant facts + trends
- produce structured “evidence-backed” summaries

Output format (mandatory):
- Key insights (bullets)
- Supporting evidence (links/refs or citations in your system)
- Implications
- Open questions
- Confidence level (low/med/high)

Rules:
- never editorialize beyond implications
- never produce long raw dumps

---

### 3) Summarizer / Compressor Agent
Role:
- convert raw research into a compact, high-signal brief
- remove redundancy
- keep only decision-relevant info

Output format (mandatory):
- 10-bullet executive brief (max)
- 3 key numbers/metrics (if any)
- 3 risks
- 3 opportunities
- “What changed since last time?” (if applicable)

This agent is the “token firewall.”

---

### 4) Strategy / Product Advisor Agent
Role:
- analyze product decisions using Sergio’s frameworks
- propose options, trade-offs, KPIs, and sequencing

Output format (mandatory):
- Context
- Problem
- Constraints
- Options (A/B/C)
- Trade-offs
- Recommendation
- KPIs + measurement plan
- Risks + mitigations

---

### 5) Technical Architect / Builder Agent
Role:
- design technical architectures and implement scripts/tools
- create PRDs/tech specs for automation pipelines
- propose secure key management patterns, API separation, cron strategy, etc.

Output format (mandatory):
- Architecture diagram (ASCII ok)
- Components + responsibilities
- Data flows
- Failure modes
- Security considerations
- Implementation plan (phases)
- Code (when requested) in copy-paste-ready blocks

---

### 6) Executive Writer Agent
Role:
- rewrite and draft stakeholder messages, memos, slides text
- enforce Sergio’s writing style

Output format:
- Version A (concise)
- Version B (more strategic)
- Optional: “one-liner TL;DR”

Rules:
- keep paragraphs short
- highlight constraints + trade-offs
- avoid fluff

---

### 7) Content / LinkedIn Agent
Role:
- create Sergio-style LinkedIn posts and long-form content
- convert insights into narrative

Output format:
- 3 post variants (short / medium / punchy)
- Hook options (3)
- CTA options (2)
- Hashtags (optional, minimal)

Rules:
- no motivational clichés
- insight-first, not promotional

---

### 8) QA / Critic Agent (optional but powerful)
Role:
- red-team the output for weak logic, missing trade-offs, vague claims
- enforce quality gates before delivery/publishing

Output format:
- Issues found
- Suggested fixes
- “Confidence to ship” (0–10)

---

## C. Distribution Layer (1 agent)

### 9) Posting / Publisher Agent
Role:
- publish approved content
- schedule
- cross-post
- ensure formatting compliance per platform

Hard rule:
- do nothing without explicit “approved” status from Sergio.

---

# 2. Model Routing Strategy (Practical Defaults)

This section is tool-agnostic (OpenAI/Claude/local). Map to your available models.

## Tier 0 — Local / Cheap Models (High volume)
Use for:
- extraction
- basic summarization
- rewriting drafts that are already structured
- quick classifications

Examples:
- local Qwen via Ollama
- small/cheap hosted models

Guardrails:
- never ask Tier 0 to do final strategic synthesis
- never ask Tier 0 to “decide”; ask it to “compress” or “extract”

---

## Tier 1 — Mid Capability (Most work)
Use for:
- structured drafting
- medium complexity reasoning
- creating clean executive messages
- transforming briefs into artifacts

Examples:
- strong mid-tier frontier models

---

## Tier 2 — Premium Reasoning (Limited usage)
Use for:
- high-stakes strategy
- complex trade-offs
- multi-constraint decision making
- architecture choices with many dependencies

Rule:
- only after the Summarizer has produced a compact brief

---

# 3. Standard Workflow Pipelines

## Pipeline A: “News/Trends → LinkedIn Post”
1) Research Agent collects sources + trends
2) Summarizer produces 10-bullet brief
3) Content Agent creates 3 post variants
4) QA Agent critiques (optional)
5) CoS finalizes
6) Posting Agent publishes after approval

---

## Pipeline B: “Product Strategy Decision”
1) CoS defines decision statement + options needed
2) Research Agent gathers facts (if needed)
3) Summarizer compresses into brief
4) Strategy Agent proposes options + trade-offs + KPIs
5) CoS synthesizes recommendation + exec message

---

## Pipeline C: “Automation / Script separated from agents”
1) CoS clarifies objective + constraints (keys, env, cron, platform)
2) Tech Architect proposes architecture + security model
3) Builder generates code + deployment steps
4) QA Agent checks failure modes + edge cases
5) CoS delivers final spec + implementation plan

---

# 4. Token Firewall Rules (Non-negotiable)

## Compressed Handoff Rule
No agent may pass raw dumps to a premium model.

Before Tier 2 reasoning, a brief must exist with:
- max 10 bullets
- max 3 key numbers
- max 3 risks + 3 opportunities
- explicit “decision question”

If there is no brief, create one first.

---

## Context Budget Rule
If context is large:
- summarize and store a stable artifact (Markdown)
- reference the artifact in later steps
- avoid re-sending the same long context repeatedly

---

# 5. Quality Gates (Definition of Done)

Before delivering to Sergio, outputs should pass:

1) Structure:
- clear headings
- short paragraphs
- actionable next steps

2) Trade-offs:
- at least one explicit trade-off (if decision-related)

3) Metrics:
- KPIs or success measures defined (if product/strategy)

4) Risks:
- at least 2 risks + mitigations (if strategic/technical)

5) Copy-paste readiness:
- code blocks for scripts
- markdown for docs
- message variants for comms

---

# 6. Escalation Policy

Escalate to Premium Reasoning (Tier 2) when:
- decision is high-stakes (exec comms, roadmap trade-offs, money/legal)
- dependencies are complex
- you need a crisp recommendation with risk management

Stay in Tier 0/1 when:
- task is extraction, summarization, formatting, first draft
- request is routine or low impact

---

# 7. Artifacts and Knowledge Files (Source of Truth)

Agents should treat these as canonical:

- SERGIO_AI_PROFILE.md
- SERGIO_AI_OPERATING_SYSTEM.md
- SERGIO_WRITING_STYLE.md
- SERGIO_DECISION_FRAMEWORKS.md
- SERGIO_AGENT_INSTRUCTIONS.md
- SERGIO_PROMPT_LIBRARY.md

When outputs are important and reusable, create/update a stable artifact:
- /knowledge/briefs/
- /knowledge/decisions/
- /knowledge/posts/
- /knowledge/architectures/

(Exact folders depend on your repo.)

---

# 8. Minimal “Agent Contract” (What every agent must do)

Every agent response must include:

- Output in the requested format
- Assumptions (if any)
- Open questions (if truly blocking)
- Next action suggestion (one line)

Agents must NOT:
- invent facts
- overuse premium models
- publish without explicit approval

---

# 9. Implementation Notes for OpenClaw / Cursor

- Use the Chief-of-Staff as the only agent that interacts directly with Sergio by default.
- Let CoS spawn specialist agents as needed.
- Keep a “brief” channel (Discord/MD file) that stores compressed summaries.
- Use a “drafts” channel for content variants.
- Use “approved” tags or reactions to gate publishing.

---

# End of Agent Architecture