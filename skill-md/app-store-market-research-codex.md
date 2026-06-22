---
name: app-store-market-research
display_name: app-store-market-research
platform: Codex
category: Business creation, ideas, and validation
---

# app-store-market-research - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `app-store-market-research` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Turn a single app identifier into a compact market brief for the iOS App Store category around it.

## How To Use It In Codex

In Codex, click the chat box, press /, choose app-store-market-research, then write the task. Fallback prompt: Use the app-store-market-research skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `app-store-market-research` |
| Canonical name | `app-store-market-research` |
| Platform | `Codex` |
| Category | Business creation, ideas, and validation |

## Description

Turn a single app identifier into a compact market brief for the iOS App Store category around it.

## Original SKILL.md

---
name: app-store-market-research
description: Build an App Store market brief from an app name, App Store URL, or bundle ID. Use when the user wants competitor research, revenue estimates, market maps, TAM sizing, monetization analysis, or reusable investor-style briefs for an iOS app category.
metadata:
  short-description: App Store competitor and market sizing workflow
---

# App Store Market Research

Turn a single app identifier into a compact market brief for the iOS App Store category around it.

## Use this skill when

- The user gives an App Store URL, app name, app ID, or bundle ID.
- The user wants competitor research for an iOS app.
- The user wants revenue estimates, market sizing, TAM, or monetization analysis for an App Store category.
- The user wants a repeatable brief instead of one-off ASO commentary.
- The user wants the result in a reusable format such as a markdown report or CSV-ready table.

Do not use this skill for implementation work, app screenshots critique, or pure keyword-ASO requests unless the user also wants market or revenue analysis.

## Inputs

Accept any of:

- App Store URL
- App name
- App ID
- Bundle ID

Optional:

- Storefront/country
- Specific competitors to include
- Whether to focus on subscription revenue, total monetization, or category TAM
- Whether to include Android / Google Play and web competitors
- Preferred output mode: brief, markdown table, CSV-ready table, full memo, or PDF report

If the user does not specify storefront, default to `US`.
If the user does not specify platform scope, default to `iOS only`.

## Workflow

### 1) Resolve the target app

Use the App Store MCP if available:

- `mcp__appstore__.lookup_app` for URL, app ID, or bundle ID
- `mcp__appstore__.search_ranked` if only a name is provided

Capture:

- app name
- developer
- app ID
- bundle ID
- genre
- rating
- review count
- release date
- update date

### 2) Build the competitor set

Prefer direct category and keyword competitors over noisy name-based matches.

Use:

- `mcp__appstore__.find_app_rank` on 4 to 8 relevant category keywords
- `mcp__appstore__.search_ranked` for the core head term
- `mcp__appstore__.app_competitors` only as a secondary input because broad names can pollute results

Assemble a practical competitor set of roughly 5 to 10 apps. Favor the apps that repeatedly appear across relevant keyword searches.

### 3) Gather monetization evidence

Use current sources only.

- Use the App Store MCP for ratings, rank context, and app identity.
- Use web search for live pricing, subscription tiers, and official policy facts.
- Prefer App Store pages, official websites, and Apple developer documentation.

If the user asks for cross-platform coverage:

- Use Google Play listings for Android pricing, installs, and review volume.
- Use official product websites for web subscriptions and browser-based plans.
- Keep the output explicit about which estimates are `iOS-only` versus `cross-platform`.

For each meaningful competitor, capture:

- monetization model: free, subscription, ads, one-time unlock, commerce, hybrid
- visible pricing tiers
- review count
- notable business model differences

### 4) Estimate revenue carefully

You do not have direct revenue data unless the user provides it. Always label estimates as modeled.

Model output should include:

- low / base / high annual revenue estimate
- whether that estimate is gross consumer spend or net developer revenue
- Apple fee assumption
- major caveats

Useful heuristics:

