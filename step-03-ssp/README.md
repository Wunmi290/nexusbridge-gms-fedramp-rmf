# Step 3: Partial FedRAMP System Security Plan (SSP)

**Project Title:** Partial FedRAMP System Security Plan (SSP) for NexusBridge Grant Management System
**System Reference:** NexusBridge Grant Management System (GMS) | DOE-NB-GMS-2024-MOD
**Framework / Standard:** FedRAMP Moderate Baseline | FedRAMP SSP Template v3.1 | NIST SP 800-18
**Author:** Omowumi Adisa, ISSO, NexusBridge Technologies
**Date:** May 2024
**Status:** Complete (Partial SSP for Portfolio Demonstration)

## Purpose

The System Security Plan (SSP) is the primary document in a FedRAMP authorization package. It provides a comprehensive description of the system, its environment, its boundary, and how each of the 325+ FedRAMP Moderate controls is implemented. A complete SSP for a production system would exceed several hundred pages.

This document presents a partial SSP covering the most critical sections: system characterization, boundary description, interconnections, roles and responsibilities, and control implementation narratives for 10 representative controls.

## Section 1: System Identification

| Field | Detail |
|---|---|
| System Name | NexusBridge Grant Management System (GMS) |
| System Abbreviation | NB-GMS |
| System Identifier | DOE-NB-GMS-2024-MOD |
| FedRAMP Unique ID | TBD (assigned upon authorization) |
| System Owner | Dr. Marcus T. Webb, DOE Deputy Director, Research Programs |
| System Type | Major Application |
| Service Model | Software as a Service (SaaS) |
| Deployment Model | Federal Community Cloud (AWS GovCloud US-West) |
| Operational Status | Operational |
| FedRAMP Baseline | Moderate |
| System Description | NexusBridge GMS is a cloud-hosted federal grants management platform supporting approximately 18,000 federal researchers across 8 regional DOE offices. It processes federal grant applications, research funding records, PII, Treasury disbursement instructions, and NSF interagency exchange data. |

## Section 2: System Owner and Authorization Information

| Role | Name | Organization | Contact |
|---|---|---|---|
| System Owner | Dr. Marcus T. Webb | DOE, Research Programs | mwebb@doe.gov (fictional) |
| ISSO | Omowumi Adisa | NexusBridge Technologies | oadisa@nexusbridge.com (fictional) |
| Authorizing Official | Patricia L. Donovan | DOE CISO | pdonovan@doe.gov (fictional) |
| CSP Representative | Daniel R. Osei | NexusBridge Technologies | dosei@nexusbridge.com (fictional) |
| SAISO | Gerald F. Muñoz | DOE CISO Office | gmunoz@doe.gov (fictional) |
| 3PAO Lead | Sandra L. Pryce | ClearPoint Assurance LLC | spryce@clearpoint.com (fictional) |
| Cloud Ops Lead | Jerome K. Okafor | NexusBridge Technologies | jokafor@nexusbridge.com (fictional) |
| Privacy Officer | Helen R. Nguyen | DOE, Office of General Counsel | hnguyen@doe.gov (fictional) |

## Section 3: System Security Categorization

Per FIPS 199 and NIST SP 800-60 Vol. II, NexusBridge GMS is categorized as follows:

**Final Security Category: SC NexusBridge-GMS = {(Confidentiality, MODERATE), (Integrity, MODERATE), (Availability, MODERATE)}**

**Overall Impact Level: MODERATE**

Rationale: The system processes federal grant applications and research funding records. A breach of confidentiality could harm thousands of researchers and expose sensitive DOE program information. Integrity failures could result in financial harm through misdirected grant funds. Availability failures are recoverable within the defined RTO (4 hours) and RPO (1 hour).

## Section 4: System Boundary

The NexusBridge GMS authorization boundary encompasses all NexusBridge-managed components within AWS GovCloud (US-West). Components inside the boundary:

- AWS VPC (dedicated, single-tenant): Contains all application and data components
- Amazon EC2 instances (application servers, web tier)
- Amazon RDS (PostgreSQL database cluster, multi-AZ)
- Amazon S3 (encrypted storage for grant documents and audit logs)
- AWS Application Load Balancer (public-facing HTTPS endpoint)
- AWS CloudTrail, CloudWatch, and Security Hub (logging and monitoring)
- AWS KMS (key management for encryption at rest)
- AWS Systems Manager (administrative access, no direct SSH)

Components outside the boundary (leveraged services):
- AWS infrastructure (physical data centers, hypervisor, networking): Covered by AWS FedRAMP High P-ATO
- DOE Central Identity Provider (IdP): Covered by DOE agency ATO
- NSF Grant Database: Interconnection documented via ISA
- Treasury Disbursement API: Interconnection documented via MOU

