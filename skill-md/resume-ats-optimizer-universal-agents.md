---
name: resume-ats-optimizer
display_name: resume-ats-optimizer
platform: Universal Agents
category: General and specialized workflows
---

# resume-ats-optimizer - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `resume-ats-optimizer` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Test résumé text extraction and parsability, compare truthful terminology with a retrieved job posting, and recommend readable ATS-compatible improvements without promising pass rates or inventing experience.

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the resume-ats-optimizer skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `resume-ats-optimizer` |
| Canonical name | `resume-ats-optimizer` |
| Platform | `Universal Agents` |
| Category | General and specialized workflows |

## Description

Test résumé text extraction and parsability, compare truthful terminology with a retrieved job posting, and recommend readable ATS-compatible improvements without promising pass rates or inventing experience.


## Original SKILL.md

---
name: resume-ats-optimizer
description: Test résumé text extraction and parsability, compare truthful terminology with a retrieved job posting, and recommend readable ATS-compatible improvements without promising pass rates or inventing experience.
---

# Resume ATS Optimizer

ATS implementations differ and employer settings are private. Never promise an ATS pass, claim a universal rejection statistic, or present keyword coverage as an employer probability.

## Workflow

1. Confirm the direct job posting is current and preserve its text and URL.
2. Extract résumé text. Report failures, reading-order problems, image-only content, and ambiguous section structure.
3. Separate required, preferred, responsibility, and context terms from the posting.
4. Build an evidence-coverage table: term, posting context, résumé evidence, exact/synonym/absent status, and safe action.
5. Add exact terminology only when the candidate's evidence truthfully supports it. Never keyword-stuff or create experience.
6. Recommend simple headings, consistent dates, readable text, and a sensible single-column fallback when extraction is unreliable.
7. Re-run text extraction after changes and compare output, not an invented success score.

## Output

Report parsability checks, evidence coverage, genuine gaps, safe wording changes, and limitations. If a numeric coverage ratio is useful, label it as a transparent document comparison only and show its numerator and denominator.


## Universal Evidence Contract

Read references/universal-runtime-and-evidence.md before producing or acting on career materials. Its truth, privacy, runtime-disclosure, and human-approval rules override any conflicting examples in this skill.
