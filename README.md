# 🔐 AZ-500: Azure Security Engineer Labs
### by Kemunto Faith Ogwoka | Cloud Security Specialist Trainee

![Azure Security](https://img.shields.io/badge/Microsoft%20Azure-Security-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white)
![AZ-500](https://img.shields.io/badge/AZ--500-Certified-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Cybershujaa](https://img.shields.io/badge/Cybershujaa-Trainee-green?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

---

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

## 🛠️ Technologies & Tools

```
☁️  Microsoft Azure          🔐  Microsoft Defender for Cloud
🖥️  Azure Virtual Machines   🐳  Docker & Azure Container Registry
🌐  Azure Virtual Networks   ☸️  Azure Kubernetes Service (AKS)
🔥  Azure Firewall           🗄️  Azure SQL Database
📦  Azure Storage            💻  PowerShell & Azure CLI (Bash)
👥  Microsoft Entra ID       📊  SIEM & Audit Logging
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
