# Skill: Idea to Technical Task

Translate a completed Idea Spec (from `/idea-processing`) into a concrete technical task ready for implementation.

## Trigger

Invoked via `/idea-to-task`. The user must provide an Idea Spec — either pasted directly or by referencing the output of `/idea-processing`. If neither is present, ask the user to provide the Idea Spec first.

## Process

### Step 1 — Parse the Idea Spec

Extract from the Idea Spec:
- The core goal and success criteria
- All stated requirements
- Constraints and risks
- Priority level

If the input is not an Idea Spec (missing key sections), ask the user to run `/idea-processing` first or provide the missing context.

### Step 2 — Ask technical clarifying questions

Before writing the task, ask only the questions the Idea Spec did not answer. Focus on:
- **Stack**: What language, framework, or platform will this be built on?
- **Integration points**: Does this touch existing systems, APIs, or data stores? Which ones?
- **Deployment**: Where does this run (cloud, local, edge)? Any infra constraints?
- **Performance / scale**: Any latency, throughput, or data-volume requirements?
- **Auth / permissions**: Does this involve user identity, roles, or access control?
- **Testing**: What level of test coverage is expected (unit, integration, e2e)?

Skip any question already answered by the Idea Spec. If all are answered, go directly to Step 3.

### Step 3 — Produce the Technical Task

Output a structured document using this exact format and save it to `docs/technical/<kebab-case-title>.md`.

---

## Technical Task: <title>

### Context
One short paragraph linking back to the business problem and the Idea Spec decision.

### Technical Goal
Single sentence. What the system must do when this task is complete.

### Architecture Notes
Bulleted list. Key design decisions, chosen patterns, affected components, and integration points. State assumptions explicitly.

### Acceptance Criteria
Numbered list of precise, testable conditions (behaviour, not implementation). Each criterion must be verifiable without reading the code.

### Definition of Done
Bulleted checklist. Conditions that must all be true before this task can be closed:
- [ ] All acceptance criteria pass
- [ ] Tests written and passing (specify: unit / integration / e2e)
- [ ] Code reviewed and approved
- [ ] Documentation updated (if applicable)
- [ ] Deployed to [environment]

Add or remove items based on the project context.

### Testing Strategy
Bulleted list. What to test, at what level, and why:
- **Unit**: Which functions/modules need isolated tests?
- **Integration**: Which service boundaries need integration tests?
- **E2E / manual**: Which user flows must be verified end-to-end?

### Implementation Breakdown
Ordered list of subtasks. Each subtask must include:
- **What**: one-line description of the change
- **Effort**: XS / S / M / L (XS = <1h, S = half-day, M = 1 day, L = 2–3 days)

Subtasks must be small enough to fit in a single PR or commit. If a subtask is L, break it down further.

### Dependencies
Bulleted list of external dependencies: libraries, services, other tasks that must be completed first, or decisions that must be made before work can start.

### Out of Scope
Copy and expand from the Idea Spec where relevant. Add any technical exclusions not covered there.

### Open Technical Questions
Bulleted list of unresolved decisions that could block or significantly alter implementation. Flag who needs to answer each one.
If any questions require investigation, note: "Run `/research-spike` for [question] before starting implementation."

### Next Steps
Always end with one of:
- "Run `/task-breakdown` to split this into sprint-ready subtasks."
- "Run `/research-spike` for [open question] before implementation."
- "Run `/pr-description` after implementation is complete."

---

## Rules

- Never invent technology choices the user has not confirmed. If unsure, list options and ask.
- Acceptance criteria must be testable — avoid vague terms like "fast", "easy", "clean".
- Keep Architecture Notes high-level; do not write implementation code in the task document.
- If the Idea Spec contains risks, map each one to a concrete mitigation or flag it as an Open Technical Question.
- Every subtask in Implementation Breakdown must have an effort estimate.
- Write the task in the same language the user used.
- This skill produces input for a developer or a planning tool (Jira, Linear, GitHub Issues) — format accordingly.
