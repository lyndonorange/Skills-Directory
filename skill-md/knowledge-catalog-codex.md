---
name: knowledge-catalog
display_name: knowledge-catalog
platform: Codex
category: General and specialized workflows
---

# knowledge-catalog - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `knowledge-catalog` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Use Google Cloud Knowledge Catalog local workflows: OKF bundles, Metadata as Code with kcmd, discovery/enrichment agents, and safe MCP setup.

## How To Use It In Codex

In Codex, click the chat box, press /, choose knowledge-catalog, then write the task. Fallback prompt: Use the knowledge-catalog skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `knowledge-catalog` |
| Canonical name | `knowledge-catalog` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Use Google Cloud Knowledge Catalog local workflows: OKF bundles, Metadata as Code with kcmd, discovery/enrichment agents, and safe MCP setup.


## Original SKILL.md

---
name: knowledge-catalog
description: Use Google Cloud Knowledge Catalog local workflows: OKF bundles, Metadata as Code with kcmd, discovery/enrichment agents, and safe MCP setup.
---

# Knowledge Catalog Skill

Use this skill when the user asks about Google Cloud Knowledge Catalog, OKF, metadata as code, catalog discovery, catalog enrichment, BigQuery/Data Catalog metadata, or making enterprise data context available to AI agents.

## Local Setup

- Checkout: `[local home]/Documents/Playground/knowledge-catalog`
- Human guide: `[local home]/Documents/Playground/knowledge-catalog/local-guide/index.html`
- `kcmd`: `[local home]/.local/bin/kcmd`
- `kcagent`: `[local home]/.local/bin/kcagent`
- `md-fileset`: `[local home]/.local/bin/md-fileset`
- Google Cloud SDK: `gcloud` and `bq`

## Choose The Right Workflow

- **OKF**: use when the goal is a portable, git-reviewable knowledge bundle made of Markdown files with YAML frontmatter.
- **kcmd / Metadata as Code**: use when the goal is to pull, inspect, modify, or push Knowledge Catalog metadata snapshots.
- **Discovery Agent**: use when the goal is to find relevant data assets from natural-language questions.
- **Enrichment Agent**: use when the goal is to improve catalog metadata using docs, schemas, files, or other knowledge sources.
- **md-fileset MCP**: use when an agent needs local markdown search/read tools over a documentation folder.

## Safety Rules

- Do not run `kcmd push`, `kcagent enrich`, BigQuery jobs, or catalog-publishing commands without explicit user approval.
- If `gcloud auth application-default login`, project config, IAM roles, or APIs are missing, explain the missing prerequisite and stop before cloud calls.
- Prefer local snapshots, dry runs, and `git diff` before publishing metadata.
- Never print credentials, tokens, private catalog data, or sensitive metadata in chat.

## Useful Commands

```bash
kcmd --version
md-fileset --version
gcloud --version
bq version
```

Manual auth setup:

```bash
gcloud auth application-default login
gcloud config set project YOUR_PROJECT_ID
gcloud auth application-default set-quota-project YOUR_PROJECT_ID
```

`kcmd` MCP template for an existing snapshot:

```json
{
  "mcpServers": {
    "knowledge-catalog-metadata": {
      "command": "kcmd",
      "args": ["mcp", "--path", "/path/to/catalog/root"]
    }
  }
}
```

`md-fileset` MCP template for local markdown docs:

```json
{
  "mcpServers": {
    "knowledge-docs": {
      "command": "md-fileset",
      "args": ["--dir", "/path/to/docs"]
    }
  }
}
```

## Example Invocations

Codex:

```text
$knowledge-catalog Explain which Knowledge Catalog workflow fits this task.
$knowledge-catalog Prepare a safe kcmd pull plan for my catalog snapshot. Do not run cloud commands yet.
$knowledge-catalog Use OKF to design a portable knowledge bundle for this project.
```

Other AI tools: invoke the `knowledge-catalog` local skill if available, or paste this `SKILL.md` plus the local guide path and ask for a dry-run-first plan.
