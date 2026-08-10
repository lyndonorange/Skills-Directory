---
name: network-job-search
display_name: network-job-search
platform: OpenCode
category: General and specialized workflows
---

# network-job-search - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `network-job-search` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use a user-supplied LinkedIn connections CSV or contact export to identify companies with warm connections, find current direct-employer openings, and draft opt-in introduction requests without logging into LinkedIn, scr

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the network-job-search skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `network-job-search` |
| Canonical name | `network-job-search` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Use a user-supplied LinkedIn connections CSV or contact export to identify companies with warm connections, find current direct-employer openings, and draft opt-in introduction requests without logging into LinkedIn, scr


## Original SKILL.md

---
name: network-job-search
description: Use a user-supplied LinkedIn connections CSV or contact export to identify companies with warm connections, find current direct-employer openings, and draft opt-in introduction requests without logging into LinkedIn, scraping private data, or sending messages.
---

# Network Job Search

## Workflow

1. Obtain explicit permission and a local user-supplied CSV. Never log into LinkedIn or scrape private profiles.
2. Run `python3 scripts/summarize_connections.py INPUT.csv` to identify company clusters. The script emits company counts only by default.
3. Ask which contacts may be used; do not expose or transmit the full export.
4. Route selected companies to `$direct-employer-job-search` and verify current direct postings.
5. Map a real contact to a suitable role only when the supplied data supports the relationship.
6. Route the selected contact and verified role to `$linkedin-job-outreach` for a concise, truthful, opt-in introduction or referral-process draft. Never send it.

Keep contact data in the user's private job-search workspace. Do not copy it into skill folders, ZIPs, logs, or shared repositories.
