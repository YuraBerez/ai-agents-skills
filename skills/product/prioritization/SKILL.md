# Skill: Prioritization

Rank a list of ideas, features, or backlog items using a structured framework and produce a prioritized roadmap slice.

## Trigger

Invoked via `/prioritization` followed by a list of items to prioritize. If no list is provided, ask the user to supply one (free-form is fine — one item per line).

Typical entry points:
- After multiple `/idea-processing` runs — when several Idea Specs compete for the same dev capacity
- During quarterly or sprint planning to rank the backlog
- After `/problem-solver` produces multiple solution options that each became separate ideas

## Process

### Step 1 — Capture the list

Read the user's input. List all items back to confirm nothing was missed. Do not proceed until confirmed.

### Step 2 — Ask clarifying questions

- **Framework**: Which prioritization method to use?
  - **RICE** — Reach × Impact × Confidence ÷ Effort (good for growth/product teams)
  - **MoSCoW** — Must / Should / Could / Won't (good for release scoping)
  - **Impact/Effort matrix** — 2×2 quadrants: quick wins, big bets, fill-ins, time sinks (good for quick decisions)
  - **Weighted scoring** — custom criteria with weights (good when stakeholders disagree)
- **Criteria**: What matters most — user value, revenue, retention, technical debt reduction, compliance?
- **Constraints**: Is there a deadline, team capacity limit, or dependency that forces any ordering?
- **Who decides**: Is this a solo decision or does it need stakeholder alignment?

Ask all questions in a single message. Wait for answers.

### Step 3 — Produce the Prioritization Report

---

## Prioritization Report: <context / sprint / quarter>

### Framework Used
Name of the framework and one sentence explaining why it was chosen for this context.

### Scoring

#### RICE (if chosen)

| Item | Reach | Impact | Confidence | Effort | RICE Score |
| --- | --- | --- | --- | --- | --- |
| Item name | N users/month | 0.25/0.5/1/2/3 | 20/50/80/100% | person-weeks | score |

RICE Score = (Reach × Impact × Confidence) ÷ Effort

#### MoSCoW (if chosen)

| Category | Items |
| --- | --- |
| **Must have** | Items that are non-negotiable for this release |
| **Should have** | Important but not critical |
| **Could have** | Nice to have if capacity allows |
| **Won't have** | Explicitly out of scope for now |

#### Impact/Effort Matrix (if chosen)

| Quadrant | Items |
| --- | --- |
| **Quick Wins** (high impact, low effort) | |
| **Big Bets** (high impact, high effort) | |
| **Fill-ins** (low impact, low effort) | |
| **Time Sinks** (low impact, high effort) | |

#### Weighted Scoring (if chosen)

| Item | Criterion A (weight) | Criterion B (weight) | Total |
| --- | --- | --- | --- |

### Prioritized List
Final ranked order with a one-line rationale for each position:

1. **[Item]** — Rationale
2. **[Item]** — Rationale

### Assumptions & Caveats
Bulleted list. State what was assumed about reach, effort, or impact that could change the ranking if wrong.

### Next Steps
- "Run `/idea-processing` on the top-priority item if it does not yet have an Idea Spec."
- "Run `/hypothesis` to validate assumptions about items ranked 1–2 before committing capacity."
- "Run `/metrics` to define success criteria for the top items before starting work."

---

## Rules

- Never mix frameworks in a single report — pick one and apply it consistently.
- Every scoring decision must be explicit — state the number and why (e.g., "Reach: 500 users/month based on current active users in segment X").
- If the user cannot provide a score input, offer a range and note the uncertainty in Assumptions.
- Items in the "Won't have" or "Time Sink" quadrant must stay in the report — removing them pretends they don't exist.
- Write the report in the same language the user used.
