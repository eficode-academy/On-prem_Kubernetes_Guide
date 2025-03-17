---
title: "Virtualisation"
date: "2025-03-17"
---


| status: | date: | decision-makers: |
| --- | --- | --- |
| proposed | 2025-03-17 | Alexandra Aldershaab |


## Context and Problem Statement

One important aspect is to determine whether the clusters should run on an OS directly on the machines, or if it makes sense to add a virtualisation layer.

Running directly on the hardware gives you a 1-1 relationship between the machines and the nodes. This is not always advised if the machines are particularly beefy. Running directly on the hardware will of course have lower latency than when adding a virtualisation layer.

A virtualisation layer can benefit via abstracting the actual hardware, and enable simple zero downtime hardware maintenance.

For larger companies, it is usually possible to provision VM's from the IT department, and in that case the clear recommendation would alway be to just use what is available.

## Considered Options

* KubeVirt
* Incus
* Proxmox

## Decision Outcome

Chosen option: "{title of option 1}", because {justification. e.g., only option, which meets k.o. criterion decision driver | which resolves force {force} | … | comes out best (see below)}.

<!-- This is an optional element. Feel free to remove. -->
### Consequences

* Good, because {positive consequence, e.g., improvement of one or more desired qualities, …}
* Bad, because {negative consequence, e.g., compromising one or more desired qualities, …}
* … <!-- numbers of consequences can vary -->