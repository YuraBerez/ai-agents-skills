# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Purpose

This repository contains custom skills for Claude Code AI agents. Skills are reusable, composable instruction sets invoked via `/skill-name` inside a Claude Code session.

## Repository Structure

```text
skills/
  <skill-name>/
    SKILL.md        # Entry point — loaded when the skill is invoked
    [other files]   # Templates, examples, config; keep co-located with the skill
README.md           # Human-facing docs; keep the skills table in sync here and below
CLAUDE.md           # This file
```

## Available Skills

| Skill | Trigger | Purpose |
| --- | --- | --- |
| idea-processing | `/idea-processing` | Turns a rough idea into a structured Idea Spec via clarifying questions |
| idea-to-task | `/idea-to-task` | Translates a completed Idea Spec into a concrete technical task ready for implementation |
| problem-solver | `/problem-solver` | Identifies problems, analyses root causes, and proposes ranked solution options |

Pipeline: `/idea-processing` → Idea Spec → `/idea-to-task` → Technical Task.
`/problem-solver` is standalone — use it whenever a problem or blocker needs structured analysis.

## Adding a New Skill

1. Create `skills/<skill-name>/SKILL.md` with trigger, process steps, and rules.
2. Add a row to the **Available Skills** table above.
3. Add the same row to the table in `README.md`.

## Skill Authoring Conventions

- Instructions must be imperative and unambiguous — Claude follows them literally.
- Every skill must have a **Trigger** section (when/how it activates) and a **Rules** section (hard constraints).
- Skills ask clarifying questions before producing output; never skip to output on ambiguous input.
- Output format must be specified exactly — use fenced template blocks with named sections.
- Skills write their output in the language the user used.
