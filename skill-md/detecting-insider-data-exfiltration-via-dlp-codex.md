---
name: detecting-insider-data-exfiltration-via-dlp
display_name: detecting-insider-data-exfiltration-via-dlp
platform: Codex
category: Security, forensics, and incident response
---

# detecting-insider-data-exfiltration-via-dlp - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `detecting-insider-data-exfiltration-via-dlp` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

- When investigating security incidents that require detecting insider data exfiltration via dlp

## How To Use It In Codex

In Codex, click the chat box, press /, choose detecting-insider-data-exfiltration-via-dlp, then write the task. Fallback prompt: Use the detecting-insider-data-exfiltration-via-dlp skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `detecting-insider-data-exfiltration-via-dlp` |
| Canonical name | `detecting-insider-data-exfiltration-via-dlp` |
| Platform | `Codex` |
| Category | Security, forensics, and incident response |

## Description

- When investigating security incidents that require detecting insider data exfiltration via dlp

## Original SKILL.md

---
name: detecting-insider-data-exfiltration-via-dlp
description: 'Detects insider data exfiltration by analyzing DLP policy violations,
  file access patterns, upload volume anomalies, and off-hours activity in endpoint
  and cloud logs. Uses pandas for behavioral analytics and statistical baselines.
  Use when investigating insider threats or building user behavior analytics for data
  loss prevention.

  '
domain: cybersecurity
subdomain: security-operations
tags:
- insider-threat
- data-loss-prevention
- dlp
- exfiltration-detection
- ueba
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
- T1048
- T1041
---

# Detecting Insider Data Exfiltration via DLP


## When to Use

- When investigating security incidents that require detecting insider data exfiltration via dlp
- When building detection rules or threat hunting queries for this domain
- When SOC analysts need structured procedures for this analysis type
- When validating security monitoring coverage for related attack techniques

## Prerequisites

- Familiarity with security operations concepts and tools
- Access to a test or lab environment for safe execution
- Python 3.8+ with required dependencies installed
- Appropriate authorization for any testing activities

## Instructions

Analyze endpoint activity logs, cloud storage access, and email DLP events to detect
data exfiltration patterns using behavioral baselines and statistical anomaly detection.

```python
import pandas as pd

df = pd.read_csv("file_activity.csv", parse_dates=["timestamp"])
# Baseline: average daily upload volume per user
baseline = df.groupby(["user", df["timestamp"].dt.date])["bytes_transferred"].sum()
user_avg = baseline.groupby("user").mean()

# Alert on users exceeding 3x their baseline
today = df[df["timestamp"].dt.date == pd.Timestamp.today().date()]
today_totals = today.groupby("user")["bytes_transferred"].sum()
anomalies = today_totals[today_totals > user_avg * 3]
```

Key indicators:
1. Upload volume exceeding 3x daily baseline
2. Access to files outside normal scope
3. Bulk downloads before resignation
4. Off-hours file access patterns
5. USB/external device usage spikes

## Examples

```python
# Detect off-hours activity
df["hour"] = df["timestamp"].dt.hour
off_hours = df[(df["hour"] < 6) | (df["hour"] > 22)]
suspicious = off_hours.groupby("user").size().sort_values(ascending=False)
```

