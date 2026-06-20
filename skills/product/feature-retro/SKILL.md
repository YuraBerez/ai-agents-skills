# Skill: Feature Retro

Evaluate a shipped feature against its original success metrics and decisions, and produce a structured retrospective with learnings and next actions.

## Trigger

Invoked via `/feature-retro` followed by the feature name or a reference to its Metrics Plan, Idea Spec, or Technical Task. If nothing is provided, ask the user to identify the feature.

Typical entry points:
- After the post-launch review date defined in `/metrics`
- After a feature has been live long enough to collect meaningful data (typically 2–6 weeks)

## Process

### Step 1 — Gather context

Ask the user to provide as much of the following as available:
- The original Idea Spec or Metrics Plan (for goals and targets)
- Current metric values vs. baseline and target
- Any qualitative feedback (user interviews, support tickets, reviews)

If none of these are available, ask the user to describe the feature's goal and what actually happened.

### Step 2 — Ask clarifying questions

- **Results**: Did the North Star Metric hit its target? By how much?
- **Guardrails**: Were any anti-metrics breached?
- **Surprises**: What happened that was not expected (positive or negative)?
- **Usage patterns**: Are users using the feature as intended? Any unexpected use cases?
- **Team friction**: Were there delivery problems (scope creep, estimates off, tech issues)?
- **Decision**: What should happen next — iterate, scale, pivot, or deprecate?

Ask all questions in a single message. Wait for answers.

### Step 3 — Produce the Feature Retrospective

---

## Feature Retro: <feature name>

### Feature Summary
One paragraph. What was built, why, and when it shipped.

### Results vs. Goals

| Metric | Baseline | Target | Actual | Status |
| --- | --- | --- | --- | --- |
| North Star | value | value | value | ✅ Hit / ⚠️ Partial / ❌ Missed |
| Supporting metric | | | | |
| Anti-metric (guardrail) | | threshold | value | ✅ Held / ❌ Breached |

### What Worked
Bulleted list. Specific things that went well — in product decisions, delivery, or outcomes.

### What Didn't Work
Bulleted list. Specific things that fell short — be precise about cause, not just symptom.

### Surprises
Bulleted list. Anything not anticipated — positive (unexpected adoption) or negative (unintended side effect).

### Root Cause Analysis (if targets were missed)
For each missed metric, one paragraph:
- What was the actual behaviour?
- What was the assumption that proved wrong?
- What would we do differently?

### Decision

Choose one:

- **Iterate** — feature is directionally right but needs improvement. Specify what.
- **Scale** — feature is working; invest more (more users, more markets, more surface area).
- **Pivot** — the problem is real but the solution needs rethinking. Specify the new direction.
- **Deprecate** — the feature is not delivering value. Specify sunset plan.

**Chosen decision**: ___
**Owner**: ___
**Date**: ___

### Learnings (Reusable)
Bulleted list of insights that apply beyond this feature — things the team should carry into future decisions:
- About the users
- About the domain
- About the delivery process

### Next Steps
Numbered list of concrete actions that follow from the decision.

Always end with the appropriate next skill:
- If Iterate or Pivot → "Run `/idea-processing` to formalize the next iteration."
- If Scale → "Run `/metrics` to update targets for the scaled version."
- If Deprecate → document the sunset plan as a Technical Task via `/idea-to-task`.

---

## Rules

- Results must be compared against the original targets — never evaluate a feature against post-hoc goals.
- If the Metrics Plan was not created before launch, note this explicitly and flag it as a learning.
- "What Didn't Work" must name specific decisions or assumptions that were wrong — not "the market wasn't ready."
- The Decision section must have a single chosen direction. "We'll monitor it" is not a decision.
- The Decision block is filled by the user, not Claude — leave Owner and Date blank for the user to complete.
- Write the retro in the same language the user used.
