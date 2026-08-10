---
name: create-implementation-plan
display_name: create-implementation-plan
platform: Universal Agents
category: Software engineering and app building
---

# create-implementation-plan - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `create-implementation-plan` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Create structured, machine-readable implementation plan files for features, refactors, package upgrades, infrastructure changes, data changes, architecture changes, process changes, and design implementation work. Use wh

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the create-implementation-plan skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `create-implementation-plan` |
| Canonical name | `create-implementation-plan` |
| Platform | `Universal Agents` |
| Category | Software engineering and app building |

## Description

Create structured, machine-readable implementation plan files for features, refactors, package upgrades, infrastructure changes, data changes, architecture changes, process changes, and design implementation work. Use wh


## Original SKILL.md

---
name: create-implementation-plan
description: Create structured, machine-readable implementation plan files for features, refactors, package upgrades, infrastructure changes, data changes, architecture changes, process changes, and design implementation work. Use when a user asks for an executable plan, implementation plan file, AI-agent-ready task breakdown, deterministic plan, /plan document, atomic task list, validation criteria, dependency ordering, or zero-ambiguity instructions for another agent or human to execute.
---

# Create Implementation Plan

## Primary Directive

Create a new implementation plan file that is deterministic, machine-readable, and executable by AI agents or humans without interpretation. The plan must be self-contained, use explicit identifiers, include exact file paths when known, and define validation criteria that can be checked automatically.

## Discovery Requirements

Before writing the plan:

1. Read applicable repository instructions.
2. Inspect enough source, tests, config, and docs to make file paths, dependencies, and validation steps concrete.
3. Identify the plan purpose prefix: `upgrade`, `refactor`, `feature`, `data`, `infrastructure`, `process`, `architecture`, or `design`.
4. If the repository has no `/plan` directory, include a task or create the directory only if the user asked you to create the file now.
5. If required details are unknowable after inspection, use explicit `ASSUMPTION-*` entries rather than vague language.

## Output File Rules

- Save plans in `/plan/` relative to the repository root when creating a file.
- Use filename format: `[purpose]-[component]-[version].md`.
- Use lowercase hyphen-case for filenames.
- Use valid Markdown with YAML front matter.
- Use the exact section headers in this skill.
- Use stable identifier prefixes: `REQ-`, `SEC-`, `CON-`, `GUD-`, `PAT-`, `GOAL-`, `TASK-`, `ALT-`, `DEP-`, `FILE-`, `TEST-`, `RISK-`, `ASSUMPTION-`, `VAL-`.
- Use deterministic task wording: imperative verbs, explicit paths, exact symbols, declared dependencies, and measurable completion criteria.
- Do not leave placeholder text.
- Do not use emoji completion markers. Use `false` or `true` in machine-readable task tables.

## Status Values

Use exactly one front matter status:

| Status | Badge color |
| --- | --- |
| Completed | brightgreen |
| In progress | yellow |
| Planned | blue |
| Deprecated | red |
| On Hold | orange |

## Required Template

Every implementation plan must use this structure exactly:

```markdown
---
goal: "[Concise implementation goal]"
version: "[Version or date]"
date_created: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
owner: "[Team or individual, or Unassigned]"
status: "Planned"
tags: ["feature"]
---

# Introduction

![Status: Planned](https://img.shields.io/badge/status-Planned-blue)

[One concise paragraph describing the plan goal and execution boundary.]

## 1. Requirements & Constraints

- **REQ-001**: [Functional requirement.]
- **SEC-001**: [Security requirement, or state not applicable with reason.]
- **CON-001**: [Constraint.]
- **GUD-001**: [Guideline.]
- **PAT-001**: [Existing pattern to follow.]

## 2. Implementation Steps

### Implementation Phase 1

- **GOAL-001**: [Measurable phase goal.]

| Task | Description | Dependencies | Files | Validation | Completed | Date |
|------|-------------|--------------|-------|------------|-----------|------|
| TASK-001 | [Atomic executable action.] | none | `path/to/file` | VAL-001 | false |  |

### Implementation Phase 2

- **GOAL-002**: [Measurable phase goal.]

| Task | Description | Dependencies | Files | Validation | Completed | Date |
|------|-------------|--------------|-------|------------|-----------|------|
| TASK-002 | [Atomic executable action.] | TASK-001 | `path/to/file` | VAL-002 | false |  |

## 3. Alternatives

- **ALT-001**: [Alternative considered and deterministic rejection reason.]

## 4. Dependencies

- **DEP-001**: [Library, service, config, tool, package, API, or component dependency.]

## 5. Files

- **FILE-001**: `path/to/file` - [create|modify|delete|rename] - [Reason and dependent task IDs.]

## 6. Testing

- **TEST-001**: [Exact test to create or run.]
- **VAL-001**: [Exact validation command or check tied to task IDs.]

## 7. Risks & Assumptions

- **RISK-001**: [Risk and mitigation.]
- **ASSUMPTION-001**: [Assumption and how to verify it.]

## 8. Related Specifications / Further Reading

- [Label](path/or/url)
```

## Atomic Task Rules

Each `TASK-*` entry must:

- Have one action only.
- Name exact files in the `Files` column.
- Declare dependencies as `none` or comma-separated task IDs.
- Reference one or more `VAL-*` checks.
- Be independently executable once dependencies are complete.
- Avoid subjective terms such as "clean up", "improve", "handle", or "update logic" unless the exact change is specified.

## Validation Rules

Before final output or file creation, verify:

- Front matter contains all required keys.
- Status matches one of the allowed status values.
- Badge color matches the status table.
- Headers match the required template exactly.
- Every task has an ID, dependency value, file path, validation ID, completion boolean, and date cell.
- Every referenced dependency ID exists.
- Every referenced validation ID exists.
- No placeholder text remains.
- File path and naming convention match the output file rules.

## Creation Modes

- If the user asks to create or save the plan, write the Markdown file under `/plan/` and report the path.
- If the user asks only for a plan in chat, output the full Markdown plan without writing a file.
- If the user asks to implement the plan immediately, create the implementation plan first, then ask for confirmation before making code changes unless they explicitly said to continue without review.
