# Step 4: Security Assessment Plan (SAP) and Security Assessment Report (SAR)

**Project Title:** Security Assessment Plan and Security Assessment Report for NexusBridge Grant Management System
**System Reference:** NexusBridge Grant Management System (GMS) | DOE-NB-GMS-2024-MOD
**Framework / Standard:** FedRAMP Moderate Baseline | FedRAMP SAP Template v3.0 | FedRAMP SAR Template v3.0
**Author:** Omowumi Adisa, ISSO, NexusBridge Technologies
**3PAO:** Sandra L. Pryce, ClearPoint Assurance LLC
**Date:** May 2024
**Status:** Complete

## Purpose

Step 4 of the NIST Risk Management Framework requires an independent assessment of the security controls documented in the SSP. For FedRAMP, this assessment must be conducted by an accredited Third Party Assessment Organization (3PAO). The assessment produces two documents: the Security Assessment Plan (SAP) and the Security Assessment Report (SAR).

## PART A: SECURITY ASSESSMENT PLAN (SAP)

### SAP Section 1: Assessment Scope

The scope of this assessment covers all 325+ FedRAMP Moderate controls applicable to NexusBridge GMS within the defined authorization boundary. The assessment covers shared and customer-responsible controls. Inherited controls (fully inherited from AWS GovCloud FedRAMP High P-ATO) are noted as inherited and are not re-tested.

| Assessment Element | Details |
|---|---|
| Assessment Organization | ClearPoint Assurance LLC |
| Lead Assessor | Sandra L. Pryce |
| Assessment Type | Initial Assessment (Pre-Authorization) |
| Assessment Period | June 2-27, 2024 |
| System | NexusBridge GMS, DOE-NB-GMS-2024-MOD |
| Baseline | FedRAMP Moderate (325+ controls) |
| Controls Inherited (Not Tested) | 52 (fully inherited from AWS) |
| Controls Assessed | 273 (shared and customer-responsible) |

### SAP Section 2: Assessment Methods

| Method | Description | Application to NexusBridge GMS |
|---|---|---|
| Examine | Review of documentation, policies, procedures, and configuration artifacts | Review SSP, policies, system architecture diagrams, scan reports, access review records |
| Interview | Structured discussions with system personnel | Interviews with ISSO (Omowumi Adisa), Cloud Ops Lead (Jerome Okafor), System Owner (Dr. Webb) |
| Test | Technical testing of system components | Vulnerability scanning, configuration audits, penetration testing, log review |

### SAP Section 3: Assessment Tools

| Tool | Purpose |
|---|---|
| Tenable Nessus | Vulnerability scanning (OS and application layer) |
| Burp Suite Pro | Web application security testing |
| AWS Config | Configuration compliance auditing |
| AWS Security Hub | Automated security findings aggregation |
| Manual review | Policy review, interview documentation, configuration verification |

### SAP Section 4: Assessment Schedule

| Activity | Dates | Lead |
|---|---|---|
| Kickoff meeting with ISSO and system owner | June 2, 2024 | Sandra L. Pryce |
| Document review (SSP, policies, diagrams) | June 2-6, 2024 | ClearPoint team |
| Personnel interviews | June 9-11, 2024 | Sandra L. Pryce |
| Technical testing (vulnerability scans, config review) | June 12-20, 2024 | ClearPoint technical team |
| Penetration testing | June 16-18, 2024 | ClearPoint red team |
| Draft SAR delivered to NexusBridge | June 24, 2024 | Sandra L. Pryce |
| NexusBridge review and factual corrections | June 25-26, 2024 | Omowumi Adisa, ISSO |
| Final SAR delivered to DOE | June 27, 2024 | Sandra L. Pryce |

## PART B: SECURITY ASSESSMENT REPORT (SAR)

### SAR Section 1: Executive Summary

ClearPoint Assurance LLC completed the FedRAMP Moderate security assessment of NexusBridge GMS during June 2-27, 2024. The assessment covered 273 controls (excluding 52 fully inherited from AWS GovCloud). The assessment team identified 16 findings, of which 2 are High risk, 7 are Moderate risk, and 7 are Low risk. No Critical findings were identified.

