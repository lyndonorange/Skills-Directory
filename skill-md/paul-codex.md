---
name: paul
display_name: paul
platform: Codex
category: General and specialized workflows
---

# paul - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `paul` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Universal, host-neutral adaptation of Christopher Kahler's PAUL (Plan-Apply-Unify Loop) for acceptance-driven work with durable project state. Use when the user invokes PAUL or asks to initialize, plan, approve, apply, v

## How To Use It In Codex

In Codex, click the chat box, press /, choose paul, then write the task. Fallback prompt: Use the paul skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `paul` |
| Canonical name | `paul` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Universal, host-neutral adaptation of Christopher Kahler's PAUL (Plan-Apply-Unify Loop) for acceptance-driven work with durable project state. Use when the user invokes PAUL or asks to initialize, plan, approve, apply, v


## Original SKILL.md

---
name: paul
description: Universal, host-neutral adaptation of Christopher Kahler's PAUL (Plan-Apply-Unify Loop) for acceptance-driven work with durable project state. Use when the user invokes PAUL or asks to initialize, plan, approve, apply, verify, reconcile, pause, resume, hand off, audit, or report progress for work tracked in a `.paul/` directory; when every implementation plan must close with a summary and state update; or when a project needs explicit acceptance criteria, scope boundaries, checkpoints, and fresh verification evidence across coding agents.
---

# PAUL

Run a durable `PLAN -> APPLY -> UNIFY` loop without assuming a specific agent, model, IDE, command syntax, or tool API.

## Portability Contract

- Use the host's available read, search, edit, shell, test, and user-input capabilities.
- Follow the applicable repository instructions before touching files. PAUL does not override AGENTS.md, permissions, safety policy, or project conventions.
- Treat `$paul`, `PAUL init`, `PAUL plan`, and similar natural-language calls as portable operations. Do not require Claude-only `/paul:*` commands.
- If the host cannot edit files or run verification, produce draft artifacts and disclose what was not written or verified.
- Keep model, vendor, agent role, delegation, and effort choices explicit. Never silently substitute them.
- Delegate only when the user and host policy allow it. The core loop must work in one agent session.
- Keep git commit, push, pull request, deployment, release, and other external actions separately authorized. PLAN approval authorizes APPLY only for the approved scope.

## Route the Request

Inspect `.paul/` before acting.

| Request or state | Operation |
|---|---|
| No `.paul/`; user asks to adopt PAUL | Initialize |
| Existing `.paul/`; new session | Resume |
| User asks what is happening or what is next | Progress |
| No active plan and work is requested | PLAN |
| Plan exists but lacks explicit approval | Present the plan and wait |
| Approved plan is ready | APPLY |
| APPLY is complete but no summary exists | UNIFY |
| User needs to stop or switch context | Pause / handoff |
| User requests acceptance testing | Verify |
| User requests another PAUL operation | Read [commands.md](references/commands.md) |

If state and artifacts disagree, stop forward execution, report the mismatch, and reconcile them from evidence.

## Initialize

Initialization creates durable project files, so confirm the user wants PAUL added to that project.

1. Read project instructions, primary docs, manifests, and current structure.
2. If `PLANNING.md` or an equivalent brief exists, offer to derive PAUL state from it.
3. Gather only missing information: project value, target users, deliverables, constraints, success measures, and near-term phases. Ask one focused question at a time when an answer materially changes the artifacts.
4. Create `.paul/phases/` and the artifacts defined in [artifacts.md](references/artifacts.md).
5. Populate real content; do not leave template placeholders.
6. Set the loop to `IDLE` and suggest exactly one next action: create the first plan.

Do not block standalone PAUL usage on optional ecosystem software.

## PLAN

PLAN defines a bounded, executable unit of work. It never authorizes implementation by itself.

1. Read `.paul/PROJECT.md`, `ROADMAP.md`, `STATE.md`, the most relevant prior summary, applicable repo instructions, and affected source files.
2. Refuse to open a new plan while a prior APPLY or UNIFY is incomplete unless the user explicitly chooses to supersede it. Record supersession.
3. Classify scope:
   - `quick-fix`: one narrow change, one or two files, no structural decision.
   - `standard`: two or three coherent tasks with full boundaries and verification.
   - `complex`: multiple subsystems, architecture decisions, or more than three tasks. Split into smaller vertical plans when practical.
4. Write a PLAN using [artifacts.md](references/artifacts.md). Require:
   - objective, purpose, and output;
   - Given/When/Then acceptance criteria;
   - tasks with exact files, action, fresh verification, and linked done criteria;
   - explicit `DO NOT CHANGE` and out-of-scope boundaries for standard or complex work;
   - blocking human checkpoints only where automation cannot settle intent, a decision, or experiential verification.
