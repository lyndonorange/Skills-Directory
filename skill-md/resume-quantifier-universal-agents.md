---
name: resume-quantifier
display_name: resume-quantifier
platform: Universal Agents
category: General and specialized workflows
---

# resume-quantifier - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `resume-quantifier` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Find defensible opportunities to quantify résumé achievements by asking evidence questions, deriving only from known inputs, and preserving qualitative impact when no truthful metric is available.

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the resume-quantifier skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `resume-quantifier` |
| Canonical name | `resume-quantifier` |
| Platform | `Universal Agents` |
| Category | General and specialized workflows |

## Description

Find defensible opportunities to quantify résumé achievements by asking evidence questions, deriving only from known inputs, and preserving qualitative impact when no truthful metric is available.


## Original SKILL.md

---
name: resume-quantifier
description: Find defensible opportunities to quantify résumé achievements by asking evidence questions, deriving only from known inputs, and preserving qualitative impact when no truthful metric is available.
---

# Resume Quantifier

## Truth rule

Never estimate, infer, round, or manufacture an unknown résumé number. A plausible number is still false if the candidate cannot support it. Mark missing metrics as questions and keep a strong qualitative version until evidence is supplied.

## Workflow

1. Identify bullets whose scale, frequency, speed, quality, money, reach, or outcome could be clarified.
2. Ask targeted questions about records the candidate may know or retrieve: counts, ranges, dates, team size, portfolio size, baseline and result, cadence, SLA, budget, or attributable outcome.
3. Classify each candidate metric:
   - **Verified:** supported by a document or exact recollection.
   - **Candidate-confirmed:** supplied and defensible but not independently documented.
   - **Derived:** arithmetic from known inputs; show the calculation and ask for confirmation.
   - **Unknown:** do not place it in the résumé.
4. Write one truthful quantified version when evidence exists and one qualitative version when it does not.
5. Flag confidentiality, attribution, rounding, and interview-defensibility risks.

## Output

For each bullet provide: original, evidence questions, evidence status, revised bullet, calculation if derived, and any remaining verification needed. Do not require every bullet to contain a number; specificity and truth outrank artificial quantification.


## Universal Evidence Contract

Read references/universal-runtime-and-evidence.md before producing or acting on career materials. Its truth, privacy, runtime-disclosure, and human-approval rules override any conflicting examples in this skill.
