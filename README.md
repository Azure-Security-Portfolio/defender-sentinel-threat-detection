## Monitoring & Detection with Microsoft Sentinel & Defender for Cloud

End-to-end detection, response and remediation of cloud security incidents using Microsoft Sentinel SIEM/SOAR and Defender for Cloud.

---

## Table of Contents

- [Overview](#overview)
- [Real-World Risk](#real-world-risk)
- [What I Built](#what-i-built)
- [Main Diagram](#main-diagram)
- [Bonus Diagram](#bonus-diagram)
- [Objectives](#objectives)
- [Steps Performed](#steps-performed)
  - [1. Resource Group & Workspace Setup]
  - [2. Defender for Cloud & Sentinel Activation]  
  - [3. Agent & Data Connector Verification] 
  - [4. Threat Simulation]
  - [5. Alert Detection & Incident Investigation]
  - [6. Automated Incident Response]  
  - [7. Remediation & Secure Score] 
  - [8. Visualization]
  - [9. Cleanup] 
  - [10. Additional Evidence]
  - [11. ⭐ Bonus & Extras]
- [Screenshots](#screenshots)
  - [Core Lab Screenshots]
  - [⭐ Bonus Screenshots]
- [Lessons Learned](#lessons-learned)
- [Post-Incident SOC Analysis](#post-incident-soc-analysis)
- [Notes & Limitations](#notes--limitations)
- [References](#references)   

---

## Overview

This lab demonstrates real-world cloud blue team operations using Microsoft Sentinel and Defender for Cloud.  
I deployed a simulated SOC workflow—detecting threats, investigating alerts, triggering automated playbooks, remediating recommendations and visualizing posture in dashboards.  
**Bonus:** I exported Secure Score & recommendations and created a custom SOC-style post-incident analysis.

---

## Real-World Risk

- **Cloud attacks (malware, brute force, lateral movement) are fast-moving and persistent.**
- Lack of SIEM/SOAR means delayed detection, no alert correlation, and slow response.
- Automated detection and response are essential to minimize impact and prove compliance.

---

## What I Built

- Enabled Microsoft Defender for Cloud, activated Defender plans (including malware scanning, CSPM, and vulnerability management).
- Onboarded Microsoft Sentinel, connected to Log Analytics Workspace.
- Integrated built-in data connectors for Microsoft 365, Defender, VMs, and storage.
- Simulated real-world threats:
    - Uploaded the EICAR test file to storage (malware detection).
    - Performed RDP brute-force attempts against a lab VM.
- Configured custom Sentinel analytics rules (KQL) to detect brute-force logins.
- Built automated incident response using Sentinel Playbooks (Logic Apps) — triggered email notifications for new incidents.
- Remediated Defender for Cloud recommendations (e.g., closed open RDP, deleted malware, restricted NSG rules).
- Visualized alerts/incidents in Sentinel Workbooks dashboards.
- **Bonus:** Exported Secure Score & recommendations as CSV/PDF and created severity charts for documentation.

---

## Main Diagram

![Lab 8 Architecture](diagram.png)

---

## Bonus Diagram

![Sentinel Playbook Automation Architecture](diagram2.png)

*This diagram shows how security events are collected from VMs, analyzed by Sentinel and how incidents can trigger automated responses such as Logic App playbooks for real-time alerting or remediation.*

---

## Objectives

- Detect and investigate cloud threats in real-time using SIEM/SOAR (Sentinel, Defender for Cloud)
- Respond to incidents with automation (Logic Apps/Playbooks)
- Remediate misconfigurations, prove improved Secure Score.
- Visualize and report on cloud security posture for auditors/managers.

---

## Steps Performed

**1. Resource Group & Workspace Setup**  
   - Created a dedicated resource group and Log Analytics workspace for the lab *(Screenshot: resource-group-created.png & log-analytics-workspace.png)*

**2. Defender for Cloud & Sentinel Activation**  
   - Enabled Defender for Cloud plans (CSPM, workload protection, malware scanning)  
   - Enabled Microsoft Sentinel and connected Log Analytics workspace *(Screenshots: defender-for-cloud-enabled.png & azure-sentinel-enabled.png)*

**3. Agent & Data Connector Verification**  
   - Verified Log Analytics/AMA agent extension on VM.  
   - Confirmed Sentinel data connectors were active for all key sources *(Screenshots: agent-extension-present.png & sentinel-data-connectors.png)*

**4. Threat Simulation**  
   - Uploaded EICAR test file to Storage (malware simulation)  
   - Performed brute-force login attempts on VM (RDP, public IP)*(Screenshots: eicar-uploaded.png, rdp-blocked.png)*

**5. Alert Detection & Incident Investigation**  
   - Observed Defender for Cloud and Sentinel alerts for simulated threats.  
   - Explored Sentinel incident details, timeline, investigation graph, and entities involved *(Screenshots: defender-alerts.png, defender-alert-details.png, defender-alert-resolved.png, sentinel-incident-details.png, sentinel-incident-timeline.png, sentinel-investigation-graph.png & sentinel-entities.png)*

**6. Automated Incident Response (Playbooks)**  
   - Built Logic App playbook for automated email notification.  
   - Linked playbook to Sentinel automation rule and tested with simulated alerts *(Screenshots: logic-app-workflow-creation.png, logic-app-workflow-email-action.png, sentinel-logicapp-connection.png, sentinel-automation-rule.png & sentinel-bruteforce-email.png)*

**7. Remediation & Secure Score**  
   - Addressed open recommendations: closed RDP, deleted malware, restricted NSGs.  
   - Exported Secure Score/recommendations as CSV/PDF; visualized results with pie chart *(Screenshots: defender-recommendations.png, recommendation-unhealthy.png, recommendation-remediated.png & recommendations-severity-chart.png)*

**8. Visualization**  
   - Created Sentinel Workbook dashboard showing SOC/incident metrics *(Screenshot: workbook-dashboard.png)*

**9. Cleanup**  
   - Detached Sentinel, deleted lab resource group and resources to avoid Azure charges.

**10. Additional Evidence**  
   - Included key screenshots of log analytics workspace, storage account and VM details *(Screenshots: log-analytics-workspace.png, storage-account-overview.png, vm-overview.png, sentinel-custom-analytics-rule.png, auto-provisioning-agent-grayed.png)*

**11. ⭐ Bonus & Extras: Advanced Sentinel Configurations & Best Practices**

a. Custom Data Collection Rule (DCR) Setup
   - To demonstrate advanced log forwarding, I configured a Data Collection Rule (DCR) to forward VM logs directly to Sentinel *(Screenshot: dcr_review-create_final-settings.png)*

b. Log Collection Architecture
   - The following diagram shows how VM security events are routed to Sentinel (*Screenshot: sentinel_dataflow_vm-to-sentinel.png*)

c. Integrating Threat Intelligence & Identity Protection
   - Connected Microsoft Entra ID Protection to enrich Sentinel incidents with identity risk signals *(Screenshot: entra-id-protection-connector.png)*

d. Cloud Governance: Resource Tagging
   - Applied best-practice tags to workspaces and resource groups for improved cost management and security oversight *(Screenshots: law-tags.png & resource-group-tags.png*

e. Additional Analytics Rules
   - As part of defense-in-depth, created custom Sentinel analytics rules for user sign-in detection *(Screenshot: create-custom-analytic-rule.png)*

f. Additional Automation Rules
   - Set up automation rules to assign owners and email alerts on incident creation *(Screenshot: sentinel-automation-rule-creation.png)*

---

## Screenshots

Below are the core and bonus screenshots that document each step and added value.
*All screenshots are included in the screenshots/ folder.*

## Core Lab Screenshots:

| Step | Filename                              | Description                                         |
|------|---------------------------------------|-----------------------------------------------------|
|  1   | resource-group-created.png            | Resource group and workspace creation for lab       |
|  2   | defender-for-cloud-enabled.png        | Defender for Cloud plans enabled                    |
|  2   | azure-sentinel-enabled.png            | Microsoft Sentinel enabled and connected            |
|  3   | agent-extension-present.png           | Log Analytics/AMA agent extension present on VM     |
|  3   | sentinel-data-connectors.png          | Sentinel data connectors overview                   |
|  4   | eicar-uploaded.png                    | EICAR test file uploaded to Azure Storage           |
|  4   | rdp-blocked.png                       | VM RDP blocked after brute-force simulation         |
|  5   | defender-alerts.png                   | Defender for Cloud alert detection                  |
|  5   | defender-alert-details.png            | Detailed Defender alert view                        |
|  5   | defender-alert-resolved.png           | Defender alert marked as resolved                   |
|  5   | sentinel-incident-details.png         | Sentinel incident details page                      |
|  5   | sentinel-incident-timeline.png        | Sentinel incident timeline view                     |
|  5   | sentinel-investigation-graph.png      | Sentinel incident investigation graph               |
|  5   | sentinel-entities.png                 | Entities involved in Sentinel incident              |
|  6   | logic-app-workflow-creation.png       | Logic App playbook (workflow) creation              |
|  6   | logic-app-workflow-email-action.png   | Playbook email action setup                         |
|  6   | sentinel-logicapp-connection.png      | Logic App connected in Sentinel automation rule     |
|  6   | sentinel-automation-rule.png          | Sentinel automation rule linked to playbook         |
|  6   | sentinel-bruteforce-email.png         | Automated email notification for brute-force alert  |
|  7   | defender-recommendations.png          | Defender for Cloud recommendations overview         |
|  7   | recommendation-unhealthy.png          | Unhealthy Defender recommendation before remediation|
|  7   | recommendation-remediated.png         | Defender recommendation after remediation (healthy) |
|  8   | workbook-dashboard.png                | Custom Sentinel Workbook dashboard                  |
|  8   | recommendations-severity-chart.png    | Pie chart: Recommendations by severity              |
|  9   | log-analytics-workspace.png           | Log Analytics workspace overview                    |
| 10   | storage-account-overview.png          | Storage account with security settings              |
| 10   | vm-overview.png                       | Azure VM overview/details                           |
| 11   | sentinel-custom-analytics-rule.png    | Custom analytics rule for brute-force detection     |
| 11   | auto-provisioning-agent-grayed.png    | Auto-provisioning agent status                      |

## ⭐ Bonus Screenshots:

| Step/Area    | Filename(s)                            | Description                                                                         |
| ------------ | -------------------------------------- | ----------------------------------------------------------------------------------- |
| DCR Setup    | dcr-review-create-final-settings.png   | **Custom Data Collection Rule:** Forward VM logs to Sentinel (DCR configuration)    |
| Dataflow     | sentinel-dataflow-vm-to-sentinel.png   | **Log Collection Architecture:** VM → DCR → LAW → Sentinel (+ Playbook/Automation)  |
| Threat Intel | entra-id-protection-connector.png      | **Entra ID Protection:** Enrich Sentinel incidents with identity risk signals       |
| Tagging      | law-tags.png, resource-group-tags.png  | **Cloud Governance:** Applied best-practice tags to LAW and resource groups         |
| Custom Rules | create-custom-analytic-rule.png        | **Analytics:** Custom analytics rule for user sign-in detection (defense-in-depth)  |
| Automation   | sentinel-automation-rule-creation.png  | **Automation:** Assign owners + send email on incident creation (SOC best practice) |

---

## Lessons Learned

- SIEM/SOAR in the cloud requires proper data source onboarding, analytics tuning and automated playbooks for effective defense.
- Hands-on detection and response (malware, brute force) builds true blue team skills.
- Remediation and Secure Score tracking prove continuous improvement to management/auditors.
- Visualization (workbooks, charts) make results actionable for SOC teams and leadership.

---

## Post-Incident SOC Analysis

**Incident:**  
- EICAR malware upload detected in storage (high-severity alert)
- Multiple failed RDP logins simulated from external IP.

**Detection & Investigation:**  
- Defender for Cloud and Sentinel both triggered on simulated threats.
- Incidents automatically created, investigated in timeline/graph and playbooks triggered.

**Response:**  
- Automated playbook sent instant email notification to SOC team.
- Blocked RDP access, deleted malicious file, refreshed recommendations.

**Outcome:**  
- All incidents resolved, recommendations remediated, Secure Score improved.
- Full detection, response, remediation and documentation cycle completed.

---

## Notes & Limitations

- Some brute-force alerts may require custom KQL analytics rules and ensuring SecurityEvent logs are ingested by Log Analytics.
- Real-world incidents may require additional forensics/investigation steps.
- Billing: To avoid unnecessary costs, always manually remove the Sentinel solution and delete the lab resource group after completing the lab.

---

## References

- [Microsoft Sentinel Documentation](https://learn.microsoft.com/en-us/azure/sentinel/)
- [Defender for Cloud Docs](https://learn.microsoft.com/en-us/azure/defender-for-cloud/)
- [Azure Logic Apps (Playbooks)](https://learn.microsoft.com/en-us/azure/logic-apps/)
- [Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction)
- [Kusto Query Language (KQL)](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/)

---

Sebastian Silva C. – July 2025 – Berlin, Germany  
[LinkedIn](https://www.linkedin.com/in/sebastiansilc/) | [GitHub](https://github.com/SebaSilC)
