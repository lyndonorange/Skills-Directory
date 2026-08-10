---
name: agent-platform-skill-registry
display_name: agent-platform-skill-registry
platform: Universal Agents
category: General and specialized workflows
---

# agent-platform-skill-registry - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `agent-platform-skill-registry` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Interact with the Gemini Enterprise Agent Platform Skill Registry to create and search for available skills. Use this skill to enable agents to register functionality or discover new capabilities.

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the agent-platform-skill-registry skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `agent-platform-skill-registry` |
| Canonical name | `agent-platform-skill-registry` |
| Platform | `Universal Agents` |
| Category | General and specialized workflows |

## Description

Interact with the Gemini Enterprise Agent Platform Skill Registry to create and search for available skills. Use this skill to enable agents to register functionality or discover new capabilities.

## Upstream provenance

This adapted package derives from [Google Agent Skills](https://github.com/google/skills/tree/092e210b243601797a0fb939040be2b1288e6d39) at commit `092e210b243601797a0fb939040be2b1288e6d39`, licensed under `Apache-2.0`.


## Original SKILL.md

---
name: agent-platform-skill-registry
description: "Interact with the Gemini Enterprise Agent Platform Skill Registry to create and search for available skills. Use this skill to enable agents to register functionality or discover new capabilities."
license: Apache-2.0
---

## Universal runtime boundary

- Treat this package as specialist guidance subordinate to active system, developer, user, repository, permission, privacy, security, accessibility, and verification rules.
- Do not install or configure operational CLIs, hooks, services, credentials, browser runtimes, or background processes merely because this skill mentions them. Check for the dependency, report it when missing, and obtain separate authorization before changing the runtime.
- Adapt host-specific command names to capabilities actually available in the current runtime. Report unsupported integrations instead of claiming they ran.
- Read `references/upstream.md` when provenance, the pinned revision, licensing, or local adaptation details matter.

# Skill Registry

This skill provides instructions for interacting with the **Skill Registry** on
the Gemini Enterprise Agent Platform.

## Core Capabilities

-   **Skill Discovery** - Query the registry to easily search, list, get
    specific skills, and inspect revision histories.
-   **Skill Lifecycle Management** - Upload, update, or permanently delete
    skills.
-   **Operation Monitoring** - Utility to check the completion status of
    long-running state changes (LROs).
-   **Generate Skill** - Automate the initial scaffolding of new agent skills
    locally.

## Core Directives

-   **Mandatory Validation**: ALWAYS execute the environment validation check
    before performing any operations.

    Before any operation, you **must** validate the core environment.

    ```bash
    # Execute the validation script
    python3 scripts/validate_env.py
    ```

## Prerequisites & Authentication

### Library & Authentication

Ensure you have the latest Google Cloud credentials and libraries installed.

```bash
# Install required libraries
pip install google-auth requests

# Authenticate with Google Cloud
gcloud auth application-default login
```

### Environment Variables

The following variables are required for operations:

-   `GCP_PROJECT_ID`: Your Google Cloud Project ID.
-   `GCP_LOCATION`: The region (e.g., `us-central1`).

--------------------------------------------------------------------------------

## Quickstart

Quickly search for available skills in the registry:

```bash
python3 scripts/skill_registry_ops.py search \
  --query "test skill" \
  --top-k 5
```

--------------------------------------------------------------------------------

## Operations

-   **Skill Discovery**: [query-skills.md](references/query-skills.md)
-   **Skill Lifecycle**: [manage-skills.md](references/manage-skills.md)
-   **Monitor Operations**:
    [monitor-operations.md](references/monitor-operations.md)
-   **Generate Skill**: [generate-skill.md](references/generate-skill.md)
