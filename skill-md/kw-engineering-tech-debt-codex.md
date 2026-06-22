---
name: kw-engineering-tech-debt
display_name: kw-engineering-tech-debt
platform: Codex
category: General and specialized workflows
---

# kw-engineering-tech-debt - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-engineering-tech-debt` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Systematically identify, categorize, and prioritize technical debt.

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-engineering-tech-debt, then write the task. Fallback prompt: Use the kw-engineering-tech-debt skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-engineering-tech-debt` |
| Canonical name | `kw-engineering-tech-debt` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Systematically identify, categorize, and prioritize technical debt.

## Original SKILL.md

---
knowledge-work-plugin: engineering
upstream-skill: tech-debt
name: kw-engineering-tech-debt
description: Identify, categorize, and prioritize technical debt. Trigger with "tech debt", "technical debt audit", "what should we refactor", "code health", or when the user asks about code quality, refactoring priorities, or maintenance backlog.
---

# Tech Debt Management

Systematically identify, categorize, and prioritize technical debt.

## Categories

| Type | Examples | Risk |
|------|----------|------|
| **Code debt** | Duplicated logic, poor abstractions, magic numbers | Bugs, slow development |
| **Architecture debt** | Monolith that should be split, wrong data store | Scaling limits |
| **Test debt** | Low coverage, flaky tests, missing integration tests | Regressions ship |
| **Dependency debt** | Outdated libraries, unmaintained dependencies | Security vulns |
| **Documentation debt** | Missing runbooks, outdated READMEs, tribal knowledge | Onboarding pain |
| **Infrastructure debt** | Manual deploys, no monitoring, no IaC | Incidents, slow recovery |

## Prioritization Framework

Score each item on:
- **Impact**: How much does it slow the team down? (1-5)
- **Risk**: What happens if we don't fix it? (1-5)
- **Effort**: How hard is the fix? (1-5, inverted — lower effort = higher priority)

Priority = (Impact + Risk) x (6 - Effort)

## Output

Produce a prioritized list with estimated effort, business justification for each item, and a phased remediation plan that can be done alongside feature work.

