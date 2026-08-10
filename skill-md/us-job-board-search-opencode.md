---
name: us-job-board-search
display_name: us-job-board-search
platform: OpenCode
category: General and specialized workflows
---

# us-job-board-search - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `us-job-board-search` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Search current U.S.-eligible jobs across public employment systems, national private-sector boards, remote and niche boards, startup communities, professional associations, and authorized member-only boards. Use when a j

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the us-job-board-search skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `us-job-board-search` |
| Canonical name | `us-job-board-search` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Search current U.S.-eligible jobs across public employment systems, national private-sector boards, remote and niche boards, startup communities, professional associations, and authorized member-only boards. Use when a j


## Original SKILL.md

---
name: us-job-board-search
description: Search current U.S.-eligible jobs across public employment systems, national private-sector boards, remote and niche boards, startup communities, professional associations, and authorized member-only boards. Use when a job search must go beyond LinkedIn or Indeed while preserving direct employer URLs, freshness, location eligibility, source provenance, and deduplication.
---

# U.S. Job Board Search

Search broadly for discovery, then verify narrowly. Never apply, message, or create an account for the user.

## Workflow

1. Confirm target titles, seniority, industries, exclusions, compensation floor, and geography. Default to U.S.-eligible remote plus Omaha and Lincoln, Nebraska.
2. Choose two to five source lanes from `references/source-catalog.md`. Do not search every board by default.
3. Search current public pages with the web. Use an authenticated or paid board only when the user already has lawful access and explicitly asks to use it.
4. Capture source board, title, employer, location, posted date, compensation as shown, source URL, and direct employer URL when available.
5. Open the employer careers page or ATS posting. Confirm the role is current, accepts the user's location, and matches the source listing. Treat the employer page as authoritative.
6. Deduplicate by canonical employer URL, requisition ID, and normalized company/title/location.
7. Return a source-by-source search log plus a compact shortlist. Label blocked pages, login requirements, stale results, missing pay, and unresolved location rules.
8. Route verified roles to `$job-description-analyzer`; use `$company-role-compensation-research` only for promising roles.

## Search order

Use this default order unless the user's role suggests a different lane:

1. Direct employer and ATS pages through `$direct-employer-job-search`.
2. U.S. public workforce sources: CareerOneStop, USAJOBS, state workforce boards, and state or local government career sites.
3. Relevant private-sector or niche boards: Built In and Dice for tech; Wellfound and Y Combinator for startups; Idealist for nonprofit work; reputable remote boards for U.S.-eligible remote roles.
4. Professional association, alumni, chamber, veteran, disability, or member boards only when relevant and accessible to the user.
5. Broad aggregators for discovery only. Resolve every candidate to the employer's own posting before recommending it.

## Output contract

Include:

- the sources searched and why each source fit the target;
- exact query, geography, filters, and retrieval date;
- verified shortlist with employer URLs and provenance;
- rejected or unresolved results with reasons;
- duplicates removed;
- a coverage note identifying source lanes not searched.

## Guardrails

- Do not bypass logins, subscriptions, CAPTCHAs, robots controls, or rate limits.
- Do not ask for, retain, or expose board credentials. Let the user sign in directly when needed.
- Do not scrape LinkedIn, Indeed, Glassdoor, or other boards in bulk.
- Do not treat board freshness, remote eligibility, compensation, or employer identity as verified until the direct posting confirms it.
- Do not reuse a board's one-click application or automated outreach features.
- Require human approval before every application or external message.
