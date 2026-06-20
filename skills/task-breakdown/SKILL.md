# Skill: Task Breakdown

Split a Technical Task into sprint-ready subtasks with effort estimates, priorities, and assignee hints.

## Trigger

Invoked via `/task-breakdown`. The user must provide a Technical Task — either pasted directly or referencing the output of `/idea-to-task`. If neither is present, ask the user to provide the Technical Task first.

## Process

### Step 1 — Parse the Technical Task

Extract from the Technical Task:
- Implementation Breakdown (existing subtasks)
- Acceptance Criteria
- Dependencies
- Open Technical Questions
- Effort estimates if already present

If the input is not a Technical Task (missing key sections), ask the user to run `/idea-to-task` first.

### Step 2 — Ask planning clarifying questions

Ask only what is needed to size and sequence the work:

- **Sprint length**: How long is a sprint / iteration (1 week, 2 weeks)?
- **Team size**: How many developers will work on this in parallel?
- **Blockers first**: Are there dependencies that must be resolved before any development starts?
- **Ticket format**: Should subtasks follow a specific format (Jira, Linear, GitHub Issues, plain list)?

Skip questions already answerable from the Technical Task. If all are clear, proceed to Step 3.

### Step 3 — Produce the Sprint Breakdown

Output a structured document using this exact format:

---

## Sprint Breakdown: <title>

### Summary
- **Total estimated effort**: X days / X story points
- **Suggested sprint allocation**: N subtasks per sprint
- **Parallel tracks**: List of work streams that can be done simultaneously

### Prerequisite Tasks
Subtasks that must be completed before any other work starts (unblock dependencies, setup, research spikes). List these first.

| # | Task | Effort | Blocks |
| --- | --- | --- | --- |
| P1 | Description | S | Tasks 1, 3 |

### Sprint 1

| # | Task | Effort | Notes |
| --- | --- | --- | --- |
| 1 | Description | M | Depends on P1 |

### Sprint 2 (if needed)

| # | Task | Effort | Notes |
| --- | --- | --- | --- |

### Parallel Tracks (if applicable)
If two or more subtasks can be done simultaneously by different developers, group them:

**Track A — [name]**: Tasks 1, 3, 5
**Track B — [name]**: Tasks 2, 4

### Risk Buffer
Bulleted list of tasks most likely to exceed their estimate and why. Recommend adding buffer time where applicable.

### Definition of Done (Sprint-level)
Bulleted checklist. When is the full breakdown considered complete:
- [ ] All subtasks delivered and reviewed
- [ ] Acceptance criteria from the Technical Task verified
- [ ] Definition of Done items from the Technical Task checked off

### Next Steps
Always end with: "Run `/pr-description` after each subtask or track is merged."

---

## Rules

- Effort scale: XS = <1h, S = half-day, M = 1 day, L = 2–3 days. If a task is L, split it.
- Never merge unrelated concerns into one subtask — one subtask = one coherent change.
- Prerequisite tasks (setup, research, unblocking) always go first regardless of their functional priority.
- If Open Technical Questions exist in the Technical Task, create a corresponding research subtask for each and put it in Prerequisites.
- Do not invent tasks not implied by the Technical Task.
- Write the breakdown in the same language the user used.
