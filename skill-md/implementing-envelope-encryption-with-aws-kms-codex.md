---
name: implementing-envelope-encryption-with-aws-kms
display_name: implementing-envelope-encryption-with-aws-kms
platform: Codex
category: General and specialized workflows
---

# implementing-envelope-encryption-with-aws-kms - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `implementing-envelope-encryption-with-aws-kms` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Envelope encryption is a strategy where data is encrypted with a data encryption key (DEK), and the DEK itself is encrypted with a master key (KEK) managed by AWS KMS. This approach allows encrypting large volumes of dat

## How To Use It In Codex

In Codex, click the chat box, press /, choose implementing-envelope-encryption-with-aws-kms, then write the task. Fallback prompt: Use the implementing-envelope-encryption-with-aws-kms skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `implementing-envelope-encryption-with-aws-kms` |
| Canonical name | `implementing-envelope-encryption-with-aws-kms` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Envelope encryption is a strategy where data is encrypted with a data encryption key (DEK), and the DEK itself is encrypted with a master key (KEK) managed by AWS KMS. This approach allows encrypting large volumes of dat

## Original SKILL.md

---
name: implementing-envelope-encryption-with-aws-kms
description: Envelope encryption is a strategy where data is encrypted with a data
  encryption key (DEK), and the DEK itself is encrypted with a master key (KEK) managed
  by AWS KMS. This approach allows encrypting
domain: cybersecurity
subdomain: cryptography
tags:
- cryptography
- encryption
- aws
- kms
- envelope-encryption
- key-management
version: '1.0'
author: mahipal
license: Apache-2.0
nist_csf:
- PR.DS-01
- PR.DS-02
- PR.DS-10
mitre_attack:
- T1600
- T1573
- T1553
- T1078.004
- T1530
---
# Implementing Envelope Encryption with AWS KMS

## Overview

Envelope encryption is a strategy where data is encrypted with a data encryption key (DEK), and the DEK itself is encrypted with a master key (KEK) managed by AWS KMS. This approach allows encrypting large volumes of data locally while keeping the master key secure in a hardware security module (HSM) managed by AWS. This skill covers implementing envelope encryption using AWS KMS GenerateDataKey API.


## When to Use

- When deploying or configuring implementing envelope encryption with aws kms capabilities in your environment
- When establishing security controls aligned to compliance requirements
- When building or improving security architecture for this domain
- When conducting security assessments that require this implementation

## Prerequisites

- Familiarity with cryptography concepts and tools
- Access to a test or lab environment for safe execution
- Python 3.8+ with required dependencies installed
- Appropriate authorization for any testing activities

## Objectives

- Understand the envelope encryption pattern and its advantages
- Generate data encryption keys using AWS KMS GenerateDataKey
- Encrypt/decrypt data locally using DEKs
- Store encrypted DEK alongside ciphertext
- Implement key caching to reduce KMS API calls
- Handle key rotation with automatic re-encryption
- Implement multi-region encryption for disaster recovery

## Key Concepts

### Envelope Encryption Flow

1. Call `kms:GenerateDataKey` to get plaintext DEK + encrypted DEK
2. Use plaintext DEK to encrypt data locally (AES-256-GCM)
3. Store encrypted DEK alongside ciphertext
4. Discard plaintext DEK from memory
5. For decryption: call `kms:Decrypt` on encrypted DEK, then decrypt data

### Advantages Over Direct KMS Encryption

| Aspect | Direct KMS | Envelope Encryption |
|--------|-----------|-------------------|
| Max data size | 4 KB | Unlimited |
| Latency | Network round-trip per operation | Local encryption |
| Cost | $0.03/10,000 requests | Fewer KMS requests |
| Offline | Not possible | Yes (with cached DEKs) |

### KMS Key Types

- **AWS Managed**: AWS creates and manages (`aws/s3`, `aws/ebs`)
- **Customer Managed**: You create and manage policies
- **Custom Key Store**: Backed by CloudHSM cluster

## Security Considerations

- Never store plaintext DEK; only keep encrypted DEK
- Use key policies to restrict who can call GenerateDataKey and Decrypt
- Enable AWS CloudTrail logging for all KMS API calls
- Implement key rotation (automatic annual rotation for CMKs)
- Use encryption context for authenticated encryption metadata
- Handle KMS throttling with exponential backoff

## Validation Criteria

- [ ] GenerateDataKey returns plaintext and encrypted DEK
- [ ] Data encrypts correctly with plaintext DEK using AES-256-GCM
- [ ] Encrypted DEK can be decrypted via KMS Decrypt API
- [ ] Decrypted DEK recovers the original data
- [ ] Plaintext DEK is wiped from memory after use
- [ ] Encryption context is validated during decryption
- [ ] Key rotation re-encrypts DEKs with new master key

