---
name: detecting-azure-storage-account-misconfigurations
display_name: detecting-azure-storage-account-misconfigurations
platform: Codex
category: Security, forensics, and incident response
---

# detecting-azure-storage-account-misconfigurations - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `detecting-azure-storage-account-misconfigurations` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Azure Storage accounts are a frequent target for attackers due to misconfigured public access, long-lived SAS tokens, missing encryption, and outdated TLS versions. This skill uses the azure-mgmt-storage Python SDK with 

## How To Use It In Codex

In Codex, click the chat box, press /, choose detecting-azure-storage-account-misconfigurations, then write the task. Fallback prompt: Use the detecting-azure-storage-account-misconfigurations skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `detecting-azure-storage-account-misconfigurations` |
| Canonical name | `detecting-azure-storage-account-misconfigurations` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

Azure Storage accounts are a frequent target for attackers due to misconfigured public access, long-lived SAS tokens, missing encryption, and outdated TLS versions. This skill uses the azure-mgmt-storage Python SDK with 

## Original SKILL.md

---
name: detecting-azure-storage-account-misconfigurations
description: Audit Azure Blob and ADLS storage accounts for public access exposure,
  weak or long-lived SAS tokens, missing encryption at rest, disabled HTTPS-only traffic,
  and outdated TLS versions using the azure-mgmt-storage Python SDK.
domain: cybersecurity
subdomain: cloud-security
tags:
- Azure
- storage-accounts
- blob-storage
- ADLS
- SAS-tokens
- encryption
- public-access
- cloud-misconfiguration
- azure-mgmt-storage
version: '1.0'
author: mahipal
license: Apache-2.0
nist_ai_rmf:
- MEASURE-2.7
- MAP-5.1
- MANAGE-2.4
atlas_techniques:
- AML.T0070
- AML.T0066
- AML.T0082
nist_csf:
- PR.IR-01
- ID.AM-08
- GV.SC-06
- DE.CM-01
mitre_attack:
- T1530
- T1078.004
- T1619
- T1580
---

# Detecting Azure Storage Account Misconfigurations

## Overview

Azure Storage accounts are a frequent target for attackers due to misconfigured public access, long-lived SAS tokens, missing encryption, and outdated TLS versions. This skill uses the azure-mgmt-storage Python SDK with StorageManagementClient to enumerate all storage accounts in a subscription, inspect their security properties, list blob containers for public access settings, and generate a risk-scored audit report identifying critical misconfigurations.


## When to Use

- When investigating security incidents that require detecting azure storage account misconfigurations
- When building detection rules or threat hunting queries for this domain
- When SOC analysts need structured procedures for this analysis type
- When validating security monitoring coverage for related attack techniques

## Prerequisites

- Python 3.9+ with `azure-mgmt-storage`, `azure-identity`
- Azure service principal with Reader role on target subscription
- Environment variables: AZURE_CLIENT_ID, AZURE_TENANT_ID, AZURE_CLIENT_SECRET, AZURE_SUBSCRIPTION_ID

## Key Detection Areas

1. **Public blob access** — `allow_blob_public_access` enabled on storage account or individual containers set to Blob/Container access level
2. **HTTPS enforcement** — `enable_https_traffic_only` disabled, allowing unencrypted HTTP traffic
3. **Minimum TLS version** — accounts accepting TLS 1.0 or TLS 1.1 instead of minimum TLS 1.2
4. **Encryption at rest** — storage service encryption not enabled or missing customer-managed keys
5. **Network rules** — default action set to Allow instead of Deny, exposing storage to all networks
6. **SAS token risks** — account-level SAS with overly broad permissions or excessive lifetime

## Output

JSON report with per-account findings, severity ratings (Critical/High/Medium/Low), and remediation recommendations aligned with CIS Azure Benchmark controls.

