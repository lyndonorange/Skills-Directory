---
name: job-application-assistant
display_name: job-application-assistant
platform: Universal Agents
category: General and specialized workflows
---

# job-application-assistant - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `job-application-assistant` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Route an evidence-based job search from live discovery through fit analysis, truthful application materials, tracked interview rounds, offer comparison, negotiation preparation, and acceptance or decline. Use for end-to-

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the job-application-assistant skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `job-application-assistant` |
| Canonical name | `job-application-assistant` |
| Platform | `Universal Agents` |
| Category | General and specialized workflows |

## Description

Route an evidence-based job search from live discovery through fit analysis, truthful application materials, tracked interview rounds, offer comparison, negotiation preparation, and acceptance or decline. Use for end-to-


## Original SKILL.md

---
name: job-application-assistant
description: Route an evidence-based job search from live discovery through fit analysis, truthful application materials, tracked interview rounds, offer comparison, negotiation preparation, and acceptance or decline. Use for end-to-end career workflows or to select the narrow specialist needed for one stage.
---

# Job Application Assistant

This is the lifecycle router. Invoke only the specialists needed for the user's current stage.
Read `references/source-and-runtime-notes.md` for provenance and runtime boundaries.

## Non-negotiable rules

- Direct employer postings outrank aggregators. Verify a posting before recommending it.
- Never fabricate candidate facts, metrics, fit probabilities, salary data, culture claims, or search results.
- Treat scores as transparent user-controlled comparisons, never employer outcome probabilities.
- Draft applications, outreach, counters, acceptances, and declines only. Human approval is mandatory before external action.
- Keep candidate evidence in the user's private workspace, never in a shared skill or distributable package.
- If a local CLI is unavailable, use current web research or user-uploaded postings. State what was and was not run.

## Lifecycle routing

1. **Set evidence:** use `$ocf-start` or the user's supplied résumé/profile.
2. **Discover:** use `$us-job-board-search` for broad U.S. public, private-sector, remote, startup, niche, or member-board coverage; pair it with `$linkedin-search`, `$freehire-search`, `$direct-employer-job-search`, or `$network-job-search` only when those narrower sources fit.
3. **Verify and compare:** use `$job-description-analyzer` and `$company-role-compensation-research`.
4. **Prepare materials:** route to the relevant résumé specialist, `$cover-letter-generator`, `$application-form-filler`, or `$cold-email-writer`.
5. **Prepare private LinkedIn outreach:** use `$linkedin-job-outreach` for job-specific recruiter, hiring-manager, employee, leader, culture, legitimacy, and referral messages. Verify the role first and keep every message draft-only.
6. **Prepare interviews:** use `$interview-prep-generator` for fast story extraction and `$interview-prep-coach` for researched coaching and live mocks.
7. **Finish hiring:** use `$offer-comparison-analyzer` and `$salary-negotiation-prep`; prepare written acceptance and decline drafts only.
8. **Record outcome:** update the private application record after user confirmation.

## Application record

Maintain one record per application, in the user's private job-search workspace, with:

- canonical employer posting URL, requisition ID, retrieved date, and saved posting;
- company/role/compensation research and source dates;
- evidence-backed fit coverage, gaps, and decision;
- each submitted artifact preserved as submitted;
- interview rounds, interviewers, prep, debrief, and follow-ups;
- offer terms, negotiation drafts, final written terms, and outcome.

Deduplicate on canonical URL and requisition ID, then normalized company/title/location. Never overwrite a submitted artifact with a later draft.

## Default market

Unless the user changes it: U.S.-eligible remote work plus Omaha and Lincoln, Nebraska local or hybrid roles. Reject location-restricted postings that exclude Nebraska.
