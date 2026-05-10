# Step 6: Continuous Monitoring (ConMon) Plan and Sample Monthly ConMon Report

**Project Title:** Continuous Monitoring Plan and Sample Monthly ConMon Report for NexusBridge GMS
**System Reference:** NexusBridge Grant Management System (GMS) | DOE-NB-GMS-2024-MOD
**Framework / Standard:** FedRAMP ConMon Guide v3.0 | NIST SP 800-137 | NIST SP 800-53 CA-7
**Author:** Omowumi Adisa, ISSO, NexusBridge Technologies
**Date:** August 2024
**Status:** Complete

## Purpose

Step 6 of the NIST Risk Management Framework is Monitoring. Once a system receives an ATO, the organization must continuously monitor the system's security posture, report findings to the AO, and manage changes that could affect its authorization. FedRAMP has specific continuous monitoring (ConMon) requirements that the CSP and ISSO must follow to maintain the ATO.

## PART A: CONTINUOUS MONITORING PLAN

### Section 1: ConMon Governance

| Field | Detail |
|---|---|
| System | NexusBridge Grant Management System (GMS) |
| System ID | DOE-NB-GMS-2024-MOD |
| ATO Date | July 21, 2024 |
| AO | Patricia L. Donovan, DOE CISO |
| ISSO | Omowumi Adisa, NexusBridge Technologies |
| ConMon Coordinator | Omowumi Adisa, ISSO |
| Monthly Report Due Date | 15th of each month |
| ConMon Plan Approved | July 9, 2024 |
| ConMon Plan Review Frequency | Annually |

### Section 2: ConMon Activities and Frequencies

| Activity | Frequency | Tool / Method | Responsible Party | Deliverable |
|---|---|---|---|---|
| Operating System Vulnerability Scans | Monthly | Tenable Nessus (authenticated) | Cloud Ops: Jerome K. Okafor | Nessus scan report |
| Web Application Vulnerability Scans | Monthly | Nessus Web App Scanning | Cloud Ops: Jerome K. Okafor | Web app scan report |
| Database Vulnerability Scans | Monthly | Nessus Database plug-ins | Cloud Ops: Jerome K. Okafor | Database scan report |
| SIEM Log Review | Weekly | Splunk (SIEM) | ISSO: Omowumi Adisa | Weekly log review summary |
| POA&M Update | Monthly | POA&M tracker (FedRAMP template) | ISSO: Omowumi Adisa | Updated POA&M |
| Hardware/Software Inventory Review | Monthly | ServiceNow CMDB + AWS Config | Cloud Ops: Jerome K. Okafor | Updated asset inventory |
| Incident Reporting | As needed (within 1 hour) | ServiceNow Incident Module | ISSO: Omowumi Adisa | US-CERT report |
| Significant Change Notification | As needed (within 30 days) | Change Advisory Board | ISSO + System Owner | Significant change notice |
| User Access Reviews | Quarterly | AWS IAM Access Analyzer + manual | ISSO: Omowumi Adisa | Access review report |
| Penetration Test | Annually | Accredited 3PAO | ClearPoint Assurance LLC | Pen test report |
| Security Assessment (full) | Annually (3-year reassessment) | Accredited 3PAO | ClearPoint Assurance LLC | Updated SAR |
| Privacy Impact Assessment Review | Annually | Privacy Officer review | Helen R. Nguyen | Updated PIA |
| Contingency Plan Test | Annually | Tabletop exercise | Jerome K. Okafor | Exercise report |
| Security Awareness Training | Annually | LMS (online training platform) | ISSO: Omowumi Adisa | Training completion records |

### Section 3: Vulnerability Management Procedures

| CVSS Score | Risk Rating | Remediation Timeframe |
|---|---|---|
| 9.0 - 10.0 | Critical | 15 days |
| 7.0 - 8.9 | High | 30 days |
| 4.0 - 6.9 | Moderate | 90 days |
| 0.1 - 3.9 | Low | 180 days |

### Section 4: Significant Change Management

A significant change is any modification to the system that could affect the security posture documented in the SSP. Examples include: changes to the authorization boundary, deployment of new software components, changes to data types processed, changes to interconnections, and changes to encryption implementations.

When a significant change occurs, the ISSO documents the change in the CAB system, notifies the AO within 30 days, and coordinates a partial or full re-assessment if required by the AO.

## PART B: SAMPLE MONTHLY CONMON REPORT (AUGUST 2024)

**Report Period:** August 1-31, 2024
**Prepared By:** Omowumi Adisa, ISSO, NexusBridge Technologies
**Submitted To:** Patricia L. Donovan, AO, DOE CISO
**Submission Date:** September 13, 2024

### Executive Summary

This is the first monthly ConMon report following the NexusBridge GMS ATO granted July 21, 2024. During August 2024, all required monitoring activities were completed on schedule. Monthly vulnerability scans identified 3 new findings: 0 Critical, 1 High, 1 Moderate, and 1 Low. The High finding has been remediated and validated. Two High-risk POA&M items from the original SAR (POA-001 and POA-002) were closed with evidence. No security incidents meeting the reporting threshold were identified.

### Vulnerability Scan Summary

| Scan Type | Date Completed | New Findings | Critical | High | Moderate | Low |
|---|---|---|---|---|---|---|
| OS Vulnerability Scan (EC2) | August 7, 2024 | 2 | 0 | 1 | 0 | 1 |
| Web Application Scan | August 14, 2024 | 1 | 0 | 0 | 1 | 0 |
| Database Scan (RDS) | August 21, 2024 | 0 | 0 | 0 | 0 | 0 |
| **Total New Findings** | | **3** | **0** | **1** | **1** | **1** |

