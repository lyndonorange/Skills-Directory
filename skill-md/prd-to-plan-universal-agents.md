---
name: prd-to-plan
display_name: prd-to-plan
platform: Universal Agents
category: Product, growth, marketing, and PM
---

# prd-to-plan - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `prd-to-plan` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Convert Product Requirements Documents (PRDs), feature specs, epics, design sprint outputs, and product briefs into phased implementation plans organized as vertical slices or tracer bullets. Use when a user asks to brea

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the prd-to-plan skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `prd-to-plan` |
| Canonical name | `prd-to-plan` |
| Platform | `Universal Agents` |
| Category | Product, growth, marketing, and PM |

## Description

Convert Product Requirements Documents (PRDs), feature specs, epics, design sprint outputs, and product briefs into phased implementation plans organized as vertical slices or tracer bullets. Use when a user asks to brea


## Original SKILL.md

---
name: prd-to-plan
description: Convert Product Requirements Documents (PRDs), feature specs, epics, design sprint outputs, and product briefs into phased implementation plans organized as vertical slices or tracer bullets. Use when a user asks to break requirements into build phases, create a local ./plans/ Markdown plan, identify durable architecture decisions before implementation, translate product requirements into end-to-end development slices, plan incremental verification, or structure feature delivery around complete user-visible layers instead of technical components.
---

# PRD To Plan

## Core Purpose

Convert a PRD into an actionable implementation plan that can be built and verified incrementally. Prefer vertical slices: each phase should cut through UI, API, data, tests, and observability only as much as needed to prove a complete user or system outcome.

## Discovery

Before writing the plan:

1. Read the PRD, parent epic, architecture notes, ADRs, UX/design sprint artifacts, and existing plans when provided or discoverable.
2. Identify users, workflows, acceptance criteria, non-functional requirements, constraints, and explicit out-of-scope items.
3. Identify durable decisions needed before coding: data model, integration boundaries, authorization model, deployment assumptions, observability, and migration strategy.
4. Inspect the repository enough to name likely files, modules, commands, frameworks, and tests.
5. Ask concise clarifying questions only when missing information blocks a safe plan.

## Design Sprint Lens

Use the design sprint frame when the PRD is still fuzzy or when planning prototype-first delivery:

- Understand: define challenge, sprint questions, user journey, and target area.
- Diverge: list solution options, inspiration, and alternative flows.
- Decide: choose the thin target workflow and storyboard the first tracer bullet.
- Prototype: plan the minimal realistic facade or working path.
- Test: define user, QA, and technical validation signals.

Load `references/design-sprint-plan.md` when the user asks for a design sprint plan or the PRD needs discovery/prototyping before implementation.

## Output Location

When saving a plan, write it under:

```text
./plans/
```

Use filename format:

```text
{feature-or-prd-name}-implementation-plan.md
```

Use lowercase hyphen-case. If the user asks only for chat output, provide the full Markdown plan without writing a file.

## Planning Rules

- Do not split phases by technical component alone, such as "backend phase" then "frontend phase".
- Use vertical slices that deliver observable value or reduce the highest implementation risk.
- Put durable architecture decisions before slices that depend on them.
- Keep each phase independently verifiable.
- Include files, tests, commands, data changes, risks, and rollback or recovery notes when relevant.
- Preserve traceability from PRD requirement IDs or acceptance criteria to implementation phases.
- If the PRD includes design sprint outputs, map tested prototype learnings into phase goals.

## Required Output

Use this structure for the generated plan:

```markdown
# Implementation Plan: [Feature Name]

## Source Inputs

- PRD: [path or title]
- Epic/Product Brief: [path or title]
- Architecture/ADRs: [path or title]
- Design Sprint Artifacts: [path or title]

## Product Outcome

[One paragraph describing the target user/business outcome.]

## Requirements Traceability

| Requirement | Source | Plan Coverage |
| --- | --- | --- |
| REQ-001 | [PRD section] | Phase 1, Phase 2 |

## Durable Decisions Before Build

| Decision | Options | Recommendation | Needed By |
| --- | --- | --- | --- |
| [Decision] | [Options] | [Recommendation] | Phase [N] |

## Vertical Slice Strategy

[Explain the tracer-bullet ordering and why the first slice proves the riskiest or most central workflow.]

## Phased Plan

### Phase 0: Readiness And Decisions

- [ ] [Decision, setup, spike, or alignment task.]
- [ ] Verify: [Command, review, approval, or artifact.]

### Phase 1: Tracer Bullet - [Thin End-To-End Outcome]

- [ ] [End-to-end task touching only the minimum UI/API/data/test surface.]
- [ ] Files: `[path]`, `[path]`
- [ ] Verify: [Command and expected result.]
- [ ] Requirement coverage: [REQ IDs.]

### Phase 2: Expand Core Flow

- [ ] [Next vertical slice.]
- [ ] Files: `[path]`, `[path]`
- [ ] Verify: [Command and expected result.]
- [ ] Requirement coverage: [REQ IDs.]

### Phase 3: Edge Cases, Hardening, And Observability

- [ ] [Validation, permissions, failure modes, metrics, alerts, accessibility, performance.]
- [ ] Verify: [Command and expected result.]

### Phase 4: Release Readiness

- [ ] [Docs, rollout, migrations, feature flags, support notes, post-release checks.]
- [ ] Verify: [Final validation command.]

## Test Plan

| Test Type | Coverage | Command/Method |
| --- | --- | --- |
| Unit | [Coverage] | `[command]` |
| Integration | [Coverage] | `[command]` |
| E2E/User | [Coverage] | `[command or protocol]` |

## Risks And Mitigations

- **Risk**: [Risk.] **Mitigation**: [Mitigation.]

## Rollback Or Recovery

- [Rollback or recovery path for data, configuration, feature flags, and deployment.]

## Open Questions

- [Question, owner, and blocking phase.]
```

## Quality Bar

- The first implementation slice must prove a real end-to-end path, even if narrow.
- Every phase must include verification.
- Every major PRD requirement must map to at least one phase or be explicitly deferred.
- Architecture decisions must be captured before dependent implementation work.
- Plans must be concrete enough for a developer or agent to execute without re-planning from scratch.
