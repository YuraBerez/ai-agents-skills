# Skill: Hypothesis

Frame a product assumption as a structured, testable hypothesis before committing to an Idea Spec or building anything.

## Trigger

Invoked via `/hypothesis` followed by a rough assumption or belief about a user, behaviour, or outcome. If nothing is provided, ask the user to state the assumption they want to test.

Typical entry points:
- Before `/idea-processing` — validate the core assumption first
- From a "Risks & Open Questions" item in an Idea Spec
- From a solution option in `/problem-solver` output

## Process

### Step 1 — Capture the assumption

Read the user's input. Restate the core assumption in one sentence. Confirm before proceeding.

### Step 2 — Ask clarifying questions

- **Who**: Which user segment does this assumption concern?
- **Belief**: What do you believe will happen, and why?
- **Stakes**: What is the cost if this assumption is wrong (wasted dev time, wrong direction, revenue loss)?
- **Signal**: What data or behaviour would confirm or refute this assumption?
- **Validation method**: How can this be tested — user interview, A/B test, prototype, analytics, survey?
- **Time box**: How long are you willing to spend validating before deciding?

Ask all questions in a single message. Wait for answers.

### Step 3 — Produce the Hypothesis Card

---

## Hypothesis: <short title>

### Assumption
One sentence. The core belief being tested.

### Context
One paragraph. Why this assumption matters and what decision it influences.

### Hypothesis Statement

> We believe that **[action or change]**
> will cause **[user segment]** to **[observable behaviour or outcome]**
> because **[underlying reason]**.
> We will know this is true when **[measurable signal or metric]**.

### Validation Plan

| Step | Method | Who | Time |
| --- | --- | --- | --- |
| 1 | Description (interview / A/B test / prototype / analytics) | Owner | Duration |

**Methods:**
- **User interview** — qualitative; good for understanding motivations
- **Prototype test** — low-fidelity; tests desirability before building
- **A/B test** — quantitative; requires existing traffic/users
- **Analytics review** — passive; checks if signal already exists in data
- **Survey** — scalable; good for ranking preferences

### Success Criteria
Bulleted list. What "validated" looks like in concrete, measurable terms:
- Metric X reaches Y within Z timeframe
- N out of M interview participants confirm behaviour

### Failure Criteria
Bulleted list. What "invalidated" looks like — be as specific as success criteria.

### Risk if Wrong
One sentence. What happens if we build based on a false assumption.

### Next Steps
- If validated → "Run `/idea-processing` to formalize this into an Idea Spec."
- If invalidated → "Run `/problem-solver` to reframe the approach."
- If inconclusive → "Run `/research-spike` to investigate [specific unknown] further."

---

## Rules

- The hypothesis statement must follow the exact format: "We believe… will cause… because… We will know when…"
- Success and failure criteria must be specific and measurable — not "users like it" but "60% of interviewed users choose option A over status quo."
- Never skip the Failure Criteria section. Defining what "wrong" looks like forces honest evaluation.
- The Validation Plan must be time-boxed. Open-ended validation is not a plan.
- Write the card in the same language the user used.
