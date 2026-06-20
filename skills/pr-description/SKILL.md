# Skill: PR Description

Generate a clear, reviewer-friendly pull request description from a Technical Task and a summary of changes made.

## Trigger

Invoked via `/pr-description`. The user must provide:
1. The Technical Task (from `/idea-to-task`) — for context, acceptance criteria, and scope
2. A summary of what was actually implemented (diff summary, list of changes, or free-form description)

If either is missing, ask for it before proceeding.

## Process

### Step 1 — Parse inputs

Extract from the Technical Task:
- Technical Goal
- Acceptance Criteria
- Out of Scope
- Dependencies

Extract from the implementation summary:
- What files / components were changed
- What was added, modified, or removed
- Any deviations from the original Technical Task

### Step 2 — Ask clarifying questions

Ask only what is needed to complete the PR description:

- **PR type**: Is this a feature, bug fix, refactor, or chore?
- **Breaking changes**: Does this change any public API, contract, or behaviour that consumers depend on?
- **How to test**: How should the reviewer verify the changes locally (run command, open URL, specific scenario)?
- **Screenshots / recordings**: Are there UI changes that should be shown visually?
- **Linked ticket**: Is there a Jira / Linear / GitHub issue number to link?

Skip questions already answerable from the inputs. If all are clear, proceed to Step 3.

### Step 3 — Produce the PR Description

Output using this exact format:

---

## PR: <title>

> **Type**: Feature / Bug fix / Refactor / Chore
> **Linked ticket**: [TICKET-123](url) _(if provided)_
> **Breaking change**: Yes / No

### What & Why
One short paragraph. What this PR does and why it's needed (link to the business problem from the Technical Task).

### Changes
Bulleted list of the concrete changes made, grouped by area (e.g., API, UI, DB, config):
- **[Area]**: Description of change

### How to Test
Step-by-step instructions for the reviewer to verify the changes:
1. Step one
2. Step two
3. Expected result

### Acceptance Criteria Coverage
Table mapping each acceptance criterion from the Technical Task to its status:

| # | Criterion | Status |
| --- | --- | --- |
| 1 | Description | ✅ Covered / ⚠️ Partial / ❌ Not covered |

### Out of Scope
Carry over from the Technical Task. Add any additional exclusions relevant to this PR.

### Notes for Reviewer
Bulleted list of anything that needs special attention:
- Non-obvious design decisions
- Areas of uncertainty or known limitations
- Anything the reviewer should NOT change in this review cycle

---

## Rules

- The PR title must be ≤72 characters and follow the format: `[type]: short description` (e.g., `feat: add idea-processing skill`).
- Never include implementation details that are obvious from the diff — the PR description explains the WHY, not the WHAT.
- If any acceptance criterion is not covered (❌), flag it explicitly and explain why (deferred, out of scope, or blocked).
- If there are UI changes, note that screenshots/recordings should be attached.
- Write the description in the same language the user used.
