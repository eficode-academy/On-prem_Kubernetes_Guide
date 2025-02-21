---
title: On-premises Kubernetes guide
---

An opinionated guide to building and running your on-prem tech-stack for running Kubernetes.

## Introduction

Deploying and operating Kubernetes on-premises is fundamentally different from doing so in the cloud. Without a managed control plane or provider-operated infrastructure, organizations must take full ownership of networking, security, and operational automation to ensure a stable and secure environment. The complexity of these decisions can quickly lead to fragmentation, inefficiency, and technical debt if not approached with a well-defined strategy.

This guide delivers an opinionated, battle-tested roadmap for building a production-grade on-prem Kubernetes environment, structured around three foundational pillars:

- Getting your hardware ready to work with Kubernetes
- Getting your software ready to work with Kubernetes
- Working with Kubernetes

Instead of presenting endless options, we provide clear, prescriptive recommendations for primary and secondary tooling, ensuring scalability, security, and maintainability without unnecessary complexity.

By following this approach, organizations can confidently design, deploy, and sustain an optimized, resilient, and future-compatible Kubernetes cluster, making informed decisions that balance control, flexibility, and operational efficiency from day one.

## Key differences between On-prem and Cloud Kubernetes

One of the biggest challenges of running Kubernetes on-prem is the absence of elastic cloud-based scaling, where compute and storage resources can be provisioned on demand. Instead, on-prem environments require careful capacity planning to avoid resource contention while minimizing unnecessary infrastructure costs. Additionally, the operational burden extends beyond initial deployment—day-two operations such as upgrades, observability, disaster recovery, and compliance enforcement demand greater automation and proactive management to maintain stability and performance. Without cloud-native integrations, teams must build and maintain their own ecosystem of networking, storage, and security solutions, ensuring that each component is optimized for reliability and maintainability. These factors make on-prem Kubernetes deployments more complex but also provide greater control over cost, security, and regulatory compliance.

## Document Structure

With the introduction and key differences out of the way, we can now get into the important parts of the document. As mentioned in the introduction, the document is structured around three foundational pillars, namely:

- Getting your hardware ready to work with Kubernetes
- Getting your software ready to work with Kubernetes
- Working with Kubernetes

For each of these pillars, we will be providing you with primary and secondary recommendations regarding tech-stack and any accompanying tools. These recommendations will go over the tools themselves and provide you with arguments for choosing them, as well as listing out common pitfalls and important points of consideration.

## Getting your hardware ready to work with Kubernetes

### Virtualisation or bare metal

One important aspect is to determine whether the clusters should run on an OS directly on the machines, or if it makes sense to add a virtualisation layer.

Running directly on the hardware gives you a 1-1 relationship between the machines and the nodes. This is not always advised if the machines are particularly beefy. Running directly on the hardware will of course have lower latency than when adding a virtualisation layer.

A virtualisation layer can benefit via abstracting the actual hardware, and enable simple zero downtime hardware maintenance.

In case virtualisation is chosen, the below recommendations are what you would run in your VM. For setting up your VM’s we recommend Talos with KubeVirt.

### Decision Matrix

| Problem domain | Description | Reason for importance | Primary tool recommendation | Secondary tool recommendation |
|:---:|:---:|:---:|:---:|:---:|
| Kubernetes Node Operating System | The Operating System running on each of the hosts that will be part of your Kubernetes cluster | Choosing the right OS will be the foundation for building a production-grade Kubernetes cluster | Talos Linux | Flatcar Linux |
| Storage solution | The underlying storage capabilities which Kubernetes will leverage to provide persistence for stateful workloads | Choosing the right storage solution for your clusters needs is important as there is a lot of balance tradeoffs associated with it, e.g redundancy vs. complexity | Longhorn (iscsi) OpenEBS (iscsi) | Rook Ceph |
| Container Runtime (CRI) | The software that is responsible for running containers | You need a working container runtime on each node in your cluster, so that the kubelet can launch pods and their containers | Containerd (embedded in Talos??? But maybe always containerd anyways?) |  |
| Network plugin (CNI) | Plugin used for cluster networking | A CNI plugin is required to implement the Kubernetes network model | Cillium? | Calico? |

## Getting your software ready to work with Kubernetes

<!-- markdownlint-disable MD024 -->
### Decision Matrix

| Problem domain | Description | Reason for importance | Primary tool recommendation | Secondary tool recommendation |
|:---:|:---:|:---:|:---:|:---:|
| Image Registry | A common place to store and fetch images | High availability, secure access control | Harbor | Sonatype Nexus |
