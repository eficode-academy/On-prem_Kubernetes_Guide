---
title: Getting your hardware ready
---
## Decision Matrix

| Problem domain | Description | Reason for importance | Tool recommendation |
|:---:|:---:|:---:|:---:|
| Kubernetes Node Operating System | The Operating System running on each of the hosts that will be part of your Kubernetes cluster | Choosing the right OS will be the foundation for building a production-grade Kubernetes cluster | [Talos OS](hardware_ready/ADRs/talos_as_os.md) |
| Storage solution | The underlying storage capabilities which Kubernetes will leverage to provide persistence for stateful workloads | Choosing the right storage solution for your clusters needs is important as there is a lot of balance tradeoffs associated with it, e.g redundancy vs. complexity | [Longhorn](Longhorn_as_storage_solution.md) |
| Container Runtime (CRI) | The software that is responsible for running containers | You need a working container runtime on each node in your cluster, so that the kubelet can launch pods and their containers |  |
| Network plugin (CNI) | Plugin used for cluster networking | A CNI plugin is required to implement the Kubernetes network model | [Cilium](Cilium_as_network_plugin.md) |
| Virtualisation | An optional layer between your hardware and your Kubernetes tech stack | In some scenarioes it might be benefitial to abstract the underlying hardeware away, and have everything running in virtual machines | [KubeVirt??](virtualisation.md) |
