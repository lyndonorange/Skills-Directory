---
name: kw-human-resources-comp-analysis
display_name: kw-human-resources-comp-analysis
platform: Codex
category: General and specialized workflows
---

# kw-human-resources-comp-analysis - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `kw-human-resources-comp-analysis` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

## How To Use It In Codex

In Codex, click the chat box, press /, choose kw-human-resources-comp-analysis, then write the task. Fallback prompt: Use the kw-human-resources-comp-analysis skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `kw-human-resources-comp-analysis` |
| Canonical name | `kw-human-resources-comp-analysis` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

## Original SKILL.md

---
knowledge-work-plugin: human-resources
upstream-skill: comp-analysis
name: kw-human-resources-comp-analysis
description: Analyze compensation — benchmarking, band placement, and equity modeling. Trigger with "what should we pay a [role]", "is this offer competitive", "model this equity grant", or when uploading comp data to find outliers and retention risks.
argument-hint: "<role, level, or dataset>"
---

# /comp-analysis

> If you see unfamiliar placeholders or need to check which tools are connected, see [CONNECTORS.md](../../CONNECTORS.md).

Analyze compensation data for benchmarking, band placement, and planning. Helps benchmark compensation against market data for hiring, retention, and equity planning.

## Usage

```
/comp-analysis $ARGUMENTS
```

## What I Need From You

**Option A: Single role analysis**
"What should we pay a Senior Software Engineer in SF?"

**Option B: Upload comp data**
Upload a CSV or paste your comp bands. I'll analyze placement, identify outliers, and compare to market.

**Option C: Equity modeling**
"Model a refresh grant of 10K shares over 4 years at a $50 stock price."

## Compensation Framework

### Components of Total Compensation
- **Base salary**: Cash compensation
- **Equity**: RSUs, stock options, or other equity
- **Bonus**: Annual target bonus, signing bonus
- **Benefits**: Health, retirement, perks (harder to quantify)

### Key Variables
- **Role**: Function and specialization
- **Level**: IC levels, management levels
- **Location**: Geographic pay adjustments
- **Company stage**: Startup vs. growth vs. public
- **Industry**: Tech vs. finance vs. healthcare

### Data Sources
- **With ~~compensation data**: Pull verified benchmarks
- **Without**: Use web research, public salary data, and user-provided context
- Always note data freshness and source limitations

## Output

Provide percentile bands (25th, 50th, 75th, 90th) for base, equity, and total comp. Include location adjustments and company-stage context.

```markdown
## Compensation Analysis: [Role/Scope]

### Market Benchmarks
| Percentile | Base | Equity | Total Comp |
|------------|------|--------|------------|
| 25th | $[X] | $[X] | $[X] |
| 50th | $[X] | $[X] | $[X] |
| 75th | $[X] | $[X] | $[X] |
| 90th | $[X] | $[X] | $[X] |

**Sources:** [Web research, compensation data tools, or user-provided data]

### Band Analysis (if data provided)
| Employee | Current Base | Band Min | Band Mid | Band Max | Position |
|----------|-------------|----------|----------|----------|----------|
| [Name] | $[X] | $[X] | $[X] | $[X] | [Below/At/Above] |

### Recommendations
- [Specific compensation recommendations]
- [Equity considerations]
- [Retention risks if applicable]
```

## If Connectors Available

If **~~compensation data** is connected:
- Pull verified market benchmarks by role, level, and location
- Compare your bands against real-time market data

If **~~HRIS** is connected:
- Pull current employee comp data for band analysis
- Identify outliers and retention risks automatically

## Tips

1. **Location matters** — Always specify location for benchmarking. SF vs. Austin vs. London are very different.
2. **Total comp, not just base** — Include equity, bonus, and benefits for a complete picture.
3. **Keep data confidential** — Comp data is sensitive. Results stay in your conversation.

