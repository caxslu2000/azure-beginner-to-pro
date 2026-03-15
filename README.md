# Azure Beginner to Pro

A practical collection of **real-world troubleshooting scenarios, solutions and operational notes** from working with Microsoft Azure environments.

This repository documents common issues, unexpected behaviors and lessons learned while operating cloud infrastructure, networking, storage, identity and automation in Azure.

The goal is to create a **knowledge base for engineers progressing from beginner to advanced levels in Azure operations and architecture**.

---

# Purpose

This repository aims to help engineers:

- Understand real-world Azure issues
- Learn troubleshooting techniques
- Document operational patterns
- Build practical Azure knowledge
- Share field-tested solutions

Unlike theoretical tutorials, the content here focuses on **problems encountered in production environments and how they were solved**.

---

# Topics Covered

This repository will include troubleshooting and operational notes related to:

- Azure Storage
- Azure Networking
- Azure Virtual Machines
- Identity and Access Management
- Azure CLI automation
- Infrastructure scripting
- Cloud security configurations
- Observability and monitoring
- SFTP and file transfer architectures
- CI/CD integrations

---

# Repository Structure

```
azure-beginner-to-pro
│
├── storage
│   ├── sftp
│   ├── blob
│   └── datalake
│
├── networking
│   ├── private-endpoints
│   ├── firewall
│   └── load-balancers
│
├── identity
│   ├── entra-id
│   └── rbac
│
├── compute
│   ├── virtual-machines
│   └── vm-troubleshooting
│
├── automation
│   ├── azure-cli
│   ├── scripts
│   └── pipelines
│
└── troubleshooting
    └── real-world-cases
```

Each section contains:

- Problem description
- Environment context
- Investigation steps
- Root cause
- Solution
- Lessons learned

---

# Example Troubleshooting Topics

Some examples of issues documented in this repository:

- Azure Storage SFTP authentication failures
- RBAC permission issues when using Azure CLI
- Storage ACL errors (`InvalidNamedUserOrNamedGroup`)
- Azure CLI authentication inconsistencies
- Storage account permission scope problems
- Network connectivity restrictions
- Misconfigured home directories in Azure Storage SFTP
- Access control conflicts between RBAC and ACL

---

# Philosophy

Cloud engineering is not just about deploying infrastructure.

It is about:

- Diagnosing failures
- Understanding platform behavior
- Investigating undocumented edge cases
- Building operational experience

This repository reflects that mindset.

---

# Who is this for?

This content may be useful for:

- Cloud Engineers
- DevOps Engineers
- Infrastructure Engineers
- Platform Engineers
- Students learning Azure
- Anyone working with Azure environments

---

# Contribution

This repository is primarily a **personal knowledge base**, but suggestions and improvements are welcome.

If you encounter similar issues or want to improve documentation, feel free to contribute.

---

# Disclaimer

All examples use **generic names and sanitized environments**.

No production identifiers, credentials or sensitive information are included.

---

# Author

Maintained by a Cloud & Infrastructure Engineer documenting real-world Azure operations.

---

# Future Plans

Planned additions include:

- More Azure networking troubleshooting
- Identity and RBAC edge cases
- Azure CLI automation patterns
- Infrastructure architecture notes
- Monitoring and observability setups
- Cloud security lessons learned
