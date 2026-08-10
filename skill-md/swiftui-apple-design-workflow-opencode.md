---
name: swiftui-apple-design-workflow
display_name: swiftui-apple-design-workflow
platform: OpenCode
category: Software engineering and app building
---

# swiftui-apple-design-workflow - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `swiftui-apple-design-workflow` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Orchestrate a human-governed Apple app lifecycle from requirements through UX, visual design, SwiftUI architecture, implementation, accessibility, build, testing, performance, and release readiness for iOS, iPadOS, and m

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the swiftui-apple-design-workflow skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `swiftui-apple-design-workflow` |
| Canonical name | `swiftui-apple-design-workflow` |
| Platform | `OpenCode` |
| Category | Software engineering and app building |

## Description

Orchestrate a human-governed Apple app lifecycle from requirements through UX, visual design, SwiftUI architecture, implementation, accessibility, build, testing, performance, and release readiness for iOS, iPadOS, and m


## Original SKILL.md

---
name: swiftui-apple-design-workflow
description: Orchestrate a human-governed Apple app lifecycle from requirements through UX, visual design, SwiftUI architecture, implementation, accessibility, build, testing, performance, and release readiness for iOS, iPadOS, and macOS. Use at the start of a new app or major feature when individually callable specialists must produce evidence, independent reviewers must verify each stage, and a human must explicitly approve every transition through apple-build-supervisor.
---

# SwiftUI Apple Design Workflow

Coordinate specialists; do not replace them. Read `references/stages.md` and `references/skill-router.md` before starting a governed run.

## Start

1. Read the project `AGENTS.md` chain and determine whether the work is new or brownfield.
2. Record platforms, deployment targets, repository, schemes, constraints, acceptance criteria, human approver, worker identity, reviewer identity, model, effort, and permissions. Never substitute any silently.
3. Initialize an approval ledger with `apple-build-supervisor/scripts/supervise.py init`.
4. Start only stage 1. The supervisor must refuse later stages until the preceding stage is `HUMAN_APPROVED`.

## Per-Stage Cycle

1. Invoke the worker skill named in `references/stages.md`.
2. Require concrete artifacts and fresh evidence.
3. Mark `WORKER_READY` in the ledger.
4. Assign a different, cold reviewer with no app-code editing authority.
5. Record `PASS`, `REVISE`, or `BLOCKED` plus the review report.
6. If the agent passes, pause for explicit human review. Silence is not approval.
7. Advance only after the supervisor records both agent `PASS` and human `APPROVE`.

Run no more than three worker-review rounds per stage. Stop after two materially identical failures, oscillation, or growing blast radius. Never weaken a check to make a stage pass.

## Runtime Portability

- Use native subagents when the runtime supports isolated roles.
- Otherwise execute the same roles sequentially with separate prompts and artifact handoffs.
- Parallelize independent read-only discovery only. Sequence writers unless isolated worktrees prevent overlap.
- Use installed Codex Apple specialists when available; otherwise route build actions through `apple-platform-build`.

## Completion

After all ten stages are human-approved, require a fresh end-to-end agent review and final human release approval. Report verified, inspected, and unverified claims separately. Never treat prior stage approvals alone as release authorization.

## Output

Return the ledger path, current stage, worker artifact paths, reviewer report, evidence commands and results, outstanding risks, invalidated approvals, and the exact human decision required next.
