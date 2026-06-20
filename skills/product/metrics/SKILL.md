# Skill: Metrics

Define measurable success criteria for a feature or initiative before work begins.

## Trigger

Invoked via `/metrics` followed by a feature name or Idea Spec. If neither is provided, ask the user what feature or initiative to define metrics for.

Typical entry points:
- After `/idea-processing` — before handing off to dev, lock in how success is measured
- After `/hypothesis` — turn the hypothesis signal into tracked metrics
- After `/prioritization` — define metrics for the top-ranked items before starting work

## Process

### Step 1 — Capture the feature context

Read the user's input. Extract:
- What the feature does
- Who it serves
- What problem it solves

If an Idea Spec is provided, use its Problem, Proposed Solution, and Requirements as input.

### Step 2 — Ask clarifying questions

- **Goal type**: Is the primary goal acquisition, activation, retention, revenue, referral, or efficiency?
- **Current baseline**: Is there existing data for the metric area (e.g., current conversion rate, current churn rate)?
- **Target**: What outcome is considered success? (absolute number, % change, or qualitative threshold)
- **Timeframe**: When should the target be reached?
- **Instrumentation**: Is analytics/tracking already in place, or does it need to be built?
- **Anti-metrics**: What must NOT get worse as a side effect of this feature?

Ask all questions in a single message. Wait for answers.

### Step 3 — Produce the Metrics Plan

---

## Metrics Plan: <feature name>

### Goal
One sentence. The business or user outcome this feature is designed to drive.

### North Star Metric
The single most important metric that captures whether this feature succeeded.

| Metric | Current baseline | Target | Timeframe |
| --- | --- | --- | --- |
| Name | value or "unknown" | value or % change | date or sprint |

### Supporting Metrics
Secondary metrics that provide context or early signal:

| Metric | Type | Baseline | Target | Why it matters |
| --- | --- | --- | --- | --- |
| Name | Leading / Lagging | value | value | Explanation |

**Types:**
- **Leading** — changes quickly; predicts future outcomes (e.g., feature adoption rate)
- **Lagging** — changes slowly; confirms outcomes (e.g., revenue impact)

### Anti-Metrics (Guardrails)
Metrics that must not degrade. If any guardrail is breached, treat it as a signal to investigate before continuing.

| Metric | Current value | Threshold (do not cross) |
| --- | --- | --- |

### Instrumentation Checklist
- [ ] Events to track: list each user action that must be logged
- [ ] Properties to capture: user segment, feature flag variant, session context
- [ ] Dashboard: where will this be monitored (Amplitude, Mixpanel, Grafana, custom)?
- [ ] Alert: what triggers an investigation (threshold breach, anomaly)?

### Review Cadence
When and how metrics will be reviewed:
- **Daily**: automated alert if guardrail is breached
- **Weekly**: metric review in [meeting/channel]
- **Post-launch review date**: [date] — first structured read of results

### Next Steps
- "Run `/idea-to-task` and include the Instrumentation Checklist as a required subtask."
- "Run `/feature-retro` after the post-launch review date to evaluate results."

---

## Rules

- There must be exactly one North Star Metric. If multiple metrics seem equally important, force a choice and justify it.
- Baseline must be stated. "Unknown" is acceptable but must be resolved before launch — add it to the Instrumentation Checklist.
- Anti-metrics are mandatory. Every feature has side effects — ignoring them is not an option.
- Targets must be specific: "increase by 20%" is acceptable; "improve engagement" is not.
- Write the plan in the same language the user used.
