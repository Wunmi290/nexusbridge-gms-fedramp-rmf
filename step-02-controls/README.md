# Step 2: Control Tailoring Log and Customer Responsibility Matrix (CRM)

**Project Title:** FedRAMP Moderate Control Tailoring Log and Customer Responsibility Matrix
**System Reference:** NexusBridge Grant Management System (GMS) | DOE-NB-GMS-2024-MOD
**Framework / Standard:** NIST SP 800-53B, FedRAMP Moderate Baseline
**Author:** Omowumi Adisa, ISSO, NexusBridge Technologies
**Date:** May 2024
**Status:** Complete

## Purpose

Step 2 of the NIST Risk Management Framework requires the organization to select, tailor, and assign security controls appropriate for the system based on the security categorization established in Step 1. For NexusBridge GMS, this means working from the FedRAMP Moderate control baseline (325+ controls per NIST SP 800-53B) and documenting which controls are fully inherited from AWS, which are shared, and which are the sole responsibility of NexusBridge.

## System Information

| Field | Detail |
|---|---|
| System Name | NexusBridge Grant Management System (GMS) |
| System ID | DOE-NB-GMS-2024-MOD |
| ISSO | Omowumi Adisa, NexusBridge Technologies |
| System Owner | Dr. Marcus T. Webb, DOE Deputy Director, Research Programs |
| FedRAMP Baseline | Moderate (NIST SP 800-53B) |
| Cloud Provider | AWS GovCloud (US-West) |
| AWS FedRAMP Package | AWS GovCloud FedRAMP High P-ATO |
| Step 2 Completion Date | April 28, 2024 |

## Control Responsibility Categories

| Category | Definition | Example for NexusBridge GMS |
|---|---|---|
| Inherited | AWS implements the control entirely. NexusBridge documents the inheritance. | PE-1 through PE-20 (Physical and Environmental Protection) |
| Shared | AWS implements part of the control at the infrastructure level. NexusBridge implements the application and configuration layer. | AU-2 (Event Logging): AWS provides CloudTrail; NexusBridge configures what events are logged at the application layer |
| Customer Responsible | NexusBridge must implement, operate, and provide evidence for this control entirely. | AC-1 (Access Control Policy and Procedures): NexusBridge writes and maintains its own access control policy |

## Representative Control Tailoring Log

