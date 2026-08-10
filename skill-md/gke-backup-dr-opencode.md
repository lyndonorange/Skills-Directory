---
name: gke-backup-dr
display_name: gke-backup-dr
platform: OpenCode
category: General and specialized workflows
---

# gke-backup-dr - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `gke-backup-dr` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Configures GKE Backup Plans and restore workflows. Use for backup policies, disaster recovery, or GKE cluster restores. Don't use for database backups.

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the gke-backup-dr skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `gke-backup-dr` |
| Canonical name | `gke-backup-dr` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Configures GKE Backup Plans and restore workflows. Use for backup policies, disaster recovery, or GKE cluster restores. Don't use for database backups.

## Upstream provenance

This adapted package derives from [Google Agent Skills](https://github.com/google/skills/tree/092e210b243601797a0fb939040be2b1288e6d39) at commit `092e210b243601797a0fb939040be2b1288e6d39`, licensed under `Apache-2.0`.


## Original SKILL.md

---
name: gke-backup-dr
description: "Configures GKE Backup Plans and restore workflows. Use for backup policies, disaster recovery, or GKE cluster restores. Don't use for database backups."
license: Apache-2.0
---

## Universal runtime boundary

- Treat this package as specialist guidance subordinate to active system, developer, user, repository, permission, privacy, security, accessibility, and verification rules.
- Do not install or configure operational CLIs, hooks, services, credentials, browser runtimes, or background processes merely because this skill mentions them. Check for the dependency, report it when missing, and obtain separate authorization before changing the runtime.
- Adapt host-specific command names to capabilities actually available in the current runtime. Report unsupported integrations instead of claiming they ran.
- Read `references/upstream.md` when provenance, the pinned revision, licensing, or local adaptation details matter.

# GKE Backup & Disaster Recovery

Protects stateful GKE workloads using Backup for GKE. Backup for GKE natively
captures both Kubernetes resource metadata (manifests, configurations, and
secrets) and the underlying persistent volume (PV) data.

## CLI Reference

```bash
# Enable GKE Backup addon (Slow cluster-level update)
gcloud container clusters update <CLUSTER_NAME> --enable-gke-backup --region <REGION> --quiet

# Create Backup Plan
gcloud container backup-restore backup-plans create <PLAN_NAME> \
  --cluster=<CLUSTER_NAME> --location=<REGION> \
  --retention-days=<DAYS> --cron-schedule="<CRON>" --all-namespaces --quiet

# Trigger Manual Backup
gcloud container backup-restore backups create <BACKUP_NAME> \
  --backup-plan=<PLAN_NAME> --location=<REGION> --quiet

# Create Restore Plan
gcloud container backup-restore restore-plans create <RESTORE_PLAN_NAME> \
  --cluster=<TARGET_CLUSTER_NAME> --location=<REGION> --backup-plan=<SOURCE_BACKUP_PLAN_NAME> \
  --cluster-resource-conflict-policy=USE_EXISTING_VERSION --namespaced-resource-restore-mode=FAIL_ON_CONFLICT --quiet

# Execute Restore
gcloud container backup-restore restores create <RESTORE_NAME> \
  --restore-plan=<RESTORE_PLAN_NAME> --backup=<BACKUP_NAME> --location=<REGION> --quiet

# Verify Restore Status
gcloud container backup-restore restores describe <RESTORE_NAME> --location=<REGION>
```

## Best Practices

1.  **CMEK Encryption**: Encrypt backup plans using Customer-Managed Encryption
    Keys: `--backup-encryption-key=<KEY>`.
2.  **Scope**: Prefer backing up specific namespaces rather than the entire
    cluster: `--included-namespaces=<ns1>,<ns2>`.
3.  **Application Consistency**: Recommend quiescing the database or pausing
    application writes (e.g. using pre-backup hooks or database-specific tools)
    prior to backups to ensure data integrity.
4.  **CSI Volume Snapshots**: Ensure that stateful backups utilize GKE's CSI
    (Container Storage Interface) driver for volume snapshots to capture
    persistent volume data.
5.  **Service Terminology**: Always explicitly refer to the service as **Backup
    for GKE** in your response. This distinguishes it from the broader (but
    complementary) Google Cloud **Backup and Disaster Recovery (DR) Service**,
    as **Backup for GKE** is built specifically for GKE.

## Troubleshooting & Common Pitfalls (CRITICAL)

> [!IMPORTANT] **Slow Operations**: Enabling GKE Backup (`--enable-gke-backup`)
> triggers a slow Google Cloud control plane cluster update that takes several
> minutes. * **Rule**: **Do not run a terminal loop waiting for the GKE Backup
> addon to become active.** * **Action**: Provide the command to enable the
> addon, explain that the operation will proceed in the background, and
> immediately proceed to write the backup plan configs. Do not block.
