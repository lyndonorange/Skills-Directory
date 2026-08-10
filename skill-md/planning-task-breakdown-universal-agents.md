---
name: planning-task-breakdown
display_name: planning-task-breakdown
platform: Universal Agents
category: Software engineering and app building
---

# planning-task-breakdown - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `planning-task-breakdown` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Decompose specs, PRDs, epics, large coding tasks, ambiguous implementation requests, and multi-session work into small, ordered, verifiable tasks with acceptance criteria. Use when a task feels too large to start, implem

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the planning-task-breakdown skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `planning-task-breakdown` |
| Canonical name | `planning-task-breakdown` |
| Platform | `Universal Agents` |
| Category | Software engineering and app building |

## Description

Decompose specs, PRDs, epics, large coding tasks, ambiguous implementation requests, and multi-session work into small, ordered, verifiable tasks with acceptance criteria. Use when a task feels too large to start, implem


## Original SKILL.md

---
name: planning-task-breakdown
description: Decompose specs, PRDs, epics, large coding tasks, ambiguous implementation requests, and multi-session work into small, ordered, verifiable tasks with acceptance criteria. Use when a task feels too large to start, implementation order is unclear, work needs parallelization, dependencies must be mapped, vertical slices or tracer bullets are needed, acceptance criteria must be written before coding, or a human-readable implementation task plan is needed before editing files.
---

# Planning And Task Breakdown

## Core Rule

Enter read-only planning mode before implementation. Read the spec and relevant code, map dependencies, identify risks, and produce a plan document. Do not edit code while preparing the task breakdown.

## When Not To Use

Skip this skill for single-file changes with obvious scope, tiny bug fixes, or specs that already contain well-defined tasks with acceptance criteria and verification steps.

## Planning Process

### Step 1: Read Before Planning

Inspect enough context to make the plan specific:

- Spec, PRD, issue, epic, or user request.
- Existing implementation patterns.
- Tests, fixtures, and verification commands.
- Configuration, schemas, migrations, generated files, and docs.
- Ownership boundaries and likely hidden coupling.

### Step 2: Map Dependencies

Identify what depends on what:

```text
Data/schema/contracts
  -> shared types/models
    -> service/API behavior
      -> clients/integrations
        -> UI/workflows
          -> tests/docs/release
```

Build foundations first, but avoid turning the whole plan into horizontal layers.

### Step 3: Slice Vertically

Prefer complete, narrow user or system flows over component-only phases.

Bad horizontal slicing:

- Build all database tables.
- Build all API endpoints.
- Build all UI components.
- Connect everything.

Good vertical slicing:

- User can register: minimal schema, API, UI, validation, and tests.
- User can log in: auth path, errors, session, and tests.
- User can create one task: task write path, UI action, and tests.
- User can view task list: query path, UI display, empty state, and tests.

Each slice should leave the system closer to working software.

### Step 4: Write Small Tasks

Use this task shape:

```markdown
## Task [N]: [Short descriptive title]

**Description:** [One paragraph explaining what this task accomplishes.]

**Acceptance Criteria:**
- [ ] [Specific, testable condition.]
- [ ] [Specific, testable condition.]

**Verification:**
- [ ] Tests pass: `[command]`
- [ ] Build succeeds: `[command]`
- [ ] Manual check: [what to verify, if needed]

**Dependencies:** [Task numbers or None]

**Files Likely Touched:**
- `path/to/file`
- `path/to/test`

**Estimated Scope:** [XS|S|M|L]
```

### Step 5: Order And Checkpoint

Arrange tasks so:

- Dependencies are satisfied.
- Each task leaves the system in a working or recoverable state.
- High-risk tasks happen early.
- Verification checkpoints occur after every 2-3 tasks or after major phases.
- Human review happens before implementation when the plan is substantial.

## Task Sizing

| Size | Files | Scope | Example |
| --- | --- | --- | --- |
| XS | 1 | Single function or config change | Add a validation rule |
| S | 1-2 | One component, endpoint, or utility | Add one API endpoint |
| M | 3-5 | One vertical feature slice | User registration flow |
| L | 5-8 | Multi-component feature | Search with filtering and pagination |
| XL | 8+ | Too large | Break it down |

Prefer S and M tasks. Break down a task when:

- It takes more than one focused session.
- Acceptance criteria need more than 3 bullets.
- It touches independent subsystems.
- The title contains "and".
- It is likely to touch more than 5 files.

## Parallelization Guidance

Safe to parallelize:

- Independent vertical slices.
- Tests for already implemented behavior.
- Documentation after behavior is stable.
- UI polish after contracts are fixed.

Must be sequential:

- Database migrations.
- Shared contracts and schemas.
- API changes required by multiple callers.
- Changes that mutate shared state or global configuration.

Needs coordination:

- Features sharing an API contract.
- Multiple agents editing the same files.
- Cross-service or cross-package changes.

## Plan Template

```markdown
# Implementation Plan: [Feature/Project Name]

## Overview

[One paragraph summary of what is being built.]

## Architecture Decisions

- [Decision and rationale.]
- [Decision and rationale.]

## Dependency Map

[Short dependency explanation or diagram.]

## Task List

### Phase 1: Foundation

- [ ] Task 1: [title]
- [ ] Task 2: [title]

### Checkpoint: Foundation

- [ ] Tests pass.
- [ ] Build succeeds.
- [ ] Human review before proceeding, if needed.

### Phase 2: Core Vertical Slices

- [ ] Task 3: [title]
- [ ] Task 4: [title]

### Checkpoint: Core Flow

- [ ] End-to-end flow works.
- [ ] Acceptance criteria for core flow are met.

### Phase 3: Edge Cases And Polish

- [ ] Task 5: [title]
- [ ] Task 6: [title]

### Checkpoint: Complete

- [ ] All acceptance criteria met.
- [ ] Final verification command passes.
- [ ] Ready for review.

## Detailed Tasks

[Use the task shape from Step 4.]

## Risks And Mitigations

| Risk | Impact | Mitigation |
| --- | --- | --- |
| [Risk] | [High/Medium/Low] | [Mitigation] |

## Open Questions

- [Question needing human input.]
```

## Final Verification

Before implementation starts, confirm:

- Every task has acceptance criteria.
- Every task has verification.
- Dependencies are identified and ordered.
- No task is XL-sized.
- Tasks touching more than 5 files are justified or split.
- Checkpoints exist between major phases.
- The human has reviewed and approved the plan when the work is non-trivial.

## Red Flags

- Starting implementation without a written task list.
- Tasks that say "implement the feature" without acceptance criteria.
- No verification steps.
- All tasks are large.
- No checkpoints.
- Dependency order is ignored.
- The plan is split only by database, API, and UI layers.
