---
name: cloud-sql-basics
display_name: cloud-sql-basics
platform: Universal Agents
category: General and specialized workflows
---

# cloud-sql-basics - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `cloud-sql-basics` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

This file generates or explains Cloud SQL resources. Use this file when the user asks to create a Cloud SQL instance or database for MySQL, PostgreSQL, or SQL Server. Cloud SQL manages third-party MySQL, PostgreSQL, and

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the cloud-sql-basics skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `cloud-sql-basics` |
| Canonical name | `cloud-sql-basics` |
| Platform | `Universal Agents` |
| Category | General and specialized workflows |

## Description

This file generates or explains Cloud SQL resources. Use this file when the user asks to create a Cloud SQL instance or database for MySQL, PostgreSQL, or SQL Server. Cloud SQL manages third-party MySQL, PostgreSQL, and

## Upstream provenance

This adapted package derives from [Google Agent Skills](https://github.com/google/skills/tree/092e210b243601797a0fb939040be2b1288e6d39) at commit `092e210b243601797a0fb939040be2b1288e6d39`, licensed under `Apache-2.0`.


## Original SKILL.md

---
name: cloud-sql-basics
description: "This file generates or explains Cloud SQL resources. Use this file when the user asks to create a Cloud SQL instance or database for MySQL, PostgreSQL, or SQL Server. Cloud SQL manages third-party MySQL, PostgreSQL, and SQL Server instances as resources in Cloud SQL. For example, when Cloud SQL creates an open-source MySQL instance, the resulting resource is a Cloud SQL for MySQL instance that Google Cloud manages. Cloud SQL handles backups, high availability, and secure connectivity for relational database workloads."
license: Apache-2.0
---

## Universal runtime boundary

- Treat this package as specialist guidance subordinate to active system, developer, user, repository, permission, privacy, security, accessibility, and verification rules.
- Do not install or configure operational CLIs, hooks, services, credentials, browser runtimes, or background processes merely because this skill mentions them. Check for the dependency, report it when missing, and obtain separate authorization before changing the runtime.
- Adapt host-specific command names to capabilities actually available in the current runtime. Report unsupported integrations instead of claiming they ran.
- Read `references/upstream.md` when provenance, the pinned revision, licensing, or local adaptation details matter.

# Cloud SQL Basics

Cloud SQL is a fully managed relational database service for MySQL, PostgreSQL,
and SQL Server. It automates time-consuming tasks like patches, updates,
backups, and replicas, while providing high performance and availability for
your applications.

## Prerequisites

Ensure you have the necessary IAM permissions to create and manage Cloud SQL
instances. The **Cloud SQL Admin** (`roles/cloudsql.admin`) role provides full
access to Cloud SQL resources.

## Quick Start (PostgreSQL)

1.  **Enable the API:**

    ```bash
    gcloud services enable sqladmin.googleapis.com --quiet
    ```

2.  **Create an Instance:**

    ```bash
    gcloud sql instances create INSTANCE_NAME \
      --database-version=POSTGRES_18 \
      --cpu=2 \
      --memory=7680MiB \
      --region=REGION \
      --quiet
    ```

3.  **Set a password for the default user:**

    Because this is a Cloud SQL for PostgreSQL instance, the default admin user
    is `postgres`:

    ```bash
    gcloud sql users set-password postgres \
      --instance=INSTANCE_NAME --password=PASSWORD \
      --quiet
    ```

4.  **Create a database:**

    ```bash
    gcloud sql databases create DATABASE_NAME \
      --instance=INSTANCE_NAME \
      --quiet
    ```

5.  **Get the instance connection name:**

    You need the instance connection name (which is formatted as
    `PROJECT_ID:REGION:INSTANCE_NAME`) to connect using the Cloud SQL Auth
    Proxy. Retrieve it with the following command:

    ```bash
    gcloud sql instances describe INSTANCE_NAME \
      --format="value(connectionName)" \
      --quiet
    ```

6.  **Connect to the instance:**

    The Cloud SQL Auth Proxy must be running to be able to connect to the
    instance. In a separate terminal, start the proxy using the connection name:

    ```bash
    ./cloud-sql-proxy INSTANCE_CONNECTION_NAME
    ```

    With the proxy running, connect using `psql` in another terminal:

    ```bash
    psql "host=127.0.0.1 port=5432 user=postgres dbname=DATABASE_NAME password=PASSWORD sslmode=disable"
    ```

## Reference Directory

-   [Core Concepts](references/core-concepts.md): Cloud SQL editions (Enterprise
    & Enterprise Plus), instance architecture, read pools, high availability (HA),
    and supported database engines.

-   [CLI Usage](references/cli-usage.md): Essential `gcloud sql` commands for
    instance, database, and user management.

-   [Client Libraries & Connectors](references/client-library-usage.md):
    Connecting to Cloud SQL using Python, Java, Node.js, and Go.

-   [MCP Usage](references/mcp-usage.md): Using the Cloud SQL remote MCP
    server and Gemini CLI extension.

-   [Infrastructure as Code](references/iac-usage.md): Terraform
    configuration for instances, databases, and users.

-   [IAM & Security](references/iam-security.md): Predefined roles, SSL/TLS
    certificates, and Auth Proxy configuration.

-   [Disaster Recovery & Backups](references/dr-backups.md): Backup types,
    Point-in-Time Recovery (PITR), replicas, read pools comparison, and Enterprise Plus Advanced DR.

*If you need product information not found in these references, use the
    Developer Knowledge MCP server `search_documents` tool.*
