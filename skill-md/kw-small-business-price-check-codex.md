---
name: kw-small-business-price-check
display_name: kw-small-business-price-check
platform: Codex
category: General and specialized workflows
---

# kw-small-business-price-check - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-small-business-price-check` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

knowledge-work-plugin: small-business

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-small-business-price-check, then write the task. Fallback prompt: Use the kw-small-business-price-check skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-small-business-price-check` |
| Canonical name | `kw-small-business-price-check` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

knowledge-work-plugin: small-business

## Original SKILL.md

---
knowledge-work-plugin: small-business
upstream-skill: price-check
name: kw-small-business-price-check
description: Produces a margin-by-product table and three pricing-scenario data views so the owner can see the full financial picture before making a pricing decision. Accepts optional product name argument.
allowed-tools: Read, WebFetch, Bash
---

Run the pricing analysis. Pull cost and revenue data, build the margin table, and model three pricing scenarios — so the owner can see the numbers clearly before deciding what to charge.

Parse arguments:
- `PRODUCT_NAME` (optional) — specific product or service to analyze; if omitted, analyze all active products

## Step 1 — Current margin baseline

Using the `margin-analyzer` skill workflow:

1. Pull QuickBooks revenue by product/service for the last 90 days.
2. Pull COGS or direct costs per product from QuickBooks (if categorized).
3. Pull PayPal gross sales for the same products to cross-validate.
4. Calculate current gross margin per product: (revenue − COGS) ÷ revenue.

Build the margin table:

```
Product          | Revenue  | COGS     | Gross Margin | Margin %
{product}        | ${amt}   | ${amt}   | ${amt}       | {X}%
```

Flag any product with margin below 20% as a risk.

## Step 2 — Three pricing scenarios

For each product (or the specified product), model three scenarios. Do NOT recommend a price — present data only.

**Scenario A — Hold current price**
- Project revenue at current price × current volume
- Project margin at current COGS

**Scenario B — Price increase (+10% to +20%, owner to specify)**
- Project revenue assuming 0%, 5%, and 10% volume loss at new price
- Show the break-even volume needed to maintain current profit

**Scenario C — Price decrease (−10%, to drive volume)**
- Project revenue assuming 10%, 20%, and 30% volume increase
- Show the volume needed to match current profit

Present each scenario as a data table, not a recommendation.

## Step 3 — Customer messaging brief

Produce a plain-language brief (for price increase scenarios) the owner can use to communicate a change to customers:
- One paragraph explaining the change
- Three key message options (direct, value-focused, empathetic)
- Suggested timing and channel (email, invoice note, in-person)

## Connector failures

If QuickBooks is unreachable, stop — margin analysis requires QB revenue and cost data. If PayPal is missing, run from QB-only and note "PayPal not connected — cross-validation against PayPal sales skipped."

## Approval gates

- **Never recommend a specific price.** Provide data views only — pricing decisions belong to the owner.
- **Flag if COGS data is incomplete** (many QB setups don't track per-product COGS) and note the gap.
- **Never update any prices in QB, PayPal, or any connected system.**

## Output

Present the margin table, then the three scenario tables side-by-side. If a price increase scenario is being considered, append the customer messaging brief. End with: "Which scenario would you like to explore further?"

