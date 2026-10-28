<div align="center">

![Wave](https://img.shields.io/badge/Wave-3-0550AE?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-SEC-6e7781?style=for-the-badge)

</div>

# DPDP Act Compliance Framework (Phase 1 scoped)

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** 1.0 | **Date:** 2026-10-28 | **Document ID:** SRIS-P1-SEC-006

| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| Title              | DPDP Act Compliance Framework (Phase 1 scoped)                    |
| Software           | SRIS                                                              |
| Software Full Form | Sarathi Railway Information System                                |
| Team Codename      | Project Sarathi                                                   |
| Document ID        | SRIS-P1-SEC-006                                                   |
| Task               | Define data privacy, consent, and erasure logic for DPDP 2023     |
| Document Type      | Detailed Design Document                                          |
| Milestone          | Phase 1 Foundation                                                |
| Classification     | Internal                                                          |
| Version            | 1.0                                                               |
| Date               | 2026-10-28                                                        |
| Author             | Koushal Jha, Lead Architect                                       |
| Approved By        | Koushal Jha, Lead Architect                                       |
| Approval Date      | 2026-10-28                                                        |
| Supersedes         | None (first version)                                              |
| Related Documents  | See Appendix B                                                    |
| Affiliation        | Independent · Not affiliated with CRIS, IRCTC, or Indian Railways |

---

## 1. Introduction

### 1.1 Purpose
This document defines how the SRIS platform implements and enforces the provisions of the Digital Personal Data Protection (DPDP) Act of 2023 for **KOSHIV VENTURES PRIVATED LIMITED**. It outlines the specific architectural mechanisms, such as Crypto-Shredding and Legal Holds, required to guarantee user data privacy, manage consent, and execute the Right to Erasure without compromising the financial integrity of the distributed microservice architecture.

### 1.2 Scope
**In Scope (Phase 1):**
*   Consent Management (versioning and logging).
*   Right to Erasure via Crypto-Shredding.
*   Data Minimization strategies for account registration.
*   Smart Deletion logic and Legal Hold conditions via inter-service mTLS.
*   Third-Party sharing constraints (Payment Gateways).
*   Frontend prohibition against exposing business or compliance logic.

**Out of Scope:**
*   Collection, vaulting, or processing of C4 restricted data (e.g., Aadhaar, PAN) — this is explicitly deferred to Phase 2 per our Data Minimization constraints.

### 1.3 Audience
*   **Legal/Compliance Officers & DPOs:** To audit the system's compliance with Indian privacy laws.
*   **Lead Architect:** To govern the security models.
*   **Backend/Security Engineers:** To implement the Crypto-Shredding middleware and consent APIs within the S1-IAM and S3-Reservation services.

---

## 2. Normative References and Terminology

### 2.1 Normative References
| Document ID | Title | Relevance |
|-------------|-------|-----------|
| [SRIS-P1-ARCH-010](../wave-2-architecture/SRIS-P1-ARCH-010_SecurityArchitectureDocument.md) | Security Architecture Document | Defines the overarching Double-Envelope Zero Trust and Crypto-Shredding concepts. |
| [SRIS-P1-REQ-014](../wave-1-requirements/SRIS-P1-REQ-014_DataPrivacyRequirements.md) | Data Privacy Requirements | The foundational requirement specification for DPDP compliance. |
| `DPDP Act 2023` | Digital Personal Data Protection Act | The legal framework governing this design. |

### 2.2 Terminology
*   **Crypto-Shredding:** The permanent destruction of a user's unique cryptographic KMS key, instantly rendering all their encrypted records (like PNRs) as anonymized, unreadable ciphertext.
*   **Legal Hold:** An automated block on account deletion triggered by active financial states (e.g., pending refunds, open disputes, or upcoming journeys).
*   **Booker Identity:** The anonymized UUID captured at the time of booking to satisfy anti-black-marketing laws, retained even if the original account is crypto-shredded.
*   **C3/C4 Data Classification:** SRIS data tiers. C3 (Sensitive: Name, Phone) is collected minimally; C4 (Restricted: Aadhaar) is prohibited in Phase 1.

---

## 3. Consent Management

### 3.1 V4/V9 Table Architecture
S1-IAM serves as the centralized consent authority for SRIS. Consent state changes are managed structurally via the database migrations defined in `V4__create_consent_records.sql` and `V9__add_consent_versioning.sql`. 

### 3.2 Anonymization Mandate
To ensure that the consent logs themselves do not become a liability or violate audit immutability rules, the consent tables strictly store **only** an anonymized identifier (UUID) mapped to the user, alongside the specific Consent Version they accepted, a timestamp, and an event hash. 

### 3.3 PII-Free Logs
Under no circumstances is plaintext PII (such as a user's Name, Email, or Phone Number) ever written to the consent log tables or the broader audit logs. If a user withdraws consent and triggers the Right to Erasure, the consent logs remain intact as evidence of compliance, but they cannot be tied back to a human identity once the user's primary identity records are shredded.

## 4. Right to Erasure (Crypto-Shredding Flow)

### 4.1 Erasure Execution via KMS
To comply with the DPDP Right to Erasure, SRIS utilizes a Crypto-Shredding architecture rather than standard SQL `DELETE` cascades. When an account is created, S1-IAM provisions a unique cryptographic key for that user in the secure KMS Vault. 

When an account is deleted (and passes all Legal Hold checks), S1-IAM executes the erasure by permanently and irreversibly destroying the user's specific cryptographic key from the KMS.

### 4.2 Ciphertext Retention and Integrity
By destroying the KMS key, all underlying data belonging to that user encrypted with that key—such as historical PNRs residing in S3-Reservation—instantly becomes permanently anonymized ciphertext. 

The physical database rows are **not deleted**. This guarantees that the referential integrity of the distributed database remains intact and preserves the financial, taxation, and analytical audit trails required by other legal frameworks, while fully satisfying the DPDP erasure mandate (since the PII is irretrievably shredded).

---

## 5. Smart Deletion & Legal Hold

### 5.1 The mTLS Inter-Service Check
Account deletion is not a unilateral operation within S1-IAM. Before S1-IAM is permitted to destroy a KMS key, it must execute a synchronous, mTLS-authenticated inter-service call to S3-Reservation to verify the user's current transactional state.

### 5.2 Legal Hold Conditions
S3-Reservation acts as the arbiter of financial state. It will place a **Legal Hold** on the account deletion request if any of the following conditions are met:
1.  An active refund is currently processing for the user.
2.  An open payment dispute or chargeback is recorded against the user.
3.  The user has an upcoming, untravelled journey associated with their account.

### 5.3 Dynamic Frontend Messaging
If a Legal Hold is active, S1-IAM denies the deletion request. The frontend dashboard must capture this denial and dynamically display a specific, user-friendly message, such as: 
*"Account deletion blocked: Refund in progress. Please try again after [Date]."* 

This ensures compliance without locking funds or destroying required operational context.

---

## 6. Data Segregation & Retention Policy

### 6.1 Account Data vs. Booking Data
SRIS strictly segregates data ownership to ensure privacy logic applies accurately:
*   **Account Data (Registration PII):** Data collected during the S1-IAM registration flow (Full Name, Mobile, Email, DOB, State, OTP) is strictly tied to the account lifecycle. Upon a valid account deletion, this data is completely crypto-shredded.
*   **Booking Data (Passenger Details):** PII provided during the actual ticket booking flow (e.g., the names of the passengers travelling) belongs to the passengers, not inherently to the account holder booking the ticket. Therefore, passenger booking data is **never** deleted or shredded as part of an account closure, preserving the historical manifest of the train.

### 6.2 Audit Log Retention
Audit logs generated by the platform (e.g., login events, consent updates) are retained for exactly **365 days**. To ensure this retention does not violate the Right to Erasure, all audit logs are explicitly engineered to be PII-free. They record actions, timestamps, and UUIDs, but never plaintext names, emails, or phone numbers.

## 7. Data Minimization & Anti-Scalping

### 7.1 Registration Minimization
In strict compliance with DPDP data minimization principles, the S1-IAM registration flow is restricted to collecting only the absolute minimum PII required to establish identity, communicate booking status, and prevent fraud.
The permitted registration fields are:
1.  Full Name
2.  Mobile Number
3.  Email Address
4.  Date of Birth (DOB)
5.  State of Residence
6.  OTP (Ephemeral)

The collection of C4 restricted identifiers (e.g., Aadhaar, PAN) is strictly prohibited during Phase 1 registration.

### 7.2 Anti-Scalping and Booker Identity
To comply with Indian anti-black-marketing laws, SRIS must maintain an irrefutable audit trail of the individual who booked a ticket. 
*   **Snapshot Capture:** When a ticket is booked, S3-Reservation captures a snapshot of the Booker's User ID (an anonymized UUID) and securely associates it with the generated PNR.
*   **Legal Retention:** Even if the booking account is subsequently deleted and the primary PII is crypto-shredded, this anonymized Booker ID remains permanently attached to the PNR ciphertext. 
*   **Ticket Delivery:** S3-Reservation dynamically fetches the Account Mobile/Email from S1-IAM via internal mTLS solely at the moment of ticket delivery, ensuring PII is not duplicated or stored redundantly across microservice boundaries.

---

## 8. Third-Party Sharing & Frontend Prohibition

### 8.1 Payment Gateway Payload (Data Minimization)
When SRIS shares data with external third parties, specifically the S5 Payment Gateway integration, strict data minimization is enforced. 
*   The outbound payload transmitted to the payment vendor contains **only** the financial data required to process the transaction (e.g., Transaction Amount, Currency, and Idempotency Key).
*   No unnecessary PII (such as passenger names, ages, or travel destinations) is shared with the payment processor.

### 8.2 India Data Residency
To comply with national security and privacy mandates, all vendor contracts and third-party API integrations must legally and technically guarantee India-only data residency. No PII or financial payloads may be routed through or stored on servers physically located outside the sovereign borders of India.

### 8.3 Frontend Prohibition and Anti-Tampering (Rule 050)
The SRIS frontend applications (web portals and mobile apps) are designated as strictly presentation layers.
*   **Zero Business Logic:** The frontend must expose absolutely zero business, pricing, or DPDP compliance logic that could be reverse-engineered by malicious actors to predict backend processing.
*   **Defense-in-Depth:** While the frontend is untrusted, it must still actively participate in basic perimeter defense. The frontend applications and the Edge WAF must rigorously sanitize inputs and defend against standard attack vectors (SQL Injection, XSS, and basic bot scraping) without revealing the internal server-side topology or security architecture.

---

## 9. Approval

| Role           | Name          | Decision | Date       |
| -------------- | ------------- | -------- | ---------- |
| Lead Architect | Koushal Jha   | Approved | 2026-10-28 |

---

## Revision History

| Version | Date       | Author      | Change           |
| ------- | ---------- | ----------- | ---------------- |
| 1.0     | 2026-10-28 | Koushal Jha | Initial release. |

---

## Appendix A: Not Applicable

Not applicable.

---

## Appendix B: Related Documents

### B.1 Directly Referenced Documents

| Seq  | Document ID      | Document Name                              | Wave | Pri | Tag     |
| ---- | ---------------- | ------------------------------------------ | ---- | --- | ------- |
| 2.10 | [SRIS-P1-ARCH-010](../wave-2-architecture/SRIS-P1-ARCH-010_SecurityArchitectureDocument.md) | Security Architecture Document             | 2    | P1  | FOLLOW  |
| 1.14 | [SRIS-P1-REQ-014](../wave-1-requirements/SRIS-P1-REQ-014_DataPrivacyRequirements.md)  | Data Privacy Requirements                  | 1    | P1  | FOLLOW  |

### B.2 Documents That Reference This Document

| Seq  | Document ID      | Document Name                                    | Why It References                                                              |
| ---- | ---------------- | ------------------------------------------------ | ------------------------------------------------------------------------------ |
| 3.45 | [SRIS-P1-SEC-007](./SRIS-P1-SEC-007_ConsentManagementDataModelPhase1Scoped.md) | Consent Management Data Model (Phase 1 scoped)   | Implements the database tables required by the consent logic defined here.       |

### B.3 Documents This Document Depends On (Upstream)

| Seq  | Document ID      | Document Name                              | Dependency Type |
| ---- | ---------------- | ------------------------------------------ | --------------- |
| 0.0  | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) | Documentation Index and Navigation Map     | Soft            |
| 2.10 | [SRIS-P1-ARCH-010](../wave-2-architecture/SRIS-P1-ARCH-010_SecurityArchitectureDocument.md) | Security Architecture Document             | Hard            |
| 1.14 | [SRIS-P1-REQ-014](../wave-1-requirements/SRIS-P1-REQ-014_DataPrivacyRequirements.md)  | Data Privacy Requirements                  | Hard            |

### B.4 Documents This Document Unblocks (Downstream)

| Seq  | Document ID      | Document Name                                    | Blocked Until |
| ---- | ---------------- | ------------------------------------------------ | ------------- |
| 3.45 | [SRIS-P1-SEC-007](./SRIS-P1-SEC-007_ConsentManagementDataModelPhase1Scoped.md) | Consent Management Data Model (Phase 1 scoped)   | This approved |

### B.5 Master Documentation Index

The complete list of Phase 1 documents is in [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

### B.6 External Reference Documents

| Title                   | Authority | Relevance                                                                 |
| ----------------------- | --------- | ------------------------------------------------------------------------- |
| Digital Personal Data Protection Act, 2023 | Government of India | Legal framework dictating Right to Erasure, data minimization, and consent mandates. |

### B.7 Document Conventions

The conventions for Priority and Tag values are defined in Section 9 of [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.