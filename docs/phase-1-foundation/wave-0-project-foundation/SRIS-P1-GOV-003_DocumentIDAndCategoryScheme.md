<div align="center">

![Wave](https://img.shields.io/badge/Wave-0-0550AE?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-GOV-6e7781?style=for-the-badge)

</div>

# Document ID and Category Scheme

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** 1.0 | **Date:** 2026-10-11 | **Document ID:** SRIS-P1-GOV-003

| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| Title              | Document ID and Category Scheme                                   |
| Software           | SRIS                                                              |
| Software Full Form | Sarathi Railway Information System                                |
| Team Codename      | Project Sarathi                                                   |
| Document ID        | SRIS-P1-GOV-003                                                   |
| Task               | Define the document ID format and the category code scheme        |
| Document Type      | Standard Document                                                 |
| Milestone          | Phase 1 Foundation                                                |
| Classification     | Internal                                                          |
| Version            | 1.0                                                               |
| Date               | 2026-10-11                                                        |
| Author             | Koushal Jha, Lead Architect                                       |
| Approved By        | Koushal Jha, Lead Architect                                       |
| Approval Date      | 2026-10-11                                                        |
| Supersedes         | None (first version)                                              |
| Related Documents  | See Appendix B                                                    |
| Affiliation        | Independent · Not affiliated with CRIS, IRCTC, or Indian Railways |

---

## Table of Contents

1. [Introduction](#1-introduction)
   - [1.1 Purpose](#11-purpose)
   - [1.2 Scope](#12-scope)
   - [1.3 Audience](#13-audience)
2. [Document ID Format](#2-document-id-format)
   - [2.1 Full Format](#21-full-format)
   - [2.2 Meaning of Each Part](#22-meaning-of-each-part)
   - [2.3 Character and Case Rules](#23-character-and-case-rules)
   - [2.4 Validation Pattern](#24-validation-pattern)
   - [2.5 Reading Hyphenated Category Codes](#25-reading-hyphenated-category-codes)
3. [Category Codes](#3-category-codes)
   - [3.1 The 15 Category Codes](#31-the-15-category-codes)
   - [3.2 Choosing a Category](#32-choosing-a-category)
   - [3.3 Rules for Adding or Changing Categories](#33-rules-for-adding-or-changing-categories)
4. [Sequence Numbers](#4-sequence-numbers)
   - [4.1 Three-Digit Rule](#41-three-digit-rule)
   - [4.2 Separate Counter per Category](#42-separate-counter-per-category)
   - [4.3 Allocation](#43-allocation)
   - [4.4 Permanence, Gaps, and Reuse](#44-permanence-gaps-and-reuse)
5. [Relationship to Other Conventions](#5-relationship-to-other-conventions)
   - [5.1 File Names](#51-file-names)
   - [5.2 Folder Structure](#52-folder-structure)
   - [5.3 Badges and Metadata](#53-badges-and-metadata)
   - [5.4 Cross-References](#54-cross-references)
   - [5.5 Phase Code and Priority Value](#55-phase-code-and-priority-value)
6. [Examples](#6-examples)
   - [6.1 Correct IDs](#61-correct-ids)
   - [6.2 Incorrect IDs](#62-incorrect-ids)
7. [Approval](#7-approval)

- [Revision History](#revision-history)
- [Appendix A: Not Applicable](#appendix-a-not-applicable)
- [Appendix B: Related Documents](#appendix-b-related-documents)

---

## 1. Introduction

### 1.1 Purpose

This document defines the Document ID format and the category code scheme used across the Phase 1 documentation of SRIS. It formalises what the register in [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map lists, and what [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard refers to when it requires a Document ID.

The scheme gives every Phase 1 document one identifier that is unambiguous and can be checked by a script. A document can then be named, linked, sorted, and found without relying on its title.

### 1.2 Scope

In scope:

- The format of the Document ID and the meaning of each part.
- The character and case rules for an ID.
- The 15 category codes and their definitions.
- The sequence number rules, including allocation, permanence, and reuse.
- The rules for adding or changing categories.
- The relationship between the ID and the file name, folder, badge, and cross-references.
- Examples of correct and incorrect IDs.

Out of scope:

- The complete list of Phase 1 documents. This is the register in [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.
- The document template, header block, and vocabulary standards. These belong to [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.
- Identifiers used outside documents, such as board cards, commits, and branches.
- The numbering of documents in phases after Phase 1.

### 1.3 Audience

Document authors use this document to allocate and write IDs correctly. Reviewers use it to check that an ID, its file name, and its badge agree. Anyone writing a script, such as a link checker or a pre-commit hook, uses it to validate IDs. Project supervisors use it to read an ID without needing the register.

---

## 2. Document ID Format

### 2.1 Full Format

Every Phase 1 document has exactly one Document ID in this format:

`SRIS-P1-<CATEGORY>-<NNN>`

For example, this document is `SRIS-P1-GOV-003`.

### 2.2 Meaning of Each Part

| Seq | Part     | Example Value | Meaning                                                          |
| --- | -------- | ------------- | ---------------------------------------------------------------- |
| 1   | SRIS     | SRIS          | Software code. Identifies the project. Fixed for every document. |
| 2   | P1       | P1            | Phase code. The letter P followed by the phase number.           |
| 3   | CATEGORY | GOV           | One of the 15 category codes defined in Section 3.               |
| 4   | NNN      | 003           | Three-digit sequence number within the category.                 |

The ID does not contain the wave, the version, the title, or the priority. These are held in the Wave badge, the Version field, the Title field, and Appendix B respectively.

### 2.3 Character and Case Rules

An ID follows these rules:

- It uses only uppercase letters A to Z, digits 0 to 9, and the hyphen.
- It contains no spaces, no underscores, no lowercase letters, and no other punctuation.
- The hyphen separates the four parts. It also appears inside two category codes, NFR-HOLD and NOTES-AI.
- The underscore is never part of an ID. It is reserved for separating the ID from the document name in a file name (see [Section 5.1](#51-file-names)).

### 2.4 Validation Pattern

An ID is valid when it matches this pattern:

`^SRIS-P1-(GOV|DEV|REQ|ARCH|DATA|API|UI|SEC|TEST|INF|OPS|PM|USR|NFR-HOLD|NOTES-AI)-(?!000)[0-9]{3}$`

Any tool that checks IDs uses this pattern. It does not count hyphen-separated fields, because two category codes contain a hyphen.

### 2.5 Reading Hyphenated Category Codes

Two category codes contain a hyphen, so an ID that uses them has five hyphen-separated fields instead of four. For example, `SRIS-P1-NFR-HOLD-001` splits into `SRIS`, `P1`, `NFR`, `HOLD`, and `001`.

To read an ID unambiguously:

1. The first field is always `SRIS` and the second is always the phase code.
2. The last field is always the three-digit sequence number.
3. Everything between the second and the last field, joined by a hyphen, is the category code.

By this rule the category code of `SRIS-P1-NFR-HOLD-001` is `NFR-HOLD`, and its sequence number is `001`.

---

## 3. Category Codes

### 3.1 The 15 Category Codes

| Seq | Code      | Category Name                     | Definition                                                                                                                                  |
| --- | --------- | --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | GOV       | Governance                        | Project governance records: documentation standards, conventions, registers, and decision rules for the documentation set.                  |
| 2   | DEV       | Developer Standards               | Standards and guides for people writing code: coding conventions, branching, code review, and local tooling.                                |
| 3   | REQ       | Requirements                      | Business, functional, and user requirements, including use cases and acceptance criteria.                                                   |
| 4   | ARCH      | Architecture                      | System structure and technical decisions: service boundaries, component views, integration, and design decisions.                           |
| 5   | DATA      | Data Design                       | Data models, schemas, data dictionaries, retention rules, and migration rules.                                                              |
| 6   | API       | API Design                        | Interface contracts: endpoints, request and response formats, error handling, and API versioning.                                           |
| 7   | UI        | User Interface Design             | Screens, navigation, wireframes, and design guidelines, including accessibility rules.                                                      |
| 8   | SEC       | Security                          | Threat models, authentication, authorisation, data protection, and security controls.                                                       |
| 9   | TEST      | Testing                           | Test strategy, test plans, test cases, and test reports.                                                                                    |
| 10  | INF       | Infrastructure                    | Environments, hosting, networking, and the set-up of build and delivery pipelines.                                                          |
| 11  | OPS       | Operations                        | Deployment procedures, monitoring, backup, incident handling, and runbooks.                                                                 |
| 12  | PM        | Project Management                | Plans, schedules, risk and issue handling, tracking rules, and reporting.                                                                   |
| 13  | USR       | User Support                      | User guides, training material, frequently asked questions, and help content.                                                               |
| 14  | NFR-HOLD  | Non-Functional Requirements, Held | Non-functional requirements such as performance, availability, scalability, and portability targets, kept under their own code apart from REQ. |
| 15  | NOTES-AI  | AI Working Notes                  | Working aids that record prompts, briefs, and context notes used to guide AI assistants on the project. They are kept in the register as supporting artefacts, not as formal deliverables. |

### 3.2 Choosing a Category

A document has exactly one category. The category is chosen by the main subject of the document, that is, by the kind of decision or record the document owns.

If a document touches several subjects, it takes the category of its main subject. The other subjects are covered by hyperlinks to the documents that own them, in line with the self-contained document rule.

### 3.3 Rules for Adding or Changing Categories

The set of categories is locked at 15 for Phase 1. During Phase 1:

- No category is added, removed, renamed, or merged.
- The meaning of a category does not change.
- A need that no category covers is handled by choosing the nearest category and stating the reason in the Scope section of the document.

If the Lead Architect decides that a change is unavoidable, the change is made through a new version of this document with a new Revision History row. The register in [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map and the validation pattern in [Section 2.4](#24-validation-pattern) are updated in the same change.

---

## 4. Sequence Numbers

### 4.1 Three-Digit Rule

The sequence number is always three digits, written with leading zeros: `001`, `002`, `003`, up to `999`. The forms `1`, `01`, and `0001` are not valid. The number `000` is not used, so every category starts at `001`.

Each category holds at most 999 documents. Phase 1 has 180 documents across 15 categories, so no category approaches this limit. Widening the sequence to four digits would be a change to this document, not a local decision.

### 4.2 Separate Counter per Category

Each category has its own counter. The sequence in one category does not affect the sequence in another.

For example, `SRIS-P1-GOV-001` and `SRIS-P1-ARCH-001` both exist. Each is the first document of its own category. The sequence number alone never identifies a document. It must be read together with the category.

### 4.3 Allocation

The next number in a category is the highest number already allocated in that category plus one. Numbers are taken from the register in [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

A number is allocated when the document is entered in the register, before the document is written. Two documents never share an ID.

### 4.4 Permanence, Gaps, and Reuse

An ID can be corrected only while its document has never been committed. After the first commit, the ID is permanent. It does not change when the title, the wave, or the file name changes.

If a document is withdrawn, its ID is retired. The ID stays in the register and is never given to another document. A gap in a category sequence therefore means a retired ID, not a free number.

---

## 5. Relationship to Other Conventions

### 5.1 File Names

The Document ID is the first part of the file name. The file name format is:

`<Document ID>_<DocumentNameInPascalCase>.md`

The underscore separates the ID from the document name. Everything before the first underscore is the Document ID. For example:

- `SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md`
- `SRIS-P1-ARCH-001_MicroservicesIdentification.md`

The file name contains no version. If a title changes, the document name part of the file name changes with it, and the ID part stays the same.

### 5.2 Folder Structure

The category does not decide the folder. The wave decides the folder. A document is stored in the wave folder that matches its Wave badge, under `docs/phase-1-foundation/`.

For example, this document has category GOV and Wave 0, so it is stored in `docs/phase-1-foundation/wave-0-project-foundation/`. A document with category ARCH can sit in Wave 2 and be stored in `docs/phase-1-foundation/wave-2-architecture/`. The ID does not encode the wave, so moving a document between waves does not change its ID.

### 5.3 Badges and Metadata

The Category badge shows the category code from the ID. The Document ID field in the metadata table and the Document ID in the metadata blockquote carry the full ID.

In a badge URL a single hyphen separates the label, the message, and the colour. A hyphen inside the category code is therefore written as two hyphens. The Category badge URLs for the two hyphenated codes end as follows:

- NFR-HOLD: `Category-NFR--HOLD-6e7781`
- NOTES-AI: `Category-NOTES--AI-6e7781`

The badge still displays the code with a single hyphen. All other category codes are written as they appear in [Section 3.1](#31-the-15-category-codes).

### 5.4 Cross-References

The Document ID is the link text of every cross-reference to a document. The link target is a relative path built from the file name in [Section 5.1](#51-file-names) and the wave folder in [Section 5.2](#52-folder-structure).

Within the same wave, the path is `./<File Name>`. Across waves, it is `../wave-N-<wave-name>/<File Name>`. For example, a link from a Wave 0 document to the Wave 2 architecture document uses `../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md`.

### 5.5 Phase Code and Priority Value

The `P1` in a Document ID is the phase code. It is unrelated to the Priority value `P1` used in Appendix B tables. The two use the same letters but mean different things. The phase code identifies the phase a document belongs to. The Priority value says how urgent a document is. The conventions for Priority values are defined in [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.

---

## 6. Examples

The IDs in this section are shown as plain text in code format because they illustrate the pattern. They are not cross-references to documents.

### 6.1 Correct IDs

| Seq | ID                      | Category  | Reading                                                  |
| --- | ----------------------- | --------- | -------------------------------------------------------- |
| 1   | `SRIS-P1-GOV-001`       | GOV       | First Governance document of Phase 1.                    |
| 2   | `SRIS-P1-GOV-003`       | GOV       | Third Governance document. This document.                |
| 3   | `SRIS-P1-ARCH-001`      | ARCH      | First Architecture document. Own counter, separate from GOV. |
| 4   | `SRIS-P1-API-012`       | API       | Twelfth API Design document.                             |
| 5   | `SRIS-P1-NFR-HOLD-001`  | NFR-HOLD  | First held Non-Functional Requirements document.         |
| 6   | `SRIS-P1-NOTES-AI-004`  | NOTES-AI  | Fourth AI Working Notes document.                        |

### 6.2 Incorrect IDs

| Seq | Incorrect ID               | Problem                                           | Correct Form                         |
| --- | -------------------------- | ------------------------------------------------- | ------------------------------------ |
| 1   | `SRIS-P1-GOV-3`            | Sequence has one digit.                           | `SRIS-P1-GOV-003`                    |
| 2   | `SRIS-P1-GOV-03`           | Sequence has two digits.                          | `SRIS-P1-GOV-003`                    |
| 3   | `SRIS-P1-GOV-0003`         | Sequence has four digits.                         | `SRIS-P1-GOV-003`                    |
| 4   | `SRIS-P1-GOV-000`          | Sequence starts at 001.                           | `SRIS-P1-GOV-001`                    |
| 5   | `SRIS-P1-gov-003`          | Category code is lowercase.                       | `SRIS-P1-GOV-003`                    |
| 6   | `SRIS-P1-GOV_003`          | Underscore used as a separator.                   | `SRIS-P1-GOV-003`                    |
| 7   | `SRIS-GOV-003`             | Phase code is missing.                            | `SRIS-P1-GOV-003`                    |
| 8   | `SRIS-P2-GOV-003`          | Phase code P2 is not used by Phase 1 documents.   | `SRIS-P1-GOV-003`                    |
| 9   | `SRIS-P1-DOC-001`          | DOC is not one of the 15 category codes.          | A code from Section 3.1              |
| 10  | `SRIS-P1-NFR-001`          | NFR alone is not a code. The code is NFR-HOLD.    | `SRIS-P1-NFR-HOLD-001`               |
| 11  | `SRIS-P1-GOV-003-v1.0`     | Version appended to the ID.                       | `SRIS-P1-GOV-003`                    |

---

## 7. Approval

| Role           | Name        | Decision | Date       |
| -------------- | ----------- | -------- | ---------- |
| Lead Architect | Koushal Jha | Approved | 2026-10-11 |

---

## Revision History

| Version | Date       | Author      | Change                                                                                      |
| ------- | ---------- | ----------- | ------------------------------------------------------------------------------------------- |
| 1.0     | 2026-10-11 | Koushal Jha | Initial version. Defines the Document ID format, the 15 category codes, and sequence rules. |

---

## Appendix A: Not Applicable

Not applicable.

---

## Appendix B: Related Documents

### B.1 Directly Referenced Documents

| Seq | Document ID                                                                                   | Document Name                          | Wave | Pri | Tag     |
| --- | --------------------------------------------------------------------------------------------- | -------------------------------------- | ---- | --- | ------- |
| 1   | [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md)                    | Documentation Index and Navigation Map | 0    | P0  | UNBLOCK |
| 2   | [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md)                              | Document Template Standard             | 0    | P0  | UNBLOCK |

### B.2 Documents That Reference This Document

Every Phase 1 document carries an ID defined by this document, so the referencing documents are too many to list here. The complete list is in the register described in [B.5](#b5-master-documentation-index).

### B.3 Documents This Document Depends On (Upstream)

| Seq | Document ID                                                                | Document Name                          | Dependency Type |
| --- | -------------------------------------------------------------------------- | -------------------------------------- | --------------- |
| 1   | [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) | Documentation Index and Navigation Map | Soft            |
| 2   | [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md)           | Document Template Standard             | Hard            |

### B.4 Documents This Document Unblocks (Downstream)

All Phase 1 documents other than the two listed in B.3 depend on the ID scheme defined here. The complete list is in the register described in [B.5](#b5-master-documentation-index).

### B.5 Master Documentation Index

The complete list of Phase 1 documents is in [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

### B.6 External Reference Documents

None.

### B.7 Document Conventions

The conventions for Priority and Tag values are defined in [Section 9](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#9-vocabulary-standards) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.