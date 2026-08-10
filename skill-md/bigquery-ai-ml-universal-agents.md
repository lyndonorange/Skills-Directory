---
name: bigquery-ai-ml
display_name: bigquery-ai-ml
platform: Universal Agents
category: Data, analytics, and databases
---

# bigquery-ai-ml - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `bigquery-ai-ml` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Leverages BigQuery's built-in machine learning and GenAI capabilities for advanced data analytics. Use when you need to write SQL queries that perform time-series forecasting, predict values, detect outliers or anomalies

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the bigquery-ai-ml skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `bigquery-ai-ml` |
| Canonical name | `bigquery-ai-ml` |
| Platform | `Universal Agents` |
| Category | Data, analytics, and databases |

## Description

Leverages BigQuery's built-in machine learning and GenAI capabilities for advanced data analytics. Use when you need to write SQL queries that perform time-series forecasting, predict values, detect outliers or anomalies

## Upstream provenance

This adapted package derives from [Google Agent Skills](https://github.com/google/skills/tree/092e210b243601797a0fb939040be2b1288e6d39) at commit `092e210b243601797a0fb939040be2b1288e6d39`, licensed under `Apache-2.0`.


## Original SKILL.md

---
name: bigquery-ai-ml
description: "Leverages BigQuery's built-in machine learning and GenAI capabilities for advanced data analytics. Use when you need to write SQL queries that perform time-series forecasting, predict values, detect outliers or anomalies, find key drivers, perform semantic search or vector search, classify text, calculate similarity, summarize content, translate language, evaluate models, filter by semantic conditions, or leverage generative AI capabilities in BigQuery. Do not use for general BigQuery dataset, table, or job management requests."
license: Apache-2.0
---

## Universal runtime boundary

- Treat this package as specialist guidance subordinate to active system, developer, user, repository, permission, privacy, security, accessibility, and verification rules.
- Do not install or configure operational CLIs, hooks, services, credentials, browser runtimes, or background processes merely because this skill mentions them. Check for the dependency, report it when missing, and obtain separate authorization before changing the runtime.
- Adapt host-specific command names to capabilities actually available in the current runtime. Report unsupported integrations instead of claiming they ran.
- Read `references/upstream.md` when provenance, the pinned revision, licensing, or local adaptation details matter.

# BigQuery AI & ML

BigQuery integrates with Vertex AI to provide powerful machine learning and
generative AI capabilities directly within SQL queries using built-in functions
like `AI.FORECAST`, `AI.KEY_DRIVERS`, `AI.DETECT_ANOMALIES`, and `AI.GENERATE`.

## Reference Directory

-   **Functions Reference**:

    -   **AI.AGG**: [ai_agg.md](references/ai_agg.md) - Multi-row semantic
        aggregation and summarization.
    -   **AI.CLASSIFY**: [ai_classify.md](references/ai_classify.md) - Classify
        text.
    -   **AI.DETECT_ANOMALIES**:
        [ai_detect_anomalies.md](references/ai_detect_anomalies.md) - Detect
        anomalies.
    -   **AI.EVALUATE**: [ai_evaluate.md](references/ai_evaluate.md) - Evaluate
        models.
    -   **AI.FORECAST**: [ai_forecast.md](references/ai_forecast.md) -
        Time-series forecasting.
    -   **AI.GENERATE**: [ai_generate.md](references/ai_generate.md) - Generate
        text using LLMs.
    -   **AI.GENERATE_EMBEDDING**:
        [ai_generate_embedding.md](references/ai_generate_embedding.md) -
        Generate embeddings.
    -   **AI.GENERATE_TABLE**:
        [ai_generate_table.md](references/ai_generate_table.md) - Table-valued
        AI generation.
    -   **AI.IF**: [ai_if.md](references/ai_if.md) - Evaluate semantic
        conditions.
    -   **AI.KEY_DRIVERS**: [ai_key_drivers.md](references/ai_key_drivers.md) -
        Identifies key drivers, this is a TVF.
    -   **AI.SCORE**: [ai_score.md](references/ai_score.md) - Score data.
    -   **AI.SEARCH**: [ai_search.md](references/ai_search.md) - Semantic
        search.
    -   **AI.SIMILARITY**: [ai_similarity.md](references/ai_similarity.md) -
        Semantic similarity.
    -   **Remote Models**: [remote_models.md](references/remote_models.md) -
        Working with remote models (Vertex AI).
    -   **CONTRIBUTION_ANALYSIS**:
        [ml_contribution_analysis.md](references/ml_contribution_analysis.md)
        -   Finds contributing factors, key drivers of change. Requires creating
            a MODEL entity.
    -   **VECTOR_SEARCH**: [vector_search.md](references/vector_search.md) -
        Vector search best practices.

## Related Skills

-   [BigQuery Basics Skill](../bigquery-basics): SKILL.md file for core BigQuery
    concepts, resource management, CLI, and client libraries.
