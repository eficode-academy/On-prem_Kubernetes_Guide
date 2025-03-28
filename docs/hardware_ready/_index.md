---
title: Getting your hardware ready
---
## Virtualisation or bare metal

One important aspect is to determine whether the clusters should run on an OS directly on the machines, or if it makes sense to add a virtualisation layer.

Running directly on the hardware gives you a 1-1 relationship between the machines and the nodes. This is not always advised if the machines are particularly beefy. Running directly on the hardware will of course have lower latency than when adding a virtualisation layer.

A virtualisation layer can benefit via abstracting the actual hardware, and enable simple zero downtime hardware maintenance.

In case virtualisation is chosen, the below recommendations are what you would run in your VM. For setting up your VM’s we recommend Talos with KubeVirt.

## Decision Matrix

| Problem domain | Description | Reason for importance | Tool recommendation |
|:---:|:---:|:---:|:---:|
| Kubernetes Node Operating System | The Operating System running on each of the hosts that will be part of your Kubernetes cluster | Choosing the right OS will be the foundation for building a production-grade Kubernetes cluster | [Talos OS](hardware_ready/ADRs/talos_as_os.md) |
| Storage solution | The underlying storage capabilities which Kubernetes will leverage to provide persistence for stateful workloads | Choosing the right storage solution for your clusters needs is important as there is a lot of balance tradeoffs associated with it, e.g redundancy vs. complexity | [Longhorn](Longhorn_as_storage_solution.md) |
| Container Runtime (CRI) | The software that is responsible for running containers | You need a working container runtime on each node in your cluster, so that the kubelet can launch pods and their containers |  |
| Network plugin (CNI) | Plugin used for cluster networking | A CNI plugin is required to implement the Kubernetes network model | [Cilium](Cilium_as_network_plugin.md) |
