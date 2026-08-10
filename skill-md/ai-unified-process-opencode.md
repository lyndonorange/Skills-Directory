---
name: ai-unified-process
display_name: ai-unified-process
platform: OpenCode
category: Software engineering and app building
---

# ai-unified-process - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `ai-unified-process` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Orchestrate a requirements-centered, human-governed software lifecycle for a solo builder coordinating multiple AI agents. Use when the user explicitly requests AI Unified Process or AIUP, wants to take a new or existing

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the ai-unified-process skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `ai-unified-process` |
| Canonical name | `ai-unified-process` |
| Platform | `OpenCode` |
| Category | Software engineering and app building |

## Description

Orchestrate a requirements-centered, human-governed software lifecycle for a solo builder coordinating multiple AI agents. Use when the user explicitly requests AI Unified Process or AIUP, wants to take a new or existing


## Original SKILL.md

---
name: ai-unified-process
description: "Orchestrate a requirements-centered, human-governed software lifecycle for a solo builder coordinating multiple AI agents. Use when the user explicitly requests AI Unified Process or AIUP, wants to take a new or existing app from intent through implementation and release, wants agents coordinated through approved change packets, or needs brownfield recovery, risk-scaled independent review, verification, rollback, and post-release learning."
---

# AI Unified Process

## Purpose

Coordinate product work from intent through learning while keeping the human user in authority. Preserve useful AIUP concepts—Inception, Elaboration, Construction, Transition; greenfield and brownfield routes; living requirements; stable IDs; use cases; and traceability—without forcing a technology stack or treating generated documents as unquestionable truth.

Act as the orchestrator. Delegate bounded work to specialist agents when agent tools are available, preserve their independence for review, and keep approvals with the user.

## Start Every Workflow

Ask exactly:

> Are we creating something new, or working on an existing app?

Do not inspect the repository, create artifacts, or edit code until the user answers. For a resumed AIUP workflow with a recorded route, state the recorded route and ask whether it is still correct.

After the answer:

- Read the applicable project instructions before touching files.
- Discover and reuse the project's existing documentation conventions.
- Use `docs/aiup/` only when the project has no suitable documentation location.
- Read [references/workflow-modes.md](references/workflow-modes.md) and follow the selected route.

## Keep the Human in Authority

Treat the user as product owner, requirements owner, release authority, and final risk acceptor.

- Ask for approval of the initial change packet before code edits.
- Let approved low-risk work proceed without another phase-by-phase coding approval while scope and risk remain unchanged.
- For medium-risk work, use initial packet approval for planning, then obtain explicit construction approval after the implementation plan and affected boundaries are concrete.
- For high-risk work, use initial packet approval for discovery and planning, obtain explicit construction approval before edits, and require additional approval before each production migration, rollout expansion, irreversible step, or legacy cutoff.
- Reopen approval whenever scope, risk, assumptions, affected data, public interfaces, or external side effects materially change.
- Obtain explicit authorization before committing, pushing, opening or merging a pull request, deploying, publishing, applying a migration, or performing another external or destructive action.
- Never let an implementation agent approve its own business interpretation or satisfy the independent-review gate.
- Stop on unresolved business ambiguity, conflicting requirements, unclear authority, unverifiable critical claims, or work outside the approved boundary.

Read [references/risk-and-approvals.md](references/risk-and-approvals.md) before classifying risk, assigning reviewers, or preparing release.

## Use a Governed Change Packet

Make one bounded change packet the unit of implementation, review, release, rollback, and learning. Read [references/change-packet.md](references/change-packet.md) before creating or updating one.

The packet must record:

- Desired outcome and non-goals
- Greenfield or brownfield route
- Requirements, use cases, and acceptance criteria
- Evidence and uncertainty
- In-scope, out-of-scope, and writable paths
- Risk classification and safety checks
- Agent assignments and independent-review depth
- Verification evidence
- Release and rollback conditions
- Post-release observations and learning

