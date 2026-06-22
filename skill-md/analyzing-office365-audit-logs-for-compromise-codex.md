---
name: analyzing-office365-audit-logs-for-compromise
display_name: analyzing-office365-audit-logs-for-compromise
platform: Codex
category: Security, forensics, and incident response
---

# analyzing-office365-audit-logs-for-compromise - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `analyzing-office365-audit-logs-for-compromise` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Business Email Compromise (BEC) attacks often leave traces in Office 365 audit logs: suspicious inbox rule creation, email forwarding to external addresses, mailbox delegation changes, and unauthorized OAuth application 

## How To Use It In Codex

In Codex, click the chat box, press /, choose analyzing-office365-audit-logs-for-compromise, then write the task. Fallback prompt: Use the analyzing-office365-audit-logs-for-compromise skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `analyzing-office365-audit-logs-for-compromise` |
| Canonical name | `analyzing-office365-audit-logs-for-compromise` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

Business Email Compromise (BEC) attacks often leave traces in Office 365 audit logs: suspicious inbox rule creation, email forwarding to external addresses, mailbox delegation changes, and unauthorized OAuth application 

## Original SKILL.md

---
name: analyzing-office365-audit-logs-for-compromise
description: Parse Office 365 Unified Audit Logs via Microsoft Graph API to detect
  email forwarding rule creation, inbox delegation, suspicious OAuth app grants, and
  other indicators of account compromise.
domain: cybersecurity
subdomain: cloud-security
tags:
- Office365
- Microsoft-Graph
- audit-logs
- email-compromise
- inbox-rules
- OAuth
- BEC
version: '1.0'
author: mahipal
license: Apache-2.0
nist_csf:
- PR.IR-01
- ID.AM-08
- GV.SC-06
- DE.CM-01
mitre_attack:
- T1114.002
- T1098.002
- T1556.006
- T1078.004
---

# Analyzing Office 365 Audit Logs for Compromise

## Overview

Business Email Compromise (BEC) attacks often leave traces in Office 365 audit logs: suspicious inbox rule creation, email forwarding to external addresses, mailbox delegation changes, and unauthorized OAuth application consent grants. This skill uses the Microsoft Graph API to query the Unified Audit Log, enumerate inbox rules across mailboxes, detect forwarding configurations, and identify compromised account indicators.


## When to Use

- When investigating security incidents that require analyzing office365 audit logs for compromise
- When building detection rules or threat hunting queries for this domain
- When SOC analysts need structured procedures for this analysis type
- When validating security monitoring coverage for related attack techniques

## Prerequisites

- Azure AD app registration with `AuditLog.Read.All`, `MailboxSettings.Read`, `Mail.Read` (application permissions)
- Python 3.9+ with `msal`, `requests`
- Client secret or certificate for authentication
- Global Reader or Security Reader role

## Steps

1. Authenticate to Microsoft Graph using MSAL client credentials flow
2. Query Unified Audit Log for suspicious operations (Set-Mailbox, New-InboxRule)
3. Enumerate inbox rules across mailboxes and flag forwarding rules
4. Detect mailbox delegation changes (Add-MailboxPermission)
5. Identify OAuth consent grants to suspicious applications
6. Check for suspicious sign-in patterns from audit logs
7. Generate compromise indicator report with timeline

## Expected Output

- JSON report listing forwarding rules, delegation changes, OAuth grants, and suspicious audit events with risk scores
- Timeline of compromise indicators with affected mailboxes