5. Run a coherence check against project requirements, current decisions, roadmap scope, affected files, and applicable permissions.
6. Update state to `PLAN`, record the plan path, and present material assumptions and risks.
7. Wait for explicit approval before APPLY. Approval must identify this plan or clearly refer to the plan just presented.

## APPLY

1. Re-read the approved plan and confirm its hash or content has not materially changed since approval. If it changed, present the delta for renewed approval.
2. Confirm every required specialized skill or workflow named by the plan is available. Do not substitute a different one silently.
3. Execute tasks in order unless the plan explicitly defines safe parallel work.
4. For each task, use the Execute/Qualify loop:
   - Execute only the listed action within boundaries.
   - Report `DONE`, `DONE_WITH_CONCERNS`, `NEEDS_CONTEXT`, or `BLOCKED`.
   - Run the listed verification fresh and inspect its output.
   - Re-read the produced artifacts and compare them with the task and linked acceptance criteria.
   - Score `PASS`, `GAP`, or `DRIFT`; repair gaps within scope and requalify.
5. Stop at a blocking checkpoint. Never infer approval, a user-only action, or a product decision.
6. When verification exposes a problem, classify it before changing work:
   - `intent`: the desired outcome changed; supersede or revise the plan.
   - `spec`: acceptance criteria or tasks were wrong; fix the plan before implementation.
   - `code`: implementation differs from the approved plan; repair and reverify.
7. Log deviations, concerns, blockers, evidence, and changed files for UNIFY.
8. Move state to `UNIFY` only after all tasks pass or unresolved results are documented and the user accepts closure with those results.

## UNIFY

UNIFY is mandatory after APPLY.

1. Re-read the plan, actual diff or produced artifacts, verification output, and APPLY log.
2. Evaluate every acceptance criterion as `PASS`, `FAIL`, or `NOT VERIFIED`, with evidence.
3. Create the matching `SUMMARY.md` using [artifacts.md](references/artifacts.md). Record actual work, deviations, decisions, concerns, blockers, files changed, and verification evidence.
4. Update `.paul/PROJECT.md` when requirements or durable decisions changed.
5. Update `.paul/ROADMAP.md` only when plan or phase status changed.
6. Update `.paul/STATE.md`, clear the active plan when closed, and set the next action.
7. Sync `.paul/paul.toml` and append an entry to `.paul/ledger.toml` if those files are in use.
8. Report one next action. Do not commit, push, open a PR, deploy, release, or tag unless separately authorized.

Never call a loop complete without a summary and fresh verification evidence. If verification could not run, close only as incomplete and say why.

## Checkpoints

Use the smallest necessary blocking checkpoint:

- `checkpoint:decision`: a human choice changes architecture, scope, risk, or product behavior.
- `checkpoint:human-verify`: automation is complete; a human must judge visual, interactive, audio, physical-device, or experiential behavior.
- `checkpoint:human-action`: no safe tool or API can perform an unavoidable action such as MFA or account approval.

Automate available builds, tests, file operations, and diagnostics before asking the user. After a checkpoint failure, use intent/spec/code classification.

## Continuity and Progress

- Pause by creating a dated `.paul/HANDOFF-*.md` and updating STATE with the exact stop point, evidence, dirty-worktree facts, blockers, and one resume action.
- Resume by reading project instructions, STATE, the newest relevant handoff, active PLAN, and current worktree evidence. Reconcile stale handoffs instead of trusting them blindly.
- Progress must show the active milestone, phase, plan, loop position, blockers, and exactly one recommended next action.
- Keep STATE concise. Put historical detail in summaries, handoffs, decisions, or the ledger.

## Specialized Flows

Use `.paul/SPECIAL-FLOWS.md` only when the project needs named skills or domain gates. Record exact skill names, when they trigger, whether they are required, and how invocation is verified. Missing required flows block APPLY; optional flows never justify silent substitution.

## References

- Read [artifacts.md](references/artifacts.md) whenever creating, repairing, or validating `.paul/` files.
- Read [commands.md](references/commands.md) for auxiliary PAUL operations beyond the core loop.
- Read [upstream.md](references/upstream.md) for provenance, the pinned source revision, and universal adaptation differences.
- The complete pinned upstream commands, workflows, rules, templates, and references are preserved under [upstream-framework](references/upstream-framework/) for on-demand compatibility review; the host-neutral contracts above remain authoritative for universal execution.
