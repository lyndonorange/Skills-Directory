---
name: herdr-libghostty-commit-messages
display_name: herdr-libghostty-commit-messages
platform: OpenCode
category: General and specialized workflows
---

# herdr-libghostty-commit-messages - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `herdr-libghostty-commit-messages` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

>-

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the herdr-libghostty-commit-messages skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `herdr-libghostty-commit-messages` |
| Canonical name | `herdr-libghostty-commit-messages` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

>-


## Original SKILL.md

---
name: herdr-libghostty-commit-messages
description: >-
  Writes Git commit messages for Herdr's vendored libghostty-vt subtree.
  Activates only when the user asks to write or apply a commit message for
  changes under Herdr's vendor/libghostty-vt directory.
---

# Writing Commit Messages

Use this skill only for changes under `vendor/libghostty-vt/` inside the Herdr repository.

Write commit messages that follow commit style guidelines for the project.

## Format

```
<subsystem>: <summary>

<reference issues/PRs/etc.>

<long form description>
```

## Rules

### Subject line

- **Subsystem prefix**: Use a short, lowercase identifier for the
  area of code changed (e.g., `terminal`, `vt`, `lib`, `config`,
  `font`). Determine this from the file paths in the diff. If
  changes span the macOS app, use `macos`. For GTK, use `gtk`. For
  build system, use `build`. Use nested subsystems with `/` when
  helpful and exclusive (e.g., `terminal/osc`).
- **Summary**: Lowercase start (not capitalized), imperative mood,
  no trailing period. Keep it concise—ideally under 60 characters
  total for the whole subject line.

### References

- If the change relates to a GitHub issue, PR, or discussion, list
  the relevant numbers on their own lines after the subject, separated
  by a blank line. E.g. `#1234`
- If there are no references, omit this section entirely (no blank
  line).

### Long form description

- Describe **what changed**, **what the previous behavior was**,
  and **how the new behavior works** at a high level.
- Use plain prose, not bullet points. Wrap lines at ~72 characters.
- Focus on the _why_ and _how_ rather than restating the diff.
- Keep the tone direct and technical without no filler phrases.
- Don't exceed a handful of paragraphs; less is more.

## Workflow

- If `.jj` is present, use `jj` instead of `git` for all commands.
- Run a diff to see what changes are present since the last commit.
- Identify the subsystem from the changed file paths.
- Identify any referenced issues/PRs from the diff context or
  branch name.
- Draft the commit message following the format above.
- Apply the commit
- Don't push the commit; leave that to the user.