Run `scripts/validate_change_packet.py <packet>` after creating or changing a packet. Use `--strict` before release readiness review. Treat it only as a structural governance preflight; it cannot establish that evidence is true, sufficient, or release-ready, and it never replaces human approval or independent-agent review.

## Run the Lifecycle

### 1. Inception — Define the outcome

- Clarify the problem, affected people, valuable outcome, success signals, and non-goals.
- Prefer one small releasable outcome over a broad feature inventory.
- Record assumptions as assumptions; do not promote AI guesses into requirements.
- Obtain human approval of the behavioral baseline.

### 2. Elaboration — Establish evidence and boundaries

- For greenfield work, derive a small requirements and use-case baseline from the approved vision.
- For brownfield work, inspect code, tests, documentation, configuration, schema, and runtime evidence as available.
- Label each recovered brownfield claim `Observed`, `Inferred`, `Intended change`, or `Unknown`.
- Add characterization tests before risky changes to poorly understood behavior.
- Create the change packet, classify risk, define acceptance criteria, identify writable paths, and propose agent assignments.
- Obtain approval of the initial packet before implementation.

### 3. Construction — Delegate and implement

- Decompose only the approved packet into bounded specialist tasks with explicit inputs, outputs, dependencies, and verification.
- Give agents the minimum context required and never let one agent's conclusions contaminate an independent review prompt.
- Preserve unrelated user changes and existing project conventions.
- Implement the smallest complete vertical slice.
- Update tests and durable behavior artifacts with the code; do not leave specifications describing behavior that no longer exists.
- Pause and reopen approval if risk or scope increases.

### 4. Independent review and verification

- Require another agent to review every meaningful code change.
- Exempt only trivial edits that do not change behavior, tests, configuration, dependencies, data, interfaces, accessibility, security, performance, or release output.
- Use a quick diff-focused review for low-risk changes, a broader dependency and edge-case review for medium risk, and an adversarial safety and rollback review for high risk.
- Give the reviewer the approved packet, relevant artifacts, and resulting diff—not the implementer's self-assessment.
- Resolve findings, rerun affected verification, and record the review result in the packet.
- Never claim completion without fresh requirement, build, test, lint/style, and runtime evidence appropriate to the change.

### 5. Transition — Release deliberately

- Prepare the release procedure, success signals, monitoring window, rollback triggers, rollback steps, and data-recovery implications.
- Obtain explicit user authorization before release or another external effect.
- Prefer staged release, feature flags, reversible migrations, backups, and bounded observation when available.
- Roll back or stop when an approved rollback trigger occurs; do not improvise past the risk boundary.

### 6. Learn and reconcile

- Compare real outcomes with the approved success signals.
- Record surprises, incidents, disproved assumptions, stakeholder feedback, and follow-up work.
- Update the requirement, implementation, test, operating procedure, or rollback decision that reality challenged.
- Close the packet only when its released state and durable artifacts agree, or explicitly record why they do not.

## Preserve Traceability Without Overclaiming

- Prefer traceability from requirement to use case, change packet, tests, implementation locations, review evidence, and release—not the unrealistic promise that every source line maps directly to a requirement.
- Use stable `FR-*`, `NFR-*`, `C-*`, `UC-*`, and `TC-*` identifiers when they improve continuity.
- Reuse existing project identifiers when they already serve the same purpose.
- Keep one authoritative home for each fact; link instead of duplicating.
- Treat tests as important evidence, not infallible truth. Challenge correlated mistakes when the same model generated the specification, code, and tests.

Read [references/compatibility.md](references/compatibility.md) when importing upstream AIUP artifacts, interoperating with AIUP tools, or deciding file locations and identifiers.

## Report State Clearly

At each handoff, state:

- Current phase and route
- Approved packet and risk
- Completed and pending work
- Agent assignments and review status
- Verification evidence and gaps
- Decisions required from the user
- Safest next action

Do not use a high confidence score to hide missing evidence. Name uncertainty directly.
