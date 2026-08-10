---
name: seed
display_name: seed
platform: Codex
category: General and specialized workflows
---

# seed - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `seed` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Universal, host-neutral adaptation of Christopher Kahler's SEED project incubator for turning raw ideas into type-aware, quality-gated PLANNING.md artifacts and optional PAUL-managed builds. Use when the user invokes SEE

## How To Use It In Codex

In Codex, click the chat box, press /, choose seed, then write the task. Fallback prompt: Use the seed skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `seed` |
| Canonical name | `seed` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Universal, host-neutral adaptation of Christopher Kahler's SEED project incubator for turning raw ideas into type-aware, quality-gated PLANNING.md artifacts and optional PAUL-managed builds. Use when the user invokes SEE


## Original SKILL.md

---
name: seed
description: Universal, host-neutral adaptation of Christopher Kahler's SEED project incubator for turning raw ideas into type-aware, quality-gated PLANNING.md artifacts and optional PAUL-managed builds. Use when the user invokes SEED; wants guided ideation for an application, workflow, client project, utility, or campaign; asks to resume, assess, graduate, launch, or list ideas; or needs a plan rich enough to hand to PAUL without repeating discovery.
---

# SEED

Turn an idea into a decision-ready plan through collaborative, type-aware exploration.

## Portability Contract

- Use conversation and local files available on the current host; do not require Claude slash commands.
- The coach offers concrete options and recommendations instead of firing a questionnaire.
- Ask one focused question group at a time. Reuse known facts and mark assumptions visibly.
- Do not create, move, delete, initialize git, or launch PAUL project files until the user requests that operation and confirms the target.
- BASE registration is optional and never blocks ideation or PAUL handoff.

## Route the Request

| Request | Operation |
|---|---|
| Raw idea or `$seed` | Ideate |
| Continue an interrupted idea | Resume |
| See idea pipeline | Status |
| Turn a mature idea into a project | Graduate |
| Graduate and start managed delivery | Launch to PAUL |
| Add a reusable project category | Add type |

## Ideate

1. Determine the project type from evidence or ask the user to choose: `application`, `workflow`, `client`, `utility`, or `campaign`.
2. Load that type's `config.md` and `guide.md` under `references/upstream-framework/data/<type>/`.
3. Set the matching rigor: deep, standard, tight, or creative.
4. Explore the sections collaboratively. Offer 2-3 plausible answers when the user is stuck; record decisions, assumptions, risks, and unresolved questions.
5. Populate the matching planning template under `references/upstream-framework/templates/` with real content.
6. Run the graduation gate from `references/upstream-framework/checklists/planning-quality.md`.
7. If the plan is not mature, identify the smallest missing decision and continue ideation. Do not fabricate completion.

## Planning Output

The plan must state:

- problem, target users, core value, and measurable outcome;
- scope, non-goals, requirements, and major features or deliverables;
- constraints, risks, assumptions, and open questions;
- architecture or delivery approach appropriate to the type;
- milestones or phases with observable completion;
- verification and acceptance expectations;
- recommended skills from the type loadout, adjusted to what is actually installed.

## Resume and Status

Inspect existing SEED planning artifacts and reconcile them with current files. Show project type, maturity, completed sections, blocking decisions, and exactly one next action. Do not trust stale status without evidence.

## Graduate

1. Confirm the destination and whether to move or copy the planning artifact.
2. Re-run the quality gate.
3. Create a clear project root and README only as requested.
4. Initialize git only when explicitly included.
5. Preserve the source plan or record its new location; do not lose ideation history.

## Launch to PAUL

1. Graduate first.
2. Invoke PAUL initialization against the completed `PLANNING.md`.
3. Map outcomes to roadmap phases and retain SEED decisions as project context.
4. Let PAUL create the first bounded plan and wait for explicit APPLY approval.

## References

- Type guides, loadouts, templates, and the quality gate are under [upstream-framework](references/upstream-framework/).
- Read [upstream.md](references/upstream.md) for provenance and universal differences.
