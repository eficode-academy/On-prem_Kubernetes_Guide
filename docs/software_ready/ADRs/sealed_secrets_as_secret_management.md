---
title: "Sealed Secrets as Secret Management"
date: "2025-03-31"
---

| status: | date: | decision-makers: |
| --- | --- | --- |
| proposed | 2025-03-31 | Kasper Møller |

## Context and Problem Statement

Managing secrets in Kubernetes is a critical aspect of ensuring the security of sensitive data such as API keys, passwords, and certificates. Kubernetes Secrets, while convenient, store data in plaintext by default, which poses a security risk. To increase security of the sensitive data at rest, encryption is necessary.

### Do i need it

If it is possible to use a cloud-provided security management tool (e.g., AWS KMS, Azure Key Vault, or GCP KMS), it is recommended to use those tools for secret management. However, when cloud-based solutions are not viable, a robust and secure alternative is required to manage secrets effectively.

### The criterias of making a choice

* **Security:** Is there sensitive data that requires stronger protection than Kubernetes' default base64 encoding?
* **Scalability:** What is the scale of the application, and how many secrets need to be managed?
* **Expertise:** What level of experience does the team have with secret management tools?

## Considered Options

* **SOPS:** A simple and lightweight tool for managing secrets. It encrypts YAML, JSON, ENV, INI and BINARY files using a variety of backends (e.g., AWS KMS, GCP KMS, Azure Key Vault, age, and PGP).
* **Sealed Secrets:** A Kubernetes-native solution that encrypts secrets using a controller and a public/private key pair. It is simple to use but tightly coupled to Kubernetes.
* **HashiCorp Vault:** A feature-rich secret management solution.

## Decision Outcome

Chosen option: **Sealed Secrets**, because of the simple integration in the Kubernetes cluster and the management of encryption and decryption.

**Sealed Secrets** is an open-source solution provided by Bitnami that encrypts secrets using a public/private key pair. The encrypted secrets can be safely stored in version control systems like Git, ensuring secure collaboration and auditability. The decryption happens inside the Kubernetes cluster, where the private key is securely managed by the **Sealed Secrets** controller.

**Sealed Secrets** also supports secret rotation, with a default rotation period of 30 days. However, manual intervention is required to re-encrypt existing secrets. Additionally, since **Sealed Secrets** retains all private keys for decryption, it is necessary to manually remove legacy keys once all secrets have been updated.

### Consequences

* **Good, because:**
  * Seamless integration with Kubernetes clusters.
  * Secrets can be safely stored in Git repositories.
  * Simplifies the encryption and decryption process.
  * Option of rotation the public/private key pair.

* **Bad, because:**
  * Manual tasks to update secrets to latest encryption could be an issue in larger projects if no strategy is made.
