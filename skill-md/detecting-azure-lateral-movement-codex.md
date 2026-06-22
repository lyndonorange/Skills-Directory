---
name: detecting-azure-lateral-movement
display_name: detecting-azure-lateral-movement
platform: Codex
category: Security, forensics, and incident response
---

# detecting-azure-lateral-movement - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `detecting-azure-lateral-movement` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Lateral movement in Azure AD/Entra ID differs from on-premises environments. Attackers pivot through OAuth application consent grants, service principal abuse, cross-tenant access policies, and stolen refresh tokens rath

## How To Use It In Codex

In Codex, click the chat box, press /, choose detecting-azure-lateral-movement, then write the task. Fallback prompt: Use the detecting-azure-lateral-movement skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `detecting-azure-lateral-movement` |
| Canonical name | `detecting-azure-lateral-movement` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

Lateral movement in Azure AD/Entra ID differs from on-premises environments. Attackers pivot through OAuth application consent grants, service principal abuse, cross-tenant access policies, and stolen refresh tokens rath

## Original SKILL.md

---
name: detecting-azure-lateral-movement
description: Detect lateral movement in Azure AD/Entra ID environments using Microsoft
  Graph API audit logs, Azure Sentinel KQL hunting queries, and sign-in anomaly correlation
  to identify privilege escalation, token theft, and cross-tenant pivoting.
domain: cybersecurity
subdomain: cloud-security
tags:
- azure
- entra-id
- lateral-movement
- sentinel
- kql
- graph-api
- cloud-security
- threat-hunting
version: '1.0'
author: mahipal
license: Apache-2.0
nist_csf:
- PR.IR-01
- ID.AM-08
- GV.SC-06
- DE.CM-01
mitre_attack:
- T1078.004
- T1550.001
- T1021.007
- T1098.003
- T1528
---

# Detecting Azure Lateral Movement

## Overview

Lateral movement in Azure AD/Entra ID differs from on-premises environments. Attackers pivot through OAuth application consent grants, service principal abuse, cross-tenant access policies, and stolen refresh tokens rather than SMB/RDP connections. Detection requires correlating Microsoft Graph API audit logs, Azure AD sign-in logs, and Entra ID protection risk events using KQL queries in Microsoft Sentinel. This skill covers building detection analytics for common Azure lateral movement techniques including application impersonation, mailbox delegation abuse, and conditional access policy bypasses.


## When to Use

- When investigating security incidents that require detecting azure lateral movement
- When building detection rules or threat hunting queries for this domain
- When SOC analysts need structured procedures for this analysis type
- When validating security monitoring coverage for related attack techniques

## Prerequisites

- Azure subscription with Microsoft Sentinel workspace configured
- Azure AD P2 or Entra ID P2 license for risk-based sign-in detection
- Microsoft Graph API permissions: AuditLog.Read.All, Directory.Read.All, SecurityEvents.Read.All
- Log Analytics workspace ingesting AuditLogs, SigninLogs, and AADServicePrincipalSignInLogs
- Familiarity with KQL (Kusto Query Language)

## Steps

### Step 1: Configure Log Ingestion

Enable diagnostic settings to stream Azure AD logs to Log Analytics:
- Sign-in logs (interactive and non-interactive)
- Audit logs (directory changes, app consent)
- Service principal sign-in logs
- Provisioning logs
- Risky users and risk detections

### Step 2: Build Detection Queries

Create KQL analytics rules in Sentinel for:
- Unusual service principal credential additions
- OAuth application consent grants to unknown apps
- Cross-tenant sign-ins from new tenants
- Token replay from different IP/user-agent combinations
- Mailbox delegation changes (FullAccess, SendAs)

### Step 3: Correlate Events

Chain multiple low-confidence indicators into high-confidence lateral movement detections by correlating sign-in anomalies with directory changes within time windows.

### Step 4: Automate Response

Create Sentinel playbooks (Logic Apps) to automatically revoke suspicious OAuth grants, disable compromised service principals, and enforce step-up authentication.

## Expected Output

JSON report containing detected lateral movement indicators, correlated event chains, affected identities, and recommended containment actions with MITRE ATT&CK technique mappings.

