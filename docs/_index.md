---
title: On-premises Kubernetes guide
---

An opinionated guide to building and running your on-prem tech-stack for running Kubernetes.
## Introduction
Deploying and operating Kubernetes on-premises is fundamentally different from doing so in the cloud. Without a managed control plane or provider-operated infrastructure, organizations must take full ownership of networking, security, and operational automation to ensure a stable and secure environment. The complexity of these decisions can quickly lead to fragmentation, inefficiency, and technical debt if not approached with a well-defined strategy.

This guide delivers an opinionated, battle-tested roadmap for building a production-grade on-prem Kubernetes environment, structured around three foundational pillars:
- [Getting your hardware ready to work with Kubernetes](hardware_ready/_index.md)
- [Getting your software ready to work with Kubernetes](software_ready/_index.md)
- [Working with Kubernetes](working_with_k8s/_index.md)

Instead of presenting endless options, we provide clear, prescriptive recommendations for tooling, ensuring scalability, security, and maintainability without unnecessary complexity.

By following this approach, organizations can confidently design, deploy, and sustain an optimized, resilient, and future-compatible Kubernetes cluster, making informed decisions that balance control, flexibility, and operational efficiency from day one.

## Key differences between On-prem and Cloud Kubernetes
One of the biggest challenges of running Kubernetes on-prem is the absence of elastic cloud-based scaling, where compute and storage resources can be provisioned on demand. Instead, on-prem environments require careful capacity planning to avoid resource contention while minimizing unnecessary infrastructure costs. Additionally, the operational burden extends beyond initial deployment—day-two operations such as upgrades, observability, disaster recovery, and compliance enforcement demand greater automation and proactive management to maintain stability and performance. Without cloud-native integrations, teams must build and maintain their own ecosystem of networking, storage, and security solutions, ensuring that each component is optimized for reliability and maintainability. These factors make on-prem Kubernetes deployments more complex but also provide greater control over cost, security, and regulatory compliance.

## Document Structure
With the introduction and key differences out of the way, we can now get into the important parts of the document. As mentioned in the introduction, the document is structured around three foundational pillars, namely:

- [Getting your hardware ready to work with Kubernetes](hardware_ready/_index.md)
- [Getting your software ready to work with Kubernetes](software_ready/_index.md)
- [Working with Kubernetes](working_with_k8s/_index.md)

For each of these pillars, we will be providing you with tool recommendations regarding tech-stack and any accompanying tools. These recommendations will go over the tools themselves and provide you with arguments for choosing them, as well as listing out common pitfalls and important points of consideration.
