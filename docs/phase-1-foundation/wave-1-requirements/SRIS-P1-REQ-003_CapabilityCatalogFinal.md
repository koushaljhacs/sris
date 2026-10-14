<div align="center">

![Wave](https://img.shields.io/badge/Wave-1-0550AE?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-REQ-6e7781?style=for-the-badge)

</div>

# Capability Catalog (Final)

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** 1.0 | **Date:** 2026-10-14 | **Document ID:** SRIS-P1-REQ-003

| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| Title              | Capability Catalog (Final)                                        |
| Software           | SRIS                                                              |
| Software Full Form | Sarathi Railway Information System                                |
| Team Codename      | Project Sarathi                                                   |
| Document ID        | SRIS-P1-REQ-003                                                   |
| Task               | Fix the final locked list of Phase 1 business capabilities        |
| Document Type      | Requirements Document                                             |
| Milestone          | Phase 1 Foundation                                                |
| Classification     | Internal                                                          |
| Version            | 1.0                                                               |
| Date               | 2026-10-14                                                        |
| Author             | Koushal Jha, Lead Architect                                       |
| Approved By        | Koushal Jha, Lead Architect                                       |
| Approval Date      | 2026-10-14                                                        |
| Supersedes         | None (first version)                                              |
| Related Documents  | See Appendix B                                                    |
| Affiliation        | Independent · Not affiliated with CRIS, IRCTC, or Indian Railways |

---

## Table of Contents

1. [Introduction](#1-introduction)
   - [1.1 Purpose](#11-purpose)
   - [1.2 Scope](#12-scope)
   - [1.3 Audience](#13-audience)
   - [1.4 Terminology and Conventions](#14-terminology-and-conventions)
2. [Capability Model and Governance Rules](#2-capability-model-and-governance-rules)
   - [2.1 Capability Definition and Granularity](#21-capability-definition-and-granularity)
   - [2.2 Capability Identification and Permanence Rules](#22-capability-identification-and-permanence-rules)
   - [2.3 Baseline Lock and Revision Rules](#23-baseline-lock-and-revision-rules)
3. [Capability Domains Overview](#3-capability-domains-overview)
   - [3.1 Phase 1 Capability Domains](#31-phase-1-capability-domains)
   - [3.2 Domain to Bounded Context Mapping](#32-domain-to-bounded-context-mapping)
4. [Phase 1 Capability Catalog](#4-phase-1-capability-catalog)
   - [4.1 Identity and Access](#41-identity-and-access)
   - [4.2 Railway Master Data](#42-railway-master-data)
   - [4.3 Fare and Pricing](#43-fare-and-pricing)
   - [4.4 Inventory and Quota](#44-inventory-and-quota)
   - [4.5 Booking and Ticketing](#45-booking-and-ticketing)
   - [4.6 Payment](#46-payment)
   - [4.7 Search and Discovery](#47-search-and-discovery)
   - [4.8 Notification](#48-notification)
5. [Service Ownership and Booking Flow Alignment](#5-service-ownership-and-booking-flow-alignment)
   - [5.1 Capability Ownership by Microservice and Module](#51-capability-ownership-by-microservice-and-module)
   - [5.2 Capability Mapping to the Ten Step Booking Flow](#52-capability-mapping-to-the-ten-step-booking-flow)
   - [5.3 User Surface Capability Consumption](#53-user-surface-capability-consumption)
6. [Deferred and Out of Scope Capabilities](#6-deferred-and-out-of-scope-capabilities)
   - [6.1 Resolution of Provisional Deferrals](#61-resolution-of-provisional-deferrals)
   - [6.2 Deferred Railway Ecosystem Catalog](#62-deferred-railway-ecosystem-catalog)
   - [6.3 Permanent Phase 1 Exclusions](#63-permanent-phase-1-exclusions)
7. [Capability Traceability](#7-capability-traceability)
   - [7.1 Upstream Traceability and Source Reconciliation](#71-upstream-traceability-and-source-reconciliation)
   - [7.2 Downstream Specification Ownership Map](#72-downstream-specification-ownership-map)
8. [Approval](#8-approval)

- [Revision History](#revision-history)
- [Appendix A: Not Applicable](#appendix-a-not-applicable)
- [Appendix B: Related Documents](#appendix-b-related-documents)

---

## 1. Introduction

### 1.1 Purpose

This document is the Capability Catalog (Final) of Phase 1 of SRIS (Sarathi Railway Information System). It fixes the locked, final list of business capabilities that Phase 1 provides, and it is the fourth index document of the register, alongside [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map, [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md) — Document ID and Category Scheme, and [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary.

This document replaces the provisional capability lists recorded in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document, [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification, and [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD), and it resolves the deferral confirmations tracked as OI-3 in [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md).

### 1.2 Scope

**In scope**

- The definition of a Phase 1 business capability and its granularity.
- The capability identification scheme and its permanence rules.
- The eight Phase 1 capability domains and their order.
- The complete, numbered catalog of Phase 1 capabilities.
- The owning microservice and internal module for each capability.
- The mapping of capabilities to the ten-step booking flow.
- The mapping of capabilities to the two user-facing surfaces.
- The formally deferred capabilities and the permanently excluded items.
- The upstream and downstream traceability of every capability.

**Out of scope**

- The project vision, mission, scope, deliverables, success criteria, constraints, and assumptions, which are defined in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document.
- The business requirements, business rules, and delivery requirements, which are defined in [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD).
- Software requirements as software requirements, which belong to [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software Requirements Specification (SRS).
- Non-functional requirements and quality attributes, which belong to [SRIS-P1-REQ-005](./SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md) — Non-Functional Requirements (ISO 25010) and to [SRIS-P1-NFR-HOLD-001](../wave-9-supporting-artifacts/SRIS-P1-NFR-HOLD-001_LoadModelAndResourceFitCheckHolding.md) — Load Model and Resource Fit Check (Holding).
- User stories and use cases, which belong to [SRIS-P1-REQ-006](./SRIS-P1-REQ-006_UserStoriesAndUseCases.md) — User Stories and Use Cases.
- The detailed domain rules for fare, ticketing, waitlist and cancellation, chart preparation, and seat matrix and inventory, which belong to [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) to [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md).
- The full cross-wave Requirement Traceability Matrix, which belongs to [SRIS-P1-REQ-012](./SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md) — Requirement Traceability Matrix (RTM).
- Service boundaries and the justification for the service count, which are defined in [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification.
- The Bounded Context Map, which belongs to [SRIS-P1-ARCH-004](../wave-2-architecture/SRIS-P1-ARCH-004_BoundedContextMap.md) — Bounded Context Map.
- Inter-service communication design, which belongs to [SRIS-P1-ARCH-009](../wave-2-architecture/SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md) — Service Interaction and Communication Design.
- The choice of language, database, framework, or tool, which belongs to [SRIS-P1-ARCH-008](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md) — Technology Stack ADR.
- The API contracts, which belong to [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md) — API Contract Document (OpenAPI).
- The data schemas, which belong to [SRIS-P1-DATA-002](../wave-3-detailed-design/SRIS-P1-DATA-002_LogicalDataModelPerService.md) — Logical Data Model (per service) and [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md) — Physical Database Schema Document.
- The screens, wireframes, and navigation, which belong to [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md) to [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md).
- The test cases, which belong to [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md) — Test Cases (Functional).
- The full deferred-capability roadmap, which belongs to [SRIS-P1-GOV-019](../wave-0-project-foundation/SRIS-P1-GOV-019_ProductRoadmapPhase123.md) — Product Roadmap (Phase 1, 2, 3).

### 1.3 Audience

- **Lead Architect:** maintains this document and is the source of every capability decision.
- **Project team:** reads the catalog before building against the frozen contracts, to understand which capability each task serves.
- **Project supervisor and evaluator:** reviews the catalog as the definitive statement of what Phase 1 provides.
- **Technical reviewers:** engineers, interviewers, or recruiters who open the repository and need the scope of Phase 1 in one document.
- **Downstream document authors:** every later register document cites the CAP-NNN identifiers recorded here.

### 1.4 Terminology and Conventions

The terminology below is local to this document. Every other term has the meaning recorded in [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary.

The 23 railway domain terms below are first exercised in the capabilities recorded in this document. Their definitions are recorded in [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) and are not repeated here. This document states the capability context in which each term is used.

| Term                          | Capability Context in This Document                              | Definition Owned By  |
| ----------------------------- | ---------------------------------------------------------------- | -------------------- |
| Train number                  | Railway Master Data — train identity configuration               | SRIS-P1-REQ-001 §3.1 |
| Train name                    | Railway Master Data — train identity configuration               | SRIS-P1-REQ-001 §3.1 |
| Train type                    | Railway Master Data — train category configuration               | SRIS-P1-REQ-001 §3.1 |
| Express                       | Railway Master Data — train category configuration               | SRIS-P1-REQ-001 §3.1 |
| Passenger                     | Railway Master Data — train category configuration               | SRIS-P1-REQ-001 §3.1 |
| Shatabdi                      | Railway Master Data — train category configuration               | SRIS-P1-REQ-001 §3.1 |
| Duronto                       | Railway Master Data — train category configuration               | SRIS-P1-REQ-001 §3.1 |
| Origin                        | Railway Master Data — route configuration                        | SRIS-P1-REQ-001 §3.2 |
| Destination                   | Railway Master Data — route configuration                        | SRIS-P1-REQ-001 §3.2 |
| Intermediate station          | Railway Master Data — route and stop configuration               | SRIS-P1-REQ-001 §3.2 |
| Route                         | Railway Master Data — route configuration                        | SRIS-P1-REQ-001 §3.2 |
| Stop                          | Railway Master Data — route and stop configuration               | SRIS-P1-REQ-001 §3.2 |
| Halt time                     | Railway Master Data — schedule configuration                     | SRIS-P1-REQ-001 §3.2 |
| Running days                  | Railway Master Data — schedule configuration                     | SRIS-P1-REQ-001 §3.2 |
| Departure                     | Railway Master Data — schedule configuration                     | SRIS-P1-REQ-001 §3.2 |
| Arrival                       | Railway Master Data — schedule configuration                     | SRIS-P1-REQ-001 §3.2 |
| Schedule                      | Railway Master Data — schedule configuration                     | SRIS-P1-REQ-001 §3.2 |
| Timetable                     | Railway Master Data — schedule configuration                     | SRIS-P1-REQ-001 §3.2 |
| Frequency                     | Railway Master Data — schedule configuration                     | SRIS-P1-REQ-001 §3.2 |
| Master data setup             | Railway Master Data — administrative configuration               | SRIS-P1-REQ-001 §3.9 |
| Station configuration         | Railway Master Data — station configuration                      | SRIS-P1-REQ-001 §3.9 |
| Train configuration           | Railway Master Data — train configuration                        | SRIS-P1-REQ-001 §3.9 |
| Schedule configuration        | Railway Master Data — schedule configuration                     | SRIS-P1-REQ-001 §3.9 |

The identifier prefixes below are local to this document.

| Prefix | Meaning                                                    |
| ------ | ---------------------------------------------------------- |
| CAP    | Phase 1 capability (in scope)                              |
| D      | Deferred capability (out of Phase 1 scope, from ARCH-001)  |

This document follows the standards below.

- [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard, for structure, header, and style.
- [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md) — Document ID and Category Scheme, for the Document ID.
- [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md) — Document Cross-Reference Standard, for citations and links.

---

## 2. Capability Model and Governance Rules

### 2.1 Capability Definition and Granularity

A Phase 1 business capability is an enduring ability of the SRIS platform to perform a defined business function or deliver a specific domain outcome. A capability is stated in terms of what the business does, not how the software, interfaces, or personnel execute it. The definition follows [Section 4.1](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#41-how-to-read-the-catalog) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification.

A capability is distinct from the following.

- **Business requirement.** A business requirement is a statement of a specific business need, recorded in [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD). A capability is the ability; a business requirement is the need that demands the ability.
- **Software requirement.** A software requirement specifies deterministic behaviour, input-output rules, and validation, and belongs to [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software Requirements Specification (SRS).
- **User story.** A user story frames an interaction goal from the perspective of an external actor and belongs to [SRIS-P1-REQ-006](./SRIS-P1-REQ-006_UserStoriesAndUseCases.md) — User Stories and Use Cases.
- **Design decision.** A design decision records how service boundaries, communication topologies, and technologies are chosen, and belongs to the ARCH category, such as [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) and [SRIS-P1-ARCH-008](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md).

**Granularity.** A capability sits at the level of a discrete business function inside a capability domain. It is coarser than a sub-function or algorithmic rule (for example, waitlist cascade arithmetic or fare distance slabs, which belong to [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) to [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)). It is finer than a capability domain.

**Naming.** A capability name is a concise noun phrase of two to five words, structured as an object noun combined with an action nominalisation, such as Station Configuration or Seat Matrix Generation. Bare single nouns (Train, Station) are not used, because they name passive data entities rather than capabilities, as noted in [Section 5.3](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#53-alternatives-considered) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md). Imperative verb-noun pairs (Configure stations, Holds a seat) are reserved for the ten-step booking flow in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document.

**Description length.** A capability description is one line, written as a single declarative sentence.

**Three-part verification test.** A candidate item is a capability when all three of the following hold.

1. **Surface and technology independence.** The item describes a core domain ability that remains invariant whether invoked from the Customer Booking Website, from the Employee Admin Console, or from an automated service test, per Requirement BR-28 in [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD). An item that describes a screen widget or a client navigation element is a UI feature and belongs to [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md) to [SRIS-P1-UI-012](../wave-3-detailed-design/SRIS-P1-UI-012_InternationalizationAndLocalizationDesign.md).
2. **Permanence.** The item represents an operational ability the system possesses continuously, not a time-boxed engineering task tracked on the Kanban board, and not a chronological step in the ten-step booking flow.
3. **Single service ownership.** The item has exactly one owning microservice, per Business Rule BRL-8 in [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) and [Section 6.3](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#63-capability-traceability) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md). An item that spans multiple services synchronously is a cross-service business process, not a capability.

### 2.2 Capability Identification and Permanence Rules

A Phase 1 capability has an identifier in the form `CAP-NNN`, where `NNN` is a three-digit zero-padded sequence number from `001` to `999`. A deferred capability retains the identifier scheme `D-NN` established in [Section 4.3](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#43-deferred-capabilities) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification.

The rules below apply.

- The identifier is permanent. Once assigned in version 1.0 of this document, a CAP-NNN identifier never changes, even if the capability title is refined in a later revision. This follows [Section 4.4](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md#44-permanence-gaps-and-reuse) of [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md) — Document ID and Category Scheme.
- The sequence number is zero-padded to three digits. The forms `1`, `01`, and `0001` are not valid. The number `000` is not used. This follows [Section 4.1](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md#41-three-digit-rule) of [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md).
- A withdrawn capability retires its identifier. The identifier stays in the register and is never given to another capability. A gap in the sequence therefore means a retired capability, not a free number.
- The identifier is independent of the capability domain and of the owning service. If a capability is moved to a different service in a later phase, its identifier does not change.
- The identifier format is: `^CAP-(?!000)[0-9]{3}$`.

The scheme `CAP-NNN` is chosen over four alternatives.

| Alternative                | Why it is not used                                                                                                          |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| `C-NNN` or `C-NN`          | Prefix `C-` is already allocated to constraints `C-1` to `C-7` in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document and in [SRIS-P1-GOV-006](../wave-0-project-foundation/SRIS-P1-GOV-006_ProjectCharter.md) — Project Charter. A direct collision. |
| `CP-NNN`                   | Opaque. Confusable with Chart Preparation and Capacity Planning.                                                             |
| `CAP-IAM-001`, `CAP-S1-001` | Encodes the domain or service inside the identifier, which violates the decoupling principle of [Section 5.2](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md#52-folder-structure) of [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md) — Document ID and Category Scheme. Full stops conflict with the anchor derivation rule AN-3 in [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md). |
| Merging deferred into CAP-NNN | Breaks backward compatibility with the D-01 to D-11 identifiers already cited in [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification. |

### 2.3 Baseline Lock and Revision Rules

This document is the baseline for Phase 1 capabilities. After approval, no capability is added, removed, or re-scoped without a formal revision that increments the minor version under [Section 7](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md#7-revision-history-standard) of [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard and adds a row to the Revision History.

The rules below apply.

- A new capability is added only when a change request is approved through the process defined in [SRIS-P1-GOV-012](../wave-0-project-foundation/SRIS-P1-GOV-012_ChangeManagementPlan.md) — Change Management Plan.
- Every change to this document is recorded as a new row in the Revision History and increments the minor version number.
- A capability that is withdrawn in a later revision has its identifier retired and its row struck through in a subsequent revision row that records the retirement. Its identifier is not reused.
- The version of this document that later documents cite is the version current at the time they are written. A later revision of this document does not invalidate the citations already made in committed documents.

---

## 3. Capability Domains Overview

### 3.1 Phase 1 Capability Domains

Phase 1 has eight capability domains. The names, spelling, capitalisation, and order are fixed by [Section 4.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#42-phase-1-capabilities) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification. They are not altered by this document.

| Seq | Capability Domain     | Owning Service                    | Capabilities |
| --- | --------------------- | --------------------------------- | ------------ |
| 1   | Identity and Access   | S1 IAM Service                    | CAP-001 to CAP-005 |
| 2   | Railway Master Data   | S2 Master Data and Pricing Service | CAP-006 to CAP-010 |
| 3   | Fare and Pricing      | S2 Master Data and Pricing Service | CAP-011 to CAP-014 |
| 4   | Inventory and Quota   | S3 Reservation Service             | CAP-015 to CAP-018 |
| 5   | Booking and Ticketing | S3 Reservation Service             | CAP-019 to CAP-024 |
| 6   | Payment               | S3 Reservation Service; S5 Mock Payment Gateway | CAP-025 to CAP-026 |
| 7   | Search and Discovery  | S4 Search Aggregator BFF           | CAP-027 to CAP-028 |
| 8   | Notification          | S6 Notification Service            | CAP-029 to CAP-030 |

The order is the sequence in [Section 4.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#42-phase-1-capabilities) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification, which reflects the acyclic synchronous dependency graph defined by criterion D2 in [Section 3.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#32-decision-criteria) of the same document, and the sprint implementation order fixed by [Section 3](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md#3-schedule-and-work-breakdown) of [SRIS-P1-GOV-007](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md) — Project Management Plan.

The eight capability domains themselves do not carry identifier codes. They are cited by their canonical names. This follows the convention throughout [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification and [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD). Only the capabilities and the deferred capabilities inside the domains carry identifiers.

### 3.2 Domain to Bounded Context Mapping

Each capability domain maps to one or more bounded contexts contained within the six microservices. The mapping is fixed by [Section 6.1](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#61-service-catalog) and [Section 6.3](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#63-capability-traceability) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification.

| Capability Domain     | Bounded Context                                | Owning Service                     |
| --------------------- | ---------------------------------------------- | ---------------------------------- |
| Identity and Access   | Identity and Access                            | S1 IAM Service                     |
| Railway Master Data   | Railway Master Data                            | S2 Master Data and Pricing Service |
| Fare and Pricing      | Fare and Pricing                               | S2 Master Data and Pricing Service |
| Inventory and Quota   | Inventory and Quota                            | S3 Reservation Service             |
| Booking and Ticketing | Booking and Ticketing                          | S3 Reservation Service             |
| Payment               | Payment, split by role between domain and simulator | S3 Reservation Service; S5 Mock Payment Gateway |
| Search and Discovery  | Search and Discovery                           | S4 Search Aggregator BFF           |
| Notification          | Notification and Eventing                      | S6 Notification Service            |

The visual bounded context map and the consolidation trade-offs are recorded in [SRIS-P1-ARCH-004](../wave-2-architecture/SRIS-P1-ARCH-004_BoundedContextMap.md) — Bounded Context Map and in [Section 7](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#7-justification-of-service-boundaries) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification, and are not repeated here.

---

## 4. Phase 1 Capability Catalog

This section is the locked catalog of Phase 1 capabilities. Each capability carries an identifier in the form `CAP-NNN`, a name, a one-line description, the owning microservice and internal module, and the source business requirement from [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD).

The catalog contains **30 capabilities**, distributed across the eight capability domains of [Section 3.1](#31-phase-1-capability-domains). Each capability is stated at the business level only. The detailed rules of a capability belong to its owning domain rule document, cited in [Section 7.2](#72-downstream-specification-ownership-map), and are not repeated here.

### 4.1 Identity and Access

The Identity and Access domain covers the capabilities that establish the identity of a caller and determine what the caller may do. The domain is owned by S1 IAM Service. Detailed design of authentication, RBAC, and token handling belongs to [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md) — Authentication and Authorization Design, [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md) — RBAC Matrix, and [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md) — JWT Token Design and Claims.

| ID      | Capability Name                        | Description                                                                                                                       | Owning Service | Source Business Requirement |
| ------- | -------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | -------------- | --------------------------- |
| CAP-001 | Customer Registration and Login        | Enables customers to register an account and authenticate on the Customer Booking Website to access booking operations.           | S1 IAM Service | BR-1                        |
| CAP-002 | Employee Authentication                | Verifies the login credentials of railway employees before granting access to the Employee Admin Console.                         | S1 IAM Service | BR-2, BR-4                  |
| CAP-003 | Role-Based Access Control              | Restricts the actions an authenticated caller may perform according to the role assigned to their identity.                        | S1 IAM Service | BR-3, BRL-7                 |
| CAP-004 | Token Issuance, Refresh, and Revocation | Issues signed tokens upon login, refreshes active sessions, revokes invalidated tokens, and validates caller tokens across services. | S1 IAM Service | BR-1, BR-2, BR-3            |
| CAP-005 | Basic User Profile Management          | Stores and maintains the basic identity profile associated with a customer or employee login account.                             | S1 IAM Service | BR-1, BR-4, BA-7            |

### 4.2 Railway Master Data

The Railway Master Data domain covers the capabilities that configure the static railway network. The domain is owned by S2 Master Data and Pricing Service. Detailed data design belongs to [SRIS-P1-DATA-002](../wave-3-detailed-design/SRIS-P1-DATA-002_LogicalDataModelPerService.md) — Logical Data Model (per service) and [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md) — Physical Database Schema Document.

| ID      | Capability Name                                | Description                                                                                                                                    | Owning Service                      | Source Business Requirement |
| ------- | ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------- | --------------------------- |
| CAP-006 | Station Configuration                          | Enables authorised employees to create and manage railway station entities with unique station codes, names, and network attributes.            | S2 Master Data and Pricing Service  | BR-5, BR-6, BRL-7           |
| CAP-007 | Route and Stop Management with Distances       | Enables authorised employees to define ordered station routes, intermediate commercial stops, and cumulative kilometre distances.                | S2 Master Data and Pricing Service  | BR-5, BR-6, BR-7            |
| CAP-008 | Train and Schedule Configuration               | Enables authorised employees to configure train numbers, names, service types, running days, frequencies, and arrival, departure, and halt times. | S2 Master Data and Pricing Service  | BR-5, BR-6, BR-7            |
| CAP-009 | Coach Composition and Berth Layout Configuration | Enables authorised employees to define the ordered carriage composition attached to each train and the seat and berth blueprint per coach.       | S2 Master Data and Pricing Service  | BR-6, BR-7                  |
| CAP-010 | Class and Quota Definition                     | Enables authorised employees to define accommodation travel classes and commercial quota categories.                                              | S2 Master Data and Pricing Service  | BR-5, BR-6, BR-7            |

### 4.3 Fare and Pricing

The Fare and Pricing domain covers the capabilities that configure fare rules and calculate prices. The domain is owned by S2 Master Data and Pricing Service. The detailed fare calculation rules belong to [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) — Domain Rules: Fare Calculation.

| ID      | Capability Name                     | Description                                                                                                                              | Owning Service                      | Source Business Requirement |
| ------- | ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------- | --------------------------- |
| CAP-011 | Base Fare Configuration by Class    | Enables authorised employees to configure base fares per kilometre, distance slabs, class multipliers, taxes, and service charges.        | S2 Master Data and Pricing Service  | BR-5, BR-6, BR-8            |
| CAP-012 | Dynamic Pricing Rule Configuration  | Enables authorised employees to configure fare surge rules that adjust prices as available seat inventory depletes.                        | S2 Master Data and Pricing Service  | BR-5, BR-6, BR-8            |
| CAP-013 | Concession Rule Configuration       | Enables authorised employees to configure eligibility criteria and percentage fare reductions granted to qualifying passenger categories. | S2 Master Data and Pricing Service  | BR-6, BR-8                  |
| CAP-014 | Fare Quote and Re-Quote Calculation | Computes estimated fare quotes during search and authoritative fare re-quotes at booking time, incorporating quota and concessions.        | S2 Master Data and Pricing Service  | BR-8, BRL-3                 |

### 4.4 Inventory and Quota

The Inventory and Quota domain covers the capabilities that generate and manage seat inventory. The domain is owned by S3 Reservation Service, in the Inventory module. The detailed rules belong to [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md) — Domain Rules: Seat Matrix and Inventory.

| ID      | Capability Name                        | Description                                                                                                                                          | Owning Service                     | Source Business Requirement |
| ------- | -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------- | --------------------------- |
| CAP-015 | Seat Matrix Generation                 | Generates the complete set of bookable physical seats and berths for each scheduled train journey from master data schedules and coach compositions.   | S3 Reservation Service (Inventory) | BR-14                       |
| CAP-016 | Quota Allocation                       | Partitions the generated seat matrix of a train run into separate logical inventory pools per travel class and commercial quota before bookings open.   | S3 Reservation Service (Inventory) | BR-14                       |
| CAP-017 | Seat Availability Enquiry              | Calculates and returns the current count of unreserved seats or waitlist positions for a given train, segment, travel class, and quota.                 | S3 Reservation Service (Inventory) | BR-13                       |
| CAP-018 | Seat Hold, Confirmation, and Release   | Enforces seat protection during booking, durable allocation upon payment, and inventory release upon expiry or cancellation, so no seat is sold twice. | S3 Reservation Service (Inventory) | BR-15, BRL-1                |

### 4.5 Booking and Ticketing

The Booking and Ticketing domain covers the capabilities that drive a booking to a PNR. The domain is owned by S3 Reservation Service, in the Booking module. The detailed rules belong to [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing, [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md) — Domain Rules: Waitlist and Cancellation, and [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md) — Domain Rules: Chart Preparation.

| ID      | Capability Name                          | Description                                                                                                                                                    | Owning Service                    | Source Business Requirement |
| ------- | ---------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------- | --------------------------- |
| CAP-019 | Booking Lifecycle State Management       | Drives each booking request through a deterministic state machine from initiation and fare re-quote to confirmed, waitlisted, or cancelled.                     | S3 Reservation Service (Booking)  | BR-20, BR-22, BRL-2, BRL-3  |
| CAP-020 | PNR Generation                           | Generates and assigns a unique ten-digit Passenger Name Record identifier to every confirmed or waitlisted booking.                                             | S3 Reservation Service (Booking)  | BR-20, BRL-4                |
| CAP-021 | Waitlist Handling and Cascade            | Places bookings into ordered waitlist or RAC queues when confirmed inventory is exhausted and promotes queued passengers on cancellation.                       | S3 Reservation Service (Booking)  | BR-16a, BR-23               |
| CAP-022 | Chart Preparation                        | Executes batch finalisation of the departure reservation manifest, resolving remaining quota pools, RAC allocations, and waitlist positions.                    | S3 Reservation Service (Booking)  | BR-23                       |
| CAP-023 | Ticket Cancellation                      | Terminates a customer booking, updates PNR and passenger status, releases seat inventory, and triggers the waitlist cascade.                                     | S3 Reservation Service (Booking)  | BR-23                       |
| CAP-024 | Ticket and PNR Status Retrieval          | Retrieves the complete e-ticket record, passenger details, coach and berth assignments, and current reservation status using the ten-digit PNR.                  | S3 Reservation Service (Booking)  | BR-21, BR-22                |

### 4.6 Payment

The Payment domain is split by role. The domain side (payment initiation, attempt tracking, callback verification) is owned by S3 Reservation Service. The simulator side (mock processing and result callback) is owned by S5 Mock Payment Gateway. The detailed integration design belongs to [SRIS-P1-API-011](../wave-3-detailed-design/SRIS-P1-API-011_PaymentGatewayIntegrationDesignMock.md) — Payment Gateway Integration Design (Mock) and [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md) — Idempotency and Retry Policy Specification.

| ID      | Capability Name                                     | Description                                                                                                                                           | Owning Service                     | Source Business Requirement |
| ------- | --------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------- | --------------------------- |
| CAP-025 | Payment Initiation, Attempt Tracking, and Callback Verification | Initiates outbound payment requests, records payment attempts, verifies signed callbacks through an anti-corruption layer, and triggers reversal on failure. | S3 Reservation Service (Booking)   | BR-16, BR-17, BR-19, BRL-2  |
| CAP-026 | Simulated Payment Processing and Result Callback    | Simulates payment execution with configurable outcomes and dispatches a signed webhook result to Reservation.                                          | S5 Mock Payment Gateway            | BR-16, BR-17, BR-18, BRL-6  |

### 4.7 Search and Discovery

The Search and Discovery domain covers the capabilities that return search results to the client. The domain is owned by S4 Search Aggregator BFF. The BFF is read-only and does not mutate state. The OpenAPI contract belongs to [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md) — API Contract Document (OpenAPI).

| ID      | Capability Name                       | Description                                                                                                                                    | Owning Service             | Source Business Requirement |
| ------- | ------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- | --------------------------- |
| CAP-027 | Train Search by Route and Date        | Accepts customer search queries by origin, destination, and journey date and returns matching trains for selection without mutating state.     | S4 Search Aggregator BFF   | BR-9, BR-11, BR-12          |
| CAP-028 | Unified Search Response Aggregation   | Composes schedules and fare quotes from S2 with seat availability from S3 into one combined read-only response for the client surfaces.          | S4 Search Aggregator BFF   | BR-10, BR-11                |

### 4.8 Notification

The Notification domain covers the capabilities that dispatch customer notifications asynchronously. The domain is owned by S6 Notification Service. Notification must never block or fail a booking, per Business Rule BRL-5. The event schema belongs to [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md) — Event Schema Document (AsyncAPI) and the integration design belongs to [SRIS-P1-API-012](../wave-3-detailed-design/SRIS-P1-API-012_NotificationIntegrationDesign.md) — Notification Integration Design.

| ID      | Capability Name                                     | Description                                                                                                                                       | Owning Service          | Source Business Requirement |
| ------- | --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------- | --------------------------- |
| CAP-029 | Booking Confirmation Notification                   | Consumes booking-confirmed events asynchronously and dispatches e-ticket confirmation to the customer by email and by SMS.                        | S6 Notification Service | BR-24, BRL-5                |
| CAP-030 | Message Template Management, Delivery Logging, and Retry | Maintains message templates, renders event payloads, logs each delivery attempt, and retries failed deliveries asynchronously.                    | S6 Notification Service | BR-25, BRL-5                |

---

## 5. Service Ownership and Booking Flow Alignment

### 5.1 Capability Ownership by Microservice and Module

Each Phase 1 capability has exactly one owning service, per Business Rule BRL-8 in [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD). Where a service contains internal modules with separate database schemas, the owning module is stated. The mapping is fixed by [Section 6.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#62-service-specifications), [Section 6.3](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#63-capability-traceability), and [Section 7.4](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#74-internal-module-boundary-rules) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification.

| Owning Service                     | Module    | Capabilities                                  |
| ---------------------------------- | --------- | --------------------------------------------- |
| S1 IAM Service                     | —         | CAP-001, CAP-002, CAP-003, CAP-004, CAP-005   |
| S2 Master Data and Pricing Service | Railway Master Data | CAP-006, CAP-007, CAP-008, CAP-009, CAP-010 |
| S2 Master Data and Pricing Service | Fare and Pricing | CAP-011, CAP-012, CAP-013, CAP-014      |
| S3 Reservation Service             | Inventory | CAP-015, CAP-016, CAP-017, CAP-018            |
| S3 Reservation Service             | Booking   | CAP-019, CAP-020, CAP-021, CAP-022, CAP-023, CAP-024, CAP-025 |
| S4 Search Aggregator BFF           | —         | CAP-027, CAP-028                              |
| S5 Mock Payment Gateway            | —         | CAP-026                                       |
| S6 Notification Service            | —         | CAP-029, CAP-030                              |

No capability is owned by more than one service. No service is absent from the catalog. The internal module boundary rules in [Section 7.4](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#74-internal-module-boundary-rules) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification apply to CAP-006 to CAP-025 and keep each module extractable into a standalone service in a later phase without a change to the domain model.

### 5.2 Capability Mapping to the Ten Step Booking Flow

The ten-step booking flow is defined in [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document and restated in [Section 6.1](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md#61-the-booking-flow) of [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD). The table below maps each step to the capabilities exercised by that step.

| Step | Actor    | Action                                                            | Capabilities Exercised                                                                |
| ---- | -------- | ----------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| 1    | Employee | Logs in to the Employee Admin Console                             | CAP-002, CAP-004                                                                       |
| 2    | Employee | Configures stations, routes, trains, schedules, fares, and quotas | CAP-006, CAP-007, CAP-008, CAP-009, CAP-010, CAP-011, CAP-012, CAP-013                 |
| 3    | Customer | Registers and logs in on the Customer Booking Website             | CAP-001, CAP-004, CAP-005                                                              |
| 4    | Customer | Searches for trains                                               | CAP-027, CAP-028                                                                       |
| 5    | Customer | Selects a train, class, and quota                                 | CAP-027, CAP-014, CAP-017                                                              |
| 6    | Customer | Commits to a seat for the selected train, class, and quota         | CAP-015, CAP-016, CAP-018                                                              |
| 7    | Customer | Pays through the mock payment gateway                             | CAP-025, CAP-026                                                                       |
| 8    | System   | Confirms the booking and issues a 10-digit PNR                    | CAP-019, CAP-020, CAP-025                                                              |
| 9    | System   | Sends email and SMS confirmations                                 | CAP-029, CAP-030                                                                       |
| 10   | Customer | Retrieves the ticket by PNR                                       | CAP-024                                                                                |

Steps 3 and 5 also exercise CAP-003 indirectly, because the role assigned to the authenticated caller determines which actions are permitted. CAP-021, CAP-022, and CAP-023 are not mapped to a single step because they operate across the booking lifecycle after confirmation, when a waitlist advances, a chart is prepared, or a ticket is cancelled.

### 5.3 User Surface Capability Consumption

The two user-facing surfaces defined in [Section 5.3](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md#53-surfaces-and-deliverables) of [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD) consume the capabilities below. The mapping follows Business Rule BRL-7 in [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) and [Section 6.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#62-service-specifications) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification.

| Surface                  | Capabilities Consumed Directly                                                                                    |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------- |
| Employee Admin Console   | CAP-002, CAP-003, CAP-006, CAP-007, CAP-008, CAP-009, CAP-010, CAP-011, CAP-012, CAP-013, CAP-022                  |
| Customer Booking Website | CAP-001, CAP-003, CAP-004, CAP-005, CAP-014, CAP-017, CAP-018, CAP-019, CAP-020, CAP-021, CAP-023, CAP-024, CAP-025, CAP-027, CAP-028 |

CAP-026 is invoked indirectly by CAP-025 during the customer booking flow and is not a surface-level capability. CAP-029 and CAP-030 are invoked asynchronously by the system after confirmation and are not surface-level capabilities. The screens, wireframes, and navigation of each surface belong to [SRIS-P1-UI-002](../wave-3-detailed-design/SRIS-P1-UI-002_ScreenInventoryAndNavigationMap.md) — Screen Inventory and Navigation Map, [SRIS-P1-UI-003](../wave-3-detailed-design/SRIS-P1-UI-003_WireframesCustomerFlow.md) — Wireframes (Customer Flow), and [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md) — Wireframes (Employee/Admin Flow), and are not defined here.

---

## 6. Deferred and Out of Scope Capabilities

### 6.1 Resolution of Provisional Deferrals

[Section 4.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#42-phase-1-capabilities) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification marks three capabilities as expected to be deferred, subject to confirmation. [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD) tracks the confirmation as OI-3. This document resolves OI-3.

- **D-12: Standalone refund processing.** Deferred to Phase 2. A customer-initiated refund calculation upon cancellation belongs to [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) — Domain Rules: Fare Calculation. A technical payment reversal when seat allocation fails belongs to [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing and to [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md) — Distributed Transaction and Saga Pattern Design. Neither is a standalone refund engine, and both are inside Phase 1.
- **D-13: Payment reconciliation and settlement.** Deferred to Phase 2. The Phase 1 payment gateway is a simulator and does not produce real transactions to reconcile.
- **D-14: In-app or push notifications.** Deferred to Future. Phase 1 provides email and SMS only.

The three capabilities are catalogued in [Section 6.2](#62-deferred-railway-ecosystem-catalog) with the identifiers D-12, D-13, and D-14, extending the D-01 to D-11 sequence established in [Section 4.3](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#43-deferred-capabilities) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md).

### 6.2 Deferred Railway Ecosystem Catalog

The capabilities below belong to the wider railway ecosystem but are outside Phase 1. They are recorded here so that the register holds one authoritative list of what Phase 1 does not provide. The list consolidates [Section 5.2](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#52-out-of-scope) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document, [Section 4.3](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#43-deferred-capabilities) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification, [Section 4](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md#4-railway-domain-terms-out-of-scope) of [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary, and [Section 5.4](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md#54-out-of-scope-and-deferred-capabilities) of [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD).

| ID   | Deferred Capability                                          | Domain                  | Target  |
| ---- | ------------------------------------------------------------ | ----------------------- | ------- |
| D-01 | Train running status and delay tracking                      | Live Operations         | Phase 2 |
| D-02 | Disruption management                                        | Live Operations         | Phase 2 |
| D-03 | Platform allocation                                          | Station Operations      | Phase 2 |
| D-04 | Station facilities management                                | Station Operations      | Phase 2 |
| D-05 | Employee records and departments                             | Workforce               | Phase 2 |
| D-06 | Crew rostering and duty assignment                           | Workforce               | Phase 2 |
| D-07 | Leave and attendance                                         | Workforce               | Phase 2 |
| D-08 | Operational dashboards and reports                           | Insights and Reporting  | Phase 2 |
| D-09 | Passenger grievance handling                                 | Grievance               | Future  |
| D-10 | Catering and on-board services                               | Catering                | Future  |
| D-11 | Vendor management                                            | Vendor Management       | Future  |
| D-12 | Standalone refund processing                                 | Payment                 | Phase 2 |
| D-13 | Payment reconciliation and settlement                        | Payment                 | Phase 2 |
| D-14 | In-app or push notifications                                 | Notification            | Future  |

The full product roadmap that assigns these capabilities to named phases belongs to [SRIS-P1-GOV-019](../wave-0-project-foundation/SRIS-P1-GOV-019_ProductRoadmapPhase123.md) — Product Roadmap (Phase 1, 2, 3).

### 6.3 Permanent Phase 1 Exclusions

Two things are excluded from Phase 1 permanently and are not deferred. They are recorded so that no later revision introduces them by mistake.

- **Connection to any live system of Indian Railways, CRIS, or IRCTC.** SRIS is an independent academic project and does not integrate with any external railway system. Source: [Section 5.2](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#52-out-of-scope) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document and Business Rule BRL-6 in [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD).
- **Real payment processing.** The payment gateway is a simulator. No real money moves. Source: [Section 5.2](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#52-out-of-scope) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) and Business Rule BRL-6 in [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md).

Both are permanent for the whole of SRIS, not only for Phase 1.

---

## 7. Capability Traceability

### 7.1 Upstream Traceability and Source Reconciliation

Every capability in [Section 4](#4-phase-1-capability-catalog) traces to a source in the register. The table below states, for each capability, whether it appears in [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document, in [Section 4.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#42-phase-1-capabilities) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification, or in both.

| ID      | In GOV-005 §5.1 | In ARCH-001 §4.2 | Note                                                                                |
| ------- | --------------- | ---------------- | ----------------------------------------------------------------------------------- |
| CAP-001 | Yes             | Yes              | Present in both                                                                     |
| CAP-002 | Yes             | Yes              | Present in both                                                                     |
| CAP-003 | Yes             | Yes              | Present in both                                                                     |
| CAP-004 | No              | Yes              | Token lifecycle is detailed in ARCH-001 and not stated as a separate bullet in GOV-005 |
| CAP-005 | No              | Yes              | Basic user profile is stated in ARCH-001 Assumption A-2 and not in GOV-005 §5.1     |
| CAP-006 | Yes             | Yes              | Present in both                                                                     |
| CAP-007 | Partial         | Yes              | Routes are in both; stops and distances are detailed in ARCH-001 only               |
| CAP-008 | Yes             | Yes              | Present in both, with running days and timings detailed in ARCH-001                 |
| CAP-009 | No              | Yes              | Coach composition is detailed in ARCH-001 and in REQ-002 BR-7                       |
| CAP-010 | Partial         | Yes              | Quotas are in both; class definitions are detailed in ARCH-001                      |
| CAP-011 | Partial         | Yes              | GOV-005 groups pricing under "fares"; ARCH-001 separates base fare by class          |
| CAP-012 | No              | Yes              | Dynamic pricing is detailed in ARCH-001 and in REQ-002 BR-8                          |
| CAP-013 | No              | Yes              | Concessions are detailed in ARCH-001 and in REQ-002 BR-8                            |
| CAP-014 | No              | Yes              | Fare quote and re-quote are in ARCH-001 §4.2 and §6.2 and in REQ-002 BR-8 and BRL-3 |
| CAP-015 | No              | Yes              | Seat matrix generation is detailed in ARCH-001 and in REQ-002 BR-14                 |
| CAP-016 | No              | Yes              | Quota allocation is detailed in ARCH-001 and in REQ-002 BR-14                       |
| CAP-017 | Yes             | Yes              | Present in both                                                                     |
| CAP-018 | Partial         | Yes              | Seat hold is in both; confirm and release are detailed in ARCH-001                  |
| CAP-019 | Partial         | Yes              | Step 8 states confirmation; the state machine is detailed in ARCH-001               |
| CAP-020 | Yes             | Yes              | Present in both                                                                     |
| CAP-021 | No              | Yes              | Waitlist is detailed in ARCH-001 and in REQ-002 BR-16a and BR-23                    |
| CAP-022 | No              | Yes              | Chart preparation is detailed in ARCH-001 and in REQ-002 BR-23                      |
| CAP-023 | No              | Yes              | Cancellation is detailed in ARCH-001 and in REQ-002 BR-23                          |
| CAP-024 | Partial         | Yes              | Step 10 states ticket retrieval; the capability is not in the GOV-005 §5.1 bullet list |
| CAP-025 | Partial         | Yes              | GOV-005 states mock payment as one bullet; ARCH-001 splits domain side and simulator side |
| CAP-026 | Yes             | Yes              | Present in both                                                                     |
| CAP-027 | Yes             | Yes              | Present in both                                                                     |
| CAP-028 | No              | Yes              | Unified response is detailed in ARCH-001 and in REQ-002 BR-10                       |
| CAP-029 | Yes             | Yes              | Present in both                                                                     |
| CAP-030 | No              | Yes              | Templates and delivery log are detailed in ARCH-001 and in REQ-002 BR-25            |

The reconciliation above explains why the final count is 30 and not 8. The 8 bullets in [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) are a summary. The 30 capabilities in [Section 4](#4-phase-1-capability-catalog) of this document are the decomposition of that summary into the discrete business functions that Phase 1 provides. This document is now the authoritative source for the count.

### 7.2 Downstream Specification Ownership Map

The table below maps each capability to the downstream document that owns its detailed rules and its design. This mapping lets a reader go from a capability to the document that specifies it, and lets a downstream author go from a requirement, an API endpoint, a data model, or a test case back to the capability it fulfils.

| Capability       | Detailed Rules Owner                                                      | Design Owner                                                                                              |
| ---------------- | ------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| CAP-001 to CAP-005 | [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — SRS | [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md), [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md), [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md) |
| CAP-006 to CAP-010 | [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — SRS | [SRIS-P1-DATA-002](../wave-3-detailed-design/SRIS-P1-DATA-002_LogicalDataModelPerService.md), [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md) |
| CAP-011 to CAP-014 | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) — Domain Rules: Fare Calculation | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md) — API Contract Document (OpenAPI) |
| CAP-015 to CAP-018 | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md) — Domain Rules: Seat Matrix and Inventory | [SRIS-P1-DATA-008](../wave-3-detailed-design/SRIS-P1-DATA-008_HighConcurrencySegmentInventoryDataModel.md), [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md) |
| CAP-019 to CAP-024 | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md), [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md), [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md) | [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md), [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md) |
| CAP-025 | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing | [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md), [SRIS-P1-API-011](../wave-3-detailed-design/SRIS-P1-API-011_PaymentGatewayIntegrationDesignMock.md) |
| CAP-026 | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing | [SRIS-P1-API-011](../wave-3-detailed-design/SRIS-P1-API-011_PaymentGatewayIntegrationDesignMock.md) |
| CAP-027 to CAP-028 | [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — SRS | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md), [SRIS-P1-ARCH-003](../wave-2-architecture/SRIS-P1-ARCH-003_SystemArchitectureDocument.md) |
| CAP-029 to CAP-030 | [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — SRS | [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md), [SRIS-P1-API-012](../wave-3-detailed-design/SRIS-P1-API-012_NotificationIntegrationDesign.md) |

The full cross-wave Requirements Traceability Matrix belongs to [SRIS-P1-REQ-012](./SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md) — Requirement Traceability Matrix (RTM), and is not repeated here.

---

## 8. Approval

| Role           | Name        | Decision | Date       |
| -------------- | ----------- | -------- | ---------- |
| Lead Architect | Koushal Jha | Approved | 2026-10-14 |

---

## Revision History

| Version | Date       | Author      | Change           |
| ------- | ---------- | ----------- | ---------------- |
| 1.0     | 2026-10-14 | Koushal Jha | Initial release. |

---

## Appendix A: Not Applicable

Not applicable.

---

## Appendix B: Related Documents

### B.1 Directly Referenced Documents

| Seq  | Document ID                                                                                                | Document Name                                     | Wave | Pri | Tag     |
| ---- | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------- | ---- | --- | ------- |
| 0.0  | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md)       | Documentation Index and Navigation Map            | 0    | P0  | UNBLOCK |
| 0.1  | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)                 | Document Template Standard                        | 0    | P0  | UNBLOCK |
| 0.2  | [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)              | Document ID and Category Scheme                   | 0    | P1  | UNBLOCK |
| 0.3  | [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md)           | Document Cross-Reference Standard                 | 0    | P1  | UNBLOCK |
| 0.4  | [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)            | Project Vision and Scope Document                 | 0    | P0  | UNBLOCK |
| 0.6  | [SRIS-P1-GOV-007](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md)                    | Project Management Plan                           | 0    | P0  | UNBLOCK |
| 0.11 | [SRIS-P1-GOV-012](../wave-0-project-foundation/SRIS-P1-GOV-012_ChangeManagementPlan.md)                     | Change Management Plan                            | 0    | P2  | FOLLOW  |
| 0.18 | [SRIS-P1-GOV-019](../wave-0-project-foundation/SRIS-P1-GOV-019_ProductRoadmapPhase123.md)                   | Product Roadmap (Phase 1, 2, 3)                   | 0    | P2  | FOLLOW  |
| 1.1  | [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md)                                          | Glossary and Domain Dictionary                    | 1    | P0  | UNBLOCK |
| 1.2  | [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md)                                     | Business Requirements Document (BRD)              | 1    | P0  | UNBLOCK |
| 1.4  | [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md)                                 | Software Requirements Specification (SRS)         | 1    | P0  | UNBLOCK |
| 1.5  | [SRIS-P1-REQ-005](./SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md)                                    | Non-Functional Requirements (ISO 25010)           | 1    | P0  | UNBLOCK |
| 1.6  | [SRIS-P1-REQ-006](./SRIS-P1-REQ-006_UserStoriesAndUseCases.md)                                              | User Stories and Use Cases                        | 1    | P0  | UNBLOCK |
| 1.7  | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)                                          | Domain Rules: Fare Calculation                    | 1    | P1  | FOLLOW  |
| 1.8  | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)                                                | Domain Rules: Ticketing                           | 1    | P1  | FOLLOW  |
| 1.9  | [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)                                  | Domain Rules: Waitlist and Cancellation           | 1    | P1  | FOLLOW  |
| 1.10 | [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md)                                         | Domain Rules: Chart Preparation                   | 1    | P1  | FOLLOW  |
| 1.11 | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)                                   | Domain Rules: Seat Matrix and Inventory           | 1    | P1  | FOLLOW  |
| 1.12 | [SRIS-P1-REQ-012](./SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md)                                    | Requirement Traceability Matrix (RTM)             | 1    | P2  | FOLLOW  |
| 2.1  | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)                  | Microservices Identification                      | 2    | P0  | UNBLOCK |
| 2.3  | [SRIS-P1-ARCH-003](../wave-2-architecture/SRIS-P1-ARCH-003_SystemArchitectureDocument.md)                   | System Architecture Document                      | 2    | P0  | UNBLOCK |
| 2.4  | [SRIS-P1-ARCH-004](../wave-2-architecture/SRIS-P1-ARCH-004_BoundedContextMap.md)                            | Bounded Context Map                               | 2    | P0  | UNBLOCK |
| 2.8  | [SRIS-P1-ARCH-008](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md)                           | Technology Stack ADR                              | 2    | P0  | UNBLOCK |
| 2.9  | [SRIS-P1-ARCH-009](../wave-2-architecture/SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md)     | Service Interaction and Communication Design      | 2    | P0  | UNBLOCK |
| 2.14 | [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md)     | Distributed Concurrency and Locking Strategy      | 2    | P0  | UNBLOCK |
| 2.15 | [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md)   | Distributed Transaction and Saga Pattern Design   | 2    | P0  | UNBLOCK |
| 3.2  | [SRIS-P1-DATA-002](../wave-3-detailed-design/SRIS-P1-DATA-002_LogicalDataModelPerService.md)                | Logical Data Model (per service)                  | 3    | P0  | UNBLOCK |
| 3.3  | [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)            | Physical Database Schema Document                 | 3    | P0  | UNBLOCK |
| 3.8  | [SRIS-P1-DATA-008](../wave-3-detailed-design/SRIS-P1-DATA-008_HighConcurrencySegmentInventoryDataModel.md)  | High-Concurrency Segment Inventory Data Model     | 3    | P0  | UNBLOCK |
| 3.14 | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)                  | API Contract Document (OpenAPI)                   | 3    | P0  | UNBLOCK |
| 3.16 | [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md)                 | Event Schema Document (AsyncAPI)                  | 3    | P0  | UNBLOCK |
| 3.18 | [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md)      | Idempotency and Retry Policy Specification        | 3    | P0  | UNBLOCK |
| 3.24 | [SRIS-P1-API-011](../wave-3-detailed-design/SRIS-P1-API-011_PaymentGatewayIntegrationDesignMock.md)         | Payment Gateway Integration Design (Mock)         | 3    | P1  | FOLLOW  |
| 3.25 | [SRIS-P1-API-012](../wave-3-detailed-design/SRIS-P1-API-012_NotificationIntegrationDesign.md)               | Notification Integration Design                   | 3    | P1  | FOLLOW  |
| 3.27 | [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md)                      | UI/UX Requirements Document                       | 3    | P0  | UNBLOCK |
| 3.28 | [SRIS-P1-UI-002](../wave-3-detailed-design/SRIS-P1-UI-002_ScreenInventoryAndNavigationMap.md)               | Screen Inventory and Navigation Map               | 3    | P0  | UNBLOCK |
| 3.29 | [SRIS-P1-UI-003](../wave-3-detailed-design/SRIS-P1-UI-003_WireframesCustomerFlow.md)                        | Wireframes (Customer Flow)                        | 3    | P0  | UNBLOCK |
| 3.30 | [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md)                   | Wireframes (Employee/Admin Flow)                  | 3    | P0  | UNBLOCK |
| 3.38 | [SRIS-P1-UI-012](../wave-3-detailed-design/SRIS-P1-UI-012_InternationalizationAndLocalizationDesign.md)     | Internationalization and Localization Design      | 3    | P2  | FOLLOW  |
| 3.39 | [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)        | Authentication and Authorization Design           | 3    | P1  | FOLLOW  |
| 3.40 | [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md)                                   | RBAC Matrix                                       | 3    | P1  | FOLLOW  |
| 3.41 | [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)                      | JWT Token Design and Claims                       | 3    | P1  | FOLLOW  |
| 4.3  | [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)                                | Test Cases (Functional)                           | 4    | P0  | UNBLOCK |
| 9.1  | [SRIS-P1-NFR-HOLD-001](../wave-9-supporting-artifacts/SRIS-P1-NFR-HOLD-001_LoadModelAndResourceFitCheckHolding.md) | Load Model and Resource Fit Check (Holding)  | 9    | —   | HOLD    |

### B.2 Documents That Reference This Document

| Seq  | Document ID                                                                                | Document Name                          | Why It References                                                              |
| ---- | ------------------------------------------------------------------------------------------ | -------------------------------------- | ------------------------------------------------------------------------------ |
| 0.0  | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) | Documentation Index and Navigation Map | Lists this document in the register and in the reading paths                   |
| 0.4  | [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)      | Project Vision and Scope Document      | Lists this document as unblocked by its approval                               |
| 1.1  | [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md)                           | Glossary and Domain Dictionary         | Names this document as the owning document for 23 railway domain terms         |
| 1.2  | [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md)                      | Business Requirements Document (BRD)   | Names this document as the fixer of the provisional capability list (OI-1)     |
| 2.1  | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)             | Microservices Identification           | Lists this document as a Hard upstream document                                |

### B.3 Documents This Document Depends On (Upstream)

| Seq | Document ID                                                                                 | Document Name                          | Dependency Type |
| --- | ------------------------------------------------------------------------------------------- | -------------------------------------- | --------------- |
| 0.0 | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) | Documentation Index and Navigation Map | Soft            |
| 0.1 | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)           | Document Template Standard             | Hard            |
| 0.2 | [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)        | Document ID and Category Scheme        | Hard            |
| 0.3 | [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md)     | Document Cross-Reference Standard      | Hard            |
| 0.4 | [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)      | Project Vision and Scope Document      | Hard            |
| 1.1 | [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md)                           | Glossary and Domain Dictionary         | Hard            |
| 1.2 | [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md)                      | Business Requirements Document (BRD)   | Hard            |
| 2.1 | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)             | Microservices Identification           | Hard            |

### B.4 Documents This Document Unblocks (Downstream)

| Seq  | Document ID                                                                      | Document Name                                | Blocked Until |
| ---- | -------------------------------------------------------------------------------- | -------------------------------------------- | ------------- |
| 1.4  | [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md)         | Software Requirements Specification (SRS)    | This approved |
| 1.5  | [SRIS-P1-REQ-005](./SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md)            | Non-Functional Requirements (ISO 25010)      | This approved |
| 1.6  | [SRIS-P1-REQ-006](./SRIS-P1-REQ-006_UserStoriesAndUseCases.md)                       | User Stories and Use Cases                   | This approved |
| 1.12 | [SRIS-P1-REQ-012](./SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md)             | Requirement Traceability Matrix (RTM)        | This approved |

### B.5 Master Documentation Index

The complete list of Phase 1 documents is in [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

### B.6 External Reference Documents

None. SRIS-P1-REQ-003 does not depend on any source outside the Phase 1 register.

### B.7 Document Conventions

The conventions for Priority and Tag values are defined in [Section 9](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md#9-vocabulary-standards) of [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.

---

**End of Document**