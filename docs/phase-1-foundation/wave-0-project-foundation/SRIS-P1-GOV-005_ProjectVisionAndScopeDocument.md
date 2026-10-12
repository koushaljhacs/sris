<div align="center">

![Wave](https://img.shields.io/badge/Wave-0-0550AE?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-GOV-6e7781?style=for-the-badge)

</div>

# Project Vision and Scope Document

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** 1.0 | **Date:** 2026-10-12 | **Document ID:** SRIS-P1-GOV-005

| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| Title              | Project Vision and Scope Document                                 |
| Software           | SRIS                                                              |
| Software Full Form | Sarathi Railway Information System                                |
| Team Codename      | Project Sarathi                                                   |
| Document ID        | SRIS-P1-GOV-005                                                   |
| Task               | Define SRIS vision, mission, motivation, and Phase 1 scope        |
| Document Type      | Governance Document                                               |
| Milestone          | Phase 1 Foundation                                                |
| Classification     | Internal                                                          |
| Version            | 1.0                                                               |
| Date               | 2026-10-12                                                        |
| Author             | Koushal Jha, Lead Architect                                       |
| Approved By        | Koushal Jha, Lead Architect                                       |
| Approval Date      | 2026-10-12                                                        |
| Supersedes         | None (first version)                                              |
| Related Documents  | See Appendix B                                                    |
| Affiliation        | Independent · Not affiliated with CRIS, IRCTC, or Indian Railways |

---

## Table of Contents

1. [Introduction](#1-introduction)
   - [1.1 Purpose](#11-purpose)
   - [1.2 Scope](#12-scope)
   - [1.3 Audience](#13-audience)
2. [Vision Statement](#2-vision-statement)
3. [Mission](#3-mission)
4. [Motivation and Rationale](#4-motivation-and-rationale)
   - [4.1 The Engine Analogy](#41-the-engine-analogy)
   - [4.2 Academic Requirement](#42-academic-requirement)
   - [4.3 Engineering Challenge](#43-engineering-challenge)
   - [4.4 Application of Learning](#44-application-of-learning)
   - [4.5 Portfolio Value](#45-portfolio-value)
   - [4.6 Why This Document Anchors the Project](#46-why-this-document-anchors-the-project)
5. [Phase 1 Scope](#5-phase-1-scope)
   - [5.1 In Scope](#51-in-scope)
   - [5.2 Out of Scope](#52-out-of-scope)
6. [Success Criteria](#6-success-criteria)
   - [6.1 Phase 1 Success Criterion](#61-phase-1-success-criterion)
   - [6.2 Proposed Measurable Criteria](#62-proposed-measurable-criteria)
   - [6.3 Priority Order If Time Runs Short](#63-priority-order-if-time-runs-short)
7. [Constraints](#7-constraints)
8. [Assumptions](#8-assumptions)
9. [Approval](#9-approval)

- [Revision History](#revision-history)
- [Appendix A: Not Applicable](#appendix-a-not-applicable)
- [Appendix B: Related Documents](#appendix-b-related-documents)

---

## 1. Introduction

### 1.1 Purpose

This document defines what the Sarathi Railway Information System (SRIS) is, why the project exists, and what Phase 1 delivers. It is the anchor for every downstream requirement, design, and test document, and those documents are expected to remain consistent with the vision, mission, scope, and constraints recorded here. It also states the criterion by which Phase 1 is judged complete.

### 1.2 Scope

**In scope**

- The vision statement and mission of SRIS.
- The motivation and rationale for the project.
- The outcome, boundary, and deliverables of Phase 1.
- The proposed success criteria for Phase 1.
- The constraints and assumptions under which Phase 1 is carried out.

**Out of scope**

- The register of project documents and its navigation map, which are maintained in [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.
- The document template and formatting rules, which are defined in [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.
- The rules for cross-referencing between documents, which are defined in [SRIS-P1-GOV-004](./SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md) — Document Cross-Reference Standard.
- The service catalogue and service boundaries, which are defined in [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification.
- The selection of any language, database, framework, or tool, which is to be decided in [SRIS-P1-ARCH-008](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md) — Technology Stack ADR.
- Detailed functional and non-functional requirements, detailed designs, and test cases.
- The definition of Phase 2 or any later phase, beyond the list of deferred capabilities in Section 5.2.

### 1.3 Audience

- **Lead Architect:** author and approver of this document, and the decision authority for Phase 1.
- **Project team (Group G320):** the four team members other than the Lead Architect, who are assigned tasks against the project documents and use this document to understand what is being built and why.
- **Project supervisor and evaluator:** Anupam Yadav, who evaluates the project.
- **Technical reviewers:** any engineer, interviewer, or recruiter who opens the repository and needs the context of the project.

---

## 2. Vision Statement

> SRIS demonstrates that a small team can design and build the transactional engine of a railway reservation system, with the architectural and documentation discipline expected of a production system, within the limits of an academic project.

In this vision, a customer books a train ticket on a booking website, a seat is never sold to two customers, and every confirmed booking carries a 10-digit PNR that can be used to retrieve the ticket. The engine is configured by railway employees through a separate administrative console.

SRIS is an independent academic project. It is not affiliated with Indian Railways, the Centre for Railway Information Systems (CRIS), or the Indian Railway Catering and Tourism Corporation (IRCTC).

---

## 3. Mission

The mission of SRIS is to deliver Phase 1 by 30 November 2026: a working end-to-end booking flow, supported by six microservices and two user-facing surfaces, together with a locked set of 180 project documents and a consolidated PDF book of those documents, all within a 5.1 GB RAM local environment and a zero budget. The mission is pursued under four working principles:

- **Engine before product:** effort goes first to the transactional core (master data, search, seat hold, payment, PNR, and confirmation) rather than to breadth of railway features.
- **One complete flow:** Phase 1 delivers a single flow end to end, rather than several flows that are only partly working.
- **Documented decisions:** design decisions are recorded in the project document set, and the documents that must precede coding are identified in [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.
- **Within limits:** every decision is made inside the hardware, budget, and time constraints in Section 7.

---

## 4. Motivation and Rationale

### 4.1 The Engine Analogy

In the framing adopted by this project, IRCTC is the product that passengers see, and CRIS is the engine behind it. SRIS is the Lead Architect's own version of the engine, built as an academic engine that simulates only the payment gateway, to understand and demonstrate how such a system is designed.

The analogy is bounded as follows:

- SRIS runs in a local environment. The payment gateway is a mock. Email delivery uses Gmail SMTP. SMS delivery uses a free-tier messaging service.
- SRIS uses IRCTC, CRIS, and Indian Railways only as domain reference. It does not compete with, replace, or claim equivalence to any of them.
- SRIS makes no claim of production scale, certification, or operational readiness.

### 4.2 Academic Requirement

SRIS is the major project for the VII semester of the Computer Science programme at GLA University, Mathura. It is undertaken by Group G320 under a project supervisor, who acts as the evaluator.

### 4.3 Engineering Challenge

The project category is Software Engineering and Distributed Systems, which raises the engineering bar. A reservation engine must handle concurrent requests, keep seat inventory consistent, and isolate failures between services. The project is expected to show mastery of software engineering, not only a working demonstration, so the architecture, the recorded decisions, and the document set form part of what is delivered.

### 4.4 Application of Learning

The project applies four years of study, together with AI-assisted tools, to one substantial piece of engineering work. It is undertaken at a time when such tools are changing how software is produced. It is intended to demonstrate the architectural judgement and design discipline that remain the engineer's responsibility whatever tools are used.

### 4.5 Portfolio Value

SRIS is both a learning instrument and a portfolio piece. A reader who opens the repository should find a real architecture and a traceable document set, not a simple create-read-update-delete application.

### 4.6 Why This Document Anchors the Project

If the vision is weak, the requirements, designs, and tests built on it are weak. This document therefore fixes the vision, scope, and constraints before those documents are written.

---

## 5. Phase 1 Scope

Phase 1 runs from 01 October 2026 to 30 November 2026, a period of about eight weeks. This section defines what Phase 1 includes and what it defers.

### 5.1 In Scope

**Phase 1 outcome**

A customer books a train ticket end to end on the Customer Booking Website, using master data set up by an employee through the Employee Admin Console. The ten-step booking flow below describes how this outcome is reached.

**Ten-step booking flow**

| Step | Actor    | Action                                                            |
| ---- | -------- | ----------------------------------------------------------------- |
| 1    | Employee | Logs in to the Employee Admin Console                             |
| 2    | Employee | Configures stations, routes, trains, schedules, fares, and quotas |
| 3    | Customer | Registers and logs in on the Customer Booking Website             |
| 4    | Customer | Searches for trains                                               |
| 5    | Customer | Selects a train, class, and quota                                 |
| 6    | Customer | Holds a seat                                                      |
| 7    | Customer | Pays through the mock payment gateway                             |
| 8    | System   | Confirms the booking and issues a 10-digit PNR                    |
| 9    | System   | Sends email and SMS confirmations                                 |
| 10   | Customer | Retrieves the ticket by PNR                                       |

**Capabilities in scope**

- Customer registration and login.
- Employee authentication and role-based access control.
- Master data setup: stations, routes, trains, schedules, fares, and quotas.
- Customer train search.
- Seat availability and seat hold.
- Mock payment.
- PNR generation.
- Email and SMS notification.

**User-facing surfaces**

| Surface                  | Intended Users    |
| ------------------------ | ----------------- |
| Customer Booking Website | Passengers        |
| Employee Admin Console   | Railway employees |

**Phase 1 deliverables**

All five deliverables are required.

| Seq | Deliverable                     | Description                                                               |
| --- | ------------------------------- | ------------------------------------------------------------------------- |
| 1   | Working end-to-end booking flow | The ten-step booking flow, demonstrated in a single run                   |
| 2   | Six microservices               | The six services identified for Phase 1, implemented and running together |
| 3   | Two user-facing surfaces        | The Customer Booking Website and the Employee Admin Console               |
| 4   | 180 project documents           | The locked document register, complete and approved                       |
| 5   | Consolidated PDF book           | One PDF containing all 180 documents                                      |

The six microservices are those identified in [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification. That document is the authoritative service catalogue, and this document does not repeat the names or responsibilities of the services.

### 5.2 Out of Scope

The following capabilities are deferred to Phase 2 or later:

- Train running status and delay tracking.
- Disruption management.
- Platform allocation.
- Station facilities management.
- Employee HR records.
- Crew rostering.
- Leave and attendance.
- Operational dashboards.
- Passenger grievance handling.
- Catering.
- Vendor management.

The following are also outside Phase 1:

- Connection to any live system of Indian Railways, CRIS, or IRCTC.
- Real payment processing.

---

## 6. Success Criteria

### 6.1 Phase 1 Success Criterion

Phase 1 is successful when all five deliverables listed in Section 5.1 exist by 30 November 2026. Delivering some of the five does not meet the criterion.

### 6.2 Proposed Measurable Criteria

The criteria in this section are proposed, pending confirmation, and are not final. Any numeric target is marked "proposed, pending confirmation" in the criterion itself.

| ID   | Criterion                                                                                                                                                            | Verification Method                                                    |
| ---- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| SC-1 | All five deliverables exist and are linked from [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map. | Inspect the links in the documentation index                           |
| SC-2 | A single demo run performs the full ten-step booking flow, from employee login to customer PNR retrieval.                                                            | Observe one uninterrupted demo run                                     |
| SC-3 | The booking flow completes without manual data patching.                                                                                                             | Confirm that no data is edited outside the two surfaces during the run |
| SC-4 | Each confirmed booking returns a 10-digit PNR, and retrieving the ticket by that PNR returns the booked ticket.                                                      | Check the PNR format and retrieval in the demo run                     |
| SC-5 | Two simultaneous requests for the last available seat in a class result in exactly one confirmed booking (proposed, pending confirmation).                           | Run a concurrent booking test                                          |
| SC-6 | All six microservices run together within 5.1 GB RAM during the demo run (proposed, pending confirmation).                                                           | Measure peak memory use of the full local environment                  |
| SC-7 | The 180-document register is complete, and every document carries a Version, an Approval row, and a Revision History row.                                            | Inspect every document in the register                                 |
| SC-8 | The consolidated PDF book contains all 180 documents.                                                                                                                | Inspect the contents of the book                                       |

### 6.3 Priority Order If Time Runs Short

If time runs short, effort is directed in this order: the booking flow first, then the six microservices, then the two surfaces, then the documents, then the PDF book. This order guides the allocation of effort only. It does not change the success criterion in Section 6.1, which requires all five deliverables.

---

## 7. Constraints

- **C-1 Timeline:** Phase 1 runs from 01 October 2026 to 30 November 2026, a period of about eight weeks.
- **C-2 Hardware:** the full local environment must fit within 5.1 GB RAM. This is the operative Phase 1 hardware constraint, and it shaped the decision to use six microservices.
- **C-3 Budget:** the budget is zero. No paid services or tooling are used.
- **C-4 Staffing:** research, documentation, architecture, and technology decisions for Phase 1 are carried out by the Lead Architect alone. The four other team members are assigned tasks against the documents the Lead Architect produces and are not involved in Phase 1 planning.
- **C-5 Document register:** the register is locked at 180 documents across ten waves, as recorded in [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.
- **C-6 Independence:** SRIS is an independent academic project and is not affiliated with Indian Railways, CRIS, or IRCTC.
- **C-7 Technology stack:** this document names no language, database, framework, or tool. The stack is to be decided in [SRIS-P1-ARCH-008](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md) — Technology Stack ADR and must fit within constraints C-2 and C-3.

---

## 8. Assumptions

- **A-1:** the register of 180 documents remains locked for the whole of Phase 1, as recorded in [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.
- **A-2:** a technology stack that fits within 5.1 GB RAM and a zero budget can be selected in [SRIS-P1-ARCH-008](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md) — Technology Stack ADR.
- **A-3:** payment remains simulated through a mock gateway, and email and SMS delivery use free-tier services that require no paid provider.
- **A-4:** the four other team members are available to take assigned tasks against completed documents during the Phase 1 period.
- **A-5:** the project supervisor evaluates Phase 1 against the deliverables defined in this document.
- **A-6:** publicly known railway reservation concepts, such as the 10-digit PNR, travel classes, and quotas, are sufficient as domain reference, and no confidential railway data is needed.

---

## 9. Approval

| Role           | Name        | Decision | Date       |
| -------------- | ----------- | -------- | ---------- |
| Lead Architect | Koushal Jha | Approved | 2026-10-12 |

---

## Revision History

| Version | Date       | Author      | Change           |
| ------- | ---------- | ----------- | ---------------- |
| 1.0     | 2026-10-12 | Koushal Jha | Initial release. |

---

## Appendix A: Not Applicable

Not applicable.

---

## Appendix B: Related Documents

### B.1 Directly Referenced Documents

| Seq | Document ID                                                                                | Document Name                          | Wave | Pri | Tag     |
| --- | ------------------------------------------------------------------------------------------ | -------------------------------------- | ---- | --- | ------- |
| 0.0 | [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md)                 | Documentation Index and Navigation Map | 0    | P0  | UNBLOCK |
| 0.1 | [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md)                           | Document Template Standard             | 0    | P0  | UNBLOCK |
| 0.3 | [SRIS-P1-GOV-004](./SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md)                     | Document Cross-Reference Standard      | 0    | P1  | UNBLOCK |
| 2.1 | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) | Microservices Identification           | 2    | P0  | UNBLOCK |
| 2.8 | [SRIS-P1-ARCH-008](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md)          | Technology Stack ADR                   | 2    | P0  | UNBLOCK |

### B.2 Documents That Reference This Document

Citations of this document are tracked through the register in [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map. Every Wave 1 Requirements, Wave 2 Architecture, Wave 3 Detailed Design, and Wave 4 Testing document is expected to cite this document as the vision and scope anchor.

### B.3 Documents This Document Depends On (Upstream)

| Seq | Document ID                                                                                | Document Name                          | Dependency Type |
| --- | ------------------------------------------------------------------------------------------ | -------------------------------------- | --------------- |
| 0.0 | [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md)                 | Documentation Index and Navigation Map | Soft            |
| 0.1 | [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md)                           | Document Template Standard             | Hard            |
| 2.1 | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) | Microservices Identification           | Soft            |

### B.4 Documents This Document Unblocks (Downstream)

| Seq | Document ID                                                                                  | Document Name                        | Blocked Until |
| --- | -------------------------------------------------------------------------------------------- | ------------------------------------ | ------------- |
| 1.2 | [SRIS-P1-REQ-002](../wave-1-requirements/SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) | Business Requirements Document (BRD) | This approved |
| 1.3 | [SRIS-P1-REQ-003](../wave-1-requirements/SRIS-P1-REQ-003_CapabilityCatalogFinal.md)          | Capability Catalog (Final)           | This approved |
| 2.8 | [SRIS-P1-ARCH-008](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md)            | Technology Stack ADR                 | This approved |

### B.5 Master Documentation Index

The master documentation index is [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

### B.6 External Reference Documents

None. IRCTC, CRIS, and Indian Railways are used only as domain reference, and none of their documents is reproduced here.

### B.7 Document Conventions

The conventions for Priority and Tag values are defined in [Section 9](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#9-vocabulary-standards) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.