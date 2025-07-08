---
title: "OS: Talos Linux"
date: "2025-02-25"
---


| status: | date: | decision-makers: |
| --- | --- | --- |
| approved | 2025-02-25 | Sofus Albertsen |

## Context and Problem Statement

Choosing the right operating system for your Kubernetes cluster is crucial for stability, security, and operational efficiency.  The OS should be optimized for container workloads, minimize overhead, and integrate well with Infrastructure as Code (IaC) practices.

## Considered Options

* Talos Linux
* Red Hat OpenShift
* SUSE Rancher (RancherOS/RKE)

## Decision Outcome

Chosen option: **Talos Linux**, because its minimal footprint, API-driven configuration, and singular focus on Kubernetes make it ideal for automated infrastructure management and reduce operational overhead.

Talos's immutable architecture and security-focused design further enhance its suitability for Kubernetes deployments, giving you a minimal attack surface from the OS point of view. As an example, the OS does not have any shell, so no bash scripts can be executed.

OpenShift and Rancher were considered, but their comprehensive feature sets, while beneficial in some scenarios, introduce increased complexity and overhead.

While their dashboards can simplify initial setup, they can also encourage "click-ops" and deviate from IaC best practices.  These platforms might be suitable if existing Red Hat or SUSE expertise is a primary driver, but becuase they are fully fledged OS's underneath, they introduce more operational overhead than Talos.

### Consequences

* **Good:** Talos's minimal package selection makes it a smaller attack surface.
* **Good:** The API-driven configuration of Talos allows for seamless integration with IaC tools like Terraform, enabling fully automated cluster provisioning and management.
* **Good:** The immutable infrastructure of Talos simplifies updates and adds recilliency because of it's dual boot bank setup.
* **Good:** The "two package" approach simplifies maintenance (day 2 operations) and reduces the likelihood of OS-related issues, as all known package combinations can be tested from the vendor.

* **Bad:**  The learning curve for Talos might be steeper initially for teams unfamiliar with its API-driven approach.
* **Bad:**  The lack of a graphical user interface might be a drawback for some users accustomed to traditional OS management.
* **Bad:** Talos is a relatively newer project compared to OpenShift or Rancher, therefore community support and available resources might be smaller.