### New Vulnerability Details

| Vuln ID | Scan Type | CVE | Description | CVSS | Risk | Status | Target Close |
|---|---|---|---|---|---|---|---|
| VUL-2024-001 | OS Scan | CVE-2024-21338 | Linux kernel elevation of privilege on AMI baseline | 7.8 | High | Remediated August 15 | Closed |
| VUL-2024-002 | Web App Scan | CVE-2024-1234 | Outdated jQuery library version in admin portal | 5.3 | Moderate | In remediation | September 30, 2024 |
| VUL-2024-003 | OS Scan | N/A | Informational: Debug headers exposed in ALB response | 2.0 | Low | In remediation | October 31, 2024 |

### POA&M Status Update

| POA&M ID | Description | Prior Status | Current Status | Evidence of Closure |
|---|---|---|---|---|
| POA-001 | Configuration baseline docs incomplete | Open (High) | Closed | Updated CMDB entries, signed baseline doc dated Aug 3, 2024 |
| POA-002 | Reflected XSS in grant search | Open (High) | Closed | Patch deployed Aug 6; rescan confirmed resolved Aug 9 |
| POA-003 | Q1 2024 account review undocumented | Open (Moderate) | In Progress (75%) | Draft retroactive review document in final review |
| POA-004 | Vulnerability scan missing 2 API endpoints | Open (Moderate) | Closed | Scan targets updated; re-scan report attached |
| POA-005 | CP tabletop exercise not conducted | Open (Moderate) | Scheduled: Sep 19 | Exercise invitation sent to all stakeholders |
| POA-006 | Treasury MOU not fully executed | Open (Moderate) | In Progress | MOU sent to Treasury OGC Aug 2; awaiting signature |
| POA-007 | SCRM policy not approved | Open (Low) | Closed | Policy approved by AO August 10, 2024 |
| POA-008 | Audit log retention not verified | Open (Moderate) | Closed | All CloudWatch log groups confirmed; screenshot attached |
| POA-009 | 2 assets missing from CMDB | Open (Moderate) | Closed | AWS Config discovery run; all assets added to ServiceNow |
| POA-010 | IR tabletop exercise not conducted | Open (Low) | Scheduled: Sep 19 | Combined with CP exercise |
| POA-011 | Rules of behavior not signed by 2 users | Open (Low) | Closed | Both signatures collected Aug 8, 2024 |
| POA-012 | Session timeout not on 1 admin screen | Open (Low) | Closed | Fix deployed Aug 13; QA verified |
| POA-013 | Security awareness training overdue | Open (Low) | Closed | All 4 users completed training by Aug 11 |

**POA&M Summary: 9 of 12 items closed. 3 items remain open. No items are past target date.**

### Significant Changes

No significant changes to the NexusBridge GMS authorization boundary, architecture, or data types occurred during August 2024.

### Incident Summary

No security incidents meeting the ConMon reporting threshold (Moderate or higher) were identified during August 2024.

One low-severity event was logged: an IAM user triggered 5 failed login attempts on August 17 due to an expired session token. The account was not locked (lockout threshold is 10 attempts). The user was notified and the token was refreshed.

### Next Month Actions

| Action | Owner | Due Date |
|---|---|---|
| Complete September vulnerability scans | Jerome K. Okafor | September 7-21, 2024 |
| Conduct combined CP/IR tabletop exercise | Jerome K. Okafor + ISSO | September 19, 2024 |
| Close POA-003 (Q1 account review documentation) | Omowumi Adisa | September 15, 2024 |
| Follow up on Treasury MOU execution | Omowumi Adisa | September 15, 2024 |
| Submit September ConMon report | Omowumi Adisa | October 15, 2024 |

## Interview Defense Notes

**What is the purpose of continuous monitoring in FedRAMP?**
An ATO is not a permanent security guarantee. ConMon ensures the system's security posture stays consistent with what the AO authorized. Without ongoing monitoring, you would not know if new vulnerabilities emerged or configurations drifted.

**What are the key FedRAMP ConMon deliverables?**
Monthly: vulnerability scan results, updated POA&M, and a monthly ConMon report. Annually: penetration test results, full control assessment by the 3PAO, and updated SSP if changes occurred.

**What is a significant change and why does it matter?**
A significant change is anything that could affect the system's security posture as documented in the SSP. It matters because the AO authorized the system as it was described. If the system changes meaningfully, the AO needs to re-evaluate whether the authorization still applies.

**What happens if a new Critical vulnerability is found during a monthly scan?**
It must be remediated within 15 days per FedRAMP SLAs. If it cannot be remediated in time, it must go into the POA&M with compensating controls and an AO-approved extension. Failure to act can result in ATO suspension.

**Why is the ISSO responsible for the monthly ConMon report?**
The ISSO is the primary security liaison between the CSP and the agency. The ISSO coordinates the technical teams and translates security data into a report the AO can act on. It is a communication and accountability role, not just a technical one.

---
*Prepared by: Omowumi Adisa, ISSO, NexusBridge Technologies*
*System: NexusBridge Grant Management System (GMS) | DOE-NB-GMS-2024-MOD*
*[GitHub Portfolio](https://github.com/Wunmi290)*
