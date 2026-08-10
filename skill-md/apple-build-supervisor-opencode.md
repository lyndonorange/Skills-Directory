---
name: apple-build-supervisor
display_name: apple-build-supervisor
platform: OpenCode
category: General and specialized workflows
---

# apple-build-supervisor - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `apple-build-supervisor` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Enforce a ten-stage Apple app approval ledger for iOS, iPadOS, and macOS with worker evidence, a different independent agent reviewer, explicit human approval, downstream invalidation, bounded revisions, stall detection,

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the apple-build-supervisor skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `apple-build-supervisor` |
| Canonical name | `apple-build-supervisor` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Enforce a ten-stage Apple app approval ledger for iOS, iPadOS, and macOS with worker evidence, a different independent agent reviewer, explicit human approval, downstream invalidation, bounded revisions, stall detection,


## Original SKILL.md

---
name: apple-build-supervisor
description: Enforce a ten-stage Apple app approval ledger for iOS, iPadOS, and macOS with worker evidence, a different independent agent reviewer, explicit human approval, downstream invalidation, bounded revisions, stall detection, and fresh final release review. Use before starting or advancing any governed app stage, when recording PASS/REVISE/BLOCKED verdicts, when requirements or artifacts change, or when proving that no agent self-approved and no human gate was inferred. The supervisor may update only its ledger; it must never edit or repair app code.
---

# Apple Build Supervisor

Enforce separation of duties. The supervisor may write only the approval ledger and administrative receipts. It must not implement, refactor, debug, or repair the app it governs.

## Initialize

```bash
python3 scripts/supervise.py init \
  --ledger <project>/docs/apple-build-approval.json \
  --project '<name>' --platform ios --platform ipados --platform macos
```

Read `references/ledger-workflow.md` before operating a ledger. Use `status` before every transition.

## Required Transition

For each stage:

1. `start`
2. Worker produces artifacts and evidence.
3. `worker-ready --worker <identity> --evidence <file> ...`
4. A different, cold, non-editing reviewer returns the format in `references/reviewer-contract.md`.
5. `agent-review --reviewer <identity> --verdict PASS|REVISE|BLOCKED --report <file>`
6. On `PASS`, stop and request explicit human review.
7. `human-review --human <identity> --decision APPROVE|REVISE|BLOCK --note '<reason>'`

Only `PASS` followed by `APPROVE` produces `HUMAN_APPROVED`. Human silence, an agent's prediction of human intent, or a prior approval never counts.

## Invalidation and Release

- Run `invalidate` when approved requirements, design, architecture, implementation, or evidence materially changes. The command invalidates that stage and all downstream stages.
- After stages 1–10 are human-approved, use `final-agent-review --verdict PASS|BLOCKED` with a reviewer who was neither a worker nor prior reviewer, then use `final-human-review` only after `PASS`.
- Never hand-edit ledger state. If the ledger and artifacts disagree, invalidate and re-review.

## Rules

- Reviewer identity must differ from worker identity.
- Maximum three worker-review iterations per stage.
- Two consecutive matching failure fingerprints block the stage as stalled.
- `REVISE` returns the stage to `IN_PROGRESS`; `BLOCKED` stops it.
- Waivers must be visible in the human note with owner, reason, risk, and follow-up. A waiver is not evidence.
- Evidence files are hashed when recorded. Changed files invalidate the trustworthiness of the recorded receipt even before the ledger is formally invalidated.
- Report command output and screenshots as files; do not enter secrets in the ledger.

## Completion Output

Return ledger path, release status, stage states, current blockers, invalidations, evidence hashes, reviewer identities, human decisions, and the exact human decision required next.
