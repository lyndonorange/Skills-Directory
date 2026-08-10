---
name: skillsmith
display_name: skillsmith
platform: Codex
category: General and specialized workflows
---

# skillsmith - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `skillsmith` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Universal adaptation of Christopher Kahler's Skillsmith meta-skill for discovering, specifying, scaffolding, distilling, and auditing agent skills with standardized entry points, tasks, frameworks, templates, context, ch

## How To Use It In Codex

In Codex, click the chat box, press /, choose skillsmith, then write the task. Fallback prompt: Use the skillsmith skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `skillsmith` |
| Canonical name | `skillsmith` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Universal adaptation of Christopher Kahler's Skillsmith meta-skill for discovering, specifying, scaffolding, distilling, and auditing agent skills with standardized entry points, tasks, frameworks, templates, context, ch


## Original SKILL.md

---
name: skillsmith
description: Universal adaptation of Christopher Kahler's Skillsmith meta-skill for discovering, specifying, scaffolding, distilling, and auditing agent skills with standardized entry points, tasks, frameworks, templates, context, checklists, and rules. Use when the user invokes Skillsmith; asks to design or scaffold a portable skill, turn source material into reusable frameworks, audit skill structure against the Skillsmith specs, or combine the upstream syntax model with the host's native skill-creator and validation tools.
---

# Skillsmith

Build understandable, portable skills from an explicit design contract.

## Universal Contract

- Use the host's native skill-creation workflow when available. On Codex, read and follow `skill-creator` before creating or modifying a skill.
- Use Skillsmith for discovery, architecture, source distillation, and conformance; do not bypass the host's required metadata or validator.
- Preserve source provenance and licensing. Distill concepts; do not copy copyrighted source wholesale unless authorized and licensed.
- Audit is read-only by default. Apply remediations only when the user requests edits.
- Keep the entry point concise and move detailed resources into on-demand directories.

## Route the Request

| Request | Workflow |
|---|---|
| New skill idea | Discover |
| Approved skill spec | Scaffold |
| Book, course, transcript, or notes | Distill |
| Existing skill quality | Audit |

## Discover

Capture:

1. name, purpose, trigger phrases, and clear non-triggers;
2. user, job to be done, outputs, and quality bar;
3. persona, tone, decision authority, permissions, and side effects;
4. commands or routes and their inputs/outputs;
5. resource architecture: tasks, frameworks, templates, context, checklists, rules, scripts, and assets;
6. portability, provenance, dependencies, tests, and failure handling.

Produce a reviewed skill spec before large scaffolds. Use the upstream `skill-spec.md` under `references/upstream-framework/skill/templates/` as one input, adjusted for the active host.

## Scaffold

1. Initialize with the host-native creator; on Codex use `init_skill.py` from `skill-creator`.
2. Keep `SKILL.md` focused on triggers, routing, core workflow, boundaries, and resource pointers.
3. Create only resources justified by the spec.
4. Generate meaningful content rather than empty placeholder documents.
5. Add `agents/openai.yaml` where the host expects it.
6. Validate with the host-native validator and forward-test realistic positive and negative invocations.

## Distill

1. Inspect the complete authorized source.
2. Create a concept-based chunking plan, not a chapter mirror.
3. For each chunk capture the core concept, when to use it, decision rules, examples, failure modes, and an optional template.
4. Separate quotation from synthesis and retain exact provenance.
5. Test whether each chunk stands alone and whether the entry point can route to it without loading everything.

## Audit

Inventory the skill and classify each file. Check:

- valid, precise frontmatter and realistic triggers;
- routing separated from detailed process content;
- required sections for each declared file type;
- explicit inputs, outputs, acceptance criteria, boundaries, and side effects;
- resource links that resolve and scripts that run;
- portability claims supported by live tests;
- stale placeholders, duplicate rules, broken references, and excessive context cost.

Report blockers and high-value remediation first. A compliance percentage never outweighs a broken trigger, unsafe instruction, missing dependency, or failed validator.

## References

- Read [file-types.md](references/file-types.md) for the universal interpretation of the seven upstream file types.
- The pinned upstream specs and workflow resources are under [upstream-framework](references/upstream-framework/).
- Read [upstream.md](references/upstream.md) for provenance and adaptation differences.
