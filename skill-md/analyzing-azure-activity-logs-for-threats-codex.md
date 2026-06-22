---
name: analyzing-azure-activity-logs-for-threats
display_name: analyzing-azure-activity-logs-for-threats
platform: Codex
category: Security, forensics, and incident response
---

# analyzing-azure-activity-logs-for-threats - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `analyzing-azure-activity-logs-for-threats` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

- When investigating security incidents that require analyzing azure activity logs for threats

## How To Use It In Codex

In Codex, click the chat box, press /, choose analyzing-azure-activity-logs-for-threats, then write the task. Fallback prompt: Use the analyzing-azure-activity-logs-for-threats skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `analyzing-azure-activity-logs-for-threats` |
| Canonical name | `analyzing-azure-activity-logs-for-threats` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

- When investigating security incidents that require analyzing azure activity logs for threats

## Original SKILL.md

---
name: analyzing-azure-activity-logs-for-threats
description: 'Queries Azure Monitor activity logs and sign-in logs via azure-monitor-query
  to detect suspicious administrative operations, impossible travel, privilege escalation,
  and resource modifications. Builds KQL queries for threat hunting in Azure environments.
  Use when investigating suspicious Azure tenant activity or building cloud SIEM detections.

  '
domain: cybersecurity
subdomain: security-operations
tags:
- azure
- cloud-security
- azure-monitor
- kql
- threat-hunting
- activity-logs
version: '1.0'
author: mahipal
license: Apache-2.0
nist_csf:
- DE.CM-01
- RS.MA-01
- GV.OV-01
- DE.AE-02
mitre_attack:
- T1078.004
- T1098.003
- T1538
- T1556.009
- T1580
---

# Analyzing Azure Activity Logs for Threats


## When to Use

- When investigating security incidents that require analyzing azure activity logs for threats
- When building detection rules or threat hunting queries for this domain
- When SOC analysts need structured procedures for this analysis type
- When validating security monitoring coverage for related attack techniques

## Prerequisites

- Familiarity with security operations concepts and tools
- Access to a test or lab environment for safe execution
- Python 3.8+ with required dependencies installed
- Appropriate authorization for any testing activities

## Instructions

Use azure-monitor-query to execute KQL queries against Azure Log Analytics workspaces,
detecting suspicious admin operations and sign-in anomalies.

```python
from azure.identity import DefaultAzureCredential
from azure.monitor.query import LogsQueryClient
from datetime import timedelta

credential = DefaultAzureCredential()
client = LogsQueryClient(credential)

response = client.query_workspace(
    workspace_id="WORKSPACE_ID",
    query="AzureActivity | where OperationNameValue has 'MICROSOFT.AUTHORIZATION/ROLEASSIGNMENTS/WRITE' | take 10",
    timespan=timedelta(hours=24),
)
```

Key detection queries:
1. Role assignment changes (privilege escalation)
2. Resource group and subscription modifications
3. Key vault secret access from new IPs
4. Network security group rule changes
5. Conditional access policy modifications

## Examples

```python
# Detect new Global Admin role assignments
query = '''
AuditLogs
| where OperationName == "Add member to role"
| where TargetResources[0].modifiedProperties[0].newValue has "Global Administrator"
'''
```

