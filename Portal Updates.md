# Microsoft Security and Compliance Portals (November 19, 2025)

Complete reference guide for SC-200 and SC-900 exam preparation.

## Core Security and Compliance Portals (Your Priority)

| Portal Name | URL | Purpose | Legacy/Merged From | SC-900 | SC-200 |
|-------------|-----|---------|-------------------|--------|--------|
| **Microsoft 365 Admin Center** | https://admin.microsoft.com | User management, licensing, org settings, subscription management | N/A | ✓ | Optional |
| **Microsoft Entra Admin Center** | https://entra.microsoft.com | Identity management, authentication, Conditional Access, PIM, Entra ID Governance | Merged from Azure AD Admin Center | ✓ | ✓ |
| **Microsoft 365 Defender** | https://security.microsoft.com | Unified threat protection, incident management, Defender services coordination | Merged from "Microsoft 365 Security Center" | ✓ | ✓ |
| **Microsoft Sentinel** | Azure Portal → Search "Sentinel" or https://portal.azure.com/#blade/Microsoft_Azure_Security_Insights/ | SIEM/SOAR, threat detection, hunting, KQL queries, automation, workbooks | Still exists independently (NOT retired, integrated into Defender XDR ecosystem) | ✓ | ✓ |
| **Microsoft Purview** | https://purview.microsoft.com | Compliance, data governance, eDiscovery, DLP, sensitivity labels, insider risk, audit, records management | **Merged from:** compliance.microsoft.com (retired Aug 31, 2025), includes all legacy eDiscovery/compliance functions | ✓ | Optional |
| **Azure Portal** | https://portal.azure.com | Cloud resources, subscriptions, Azure services, Defender for Cloud, virtual machines | N/A | Optional | ✓ |
| **Microsoft Intune** | https://intune.microsoft.com | Device management, MDM, app deployment, endpoint compliance | Endpoint Manager | Optional | ✓ |
| **Microsoft Defender for Cloud** | Azure Portal → "Defender for Cloud" blade | Cloud security posture, workload protections, vulnerability management, CSPM | Formerly "Azure Security Center (ASC)" | ✓ | ✓ |
| **Microsoft Security Copilot** | Integrated in https://security.microsoft.com | AI-assisted threat analysis, incident investigation, threat hunting automation | New portal (Copilot-integrated) | Emerging | ✓ |

## Additional Portals You May Encounter

| Portal Name | URL | Purpose | SC-900 | SC-200 |
|-------------|-----|---------|--------|--------|
| **Microsoft Defender for Endpoint** | Part of https://security.microsoft.com | Endpoint detection and response (EDR), device management, threat analytics | ✓ | ✓ |
| **Microsoft Defender for Identity** | Part of https://security.microsoft.com | Identity threat detection and investigation | ✓ | Optional |
| **Microsoft Defender for Office 365** | Part of https://security.microsoft.com | Email and collaboration threat protection, phishing, malware | ✓ | ✓ |
| **Microsoft Defender for Cloud Apps** | Part of https://security.microsoft.com | Cloud app security, shadow IT discovery, data protection | ✓ | Optional |
| **Power Platform Admin Center** | https://admin.powerplatform.microsoft.com | Power Apps, Power Automate security and governance | Optional | Optional |
| **Service Trust Portal** | https://servicetrust.microsoft.com | Compliance certifications, audit reports, security assessments, trust center documents | ✓ | Optional |
| **Microsoft 365 Compliance Portal** | Now part of **Microsoft Purview** (https://purview.microsoft.com) | **RETIRED - Redirects to Purview** | Legacy | Legacy |
| **Office 365 Security & Compliance Center** | Now part of **Microsoft Purview** and **Microsoft 365 Defender** | **RETIRED** | Legacy | Legacy |

## Key Mergers and Retirements (As of November 2025)

### Retired/Consolidated
- ❌ **compliance.microsoft.com** → Fully retired August 31, 2025 → Use **purview.microsoft.com**
- ❌ **Office 365 Security & Compliance** → Consolidated into **Microsoft Purview** + **Microsoft 365 Defender**
- ❌ **Legacy eDiscovery tools** (Classic Content Search, eDiscovery Standard/Premium) → Retired August 31, 2025 → Use **Microsoft Purview eDiscovery** instead
- ❌ **Azure Security Center (ASC)** → Rebranded as **Microsoft Defender for Cloud**

### Still Active (Not Retired)
- ✓ **Microsoft Sentinel** → Remains independent SIEM/SOAR platform, now integrated into **Defender XDR ecosystem** (still accessed via Azure Portal, NOT retired)
- ✓ **Azure AD** → Rebranded as **Microsoft Entra**, full functionality preserved

## Certification Exam Focus Areas

### SC-900 (Security, Compliance, and Identity Fundamentals)

**Portal Focus:**
- **Microsoft Entra** (25–30% of exam)
- **Microsoft Defender** (Endpoint, Identity, Office 365, Cloud Apps)
- **Microsoft Sentinel** (SIEM/SOAR concepts)
- **Microsoft Purview** (compliance, DLP, insider risk, eDiscovery, audit)
- **Azure security services** (Defender for Cloud, DDoS, Firewall, Key Vault)

### SC-200 (Security Operations Analyst)

**Portal Focus:**
- **Microsoft Sentinel** (40–50% of exam focus) - advanced workspace config, KQL, analytics rules, hunting, automation
- **Microsoft 365 Defender** (threat investigations, incident response, Copilot integration)
- **Microsoft Intune** (endpoint compliance)
- **Azure Portal** (resource management, Defender for Cloud)
- **Microsoft Entra** (identity investigations)

## Quick Reference: Which Portal to Use

| Task | Portal |
|------|--------|
| Manage users and licenses | Microsoft 365 Admin Center |
| Set up identity policies | Microsoft Entra |
| Configure conditional access | Microsoft Entra |
| Investigate security incidents | Microsoft 365 Defender |
| Build SIEM queries and automation | Microsoft Sentinel |
| Configure compliance policies | Microsoft Purview |
| Manage cloud resources | Azure Portal |
| Manage devices and apps | Microsoft Intune |
| Cloud security posture | Microsoft Defender for Cloud |
| Perform threat hunting | Microsoft Sentinel |

## Notes

- **Updated:** November 19, 2025
- **Status:** Current as of SC-900 and SC-200 study guides (October/November 2025 versions)
- **Legacy Features:** All compliance features from the retired compliance.microsoft.com and Office 365 Security & Compliance Center have been merged into Microsoft Purview
- **Microsoft Sentinel Status:** NOT retired—remains a core SIEM/SOAR platform and primary component of SC-200 exam
