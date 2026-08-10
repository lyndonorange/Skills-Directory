---
name: agentic-os-workflow
display_name: agentic-os-workflow
platform: Codex
category: General and specialized workflows
---

# agentic-os-workflow - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `agentic-os-workflow` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Universal router for the complete Christopher Kahler Agentic OS workflow across SEED, PAUL, CARL, BASE, AEGIS, and Skillsmith. Use when the user asks for the full PAUL/CARL ecosystem, Agentic OS, an end-to-end idea-to-bu

## How To Use It In Codex

In Codex, click the chat box, press /, choose agentic-os-workflow, then write the task. Fallback prompt: Use the agentic-os-workflow skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `agentic-os-workflow` |
| Canonical name | `agentic-os-workflow` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Universal router for the complete Christopher Kahler Agentic OS workflow across SEED, PAUL, CARL, BASE, AEGIS, and Skillsmith. Use when the user asks for the full PAUL/CARL ecosystem, Agentic OS, an end-to-end idea-to-bu


## Original SKILL.md

---
name: agentic-os-workflow
description: Universal router for the complete Christopher Kahler Agentic OS workflow across SEED, PAUL, CARL, BASE, AEGIS, and Skillsmith. Use when the user asks for the full PAUL/CARL ecosystem, Agentic OS, an end-to-end idea-to-build-to-audit workflow, which ecosystem component should run next, or verification that all six framework and skill components are present across configured agent runtimes.
---

# Agentic OS Workflow

Route each concern to one owner and keep optional infrastructure from blocking the core delivery loop.

## Component Ownership

| Component | Primary job | Required for core delivery? |
|---|---|---|
| SEED | Turn a raw idea into a type-aware, quality-gated `PLANNING.md` | For unclear or new ideas |
| PAUL | Plan, approve, apply, verify, and unify bounded work | Yes |
| CARL | Resolve only the reusable rules and decisions relevant now | Yes when configured; otherwise optional |
| BASE | Graph-backed workspace, code, project, decision, and health context | Optional runtime |
| AEGIS | Diagnose codebase risk and design safe remediation | At major review or risk gates |
| Skillsmith | Design, scaffold, distill, and audit skills | When the product is a skill or workflow |

## End-to-End Route

1. **Preflight:** read repository instructions; inspect existing `PLANNING.md`, `.paul/`, `.carl/`, `.base/`, and prior audit artifacts; identify the user's requested authorization level.
2. **Incubate:** use SEED when the desired product or workflow is still ambiguous. Skip it when requirements are already complete.
3. **Initialize delivery:** derive PAUL project state and roadmap from the approved planning source.
4. **Load behavior:** resolve CARL at the start of a materially different task, after compaction, or after config changes. Apply only non-conflicting rules.
5. **Enrich context:** use BASE only when its binary and graph are actually installed and healthy. Otherwise proceed with current repository evidence and disclose that BASE automation is absent.
6. **Deliver:** run PAUL PLAN, wait for explicit approval, APPLY with fresh verification, then mandatory UNIFY.
7. **Audit:** use AEGIS at milestone, release, takeover, or high-risk change gates. Audit remains read-only until fixes are requested.
8. **Remediate:** translate approved AEGIS findings into new PAUL plans; never implement directly from an unapproved audit report.
9. **Evolve skills:** use Skillsmith plus the host-native skill creator when a reusable skill is the deliverable.

## Routing Rules

- Do not load all components for every request. Invoke the smallest owner that matches the current need.
- Do not substitute BASE, PAUL, CARL, or another named component silently. State when an optional runtime is unavailable.
- Do not use multi-agent execution unless the user explicitly requests delegation and the host permits it.
- Do not infer git, deployment, release, account, licensing, hook-installation, or external-service authority from plan approval.
- AEGIS cannot authorize remediation; CARL cannot grant permissions; BASE context is not source-of-truth proof; SEED maturity does not approve implementation.

## Installation Verification

Run the bundled checker from this skill's directory:

```bash
python3 scripts/ecosystem_check.py
```

The checker verifies all six canonical skills, complete PAUL/CARL framework assets, SEED type resources, Skillsmith specs, AEGIS/BASE source checkouts, pinned revisions, and configured runtime projections. BASE binary status is reported separately because its source checkout and skill can be present without licensed runtime activation or hooks.

## References

- Read [workflow.md](references/workflow.md) for handoffs, required artifacts, and acceptance gates.
- Read [install-manifest.json](references/install-manifest.json) for pinned upstream revisions and package status.
