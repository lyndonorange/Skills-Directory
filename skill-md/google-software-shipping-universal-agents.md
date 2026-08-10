---
name: google-software-shipping
display_name: google-software-shipping
platform: Universal Agents
category: General and specialized workflows
---

# google-software-shipping - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `google-software-shipping` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Ship production software through a Google-inspired define, plan, build, verify, review, and release lifecycle adapted from addyosmani/agent-skills. Use when Codex must take a feature, fix, migration, API, UI, or service

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the google-software-shipping skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `google-software-shipping` |
| Canonical name | `google-software-shipping` |
| Platform | `Universal Agents` |
| Category | General and specialized workflows |

## Description

Ship production software through a Google-inspired define, plan, build, verify, review, and release lifecycle adapted from addyosmani/agent-skills. Use when Codex must take a feature, fix, migration, API, UI, or service


## Original SKILL.md

---
name: google-software-shipping
description: Ship production software through a Google-inspired define, plan, build, verify, review, and release lifecycle adapted from addyosmani/agent-skills. Use when Codex must take a feature, fix, migration, API, UI, or service change from an idea or specification through implementation and a release-ready handoff with evidence. Also use for requests to ship software using Google engineering practices. Not for a narrow lookup, prose-only edit, or isolated code explanation that does not require a delivery lifecycle.
---

# Google Software Shipping

Guide a software change from intent to a safe release. Preserve project-local instructions and choose only the gates proportional to the change.

## Source and scope

This workflow adapts the lifecycle and quality gates from the MIT-licensed `addyosmani/agent-skills` repository at revision `4e8bd9fde4a38cd009053e649f4cdc7cd36b568b`. Read [references/upstream-map.md](references/upstream-map.md) when selecting phase-specific practices or tracing provenance.

## Step 0: Establish sufficiency

1. Read the request, repository instructions, existing plans, and relevant code.
2. Identify the desired user outcome, constraints, release target, and proof required.
3. If ambiguity is workable, state one concise assumption and continue. If it would produce a structurally wrong result or cross an unapproved production boundary, ask no more than three questions and pause.
4. Scale the lifecycle: a tiny safe fix may need a one-paragraph spec; a risky migration needs explicit rollout and rollback plans.

## Workflow routing

| Phase | Use when | Required output or evidence |
|---|---|---|
| Define | Outcome or requirements are unclear | Scope, acceptance criteria, non-goals |
| Plan | Work spans multiple meaningful steps | Ordered, verifiable tasks and dependencies |
| Build | Behavior changes | Thin vertical slices; tests first where practical |
| Verify | Any implementation changed | Fresh relevant test, build, lint, or runtime evidence |
| Review | Before handoff or merge | Correctness, security, maintainability, performance findings |
| Ship | A release or deployment is in scope | Readiness, rollout, observability, rollback, owner handoff |

## Execute the lifecycle

### 1. Define

- Translate the request into observable behavior and acceptance criteria.
- Record non-goals and compatibility constraints.
- For public interfaces, specify contracts, failure semantics, and boundary validation before implementation.

### 2. Plan

- Break work into small vertical slices that each leave the system coherent.
- Name affected paths, dependencies, validation commands, and rollback points.
- Surface irreversible or production-impacting actions for user approval before performing them.

### 3. Build

- Inspect existing patterns before adding abstractions.
- Implement the smallest complete slice, then verify it before starting the next.
- Prefer red-green-refactor for logic and bug fixes. Preserve security, accessibility, and data-integrity boundaries even for prototypes.
- Keep commits atomic only when the user has authorized commits; never infer permission to publish.

### 4. Verify

- Run fresh checks proportional to risk. Treat passing output as evidence, not memory or expectation.
- Reproduce bugs before fixing them and add regression coverage when feasible.
- For browser behavior, verify the live runtime, console, network, accessibility, and relevant performance signals.

### 5. Review

- Review the diff for correctness, tests, clarity, security, and operational impact.
- Measure performance before optimizing.
- Simplify only after understanding why existing code exists; preserve behavior and contracts.
- Resolve blockers and major findings, then rerun affected verification.

### 6. Ship

- Confirm acceptance criteria and the repository definition of done.
- Prepare staged rollout, monitoring signals, and a practical rollback path when deployment is involved.
- Include migration, deprecation, documentation, ADR, and observability work when the change creates those obligations.
- Report what changed, fresh evidence, residual risks, and the exact next action. Do not claim deployment, merge, or publication unless it actually occurred.

## Completion gate

Do not call the work complete until:

- acceptance criteria are satisfied or explicitly deferred;
- relevant fresh verification passes;
- review findings are resolved or disclosed;
- rollout and rollback are defined when production changes are in scope;
- the handoff names changed artifacts, evidence, and remaining risks.

## Examples

**Feature:** “Ship organization invitations.” Define invite behavior and expiry, plan API/UI/data slices, implement with tests, review auth boundaries, and prepare staged rollout plus monitoring.

**Bug fix:** “Fix duplicate charges.” Reproduce the failure, define the invariant, add a failing regression test, implement the smallest fix, review idempotency and data repair risk, then provide verified release guidance.

**Migration:** “Replace the legacy cache.” Specify compatibility and performance targets, phase the migration behind a safe switch, measure before and after, and document rollback and deprecation cleanup.

## Gotchas

- Do not turn every change into a heavyweight ceremony; preserve the gates while scaling the artifacts.
- “Ship” does not authorize commits, pushes, merges, deployments, or external messages unless the user placed those actions in scope.
- Passing unit tests alone may not prove browser, migration, security, or production readiness.
- Feature flags require an owner and removal condition or they become permanent complexity.
- Small diffs can still be high risk when they affect authentication, billing, migrations, data deletion, or public contracts.
