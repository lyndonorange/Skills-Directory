---
name: skillsopt
display_name: skillsopt
platform: OpenCode
category: General and specialized workflows
---

# skillsopt - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `skillsopt` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use when Codex needs to optimize, train, evaluate, or evolve an agent skill document with Microsoft SkillOpt or SkillOpt-Sleep: configuring skill training loops, running rollout-reflect-aggregate-select-update-evaluate w

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the skillsopt skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `skillsopt` |
| Canonical name | `skillsopt` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Use when Codex needs to optimize, train, evaluate, or evolve an agent skill document with Microsoft SkillOpt or SkillOpt-Sleep: configuring skill training loops, running rollout-reflect-aggregate-select-update-evaluate w


## Original SKILL.md

---
name: skillsopt
description: "Use when Codex needs to optimize, train, evaluate, or evolve an agent skill document with Microsoft SkillOpt or SkillOpt-Sleep: configuring skill training loops, running rollout-reflect-aggregate-select-update-evaluate workflows, evaluating `best_skill.md`, launching the SkillOpt WebUI, running nightly offline self-evolution over Codex/Claude/Copilot sessions, staging/adopting SkillOpt-Sleep proposals, or adding SkillOpt backends and benchmarks."
---

# Skillsopt

## Overview

SkillOpt treats a skill document as trainable state for a frozen target agent. It improves the text through scored rollouts, bounded edits, validation gates, and epoch-style updates without changing model weights.

Read `references/upstream.md` when you need install commands, CLI details, config fields, SkillOpt-Sleep commands, or upstream links.

## Choose The Path

- Use classic SkillOpt training when the user has a benchmark, split, seed skill, scoring function, and wants to produce or compare an optimized `best_skill.md`.
- Use SkillOpt evaluation when the user already has a candidate skill and wants to score it on a train, validation, or test split.
- Use SkillOpt-Sleep when the user wants local offline self-evolution from prior Codex, Claude Code, or Copilot sessions, with proposals staged for review before adoption.
- Use backend or benchmark extension guidance when the user wants to integrate a new model target, execution harness, or task environment into SkillOpt.

## Training Workflow

1. Confirm the benchmark, target agent/backend, optimizer model, scoring signal, seed skill, and train/validation/test split boundaries.
2. Install only the needed extras for the benchmark/backend.
3. Start with an existing config, then make explicit overrides for epochs, batch size, learning rate, validation gating, worker count, and initial skill path.
4. Run a smoke test before full training when the benchmark is expensive.
5. Train with `skillopt-train` or `python scripts/train.py`.
6. Inspect `outputs/<benchmark>/<run_id>/best_skill.md`, `history.json`, step records, and validation-gate decisions.
7. Evaluate `best_skill.md` on a held-out split with `skillopt-eval` or `python scripts/eval_only.py`.

## SkillOpt-Sleep Workflow

1. Run `skillopt-sleep dry-run` first to harvest and mine without changing anything.
2. Run `skillopt-sleep run` for a full offline cycle only when the user accepts the local API/runtime cost.
3. Use `skillopt-sleep status` to inspect staged proposals.
4. Adopt with `skillopt-sleep adopt` only after reviewing the staged diff and validation result.
5. Schedule nightly runs with `skillopt-sleep schedule` only when the user explicitly wants recurring automation.

## Guardrails

- Keep validation gates on by default for training and sleep cycles.
- Do not overwrite a hand-authored skill directly; stage the optimized skill, compare diffs, and preserve the original.
- Treat sub-1.5 point gains as likely noise unless repeated runs or benchmark variance says otherwise.
- Do not claim a skill improved until a held-out evaluation confirms it.
- Keep API credentials in `.env` or existing secret stores; never write real keys into configs, docs, or skill files.
- For personal-session harvesting, tell the user what transcript sources will be read before running non-dry-run sleep cycles.

## Outputs To Expect

- Training runs under `outputs/<benchmark>/<run_id>/`.
- Step-level candidate skills and records under `steps/`.
- Best deployable artifact as `best_skill.md`.
- Training/evaluation history as `history.json`.
- SkillOpt-Sleep staged proposals and state from the local sleep engine.
