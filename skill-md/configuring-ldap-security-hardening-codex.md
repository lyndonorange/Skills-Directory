---
name: configuring-ldap-security-hardening
display_name: configuring-ldap-security-hardening
platform: Codex
category: General and specialized workflows
---

# configuring-ldap-security-hardening - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `configuring-ldap-security-hardening` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Harden LDAP directory services against common attacks including credential harvesting, LDAP injection, anonymous binding, and channel binding bypass. Covers LDAPS enforcement, channel binding, LDAP signing, access contro

## How To Use It In Codex

In Codex, click the chat box, press /, choose configuring-ldap-security-hardening, then write the task. Fallback prompt: Use the configuring-ldap-security-hardening skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `configuring-ldap-security-hardening` |
| Canonical name | `configuring-ldap-security-hardening` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Harden LDAP directory services against common attacks including credential harvesting, LDAP injection, anonymous binding, and channel binding bypass. Covers LDAPS enforcement, channel binding, LDAP signing, access contro

## Original SKILL.md

---
name: configuring-ldap-security-hardening
description: Harden LDAP directory services against common attacks including credential
  harvesting, LDAP injection, anonymous binding, and channel binding bypass. Covers
  LDAPS enforcement, channel binding, LDAP si
domain: cybersecurity
subdomain: identity-access-management
tags:
- iam
- identity
- access-control
- ldap
- directory-services
- hardening
version: '1.0'
author: mahipal
license: Apache-2.0
nist_csf:
- PR.AA-01
- PR.AA-02
- PR.AA-05
- PR.AA-06
mitre_attack:
- T1087.002
- T1110.003
- T1557.001
- T1040
- T1078.002
---
# Configuring LDAP Security Hardening

## Overview
Harden LDAP directory services against common attacks including credential harvesting, LDAP injection, anonymous binding, and channel binding bypass. Covers LDAPS enforcement, channel binding, LDAP signing, access control lists, and monitoring for LDAP-based attacks.


## When to Use

- When deploying or configuring configuring ldap security hardening capabilities in your environment
- When establishing security controls aligned to compliance requirements
- When building or improving security architecture for this domain
- When conducting security assessments that require this implementation

## Prerequisites

- Familiarity with identity access management concepts and tools
- Access to a test or lab environment for safe execution
- Python 3.8+ with required dependencies installed
- Appropriate authorization for any testing activities

## Objectives
- Implement comprehensive configuring ldap security hardening capability
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