| Control ID | Control Name | Responsibility | Tailoring Decision | AWS Package Ref |
|---|---|---|---|---|
| AC-1 | Access Control Policy and Procedures | Customer | NexusBridge maintains policy reviewed annually | N/A |
| AC-2 | Account Management | Shared | AWS provides IAM infrastructure; NexusBridge owns provisioning, review, and termination workflows | AWS CRM AC-2 |
| AC-3 | Access Enforcement | Shared | AWS enforces at infrastructure level; NexusBridge configures IAM roles and application-level RBAC | AWS CRM AC-3 |
| AC-17 | Remote Access | Customer | NexusBridge policy prohibits direct remote access; all admin access via Systems Manager Session Manager | N/A |
| AU-2 | Event Logging | Shared | AWS provides CloudTrail and CloudWatch; NexusBridge defines application-level log events and retention | AWS CRM AU-2 |
| AU-6 | Audit Record Review, Analysis, and Reporting | Customer | NexusBridge ISSO reviews SIEM alerts weekly; monthly report to AO | N/A |
| CA-2 | Control Assessments | Customer | Scheduled with 3PAO ClearPoint Assurance LLC | N/A |
| CA-7 | Continuous Monitoring | Customer | NexusBridge ConMon plan developed post-RAR (RAR-001 remediation) | N/A |
| CM-2 | Baseline Configuration | Shared | AWS provides AMI hardening; NexusBridge applies CIS Benchmarks at OS and application layer | AWS CRM CM-2 |
| CP-4 | Contingency Plan Testing | Customer | NexusBridge conducts annual tabletop exercise | N/A |
| CP-9 | System Backup | Shared | AWS manages RDS automated backups; NexusBridge tests restores quarterly | AWS CRM CP-9 |
| IA-2 | Identification and Authentication (Organizational Users) | Shared | DOE Central IdP provides SAML federation; NexusBridge enforces MFA at application layer | AWS CRM IA-2 |
| IR-4 | Incident Handling | Customer | NexusBridge maintains Incident Response Plan; drills conducted semi-annually | N/A |
| IR-6 | Incident Reporting | Customer | NexusBridge reports incidents to DOE CISO within 1 hour of detection | N/A |
| MP-2 | Media Access | Inherited | No removable media in AWS GovCloud; inherited fully | AWS CRM MP-2 |
| PE-2 | Physical Access Authorizations | Inherited | AWS GovCloud physical access controls; fully inherited | AWS CRM PE-2 |
| PL-2 | System Security Plan | Customer | NexusBridge ISSO responsible for SSP development and maintenance | N/A |
| PS-3 | Personnel Screening | Customer | Background checks completed by NexusBridge HR for all staff with system access | N/A |
| RA-3 | Risk Assessment | Customer | ISSO conducts annual risk assessment; results documented in risk register | N/A |
| RA-5 | Vulnerability Monitoring and Scanning | Shared | AWS Inspector provides EC2 scanning; NexusBridge runs Nessus for application layer | AWS CRM RA-5 |
| SA-9 | External System Services | Customer | NexusBridge documents all external connections (DOE IdP, NSF, Treasury) with ISA/MOU | N/A |
| SC-5 | Denial of Service Protection | Inherited | AWS Shield Standard protects against volumetric DDoS; inherited from AWS | AWS CRM SC-5 |
| SC-7 | Boundary Protection | Shared | AWS VPC provides network boundary; NexusBridge configures security groups and NACLs | AWS CRM SC-7 |
| SC-8 | Transmission Confidentiality and Integrity | Shared | AWS manages TLS termination at ALB; NexusBridge enforces TLS 1.2+ and certificate management | AWS CRM SC-8 |
| SC-28 | Protection of Information at Rest | Shared | AWS KMS encrypts RDS and S3; NexusBridge manages key policy and rotation | AWS CRM SC-28 |
| SI-2 | Flaw Remediation | Customer | NexusBridge patches critical findings within 30 days, high within 60 days | N/A |
| SI-3 | Malicious Code Protection | Shared | AWS GuardDuty provides threat detection; NexusBridge deploys host-based endpoint protection | AWS CRM SI-3 |

## Control Count Summary

| Responsibility Category | Control Count (Approximate) |
|---|---|
| Inherited from AWS | 52 controls |
| Shared (AWS + NexusBridge) | 138 controls |
| Customer Responsible (NexusBridge only) | 135 controls |
| Total FedRAMP Moderate Controls | 325+ controls |

## Organizational-Defined Parameters (ODPs)

| Control | Parameter | NexusBridge Value |
|---|---|---|
| AC-2(j) | Account review frequency | Quarterly |
| AU-11 | Audit log retention period | 3 years |
| CA-7 | Continuous monitoring frequency | Monthly (vulnerability scans), weekly (log review) |
| CP-2 | Contingency plan review frequency | Annually |
| IA-5(1)(a) | Minimum password length | 15 characters |
| IA-5(1)(d) | Password change frequency | 90 days |
| IR-6 | Incident reporting time to AO | 1 hour |
| RA-3 | Risk assessment frequency | Annually |
| RA-5 | Vulnerability scanning frequency | Weekly (infrastructure), monthly (application) |
| SC-10 | Network disconnect timeout | 30 minutes |
| SI-2 | Patch remediation timeframes | Critical: 30 days, High: 60 days, Medium: 90 days |

## Interview Defense Notes

**What is the purpose of Step 2 in the NIST RMF?**
Step 2 is where you select the security controls for your system based on the security category determined in Step 1. You start with the appropriate baseline and then tailor it by adding, removing, or adjusting controls based on your specific environment and risk.

**What is a Customer Responsibility Matrix (CRM)?**
A CRM is a FedRAMP document that maps each control in the baseline to who is responsible for implementing it: the cloud provider (inherited), both the provider and the customer (shared), or the customer alone. It prevents gaps where both sides assume the other is handling something.

**What are organizational-defined parameters (ODPs)?**
ODPs are the blanks in NIST controls that each organization fills in based on its risk tolerance and operational needs. For example, NIST says you should review accounts periodically. The ODP is the specific frequency. NexusBridge set that to quarterly for AC-2.

---
*Prepared by: Omowumi Adisa, ISSO, NexusBridge Technologies*
*System: NexusBridge Grant Management System (GMS) | DOE-NB-GMS-2024-MOD*
*[GitHub Portfolio](https://github.com/Wunmi290)*
