# Step 5: Authorization Package Index, POA&M Tracker, and ATO Decision Memo

**Project Title:** Authorization Package Index, Plan of Action and Milestones (POA&M), and ATO Decision Memo
**System Reference:** NexusBridge Grant Management System (GMS) | DOE-NB-GMS-2024-MOD
**Framework / Standard:** FedRAMP Moderate Baseline | FedRAMP Authorization Playbook | OMB Memo M-02-01
**Author:** Omowumi Adisa, ISSO, NexusBridge Technologies
**Date:** July 2024
**Status:** Complete

## Purpose

Step 5 of the NIST Risk Management Framework is the authorization step. The system owner and ISSO compile the complete authorization package, address outstanding findings, and submit the package to the Authorizing Official (AO) for a risk-based authorization decision. This step produces three key deliverables: the Authorization Package Index, the Plan of Action and Milestones (POA&M), and the ATO Decision Memo.

## PART A: AUTHORIZATION PACKAGE INDEX

| Field | Detail |
|---|---|
| System | NexusBridge Grant Management System (GMS) |
| System ID | DOE-NB-GMS-2024-MOD |
| Authorization Type | Agency ATO |
| Sponsoring Agency | Department of Energy (DOE) |
| AO | Patricia L. Donovan, DOE CISO |
| ISSO | Omowumi Adisa, NexusBridge Technologies |
| Package Submission Date | July 14, 2024 |
| Package Version | 1.0 |

### Document Index

| # | Document | Owner | Version | Date | Status |
|---|---|---|---|---|---|
| 1 | FedRAMP Readiness Assessment Report (RAR) | ClearPoint Assurance LLC | 1.0 | March 5, 2024 | Final |
| 2 | FIPS 199 Security Categorization Workbook | Omowumi Adisa, ISSO | 1.0 | April 12, 2024 | AO Approved |
| 3 | e-Authentication Risk Assessment | Omowumi Adisa, ISSO | 1.0 | April 18, 2024 | Final |
| 4 | Privacy Impact Assessment (PIA) | Helen R. Nguyen, Privacy Officer | 1.0 | May 2, 2024 | Final |
| 5 | System Security Plan (SSP) | Omowumi Adisa, ISSO | 1.2 | June 28, 2024 | Final |
| 6 | SSP Attachments (Architecture Diagrams, Data Flow Diagrams) | Jerome K. Okafor, Cloud Ops | 1.0 | June 14, 2024 | Final |
| 7 | Customer Responsibility Matrix (CRM) | Omowumi Adisa, ISSO | 1.0 | April 28, 2024 | Final |
| 8 | AWS GovCloud Inheritance Package | AWS / NexusBridge Reference | 2024 | Active | |
| 9 | Security Assessment Plan (SAP) | ClearPoint Assurance LLC | 1.0 | June 2, 2024 | Final |
| 10 | Security Assessment Report (SAR) | ClearPoint Assurance LLC | 1.0 | June 27, 2024 | Final |
| 11 | SAR Appendix: Penetration Test Report | ClearPoint Assurance LLC | 1.0 | June 27, 2024 | Final |
| 12 | Plan of Action and Milestones (POA&M) | Omowumi Adisa, ISSO | 1.0 | July 14, 2024 | Open (13 items) |
| 13 | Continuous Monitoring Plan | Omowumi Adisa, ISSO | 1.0 | July 9, 2024 | Final |
| 14 | Incident Response Plan | Jerome K. Okafor, Cloud Ops | 2.1 | May 12, 2024 | Final |
| 15 | Interconnection Security Agreements (ISA) | Omowumi Adisa, ISSO | 1.0 | June 28, 2024 | Executed |
| 16 | Memoranda of Understanding (MOU) | Omowumi Adisa, ISSO | 1.0 | June 28, 2024 | Executed |
| 17 | ATO Decision Memo | Patricia L. Donovan, AO | 1.0 | July 21, 2024 | Signed |

## PART B: PLAN OF ACTION AND MILESTONES (POA&M)

| Metric | Value |
|---|---|
| Total POA&M Items | 13 |
| High Risk Items | 2 |
| Moderate Risk Items | 6 |
| Low Risk Items | 5 |
| Items Closed Before ATO | 1 (SAR-001: patched June 26, 2024) |
| Items Open at ATO | 12 |

### POA&M Tracker

