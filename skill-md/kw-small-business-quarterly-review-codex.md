---
name: kw-small-business-quarterly-review
display_name: kw-small-business-quarterly-review
platform: Codex
category: General and specialized workflows
---

# kw-small-business-quarterly-review - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-small-business-quarterly-review` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

knowledge-work-plugin: small-business

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-small-business-quarterly-review, then write the task. Fallback prompt: Use the kw-small-business-quarterly-review skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-small-business-quarterly-review` |
| Canonical name | `kw-small-business-quarterly-review` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

knowledge-work-plugin: small-business

## Original SKILL.md

---
knowledge-work-plugin: small-business
upstream-skill: quarterly-review
name: kw-small-business-quarterly-review
description: Generates a full QBR narrative — revenue trend, margin trend, customer health, top opportunities and risks — as a presentation-ready PDF or deck. Accepts optional quarter and save-to arguments.
allowed-tools: Read, WebFetch, Bash
---

Run the quarterly business review. Pull financial, sales, and customer data for the quarter, synthesize it into a narrative, and produce a presentation-ready document.

Parse arguments:
- `--quarter` (default: previous calendar quarter) — format `YYYY-QN` (e.g., `2026-Q1`)
- `--save-to` (default: `files`) — `files` (Google Drive / OneDrive), `desktop`, or `both`

## Step 1 — Financial performance

Using the `business-pulse` skill in deep mode:

1. Pull QuickBooks P&L for the quarter: revenue, COGS, gross margin, operating expenses, net margin.
2. Compare to prior quarter and same quarter last year (if available).
3. Pull PayPal settlements for the same period to validate QB revenue.
4. Calculate: revenue growth %, margin change in points, top 3 revenue categories.

## Step 2 — Customer health

1. Pull HubSpot deal data: new customers won, churned, average deal size, pipeline entering next quarter.
2. Calculate customer acquisition cost (if data available) and revenue per customer.
3. Flag any customers representing >20% of revenue (concentration risk).

## Step 3 — Top opportunities

Identify 3 specific opportunities for next quarter based on the data:
- Revenue upside (category, customer segment, or channel to double down on)
- Margin upside (cost to cut or price to raise)
- Customer upside (segment to target or churn to reduce)

## Step 4 — Top risks

Identify 3 specific risks for next quarter:
- Revenue risk (concentration, trend, seasonality)
- Margin risk (rising cost, pricing pressure)
- Operational risk (pipeline gap, vendor dependency)

## Step 5 — QBR narrative

Write a 500–800 word narrative in plain business English with this structure:
1. Quarter headline (one sentence)
2. Revenue story (trend + why)
3. Margin story (trend + why)
4. Customer story (health + pipeline)
5. Three opportunities
6. Three risks
7. One-paragraph call to action for next quarter

## Step 6 — Export

Generate:
1. **`qbr-{YYYY-QN}.pdf`** — formatted narrative + key charts (as ASCII tables if no chart tool available)
2. Save to `--save-to` location

## Connector failures

If QuickBooks is unreachable, stop — the QBR requires QB financial data as the foundation. If PayPal is missing, skip cross-validation and note "PayPal not connected — revenue validated from QB only." If HubSpot is missing, skip customer health (Step 2) and note "HubSpot not connected — customer health section skipped."

## Approval gates

- **Never publish or email the QBR automatically.** Always display for owner review first.
- **Flag if any data source returns incomplete data** — note gaps in the narrative.

## Output

Present the narrative in-line, then confirm export. End with a one-paragraph "what to focus on next quarter" summary.