- Subscription utilities usually monetize through a small paying subset with relatively high ARPPU.
- One-time purchase apps have lower lifetime ceilings than subscriptions.
- Community or commerce apps can have larger upside than utility-only trackers.
- Review volume is only a proxy and should never be presented as revenue.

If exact market-intel tools are unavailable, say so plainly and produce a public-signal estimate.

### 5) Build the market map

Group competitors by business model, not just feature overlap. Common buckets:

- free strategic network
- premium utility
- freemium subscription
- community/social
- commerce-enabled
- indie one-time purchase

For each segment, explain:

- who is in it
- what the monetization logic is
- what the likely ceiling is

### 6) Build the TAM model

Use current sources for the top-down inputs when the user asks for TAM or market size:

- adult population
- reading or category-participation rate
- iOS share or installed-base proxy
- likely serviceable audience

Make the formulas explicit. Prefer:

- conservative
- base
- upside

Each scenario should show:

- reachable users
- paying conversion
- ARPPU or subscription revenue per payer
- annual revenue
- optional contribution profit range

### 7) Produce the brief

Default output sections:

1. Target app summary
2. Competitor revenue table
3. Market map
4. Bottom-up TAM model
5. Key takeaways
6. Sources and assumptions

## Output modes

Choose the lightest useful output unless the user asks for a specific format:

- `brief`: short narrative summary with key numbers
- `markdown-table`: report plus one or more markdown tables
- `csv-ready`: include flat tables that can be pasted into Sheets
- `full-memo`: investor-style write-up with assumptions and caveats
- `pdf-report`: create a polished report and render it as a PDF file

For `full-memo`, include CSV blocks by default unless the user explicitly says not to. The default `full-memo` package should include:

- narrative memo
- competitor revenue CSV
- TAM scenario CSV
- key input assumptions CSV

If the user asks for cross-platform coverage in `full-memo`, also include:

- cross-platform adjusted competitor CSV

For `csv-ready`:

- Prefer flat, pasteable `csv` fenced code blocks
- If the user wants files, write one or more `.csv` files and tell them the paths

For `pdf-report`:

- First prepare the same content as `full-memo`
- Then create a clean PDF version with the narrative, tables, and sources
- If CSV is also requested, include both the PDF and the CSV blocks or CSV files
- Read `references/pdf-output.md` before generating the PDF

When the user asks for structured data, read `references/output-modes.md`.
When the user asks for a standard market brief layout, read `references/report-template.md`.
When the user asks for Android or web inclusion, read `references/cross-platform-scope.md`.
When the user asks for a PDF, read `references/pdf-output.md`.

## Output rules

- Use concrete dates when referencing current facts.
- Separate fact from inference.
- Provide links to sources.
- Do not imply exact revenue unless a source explicitly reports it.
- State when a figure is estimated, modeled, or inferred.
- Keep the tone investor-practical rather than promotional.
- When emitting CSV, place each table in its own fenced `csv` block.
- In CSV output, label estimate scope clearly, such as `iOS only` or `cross-platform adjusted`.

## Quick prompts

- Use `$app-store-market-research` on this App Store URL and build a competitor revenue table, market map, and TAM model.
- Use `$app-store-market-research` for this app name and estimate how much profit potential exists in the category.
- Use `$app-store-market-research` on this app and compare the utility-only business model against community or commerce-led competitors.
- Use `$app-store-market-research` on this app and return a CSV-ready competitor revenue table plus a TAM model.
- Use `$app-store-market-research` on this app and include Google Play and web subscription competitors.
- Use `$app-store-market-research` on this app and produce a full memo with built-in CSV tables.
- Use `$app-store-market-research` on this app and create a PDF report with the CSV tables included.

## Reference

- Read `references/report-template.md` when you need a consistent structure for the final brief.
- Read `references/output-modes.md` for markdown-table and CSV-ready output shapes.
- Read `references/cross-platform-scope.md` when the user wants Android or web coverage.
- Read `references/pdf-output.md` when the user wants a PDF artifact.

