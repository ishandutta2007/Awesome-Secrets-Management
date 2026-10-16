# Awesome-Secrets-Management

# Top Secrets Management Tools Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Dynamic Secrets, Privileged Access & Developer-First Secret Sync*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Secrets Management**. These tools help organizations securely store, distribute, rotate, and audit credentials — API keys, database passwords, certificates, and tokens — reducing secret sprawl and enabling least-privilege access for both humans and machine identities.

**Examples** include CyberArk, HashiCorp Vault, BeyondTrust, Thales CipherTrust, Delinea, One Identity, ManageEngine PAM360, SailPoint, Saviynt, and Okta Privileged Access (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, dynamic secret generation, and transparent governance — ideal for platform engineering teams prioritizing open licensing, avoiding vendor lock-in, and building secrets infrastructure they fully control.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[HashiCorp Vault (HCP)](https://www.hashicorp.com/products/vault)**  
  **The most capable general-purpose secrets management platform**, now an IBM product following acquisition . **Dynamic secrets** generate real database users on demand with automatic revocation at lease expiry — nothing to rotate because nothing persists long enough to need it . **Deep Terraform provider integration** means credential issuance is part of the infrastructure pipeline rather than a manual post-provisioning step . **Transit engine** provides encryption-as-a-service for application data. **Trade-offs**: The source code moved to the **Business Source License (BUSL-1.1)** in August 2023 — source-available but **not OSI-approved open source**, which matters to compliance and procurement teams . Running a highly available Vault cluster involves unseal management, upgrade cycles, and real platform engineering time . **HCP Vault Dedicated** removes operational burden at enterprise cost. **Best for platform teams needing the deepest secrets engine ecosystem** and willing to accept BUSL licensing.

- **[CyberArk Identity Security Platform](https://www.cyberark.com/)**  
  **The enterprise PAM leader** for privileged human access, with broad vaulting, session recording, endpoint privilege management (PEDM), and secure remote access . **CyberArk Conjur** extends the platform to machine identities and DevSecOps workflows . **Best for large enterprises in financial services, healthcare, energy, and government** with mature security programs and complex compliance obligations . Enterprise-negotiated pricing; no published list.

- **[BeyondTrust](https://www.beyondtrust.com/)**  
  **Leading enterprise PAM alternative to CyberArk** with privileged account management, session management, endpoint privilege management, and secure remote access. **Best for organizations needing broad PEDM and password safe coverage** in one stack.

- **[Delinea](https://delinea.com/)**  
  Enterprise PAM with privileged account vaulting, session brokering, and DevOps secrets management. Often evaluated alongside CyberArk and BeyondTrust.

- **[One Identity](https://www.oneidentity.com/)**  
  Identity governance and privileged access management suite with vaulting, session management, and least-privilege enforcement.

- **[ManageEngine PAM360](https://www.manageengine.com/)**  
  Enterprise privileged access management with credential vaulting, session monitoring, and application-to-application password management. Cost-effective for mid-market organizations.

- **[Thales CipherTrust](https://cpl.thalesgroup.com/)**  
  Enterprise key management and secrets management platform with HSM-backed root of trust, data protection, and compliance-focused controls.

- **[SailPoint](https://www.sailpoint.com/)**  
  Identity security platform with privileged access governance, including credential vaulting and session management integrated with broader identity governance.

- **[Saviynt](https://saviynt.com/)**  
  Cloud identity governance with privileged access management capabilities, including just-in-time access provisioning and credential vaulting.

- **[Okta Privileged Access](https://www.okta.com/)**  
  Privileged access management integrated with Okta's identity platform, providing just-in-time access to servers and databases with short-lived credentials.

## Open-Source GitHub Projects

- **[OpenBao](https://github.com/openbao/openbao)**  
  **The license-clean continuation of HashiCorp Vault** — MPL-2.0 licensed under Linux Foundation governance with OpenSSF oversight . **Branched from Vault's final MPL 2.0 release** after the BUSL relicensing . **Vault-compatible API and CLI** means existing tooling, Terraform providers, and integrations work with little change — the lowest-friction migration path for Vault-familiar teams . **Version 2.6** (July 2026) introduced **namespace sealing** (each namespace with its own Shamir key material for independent tenant sealing), **external KMS auto-unseal plugin binaries**, a **sys/workflows API** for wrapping standard API calls in simpler interfaces, an **authenticated root token generation endpoint**, and a **distroless container image** . **Version 2.5** had already added **horizontal read scaling** — features that are Enterprise line items in Vault, free here . **Dynamic secrets** for databases and Kubernetes are available in the community edition . **The real cost is gravity**: Vault has more tutorials, more Stack Overflow answers, and more engineers who have survived an outage with it. API compatibility carries most of that knowledge across, but you are the one signing off on production . **Best for organizations requiring an OSI-approved license** while keeping Vault-style capabilities and skills.

- **[Infisical](https://github.com/Infisical/infisical)**  
  **The developer-first, all-in-one platform for secrets, certificates, and privileged access** — **MIT-licensed core**, 27,000+ GitHub stars . **Six integrated products**: Manage Secrets, Detect Leaked Secrets, Manage Certificates (X.509 issuance and renewal), Manage Cryptographic Keys, Manage Privileged Access (session-based database and server access without revealing underlying credentials), and **Run AI Agents Securely** (brokers outbound API access so agents never hold real credentials) . **End-to-end encryption with opt-out** — the only solution offering E2EE-with-opt-out for cloud platforms that require decrypted secrets (GitHub Actions, Vercel, Render) . **Self-hosted edition has no artificial usage caps**; runs on **Postgres** (migrated from MongoDB) with Redis for queues and caching . **Kubernetes operator** syncs secrets into native K8s Secrets; **CLI injection** (`infisical run -- node index.js`) wins over developers more than anything else . **RBAC enforced at environment level** — "this team can see dev and staging, not prod" . **Pricing**: Free covers 5 identities, 3 environments, 10 syncs; **Pro at $20/identity/month** (annual) adds access controls, rotation, SAML SSO, 30-day audit logs; **Advanced at $40** unlocks dynamic secrets, honey tokens, custom roles, 90-day logs; Enterprise adds approvals, LDAP, SCIM, KMIP, self-hosting . **The trade-off**: dynamic database secrets cover fewer engines than Vault/OpenBao and are in higher-tier commercial offerings . **Best for product engineering teams** that want a real secrets platform without running Vault .

- **[CyberArk Conjur](https://github.com/cyberark/conjur)**  
  **Open-source secrets management for machine identities and DevOps workflows** — **Conjur Open Source is Apache 2.0 licensed**; **CyberArk Secrets Manager, Self-Hosted** is the commercially supported enterprise edition . **Secrets Provider for Kubernetes** and **Conjur provider for External Secrets Operator** integrate with cloud-native stacks . Positioned within the broader CyberArk Identity Security Platform, distinct from enterprise password vault (human accounts) and Endpoint Privilege Manager . **Best for organizations with existing CyberArk deployments** or strong PAM governance requirements that also need machine identity secrets management . **Note**: Conjur OSS and the enterprise edition differ materially in capabilities and support — evaluate the specific edition against your requirements .

- **[Teleport](https://github.com/gravitational/teleport)**  
  **Identity-aware access for SSH, Kubernetes, databases, and applications** — **GPL-3.0 licensed**, 31,000+ GitHub stars . **Certificate-based access with short-lived credentials** — eliminates static SSH keys and long-lived database passwords . **Session recording and audit** built in. **Pairs with Vault for JIT credential injection** . **Free Community Edition**; Enterprise priced by infrastructure resources . **Best for engineering teams replacing bastion hosts and VPNs** with certificate-based access to infrastructure.

- **[HashiCorp Boundary](https://github.com/hashicorp/boundary)**  
  **Session broker for just-in-time access to hosts and services** — pairs with Vault for credential injection . **Best for teams already invested in HashiCorp tooling** wanting unified secrets and session access governance.

- **[SOPS](https://github.com/getsops/sops)**  
  **Editor of encrypted files with KMS, age, and PGP support** — MPL-2.0 licensed, CNCF project . **Encrypts values while keeping keys in plaintext** for easy diffing and review in Git . **Not a secrets server** — it's a file encryption tool for GitOps workflows . **Best for teams storing encrypted secrets alongside code** in Git repositories.

- **[Sealed Secrets](https://github.com/bitnami-labs/sealed-secrets)**  
  **One-way encrypted secrets for Kubernetes** — encrypt secrets client-side and commit the SealedSecret to Git; the controller decrypts in-cluster . **Best for Kubernetes GitOps workflows** where secrets must live in version control.

- **[External Secrets Operator](https://github.com/external-secrets/external-secrets)**  
  **Kubernetes operator that syncs secrets from external managers** (Vault, OpenBao, AWS Secrets Manager, GCP Secret Manager, Azure Key Vault, Infisical, and more) into native Kubernetes Secrets . **The glue layer between your secrets platform and Kubernetes workloads** . **Best for any Kubernetes deployment** using an external secrets manager.

- **[Bitwarden Secrets Manager](https://github.com/bitwarden/sdk)**  
  **Open-source secrets management for DevOps** — self-hosting available on Enterprise; cloud offering also available . **Extends Bitwarden's zero-knowledge architecture** to machine secrets . **Best for teams already using Bitwarden** for password management wanting unified credential governance.

### Additional Strong Open-Source Options

- **Kubernetes Secrets Store CSI Driver** — Mounts secrets from external providers as volumes in Kubernetes pods.
- **Vault Secrets Operator** — Kubernetes operator for Vault that syncs secrets to native K8s Secrets.
- **Chamber** — CLI for managing secrets in AWS SSM Parameter Store.
- **Envy** — TUI and CLI for browsing and automating secrets.
- **fnox** — Encrypted and remote secret manager.

**Frameworks for building custom systems**: Combine **OpenBao** for Vault-compatible dynamic secrets under an OSI-approved license, **Infisical** for developer-first secret sync across environments with built-in PKI and PAM, **Teleport** for certificate-based infrastructure access replacing SSH keys, **External Secrets Operator** for syncing any secrets manager into Kubernetes, and **SOPS** or **Sealed Secrets** for GitOps-friendly encrypted secrets — to build a complete secrets management stack spanning human access, machine identities, CI/CD, and Kubernetes.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Secrets management tools differ significantly in licensing, dynamic secret capability, and operational complexity. **HashiCorp Vault's source is BUSL-1.1, not OSI-approved open source** — OpenBao is the MPL-2.0 fork that inherits Vault's API and skills . **Infisical's dynamic database secrets cover fewer engines than Vault/OpenBao** and are in higher-tier commercial offerings — validate against your specific database requirements before assuming parity . **Conjur OSS and Conjur Enterprise differ materially** — the open-source edition lacks capabilities and support of the commercial Secrets Manager, Self-Hosted . **Doppler is hosted-only** — no self-hosted option exists if keeping secrets infrastructure inside your network is a hard requirement . **The most important architectural point for AI agents**: none of these tools keeps a secret out of an agent's reach on its own, because they all hand the credential to whatever authenticates. The pattern that defends against prompt-injection exfiltration is a vault behind a **credential proxy** .
- Self-hosted open-source solutions require proper Postgres reliability practices (backups, PITR, restore drills), Redis sizing at scale, and schema migration planning across major version upgrades.

---

**Made for platform engineers, security architects, DevOps teams, and developers building secrets management platforms.**
Let's make secrets management more open, auditable, and developer-friendly.
