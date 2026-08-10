---
name: competition-supply-chain
display_name: competition-supply-chain
platform: OpenCode
category: General and specialized workflows
---

# competition-supply-chain - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `competition-supply-chain` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Internal downstream skill for ctf-sandbox-orchestrator. CTF-sandbox workflow for CI/CD, registry, dependency drift, artifact provenance, image build, release pipeline, and runtime consumer challenges. Use when the user a

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the competition-supply-chain skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `competition-supply-chain` |
| Canonical name | `competition-supply-chain` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Internal downstream skill for ctf-sandbox-orchestrator. CTF-sandbox workflow for CI/CD, registry, dependency drift, artifact provenance, image build, release pipeline, and runtime consumer challenges. Use when the user a


## Original SKILL.md

---
name: competition-supply-chain
description: Internal downstream skill for ctf-sandbox-orchestrator. CTF-sandbox workflow for CI/CD, registry, dependency drift, artifact provenance, image build, release pipeline, and runtime consumer challenges. Use when the user asks to trace dependency drift, registry pulls, malicious packages, build or release tampering, CI execution, artifact signing, or which shipped artifact the runtime actually consumes. Use only after `$ctf-sandbox-orchestrator` has already established sandbox assumptions and routed here.
---

# Competition Supply Chain

Use this skill only as a downstream specialization after `$ctf-sandbox-orchestrator` is already active and has established sandbox assumptions, node ownership, and evidence priorities. If that has not happened yet, return to `$ctf-sandbox-orchestrator` first.

Use this skill when the challenge is really about provenance, dependency drift, build output, release flow, or what runtime artifact actually got shipped.

Reply in Simplified Chinese unless the user explicitly requests English.

## Quick Start

1. Split the problem into source, dependency resolution, build, packaging, publish, and runtime consumption.
2. Decide where the first divergence occurs between intended artifact and runtime artifact.
3. Keep provenance as a compact chain, not a scattered set of observations.
4. Reproduce the smallest possible build or package path that still shows the issue.
5. Separate checked-in intent from what the pipeline actually emitted.

## Workflow

### 1. Trace Provenance End-To-End

- Map source checkout, lockfiles, dependency fetch, pre/post-install steps, build scripts, packaging, publish target, and runtime consumer.
- Compare declared version, resolved version, and shipped artifact.
- Note registry, cache, mirror, or CI environment differences.

### 2. Reconcile Build-Time And Runtime

- Compare manifests with image layers, mounted secrets, generated files, and runtime hooks.
- Identify whether the decisive mutation happens in dependency install, build step, publish step, or runtime bootstrap.

### 3. Report The Break Point

- State the earliest point where provenance diverges.
- Keep evidence in one short chain from source to runtime consumer.

## Read This Reference

- Load `references/supply-chain.md` for the provenance checklist, evidence packaging, and common pipeline failure modes.

## What To Preserve

- Declared dependency, resolved dependency, and runtime artifact versions
- CI step names, registry pulls, artifact hashes, and image or package layers
- The runtime consumer that actually accepts or executes the artifact
