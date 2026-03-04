# AzCopy v10

## Introduction

AzCopy is a high-performance command-line utility designed for fast and secure data transfer to and from Microsoft Azure Storage services. It enables users to efficiently copy data between local systems and Azure Blob Storage, Azure Files, and Azure Data Lake Storage. Built for reliability and speed, AzCopy leverages parallelization and optimized network usage to deliver maximum throughput, even when handling large-scale datasets.

AzCopy is commonly used for cloud migrations, backup operations, disaster recovery setups, and large data synchronization tasks. It provides detailed logging and performance reporting, allowing administrators to monitor transfer status and troubleshoot issues effectively. The utility is cross-platform and runs on Windows, macOS, and Linux environments, making it ideal for developers, IT professionals, and DevOps teams.

Optimized for automation, AzCopy can be integrated into scripts and CI/CD pipelines, enabling scalable and repeatable data workflows. Whether transferring a few files or petabytes of information, AzCopy delivers secure, consistent, and high-speed data movement across Azure storage environments.

## Authentication & Access Control

AzCopy supports multiple authorization models so you can align transfers with your security posture. For interactive, role-based access, you can authenticate with Microsoft Entra ID and use Azure RBAC; in that case, ensure the identity has a suitable data-plane role (for example, **Storage Blob Data Contributor**) scoped to the storage account, resource group, or subscription.

For automated pipelines and limited-scope operations, AzCopy also works with **SAS tokens** and **storage account keys**, which are useful when you need time-bound access or when interactive sign-in isn’t practical. Choose SAS when you want least-privilege, expiration-based access; reserve account keys for tightly controlled environments because they generally grant broad permissions.

## Usage Essentials: Data Integrity, Preservation & Operational Safety

Before large migrations, decide what must be preserved and validated. AzCopy can preserve metadata and (for Azure Files) SMB/NFS properties and permissions using preservation flags; on Linux, preserving owner/group may require elevated privileges when downloaded ownership differs from the current user.

Plan for integrity verification and predictable operations. MD5 handling can be important in compliance-sensitive environments: AzCopy does not automatically calculate and store an MD5 hash for files larger than 256 MB unless this option is explicitly enabled, which can impact downstream validation processes.

From an operational standpoint, treat transfers as jobs that may need to be audited or resumed. Use dry-run where available (for example, before deletion operations) to preview changes without modifying the data. For large-scale transfers, performance can often be improved by lowering log verbosity and disabling post-transfer length checks when appropriate. Throughput and parallelism can also be tuned using AzCopy settings or environment variables after proper benchmarking.
