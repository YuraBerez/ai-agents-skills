# AI Agents Skills

A collection of custom skills for [Claude Code](https://claude.ai/code) — reusable instruction sets that extend Claude's behaviour inside any project.

## What is a skill?

A skill is a `SKILL.md` file that Claude Code loads when you type `/skill-name` in a session. It contains structured instructions that guide Claude through a specific, repeatable workflow — like processing an idea or writing a technical task.

## Available Skills

| Skill | Trigger | Description |
| --- | --- | --- |
| [idea-processing](skills/idea-processing/SKILL.md) | `/idea-processing` | Turns a rough idea into a structured Idea Spec via clarifying questions |
| [idea-to-task](skills/idea-to-task/SKILL.md) | `/idea-to-task` | Translates a completed Idea Spec into a concrete technical task ready for implementation |
| [task-breakdown](skills/task-breakdown/SKILL.md) | `/task-breakdown` | Splits a Technical Task into sprint-ready subtasks with effort estimates |
| [pr-description](skills/pr-description/SKILL.md) | `/pr-description` | Generates a reviewer-friendly PR description from a Technical Task and implementation summary |
| [pr-check](skills/pr-check/SKILL.md) | `/pr-check` | Reviews a PR against its Technical Task — verifies criteria coverage, scope, tests, and links |
| [problem-solver](skills/problem-solver/SKILL.md) | `/problem-solver` | Identifies problems, analyses root causes, and proposes ranked solution options |
| [research-spike](skills/research-spike/SKILL.md) | `/research-spike` | Structures a time-boxed investigation into an unknown and produces a decision-ready findings report |

## Workflow

### Idea pipeline

```text
Raw idea
  └─▶ /idea-processing ──▶ Idea Spec
                                └─▶ /idea-to-task ──▶ Technical Task
                                                            ├─▶ /research-spike  (open questions)
                                                            ├─▶ /task-breakdown  (sprint planning)
                                                            └─▶ /pr-description  (after implementation)
                                                                      └─▶ /pr-check  (before merge)
```

### Problem pipeline

```text
Problem / blocker
  └─▶ /problem-solver ──▶ Problem Analysis + Ranked Solutions
                                └─▶ /idea-processing  (solution = new feature)
                                └─▶ /idea-to-task     (solution is already well-defined)
                                └─▶ /research-spike   (solution needs investigation first)
```

## How to use a skill in your project

1. Copy the desired skill directory into your project under `.claude/skills/<skill-name>/`
2. Open Claude Code in that project
3. Type `/skill-name` to invoke it

Or reference skills from this repo directly in your `CLAUDE.md`:

```markdown
Skills are located at: ~/Documents/ai-agents-skills/skills/
```

## Adding a new skill

1. Create a directory under `skills/` named after the skill (kebab-case)
2. Add a `SKILL.md` with clear, imperative instructions
3. Register the skill in the table above and in `CLAUDE.md`

### SKILL.md structure

```markdown
# Skill: <Name>

One-line description of what this skill does.

## Trigger
When and how this skill is invoked. Include typical entry points from other skills.

## Process
Step-by-step instructions Claude follows.

## Rules
Hard constraints that apply throughout.
```
