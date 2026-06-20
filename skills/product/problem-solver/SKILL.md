# Skill: Problem Solver

Identify a problem clearly, analyse its root causes, and produce ranked solution options with trade-offs.

## Trigger

Invoked via `/problem-solver` followed by a description of the problem or blocker. If no description is provided, ask the user to state the problem first.

## Process

### Step 1 — Capture the problem

Read the user's input. Restate the problem in one sentence to confirm understanding. Do not proceed until the restatement is confirmed (explicitly or implicitly by the user continuing).

### Step 2 — Ask clarifying questions

Ask only what is needed to perform root cause analysis and generate meaningful solutions. Focus on:

- **Symptoms vs. cause**: What exactly is going wrong? When did it start?
- **Context**: Where does this occur (environment, system, workflow, team)?
- **Impact**: Who is affected and how severely?
- **Already tried**: What solutions have already been attempted and why did they fail?
- **Constraints**: What cannot be changed (tech, budget, time, people)?

Ask all questions in a single message. Wait for answers before proceeding.

### Step 3 — Produce the Problem Analysis

Output a structured document using this exact format:

---

## Problem Analysis: <short title>

### Problem Statement
One precise sentence. What is broken, for whom, and under what conditions.

### Root Causes
Bulleted list. Each entry is a distinct, independently verifiable cause. Distinguish between:
- **Root cause** — the underlying reason the problem exists
- **Contributing factor** — something that makes it worse but is not the origin

### Impact
Bulleted list. Quantify where possible (frequency, number of users affected, hours lost, revenue risk).

### Solution Options

For each option (minimum 2, maximum 5):

#### Option N: <title>

- **What**: One sentence describing the solution.
- **How**: Key implementation steps (3–5 bullet points).
- **Pros**: What this solves well.
- **Cons**: Trade-offs, risks, or limitations.
- **Effort**: Low / Medium / High
- **Addresses root cause**: Yes / Partial / No

### Recommendation

State which option is recommended and why. If the answer depends on a constraint the user must clarify, say so explicitly.

### Decision

Leave this section blank — the user fills it in after reviewing options:

> **Chosen option**: ___
> **Reason**: ___
> **Decided by**: ___
> **Date**: ___

### Next Steps

Numbered list of the first concrete actions to move forward with the recommended option.

Always end with the appropriate next skill based on the chosen solution:
- If the solution is a new feature or capability → "Run `/idea-processing` to formalize the solution as an Idea Spec."
- If the solution is well-defined and technical → "Run `/idea-to-task` to create a Technical Task directly."
- If the solution requires investigation before committing → "Run `/research-spike` to explore [specific unknown] first."

---

## Rules

- Never skip Step 1. Restate the problem before analysing it — a misunderstood problem leads to irrelevant solutions.
- Root causes must be specific and actionable. "Poor communication" or "technical debt" alone are not root causes.
- Every solution option must address at least one root cause. Do not suggest solutions that only mask symptoms unless explicitly useful as a short-term workaround — label those clearly as "Workaround".
- Do not recommend more than one option as primary. Pick one and justify it.
- Always include the Decision section as a blank template — it is filled by the user, not Claude.
- Always include the next-skill reference in Next Steps.
- Write the analysis in the same language the user used.
