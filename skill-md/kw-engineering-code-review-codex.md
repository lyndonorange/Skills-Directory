---
name: kw-engineering-code-review
display_name: kw-engineering-code-review
platform: Codex
category: General and specialized workflows
---

# kw-engineering-code-review - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-engineering-code-review` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-engineering-code-review, then write the task. Fallback prompt: Use the kw-engineering-code-review skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-engineering-code-review` |
| Canonical name | `kw-engineering-code-review` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

## Original SKILL.md

---
knowledge-work-plugin: engineering
upstream-skill: code-review
name: kw-engineering-code-review
description: Review code changes for security, performance, and correctness. Trigger with a PR URL or diff, "review this before I merge", "is this code safe?", or when checking a change for N+1 queries, injection risks, missing edge cases, or error handling gaps.
argument-hint: "<PR URL, diff, or file path>"
---

# /code-review

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

Review code changes with a structured lens on security, performance, correctness, and maintainability.

## Usage

```
/code-review <PR URL or file path>
```

Review the provided code changes: @$1

If no specific file or URL is provided, ask what to review.

## How It Works

```
┌─────────────────────────────────────────────────────────────────┐
│                      CODE REVIEW                                   │
├─────────────────────────────────────────────────────────────────┤
│  STANDALONE (always works)                                       │
│  ✓ Paste a diff, PR URL, or point to files                      │
│  ✓ Security audit (OWASP top 10, injection, auth)               │
│  ✓ Performance review (N+1, memory leaks, complexity)           │
│  ✓ Correctness (edge cases, error handling, race conditions)    │
│  ✓ Style (naming, structure, readability)                        │
│  ✓ Actionable suggestions with code examples                    │
├─────────────────────────────────────────────────────────────────┤
│  SUPERCHARGED (when you connect your tools)                      │
│  + Source control: Pull PR diff automatically                    │
│  + Project tracker: Link findings to tickets                     │
│  + Knowledge base: Check against team coding standards           │
└─────────────────────────────────────────────────────────────────┘
```

## Review Dimensions

### Security
- SQL injection, XSS, CSRF
- Authentication and authorization flaws
- Secrets or credentials in code
- Insecure deserialization
- Path traversal
- SSRF

### Performance
- N+1 queries
- Unnecessary memory allocations
- Algorithmic complexity (O(n²) in hot paths)
- Missing database indexes
- Unbounded queries or loops
- Resource leaks

### Correctness
- Edge cases (empty input, null, overflow)
- Race conditions and concurrency issues
- Error handling and propagation
- Off-by-one errors
- Type safety

### Maintainability
- Naming clarity
- Single responsibility
- Duplication
- Test coverage
- Documentation for non-obvious logic

## Output

```markdown
## Code Review: [PR title or file]

### Summary
[1-2 sentence overview of the changes and overall quality]

### Critical Issues
| # | File | Line | Issue | Severity |
|---|------|------|-------|----------|
| 1 | [file] | [line] | [description] | 🔴 Critical |

### Suggestions
| # | File | Line | Suggestion | Category |
|---|------|------|------------|----------|
| 1 | [file] | [line] | [description] | Performance |

### What Looks Good
- [Positive observations]

### Verdict
[Approve / Request Changes / Needs Discussion]
```

## If Connectors Available

If **~~source control** is connected:
- Pull the PR diff automatically from the URL
- Check CI status and test results

If **~~project tracker** is connected:
- Link findings to related tickets
- Verify the PR addresses the stated requirements

If **~~knowledge base** is connected:
- Check changes against team coding standards and style guides

## Tips

1. **Provide context** — "This is a hot path" or "This handles PII" helps me focus.
2. **Specify concerns** — "Focus on security" narrows the review.
3. **Include tests** — I'll check test coverage and quality too.