## Section 5: System Interconnections

| External System | Owner | Connection Type | Data Exchanged | Agreement | Impact |
|---|---|---|---|---|---|
| DOE Central IdP | DOE CISO Office | SAML 2.0 (HTTPS) | Authentication tokens | ISA-DOE-001 | Moderate |
| NSF Grant Database | NSF CISO | SFTP (dedicated circuit) | Grant application records | ISA-NSF-001 (in progress) | Moderate |
| Treasury Disbursement API | Treasury BFS | REST API (HTTPS, mutual TLS) | Grant payment instructions | MOU-TREAS-001 (in progress) | Moderate |

## Section 7: Control Implementation Narratives (Representative Sample)

### AC-2: Account Management

**Control Requirement:** The organization manages information system accounts, including establishing, activating, modifying, reviewing, disabling, and removing accounts.

**Implementation:** NexusBridge Technologies manages all NexusBridge GMS accounts. AWS IAM is used for infrastructure-level accounts. Application-level user accounts are provisioned through the DOE HR onboarding process. The ISSO receives a provisioning request form signed by the user's manager before creating any account. All accounts are reviewed quarterly by the ISSO and system owner. Accounts for departing employees are disabled within 4 hours of notification from DOE HR and removed within 30 days. Privileged accounts (admin roles) are reviewed monthly.

**Responsibility:** Shared (AWS manages IAM infrastructure; NexusBridge manages provisioning workflows and reviews)

### IA-2: Identification and Authentication (Organizational Users)

**Control Requirement:** The information system uniquely identifies and authenticates organizational users.

**Implementation:** NexusBridge GMS uses federated authentication through the DOE Central Identity Provider (IdP) via SAML 2.0. Users authenticate to the DOE IdP using their DOE Active Directory credentials plus a PIV card or software-based MFA token (Okta Verify). The GMS application validates the SAML assertion and creates a session. No local passwords are stored in NexusBridge GMS. Privileged access for NexusBridge system administrators uses IAM users with hardware MFA (YubiKey) enforced through an IAM policy condition.

**Responsibility:** Shared (DOE IdP manages credential validation; NexusBridge configures SAML integration and enforces MFA at application layer)

### SC-7: Boundary Protection

**Control Requirement:** The information system monitors and controls communications at the external boundary and key internal boundaries.

**Implementation:** The NexusBridge GMS authorization boundary is enforced through AWS VPC architecture. The VPC contains three subnets: public (ALB only), private application (EC2 instances), and private data (RDS). Network ACLs and security groups enforce least-privilege traffic flow between subnets. The ALB is the only public-facing component and only accepts HTTPS on port 443. AWS WAF is deployed on the ALB to inspect and block common web attack patterns.

**Responsibility:** Shared (AWS provides VPC, Security Groups, and NACL infrastructure; NexusBridge configures rules and manages WAF policies)

### IR-4: Incident Handling

**Control Requirement:** The organization implements an incident handling capability for security incidents.

**Implementation:** NexusBridge maintains a formal Incident Response Plan (IRP) approved by AO Patricia L. Donovan. The IRP follows the NIST SP 800-61 Rev 2 incident lifecycle: Preparation, Detection and Analysis, Containment, Eradication, Recovery, and Post-Incident Activity. The ISSO is the incident coordinator. All security incidents are reported to the DOE CISO within 1 hour of detection. Incident response drills are conducted semi-annually.

**Responsibility:** Customer (NexusBridge owns the IRP and all incident response activities)

## Interview Defense Notes

**What is an SSP and why is it the centerpiece of a FedRAMP package?**
The SSP is the document that describes the system and documents how every required control is implemented. Reviewers and the AO rely on the SSP to understand the security posture of the system.

**What is the system boundary and why does it matter?**
The boundary defines what is inside the authorization. Controls apply to everything inside the boundary. Getting the boundary wrong means you might miss controls or overstate what you are responsible for.

**Why is a partial SSP a legitimate portfolio artifact?**
A full SSP for a Moderate system can be 300-500 pages. As a junior analyst, you would own specific sections or specific control families, not the entire document. A partial SSP demonstrating deep knowledge of key sections is more credible than a superficial treatment of all 325 controls.

---
*Prepared by: Omowumi Adisa, ISSO, NexusBridge Technologies*
*System: NexusBridge Grant Management System (GMS) | DOE-NB-GMS-2024-MOD*
*[GitHub Portfolio](https://github.com/Wunmi290)*
