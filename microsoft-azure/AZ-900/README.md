# AZ-900 · Microsoft Azure Fundamentals — from zero to certified

> **Who this is for:** anyone who has never used the cloud. No coding, no Azure account needed to start.
> **Time budget:** **~18 hours** over 2–3 weeks (about 1 hour a day + one longer weekend session).
> **Interactive practice:** [`AZ-900-trainer.html`](AZ-900-trainer.html) — download it and open it in your browser.

| Exam fact | Value |
|---|---|
| Format | ~40–60 questions, 45 minutes of answering time |
| Passing score | 700 / 1000 |
| Question types | Single choice, multiple choice, yes/no statements, drop-down "complete the sentence" |
| Prerequisites | None |
| Skills outline | Version of **14 January 2026** (same three domains and weights as in this guide) |
| Validity | Fundamentals certifications **don't expire** |
| Official page | [AZ-900 study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-900) — always check it for the current skills outline |

---

## Contents

1. [Study plan (18 h)](#1-study-plan-18-hours)
2. [Domain 1 — Cloud concepts (25–30%)](#2-domain-1--cloud-concepts-2530)
3. [Domain 2 — Azure architecture and services (35–40%)](#3-domain-2--azure-architecture-and-services-3540)
4. [Domain 3 — Management and governance (30–35%)](#4-domain-3--azure-management-and-governance-3035)
5. [One-page cheatsheet](#5-one-page-cheatsheet)
6. [Exam-day tactics](#6-exam-day-tactics)

---

## 1. Study plan (18 hours)

| Day | Hours | What you do | Done when you can… |
|---|---|---|---|
| 1 | 1.5 h | Read §2.1–2.3 (cloud model, shared responsibility, deployment models) | explain IaaS / PaaS / SaaS with the pizza analogy |
| 2 | 1.5 h | Read §2.4–2.5 (benefits, CapEx vs OpEx) + trainer: Domain 1 | score 80%+ on Domain 1 in the trainer |
| 3 | 1.5 h | Read §3.1 (regions, availability zones, resource hierarchy) | draw tenant → management group → subscription → resource group → resource |
| 4 | 2 h | Read §3.2 (compute) + free Azure account: create a VM, then delete it | say when to use a VM vs App Service vs Functions vs containers |
| 5 | 1.5 h | Read §3.3 (networking) | explain VNet, peering, VPN Gateway, ExpressRoute, DNS |
| 6 | 2 h | Read §3.4 (storage) + upload a file to a storage account | pick the right access tier and redundancy option |
| 7 | 1.5 h | Read §3.5 (identity & security) + trainer: Domain 2 | tell authentication from authorization; explain MFA, Conditional Access, Zero Trust |
| 8 | 1.5 h | Read §4.1 (cost management) | name 3 things that affect cost and 2 tools to estimate it |
| 9 | 1.5 h | Read §4.2–4.3 (governance, management tools, monitoring) + trainer: Domain 3 | choose between Policy, RBAC, locks, tags |
| 10 | 1 h | Re-read the [cheatsheet](#5-one-page-cheatsheet), drill **Weak skills** | every domain is green in the trainer |
| 11 | 1 h | **Exam simulation** in the trainer + Microsoft's free practice assessment | 800+ in the simulation, 80%+ on the official assessment |
| 12 | 0.5 h | Light review of the cheatsheet only | — book the exam |

> 💡 **Free resources:** the [Microsoft Learn AZ-900 learning path](https://learn.microsoft.com/en-us/credentials/certifications/azure-fundamentals/) (free), the official **practice assessment** on the same page, and a [free Azure account](https://azure.microsoft.com/free/) for hands-on clicks. Watch out for virtual-training-day events: Microsoft regularly offers free exam vouchers to attendees.

---

## 2. Domain 1 — Cloud concepts (25–30%)

### 2.1 What is cloud computing?

Cloud computing = **renting computing resources (servers, storage, networking, software) over the internet, and paying only for what you use**, instead of buying and running your own data center.

Think of electricity: you don't build a power plant, you plug in and pay the bill. The cloud does the same for IT.

### 2.2 The shared responsibility model

Who secures what? It depends on how much you rent.

| Responsibility | On-premises | IaaS | PaaS | SaaS |
|---|---|---|---|---|
| Information & data, devices, accounts & identities | **You** | **You** | **You** | **You** |
| Applications | You | You | Shared | Microsoft |
| Operating system, network controls | You | You | Microsoft | Microsoft |
| Physical hosts, network, data center | You | Microsoft | Microsoft | Microsoft |

> ⚠️ **Exam trap:** your **data, devices, accounts and identities are always your responsibility**, even in SaaS. The physical data center is **always Microsoft's** in the cloud.

### 2.3 Service models — the pizza analogy 🍕

| Model | You manage | Provider manages | Pizza version | Azure examples |
|---|---|---|---|---|
| **IaaS** — Infrastructure as a Service | OS, runtime, apps, data | Hardware, network, virtualization | Buy a frozen pizza, bake it in your oven | Virtual Machines, VNets, managed disks |
| **PaaS** — Platform as a Service | Apps and data | Everything below the app | Pizza delivery: you just set the table | App Service, Azure SQL Database, Azure Functions |
| **SaaS** — Software as a Service | Your data and users | The whole application | Eat at the restaurant | Microsoft 365, Outlook, Dynamics 365 |

**Rule of thumb:** the more control you need (custom OS, legacy software) → IaaS. The less you want to manage → SaaS.

### 2.4 Deployment models

| Model | What it is | Typical reason |
|---|---|---|
| **Public cloud** | Resources owned by a provider, shared by many customers, reached over the internet | No upfront cost, scale fast |
| **Private cloud** | Cloud resources used by one organization only (on-premises or hosted) | Full control, strict regulation |
| **Hybrid cloud** | Public + private connected together | Keep sensitive data on-premises, burst to the cloud |
| **Multi-cloud** | Several public cloud providers at once | Avoid lock-in, use best service of each |

**Azure Arc** manages servers, Kubernetes and databases **outside Azure** (on-premises or other clouds) as if they were Azure resources. **Azure VMware Solution** runs VMware workloads in Azure.

### 2.5 Benefits of the cloud (learn the vocabulary — the exam tests the exact words)

| Benefit | Meaning in one line |
|---|---|
| **High availability** | The service stays up; measured by the **SLA** (e.g. 99.9% uptime) |
| **Scalability** | Add resources to handle more load. **Vertical** = bigger machine (scale up); **horizontal** = more machines (scale out) |
| **Elasticity** | Scale **automatically** up *and down* with demand |
| **Reliability** | Recover from failures; resources spread across regions/zones |
| **Predictability** | *Performance* predictability (autoscale, load balancing) and *cost* predictability (pricing calculator, budgets) |
| **Security** | Choose your control level; built-in protection like DDoS mitigation |
| **Governance** | Templates and policies keep resources compliant |
| **Manageability** | Manage *of* the cloud (autoscale, monitoring) and *in* the cloud (portal, CLI, APIs) |

### 2.6 Consumption-based model: CapEx vs OpEx

- **CapEx (capital expenditure):** big upfront spending on physical assets (buy servers, build a data center). Value depreciates.
- **OpEx (operational expenditure):** pay as you go for services, deducted in the same year. **The cloud is OpEx.**
- **Consumption-based model:** no upfront cost, pay only for what you use, stop paying when you stop using.

> ✅ **Check yourself:** A start-up wants to avoid buying servers and pay monthly based on usage. Which expenditure model? → **OpEx**.

---

## 3. Domain 2 — Azure architecture and services (35–40%)

### 3.1 Core architecture

**Physical**

- **Region** — a geographic area with one or more data centers (e.g. *France Central*). Choose the region close to your users, for latency and data-residency laws.
- **Availability zone** — physically separate data centers **inside a region**, with independent power, cooling and network. Spread VMs across zones to survive a data-center failure.
- **Region pair** — two regions in the same geography (≥ 300 miles apart where possible), updated one at a time and prioritized for recovery during a large outage.
- **Sovereign regions** — isolated instances of Azure for governments (e.g. Azure Government in the US, Azure operated by 21Vianet in China).

**Logical — the resource hierarchy (memorize it top-down):**

```
Microsoft Entra tenant
└── Management groups      (organize subscriptions; policies & RBAC inherit down)
    └── Subscriptions      (billing + access boundary)
        └── Resource groups (logical folder; a resource lives in exactly ONE group)
            └── Resources   (VM, storage account, database…)
```

> ⚠️ **Exam traps:** resource groups **cannot be nested**. Deleting a resource group **deletes everything in it**. Settings applied at a higher level are **inherited** by everything below.

### 3.2 Compute — "where does my code run?"

| Service | Pick it when… | Model |
|---|---|---|
| **Virtual Machines** | You need full control of the OS or must "lift and shift" an existing server | IaaS |
| **Virtual Machine Scale Sets** | Many identical, load-balanced VMs that autoscale | IaaS |
| **Availability sets** | Spread VMs over update and fault domains inside one data center | IaaS |
| **Azure Virtual Desktop** | Windows desktops and apps streamed to users from the cloud | Desktop as a service |
| **Containers** — Azure Container Instances (ACI) | Run one container quickly, no orchestration | PaaS |
| **Azure Container Apps** | Serverless containers with autoscaling and microservices features | PaaS |
| **Azure Kubernetes Service (AKS)** | Orchestrate many containers at scale | Managed Kubernetes |
| **Azure Functions** | Small pieces of code triggered by events, pay per execution | **Serverless** |
| **App Service** | Host web apps, REST APIs, mobile back ends without managing servers | PaaS |

**Container vs VM:** a VM virtualizes the *hardware* (each VM has its own OS); a container virtualizes the *OS* (lightweight, starts in seconds).

### 3.3 Networking

| Service | One-line purpose |
|---|---|
| **Virtual Network (VNet)** | Your private network in Azure; split into **subnets** |
| **VNet peering** | Connect two VNets privately over the Microsoft backbone (can be in different regions) |
| **VPN Gateway** | Encrypted tunnel **over the public internet** (site-to-site, point-to-site) |
| **ExpressRoute** | **Private** dedicated connection to Azure, **does not go over the internet**; more reliable, faster, more expensive |
| **Azure DNS** | Host your DNS domains in Azure |
| **Public / private endpoints** | Public = reachable from internet; private endpoint = a service gets a private IP inside your VNet |

> ✅ **Check yourself:** A bank needs a connection to Azure that never crosses the public internet. → **ExpressRoute**.

### 3.4 Storage

**Storage account services**

| Service | Stores | Example |
|---|---|---|
| **Blob storage** | Unstructured objects (files, images, video, backups) | Website images |
| **Azure Files** | Managed file shares (SMB/NFS), mountable like a network drive | Replace an on-prem file server |
| **Queue storage** | Messages between app components | Order-processing queue |
| **Table storage** | NoSQL key/attribute data | Simple user profiles |
| **Disk storage** | Disks attached to VMs | VM OS disk |

**Blob access tiers** (cheaper storage ↔ more expensive access):

| Tier | Use for | Note |
|---|---|---|
| **Hot** | Frequently accessed data | Highest storage cost, lowest access cost |
| **Cool** | Infrequent access, kept ≥ 30 days | |
| **Cold** | Rarely accessed, kept ≥ 90 days | |
| **Archive** | Almost never accessed, kept ≥ 180 days | **Offline**: must be *rehydrated* (hours) before reading |

**Redundancy** (how many copies, where):

| Option | Copies | Protects against |
|---|---|---|
| **LRS** — locally redundant | 3 in one data center | Disk/server failure |
| **ZRS** — zone-redundant | 3 across availability zones | Data-center failure |
| **GRS** — geo-redundant | LRS + 3 more in the paired region | Regional disaster |
| **GZRS** — geo-zone-redundant | ZRS + 3 more in the paired region | Both |
| **RA-GRS / RA-GZRS** | Same as above + **read** access to the secondary region | Read during an outage |

**Moving data:** **AzCopy** (command line), **Azure Storage Explorer** (GUI), **Azure File Sync** (sync on-prem file servers with Azure Files), **Azure Migrate** (migrate servers), **Azure Data Box** (a physical device shipped to you for terabytes of data when the network is too slow).

### 3.5 Identity, access and security

- **Authentication (AuthN)** = *who are you?* · **Authorization (AuthZ)** = *what are you allowed to do?*
- **Microsoft Entra ID** (formerly Azure Active Directory) — the cloud identity service: users, groups, apps, sign-in.
- **Single sign-on (SSO)** — one identity for many apps.
- **Multifactor authentication (MFA)** — something you **know** (password) + something you **have** (phone) + something you **are** (fingerprint).
- **Passwordless** — Windows Hello, Microsoft Authenticator, FIDO2 keys.
- **Conditional Access** — *if* (user, location, device, risk) *then* (allow, require MFA, block).
- **External identities (B2B)** — let partners sign in with their own accounts.
- **Microsoft Entra Domain Services** — managed domain join, LDAP, Kerberos without running domain controllers.
- **Azure RBAC** — give *least privilege* roles (Owner, Contributor, Reader…) at a scope.
- **Zero Trust** — *never trust, always verify*: verify explicitly, use least privilege, assume breach.
- **Defense in depth** — layers: physical → identity & access → perimeter → network → compute → application → data.
- **Microsoft Defender for Cloud** — security posture management and threat protection, for Azure, on-prem and other clouds.

---

## 4. Domain 3 — Azure management and governance (30–35%)

### 4.1 Cost management

**What changes the bill:** resource type and size, consumption, region, **bandwidth (data leaving Azure — egress — is charged; data entering is free)**, reserved instances, savings plans, and the **Azure Hybrid Benefit** (reuse your existing Windows Server/SQL Server licenses).

| Tool | Answers the question |
|---|---|
| **Pricing calculator** | "How much will *this new solution* cost per month?" |
| **TCO calculator** | "How much will I *save* moving from on-premises to Azure?" |
| **Cost Management + Billing** | "What am I spending *now*?" — analysis, **budgets**, **alerts** |
| **Tags** | "Which department/project does this resource belong to?" (name:value pairs used for cost reports) |

### 4.2 Governance and compliance

| Tool | What it does | Memory hook |
|---|---|---|
| **Azure Policy** | Enforces rules on **resource properties** (e.g. "only allow VMs in EU regions", "require a tag") | Rules for **what** can be created |
| **Azure RBAC** | Controls **who** can do **what** | Rules for **who** |
| **Resource locks** | **CanNotDelete** or **ReadOnly** — prevent accidental deletion/change, *even for Owners* | Safety catch |
| **Microsoft Purview** | Data governance: discover, classify and track data across your estate | Data catalog |
| **Service Trust Portal** | Microsoft's compliance reports and audit documents | Proof for auditors |

> ⚠️ **Exam trap:** Policy ≠ RBAC. A *Policy* can block the creation of a VM in the US **for everyone**; *RBAC* decides **whether a user can create VMs at all**.

### 4.3 Managing and deploying resources

| Tool | Use |
|---|---|
| **Azure portal** | Web UI |
| **Azure Cloud Shell** | Browser-based shell (Bash or PowerShell), no install |
| **Azure CLI / Azure PowerShell** | Scripting from your machine |
| **Azure Arc** | Manage non-Azure resources from Azure |
| **Infrastructure as Code** — **ARM templates** (JSON) and **Bicep** (simpler language that compiles to ARM) | Repeatable, declarative deployments |

### 4.4 Monitoring

| Tool | Question it answers |
|---|---|
| **Azure Advisor** | "How can I improve **cost, security, reliability, performance, operational excellence**?" (free recommendations) |
| **Azure Service Health** | "Is **Azure itself** having a problem that affects me?" (outages, planned maintenance) |
| **Azure Monitor** | Collect and analyze **metrics and logs** from your resources |
| **Log Analytics** | Query logs with KQL (part of Azure Monitor) |
| **Azure Monitor alerts** | Notify or act when a metric/log condition is met |
| **Application Insights** | Monitor **application** performance and usage (APM) |

---

## 5. One-page cheatsheet

| If the question says… | The answer is usually… |
|---|---|
| "pay only for what you use", "no upfront cost" | Consumption-based model / **OpEx** |
| "full control of the operating system" | **IaaS** (Virtual Machines) |
| "focus only on code, no server management" | **PaaS** (App Service) |
| "run code when an event happens, pay per execution" | **Azure Functions** (serverless) |
| "private connection, not over the internet" | **ExpressRoute** |
| "encrypted connection over the internet" | **VPN Gateway** |
| "survive a data-center failure in one region" | **Availability zones** / **ZRS** |
| "survive a whole-region disaster" | **Region pairs** / **GRS / GZRS** |
| "rarely accessed data, lowest storage cost, can wait hours" | **Archive tier** |
| "move 80 TB with a slow internet link" | **Azure Data Box** |
| "who can do what" | **Azure RBAC** |
| "only allow resources in certain regions" | **Azure Policy** |
| "stop anyone from deleting this resource" | **Resource lock** (CanNotDelete) |
| "estimate savings vs. our data center" | **TCO calculator** |
| "estimate monthly cost of a new deployment" | **Pricing calculator** |
| "recommendations to reduce cost / improve security" | **Azure Advisor** |
| "is there an Azure outage in my region?" | **Azure Service Health** |
| "verify explicitly, least privilege, assume breach" | **Zero Trust** |
| "password + phone code" | **MFA** |
| "require MFA only when signing in from outside the office" | **Conditional Access** |
| "manage on-prem servers and other clouds from Azure" | **Azure Arc** |

## 6. Exam-day tactics

- Read the **last sentence first** — it tells you what is actually asked.
- Words like *always*, *never*, *only* usually make a statement **false** in yes/no questions.
- When two answers look right, choose the one that needs **the least management effort** — fundamentals exams love PaaS/SaaS answers.
- You can't lose points by guessing: **never leave a question blank**.

---

## 7. All the official resources

| Resource | Link | Why use it |
|---|---|---|
| Certification page (schedule, free practice assessment) | [Azure Fundamentals](https://learn.microsoft.com/en-us/credentials/certifications/azure-fundamentals/) | The free official practice assessment is the best predictor of your score |
| Study guide (skills measured + change log) | [AZ-900 study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-900) | The exact list of what can be asked |
| Free self-paced course | [AZ-900T00 on Microsoft Learn](https://learn.microsoft.com/en-us/training/courses/az-900t00) | Official modules with knowledge checks |
| Exam sandbox | [aka.ms/examdemo](https://aka.ms/examdemo) | Click through the real exam interface before the day |
| Exam duration and experience | [Exam duration](https://learn.microsoft.com/en-us/credentials/support/exam-duration-exam-experience) | Timing, accommodations, online vs test center |
| Free Azure account | [azure.microsoft.com/free](https://azure.microsoft.com/free/) | Hands-on practice with free credits |
| Pricing calculator / TCO calculator | [Pricing calculator](https://azure.microsoft.com/pricing/calculator/) · [TCO calculator](https://azure.microsoft.com/pricing/tco/calculator/) | Open them once — they're exam topics |
| Microsoft Virtual Training Days | [events.microsoft.com/mvtd](https://events.microsoft.com/en-us/mvtd) | Free live training, often with a **free exam voucher** |

---

<sub>Unofficial study material, not affiliated with or endorsed by Microsoft. Azure changes often: when this guide and Microsoft Learn disagree, trust Microsoft Learn. Found a mistake? Open an issue or a pull request.</sub>
