---
title: "Harbor_as_image_registry"
date: "2025-03-31"
---

| status: | date: | decision-makers: |
| --- | --- | --- |
| proposed | 2025-03-31 | Kasper Møller |

## Context and Problem Statement

Containerized applications require a reliable and secure image registry to store and distribute container images. The chosen solution must integrate seamlessly with Kubernetes, provide robust security features, and support scalability for future growth.

The question is: **Which container image registry should we use for our on-premises Kubernetes cluster?**

## Considered Options

* **Harbor:** An open-source, cloud-native registry that provides vulnerability scanning, role-based access control (RBAC), and image replication. It integrates well with Kubernetes and supports OCI-compliant images.
* **JFrog Artifactory:** A universal artifact repository manager that supports container images, binaries, and other artifacts. It offers advanced features like high availability, replication, and enterprise-grade security but comes with licensing costs.
* **Sonatype Nexus:** A repository manager that supports container images and other artifacts. It provides features like vulnerability scanning and integration with CI/CD pipelines but lacks some Kubernetes-specific optimizations.

## Decision Outcome

Chosen option: **Harbor**, because it provides a strong balance of features, open-source flexibility, and seamless integration with Kubernetes, while avoiding the licensing costs associated with commercial solutions.

### Consequences

* **Good, because:**
  * Harbor is open-source and free to use, reducing costs.
  * It provides robust security features, including vulnerability scanning and RBAC, which align with our security requirements.
  * It integrates well with Kubernetes and supports image replication, making it suitable for multi-cluster setups.
  * Harbor supports Helm charts and OCI-compliant libraries, making it versatile for managing not only container images but also other Kubernetes-related artifacts.

* **Bad, because:**
  * Harbor's user interface and feature set may not be as polished or extensive as JFrog Artifactory.
  * It lacks some advanced enterprise features, such as those offered by Artifactory, which might be needed for highly complex environments.
  * While Harbor supports Helm charts, its feature set for managing non-container artifacts may not be as comprehensive as JFrog Artifactory or Sonatype Nexus.

### Recommendations

* For organizations that require a cost-effective, Kubernetes-native solution with strong security features and support for Helm charts and OCI-compliant libraries, Harbor is an excellent choice.
* For teams with complex artifact management needs and a budget for licensing, JFrog Artifactory may be a better fit due to its advanced features and broader artifact support.
* For simpler use cases or teams already using Sonatype Nexus for other artifacts, Nexus can be considered, though it may lack Kubernetes-specific optimizations and advanced Helm chart support.
