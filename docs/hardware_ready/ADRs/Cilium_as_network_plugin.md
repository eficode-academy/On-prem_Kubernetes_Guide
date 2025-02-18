---
title: Use Cillium as Network Plugin
---

| status: | date: | decision-makers: |
| --- | --- | --- |
| proposed | 2025-02-18 | Alexandra Aldershaab |


## Context and Problem Statement

A CNI plugin is required to implement the Kubernetes network model

## Considered Options

* Flannel
* Cilium
* Calico

## Decision Outcome

Chosen option: Cillium, because we believe it is the future of CNI's.

We looked at Flannel, since it is embedded in Talos, but we wanted a plugin that would support Network policies, which flannel do not.

Calico, while supporting Network policies, just doesn't offer the vast range of smart stuff cilium does.

### Consequences

* Good, because {positive consequence, e.g., improvement of one or more desired qualities, …}
* Bad, because {negative consequence, e.g., compromising one or more desired qualities, …}
* … <!-- numbers of consequences can vary -->