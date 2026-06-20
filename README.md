# AI Agents Skills

A collection of custom skills for [Claude Code](https://claude.ai/code) — reusable instruction sets that extend Claude's behaviour inside any project.

## What is a skill?

A skill is a `SKILL.md` file that Claude Code loads when you type `/skill-name` in a session. It contains structured instructions that guide Claude through a specific, repeatable workflow.

## Skills

### Product

Define what to build, why, and whether it worked.

| Skill | Trigger | Description |
| --- | --- | --- |
| [hypothesis](skills/product/hypothesis/SKILL.md) | `/hypothesis` | Frames a product assumption as a testable hypothesis before committing to build |
| [idea-processing](skills/product/idea-processing/SKILL.md) | `/idea-processing` | Turns a rough idea into a structured Idea Spec via clarifying questions |
| [problem-solver](skills/product/problem-solver/SKILL.md) | `/problem-solver` | Identifies problems, analyses root causes, and proposes ranked solution options |
| [user-story](skills/product/user-story/SKILL.md) | `/user-story` | Breaks an Idea Spec into well-formed user stories ready for a dev backlog |
| [prioritization](skills/product/prioritization/SKILL.md) | `/prioritization` | Ranks a list of ideas or features using RICE, MoSCoW, or Impact/Effort matrix |
| [metrics](skills/product/metrics/SKILL.md) | `/metrics` | Defines measurable success criteria and instrumentation plan before work begins |
| [feature-retro](skills/product/feature-retro/SKILL.md) | `/feature-retro` | Evaluates a shipped feature against its goals and produces learnings and next actions |

### Dev

Plan, research, and ship.

| Skill | Trigger | Description |
| --- | --- | --- |
| [idea-to-task](skills/dev/idea-to-task/SKILL.md) | `/idea-to-task` | Translates a completed Idea Spec into a concrete technical task ready for implementation |
| [task-breakdown](skills/dev/task-breakdown/SKILL.md) | `/task-breakdown` | Splits a Technical Task into sprint-ready subtasks with effort estimates |
| [research-spike](skills/dev/research-spike/SKILL.md) | `/research-spike` | Structures a time-boxed investigation and produces a decision-ready findings report |
| [pr-description](skills/dev/pr-description/SKILL.md) | `/pr-description` | Generates a reviewer-friendly PR description from a Technical Task and implementation summary |

### QA

Verify and validate.

| Skill | Trigger | Description |
| --- | --- | --- |
| [pr-check](skills/qa/pr-check/SKILL.md) | `/pr-check` | Reviews a PR against its Technical Task — verifies criteria coverage, scope, tests, and links |

## Workflow

### Full product pipeline

```text
/hypothesis  ──▶  validated assumption
                        └─▶ /idea-processing ──▶ Idea Spec
                                                      ├─▶ /user-story      (backlog-based teams)
                                                      ├─▶ /metrics         (define success first)
                                                      └─▶ /idea-to-task ──▶ Technical Task
                                                                                ├─▶ /research-spike
                                                                                ├─▶ /task-breakdown
                                                                                └─▶ /pr-description
                                                                                          └─▶ /pr-check
                                                                                                  └─▶ /feature-retro
```

### Problem pipeline

```text
/problem-solver ──▶ Problem Analysis
                          ├─▶ /idea-processing  (solution = new feature)
                          ├─▶ /idea-to-task     (solution is already well-defined)
                          └─▶ /research-spike   (solution needs investigation first)
```

### Planning pipeline

```text
[list of ideas] ──▶ /prioritization ──▶ ranked list
                                              └─▶ /hypothesis  (validate top items)
                                              └─▶ /metrics     (define success for top items)
```

## How to use a skill in your project

### Option A — copy individual skills

1. Copy the desired skill directory into your project under `.claude/skills/<skill-name>/`
2. Open Claude Code in that project
3. Type `/skill-name` to invoke it

### Option B — copy all commands (recommended)

1. Copy `.claude/commands/` from this repo into your project's `.claude/commands/`
2. Copy the `skills/` directory into your project root
3. Open Claude Code and type any `/skill-name` listed above

The command files in `.claude/commands/` are thin wrappers that load the corresponding `SKILL.md` at invocation time, so you can update skills without touching the commands.

## Adding a new skill

1. Choose the right category: `skills/product/`, `skills/dev/`, or `skills/qa/`
2. Create `<category>/<skill-name>/SKILL.md` with clear, imperative instructions
3. Register the skill in the table above and in `CLAUDE.md`

### SKILL.md structure

```markdown
# Skill: <Name>

One-line description.

## Trigger
When and how this skill is invoked. Include typical entry points from other skills.

## Process
Step-by-step instructions Claude follows.

## Rules
Hard constraints that apply throughout.
```
