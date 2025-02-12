---
status: proposed
date: 2025-02-12
decision-makers: Alexandra Aldershaab
---

# Use Cillium as Network Plugin

## Context and Problem Statement

A CNI plugin is required to implement the Kubernetes network model

## Considered Options

* Cillium
* Calico

## Decision Outcome

Chosen option: Cillium, because it was recommended at a knowledge sharing event by a company running large scale Kubernetes on prem. If we go with Talos, this is also the only CNI plugin they have a guide on how to use with Talos. 