The system demonstrates a strong security posture in identity and access management, encryption, network boundary protection, and audit logging. The primary gaps are in configuration management documentation and the maturity of the continuous monitoring program.

| Finding Level | Count |
|---|---|
| Critical | 0 |
| High | 2 |
| Moderate | 7 |
| Low | 7 |
| Total | 16 |

### SAR Section 2: Control Assessment Results Summary

| Control Family | Controls Assessed | Satisfied | Other Than Satisfied |
|---|---|---|---|
| Access Control (AC) | 25 | 23 | 2 |
| Audit and Accountability (AU) | 16 | 15 | 1 |
| Configuration Management (CM) | 18 | 15 | 3 |
| Contingency Planning (CP) | 12 | 11 | 1 |
| Identification and Authentication (IA) | 12 | 12 | 0 |
| Incident Response (IR) | 10 | 9 | 1 |
| Risk Assessment (RA) | 9 | 8 | 1 |
| System and Communications (SC) | 44 | 42 | 2 |
| System and Information Integrity (SI) | 16 | 14 | 2 |
| Other Families | 111 | 106 | 3 |
| **Total** | **273** | **255** | **16** |

### SAR Section 3: Significant Findings

**Finding SAR-001: Patch Management Delay on Non-Production Instances (High)**

- **Control:** SI-2 (Flaw Remediation)
- **Description:** Two non-production EC2 instances had 12 unpatched High-severity vulnerabilities older than 60 days. These instances are used for development testing but share the authorization boundary.
- **Risk:** An attacker with access to the development environment could exploit these vulnerabilities to pivot to production systems.
- **Recommendation:** Apply patches immediately and update patch management procedures to include non-production instances within the same SLA as production.
- **Status:** Remediated before final SAR delivery (June 26, 2024)

**Finding SAR-002: Incomplete Configuration Baseline Documentation (High)**

- **Control:** CM-2 (Baseline Configuration)
- **Description:** The NexusBridge configuration baseline documentation does not cover 3 EC2 instance types added during a recent scale-out. The CMDB in ServiceNow was not updated.
- **Risk:** Untracked instances may have inconsistent configurations and could introduce unauthorized software or services.
- **Recommendation:** Update the configuration baseline document and CMDB to include all current instance types.
- **Status:** Open, included in POA&M (SAR-002), target completion July 15, 2024.

**Finding SAR-003: Reflected XSS in Grant Search Function (High)**

- **Control:** SI-10 (Information Input Validation)
- **Description:** The penetration test identified a reflected cross-site scripting (XSS) vulnerability in the grant application search input field.
- **Recommendation:** Implement output encoding and input validation for all search fields. Conduct a full code review of input handling.
- **Status:** Open, included in POA&M (SAR-003), target completion July 15, 2024.

### SAR Section 4: Assessment Team Attestation

ClearPoint Assurance LLC attests that the assessment was conducted in accordance with FedRAMP requirements and NIST SP 800-53A Rev 5. All findings are based on evidence collected during the assessment period.

*Assessor: Sandra L. Pryce, ClearPoint Assurance LLC | Date: June 27, 2024*

## Interview Defense Notes

**What is the difference between a SAP and a SAR?**
The SAP is the plan: it describes what the 3PAO will test, how they will test it, and the schedule. The SAR is the report: it documents what they actually found. The SAP comes before the assessment, the SAR comes after.

**What are the three assessment methods in NIST SP 800-53A?**
Examine (reviewing documents and artifacts), Interview (talking to system personnel), and Test (technical testing like scanning and pen testing). A rigorous assessment uses all three for each control.

**What does Other Than Satisfied mean in a SAR?**
It means the control has a finding: it is not fully implemented as required. OTS findings become POA&M items.

**What happens when a 3PAO finds a High finding?**
It gets documented in the SAR with a risk rating, description, and recommendation. The CSP typically has to address High findings before authorization or include them in the POA&M with a 30-day remediation target.

---
*Prepared by: Omowumi Adisa, ISSO, NexusBridge Technologies*
*Assessment conducted by: Sandra L. Pryce, ClearPoint Assurance LLC*
*System: NexusBridge Grant Management System (GMS) | DOE-NB-GMS-2024-MOD*
*[GitHub Portfolio](https://github.com/Wunmi290)*
