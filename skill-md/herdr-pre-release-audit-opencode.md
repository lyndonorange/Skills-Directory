---
name: herdr-pre-release-audit
display_name: herdr-pre-release-audit
platform: OpenCode
category: General and specialized workflows
---

# herdr-pre-release-audit - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `herdr-pre-release-audit` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Audit herdr release readiness by comparing commits since the base release against next-release changelog and docs. Use when asked to run or apply the repo's pre-release audit, validate docs/next before release, inspect i

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the herdr-pre-release-audit skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `herdr-pre-release-audit` |
| Canonical name | `herdr-pre-release-audit` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Audit herdr release readiness by comparing commits since the base release against next-release changelog and docs. Use when asked to run or apply the repo's pre-release audit, validate docs/next before release, inspect i


## Original SKILL.md

---
name: herdr-pre-release-audit
description: Audit herdr release readiness by comparing commits since the base release against next-release changelog and docs. Use when asked to run or apply the repo's pre-release audit, validate docs/next before release, inspect issue refs that release CI will close, or finalize release docs for herdr.
---

# Herdr Pre-release Audit

Use this skill only inside the herdr repository.

Read `references/pre-release-audit.md` and follow its workflow. Treat it as the source of truth for:

- choosing the release base ref
- inspecting first-parent history and merged PRs
- auditing `docs/next/CHANGELOG.md`
- auditing `docs/next/README.md` and staged website docs
- checking issue reference lines
- deciding when to run `just release-docs-check`
- producing the final release-readiness report

Do not edit files during the audit unless the user explicitly asks to apply fixes. When applying fixes, keep changes scoped to the files named in the reference workflow.
