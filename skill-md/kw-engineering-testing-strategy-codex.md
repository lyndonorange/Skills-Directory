---
name: kw-engineering-testing-strategy
display_name: kw-engineering-testing-strategy
platform: Codex
category: General and specialized workflows
---

# kw-engineering-testing-strategy - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-engineering-testing-strategy` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Design effective testing strategies balancing coverage, speed, and maintenance.

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-engineering-testing-strategy, then write the task. Fallback prompt: Use the kw-engineering-testing-strategy skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-engineering-testing-strategy` |
| Canonical name | `kw-engineering-testing-strategy` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Design effective testing strategies balancing coverage, speed, and maintenance.

## Original SKILL.md

---
knowledge-work-plugin: engineering
upstream-skill: testing-strategy
name: kw-engineering-testing-strategy
description: Design test strategies and test plans. Trigger with "how should we test", "test strategy for", "write tests for", "test plan", "what tests do we need", or when the user needs help with testing approaches, coverage, or test architecture.
---

# Testing Strategy

Design effective testing strategies balancing coverage, speed, and maintenance.

## Testing Pyramid

```
        /  E2E  \         Few, slow, high confidence
       / Integration \     Some, medium speed
      /    Unit Tests  \   Many, fast, focused
```

## Strategy by Component Type

- **API endpoints**: Unit tests for business logic, integration tests for HTTP layer, contract tests for consumers
- **Data pipelines**: Input validation, transformation correctness, idempotency tests
- **Frontend**: Component tests, interaction tests, visual regression, accessibility
- **Infrastructure**: Smoke tests, chaos engineering, load tests

## What to Cover

Focus on: business-critical paths, error handling, edge cases, security boundaries, data integrity.

Skip: trivial getters/setters, framework code, one-off scripts.

## Output

Produce a test plan with: what to test, test type for each area, coverage targets, and example test cases. Identify gaps in existing coverage.

