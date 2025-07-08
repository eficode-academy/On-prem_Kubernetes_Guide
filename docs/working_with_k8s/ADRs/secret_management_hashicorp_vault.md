---
title: "Secret Management: Hashicorp Vault"
date: "2025-04-14"
---


| status: | date: | decision-makers: |
| --- | --- | --- |
| approved | 2025-04-14 | Kasper Møller |

## Context and Problem Statement

Managing secrets in Kubernetes is a critical aspect of ensuring the security of sensitive data such as API keys, passwords, and certificates. Kubernetes Secrets, while convenient, store data in plaintext by default, which poses a security risk. To increase security of the sensitive data at rest, encryption is necessary.

To mitigate this risk, a robust secret management solution is required. This solution should provide strong encryption, easy integration with Kubernetes, and support for secret rotation. Additionally, it should be easy to use and manage, allowing teams to focus on their applications rather than the underlying infrastructure.

### Do i need it

If it is possible to use a cloud-provided security management tool (e.g., AWS KMS, Azure Key Vault, or GCP KMS), it is recommended to use those tools for secret management. These tools are designed to handle sensitive data securely and provide built-in features for encryption, access control, and auditing. however it is recommended to utilize **External Secrets Operator** to manage the secrets in Kubernetes. This operator allows you to synchronize secrets from external secret management systems into Kubernetes secrets, making it easier to change the secret management solution without changing the way secrets are accessed in your applications to avoid vendor lock-in.

However, when cloud-based solutions are not viable, an on-premises or self-hosted solution is required to manage secrets effectively.

### The criterias of making a choice

* **Security:** Is there sensitive data that requires stronger protection than Kubernetes' default base64 encoding?
* **Scalability:** What is the scale of the application, and how many secrets need to be managed?
* **Expertise:** What level of experience does the team have with secret management tools?
* **Integration:** How well does the solution integrate with existing tools and workflows?
* **Ease of Use:** How easy is it to set up and manage the solution?
* **Cost:** What are the costs associated with using the solution, including licensing, infrastructure, and maintenance?

## Considered Options

* **SOPS:** A simple and lightweight tool for managing secrets. It encrypts YAML, JSON, ENV, INI and BINARY files using a variety of backends (e.g., AWS KMS, GCP KMS, Azure Key Vault, age, and PGP).
* **Sealed Secrets:** A Kubernetes-native solution that encrypts secrets using a controller and a public/private key pair. It is simple to use but tightly coupled to Kubernetes.
* **HashiCorp Vault:** A feature-rich secret management solution that provides strong encryption, access control, and auditing capabilities. It supports various backends for storage.

## Decision Outcome

Chosen option: **HashiCorp Vault**, because it provides a comprehensive solution for managing secrets with strong encryption and access control. It integrates well with Kubernetes and supports secret rotation, making it suitable for managing sensitive data in a secure manner. Additionally, **HashiCorp Vault** offers a wide range of features, including dynamic secrets, leasing, and revocation, which enhance security and flexibility in managing secrets.

The secrets in **HashiCorp Vault** can be accessed using **External Secrets Operator**, which allows for seamless integration with Kubernetes. This enables the possibility to exchange the secret management solution in the future without changing the way secrets are accessed in applications.

**HashiCorp Vault** has a fixed based on the required package and it is reccomended to look into the pricing for the other external providers such as AWS KMS, Azure Key Vault, or GCP KMS to see if they are more cost-effective for your use case. The use of **External Secrets Operator** is the same regardless and is free to use.

**SOPS** and **Sealed Secrets** are also good options, but they may not provide the same level of security and features as **HashiCorp Vault**. They require a well defined strategy for managing secrets and may not be as scalable or flexible as **HashiCorp Vault** which introduces additional complexity and will be harder to manage in the long run.

### Consequences

* Good, because:
  * vast range of features for managing secrets.
  * strong encryption and access control.
  * supports secret rotation and dynamic secrets.
  * integrates well with Kubernetes.
* Bad, because:
  * requires additional setup and management compared to simpler solutions.
  * requires a license for enterprise features.
