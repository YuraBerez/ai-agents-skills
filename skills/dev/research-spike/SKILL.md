# Skill: Research Spike

Structure an investigation into an unknown or open question, produce a time-boxed research plan, and summarise findings in a decision-ready format.

## Trigger

Invoked via `/research-spike` followed by the open question or unknown to investigate. If no question is provided, ask the user to state what needs to be researched.

Typical entry points:
- An "Open Technical Questions" item from `/idea-to-task`
- A "Risks & Open Questions" item from `/idea-processing`
- An unknown in the Recommendation from `/problem-solver`

## Process

### Step 1 — Define the research question

Read the user's input. Restate the question in one precise sentence. Confirm before proceeding.

### Step 2 — Ask scoping questions

- **Decision this unblocks**: What will be decided based on this research? (forces focus)
- **Time box**: How much time is available for the spike (hours / days)?
- **Success definition**: What does "done" look like — a decision, a prototype, a benchmark, a recommendation?
- **Known constraints**: Are any options already ruled out? What do we already know?
- **Resources available**: Who can be consulted? Are there existing docs, codebases, or experiments to reference?

Ask all questions in a single message. Wait for answers before proceeding.

### Step 3 — Produce the Research Plan

Output a structured document using this exact format:

---

## Research Spike: <short title>

### Research Question
One precise sentence. What are we trying to answer, and why does it matter?

### Decision This Unblocks
One sentence. What cannot proceed until this is answered.

### Time Box
- **Total time allocated**: X hours / X days
- **Deadline**: [date or milestone]

### What We Already Know
Bulleted list. Established facts, prior attempts, and constraints that narrow the solution space.

### Research Tasks

Ordered list of investigation steps, each with a time estimate:

| # | Task | Method | Time |
| --- | --- | --- | --- |
| 1 | Description | Read docs / Build PoC / Benchmark / Interview | 2h |

Methods:
- **Read docs** — review official documentation, RFCs, changelogs
- **Build PoC** — write a minimal prototype to test a hypothesis
- **Benchmark** — measure performance, cost, or capacity under realistic conditions
- **Interview** — consult a domain expert or team member
- **Analyse existing code** — read the relevant parts of the current codebase

### Evaluation Criteria
Bulleted list of what a good answer must satisfy (used to compare options):
- Criterion 1
- Criterion 2

### Findings Template

Fill this in after completing the research tasks:

**Summary**: One sentence conclusion.

**Options evaluated**:
| Option | Pros | Cons | Meets criteria? |
| --- | --- | --- | --- |
| Option A | | | Yes / Partial / No |

**Recommendation**: Chosen option and reasoning.

**Confidence**: High / Medium / Low — and why.

**Unknowns remaining**: Anything still unresolved after the spike.

### Next Steps After Spike
Always end with the appropriate next skill:
- If findings enable implementation → "Run `/idea-to-task` to create the Technical Task with these findings incorporated."
- If findings open new questions → "Run `/research-spike` for [new question]."
- If findings resolve a problem → "Update the Decision section in the `/problem-solver` output."

---

## Rules

- The spike must be time-boxed. If no time box is provided, ask for one — open-ended research is not a spike.
- Research tasks must be specific and actionable. "Research X" is not a task; "Read the official X docs and list its constraints" is.
- The Findings Template is always included blank — it is filled by the user or a developer after the spike, not by Claude.
- A spike produces a decision or recommendation, not just information. If the user asks for a "summary of findings" without a decision, push back and ask what decision this enables.
- Write the plan in the same language the user used.
