---
name: performing-privileged-account-discovery
display_name: performing-privileged-account-discovery
platform: Codex
category: Security, forensics, and incident response
---

# performing-privileged-account-discovery - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `performing-privileged-account-discovery` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Discover and inventory all privileged accounts across enterprise infrastructure including domain admins, local admins, service accounts, database admins, cloud IAM roles, and application admin accounts. Covers automated 

## How To Use It In Codex

In Codex, click the chat box, press /, choose performing-privileged-account-discovery, then write the task. Fallback prompt: Use the performing-privileged-account-discovery skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `performing-privileged-account-discovery` |
| Canonical name | `performing-privileged-account-discovery` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

Discover and inventory all privileged accounts across enterprise infrastructure including domain admins, local admins, service accounts, database admins, cloud IAM roles, and application admin accounts. Covers automated 

## Original SKILL.md

---
name: performing-privileged-account-discovery
description: Discover and inventory all privileged accounts across enterprise infrastructure
  including domain admins, local admins, service accounts, database admins, cloud
  IAM roles, and application admin account
domain: cybersecurity
subdomain: identity-access-management
tags:
- iam
- identity
- access-control
- privileged-access
- discovery
- inventory
version: '1.0'
author: mahipal
license: Apache-2.0
nist_csf:
- PR.AA-01
- PR.AA-02
- PR.AA-05
- PR.AA-06
mitre_attack:
- T1078
- T1110
- T1556
- T1098
- T1078.004
---
# Performing Privileged Account Discovery

## Overview
Discover and inventory all privileged accounts across enterprise infrastructure including domain admins, local admins, service accounts, database admins, cloud IAM roles, and application admin accounts. Covers automated scanning, risk classification, and onboarding to PAM.


## When to Use

- When conducting security assessments that involve performing privileged account discovery
- When following incident response procedures for related security events
- When performing scheduled security testing or auditing activities
- When validating security controls through hands-on testing

## Prerequisites

- Familiarity with identity access management concepts and tools
- Access to a test or lab environment for safe execution
- Python 3.8+ with required dependencies installed
- Appropriate authorization for any testing activities

## Objectives
- Implement comprehensive performing privileged account discovery capability
- Establish automated discovery and monitoring processes
- Integrate with enterprise IAM and security tools
- Generate compliance-ready documentation and reports
- Align with NIST 800-53 access control requirements

## Security Controls
| Control | NIST 800-53 | Description |
|---------|-------------|-------------|
| Account Management | AC-2 | Lifecycle management |
| Access Enforcement | AC-3 | Policy-based access control |
| Least Privilege | AC-6 | Minimum necessary permissions |
| Audit Logging | AU-3 | Authentication and access events |
| Identification | IA-2 | User and service identification |

## Verification
- [ ] Implementation tested in non-production environment
- [ ] Security policies configured and enforced
- [ ] Audit logging enabled and forwarding to SIEM
- [ ] Documentation and runbooks complete
- [ ] Compliance evidence generated

