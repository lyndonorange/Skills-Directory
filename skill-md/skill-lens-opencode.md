---
name: skill-lens
display_name: skill-lens
platform: OpenCode
category: General and specialized workflows
---

# skill-lens - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `skill-lens` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use when Codex needs to study, extract, or evaluate model-generated agent skills with Microsoft SkillLens: loading raw agent trajectories, normalizing benchmark outputs, extracting reusable skills with sequential or para

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the skill-lens skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `skill-lens` |
| Canonical name | `skill-lens` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Use when Codex needs to study, extract, or evaluate model-generated agent skills with Microsoft SkillLens: loading raw agent trajectories, normalizing benchmark outputs, extracting reusable skills with sequential or para


## Original SKILL.md

---
name: skill-lens
description: "Use when Codex needs to study, extract, or evaluate model-generated agent skills with Microsoft SkillLens: loading raw agent trajectories, normalizing benchmark outputs, extracting reusable skills with sequential or parallel extraction, injecting a skill set into benchmark inference, comparing baseline vs skill consumption, or reproducing SkillLens experiments across ALFWorld, BFCL v4, SEAL-0, SpreadsheetBench, or SWE-bench Verified."
---

# Skill Lens

## Overview

SkillLens is a research and evaluation framework for the full lifecycle of model-generated agent skills: experience generation, schema normalization, skill extraction, and skill consumption. Use it to answer whether a generated skill is actually useful to a target model and why.

Read `references/upstream.md` when you need install commands, CLI flags, provider configuration, benchmark names, or the upstream repository links.

## Workflow

1. Confirm the benchmark and target model.
2. Generate or locate raw trajectories with `skilllens infer`.
3. Normalize raw benchmark output into the unified `Trajectory` schema with `skilllens convert`.
4. Extract a `skill_set.json` with `skilllens extract`, preferring the `parallel` method for paper-style extraction unless the user asks for a simpler baseline.
5. Re-run inference with `skilllens infer --skill-set <path>` and compare against the no-skill baseline.
6. Report both extraction quality and target-model skill consumption results; keep benchmark setup caveats explicit.

## Operating Guidance

- Treat SkillLens as an experiment harness, not as a generic skill authoring shortcut.
- Keep baseline and skill-injected runs comparable: same benchmark split, model, provider, worker count, sample count, and reasoning settings unless the user asks to vary them.
- Use small `--num-samples` smoke tests before full benchmark runs.
- Preserve raw trajectories, converted experience pools, extraction configs, `skill_set.json`, and inference outputs so results are reproducible.
- Prefer committed config files under `configs/examples/` as starting points, then override with `--set key=value` for local experiments.
- Do not claim a skill improves performance until a fresh skill-consumption run has been compared to a baseline.

## Outputs To Expect

- Raw inference runs under `inference_output/<benchmark>/...`.
- Experience pools under `data/experience_pool/<benchmark>/...` or a custom `-o` path.
- Extracted skills under the selected extraction output directory, including `skill_set.json`.
- Benchmark-specific results in the inference output directory.
