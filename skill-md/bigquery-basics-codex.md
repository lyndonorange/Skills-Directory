---
name: bigquery-basics
display_name: bigquery-basics
platform: Codex
category: Data, analytics, and databases
---

# bigquery-basics - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `bigquery-basics` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Manages datasets, tables, and jobs in BigQuery. Use when you need to interact with BigQuery, run SQL queries, manage BigQuery resources (datasets, tables, views), or perform basic data ingestion and analysis.

## How To Use It In Codex

In Codex, click the chat box, press /, choose bigquery-basics, then write the task. Fallback prompt: Use the bigquery-basics skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `bigquery-basics` |
| Canonical name | `bigquery-basics` |
| Platform | `Codex` |
| Category | Data, analytics, and databases |

## Description

Manages datasets, tables, and jobs in BigQuery. Use when you need to interact with BigQuery, run SQL queries, manage BigQuery resources (datasets, tables, views), or perform basic data ingestion and analysis.

## Upstream provenance

This adapted package derives from [Google Agent Skills](https://github.com/google/skills/tree/092e210b243601797a0fb939040be2b1288e6d39) at commit `092e210b243601797a0fb939040be2b1288e6d39`, licensed under `Apache-2.0`.


## Original SKILL.md

---
name: bigquery-basics
description: "Manages datasets, tables, and jobs in BigQuery. Use when you need to interact with BigQuery, run SQL queries, manage BigQuery resources (datasets, tables, views), or perform basic data ingestion and analysis."
license: Apache-2.0
---

## Universal runtime boundary

- Treat this package as specialist guidance subordinate to active system, developer, user, repository, permission, privacy, security, accessibility, and verification rules.
- Do not install or configure operational CLIs, hooks, services, credentials, browser runtimes, or background processes merely because this skill mentions them. Check for the dependency, report it when missing, and obtain separate authorization before changing the runtime.
- Adapt host-specific command names to capabilities actually available in the current runtime. Report unsupported integrations instead of claiming they ran.
- Read `references/upstream.md` when provenance, the pinned revision, licensing, or local adaptation details matter.

# BigQuery Basics

BigQuery is a serverless, AI-ready data platform that enables high-speed
analysis of large datasets using SQL and Python. Its disaggregated architecture
separates compute and storage, allowing them to scale independently while
providing built-in machine learning, geospatial analysis, and business
intelligence capabilities.

## Setup and Basic Usage

1.  **Enable the BigQuery API:**

    ```bash
    gcloud services enable bigquery.googleapis.com --quiet
    ```

2.  **Create a Dataset:**

    ```bash
    bq mk --dataset --location=US my_dataset
    ```

3.  **Create a Table:**

    Create a file named `schema.json` with your table schema:

    ```json
    [
      {
        "name": "name",
        "type": "STRING",
        "mode": "REQUIRED"
      },
      {
        "name": "post_abbr",
        "type": "STRING",
        "mode": "NULLABLE"
      }
    ]
    ```

    Then create the table with the `bq` tool:

    ```bash
    bq mk --table my_dataset.mytable schema.json
    ```

4.  **Run a Query:**

    ```bash
    bq query --use_legacy_sql=false \
    'SELECT name FROM `bigquery-public-data.usa_names.usa_1910_2013` \
    WHERE state = "TX" LIMIT 10'
    ```

## Reference Directory

- [Core Concepts](references/core-concepts.md): Storage types, analytics
  workflows, and BigQuery Studio features.

- [Change History](references/change-history.md): Tracking and querying
  incremental table changes using APPENDS and CHANGES.

-   [Continuous Queries](references/continuous-queries.md): Running continuous
    SQL statements to analyze incoming data in real time.

- [CLI Usage](references/cli-usage.md): Essential `bq` command-line tool
  operations for managing data and jobs.

- [Client Libraries](references/client-library-usage.md): Using Google Cloud
  client libraries for Python, Java, Node.js, and Go.

- [MCP Usage](references/mcp-usage.md): Using the BigQuery remote MCP server and
  Gemini CLI extension.

- [Infrastructure as Code](references/iac-usage.md): Terraform examples for
  datasets, tables, and reservations.

- [IAM & Security](references/iam-security.md): Roles, permissions, and data
  governance best practices.

*If you need product information not found in these references, use the
Developer Knowledge MCP server `search_documents` tool.*

## Related Skills

- [BigQuery AI & ML Skill](../bigquery-ai-ml):
  SKILL.md file for BigQuery AI and ML capabilities (forecast, anomaly
  detection, text generation).
