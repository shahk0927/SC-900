# SC-900: Microsoft Security, Compliance, and Identity Fundamentals - Master Study Guide

This repository contains a deep-dive study guide for the **SC-900** exam. Unlike standard definitions, this guide focuses on the *nuance*, the *differences between similar tools*, and the specific scenarios Microsoft tests on.

---

## 📚 Table of Contents
1. [Describe the Concepts of Security, Compliance, and Identity (10–15%)](#1-describe-the-concepts-of-security-compliance-and-identity-1015)
2. [Describe the Capabilities of Microsoft Entra (25–30%)](#2-describe-the-capabilities-of-microsoft-entra-2530)
3. [Describe the Capabilities of Microsoft Security Solutions (35–40%)](#3-describe-the-capabilities-of-microsoft-security-solutions-3540)
4. [Describe the Capabilities of Microsoft Compliance Solutions (20–25%)](#4-describe-the-capabilities-of-microsoft-compliance-solutions-2025)
5. [Top "Gotcha" Scenarios (Crucial Differences)](#5-top-gotcha-scenarios-crucial-differences)
6. [Essential Acronyms Cheat Sheet](#6-essential-acronyms-cheat-sheet)

---

## 1. Describe the Concepts of Security, Compliance, and Identity (10–15%)

### Security Methodologies & Core Concepts

| Concept | Deep-Dive Description & Exam Nuance |
|---|---|
| **Shared Responsibility Model** | Defines who manages what as you move to the cloud. <br/> &bull; **On-Prem:** You manage everything (Hardware to Data). <br/> &bull; **IaaS:** MS manages physical hardware (Power, Cooling, Network cables). You manage OS, Patching, Apps, Data. <br/> &bull; **PaaS:** MS manages hardware + OS/Runtime. You manage Apps + Data. <br/> &bull; **SaaS:** MS manages everything up to the app. <br/> **CRITICAL:** In *all* models, you are always responsible for **Data**, **Endpoints (Devices)**, and **Identity (Accounts)**. |
| **Defense-in-Depth** | The "Layered" approach (Onion model). If one layer fails, the next stops the attack. <br/> **Layers:** Physical -> Identity & Access -> Perimeter -> Network -> Compute -> Application -> Data. <br/> *Exam Tip:* **Identity** is now considered the "Primary Perimeter" in cloud computing, replacing the traditional network firewall. |
| **Zero Trust Model** | Stop assuming traffic inside your network is safe. <br/> **The 3 Guiding Principles (Memorize these):** <br/> 1. **Verify Explicitly:** Always authenticate/authorize based on all data points (User, Location, Device). <br/> 2. **Use Least Privilege:** Limit access with Just-In-Time (JIT) and Just-Enough-Access (JEA). <br/> 3. **Assume Breach:** Minimize blast radius, segment networks, use encryption. |
| **CIA Triad** | &bull; **Confidentiality:** Keeping data secret (Encryption). <br/> &bull; **Integrity:** Keeping data accurate/unchanged (Hashing). <br/> &bull; **Availability:** Keeping data accessible (DDoS protection, Redundancy). |

### Encryption & Hashing

| Term | Description |
|---|---|
| **Encryption** | A **two-way** function to hide data. <br/> &bull; **At Rest:** Data on disk/DB (BitLocker, TDE). <br/> &bull; **In Transit:** Data moving over the network (HTTPS/TLS). |
| **Hashing** | A **one-way** function used for **Data Integrity**. <br/> It converts text into a unique fixed-length string (hash). If you change one letter in a file, the hash changes completely. It proves the file hasn't been tampered with. *Note: Hashing is NOT for hiding data.* |

---

## 2. Describe the Capabilities of Microsoft Entra (25–30%)

### Microsoft Entra ID (formerly Azure AD)

| Feature | Description |
|---|---|
| **Entra ID vs. Active Directory** | &bull; **Active Directory (AD):** On-Prem, hierarchical (OUs), uses Kerberos/NTLM. <br/> &bull; **Entra ID:** Cloud, flat structure, uses HTTP/REST/OAUTH. |
| **Identity Types** | &bull; **User:** A person (Employee/Guest). <br/> &bull; **Service Principal:** An identity used by an **application** to access resources (avoiding hardcoded credentials). <br/> &bull; **Managed Identity:** A special Service Principal managed by Azure. Eliminates the need for developers to manage secrets/passwords in code. Used for Azure-to-Azure comms (e.g., VM talking to SQL). |
| **Hybrid Identity** | &bull; **Password Hash Sync:** Simplest. Copies password hash to cloud. <br/> &bull; **Pass-through Auth:** Validates password against on-prem AD directly (agent required). <br/> &bull; **Federation (AD FS):** Redirects user to on-prem server to login. |
| **External Identities** | &bull; **B2B (Business to Business):** Guest users from other companies accessing your resources. <br/> &bull; **B2C (Business to Consumer):** Customers using Facebook/Google/Email to log into your customer-facing app. |

### Authentication & Access Management

| Capability | Description |
|---|---|
| **MFA (Multi-Factor Auth)** | Requires **2 of 3** distinct factors: <br/> 1. Something you **Know** (Password/PIN). <br/> 2. Something you **Have** (Phone/Token). <br/> 3. Something you **Are** (Biometric/FaceID). |
| **SSPR** | **Self-Service Password Reset.** Reduces helpdesk tickets. Requires **P1/P2 license**. "Write-back" allows the cloud password to sync back to On-Prem AD. |
| **Conditional Access** | The **"If/Then" Engine**. <br/> **Signals:** Who (User), Where (Location), Device Health, Risk Level. <br/> **Decision:** Block, Allow, or **Grant but require MFA**. |
| **RBAC** | **Role-Based Access Control.** Permissions are assigned to a **Role** (e.g., "Global Reader"), and users are assigned to that role. Prevents having to assign permissions user-by-user. |

### Governance & Protection

| Tool | Description |
|---|---|
| **Privileged Identity Management (PIM)** | Provides **Just-in-Time (JIT)** access. <br/> Admins are "Eligible" for a role but not active. They must "Activate" it to use it (time-bound, e.g., 4 hours). |
| **Entra ID Protection** | Detects **Identity Risks** (Risk-based). <br/> &bull; **Sign-in Risk:** Real-time (Anonymous IP, Impossible Travel). <br/> &bull; **User Risk:** Aggregate (Leaked credentials found on dark web). |
| **Access Reviews** | Automated auditing. "Does John still need access to the Finance Group?" Helps prevent permission creep. |

---

## 3. Describe the Capabilities of Microsoft Security Solutions (35–40%)

### Azure Infrastructure Security

| Service | Description |
|---|---|
| **DDoS Protection** | &bull; **Basic:** Free, on by default. Protects Azure infrastructure. <br/> &bull; **Network Protection (Standard):** Paid. Protects *your* specific VNET. Adds logging/reporting/SLA. |
| **Azure Firewall** | A managed, stateful firewall **service**. Centralized. Filters based on **FQDN** (e.g., "Block www.badsite.com"). |
| **Network Security Group (NSG)** | Basic traffic filtering for subnets or NICs. Filters by **5-Tuple** (Source IP, Source Port, Dest IP, Dest Port, Protocol). |
| **Application Security Group (ASG)** | Allows grouping of VMs (e.g., "WebServers") to simplify NSG rules. |
| **Azure Bastion** | Secure RDP/SSH access to VMs via the Azure Portal (HTML5) over TLS. **No Public IP required on the VM.** |
| **WAF (Web App Firewall)** | Protects HTTP/HTTPS apps against **OWASP Top 10** (SQL Injection, XSS). Found on *Application Gateway* and *Front Door*. |

### Security Management (Defender for Cloud)

| Component | Description |
|---|---|
| **CSPM** | **Cloud Security Posture Management.** <br/> **Free.** Gives you the **Secure Score**. Scans config and recommends fixes (e.g., "Enable MFA", "Close Port 22"). Prevents issues before they happen. |
| **CWP** | **Cloud Workload Protection.** <br/> **Paid.** Protects the *actual resources* (VMs, SQL, Containers, Storage) from malware and threats. |

### SIEM & SOAR (Microsoft Sentinel)

| Concept | Description |
|---|---|
| **SIEM** | **Security Information & Event Management.** Collects logs from *everywhere* (Azure, AWS, On-Prem). Aggregates and analyzes data. |
| **SOAR** | **Security Orchestration, Automated Response.** Uses **Playbooks** (Logic Apps) to automate responses (e.g., "If virus detected -> Isolate VM"). |

### Microsoft Defender XDR (Extended Detection and Response)

| Product | What it Protects |
|---|---|
| **Defender for Office 365** | **Email & Collab.** Anti-Phishing, Safe Links, Safe Attachments (Teams/SharePoint). |
| **Defender for Endpoint** | **Devices.** Laptops, Mobiles. Anti-virus, EDR, Attack Surface Reduction. |
| **Defender for Identity** | **On-Prem Active Directory.** Detects lateral movement and compromised on-prem identities (installs on Domain Controller). |
| **Defender for Cloud Apps** | **CASB (Cloud Access Security Broker).** Discovers "Shadow IT" (unauthorized SaaS apps) and controls data travel in apps like Salesforce/Dropbox. |

---

## 4. Describe the Capabilities of Microsoft Compliance Solutions (20–25%)

### Service Trust & Privacy

| Tool | Description |
|---|---|
| **Service Trust Portal** | Public site to download **Audit Reports** (SOC, ISO, FedRAMP). Used to prove to *your* auditors that Microsoft is compliant. |
| **Microsoft Priva** | Dedicated to **Privacy Risk**. Identifies personal data (GDPR) and manages "Right to be forgotten" requests. |

### Microsoft Purview (Compliance)

| Feature | Description |
|---|---|
| **Compliance Manager** | Calculates your **Compliance Score**. Provides "Improvement Actions" to help meet regulations (HIPAA, GDPR). |
| **Sensitivity Labels** | **Classify & Protect.** Tags documents (Public, Confidential). Can apply encryption/watermarks. *Protection travels with the file.* |
| **Data Lifecycle (Retention)** | **Retention Policies.** "Keep financial data for 7 years, then delete" or "Delete chat history after 30 days." |
| **DLP (Data Loss Prevention)** | Prevents sensitive data from **leaving** the org. (e.g., Block emails containing Credit Card numbers). |
| **Insider Risk Management** | Detects malicious activity **internal** to the company (e.g., Resignation submitted + Large data download). |
| **eDiscovery** | Legal search. Identifying, preserving (Legal Hold), and exporting data for court cases. |

---

## 5. Top "Gotcha" Scenarios (Crucial Differences)

| Confusing Pair | The Difference |
|---|---|
| **Azure Firewall vs. NSG** | **Firewall:** Intelligent, Domain-based, Centralized Service. <br/> **NSG:** Basic, IP/Port-based, Decentralized rule list. |
| **Authentication vs. Authorization** | **AuthN:** Who are you? (Logging in). <br/> **AuthZ:** What can you do? (Permissions). |
| **Encryption vs. Hashing** | **Encryption:** Hides data (Confidentiality). Two-way. <br/> **Hashing:** Verifies Integrity. One-way. |
| **Defender for Cloud vs. Def. for Cloud Apps** | **Def for Cloud:** Protects Infrastructure (VMs/SQL). <br/> **Def for Cloud Apps:** Protects SaaS software usage (Dropbox/Salesforce/Shadow IT). |
| **Zero Trust vs. Defense in Depth** | **Zero Trust:** A *Strategy* (Verify, Least Privilege, Assume Breach). <br/> **Defense in Depth:** An *Architecture* (Layers of security). |
| **Sentinel vs. Defender** | **Sentinel:** Birds-eye view of everything (SIEM). <br/> **Defender:** Specialized protection for specific assets (XDR). |

---

## 6. Essential Acronyms Cheat Sheet

| Acronym | Full Name | Quick Definition |
|---|---|---|
| **RBAC** | Role-Based Access Control | Permissions assigned to a role, not a user. |
| **MFA** | Multi-Factor Authentication | Using 2+ methods to sign in. |
| **SSPR** | Self-Service Password Reset | Users resetting their own passwords. |
| **PIM** | Privileged Identity Management | Just-in-Time (JIT) admin access. |
| **JIT** | Just-In-Time | Access granted only when needed (time-bound). |
| **JEA** | Just-Enough-Access | Access granted only to the specific thing needed. |
| **SIEM** | Security Info & Event Management | Logging and Analytics (Sentinel). |
| **SOAR** | Security Orchestration & Auto Response | Automated Logic App workflows (Sentinel). |
| **XDR** | Extended Detection & Response | Deep protection for specific assets (Defender). |
| **CSPM** | Cloud Security Posture Management | Checks your settings/configuration (Secure Score). |
| **CWP** | Cloud Workload Protection | Checks your actual servers/VMs for viruses. |
| **CASB** | Cloud Access Security Broker | Sits between users and SaaS apps (Defender for Cloud Apps). |
| **DLP** | Data Loss Prevention | Stops sensitive data from leaving the org. |
| **TDE** | Transparent Data Encryption | Encrypts SQL Databases at rest. |
| **TLS** | Transport Layer Security | Encrypts data in transit (HTTPS). |
