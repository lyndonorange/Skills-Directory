---
name: kw-operations-process-optimization
display_name: kw-operations-process-optimization
platform: Codex
category: General and specialized workflows
---

# kw-operations-process-optimization - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-operations-process-optimization` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Analyze existing processes and recommend improvements.

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-operations-process-optimization, then write the task. Fallback prompt: Use the kw-operations-process-optimization skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-operations-process-optimization` |
| Canonical name | `kw-operations-process-optimization` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Analyze existing processes and recommend improvements.

## Original SKILL.md

---
knowledge-work-plugin: operations
upstream-skill: process-optimization
name: kw-operations-process-optimization
description: Analyze and improve business processes. Trigger with "this process is slow", "how can we improve", "streamline this workflow", "too many steps", "bottleneck", or when the user describes an inefficient process they want to fix.
---

# Process Optimization

Analyze existing processes and recommend improvements.

## Analysis Framework

### 1. Map Current State
- Document every step, decision point, and handoff
- Identify who does what and how long each step takes
- Note manual steps, approvals, and waiting times

### 2. Identify Waste
- **Waiting**: Time spent in queues or waiting for approvals
- **Rework**: Steps that fail and need to be redone
- **Handoffs**: Each handoff is a potential point of failure or delay
- **Over-processing**: Steps that add no value
- **Manual work**: Tasks that could be automated

### 3. Design Future State
- Eliminate unnecessary steps
- Automate where possible
- Reduce handoffs
- Parallelize independent steps
- Add checkpoints (not gates)

### 4. Measure Impact
- Time saved per cycle
- Error rate reduction
- Cost savings
- Employee satisfaction improvement

## Output

Produce a before/after process comparison with specific improvement recommendations, estimated impact, and an implementation plan.

