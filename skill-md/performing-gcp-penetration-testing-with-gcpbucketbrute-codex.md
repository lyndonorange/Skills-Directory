---
name: performing-gcp-penetration-testing-with-gcpbucketbrute
display_name: performing-gcp-penetration-testing-with-gcpbucketbrute
platform: Codex
category: Security, forensics, and incident response
---

# performing-gcp-penetration-testing-with-gcpbucketbrute - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `performing-gcp-penetration-testing-with-gcpbucketbrute` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

This skill covers Google Cloud Platform security testing using GCPBucketBrute for storage bucket enumeration and access permission testing, combined with gcloud CLI IAM enumeration to identify privilege escalation paths.

## How To Use It In Codex

In Codex, click the chat box, press /, choose performing-gcp-penetration-testing-with-gcpbucketbrute, then write the task. Fallback prompt: Use the performing-gcp-penetration-testing-with-gcpbucketbrute skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `performing-gcp-penetration-testing-with-gcpbucketbrute` |
| Canonical name | `performing-gcp-penetration-testing-with-gcpbucketbrute` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

This skill covers Google Cloud Platform security testing using GCPBucketBrute for storage bucket enumeration and access permission testing, combined with gcloud CLI IAM enumeration to identify privilege escalation paths.

## Original SKILL.md

---
name: performing-gcp-penetration-testing-with-gcpbucketbrute
description: Perform GCP security testing using GCPBucketBrute for storage bucket
  enumeration, gcloud IAM privilege escalation path analysis, and service account
  permission auditing
domain: cybersecurity
subdomain: cloud-security
tags:
- gcp
- cloud-pentesting
- bucket-enumeration
- iam-audit
- privilege-escalation
- gcpbucketbrute
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
- T1078.004
- T1530
- T1537
- T1580
- T1068
---

# Performing GCP Penetration Testing with GCPBucketBrute

## Overview

This skill covers Google Cloud Platform security testing using GCPBucketBrute for storage bucket enumeration and access permission testing, combined with gcloud CLI IAM enumeration to identify privilege escalation paths. The approach tests for publicly accessible buckets, overly permissive IAM bindings, and service account key exposure.


## When to Use

- When conducting security assessments that involve performing gcp penetration testing with gcpbucketbrute
- When following incident response procedures for related security events
- When performing scheduled security testing or auditing activities
- When validating security controls through hands-on testing

## Prerequisites

- Python 3.8+ with google-cloud-storage library
- GCPBucketBrute installed from RhinoSecurityLabs GitHub
- gcloud CLI authenticated with test credentials
- Authorized penetration testing scope for target GCP project
- google-api-python-client and google-auth libraries

## Steps

1. **Enumerate Storage Buckets** — Use GCPBucketBrute with keyword permutations to discover accessible GCP storage buckets
2. **Test Bucket Permissions** — Call TestIamPermissions API on each discovered bucket to determine read/write/admin access levels
3. **Audit IAM Bindings** — Enumerate project-level IAM policies to identify overly permissive role bindings
4. **Check Service Account Keys** — Identify service accounts with user-managed keys and test for privilege escalation via impersonation
5. **Test Privilege Escalation Paths** — Check for iam.serviceAccounts.actAs, setIamPolicy, and other privilege escalation vectors
6. **Generate Findings Report** — Produce a structured security assessment with risk severity ratings

## Expected Output

- JSON report of discovered buckets with permission levels
- IAM privilege escalation path analysis
- Service account security assessment
- Risk-scored findings with remediation recommendations

