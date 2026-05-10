# Step 1: FIPS 199 Security Categorization Workbook

**Project Title:** FIPS 199 Security Categorization Workbook for NexusBridge Grant Management System
**System Reference:** NexusBridge Grant Management System (GMS) | DOE-NB-GMS-2024-MOD
**Framework / Standard:** FIPS 199, NIST SP 800-60 Volume II Rev 1
**Author:** Omowumi Adisa, ISSO, NexusBridge Technologies
**Date:** May 2024
**Status:** Complete

## Purpose

Step 1 of the NIST Risk Management Framework requires the system owner and ISSO to formally categorize the information system based on the potential impact that a loss of confidentiality, integrity, or availability would have on organizational operations, assets, or individuals. This categorization drives control selection in Step 2 and all subsequent authorization activities.

For NexusBridge GMS, categorization was performed using FIPS 199 and NIST SP 800-60 Volume II Rev 1. The categorization was reviewed and approved by AO Patricia L. Donovan and SAISO Gerald F. Muñoz before SSP development began.

## System Overview for Categorization

| Field | Detail |
|---|---|
| System Name | NexusBridge Grant Management System (GMS) |
| System ID | DOE-NB-GMS-2024-MOD |
| ISSO | Omowumi Adisa, NexusBridge Technologies |
| System Owner | Dr. Marcus T. Webb, DOE Deputy Director, Research Programs |
| Authorizing Official | Patricia L. Donovan, DOE CISO |
| SAISO | Gerald F. Muñoz, DOE Sr. Agency Information Security Officer |
| Categorization Completed | April 5, 2024 |
| AO Approval Date | April 12, 2024 |

## FIPS 199 Categorization Methodology

FIPS 199 defines three security objectives: Confidentiality, Integrity, and Availability. Each objective is evaluated at three impact levels: Low, Moderate, or High. The system impact level is determined by identifying all information types processed, stored, or transmitted by the system, categorizing each using SP 800-60 Vol. II, and applying the high-water mark principle.

## Information Type Identification and Categorization

| # | Information Type | SP 800-60 Identifier | Confidentiality | Integrity | Availability |
|---|---|---|---|---|---|
| 1 | Federal Grant Application Data | C.3.2.1 | Moderate | Moderate | Moderate |
| 2 | Research Funding Records | C.3.2.2 | Moderate | High | Moderate |
| 3 | Personally Identifiable Information (PII) | C.3.5.8 | Moderate | Moderate | Low |
| 4 | Grant Payment and Disbursement Records | C.3.2.3 | Moderate | High | Moderate |
| 5 | Audit and Accountability Logs | D.16.1 | Low | Moderate | Low |
| 6 | System Configuration Data | D.16.2 | Low | Moderate | Low |
| 7 | User Account and Access Records | D.17.1 | Moderate | Moderate | Low |
| 8 | Incident Response Records | D.16.3 | Low | Low | Low |
| 9 | Treasury Disbursement Instructions | C.3.2.4 | Moderate | High | Moderate |
| 10 | NSF/DOE Interagency Data Exchange Records | C.3.2.5 | Moderate | Moderate | Low |

## High-Water Mark Analysis

| Security Objective | Highest Impact Level Identified | Information Type Driving the Rating |
|---|---|---|
| Confidentiality | Moderate | Grant Applications, PII, Funding Records |
| Integrity | High | Research Funding Records, Treasury Disbursement Instructions |
| Availability | Moderate | Grant Application Data, Disbursement Records |

## Rationale for Integrity High Rating

The Research Funding Records and Treasury Disbursement Instructions information types were elevated to High Integrity based on the following rationale: unauthorized modification of federal research grant awards or disbursement instructions could result in direct financial harm to research institutions, potential fraud or mispayment of federal funds, and significant reputational and legal consequences for DOE. This elevation was documented in a formal deviation memo reviewed by AO Patricia L. Donovan on April 12, 2024.

## Agency Adjustment: Downgrade of Integrity to Moderate

After consultation with the SAISO and the system owner, AO Patricia L. Donovan approved a downgrade of the Integrity impact from High to Moderate based on compensating controls: treasury disbursement API transactions are cryptographically signed using HMAC-SHA256, validated before processing, logged in immutable CloudTrail records, and reconciled against Treasury records daily.

## Final Approved Security Category

**SC NexusBridge-GMS = {(Confidentiality, MODERATE), (Integrity, MODERATE), (Availability, MODERATE)}**

**Overall System Impact Level: MODERATE**

This categorization determines that NexusBridge GMS will use the FedRAMP Moderate control baseline (325+ controls per NIST SP 800-53B).

## Approval and Sign-Off

| Role | Name | Organization | Date |
|---|---|---|---|
| ISSO | Omowumi Adisa | NexusBridge Technologies | April 5, 2024 |
| System Owner | Dr. Marcus T. Webb | DOE, Research Programs | April 8, 2024 |
| SAISO | Gerald F. Muñoz | DOE CISO Office | April 11, 2024 |
| Authorizing Official | Patricia L. Donovan | DOE CISO | April 12, 2024 |
| Privacy Officer | Helen R. Nguyen | DOE Office of General Counsel | April 9, 2024 |

## Interview Defense Notes

**What is FIPS 199 and why does it matter?**
FIPS 199 is a federal standard that defines how to categorize information systems based on the potential impact of a security failure. The categorization determines which control baseline applies, which in turn determines how much security work the system must do to get authorized.

**What is the high-water mark principle?**
It means you look at all the information types in the system and take the highest impact level for each security objective (C, I, A) across all of them. The highest one becomes the system-level value for that objective.

**Why was NexusBridge GMS categorized as Moderate overall?**
The high-water mark produced Moderate for Confidentiality and Moderate for Availability. Integrity was initially High due to grant funding and disbursement data, but was downgraded to Moderate after the AO reviewed compensating controls, resulting in an overall Moderate system.

**What is the difference between a preliminary and a final security category?**
The preliminary category comes directly from the high-water mark analysis. The final category reflects any AO-approved adjustments based on risk analysis and compensating controls.

---
*Prepared by: Omowumi Adisa, ISSO, NexusBridge Technologies*
*System: NexusBridge Grant Management System (GMS) | DOE-NB-GMS-2024-MOD*
*[GitHub Portfolio](https://github.com/Wunmi290)*
