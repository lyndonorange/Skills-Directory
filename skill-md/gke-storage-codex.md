---
name: gke-storage
display_name: gke-storage
platform: Codex
category: General and specialized workflows
---

# gke-storage - Codex Skill Package

## What This Is

This is a friend-safe Markdown copy of `gke-storage` for Codex. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Manages GKE storage, including PVCs, PersistentVolumes, Filestore, and GCS FUSE. Use when configuring GKE storage, creating PVCs, or setting up GCS FUSE on GKE. Don't use for database administration or replication strate

## How To Use It In Codex

In Codex, click the chat box, press /, choose gke-storage, then write the task. Fallback prompt: Use the gke-storage skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `gke-storage` |
| Canonical name | `gke-storage` |
| Platform | `Codex` |
| Category | General and specialized workflows |

## Description

Manages GKE storage, including PVCs, PersistentVolumes, Filestore, and GCS FUSE. Use when configuring GKE storage, creating PVCs, or setting up GCS FUSE on GKE. Don't use for database administration or replication strate

## Upstream provenance

This adapted package derives from [Google Agent Skills](https://github.com/google/skills/tree/092e210b243601797a0fb939040be2b1288e6d39) at commit `092e210b243601797a0fb939040be2b1288e6d39`, licensed under `Apache-2.0`.


## Original SKILL.md

---
name: gke-storage
description: "Manages GKE storage, including PVCs, PersistentVolumes, Filestore, and GCS FUSE. Use when configuring GKE storage, creating PVCs, or setting up GCS FUSE on GKE. Don't use for database administration or replication strategies outside volume provisioning context."
license: Apache-2.0
---

## Universal runtime boundary

- Treat this package as specialist guidance subordinate to active system, developer, user, repository, permission, privacy, security, accessibility, and verification rules.
- Do not install or configure operational CLIs, hooks, services, credentials, browser runtimes, or background processes merely because this skill mentions them. Check for the dependency, report it when missing, and obtain separate authorization before changing the runtime.
- Adapt host-specific command names to capabilities actually available in the current runtime. Report unsupported integrations instead of claiming they ran.
- Read `references/upstream.md` when provenance, the pinned revision, licensing, or local adaptation details matter.

# GKE Storage

This reference covers storage configuration for GKE clusters including
persistent disks, file storage, and cloud storage integration.

> **MCP Tools:** `apply_k8s_manifest`, `get_k8s_resource`,
> `describe_k8s_resource`, `get_cluster`

## Golden Path Storage Defaults

The golden path Autopilot config enables these CSI drivers:

| Driver          | Golden Path       | Access Mode     | Use Case             |
| --------------- | ----------------- | --------------- | -------------------- |
| Compute Engine  | Enabled (default) | ReadWriteOnce   | Block storage for    |
: Persistent Disk :                   :                 : databases,           :
: CSI             :                   :                 : single-pod workloads :
| Google Cloud    | Enabled           | ReadWriteMany   | Shared NFS for       |
: Filestore CSI   :                   :                 : multi-pod access     :
| Cloud Storage   | Enabled           | ReadWriteMany / | Mount GCS buckets as |
: FUSE CSI        :                   : ReadOnlyMany    : volumes              :
| Parallelstore   | Enabled           | ReadWriteMany   | High-performance     |
: CSI             :                   :                 : parallel file system :
| Boot disk type  | `pd-balanced`     | N/A             | Node boot disks      |

## StorageClasses

### Default StorageClasses

GKE provides built-in StorageClasses:

StorageClass   | Disk Type             | Use Case
-------------- | --------------------- | ------------------------------
`standard-rwo` | `pd-standard`         | Cost-effective, low IOPS
`premium-rwo`  | `pd-ssd`              | High IOPS, databases
`standard-rwx` | Filestore (Basic HDD) | Shared NFS
`premium-rwx`  | Filestore (Basic SSD) | Shared NFS, higher performance

### Custom StorageClass

```yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: fast-regional
provisioner: pd.csi.storage.gke.io
parameters:
  type: pd-ssd
  replication-type: regional-pd    # Replicate across 2 zones
volumeBindingMode: WaitForFirstConsumer
allowVolumeExpansion: true         # Always enable for production
```

## PersistentVolumeClaims

### Block Storage (ReadWriteOnce)

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: database-pvc
spec:
  accessModes:
  - ReadWriteOnce
  storageClassName: premium-rwo
  resources:
    requests:
      storage: 100Gi
```

### Shared File Storage (ReadWriteMany via Filestore)

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: shared-data
spec:
  accessModes:
  - ReadWriteMany
  storageClassName: standard-rwx
  resources:
    requests:
      storage: 1Ti    # Filestore minimum is 1 TiB for Basic tier
```

### GCS Bucket Mount (Cloud Storage FUSE)

Mount a GCS bucket as a volume without a PVC:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: gcs-reader
  annotations:
    gke-gcsfuse/volumes: "true"
spec:
  containers:
  - name: reader
    image: busybox
    command: ["ls", "/data"]
    volumeMounts:
    - name: gcs-bucket
      mountPath: /data
  volumes:
  - name: gcs-bucket
    csi:
      driver: gcsfuse.csi.storage.gke.io
      readOnly: true
      volumeAttributes:
        bucketName: <BUCKET_NAME>
```

> Requires Workload Identity for the pod's service account to have
> `storage.objectViewer` on the bucket.

## Volume Expansion

If `allowVolumeExpansion: true` is set on the StorageClass, resize by updating
the PVC:

```bash
# kubectl
kubectl patch pvc <PVC_NAME> -p '{"spec":{"resources":{"requests":{"storage":"200Gi"}}}}'
```

```
# MCP (preferred)
patch_k8s_resource(parent="...", resourceType="persistentvolumeclaim", name="<PVC_NAME>",
  patch='{"spec":{"resources":{"requests":{"storage":"200Gi"}}}}')
```

Kubernetes automatically resizes the filesystem.

## Best Practices

1.  **Always enable volume expansion**: Set `allowVolumeExpansion: true` on all
    StorageClasses
2.  **Use regional PDs for production**: `replication-type: regional-pd`
    replicates across 2 zones for HA
3.  **Use `WaitForFirstConsumer`**: Ensures the PV is provisioned in the same
    zone as the pod
4.  **Choose the right disk type**: `pd-ssd` for databases, `pd-balanced`
    (golden path default) for general use, `pd-standard` for cold storage
5.  **Use Filestore for shared access**: When multiple pods need to read/write
    the same files
6.  **Use GCS FUSE for data pipelines**: Mount buckets directly for ML training
    data, logs, etc.
7.  **Back up PVCs**: Use Backup for GKE (see the `gke-backup-dr` skill) to
    protect persistent data
