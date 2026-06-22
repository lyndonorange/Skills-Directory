---
name: implementing-honeytokens-for-breach-detection
display_name: implementing-honeytokens-for-breach-detection
platform: Codex
category: General and specialized workflows
---

# implementing-honeytokens-for-breach-detection - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `implementing-honeytokens-for-breach-detection` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

- When deploying or configuring implementing honeytokens for breach detection capabilities in your environment

## How To Use It In Codex

In Codex, click the chat box, press /, choose implementing-honeytokens-for-breach-detection, then write the task. Fallback prompt: Use the implementing-honeytokens-for-breach-detection skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `implementing-honeytokens-for-breach-detection` |
| Canonical name | `implementing-honeytokens-for-breach-detection` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

- When deploying or configuring implementing honeytokens for breach detection capabilities in your environment

## Original SKILL.md

---
name: implementing-honeytokens-for-breach-detection
description: 'Deploys canary tokens and honeytokens (fake AWS credentials, DNS canaries,
  document beacons, database records) that trigger alerts when accessed by attackers.
  Uses the Canarytokens API and custom webhook integrations for breach detection.
  Use when building deception-based early warning systems for intrusion detection.

  '
domain: cybersecurity
subdomain: security-operations
tags:
- deception-technology
- honeytokens
- canary-tokens
- breach-detection
- dns-canary
- security-operations
version: '1.0'
author: mahipal
license: Apache-2.0
nist_csf:
- DE.CM-01
- RS.MA-01
- GV.OV-01
- DE.AE-02
mitre_attack:
- T1078
- T1190
- T1059
- T1003
- T1110
---

# Implementing Honeytokens for Breach Detection


## When to Use

- When deploying or configuring implementing honeytokens for breach detection capabilities in your environment
- When establishing security controls aligned to compliance requirements
- When building or improving security architecture for this domain
- When conducting security assessments that require this implementation

## Prerequisites

- Familiarity with security operations concepts and tools
- Access to a test or lab environment for safe execution
- Python 3.8+ with required dependencies installed
- Appropriate authorization for any testing activities

## Instructions

Deploy honeytokens across critical systems to detect unauthorized access. Each token
type alerts via webhook when triggered by an attacker.

```python
import requests

# Create a DNS canary token via Canarytokens
resp = requests.post("https://canarytokens.org/generate", data={
    "type": "dns",
    "email": "soc@company.com",
    "memo": "Production DB server honeytoken",
})
token = resp.json()
print(f"DNS token: {token['hostname']}")
```

Token types to deploy:
1. AWS credential files (~/.aws/credentials) with canary keys
2. DNS tokens embedded in configuration files
3. Document beacons (Word/PDF) in sensitive file shares
4. Database honeytoken records in user tables
5. Web bugs in internal wiki/documentation pages

## Examples

```python
# Generate a fake AWS credentials file with canary token
aws_creds = f"[default]\naws_access_key_id = {canary_key_id}\naws_secret_access_key = {canary_secret}\n"
with open("/opt/backup/.aws/credentials", "w") as f:
    f.write(aws_creds)
```

