# Skill: User Story

Break an Idea Spec into well-formed user stories with acceptance criteria ready for a dev backlog.

## Trigger

Invoked via `/user-story`. The user must provide an Idea Spec (from `/idea-processing`). If not provided, ask for it.

Typical entry points:
- After `/idea-processing` — when the team works with a story-based backlog (Jira, Linear, GitHub Issues)
- Before `/idea-to-task` — when stories need product sign-off before technical decomposition

## Process

### Step 1 — Parse the Idea Spec

Extract:
- User types / personas mentioned
- Requirements (each requirement typically becomes one or more stories)
- Out of Scope (must not appear in stories)
- Constraints

### Step 2 — Ask clarifying questions

- **Personas**: Who are the distinct user types? (e.g., admin vs. end user)
- **Granularity**: Should stories be epic-level (large, shippable chunks) or task-level (small, days of work)?
- **Format**: Should acceptance criteria use Given/When/Then (BDD) or a plain bulleted list?
- **Priority signal**: Are any requirements more urgent than others?

Skip questions already answered by the Idea Spec.

### Step 3 — Produce the User Story Map

---

## User Story Map: <Idea Spec title>

### Personas
Bulleted list of the user types involved and a one-line description of each.

### Epic: <name>
One sentence describing the high-level user goal this epic addresses.

#### Story <N>: <title>

**As a** [persona],
**I want** [goal or action],
**so that** [benefit or outcome].

**Priority**: Critical / High / Medium / Low

**Acceptance Criteria**:

_BDD format:_
- **Given** [initial context], **When** [action], **Then** [expected result]

_or plain format:_
- Criterion 1
- Criterion 2

**Out of Scope for this story**:
- Anything explicitly excluded

---

Repeat the Story block for each story within the epic. Repeat the Epic block for each epic.

### Story Dependency Map
If stories have dependencies, list them:
- Story 2 depends on Story 1 (shared data model)
- Story 4 can be built in parallel with Story 3

### Next Steps
- "Run `/idea-to-task` on any story to produce a Technical Task for implementation."
- "Run `/prioritization` if story priority needs to be ranked against other backlog items."

---

## Rules

- One story = one user goal. Never combine multiple user goals into a single story.
- Acceptance criteria must be testable without reading the code.
- Do not include implementation details in stories — those belong in `/idea-to-task`.
- If the Idea Spec has multiple user types, create separate stories for each type even if the underlying feature is the same.
- Out of Scope must appear in every story — an empty scope boundary is a sign the story is too vague.
- Write the map in the same language the user used.
