# Skill: Idea Processing

Turn a rough idea into a clear, actionable specification through structured clarification and analysis.

## Trigger

Invoked via `/idea-processing` followed by a brief description of the idea. If no description is provided, ask the user to state their idea first.

## Process

### Step 1 — Understand the raw idea

Read the user's input. Identify what is clear and what is ambiguous. Do not ask anything yet.

### Step 2 — Ask clarifying questions

Ask 3–5 targeted questions to resolve the key unknowns. Focus on:
- **Goal**: What problem does this solve? Who benefits?
- **Scope**: What is explicitly in/out of scope?
- **Constraints**: Time, budget, tech stack, dependencies, team size?
- **Success criteria**: How will we know it worked?
- **Priority**: How urgent is this? Does it block anything else?
- **Risks**: What could go wrong or block this?

Ask all questions in a single message. Number them. Wait for answers before proceeding.

### Step 3 — Produce the Idea Spec

After receiving answers, output a structured document using this exact format and save it to `docs/idea/<kebab-case-title>.md`.

---

## Idea Spec: <short title>

### Problem
One paragraph. What is broken or missing, and for whom.

### Proposed Solution
One paragraph. What we're building and how it addresses the problem.

### Requirements
Bulleted list of concrete, testable requirements (what must be true when done).

### Out of Scope
Bulleted list of things explicitly not being addressed in this iteration.

### Constraints
Bulleted list: technical, resource, time, or dependency constraints.

### Priority
One line: urgency level (Critical / High / Medium / Low) and what it blocks or depends on.

### Risks & Open Questions
Bulleted list. Flag anything that needs a decision or investigation before work can start.

### Next Steps
Numbered list. Always end with: "Run `/idea-to-task` to translate this spec into a technical task."
If there are open questions that need research first, add: "Run `/research-spike` for [specific question] before proceeding."

---

## Rules

- Never skip Step 2. Even if the idea seems clear, at least confirm scope and success criteria.
- Keep the Idea Spec concise — each section should be scannable, not exhaustive.
- Do not include implementation details unless the user explicitly asked for them.
- If the user provides partial answers, make reasonable assumptions and state them clearly in the spec.
- Always include the explicit next-skill reference in the Next Steps section.
- Write the spec in the same language the user used.