| POA&M ID | Control | Description | Risk | Target Close | Status |
|---|---|---|---|---|---|
| POA-001 | CM-2 | Configuration baseline documentation missing for 3 EC2 instance types | High | July 31, 2024 | Open |
| POA-002 | SI-10 | Reflected XSS in grant search input; output encoding not implemented | High | July 31, 2024 | Open |
| POA-003 | AC-2 | Quarterly account review for Q1 2024 not formally documented | Moderate | August 15, 2024 | Open |
| POA-004 | RA-5 | Application vulnerability scan did not cover 2 microservice API endpoints | Moderate | July 31, 2024 | Open |
| POA-005 | CP-4 | Contingency plan tabletop exercise not conducted in current period | Moderate | August 30, 2024 | Open |
| POA-006 | SA-9 | MOU with Treasury Disbursement API not fully executed | Moderate | August 30, 2024 | Open |
| POA-007 | SA-12 | SCRM policy not formally approved by AO | Low | August 15, 2024 | Open |
| POA-008 | AU-11 | Audit log retention not verified for all CloudWatch log groups | Moderate | August 1, 2024 | Open |
| POA-009 | CM-8 | 2 assets missing from ServiceNow CMDB inventory | Moderate | July 31, 2024 | Open |
| POA-010 | IR-3 | IR tabletop exercise not conducted in past 12 months | Low | August 30, 2024 | Open |
| POA-011 | PL-4 | Rules of behavior not signed by 2 remaining remote users | Low | July 31, 2024 | Open |
| POA-012 | SC-10 | Session timeout not enforced on 1 internal admin screen | Low | July 31, 2024 | Open |
| POA-013 | AT-2 | Security awareness training overdue for 4 users | Low | July 31, 2024 | Open |

## PART C: ATO DECISION MEMO

---
### AUTHORIZATION TO OPERATE
### NexusBridge Grant Management System (GMS)
### DOE-NB-GMS-2024-MOD

**Date:** July 21, 2024
**To:** Dr. Marcus T. Webb, System Owner, DOE Research Programs
**From:** Patricia L. Donovan, Authorizing Official, DOE CISO
**Re:** Authorization to Operate Decision for NexusBridge Grant Management System

### Authorization Decision

I have reviewed the FedRAMP Moderate authorization package for the NexusBridge Grant Management System (GMS), system identifier DOE-NB-GMS-2024-MOD, submitted on July 14, 2024. The package was prepared by ISSO Omowumi Adisa of NexusBridge Technologies and assessed by ClearPoint Assurance LLC (3PAO lead: Sandra L. Pryce).

Based on my review of the System Security Plan, Security Assessment Report, and Plan of Action and Milestones, I hereby grant an **Authorization to Operate (ATO)** for the NexusBridge Grant Management System at the FedRAMP Moderate baseline.

### Risk Acceptance Statement

The authorization package documents 12 open POA&M items. Two items are rated High risk (POA-001, POA-002). I have reviewed these items and determined that the mitigating controls in place reduce residual risk to an acceptable level. All High-risk items must be closed by July 31, 2024, and all remaining items by August 30, 2024.

### Authorization Conditions

1. Monthly ConMon deliverables must be submitted to DOE CISO no later than the 15th of each following month.
2. All High-risk POA&M items must be closed within 30 days of authorization.
3. Significant changes to system boundary, architecture, or data types must be reported within 30 days.
4. The pending Treasury MOU (POA-006) must be completed within 60 days.
5. Annual security assessments must be conducted by an accredited 3PAO.

### Authorization Period

This ATO is effective July 21, 2024. It remains valid unless the system undergoes a significant change, falls out of continuous monitoring compliance, or the DOE CISO determines that the risk posture has materially changed.

*Signed: Patricia L. Donovan, DOE Chief Information Security Officer, July 21, 2024*

---

## Interview Defense Notes

**What is a POA&M and why does the AO care about it?**
A POA&M is a formal tracker of security weaknesses that have not been fully fixed. The AO uses it to understand what risks remain and decide if those risks are acceptable. A well-maintained POA&M with clear milestones and owners shows maturity.

**Can a system get an ATO with open High findings?**
Yes, but it requires explicit risk acceptance by the AO. The AO must document why the residual risk is acceptable given mitigating controls. Open Critical findings are generally not accepted.

**What is the difference between an ATO and a FedRAMP P-ATO?**
An ATO is an Agency Authorization to Operate granted by the sponsoring agency's AO. A P-ATO (Provisional ATO) is granted by the FedRAMP Joint Authorization Board (JAB) and can be leveraged by any federal agency. NexusBridge GMS uses the Agency ATO path through DOE.

---
*Prepared by: Omowumi Adisa, ISSO, NexusBridge Technologies*
*System: NexusBridge Grant Management System (GMS) | DOE-NB-GMS-2024-MOD*
*[GitHub Portfolio](https://github.com/Wunmi290)*
