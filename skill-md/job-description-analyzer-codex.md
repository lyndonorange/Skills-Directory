---
name: job-description-analyzer
display_name: job-description-analyzer
platform: Codex
category: General and specialized workflows
---

# job-description-analyzer - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `job-description-analyzer` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Analyze a current job posting against verified candidate evidence, distinguish requirements from preferences, surface red flags and gaps, and recommend an application strategy without pretending a heuristic score predict

## How To Use It In Codex

In Codex, click the chat box, press /, choose job-description-analyzer, then write the task. Fallback prompt: Use the job-description-analyzer skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `job-description-analyzer` |
| Canonical name | `job-description-analyzer` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Analyze a current job posting against verified candidate evidence, distinguish requirements from preferences, surface red flags and gaps, and recommend an application strategy without pretending a heuristic score predict


## Original SKILL.md

---
name: job-description-analyzer
description: Analyze a current job posting against verified candidate evidence, distinguish requirements from preferences, surface red flags and gaps, and recommend an application strategy without pretending a heuristic score predicts employer decisions.
---

# Job Description Analyzer

## Workflow

1. Fetch or read the complete posting and preserve the direct employer URL, requisition ID, location, compensation, and retrieval date.
2. Separate must-haves, preferences, responsibilities, outcomes, logistics, and company-language signals. Note ambiguity and copied boilerplate.
3. Map every important requirement to candidate evidence as **strong**, **partial/transferable**, **missing**, or **unknown**. Quote or point to the evidence source.
4. Check eligibility, seniority, location, travel, schedule, compensation, and legal/certification constraints before recommending effort.
5. Flag posting risks: contradictory scope, implausible breadth, unclear reporting line, missing pay where legally expected, stale dates, or suspicious application domains.
6. Recommend apply, investigate first, or pass, with reasons and questions to resolve.

## Scoring rule

Do not call any score a match probability or ATS outcome. Prefer a coverage table. If the user asks for a score, use their chosen weights, show the calculation, preserve unknowns, and label it a personal prioritization aid.

## Output

Return posting facts, evidence coverage, differentiators, gaps and bridge strategies, red flags, questions, and an evidence-backed recommendation. Route company, culture, pay, and risk claims to `$company-role-compensation-research`.


## Universal Evidence Contract

Read references/universal-runtime-and-evidence.md before producing or acting on career materials. Its truth, privacy, runtime-disclosure, and human-approval rules override any conflicting examples in this skill.
