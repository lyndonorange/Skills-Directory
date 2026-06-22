---
name: detecting-insider-threat-with-ueba
display_name: detecting-insider-threat-with-ueba
platform: Codex
category: Security, forensics, and incident response
---

# detecting-insider-threat-with-ueba - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `detecting-insider-threat-with-ueba` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

User and Entity Behavior Analytics (UEBA) moves beyond static rule-based detection to model normal behavior for users, hosts, and applications, then flag statistically significant deviations that may indicate insider thr

## How To Use It In Codex

In Codex, click the chat box, press /, choose detecting-insider-threat-with-ueba, then write the task. Fallback prompt: Use the detecting-insider-threat-with-ueba skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `detecting-insider-threat-with-ueba` |
| Canonical name | `detecting-insider-threat-with-ueba` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

User and Entity Behavior Analytics (UEBA) moves beyond static rule-based detection to model normal behavior for users, hosts, and applications, then flag statistically significant deviations that may indicate insider thr

## Original SKILL.md

---
name: detecting-insider-threat-with-ueba
description: Implement User and Entity Behavior Analytics using Elasticsearch/OpenSearch
  to build behavioral baselines, calculate anomaly scores, perform peer group analysis,
  and detect insider threat indicators such as data exfiltration, privilege abuse,
  and unauthorized access patterns.
domain: cybersecurity
subdomain: threat-detection
tags:
- ueba
- insider-threat
- anomaly-detection
- elasticsearch
- behavior-analytics
- machine-learning
- siem
version: '1.0'
author: mahipal
license: Apache-2.0
nist_csf:
- DE.CM-01
- DE.AE-02
- DE.AE-06
- ID.RA-05
mitre_attack:
- T1078
- T1190
- T1059
- T1048
- T1041
---

# Detecting Insider Threat with UEBA

## Overview

User and Entity Behavior Analytics (UEBA) moves beyond static rule-based detection to model normal behavior for users, hosts, and applications, then flag statistically significant deviations that may indicate insider threats. Using Elasticsearch as the analytics backend, this skill covers building behavioral baselines from authentication logs, file access events, and network activity, computing risk scores using statistical deviation and peer group comparison, and correlating multiple low-confidence indicators into high-confidence insider threat alerts.


## When to Use

- When investigating security incidents that require detecting insider threat with ueba
- When building detection rules or threat hunting queries for this domain
- When SOC analysts need structured procedures for this analysis type
- When validating security monitoring coverage for related attack techniques

## Prerequisites

- Elasticsearch 8.x or OpenSearch 2.x cluster with security audit data
- Log sources: Active Directory authentication, VPN, DLP, file server access, email
- Python 3.9+ with elasticsearch client library
- Baseline period of 30+ days of normal user activity data
- Defined peer groups based on department, role, or job function

## Steps

### Step 1: Ingest and Normalize Activity Logs
Configure log pipelines to ingest authentication, file access, email, and network logs into Elasticsearch with a unified user identity field.

### Step 2: Build Behavioral Baselines
Calculate per-user baselines for login times, data volume, application usage, and access patterns over a rolling 30-day window using Elasticsearch aggregations.

### Step 3: Calculate Anomaly Scores
Compare current activity against baselines using z-score deviation and peer group comparison to generate per-user risk scores.

### Step 4: Correlate and Alert
Combine multiple anomalous indicators (unusual hours + large downloads + new system access) into composite risk scores that trigger SOC investigation workflows.

## Expected Output

JSON report containing per-user risk scores, anomalous activity details, peer group deviations, and recommended investigation actions.

