# Azure Cloud Environment Setup – Summary Report

**Student:** Olamileye Duduyemi  
**Date:** May 2026  
**Assignment:** Foundational Introduction to Cloud Computing – Microsoft Azure Setup

---

## 1. Overview

This report summarizes the setup of a Microsoft Azure Free Tier environment, covering the creation of a subscription, resource group, and a test resource deployment. It also outlines the region selection rationale and how the Shared Responsibility Model applies to the deployed resource.

---

## 2. Region Selection

### Chosen Region: **UK South (London)**

### Rationale

Deploying from **Nigeria (West Africa)**, there is currently no Azure region located on the African continent's west coast. The **UK South** region (London, United Kingdom) was selected as the optimal choice for the following reasons:

- **Geographic Proximity:** At approximately 4,900 km from Lagos, Nigeria, UK South (London) is the closest major Azure region geographically, offering lower latency compared to other European alternatives.
- **Availability Zones:** UK South supports multiple Availability Zones (AZ-1, AZ-2, AZ-3), providing redundancy and high availability for services that require it.
- **Service Coverage:** UK South offers a broad range of Azure services including Compute (Virtual Machines), Storage Accounts, Azure Active Directory, and Cost Management — all of which are relevant to this assignment.
- **Compliance:** Storing data in UK South aligns with international data protection standards. For Nigerian users, this is relevant under the **Nigeria Data Protection Regulation (NDPR)**, which mandates lawful cross-border data transfers.

### Alternative Region Considered

**West Europe (Netherlands/Amsterdam)** was considered as a secondary option, but at approximately 5,100 km from Lagos it is slightly farther than UK South. **South Africa North (Johannesburg)** was also evaluated as an African-continent option, however at ~5,500 km from Lagos it is actually farther than London, and UK South provides a richer service catalog for this assignment's requirements.

---

## 3. Resource Deployed

### Resource Type: **Azure Storage Account (PaaS)**

A **Storage Account** was deployed in the `assignment-rg` Resource Group within the **UK South** region, accessed remotely from Lagos, Nigeria.

**Configuration Details:**

| Setting              | Value                        |
|----------------------|------------------------------|
| Resource Type        | Storage Account              |
| Resource Group       | `assignment-rg`              |
| Region               | UK South                     |
| Performance          | Standard                     |
| Redundancy           | Locally Redundant (LRS)      |
| Service Model        | Platform as a Service (PaaS) |

A Storage Account was chosen over a Virtual Machine because it:
- Falls well within the Azure Free Tier limits (5 GB free).
- Has no compute costs (unlike a VM which consumes compute hours).
- Demonstrates the PaaS model, where Azure manages the underlying infrastructure.

---

## 4. Shared Responsibility Model

The **Shared Responsibility Model** defines which security tasks are handled by the cloud provider (Microsoft Azure) and which remain the responsibility of the customer (me, as the cloud user).

### How It Applies to a Storage Account (PaaS)

| Responsibility Area            | Microsoft Azure (Provider)              | Customer (Me)                                |
|--------------------------------|-----------------------------------------|----------------------------------------------|
| **Physical Security**          | ✅ Secures data centers, hardware       | ❌ Not responsible                           |
| **Network Infrastructure**     | ✅ Manages underlying network fabric    | ❌ Not responsible                           |
| **Host OS / Virtualization**   | ✅ Manages hypervisor and host OS       | ❌ Not responsible                           |
| **Platform & Runtime**         | ✅ Manages storage service platform     | ❌ Not responsible                           |
| **Data Encryption (at rest)**  | ✅ Provides encryption by default (AES-256) | ✅ Must ensure correct key management if using CMK |
| **Access Control (IAM/RBAC)**  | ✅ Provides RBAC tools                  | ✅ Must configure roles and permissions correctly |
| **Data Classification**        | ❌ Not Azure's responsibility           | ✅ Must tag and classify sensitive data      |
| **Network Access Rules**       | ✅ Provides firewall/VNet tools         | ✅ Must configure allowed IPs and networks   |
| **Application-Level Security** | ❌ Not Azure's responsibility           | ✅ Must secure any app using the storage     |
| **Compliance & Auditing**      | ✅ Provides audit logs (Activity Log)   | ✅ Must review and act on audit logs         |

### Key Takeaway

For **PaaS services** like Storage Accounts, Azure handles most of the infrastructure-level security (physical, host, and platform layers). However, the **customer retains full responsibility** for:
- **Who can access the storage** (configuring RBAC and Shared Access Signatures correctly).
- **What data is stored** and whether it is classified and tagged appropriately.
- **Network-level controls** such as restricting access to specific virtual networks or IP ranges.
- **Application security** for any code that reads from or writes to the storage account.

This is different from **IaaS** (e.g., a Virtual Machine), where the customer is additionally responsible for the operating system, runtime, middleware, and application — a much larger security surface.

---

## 5. Summary of Completed Tasks

| Task                        | Status    | Notes                                                      |
|-----------------------------|-----------|------------------------------------------------------------|
| Account Registration        | ✅ Done   | Azure Free Tier account created with verified identity     |
| Portal Exploration          | ✅ Done   | Navigated dashboard, service menu, and search              |
| Subscription Identified     | ✅ Done   | Azure subscription visible on dashboard                    |
| Resource Group Created      | ✅ Done   | `assignment-rg` created in UK South                        |
| Azure AD / RBAC Reviewed    | ✅ Done   | Explored user management and RBAC documentation            |
| Region Selected             | ✅ Done   | UK South — closest Azure region to Nigeria (~4,900 km)     |
| Resource Deployed           | ✅ Done   | Storage Account deployed in `assignment-rg`                |
| Cost Management Configured  | ✅ Done   | Accessed Cost Analysis and Budgets section                 |

---

*Report prepared as part of the Azure Cloud Computing Foundations assignment.*
