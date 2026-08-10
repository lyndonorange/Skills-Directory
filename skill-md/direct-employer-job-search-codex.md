---
name: direct-employer-job-search
display_name: direct-employer-job-search
platform: Codex
category: General and specialized workflows
---

# direct-employer-job-search - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `direct-employer-job-search` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Find and verify current jobs on public Greenhouse, Lever, Ashby, USAJOBS, and direct employer career sites while preserving direct URLs, dates, location eligibility, compensation, and deduplicated evidence. Use for evide

## How To Use It In Codex

In Codex, click the chat box, press /, choose direct-employer-job-search, then write the task. Fallback prompt: Use the direct-employer-job-search skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `direct-employer-job-search` |
| Canonical name | `direct-employer-job-search` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Find and verify current jobs on public Greenhouse, Lever, Ashby, USAJOBS, and direct employer career sites while preserving direct URLs, dates, location eligibility, compensation, and deduplicated evidence. Use for evide


## Original SKILL.md

---
name: direct-employer-job-search
description: Find and verify current jobs on public Greenhouse, Lever, Ashby, USAJOBS, and direct employer career sites while preserving direct URLs, dates, location eligibility, compensation, and deduplicated evidence. Use for evidence-based job discovery without bulk scraping or automatic applications.
---

# Direct Employer Job Search

Use direct employer postings as the source of truth. Search only at the user's request and never submit an application.

## Workflow

1. Confirm role terms and geography. Default to U.S.-eligible remote plus Omaha and Lincoln, Nebraska.
2. Search one or more public employer boards with `scripts/search_public_boards.py`; use web search for Workday, iCIMS, SmartRecruiters, or another employer career site when a public board identifier is unknown.
3. Open the direct employer URL and confirm the posting remains retrievable, location-eligible, and current. Record retrieval time and any posted/updated date.
4. Deduplicate by canonical URL, requisition ID, and normalized company/title/location. If a private tracker is in scope, compare without copying its personal data into this skill.
5. Return a compact evidence table: employer, title, location, compensation as posted, source, direct URL, retrieved date, and uncertainty.
6. Route promising postings to `$job-description-analyzer` and `$company-role-compensation-research`.

When a role came from `$us-job-board-search`, preserve both the discovery-board URL and the canonical employer URL, and treat the employer version as authoritative.

## Commands

```bash
python3 scripts/search_public_boards.py greenhouse BOARD_TOKEN --query "product manager" --location "remote" --limit 10
python3 scripts/search_public_boards.py lever SITE --query "engineer" --limit 10
python3 scripts/search_public_boards.py ashby BOARD --query "designer" --limit 10
python3 scripts/search_public_boards.py usajobs --query "program manager" --location "Nebraska" --limit 10
```

USAJOBS requires `USAJOBS_API_KEY` and `USAJOBS_USER_AGENT`. If absent, use the official USAJOBS website and explicitly label the credential fallback. Read `references/source-policy.md` before interpreting results.

## Guardrails

- Do not use bulk LinkedIn, Indeed, or Glassdoor scrapers.
- Do not bypass authentication, rate limits, robots controls, or terms.
- Do not call a posting current until its direct URL or public board response is verified.
- Do not invent pay, eligibility, freshness, match probability, or company facts.
- Require human approval before any application, outreach, negotiation, acceptance, or decline.
