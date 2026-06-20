# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

This repository contains custom skills for Claude Code AI agents. Skills are reusable, composable instruction sets invoked via `/skill-name` inside a Claude Code session.

## Repository Structure

```text
skills/
  product/          # Define what to build, why, and whether it worked
    hypothesis/
    idea-processing/
    problem-solver/
    user-story/
    prioritization/
    metrics/
    feature-retro/
  dev/              # Plan, research, and ship
    idea-to-task/
    task-breakdown/
    research-spike/
    pr-description/
  qa/               # Verify and validate
    pr-check/
docs/
  idea/             # Idea Specs saved by /idea-processing
  technical/        # Technical Tasks saved by /idea-to-task
README.md
CLAUDE.md
```

## Available Skills

### Product

| Skill | Trigger | Purpose |
| --- | --- | --- |
| hypothesis | `/hypothesis` | Frames a product assumption as a testable hypothesis before committing to build |
| idea-processing | `/idea-processing` | Turns a rough idea into a structured Idea Spec via clarifying questions |
| problem-solver | `/problem-solver` | Identifies problems, analyses root causes, and proposes ranked solution options |
| user-story | `/user-story` | Breaks an Idea Spec into well-formed user stories ready for a dev backlog |
| prioritization | `/prioritization` | Ranks ideas or features using RICE, MoSCoW, or Impact/Effort matrix |
| metrics | `/metrics` | Defines measurable success criteria and instrumentation plan before work begins |
| feature-retro | `/feature-retro` | Evaluates a shipped feature against its goals and produces learnings and next actions |

### Dev

| Skill | Trigger | Purpose |
| --- | --- | --- |
| idea-to-task | `/idea-to-task` | Translates a completed Idea Spec into a concrete technical task |
| task-breakdown | `/task-breakdown` | Splits a Technical Task into sprint-ready subtasks with effort estimates |
| research-spike | `/research-spike` | Structures a time-boxed investigation and produces a decision-ready findings report |
| pr-description | `/pr-description` | Generates a reviewer-friendly PR description |

### QA

| Skill | Trigger | Purpose |
| --- | --- | --- |
| pr-check | `/pr-check` | Reviews a PR against its Technical Task — criteria, scope, tests, links |

## Skill Pipelines

**Full product**: `/hypothesis` → `/idea-processing` → `/metrics` → `/idea-to-task` → `/task-breakdown` → `/pr-description` → `/pr-check` → `/feature-retro`

**Problem**: `/problem-solver` → `/idea-processing` or `/idea-to-task` or `/research-spike`

**Planning**: `/prioritization` → `/hypothesis` → `/metrics`

**Research**: `/research-spike` can be triggered from any skill that produces Open Technical Questions or Risks.

## Adding a New Skill

1. Pick the right category: `skills/product/`, `skills/dev/`, or `skills/qa/`
2. Create `<category>/<skill-name>/SKILL.md`
3. Add a row to the correct table above and in `README.md`

## Skill Authoring Conventions

- Instructions must be imperative and unambiguous.
- Every skill must have a **Trigger** section (with entry points from other skills) and a **Rules** section.
- Every skill must end its output with explicit next-skill references — skills chain, not dead-end.
- Ask clarifying questions before producing output; never skip on ambiguous input.
- Specify output format exactly — use fenced template blocks with named sections.
- Effort scale: XS = <1h, S = half-day, M = 1 day, L = 2–3 days. Split any task sized L.
- Write output in the language the user used.
