---
name: analyzing-kubernetes-audit-logs
display_name: analyzing-kubernetes-audit-logs
platform: Codex
category: Security, forensics, and incident response
---

# analyzing-kubernetes-audit-logs - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `analyzing-kubernetes-audit-logs` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

- When investigating security incidents that require analyzing kubernetes audit logs

## How To Use It In Codex

In Codex, click the chat box, press /, choose analyzing-kubernetes-audit-logs, then write the task. Fallback prompt: Use the analyzing-kubernetes-audit-logs skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `analyzing-kubernetes-audit-logs` |
| Canonical name | `analyzing-kubernetes-audit-logs` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

- When investigating security incidents that require analyzing kubernetes audit logs

## Original SKILL.md

---
name: analyzing-kubernetes-audit-logs
description: 'Parses Kubernetes API server audit logs (JSON lines) to detect exec-into-pod,
  secret access, RBAC modifications, privileged pod creation, and anonymous API access.
  Builds threat detection rules from audit event patterns. Use when investigating
  Kubernetes cluster compromise or building k8s-specific SIEM detection rules.

  '
domain: cybersecurity
subdomain: container-security
tags:
- kubernetes-security
- container-security
- audit-log-analysis
- rbac
- privilege-escalation
- k8s-api-server
- threat-detection
version: '1.0'
author: mahipal
license: Apache-2.0
nist_csf:
- PR.PS-01
- PR.IR-01
- ID.AM-08
- DE.CM-01
mitre_attack:
- T1610
- T1613
- T1078
- T1552.007
---

# Analyzing Kubernetes Audit Logs


## When to Use

- When investigating security incidents that require analyzing kubernetes audit logs
- When building detection rules or threat hunting queries for this domain
- When SOC analysts need structured procedures for this analysis type
- When validating security monitoring coverage for related attack techniques

## Prerequisites

- Familiarity with container security concepts and tools
- Access to a test or lab environment for safe execution
- Python 3.8+ with required dependencies installed
- Appropriate authorization for any testing activities

## Instructions

Parse Kubernetes audit log files (JSON lines format) to detect security-relevant
events including unauthorized access, privilege escalation, and data exfiltration.

```python
import json

with open("/var/log/kubernetes/audit.log") as f:
    for line in f:
        event = json.loads(line)
        verb = event.get("verb")
        resource = event.get("objectRef", {}).get("resource")
        user = event.get("user", {}).get("username")
        if verb == "create" and resource == "pods/exec":
            print(f"Pod exec by {user}")
```

Key events to detect:
1. pods/exec and pods/attach (shell into containers)
2. secrets access (get/list/watch)
3. clusterrolebindings creation (RBAC escalation)
4. Privileged pod creation
5. Anonymous or system:unauthenticated access

## Examples

```python
# Detect secret enumeration
if verb in ("get", "list") and resource == "secrets":
    print(f"Secret access: {user} -> {event['objectRef'].get('name')}")
```

