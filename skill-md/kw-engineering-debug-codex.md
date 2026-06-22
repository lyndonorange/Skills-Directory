---
name: kw-engineering-debug
display_name: kw-engineering-debug
platform: Codex
category: General and specialized workflows
---

# kw-engineering-debug - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-engineering-debug` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-engineering-debug, then write the task. Fallback prompt: Use the kw-engineering-debug skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-engineering-debug` |
| Canonical name | `kw-engineering-debug` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

## Original SKILL.md

---
knowledge-work-plugin: engineering
upstream-skill: debug
name: kw-engineering-debug
description: Structured debugging session — reproduce, isolate, diagnose, and fix. Trigger with an error message or stack trace, "this works in staging but not prod", "something broke after the deploy", or when behavior diverges from expected and the cause isn't obvious.
argument-hint: "<error message or problem description>"
---

# /debug

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

Run a structured debugging session to find and fix issues systematically.

## Usage

```
/debug $ARGUMENTS
```

## How It Works

```
┌─────────────────────────────────────────────────────────────────┐
│                       DEBUG                                        │
├─────────────────────────────────────────────────────────────────┤
│  Step 1: REPRODUCE                                                │
│  ✓ Understand the expected vs. actual behavior                   │
│  ✓ Identify exact reproduction steps                             │
│  ✓ Determine scope (when did it start? who is affected?)        │
│                                                                    │
│  Step 2: ISOLATE                                                   │
│  ✓ Narrow down the component, service, or code path             │
│  ✓ Check recent changes (deploys, config changes, dependencies) │
│  ✓ Review logs and error messages                                │
│                                                                    │
│  Step 3: DIAGNOSE                                                  │
│  ✓ Form hypotheses and test them                                 │
│  ✓ Trace the code path                                           │
│  ✓ Identify root cause (not just symptoms)                      │
│                                                                    │
│  Step 4: FIX                                                       │
│  ✓ Propose a fix with explanation                                │
│  ✓ Consider side effects and edge cases                          │
│  ✓ Suggest tests to prevent regression                           │
└─────────────────────────────────────────────────────────────────┘
```

## What I Need From You

Tell me about the problem. Any of these help:
- Error message or stack trace
- Steps to reproduce
- What changed recently
- Logs or screenshots
- Expected vs. actual behavior

## Output

```markdown
## Debug Report: [Issue Summary]

### Reproduction
- **Expected**: [What should happen]
- **Actual**: [What happens instead]
- **Steps**: [How to reproduce]

### Root Cause
[Explanation of why the bug occurs]

### Fix
[Code changes or configuration fixes needed]

### Prevention
- [Test to add]
- [Guard to put in place]
```

## If Connectors Available

If **~~monitoring** is connected:
- Pull logs, error rates, and metrics around the time of the issue
- Show recent deploys and config changes that may correlate

If **~~source control** is connected:
- Identify recent commits and PRs that touched affected code paths
- Check if the issue correlates with a specific change

If **~~project tracker** is connected:
- Search for related bug reports or known issues
- Create a ticket for the fix once identified

## Tips

1. **Share error messages exactly** — Don't paraphrase. The exact text matters.
2. **Mention what changed** — Recent deploys, dependency updates, and config changes are top suspects.
3. **Include context** — "This works in staging but not prod" or "Only affects large payloads" narrows things fast.

