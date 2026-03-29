# 🔐 AZ-500: Azure Security Engineer Labs
### by Kemunto Faith Ogwoka | Cloud Security Specialist Trainee


## 👩‍💻 About This Repository

This repository documents my hands-on lab work completed as part of the **Microsoft AZ-500: Azure Security Engineer Associate** training through the **Cybershujaa Cloud Security Specialist Programme** (Microsoft ADC).

Each lab demonstrates real-world Azure security configurations, covering identity management, network protection, data security, and cloud-native security tools. All labs were completed in live Azure environments with full documentation and screenshots.

---

## 📋 Lab Overview

| # | Lab Title | Key Skills |
|---|-----------|------------|
| 01 | [Role-Based Access Control (RBAC)](#lab-01---role-based-access-control) | Azure AD, Users, Groups, IAM |
| 02 | [Security for Virtual Networks](#lab-02---security-for-virtual-networks) | NSG, ASG, Virtual Networks |
| 03 | [Azure Firewall](#lab-03---azure-firewall) | Firewall Rules, Route Tables, DNS |
| 04 | [Configuring and Securing ACR & AKS](#lab-04---configuring-and-securing-acr--aks) | Containers, Kubernetes, Docker |
| 05 | [Securing Azure SQL Database](#lab-05---securing-azure-sql-database) | Defender for SQL, Data Classification, Auditing |
| 06 | [Service Endpoints and Securing Storage](#lab-06---service-endpoints-and-securing-storage) | Storage Security, Service Endpoints, NSG |
| 07 | [Key Vault — Always Encrypted](#lab-07---key-vault--always-encrypted) | Key Vault, Always Encrypted, App Registration, SQL |
| 08 | [Azure Monitor, Defender for Cloud, JIT Access & Microsoft Sentinel](#lab-08---azure-monitor-defender-for-cloud-jit-access--microsoft-sentinel) | Monitor, DCR, Defender, JIT, Sentinel, Playbooks |

---

## 🧪 Lab Details

### Lab 01 - Role-Based Access Control
**Objective:** Demonstrate how Azure users, groups, and RBAC are used to control access to resources.

**What I did:**
- Created user accounts (Joseph Price, Isabel Garcia, Dylan Williams) using the Azure Portal, PowerShell, and Azure CLI
- Created security groups: Senior Admins, Junior Admins, and Service Desk
- Assigned the **Virtual Machine Contributor** role to the Service Desk group on a resource group
- Verified access assignments using the IAM Check Access feature

**Tools Used:** Azure Portal · PowerShell · Azure CLI · Microsoft Entra ID

---

### Lab 02 - Security for Virtual Networks
**Objective:** Configure virtual network infrastructure with Application Security Groups and Network Security Groups.

**What I did:**
- Created a Virtual Network with a custom subnet (10.0.0.0/16)
- Created two Application Security Groups: `myAsgWebServers` and `myAsgMgmtServers`
- Created and configured a Network Security Group with inbound rules for HTTP/HTTPS (ports 80/443) and RDP (port 3389)
- Deployed two Virtual Machines and associated their NICs to the correct ASGs
- Tested network traffic filtering by connecting via RDP and verifying web server accessibility

**Tools Used:** Azure Portal · Virtual Networks · NSG · ASG · RDP · IIS

---

### Lab 03 - Azure Firewall
**Objective:** Deploy and configure an Azure Firewall to control inbound and outbound traffic.

**What I did:**
- Deployed an Azure Firewall using an ARM template
- Created a default route table (`Firewall-route`) to route traffic through the firewall
- Configured an **Application Rule** to allow outbound access to `www.bing.com`
- Configured a **Network Rule** to allow DNS traffic on port 53
- Configured custom DNS servers on the VM network interface
- Tested the firewall by verifying Bing access was allowed and Microsoft.com was blocked

**Tools Used:** Azure Firewall · Route Tables · ARM Templates · RDP · DNS · Application & Network Rules

---

### Lab 04 - Configuring and Securing ACR & AKS
**Objective:** Deploy and secure containerized applications using Azure Container Registry and Azure Kubernetes Service.

**What I did:**
- Created an **Azure Container Registry (ACR)** using Bash in Cloud Shell
- Built a Dockerfile for an Nginx-based image and pushed it to ACR
- Deployed an **Azure Kubernetes Service (AKS)** cluster
- Granted the AKS cluster the `acrpull` role to access ACR securely
- Deployed both an **external-facing** and **internal-facing** Nginx service using YAML manifests
- Verified external access via public IP and internal access via pod-to-pod communication

**Tools Used:** Azure Container Registry · Azure Kubernetes Service · Docker · Bash · kubectl · YAML · Nginx

---

### Lab 05 - Securing Azure SQL Database
**Objective:** Implement security features for Azure SQL including threat protection, data classification, and auditing.

**What I did:**
- Deployed an Azure SQL Database using an ARM template
- Enabled **Microsoft Defender for SQL** and reviewed vulnerability assessment and threat protection settings
- Performed **Data Discovery & Classification** — identified and classified 15 columns with sensitivity labels for GDPR compliance
- Configured **server-level and database-level auditing** with a 5-day retention policy
- Ran queries in the Query Editor and reviewed audit logs showing authentication and batch events

**Tools Used:** Azure SQL · Microsoft Defender for Cloud · Data Classification · Auditing · PowerShell · Query Editor

---

### Lab 06 - Service Endpoints and Securing Storage
**Objective:** Secure Azure file shares using service endpoints, NSGs, and storage network rules.

**What I did:**
- Created a Virtual Network with two subnets: `Public` (10.0.0.0/24) and `Private` (10.0.1.0/24)
- Configured a **Storage Service Endpoint** on the Private subnet
- Created `myNsgPrivate` with rules to allow storage access and deny internet outbound
- Created `myNsgPublic` with RDP access only
- Created a Storage Account with a file share and restricted access to the Private subnet only
- Deployed VMs in both subnets and tested storage connectivity:
  - ✅ Private VM: successfully mapped Z: drive to the file share
  - ❌ Public VM: access denied as expected

**Tools Used:** Virtual Networks · Service Endpoints · NSG · Azure Storage · File Shares · PowerShell · RDP

---

### Lab 07 - Key Vault & Always Encrypted
**Objective:** Implement secure data protection using Azure Key Vault and SQL Always Encrypted to safeguard sensitive database columns.

**What I did:**
- Deployed an Azure VM pre-installed with Visual Studio 2019 and SQL Server Management Studio using an ARM template
- Created an **Azure Key Vault** using PowerShell and configured access policies
- Added a software-protected **RSA 2048 key** (`MyLabKey`) and a **secret** (`SQLPassword`) to the vault
- Registered a client application (`sqlApp`) in **Microsoft Entra ID** and generated a client secret (Key1)
- Granted the registered app Key Vault permissions: `get`, `wrapKey`, `unwrapKey`, `sign`, `verify`, `list`
- Retrieved the **ADO.NET connection string** for the Azure SQL `medical` database
- Connected to the SQL database via **SQL Server Management Studio**, created a `Patients` table and encrypted two columns:
  - `SSN` — **Deterministic** encryption
  - `BirthDate` — **Randomized** encryption
- Used the **Always Encrypted wizard** to store Column Master Keys and Column Encryption Keys in Key Vault
- Built a **C# Console Application** in Visual Studio 2019, installed required NuGet packages, and configured it with the connection string, App Client ID, and Key1
- Ran the app to load patient data and queried the database — confirmed SSN and BirthDate columns were **fully encrypted at rest** but decryptable by the authorized app

**Tools Used:** Azure Key Vault · Always Encrypted · Microsoft Entra ID (App Registration) · Azure SQL · SQL Server Management Studio · Visual Studio 2019 · C# · PowerShell · ARM Templates

---

### Lab 08 - Azure Monitor, Defender for Cloud, JIT Access & Microsoft Sentinel
**Objective:** Implement end-to-end Azure security monitoring and threat detection using Azure Monitor, Microsoft Defender for Cloud, Just-in-Time VM access, and Microsoft Sentinel.

This lab covered four interconnected security scenarios:

**Part 1 — Azure Monitor: Log Analytics & Data Collection Rule**
- Deployed an Azure VM (`myVM`) using PowerShell with encryption at host enabled
- Created a **Log Analytics Workspace** to centralize security and performance logs
- Created an **Azure Storage Account** for log archiving
- Configured a **Data Collection Rule (DCR)** with Performance Counters as the data source and the Log Analytics Workspace as the destination

**Part 2 — Microsoft Defender for Cloud: Enhanced Security for Servers**
- Navigated to **Environment Settings** in Microsoft Defender for Cloud
- Expanded **Cloud Workload Protection (CWP)** and enabled **Defender for Servers Plan 2**
- Reviewed advanced threat protection settings and plan details

**Part 3 — Just-in-Time (JIT) VM Access**
- Enabled **Just-in-Time VM Access** on `myVM` directly from the VM Configuration blade
- Reviewed default JIT settings: RDP port 3389, max access 3 hours, any source IP
- Edited port configurations and saved updated JIT policy
- Submitted an **access request** through the VM Connect page to demonstrate JIT workflow in action

**Part 4 — Microsoft Sentinel: SIEM & SOAR**
- Onboarded **Microsoft Sentinel** and connected it to the existing Log Analytics Workspace
- Installed the **Azure Activity** content hub connector and configured it via Azure Policy Assignment to stream diagnostic logs
- Created a remediation task to enforce log streaming across the subscription
- Created a **Scheduled Analytics Rule** — "Suspicious number of resource creation or deployment" — using the Azure Activity data connector
- Deployed a **Logic App Playbook** (`Change-Incident-Severity`) using an ARM template and configured connection authentication
- Created a **Custom Scheduled Alert Rule** with a 5-minute query interval and linked the playbook as an **Automated Response** via an Automation Rule
- Triggered a real incident by **removing the JIT policy** — confirmed the deletion appeared in the Activity Log
- Verified that **Microsoft Sentinel** detected the incident and displayed it with medium/high severity on the dashboard

**Tools Used:** Azure Monitor · Log Analytics · Data Collection Rules · Microsoft Defender for Cloud · Just-in-Time VM Access · Microsoft Sentinel · Logic Apps · Azure Policy · ARM Templates · PowerShell · Content Hub

---

## 🛠️ Technologies & Tools

```
☁️  Microsoft Azure          🔐  Microsoft Defender for Cloud
🖥️  Azure Virtual Machines   🐳  Docker & Azure Container Registry
🌐  Azure Virtual Networks   ☸️  Azure Kubernetes Service (AKS)
🔥  Azure Firewall           🗄️  Azure SQL Database
📦  Azure Storage            💻  PowerShell & Azure CLI (Bash)
👥  Microsoft Entra ID       📊  Log Analytics & Azure Monitor
🔑  Azure Key Vault          🔒  Always Encrypted (SQL)
💻  Visual Studio 2019       🛡️  SQL Server Management Studio
🕵️  Microsoft Sentinel       📋  Data Collection Rules (DCR)
⏱️  Just-in-Time VM Access   🤖  Logic Apps & Playbooks
```

---

## 📜 Certifications & Training

- 🏅 **Microsoft Certified: Azure Security Engineer Associate (AZ-500)** — March 2026
- 🏅 **Microsoft Certified: Security, Compliance & Identity Fundamentals (SC-900)** — June 2025
- 🎓 **Cloud Security Specialist Trainee** — Cybershujaa / Microsoft ADC (Apr–Aug 2025)
- 🎓 **Cybersecurity Analyst Trainee** — Cybershujaa (Sep–Dec 2024)
- 🎓 **Ethical Hacker** — Cisco Netacad Academy (Jan 2025)

---

## 📬 Connect With Me

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Faith%20Ogwoka-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](http://www.linkedin.com/in/faith-ogwoka)
[![Email](https://img.shields.io/badge/Email-faithogwoka@gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:faithogwoka@gmail.com)

---

> *"Security is not a product, but a process." — Building one lab at a time.*

