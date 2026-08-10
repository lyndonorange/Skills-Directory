---
name: openhands-agent-canvas
display_name: openhands-agent-canvas
platform: OpenCode
category: General and specialized workflows
---

# openhands-agent-canvas - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `openhands-agent-canvas` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Operate, inspect, troubleshoot, and verify the local OpenHands Agent Canvas installation and its built-in OpenHands or ACP agent profiles. Use for launching or stopping Agent Canvas, checking health, selecting an install

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the openhands-agent-canvas skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `openhands-agent-canvas` |
| Canonical name | `openhands-agent-canvas` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Operate, inspect, troubleshoot, and verify the local OpenHands Agent Canvas installation and its built-in OpenHands or ACP agent profiles. Use for launching or stopping Agent Canvas, checking health, selecting an install


## Original SKILL.md

---
name: openhands-agent-canvas
description: Operate, inspect, troubleshoot, and verify the local OpenHands Agent Canvas installation and its built-in OpenHands or ACP agent profiles. Use for launching or stopping Agent Canvas, checking health, selecting an installed coding agent, validating ACP connectivity, inspecting local profiles, or maintaining this installation without exposing secrets or changing model credentials.
---

# OpenHands Agent Canvas

Use the installed local Agent Canvas as the visual workspace for OpenHands and authenticated ACP coding agents. Keep the service localhost-only and preserve the user's model and account choices.

## Route the request

- Launch or open the app: use the signed Desktop launcher, then verify the health endpoint.
- Inspect agents: read the profile API and report which profiles materialize successfully.
- Validate ACP: perform initialize and session-create only; do not send a model prompt unless the user requested a model call.
- Fix Codex skill-budget warnings: refresh the dedicated Canvas Codex home with `configure_codex_skills.py`; do not alter the regular Codex home or the shared skillset.
- Synchronize local models: query the live Atomic Chat, oMLX, and LM Studio `/v1/models` catalogs with `sync_local_models.py`, exclude embedding-only models from chat profiles, then test one bounded completion per provider.
- Add an agent: require an installed stdio ACP command, validate it independently, create the profile, and materialize it.
- Troubleshoot: check the launcher log, process ports, profile materialization, then the relevant ACP command.
- Change models, credentials, automation, remote access, or security boundaries: pause for explicit authorization.

## Safety contract

1. Never print, copy, commit, or expose the Agent Canvas API key or agent-provider credentials.
2. Bind services to localhost. Do not enable remote access, tunnels, or public listeners without explicit authorization.
3. Preserve existing profiles and conversations. Use disposable conversations for verification and delete only those test records.
4. Treat agent installation, account login, model selection, paid API use, and autonomous automation as separate decisions.
5. Do not claim an agent is usable from command discovery alone. Require an ACP initialize plus session-create check or an equivalent native health check.
6. Keep the built-in OpenHands profile credential-free until the user chooses an LLM provider and model.
7. Catalog visibility is not proof that every model can run as a coding agent. Never load or invoke all local models at once; verify one representative chat model per live endpoint and report embedding-only or tool-calling limitations truthfully.

## Standard verification

1. Confirm the signed launcher and installed application exist.
2. Open the Desktop launcher and wait for `http://127.0.0.1:8000/health` to return healthy.
3. Confirm the configured UI port and internal agent ports belong to this installation.
4. List profiles without revealing secrets and materialize each intended profile.
5. For ACP profiles, negotiate protocol version 1 and create a disposable session.
6. Confirm the effective Canvas Codex prompt stays within its focused skill budget and contains no truncation warning.
7. Synchronize local model profiles from live catalogs, then run one representative completion per provider.
8. Scan current startup logs for fatal errors and credential leakage.
9. Report handshake-verified agents, prompt-verified routes, catalog-only models, embedding models, and credential-blocked routes separately.

Read [references/operations.md](references/operations.md) for the pinned local paths, installed profiles, commands, rollback location, and known limitations.
