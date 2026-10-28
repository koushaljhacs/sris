<div align="center">

![Wave](https://img.shields.io/badge/Wave-3-0550AE?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-SEC-6e7781?style=for-the-badge)

</div>

# Consent Management Data Model (Phase 1 scoped)

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** 1.0 | **Date:** 2026-10-28 | **Document ID:** SRIS-P1-SEC-007

| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| Title              | Consent Management Data Model (Phase 1 scoped)                    |
| Software           | SRIS                                                              |
| Software Full Form | Sarathi Railway Information System                                |
| Team Codename      | Project Sarathi                                                   |
| Document ID        | SRIS-P1-SEC-007                                                   |
| Task               | Define the database schema and logic for PII-free consent logging |
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
This document defines the detailed, event-driven database schema and domain logic required to implement the Consent Management module within the S1-IAM microservice for **KOSHIV VENTURES PRIVATED LIMITED**. The primary architectural goal is to capture, version, and manage user consent in a cryptographically secure, append-only ledger that strictly adheres to the "Anonymization Mandate" required by the Digital Personal Data Protection (DPDP) Act.

### 1.2 Scope
This document specifies:
*   The exact table structures for the `V4__create_consent_records.sql` and `V9__add_consent_versioning.sql` database migrations.
*   The Write-Once-Read-Many (WORM) event-sourcing logic required for legally recording consent withdrawals.
*   The integration of envelope encryption to align the consent ledger with the broader Crypto-Shredding architecture.

### 1.3 Audience
*   **Database Administrators:** To execute the V4 and V9 schema migrations.
*   **Security Engineers & DPDP Auditors:** To verify the immutability and anonymity of the consent trails.
*   **Lead Architect:** For overarching governance and approval.

---

## 2. Normative References and Terminology

### 2.1 Normative References
| Document ID | Title | Relevance |
|-------------|-------|-----------|
| [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md) | DPDP Act Compliance Framework (Phase 1) | Mandates the Right to Erasure and PII-free logging rules. |
| [SRIS-P1-ARCH-010](../wave-2-architecture/SRIS-P1-ARCH-010_SecurityArchitectureDocument.md) | Security Architecture Document | Establishes the Crypto-Shredding paradigm. |
| [SRIS-P1-DATA-001](../wave-3-detailed-design/SRIS-P1-DATA-001_DataDesignDocument.md) | Data Design Document | Outlines the baseline PostgreSQL standards. |

### 2.2 Terminology
*   **WORM (Write-Once-Read-Many):** An append-only data storage principle where once data is written, it cannot be modified or deleted, preserving an absolute historical audit trail.
*   **Envelope Encryption:** A process where the data itself is encrypted by a Data Encryption Key (DEK), and the DEK is subsequently encrypted by a Customer Master Key (CMK) managed by the KMS.
*   **Crypto-Shredding:** The deliberate destruction of a user's DEK, rendering all ciphertext associated with that user permanently mathematically irretrievable.
*   **Event Sourcing:** An architectural pattern where state is derived by querying a sequential log of immutable events (e.g., `GRANTED`, then `REVOKED`), rather than querying a mutable state column.

---

## 3. Database Schemas: V4 and V9 Tables

### 3.1 V4 Schema (`V4__create_consent_records.sql`)
The foundational `consent_records` table is designed strictly as an append-only event ledger. It enforces the Anonymization Mandate by actively prohibiting the storage of plaintext identifying information (such as Name, Email, or Phone).

**Table: `consent_records`**
| Column Name | Database Type | Indexing / Constraint | Architectural Purpose |
| :--- | :--- | :--- | :--- |
| `consent_event_id` | `UUID` | `PRIMARY KEY`, `gen_random_uuid()` | Unique identifier for this specific interaction. Prevents sequential enumeration. |
| `subject_id_ciphertext` | `BYTEA` | `NOT NULL`, B-Tree Indexed | The user's system UUID, encrypted via KMS DEK. Replaces plaintext identity. |
| `consent_domain` | `VARCHAR(50)` | `NOT NULL` | The scope of consent (e.g., `TERMS_OF_SERVICE`, `MARKETING_COMMUNICATIONS`). |
| `event_action` | `VARCHAR(20)` | `NOT NULL` | The state transition. Strictly enumerated: `GRANTED` or `REVOKED`. |
| `policy_version_id` | `UUID` | `NOT NULL`, `FOREIGN KEY` | Hard relational link to the V9 `privacy_policy_versions` table. |
| `event_timestamp_utc` | `TIMESTAMPTZ` | `NOT NULL`, `NOW()` | The exact temporal marker of the action in UTC. |
| `consent_artifact_hash` | `BYTEA` | `NOT NULL` | A SHA-256 hash of the transactional payload (IP, user agent, text) for non-repudiation. |

### 3.2 V9 Schema (`V9__add_consent_versioning.sql`)
Consent is legally bound to the specific text presented to the user at the exact moment of agreement. The V9 migration introduces the `privacy_policy_versions` table to track these iterations over time.

**Table: `privacy_policy_versions`**
| Column Name | Database Type | Indexing / Constraint | Architectural Purpose |
| :--- | :--- | :--- | :--- |
| `policy_version_id` | `UUID` | `PRIMARY KEY`, `gen_random_uuid()` | Unique identifier for a specific policy iteration. |
| `semantic_version_tag` | `VARCHAR(20)` | `UNIQUE`, `NOT NULL` | Human-readable identifier (e.g., 'v1.1.0'). |
| `document_sha256` | `BYTEA` | `NOT NULL` | Cryptographic hash proving the legal document stored in S3 has not been altered. |
| `published_timestamp_utc` | `TIMESTAMPTZ` | `NOT NULL` | Exact temporal marker of when this specific policy became active. |
| `is_currently_active` | `BOOLEAN` | `NOT NULL`, `DEFAULT FALSE` | Flag indicating the currently enforced policy. |

When evaluating compliance, S1-IAM cross-references the user's latest `consent_records` row against the `is_currently_active` flag in `privacy_policy_versions` to determine if a re-consent prompt is required upon login.

## 4. WORM (Append-Only) Withdrawal Logic

### 4.1 The Immutability Constraint
Under the Data Protection and Privacy governance standards of SRIS (governed by Rule 114), compliance logs and consent event trails must maintain absolute tamper-evidence and historical continuity. 

To achieve this, the `consent_records` table is architected strictly as a Write-Once-Read-Many (WORM), append-only ledger. 
*   **Prohibition of Mutable State:** The application layer and database schemas strictly prohibit the execution of SQL `UPDATE` or `DELETE` statements against the `consent_records` table. Changing a user's preference from granted to revoked via a direct row mutation destroys the historical proof of prior agreement, violating regulatory non-repudiation mandates.

### 4.2 Withdrawal Execution via Insert
When a user explicitly decides to withdraw their consent (e.g., via the privacy preference center):
1.  The S1-IAM service captures the withdrawal request context.
2.  Instead of modifying prior records, the application executes a clean, atomic `INSERT` statement into the `consent_records` ledger.
3.  This new event record is populated with `event_action = 'REVOKED'`, a fresh `event_timestamp_utc`, the associated `policy_version_id`, and a newly generated `consent_event_id` and `consent_artifact_hash`.

### 4.3 State Projection
Because the data model relies on event sourcing rather than static columns, determining a user's current consent posture requires resolving the chronological sequence of events. 
*   **Projection Query:** The application layer evaluates current consent by querying the most recent event row for a given encrypted subject identifier and consent domain, utilizing an ordering clause sorted by timestamp descending:
    ```sql
    SELECT event_action, policy_version_id, event_timestamp_utc
    FROM consent_records 
    WHERE subject_id_ciphertext = $1 AND consent_domain = $2
    ORDER BY event_timestamp_utc DESC 
    LIMIT 1;
    ```
*   **Performance Cache:** To prevent continuous read overhead on high-throughput paths, the projected active status is mirrored into an eventually consistent distributed cache (Redis) via asynchronous event streams.

---

## 5. Crypto-Shredding Alignment

### 5.1 Envelope Encryption Integration
To bridge the gap between immutable WORM audit requirements and the DPDP Right to Erasure, SRIS integrates an advanced Envelope Encryption model with the consent architecture:
*   **Data Encryption Key (DEK):** Every registered user is assigned a unique Data Encryption Key managed within the centralized KMS/Vault infrastructure.
*   **Ciphertext Obfuscation:** The user's primary system UUID is encrypted using their specific DEK before being written to the `subject_id_ciphertext` column of the `consent_records` table. 

### 5.2 Execution of the Right to Erasure via KMS Key Deletion
When a verified Right to Erasure request is processed for an account:
1.  S1-IAM bypasses any requirement to execute row-level deletes across historical audit ledgers.
2.  Instead, the platform permanently and irreversibly destroys the user's specific DEK from the KMS Vault.
3.  **Orphaned Ciphertext:** Because the cryptographic key has been annihilated, the `subject_id_ciphertext` values stored in the `consent_records` table instantly become mathematically unrecoverable, random-noise ciphertext. 

### 5.3 Audit Integrity Preservation
Crypto-shredding ensures a dual-compliance victory:
*   **DPDP Compliance:** The physical identity and relational link of the user are permanently destroyed, satisfying the legal mandate for data erasure.
*   **Audit & Retention Integrity:** The structural rows within the `consent_records` table remain entirely intact, preserving volume statistics, temporal integrity, and non-repudiation trails without retaining plaintext PII or violating Rule 114 immutability constraints.

## 6. Approval

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
| 3.44 | [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md) | DPDP Act Compliance Framework (Phase 1)    | 3    | P0  | UNBLOCK |
| 2.10 | [SRIS-P1-ARCH-010](../wave-2-architecture/SRIS-P1-ARCH-010_SecurityArchitectureDocument.md) | Security Architecture Document             | 2    | P1  | FOLLOW  |
| 3.1  | [SRIS-P1-DATA-001](../wave-3-detailed-design/SRIS-P1-DATA-001_DataDesignDocument.md) | Data Design Document                       | 3    | P0  | UNBLOCK |

### B.2 Documents That Reference This Document

| Seq  | Document ID      | Document Name                                    | Why It References                                                              |
| ---- | ---------------- | ------------------------------------------------ | ------------------------------------------------------------------------------ |
| 3.2  | [SRIS-P1-DATA-002](../wave-3-detailed-design/SRIS-P1-DATA-002_LogicalDataModelPerService.md) | Logical Data Model (per service)                 | Incorporates the consent tables defined here into the broader logical model.     |
| 3.3  | [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)| Physical Database Schema Document                | Synthesizes the final SQL execution blocks for `V4` and `V9` migrations.         |

### B.3 Documents This Document Depends On (Upstream)

| Seq  | Document ID      | Document Name                              | Dependency Type |
| ---- | ---------------- | ------------------------------------------ | --------------- |
| 0.0  | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) | Documentation Index and Navigation Map     | Soft            |
| 3.44 | [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md) | DPDP Act Compliance Framework (Phase 1)    | Hard            |

### B.4 Documents This Document Unblocks (Downstream)

| Seq  | Document ID      | Document Name                                    | Blocked Until |
| ---- | ---------------- | ------------------------------------------------ | ------------- |
| 3.2  | [SRIS-P1-DATA-002](../wave-3-detailed-design/SRIS-P1-DATA-002_LogicalDataModelPerService.md) | Logical Data Model (per service)                 | This approved |
| 3.3  | [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)| Physical Database Schema Document                | This approved |

### B.5 Master Documentation Index

The complete list of Phase 1 documents is in [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

### B.6 External Reference Documents

| Title                   | Authority | Relevance                                                                 |
| ----------------------- | --------- | ------------------------------------------------------------------------- |
| Digital Personal Data Protection Act, 2023 | Government of India | Legal framework dictating data minimization, consent tracking, and erasure mandates. |

### B.7 Document Conventions

The conventions for Priority and Tag values are defined in Section 9 of [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.