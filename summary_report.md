# Azure Cloud Environment Setup – Summary Report

**Student:** Olamileye Duduyemi
**Date:** May 2026
**Assignment:** Foundational Introduction to Cloud Computing – Microsoft Azure Setup

---

## 1. Overview

This report documents the end-to-end setup of a Microsoft Azure Free Tier environment, covering account registration, portal navigation, resource group creation, resource deployment, identity and access management, cost management configuration, and cloud security principles. It also outlines the region selection rationale and the Shared Responsibility Model as it applies to the deployed resource.

---

## 2. Account Registration – Step-by-Step Process

### Step 1 – Navigate to the Azure Free Tier Page
Go to **[https://azure.microsoft.com/free](https://azure.microsoft.com/free)** and click **"Start free"**.

### Step 2 – Sign In with a Microsoft Account
Sign in with an existing Microsoft account (Outlook, Hotmail) or create a new one at **[https://account.microsoft.com](https://account.microsoft.com)**. A Microsoft account is required to access Azure.

### Step 3 – Enter Personal Details
Fill in the registration form:
- Full name
- Country/Region (selected: **Nigeria**)
- Date of birth

### Step 4 – Phone Verification
Azure requires phone-based identity verification:
1. Enter your mobile phone number (including country code, e.g. +234 for Nigeria)
2. Choose **"Text me"** or **"Call me"**
3. Enter the 6-digit verification code received via SMS
4. Click **"Verify code"**

### Step 5 – Payment Method Validation
A debit or credit card is required for identity verification. Azure charges a **temporary $1 authorization hold** (which is refunded within a few days). No charges occur while using the Free Tier:
1. Select card type (Visa, Mastercard, etc.)
2. Enter card number, expiry date, and CVV
3. Enter billing address
4. Click **"Sign up"**

> ⚠️ **Important:** The $1 charge is for identity verification only. Azure will NOT bill you for Free Tier services unless you manually upgrade to Pay-As-You-Go.

### Step 6 – Agreement and Activation
- Review and accept the Azure Subscription Agreement and Privacy Statement
- Click **"Sign up"**
- After a short loading screen, you are redirected to the **Azure Portal** at [https://portal.azure.com](https://portal.azure.com)

### What You Get with the Free Tier
| Benefit | Details |
|---|---|
| **Credit** | $200 USD for the first 30 days |
| **Duration** | 12 months of selected free services |
| **Always Free** | 55+ services always free (e.g., Azure Functions, App Service) |
| **Storage** | 5 GB Blob Storage free for 12 months |
| **Compute** | 750 hours/month of B1s Linux VM for 12 months |

---

## 3. Azure Portal Navigation

### 3.1 Dashboard Overview
Upon login, the **Azure Portal home** ([https://portal.azure.com](https://portal.azure.com)) presents:
- **Top navigation bar** – Search bar, Cloud Shell (`>_`), Notifications bell, Account settings
- **Left sidebar** – Quick links: Home, Dashboard, All Services, Resource Groups, Subscriptions
- **Central tiles** – Shortcut cards for recently accessed services and resources
- **Favourites** – Pinned services for quick access

### 3.2 Using the Search Bar
The **global search bar** (top centre) is the fastest way to navigate:
- Type any service name (e.g., `"Storage accounts"`, `"Virtual Machines"`, `"Cost Management"`)
- Results appear instantly, categorised as **Services**, **Resources**, and **Marketplace**
- Clicking a result navigates directly to that service or resource blade

### 3.3 Using Breadcrumbs
Azure uses **breadcrumb navigation** displayed at the top of every page to show your current location in the portal hierarchy. For example:

```
Home > Resource groups > assignment-rg > Storage accounts > mystorageaccount
```

- Each item in the breadcrumb is **clickable** and navigates back to that level
- Breadcrumbs help you understand the parent-child relationship between resources (e.g., a Storage Account belongs to a Resource Group, which belongs to a Subscription)
- This is especially useful when drilling into nested resource settings

### 3.4 Service Menus (Left Blade Navigation)
When you open any resource or service, a **left-side blade menu** appears with contextual options. For example, on a Storage Account:
- **Overview** – Summary, status, endpoints
- **Access keys** – Shared access credentials
- **Networking** – Firewall and VNet rules
- **Tags** – Metadata key-value pairs
- **Monitoring** – Metrics and diagnostics

### 3.5 Custom Dashboard Setup
A custom Azure Dashboard was created to centralise key monitoring tiles:

**Steps to create a custom dashboard:**
1. From the Azure Portal home, click **"Dashboard"** in the left sidebar
2. Click **"+ New dashboard"** → select **"Blank dashboard"**
3. Name the dashboard (e.g., `"Assignment Dashboard"`)
4. In the **Tile Gallery** on the right, search for and drag tiles onto the canvas:
   - **"All resources"** – Shows a live list of all deployed resources
   - **"Resource groups"** – Quick view of all resource groups
   - **"Clock"** – UTC time display
   - **"Service Health"** – Azure service status
5. Resize and arrange tiles by dragging their corners
6. Click **"Save"** (top left) to persist the dashboard

*Screenshot evidence: see `screenshots/04_custom_dashboard.png`*

---

## 4. Governance Setup – Subscription & Resource Group

### 4.1 Subscription
The **Azure Free Tier** creates one subscription automatically upon account activation:
- **Subscription Name:** Azure subscription 1
- **Status:** Active
- **Type:** Free Trial / Pay-As-You-Go (after trial)

Subscriptions act as the **billing boundary** and **access control boundary** in Azure. All resources and their costs are tracked under the subscription.

*Screenshot evidence: see `screenshots/01_azure_dashboard.png`*

### 4.2 Resource Group Created
A **Resource Group** named `assignment-rg` was created to serve as a logical container for all project resources:

| Setting | Value |
|---|---|
| Resource Group Name | `assignment-rg` |
| Region | UK South |
| Subscription | Azure subscription 1 |

**Steps to create:**
1. Search `"Resource groups"` in the portal search bar
2. Click **"+ Create"**
3. Enter the name `assignment-rg`, select subscription, select region **UK South**
4. Click **"Review + create"** → **"Create"**

*Screenshot evidence: see `screenshots/02_resource_group.png`*

---

## 5. Region Selection

### Chosen Region: **UK South (London)**

### Rationale

Deploying from **Nigeria (West Africa)**, there is currently no Azure region located on the African continent's west coast. The **UK South** region (London, United Kingdom) was selected as the optimal choice for the following reasons:

- **Geographic Proximity:** At approximately 4,900 km from Lagos, Nigeria, UK South (London) is the closest major Azure region geographically, offering lower latency compared to other European alternatives.
- **Availability Zones:** UK South supports multiple Availability Zones (AZ-1, AZ-2, AZ-3), providing redundancy and high availability for services that require it.
- **Service Coverage:** UK South offers a broad range of Azure services including Compute (Virtual Machines), Storage Accounts, Azure Active Directory, and Cost Management — all of which are relevant to this assignment.
- **Compliance:** Storing data in UK South aligns with international data protection standards. For Nigerian users, this is relevant under the **Nigeria Data Protection Regulation (NDPR)**, which mandates lawful cross-border data transfers.

### Alternative Regions Considered

| Region | Distance from Lagos | Decision |
|---|---|---|
| **UK South (London)** | ~4,900 km | ✅ Selected — closest |
| West Europe (Netherlands) | ~5,100 km | ❌ Farther |
| South Africa North (Johannesburg) | ~5,500 km | ❌ Farther and fewer services |

---

## 6. Identity & Access Management (Azure AD / RBAC)

### 6.1 Microsoft Entra ID (formerly Azure Active Directory)
Navigated to **Microsoft Entra ID** via the portal search bar:
- Reviewed the **Users** section — the student account is listed as the sole user and Global Administrator
- Explored **Roles and administrators** — viewed all built-in RBAC roles

### 6.2 Key RBAC Roles Reviewed
| Role | Description |
|---|---|
| **Owner** | Full access including managing permissions |
| **Contributor** | Can create/manage resources but cannot manage access |
| **Reader** | Read-only access to all resources |

### 6.3 Account Security – MFA
Multi-Factor Authentication (MFA) is **enabled by default** on Microsoft accounts. Azure enforces MFA for portal sign-in via **Microsoft Authenticator** or SMS. To review:
1. Navigate to **Microsoft Entra ID** → **Security** → **Authentication methods**
2. Confirm MFA is active for the admin account

Password policy: Microsoft accounts enforce a minimum password length and complexity. Azure AD applies Conditional Access policies in enterprise environments.

---

## 7. Resource Deployed – Azure Storage Account (PaaS)

A **Storage Account** named `mystaticdoc` was deployed in the `rg-staticweb` Resource Group within the **West Europe** region, accessed remotely from Lagos, Nigeria.

**Steps to deploy:**
1. Search `"Storage accounts"` in the portal search bar → click **"+ Create"**
2. Select subscription: `Azure subscription 1`
3. Select resource group: `rg-staticweb`
4. Enter a globally unique storage account name: `mystaticdoc`
5. Select region: **West Europe**
6. Performance: **Standard**; Redundancy: **Locally Redundant (LRS)**
7. Click **"Review"** → **"Create"** → wait ~30 seconds for deployment

**Configuration Details:**

| Setting | Value |
|---|---|
| Resource Type | Storage Account (PaaS) |
| Account Name | `mystaticdoc` |
| Resource Group | `rg-staticweb` |
| Region | West Europe |
| Performance | Standard |
| Redundancy | Locally Redundant (LRS) |
| Account Kind | StorageV2 (general purpose v2) |
| Created | 01/06/2026 |
| Free Tier Allowance | 5 GB Blob Storage (12 months) |

A Storage Account was chosen over a Virtual Machine because it falls within the Azure Free Tier limits (5 GB free), incurs no compute costs, and demonstrates the PaaS model where Azure manages the underlying infrastructure.

---

## 8. Shared Responsibility Model

The **Shared Responsibility Model** defines which security tasks are handled by Microsoft Azure and which remain the responsibility of the customer.

### How It Applies to a Storage Account (PaaS)

| Responsibility Area | Microsoft Azure (Provider) | Customer (Me) |
|---|---|---|
| **Physical Security** | ✅ Secures data centers, hardware | ❌ Not responsible |
| **Network Infrastructure** | ✅ Manages underlying network fabric | ❌ Not responsible |
| **Host OS / Virtualization** | ✅ Manages hypervisor and host OS | ❌ Not responsible |
| **Platform & Runtime** | ✅ Manages storage service platform | ❌ Not responsible |
| **Data Encryption (at rest)** | ✅ AES-256 encryption by default | ✅ Key management if using CMK |
| **Access Control (IAM/RBAC)** | ✅ Provides RBAC tools | ✅ Must configure roles correctly |
| **Data Classification** | ❌ Not Azure's responsibility | ✅ Must tag and classify sensitive data |
| **Network Access Rules** | ✅ Provides firewall/VNet tools | ✅ Must configure allowed IPs and VNets |
| **Application-Level Security** | ❌ Not Azure's responsibility | ✅ Must secure apps using the storage |
| **Compliance & Auditing** | ✅ Provides audit logs (Activity Log) | ✅ Must review and act on audit logs |

### IaaS vs PaaS vs SaaS Responsibility Comparison

| Layer | IaaS (VM) | PaaS (Storage) | SaaS (Office 365) |
|---|---|---|---|
| Physical & Network | Azure | Azure | Azure |
| Host OS | Azure | Azure | Azure |
| Guest OS / Runtime | **Customer** | Azure | Azure |
| Application | **Customer** | **Customer** | Azure |
| Data & Access | **Customer** | **Customer** | **Customer** |

**Key Takeaway:** PaaS reduces the customer's security surface significantly compared to IaaS, making it safer for teams without dedicated infrastructure management.

---

## 9. Cost Management & Billing

### 9.1 Accessing Cost Management
Navigated to **Cost Management + Billing** via the portal search bar:
- **Cost Analysis** section reviewed — shows spending trends, resource-level cost breakdown
- Current spend: **$4.49** (as shown in cost analysis screenshot)

### 9.2 Budget Alert Configuration
A budget was configured in the **Budgets** section with a **75% alert threshold** to ensure spending stays within Free Tier limits:

**Steps to configure a Budget with 75% threshold:**
1. Search `"Cost Management + Billing"` → click **"Budgets"** in the left menu
2. Click **"+ Add"**
3. Configure:
   - **Name:** `olamileye_budget`
   - **Reset period:** Monthly
   - **Budget amount:** $200 (covers Free Tier $200 credit)
4. Under **Alert conditions**:
   - **Alert type:** Actual cost
   - **% of budget:** `75` → triggers at **$150**
   - **Alert recipients (email):** `duduyemiolamileyeclement@gmail.com`
5. Click **"Create"**

This ensures an email notification is sent when 75% of the $200 budget ($150) is reached. The budget runs monthly and expires 31/05/2028, providing long-term spend visibility.

*Screenshot evidence: see `screenshots/05_budget_75_alert.png`*

*Cost Analysis screenshot: see `screenshots/03_cost_management.png`*

---

## 10. Formal Completion Checklist

The following checklist explicitly verifies that every required task for this assignment has been completed and evidenced.

### Account Setup
- [x] **Azure Free Tier account created** — email, phone (SMS), and payment card verified during signup (Section 2)
- [x] **Active subscription confirmed** — `Azure subscription 1` visible in portal (`screenshots/01_azure_dashboard.png`)
- [x] **MFA enabled** — Microsoft account MFA active via Microsoft Authenticator / SMS (Section 6.3)

### Portal Navigation
- [x] **Dashboard navigated** — Azure Portal home reviewed; left sidebar, top nav bar, and favourites explored
- [x] **Search bar used** — searched `"storage accounts"`, results categorised as Services / Marketplace / Documentation (`screenshots/06_portal_navigation.png`)
- [x] **Breadcrumbs explained** — hierarchical path navigation documented in Section 3.3
- [x] **Service blade menus explained** — left-side contextual menu documented in Section 3.4

### Dashboard Customisation
- [x] **Custom dashboard created** — `My Dashboard` created with pinned monitoring tiles (`screenshots/04_custom_dashboard.png`)
- [x] **Tiles pinned** — Cosmos DB latency and request metric tiles added and displayed

### Resource Group & Deployment
- [x] **Resource Group created** — `assignment-rg` provisioned in UK South (`screenshots/02_resource_group.png`)
- [x] **Region selected and justified** — UK South chosen; rationale documented in Section 5
- [x] **Storage Account deployed** — `mystaticdoc` (PaaS, West Europe, LRS) deployed successfully (`screenshots/07_storage_account.png`)

### Identity & Access Management
- [x] **Microsoft Entra ID accessed** — Roles and Administrators page reviewed
- [x] **RBAC roles reviewed** — Owner, Contributor, Reader roles documented (Section 6.2)
- [x] **Student role confirmed** — Global Administrator role visible (`screenshots/08_entra_id_rbac.png`)

### Cost Management & Billing
- [x] **Cost Analysis accessed** — $4.49 spend recorded (`screenshots/03_cost_management.png`)
- [x] **Budget created** — `olamileye_budget`, $200/month, monthly reset
- [x] **75% alert configured** — Alert triggers at $150 (75% of $200), email recipient set (`screenshots/05_budget_75_alert.png`)

### Documentation
- [x] **Shared Responsibility Model documented** — PaaS vs IaaS vs SaaS comparison table included (Section 8)
- [x] **Free Tier limits documented** — $200 credit, 12-month services, 5 GB storage (Section 2)
- [x] **All 8 screenshots referenced** — README screenshot index maps each file to its content
- [x] **Troubleshooting section included** — Section 11 covers common signup and deployment errors

---

## 11. Troubleshooting – Common Errors

The following errors were encountered or are commonly reported during Azure Free Tier setup and resource deployment.

### 11.1 Account Signup Errors

| Error | Cause | Fix |
|---|---|---|
| **"Your account cannot be verified"** | Phone number already used on another Azure account | Use a different phone number or contact Azure Support |
| **"Credit card was declined"** | Prepaid/virtual cards are not accepted | Use a standard Visa/Mastercard debit card linked to a bank account |
| **"This offer is not available in your country"** | Free Tier not available in certain regions | Select **Nigeria** as country during signup; ensure card is internationally enabled |
| **SMS verification code not received** | Network delay or incorrect country code | Wait 2 minutes and retry; ensure `+234` prefix is used for Nigerian numbers |
| **"Email is already associated with a Microsoft account"** | Existing account conflict | Sign in with the existing account instead of creating a new one |

### 11.2 Portal & Resource Deployment Errors

| Error | Cause | Fix |
|---|---|---|
| **"The subscription is not registered to use namespace 'Microsoft.Storage'"** | Resource provider not enabled | Go to **Subscription → Resource providers** → search `Microsoft.Storage` → click **Register** |
| **"Storage account name is already taken"** | Storage names are globally unique across all Azure tenants | Choose a different name (e.g. add your initials or a number: `mystaticdoc01`) |
| **"Deployment failed – QuotaExceeded"** | Free Tier compute quota reached (750 hrs/month for B1s VMs) | Delete unused VMs or wait until the quota resets at the start of the next month |
| **"AuthorizationFailed" when creating a Resource Group** | Insufficient permissions on the subscription | Ensure you are signed in as the account **Owner** (the account that created the subscription) |
| **Dashboard tiles not loading / showing errors** | Resource was deleted or access revoked | Remove the broken tile from the dashboard and re-pin it from the relevant resource page |
| **Budget alert email not received** | Incorrect email address entered, or spam filter | Check junk/spam folder; verify recipient email in **Cost Management → Budgets → Edit** |

### 11.3 General Tips

- Always check the **Notifications bell** (top right) after any deployment — it shows success or failure with a detailed error message.
- Use the **Activity Log** on any resource blade to see a full history of operations and error codes.
- If the portal becomes unresponsive, clear your browser cache or try a different browser (Microsoft Edge is recommended for best compatibility).

---

*Report prepared as part of the Azure Cloud Computing Foundations assignment.*
