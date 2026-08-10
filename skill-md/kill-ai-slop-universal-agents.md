---
name: kill-ai-slop
display_name: kill-ai-slop
platform: Universal Agents
category: General and specialized workflows
---

# kill-ai-slop - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `kill-ai-slop` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Audit or remove generic, inflated, unearned, or structurally careless output in writing, visual design, and software. Use when the user says kill AI slop, de-slop, humanize, remove the AI look, simplify generated code, r

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the kill-ai-slop skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kill-ai-slop` |
| Canonical name | `kill-ai-slop` |
| Platform | `Universal Agents` |
| Category | General and specialized workflows |

## Description

Audit or remove generic, inflated, unearned, or structurally careless output in writing, visual design, and software. Use when the user says kill AI slop, de-slop, humanize, remove the AI look, simplify generated code, r


## Original SKILL.md

---
name: kill-ai-slop
description: Audit or remove generic, inflated, unearned, or structurally careless output in writing, visual design, and software. Use when the user says kill AI slop, de-slop, humanize, remove the AI look, simplify generated code, review vibe-coded work, or asks for a local-only anti-slop gate. Report concrete defects; never guess AI authorship or assign an AI probability.
---

# Kill AI Slop

Treat slop as a quality problem, not an authorship detector. Find observable defects, decide whether each is intentional, and make the smallest change that improves the artifact without erasing voice, visual direction, or working behavior.

## Interface

```text
$kill-ai-slop audit [auto|writing|visual|code] <target>
$kill-ai-slop fix   [auto|writing|visual|code] <target>
```

- Default to `audit auto` for review or ambiguous requests.
- Use `fix` only when the user authorizes editing, rewriting, redesign, or refactoring.
- In `auto`, classify each artifact and use every applicable domain.
- Treat pasted material as the target when no path or URL is supplied.
- Do not broaden scope beyond the request.

## Non-negotiables

1. Never claim an artifact was AI-generated or output an AI probability. There is no dependable technical authorship indicator.
2. Keep deterministic checks local. Do not upload source, prose, screenshots, or findings to external detector services.
3. Preserve facts, intent, voice, brand choices, accessibility, security, and behavior.
4. Never invent evidence, metrics, citations, user quotes, tests, or rationale.
5. Pattern matches are leads, not verdicts. Read the surrounding artifact.
6. Do not flatten deliberate style. A gradient, em dash, passive sentence, abstraction, or card can be correct when it earns its place.
7. In code, correctness, tests, security, and project conventions outrank a scanner score.

## Workflow

### 1. Establish scope

Identify operation, domain, target, output, and constraints. In a repository, read its instructions first. Skip generated output, dependencies, lockfiles, builds, and unrelated work unless included.

### 2. Run local evidence checks

For web/UI source and embedded product copy, run the bundled scanner from this skill directory:

```bash
node scripts/scan.mjs <target>
node scripts/scan.mjs <target> --json
```

Narrow with `--only=01,06`, `--skip=19`, or `--exclude=legacy` when useful.

For program source, prefer a project-pinned `aislop`; otherwise use the installed `aislop@0.14.0`. Run `aislop --help` before first use and never substitute a floating `npx` version.

If a scanner is unavailable, inspect directly and disclose the missing check. Never substitute a remote detector.

### 3. Inspect context

Classify each lead:

- `confirmed`: generic, inflated, misleading, structurally careless, or unearned here.
- `intentional`: defensible for this voice, design system, domain, or repository.
- `uncertain`: requires author, product, or maintainer intent.

Load only what applies:

- Writing: `references/writing.md`
- Visual/UI: `references/taxonomy.md`, `references/detection.md`, `references/fixes.md`
- Programming: `references/programming.md`
- Provenance: `references/upstream.md`

Inspect rendered visuals at relevant platform or viewport states. Source matches cannot prove visual quality.

### 4. Report before changing

Every confirmed finding includes:

```text
location | concrete pattern or defect | contextual judgment | proposed fix | verification
```

Group by domain and severity. Do not pad the report. Say when no confirmed defects remain.

### 5. Apply the minimum effective edit

- Writing: preserve meaning and facts; rewrite only the defective spans.
- Visual: preserve the chosen direction; fix shared tokens or components before scattered call sites.
- Code: preserve APIs and behavior unless a change was approved; follow local idioms.
- Delete redundancy before adding layers.
- Leave intentional hits alone; use narrow suppression only when documenting intent helps the project.
- Avoid unrelated formatting or cleanup.

### 6. Verify the artifact

Re-run the same scans, then check the outcome:

- Writing: facts, meaning, voice, rhythm, and requested format.
- Visual: hierarchy, responsive states, interactions, contrast, focus, and accessible motion in rendered output.
- Code: focused tests, type checks, lint, build, and real boundary behavior as appropriate.

Report before/after counts, intentional remaining hits, and checks actually run. A clean scan does not prove good prose, design, or software.

## Intent-triggered gate

Run this workflow only when explicitly invoked or when the user asks for de-slopping, humanization, generated-work cleanup, AI-tell removal, vibe-code review, or an anti-slop gate.

For CI:

- gate observable local rules, not inferred authorship;
- keep human accountability;
- begin in report-only mode and promote stable rules deliberately;
- allow reviewed, reasoned suppressions;
- never auto-close a contribution merely because it looks AI-like.

## Routing

- Use `humanizer` then `structural-humanizer` for deeper prose passes.
- Use `hallmark` for rendered study, redesign, interaction completeness, and platform-aware visual critique.
- Use the project's language specialist and verification contract for engineering correctness.

## Resources

- `scripts/scan.mjs`: local dependency-free visual/copy scanner.
- `scripts/scan.test.mjs`: scanner regression tests.
- `scripts/rules.ru.mjs`: example scanner extension.
- `references/writing.md`: contextual prose review.
- `references/programming.md`: code review and verification.
- `references/taxonomy.md`, `detection.md`, `fixes.md`: visual tells, false positives, and fixes.
- `references/upstream.md`: pins, licenses, adaptations, and exclusions.
