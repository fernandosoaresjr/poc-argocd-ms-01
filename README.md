# PoC - Multi-Cluster Deployment with ArgoCD and Argo Rollout

This repository represents a Proof of Concept (PoC) for deploying a multi-cluster application using **ArgoCD** and **Argo Rollouts**.

## About the PoC

The goal of this PoC is to demonstrate how to deploy a simple application to _n_ number of Kubernetes clusters using ArgoCD and Argo Rollouts in a controlled and structured manner.

## Problem Statement

In modern cloud environments, organizations often operate across multiple Kubernetes clusters for redundancy, performance, or client segmentation. However, deploying applications across multiple clusters in a controlled way can be complex. This PoC aims to address these challenges by implementing a structured multi-cluster deployment strategy.

## Deployment Strategy

Even though this is a multi-cluster deployment, we focus on **a single environment** (e.g., `staging` or `production`). The deployment follows a sequential rollout process across clusters, based on stability signals and time-based gating mechanisms.

### Key Principles

- **Configurable Cluster Scaling:** The number of clusters is fully configurable, allowing flexibility based on infrastructure and operational needs.
- **Fast Iteration for Development Teams:** Developers can deploy freely in the first cluster to test and iterate quickly.
- **Non-Critical Clients First:** The initial clusters serve non-critical clients, allowing early adopters to use the latest features.
- **Stability-Based Promotion:** The application is promoted to the next cluster only when it meets stability criteria (e.g., health checks, error rates, or time-based constraints).
- **Critical Clients Are Protected:** The last clusters in the chain serve the most critical clients, ensuring they only receive stable and well-tested versions.

### Deployment Flow

1. **Deployment starts in the first cluster**
   - Developers deploy frequently ("deploy fast, fail fast").
   - Observability and monitoring tools track application health.
2. **Automatic or manual promotion to the next cluster**
   - If health metrics are within acceptable thresholds, the rollout continues.
   - If issues arise, the rollout is halted or rolled back.
3. **Final clusters serve critical clients**
   - Only stable versions reach these clusters.
   - Critical clients experience fewer disruptions due to bugs or instability.

## Technologies Used

- **ArgoCD**: GitOps-based continuous delivery for Kubernetes.
- **Argo Rollouts**: Progressive delivery tool for advanced deployment strategies (e.g., Canary, Blue-Green, etc.).
- **Kubernetes**: Multi-cluster setup for testing.
- **Prometheus + Grafana**: Monitoring and observability.
- **Istio (optional)**: Service mesh for traffic routing (if needed for testing different rollout strategies).

## How to Run the PoC

WIP: The PoC is currently under development. Detailed instructions will be provided once the PoC is ready for testing.


---

This PoC serves as a foundation for multi-cluster deployments with controlled rollouts. Contributions and feedback are welcome!
