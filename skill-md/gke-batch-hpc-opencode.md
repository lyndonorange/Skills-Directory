---
name: gke-batch-hpc
display_name: gke-batch-hpc
platform: OpenCode
category: General and specialized workflows
---

# gke-batch-hpc - OpenCode Skill Package

## What This Is

This is a friend-safe Markdown copy of `gke-batch-hpc` for OpenCode. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Runs batch and HPC workloads on GKE, utilizing job queues and parallel processing. Use when running GKE batch jobs, configuring GKE HPC, or setting up GKE job queues. Don't use for standard web application deployments (u

## How To Use It In OpenCode

In OpenCode, open the project and type: Use the gke-batch-hpc skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `gke-batch-hpc` |
| Canonical name | `gke-batch-hpc` |
| Platform | `OpenCode` |
| Category | General and specialized workflows |

## Description

Runs batch and HPC workloads on GKE, utilizing job queues and parallel processing. Use when running GKE batch jobs, configuring GKE HPC, or setting up GKE job queues. Don't use for standard web application deployments (u

## Upstream provenance

This adapted package derives from [Google Agent Skills](https://github.com/google/skills/tree/092e210b243601797a0fb939040be2b1288e6d39) at commit `092e210b243601797a0fb939040be2b1288e6d39`, licensed under `Apache-2.0`.


## Original SKILL.md

---
name: gke-batch-hpc
description: "Runs batch and HPC workloads on GKE, utilizing job queues and parallel processing. Use when running GKE batch jobs, configuring GKE HPC, or setting up GKE job queues. Don't use for standard web application deployments (use gke-app-onboarding instead)."
license: Apache-2.0
---

## Universal runtime boundary

- Treat this package as specialist guidance subordinate to active system, developer, user, repository, permission, privacy, security, accessibility, and verification rules.
- Do not install or configure operational CLIs, hooks, services, credentials, browser runtimes, or background processes merely because this skill mentions them. Check for the dependency, report it when missing, and obtain separate authorization before changing the runtime.
- Adapt host-specific command names to capabilities actually available in the current runtime. Report unsupported integrations instead of claiming they ran.
- Read `references/upstream.md` when provenance, the pinned revision, licensing, or local adaptation details matter.

# GKE Batch & HPC Workloads

This reference covers running batch processing and high-performance computing
(HPC) workloads on GKE.

> **MCP Tools:** `apply_k8s_manifest`, `get_k8s_resource`,
> `describe_k8s_resource`, `get_k8s_logs`, `delete_k8s_resource`,
> `list_k8s_events`

## When to Use

-   Running batch data processing pipelines
-   HPC simulations (CFD, molecular dynamics, financial modeling)
-   Large-scale parallel computation (MPI, MapReduce)
-   ML training jobs
-   CI/CD build farms

## Batch Processing on GKE

### Kubernetes Jobs

```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: batch-job
spec:
  parallelism: 10
  completions: 100
  backoffLimit: 3
  template:
    spec:
      containers:
      - name: worker
        image: <IMAGE>
        resources:
          requests:
            cpu: "1"
            memory: "2Gi"
      restartPolicy: Never
```

### JobSet (for Complex Multi-Job Workflows)

The golden path enables JobSet monitoring (`JOBSET` in monitoringConfig).

```yaml
apiVersion: jobset.x-k8s.io/v1alpha2
kind: JobSet
metadata:
  name: training-job
spec:
  replicatedJobs:
  - name: workers
    replicas: 4
    template:
      spec:
        parallelism: 1
        completions: 1
        template:
          spec:
            containers:
            - name: worker
              image: <IMAGE>
              resources:
                requests:
                  cpu: "4"
                  memory: "8Gi"
```

### Kueue (Job Queuing)

Kueue manages job scheduling and resource allocation for batch workloads:

```bash
# Install Kueue
kubectl apply --server-side -f https://github.com/kubernetes-sigs/kueue/releases/latest/download/manifests.yaml
```

```yaml
# Define a ClusterQueue
apiVersion: kueue.x-k8s.io/v1beta1
kind: ClusterQueue
metadata:
  name: batch-queue
spec:
  namespaceSelector: {}
  resourceGroups:
  - coveredResources: ["cpu", "memory"]
    flavors:
    - name: default
      resources:
      - name: "cpu"
        nominalQuota: 100
      - name: "memory"
        nominalQuota: "200Gi"
---
# Allow a namespace to use the queue
apiVersion: kueue.x-k8s.io/v1beta1
kind: LocalQueue
metadata:
  name: batch-local
  namespace: batch-jobs
spec:
  clusterQueue: batch-queue
```

## HPC on GKE

### Compact Placement (Low-Latency Networking)

For tightly-coupled HPC workloads that need low-latency inter-node
communication:

```bash
# Standard clusters: create node pool with compact placement
gcloud container node-pools create hpc-pool \
  --cluster <CLUSTER_NAME> --region <REGION> \
  --machine-type c3-standard-44 \
  --placement-type COMPACT \
  --num-nodes 8 \
  --enable-autoscaling --min-nodes 0 --max-nodes 16 \
  --quiet
```

### MPI Workloads

Use the MPI Operator for MPI-based HPC applications:

```bash
# Install MPI Operator
kubectl apply -f https://raw.githubusercontent.com/kubeflow/mpi-operator/master/deploy/v2beta1/mpi-operator.yaml
```

```yaml
apiVersion: kubeflow.org/v2beta1
kind: MPIJob
metadata:
  name: hpc-simulation
spec:
  slotsPerWorker: 4
  mpiReplicaSpecs:
    Launcher:
      replicas: 1
      template:
        spec:
          containers:
          - name: launcher
            image: <MPI_IMAGE>
            command: ["mpirun", "-np", "32", "./simulation"]
            resources:
              requests:
                cpu: "1"
                memory: "2Gi"
              limits:
                cpu: "2"
                memory: "4Gi"
    Worker:
      replicas: 8
      template:
        spec:
          containers:
          - name: worker
            image: <MPI_IMAGE>
            resources:
              requests:
                cpu: "4"
                memory: "8Gi"
              limits:
                cpu: "8"
                memory: "16Gi"
```

## Cost Optimization for Batch/HPC

### Spot VMs for Batch

Batch workloads are ideal Spot VM candidates (interruptible, can checkpoint).
Use a ComputeClass with Spot-first priority and `activeMigration` to return to
Spot when available. See the `gke-compute-classes` skill for the
Spot-with-fallback pattern.

### Scale-to-Zero

For batch clusters, allow node pools to scale to zero when no jobs are running:

-   Autopilot (golden path): Automatic, nodes scale to zero when no pods are
    scheduled
-   Standard: Set `--min-nodes 0` on batch node pools

## Best Practices & Production Guidelines

-   **Resource Quotas**: Always specify resource requests and limits (CPU,
    memory, and optionally GPU/TPU) for all batch/HPC manifests. This is
    critical for Kueue admission, autoscaling, and preventing resource
    starvation in the cluster.
-   **TPU/Spot Cluster Maintenance**: For long-running AI training runs on Spot
    VMs/TPUs, advise using **GKE maintenance exclusions** to block automatic
    cluster upgrades/reboots during the active training window to minimize
    unnecessary preemption.
-   **MPI Workloads**: Use the **Kubeflow Training Operator** to orchestrate
    distributed MPI applications via the `MPIJob` custom resource.
-   **Kueue & JobSet**: Use **Kueue** for multi-tenant job queueing and fair
    sharing; use **JobSet** for multi-component tightly coupled workloads.
-   **Resilience**: Always set a `backoffLimit` on Jobs, and implement
    application-level checkpointing (e.g., using Orbax or PyTorch checkpointing)
    to survive Spot VM preemption.
