<div align="center">

![Wave](https://img.shields.io/badge/Wave-1-0550AE?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-REQ-6e7781?style=for-the-badge)

</div>

# Business Requirements Document (BRD)

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** 1.0 | **Date:** 2026-10-14 | **Document ID:** SRIS-P1-REQ-002

| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| Title              | Business Requirements Document (BRD)                              |
| Software           | SRIS                                                              |
| Software Full Form | Sarathi Railway Information System                                |
| Team Codename      | Project Sarathi                                                   |
| Document ID        | SRIS-P1-REQ-002                                                   |
| Task               | Define the business needs that Phase 1 of SRIS must meet          |
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
2. [Business Background](#2-business-background)
   - [2.1 Vision](#21-vision)
   - [2.2 Mission](#22-mission)
   - [2.3 Business Context](#23-business-context)
   - [2.4 Business Need](#24-business-need)
3. [Business Objectives](#3-business-objectives)
4. [Stakeholders](#4-stakeholders)
5. [Business Scope](#5-business-scope)
   - [5.1 Phase 1 Outcome](#51-phase-1-outcome)
   - [5.2 Capabilities in Scope](#52-capabilities-in-scope)
   - [5.3 Surfaces and Deliverables](#53-surfaces-and-deliverables)
   - [5.4 Out of Scope and Deferred Capabilities](#54-out-of-scope-and-deferred-capabilities)
6. [Business Process](#6-business-process)
   - [6.1 The Booking Flow](#61-the-booking-flow)
   - [6.2 Actors in the Flow](#62-actors-in-the-flow)
7. [Business Requirements](#7-business-requirements)
   - [7.1 Identity and Access](#71-identity-and-access)
   - [7.2 Master Data and Pricing](#72-master-data-and-pricing)
   - [7.3 Search and Discovery](#73-search-and-discovery)
   - [7.4 Seat Availability and Allocation](#74-seat-availability-and-allocation)
   - [7.5 Payment](#75-payment)
   - [7.6 Booking and Ticketing](#76-booking-and-ticketing)
   - [7.7 Notification](#77-notification)
   - [7.8 Surfaces](#78-surfaces)
   - [7.9 Deliverables](#79-deliverables)
8. [Business Rules](#8-business-rules)
   - [8.1 Booking Rules](#81-booking-rules)
   - [8.2 Service Ownership Rules](#82-service-ownership-rules)
   - [8.3 Delivery Rules](#83-delivery-rules)
9. [Delivery Requirements](#9-delivery-requirements)
   - [9.1 Sprints and Schedule](#91-sprints-and-schedule)
   - [9.2 Roles](#92-roles)
   - [9.3 Testing and Reporting](#93-testing-and-reporting)
   - [9.4 Branching and Versioning](#94-branching-and-versioning)
10. [Success Criteria](#10-success-criteria)
    - [10.1 Phase 1 Success Criterion](#101-phase-1-success-criterion)
    - [10.2 Proposed Measurable Criteria](#102-proposed-measurable-criteria)
    - [10.3 Priority Order If Time Runs Short](#103-priority-order-if-time-runs-short)
11. [Constraints and Assumptions](#11-constraints-and-assumptions)
    - [11.1 Constraints](#111-constraints)
    - [11.2 Assumptions](#112-assumptions)
12. [Risks and Open Items](#12-risks-and-open-items)
    - [12.1 Risks](#121-risks)
    - [12.2 Open Items](#122-open-items)
13. [Traceability](#13-traceability)
14. [Approval](#14-approval)

- [Revision History](#revision-history)
- [Appendix A: Not Applicable](#appendix-a-not-applicable)
- [Appendix B: Related Documents](#appendix-b-related-documents)

---

## 1. Introduction

### 1.1 Purpose

This document is the Business Requirements Document (BRD) of Phase 1 of SRIS (Sarathi Railway Information System). It states what the business needs, in business language, before any need is translated into software terms. It follows [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary, which fixes the vocabulary, and precedes [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final), which fixes the final list of capabilities.

The document records the business background, objectives, stakeholders, scope, and business process of Phase 1. It then records the business requirements, business rules, delivery requirements, success criteria, constraints, assumptions, risks, and open items. Every business requirement and every business rule names the source document and section that it traces to. Where the detailed rule of a topic belongs to another document, this document cites the owner and does not restate the rule.

### 1.2 Scope

**In scope**

- The business background and the motivation for Phase 1.
- The business objectives of Phase 1 and the measures that show they are met.
- The stakeholders and what each needs from Phase 1.
- The business scope: the capabilities in scope and the capabilities deferred.
- The business process of the ten-step booking flow.
- The business requirements and business rules of Phase 1.
- The delivery requirements, success criteria, constraints, assumptions, risks, and open items that bound Phase 1.

**Out of scope**

- The full vision, mission, scope, deliverables, success criteria, constraints, and assumptions, which are defined in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document.
- The final list of capabilities and their numbering, which is defined in [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final).
- Software requirements as software requirements, which belong to [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software Requirements Specification (SRS).
- Non-functional requirements, which belong to [SRIS-P1-REQ-005](./SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md) — Non-Functional Requirements (ISO 25010).
- User stories and use cases, which belong to [SRIS-P1-REQ-006](./SRIS-P1-REQ-006_UserStoriesAndUseCases.md) — User Stories and Use Cases.
- The detailed domain rules for fare, ticketing, waitlist and cancellation, chart preparation, and seat matrix and inventory, which belong to [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) to [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md).
- The service catalogue and service boundaries, which are defined in [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification.
- The choice of language, database, framework, or tool, which is defined in [SRIS-P1-ARCH-008](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md) — Technology Stack ADR.
- The full schedule, roles, testing approach, branching model, and versioning rules, which are defined in [SRIS-P1-GOV-007](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md) — Project Management Plan.
- The vocabulary of railway and system terms, which is defined in [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary.

### 1.3 Audience

- **Lead Architect:** maintains this document and uses it as the anchor for the requirement documents that follow.
- **Project team:** the four team members other than the Lead Architect, who read the business needs before they build against the frozen contracts.
- **Project supervisor and evaluator:** evaluates Phase 1 against the deliverables defined in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document.
- **Technical reviewers:** any engineer, interviewer, or recruiter who opens the repository and needs the business context of Phase 1.

### 1.4 Terminology and Conventions

Every term in this document has the meaning recorded in [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary. The terms below carry the most weight in this document. Where a term's detailed rule belongs to another document, the owner is cited.

| Term              | Meaning                                                                                                |
| ----------------- | ------------------------------------------------------------------------------------------------------ |
| Booking           | The end-to-end flow in which a customer requests travel, selects a seat, pays, and receives a ticket.   |
| Reservation       | The act of securing a defined seat or waitlist position within the inventory matrix.                    |
| Seat allocation   | The process of assigning a specific physical seat or berth to a confirmed booking.                     |
| Confirmation      | The state in which a booking has secured payment and obtained a guaranteed seat or RAC position.        |
| PNR               | Passenger Name Record. A unique ten-digit identifier that locates a booking and its passengers.         |
| Seat matrix       | The generated set of all physical seats and berths available for a specific train journey.              |
| Master data setup | The administrative process of configuring static network parameters such as stations, distances, and trains. |
| Fare quote        | An estimated total price shown during search, before final quota and concession validation.             |
| Fare re-quote     | The final authoritative price calculation performed before payment, incorporating all selected criteria. |
| Customer          | The account holder.                                                                                    |
| Passenger         | An individual traveller associated with a booking, with attributes such as age, gender, and berth preference. |
| Employee          | The actor on the Employee Admin Console. Employees configure the network.                              |

The identifier prefixes below are used in this document. Each identifier is local to this document.

| Prefix | Meaning             |
| ------ | ------------------- |
| BO     | Business objective  |
| BR     | Business requirement |
| BRL    | Business rule       |
| DR     | Delivery requirement |
| SC     | Success criterion, numbered as in its source document |
| BC     | Business constraint |
| BA     | Business assumption |
| RK     | Risk                |
| OI     | Open item           |

This document follows the standards below.

- [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard, for structure, header, and style.
- [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md) — Document ID and Category Scheme, for the Document ID.
- [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md) — Document Cross-Reference Standard, for citations and links.

---

## 2. Business Background

### 2.1 Vision

The vision of SRIS is that a small team can design and build the transactional engine of a railway reservation system, with the architectural and documentation discipline expected of a production system, within the limits of an academic project. The vision statement is recorded in [Section 2](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#2-vision-statement) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document.

In this vision, a customer books a train ticket on a booking website, a seat is never sold to two customers, and every confirmed booking carries a 10-digit PNR that can be used to retrieve the ticket. The engine is configured by railway employees through a separate administrative console.

### 2.2 Mission

The mission of SRIS is to deliver Phase 1 by 30 November 2026. Phase 1 delivers a working end-to-end booking flow supported by six microservices and two user-facing surfaces, together with a locked set of 180 project documents and a consolidated PDF book of those documents. All of this is done within a 5.1 GB RAM local environment and a zero budget, as recorded in [Section 3](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#3-mission) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document.

The mission is pursued under four working principles.

- **Engine before product:** effort goes first to the transactional core (master data, search, seat selection, payment, PNR, and confirmation) rather than to breadth of railway features.
- **One complete flow:** Phase 1 delivers a single flow end to end, rather than several flows that are only partly working.
- **Documented decisions:** design decisions are recorded in the project document set.
- **Within limits:** every decision is made inside the hardware, budget, and time constraints.

### 2.3 Business Context

In the framing adopted by the project, IRCTC is the product that passengers see, and CRIS is the engine behind it. SRIS is the Lead Architect's own version of that engine, built as an academic engine that simulates only the payment gateway. The framing is recorded in [Section 4.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#41-the-engine-analogy) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document.

The framing is bounded. SRIS runs in a local environment, its payment gateway is a mock, email delivery uses Gmail SMTP, and SMS delivery uses a free-tier messaging service. SRIS uses IRCTC, CRIS, and Indian Railways only as domain reference. It does not compete with, replace, or claim equivalence to any of them, and it makes no claim of production scale, certification, or operational readiness.

### 2.4 Business Need

The business need for Phase 1 has four parts. Each part is recorded in [Section 4](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#4-motivation-and-rationale) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document.

- **Academic requirement.** SRIS is the major project for the VII semester of the Computer Science programme at GLA University, Mathura. It is undertaken by Group G320 under a project supervisor, who acts as the evaluator.
- **Engineering challenge.** A reservation engine must handle concurrent requests, keep seat inventory consistent, and isolate failures between services. The architecture, the recorded decisions, and the document set form part of what is delivered.
- **Application of learning.** The project applies four years of study, together with AI-assisted tools, to one substantial piece of engineering work. It is intended to demonstrate the architectural judgement and design discipline that remain the engineer's responsibility.
- **Portfolio value.** A reader who opens the repository should find a real architecture and a traceable document set, not a simple create-read-update-delete application.

---

## 3. Business Objectives

The business objectives state what Phase 1 must achieve for the business. They follow the vision, mission, and scope in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document. Each objective names the success criteria that measure it, and the criteria are listed in [Section 10](#10-success-criteria).

| ID   | Objective                                                                                                                              | Measure       | Source                                                                                 |
| ---- | -------------------------------------------------------------------------------------------------------------------------------------- | ------------- | -------------------------------------------------------------------------------------- |
| BO-1 | Deliver a working end-to-end booking flow in which a customer books a train ticket using master data set up by an employee.             | SC-2, SC-3    | [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005 |
| BO-2 | Ensure that a seat is never sold to two customers.                                                                                     | SC-5          | [Section 2](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#2-vision-statement) of SRIS-P1-GOV-005 |
| BO-3 | Ensure that every confirmed booking carries a 10-digit PNR that retrieves the ticket.                                                  | SC-4          | [Section 2](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#2-vision-statement) of SRIS-P1-GOV-005 |
| BO-4 | Let railway employees configure the engine through a separate Employee Admin Console.                                                  | SC-2          | [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005 |
| BO-5 | Deliver the six microservices identified for Phase 1, running together.                                                                | SC-1, SC-6    | [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005 and [Section 6.1](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#61-service-catalog) of SRIS-P1-ARCH-001 |
| BO-6 | Deliver the two user-facing surfaces: the Customer Booking Website and the Employee Admin Console.                                     | SC-1, SC-2    | [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005 |
| BO-7 | Deliver the locked set of 180 project documents and the consolidated PDF book.                                                         | SC-7, SC-8    | [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005 |
| BO-8 | Show the architectural and documentation discipline expected of a production system, within the limits of an academic project.         | SC-7          | [Section 2](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#2-vision-statement) of SRIS-P1-GOV-005 |
| BO-9 | Complete Phase 1 by 30 November 2026, within a 5.1 GB RAM local environment and a zero budget.                                          | SC-1, SC-6    | [Section 3](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#3-mission) of SRIS-P1-GOV-005 |

---

## 4. Stakeholders

The stakeholders are drawn from [Section 1.3](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#13-audience) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document, for the audience of the project and the intended users of the two surfaces, and from [Section 7](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md#7-roles-and-responsibilities) of [SRIS-P1-GOV-007](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md) — Project Management Plan, for the roles in Phase 1.

| Stakeholder                  | Role in Phase 1                                                                                          | Business Need                                                                                          |
| ---------------------------- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| Lead Architect               | Author and approver of the project documents, decision authority for Phase 1, builder of frontend and backend where needed | A complete and consistent Phase 1, delivered by 30 November 2026                                       |
| Project team                 | The four team members other than the Lead Architect, who join active development from Week 3 Day 1        | Documents that state what is being built and why, and frozen contracts to build against                |
| Project supervisor and evaluator | Evaluates Phase 1 and takes no part in project decisions                                                 | Deliverables that can be inspected against the success criteria                                        |
| Technical reviewers          | Engineers, interviewers, or recruiters who open the repository                                            | The context of the project and a traceable document set                                                |
| Customers                    | Account holders who use the Customer Booking Website                                                      | To search for trains, select a seat, pay, and retrieve the ticket by PNR, with no seat sold twice      |
| Railway employees            | Employees who use the Employee Admin Console                                                              | To set up stations, routes, trains, schedules, fares, and quotas                                       |

---

## 5. Business Scope

### 5.1 Phase 1 Outcome

The outcome of Phase 1 is that a customer books a train ticket end to end on the Customer Booking Website, using master data set up by an employee through the Employee Admin Console. The outcome is recorded in [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document. The ten steps by which the outcome is reached are recorded in [Section 6.1](#61-the-booking-flow).

### 5.2 Capabilities in Scope

[Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document lists eight capabilities in scope for Phase 1. [Section 6.3](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#63-capability-traceability) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification assigns each capability domain to one owning service. The capability list is provisional until [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final) fixes it.

| Capability                                                          | Capability Domain                    | Owning Service                                                 |
| ------------------------------------------------------------------- | ------------------------------------ | -------------------------------------------------------------- |
| Customer registration and login                                     | Identity and Access                  | S1 IAM Service                                                 |
| Employee authentication and role-based access control               | Identity and Access                  | S1 IAM Service                                                 |
| Master data setup: stations, routes, trains, schedules, fares, quotas | Railway Master Data; Fare and Pricing | S2 Master Data and Pricing Service                             |
| Customer train search                                               | Search and Discovery                 | S4 Search Aggregator BFF                                       |
| Seat availability and seat selection                                | Inventory and Quota                  | S3 Reservation Service                                         |
| Mock payment                                                        | Payment                              | S3 Reservation Service; S5 Mock Payment Gateway                |
| PNR generation                                                      | Booking and Ticketing                | S3 Reservation Service                                         |
| Email and SMS notification                                          | Notification                         | S6 Notification Service                                        |

### 5.3 Surfaces and Deliverables

Phase 1 has two user-facing surfaces and five deliverables, as recorded in [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document.

| Surface                  | Intended Users    |
| ------------------------ | ----------------- |
| Customer Booking Website | Passengers        |
| Employee Admin Console   | Railway employees |

All five deliverables are required.

| Seq | Deliverable                     | Description                                                               |
| --- | ------------------------------- | ------------------------------------------------------------------------- |
| 1   | Working end-to-end booking flow | The ten-step booking flow, demonstrated in a single run                   |
| 2   | Six microservices               | The six services identified for Phase 1, implemented and running together |
| 3   | Two user-facing surfaces        | The Customer Booking Website and the Employee Admin Console               |
| 4   | 180 project documents           | The locked document register, complete and approved                       |
| 5   | Consolidated PDF book           | One PDF containing all 180 documents                                      |

### 5.4 Out of Scope and Deferred Capabilities

The capabilities below are deferred to Phase 2 or later, as recorded in [Section 5.2](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#52-out-of-scope) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document. They are catalogued in [Section 4.3](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#43-deferred-capabilities) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification. This document assigns no target phase to any of them.

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

The following are also outside Phase 1.

- Connection to any live system of Indian Railways, CRIS, or IRCTC.
- Real payment processing.

Refund processing, payment reconciliation and settlement, and in-app or push notifications are expected to be deferred, subject to confirmation, as recorded in [Section 4.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#42-phase-1-capabilities) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification. The confirmation is tracked as [OI-3](#122-open-items).

---

## 6. Business Process

### 6.1 The Booking Flow

The booking flow has ten steps, as recorded in [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document. The last column names the service that supports each step, as assigned in [Section 6.1](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#61-service-catalog) and [Section 6.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#62-service-specifications) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification.

| Step | Actor    | Action                                                            | Supporting Service                                        |
| ---- | -------- | ----------------------------------------------------------------- | --------------------------------------------------------- |
| 1    | Employee | Logs in to the Employee Admin Console                             | S1 IAM Service                                            |
| 2    | Employee | Configures stations, routes, trains, schedules, fares, and quotas | S2 Master Data and Pricing Service                        |
| 3    | Customer | Registers and logs in on the Customer Booking Website             | S1 IAM Service                                            |
| 4    | Customer | Searches for trains                                               | S4 Search Aggregator BFF, which draws on S2 and S3        |
| 5    | Customer | Selects a train, class, and quota                                 | S4 Search Aggregator BFF, which changes no data            |
| 6    | Customer | Commits to a seat for the selected train, class, and quota         | S3 Reservation Service                                    |
| 7    | Customer | Pays through the mock payment gateway                             | S5 Mock Payment Gateway, called by S3                      |
| 8    | System   | Confirms the booking and issues a 10-digit PNR                    | S3 Reservation Service                                    |
| 9    | System   | Sends email and SMS confirmations                                 | S6 Notification Service                                   |
| 10   | Customer | Retrieves the ticket by PNR                                       | S3 Reservation Service                                    |

Step 6 is stated at the business level. Its exact mechanism — whether the seat is protected before payment or allocation runs after payment succeeds — is decided in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing, and is tracked as [OI-4](#122-open-items).

### 6.2 Actors in the Flow

Steps 1 and 2 are performed by an employee. Steps 3 to 7 and step 10 are performed by a customer. Steps 8 and 9 are performed by the system. The payment gateway in step 7 is a simulator and not a real provider.

The flow is demonstrated in a single uninterrupted run and completes without manual data patching. These two conditions are SC-2 and SC-3 in [Section 10.2](#102-proposed-measurable-criteria).

---

## 7. Business Requirements

Each business requirement has an identifier, a statement, and a source. A requirement states what the business needs and not how software provides it. The requirements trace to the sources below.

- [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document, for the business scope and the booking flow.
- [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification, for the capability domains and the responsibilities of each service.

The requirements are written as software requirements in [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software Requirements Specification (SRS). The capabilities that the requirements rely on are provisional until [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final) fixes the final list. Where a requirement touches a domain rule, the detailed rule belongs to the owning document and is cited in the requirement.

### 7.1 Identity and Access

- **BR-1** A customer must be able to register and log in on the Customer Booking Website. Source: [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005.
- **BR-2** An employee must be authenticated before using the Employee Admin Console. Source: [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005.
- **BR-3** The actions that an employee can perform must depend on the role that the employee holds. Source: [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005 and [Section 6.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#62-service-specifications) of SRIS-P1-ARCH-001.
- **BR-4** Only the login identity of an employee must be held for access purposes, and employment records are outside Phase 1. Source: [Section 6.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#62-service-specifications) of SRIS-P1-ARCH-001 and [Section 5.2](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#52-out-of-scope) of SRIS-P1-GOV-005.

### 7.2 Master Data and Pricing

- **BR-5** An employee must be able to set up stations, routes, trains, schedules, fares, and quotas through the Employee Admin Console. Source: [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005.
- **BR-6** All static railway configuration and all fare rules must be held in one place that is the single source of truth. Source: [Section 6.1](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#61-service-catalog) of SRIS-P1-ARCH-001.
- **BR-7** Master data must cover stops and distances along each route, running days and timings of each train, coach composition and berth layout, and class and quota definitions. Source: [Section 4.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#42-phase-1-capabilities) of SRIS-P1-ARCH-001.
- **BR-8** Fare rules must cover a base fare per kilometre by class, dynamic pricing rules, and concessions, and the business must be able to give a fare quote. The detailed fare calculation rules are decided in [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) — Domain Rules: Fare Calculation. Source: [Section 4.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#42-phase-1-capabilities) of SRIS-P1-ARCH-001.

### 7.3 Search and Discovery

- **BR-9** A customer must be able to search for trains by route and date. Source: [Section 4.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#42-phase-1-capabilities) of SRIS-P1-ARCH-001 and [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005.
- **BR-10** One search must return the schedule, the seat availability, and the fare together as one combined result. Source: [Section 4.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#42-phase-1-capabilities) of SRIS-P1-ARCH-001.
- **BR-11** A search must not change any stored data. Source: [Section 6.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#62-service-specifications) of SRIS-P1-ARCH-001.
- **BR-12** A customer must be able to select a train, a class, and a quota from the search result. Source: [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005.

### 7.4 Seat Availability and Allocation

- **BR-13** The business must be able to tell a customer the seat availability for a train, a class, and a quota. Source: [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005 and [Section 4.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#42-phase-1-capabilities) of SRIS-P1-ARCH-001.
- **BR-14** The seat matrix for each train journey must be generated from master data, and its seats must be divided into quotas before bookings begin. The detailed rules for the seat matrix and quota allocation are decided in [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md) — Domain Rules: Seat Matrix and Inventory. Source: [Section 4.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#42-phase-1-capabilities) of SRIS-P1-ARCH-001.
- **BR-15** The system must protect the seat that a customer has selected, so that another customer cannot take the same seat while the first customer is completing their booking. The mechanism that protects the seat is decided in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing, and is tracked as [OI-4](#122-open-items).
- **BR-16** If a customer's payment succeeds but a seat cannot be allocated, the customer's money must be returned through the mock payment gateway. The mechanism that returns the money is decided in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing, and is tracked as [OI-4](#122-open-items).
- **BR-16a** When all confirmed seats of a train for a given class and quota are occupied, further customers must be placed on a waitlist in the same class and quota. The waitlist order, cascade rules, and any further fallback to a pooled or remote waitlist are decided in [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md) — Domain Rules: Waitlist and Cancellation, and are tracked as [OI-5](#122-open-items).

### 7.5 Payment

- **BR-17** A customer must be able to complete payment for the seat they have selected. A customer may abandon the payment step; the system does not force payment. Source: [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005.
- **BR-18** The mock payment gateway must process a dummy payment with configurable outcomes and return a signed result to the booking. Source: [Section 6.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#62-service-specifications) of SRIS-P1-ARCH-001.
- **BR-19** Each payment attempt must be recorded, and the payment result must be verified. The verification and idempotency rules are decided in [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md) — Idempotency and Retry Policy Specification. Source: [Section 6.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#62-service-specifications) of SRIS-P1-ARCH-001.

### 7.6 Booking and Ticketing

- **BR-20** The system must confirm a booking and issue a 10-digit PNR. Source: [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005.
- **BR-21** A customer must be able to retrieve the ticket by PNR, and the ticket returned must be the booked ticket. Source: [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) and [Section 6.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#62-service-specifications) of SRIS-P1-GOV-005.
- **BR-22** Each booking must follow a defined lifecycle, and the status of a ticket and of a PNR must be retrievable. Source: [Section 4.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#42-phase-1-capabilities) of SRIS-P1-ARCH-001.
- **BR-23** Provisionally, the booking lifecycle also covers waitlist handling and cascade, cancellation, and chart preparation. The exact mechanism of waitlist handling and cascade is decided in [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md) — Domain Rules: Waitlist and Cancellation. The exact mechanism of chart preparation is decided in [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md) — Domain Rules: Chart Preparation. Source: [Section 4.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#42-phase-1-capabilities) of SRIS-P1-ARCH-001.

### 7.7 Notification

- **BR-24** After a booking is confirmed, the customer must receive a confirmation by email and by SMS. Source: [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005.
- **BR-25** Message templates and a delivery log must be kept, and a failed delivery must be retried. Source: [Section 4.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#42-phase-1-capabilities) and [Section 6.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#62-service-specifications) of SRIS-P1-ARCH-001.

### 7.8 Surfaces

- **BR-26** A Customer Booking Website must be available to passengers. Source: [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005.
- **BR-27** An Employee Admin Console must be available to railway employees. Source: [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005.
- **BR-28** The two surfaces must be client applications and are not counted among the six microservices. Source: [Section 8.1](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#81-assumptions) of SRIS-P1-ARCH-001.

### 7.9 Deliverables

- **BR-29** The six microservices must be implemented and must run together. Source: [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005 and [Section 6.1](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#61-service-catalog) of SRIS-P1-ARCH-001.
- **BR-30** The locked set of 180 project documents must be complete and approved. Source: [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005.
- **BR-31** One consolidated PDF book containing all 180 documents must be produced. Source: [Section 5.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#51-in-scope) of SRIS-P1-GOV-005.

---

## 8. Business Rules

A business rule is a condition that the business requires to hold whenever the flow runs or the project is delivered. Each rule has an identifier, a statement, and a source. The rules trace to the sources below.

- [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document, for the vision, scope, and success criteria.
- [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification, for the decision criteria and service boundaries.
- [SRIS-P1-GOV-007](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md) — Project Management Plan, for the delivery rules.

### 8.1 Booking Rules

- **BRL-1** A seat must never be sold twice. Source: [Section 2](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#2-vision-statement) of SRIS-P1-GOV-005 and [Section 6.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#62-service-specifications) of SRIS-P1-ARCH-001.
- **BRL-2** Payment status determines whether a booking is confirmed. Source: [Section 7.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#72-consolidations) of SRIS-P1-ARCH-001.
- **BRL-3** A booking uses the fare re-quoted by the master data and pricing authority at booking time, and does not use a price supplied by search. Source: [Section 6.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#62-service-specifications) of SRIS-P1-ARCH-001.
- **BRL-4** Every confirmed booking carries a 10-digit PNR. Source: [Section 2](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#2-vision-statement) and [Section 6.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#62-service-specifications) of SRIS-P1-GOV-005.
- **BRL-5** Sending a notification is asynchronous and must never block or fail a booking. Source: [Section 3.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#32-decision-criteria) and [Section 7.3](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#73-why-not-fewer-than-six) of SRIS-P1-ARCH-001.
- **BRL-6** Payment is simulated only. No real payment is processed, and no live system of Indian Railways, CRIS, or IRCTC is connected. Source: [Section 5.2](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#52-out-of-scope) of SRIS-P1-GOV-005.
- **BRL-7** The configuration of railway data is an employee action, and booking is a customer action. Source: [Section 7.3](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#73-why-not-fewer-than-six) of SRIS-P1-ARCH-001.

### 8.2 Service Ownership Rules

- **BRL-8** Each Phase 1 capability has exactly one owning service. Source: [Section 6.3](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#63-capability-traceability) of SRIS-P1-ARCH-001.
- **BRL-9** Each service owns its data, no service reads another service's data store directly, and services communicate only through APIs or events. Source: [Section 6.5](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#65-supporting-infrastructure) of SRIS-P1-ARCH-001.
- **BRL-10** The six services are the Phase 1 count and not the count for the complete system. Later phases add services for the deferred capabilities. Source: [Section 6.1](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#61-service-catalog) of SRIS-P1-ARCH-001.

### 8.3 Delivery Rules

- **BRL-11** All five deliverables are required. Delivering some of the five does not meet the Phase 1 success criterion. Source: [Section 6.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#61-phase-1-success-criterion) of SRIS-P1-GOV-005.
- **BRL-12** If time runs short, effort is directed in this order: the booking flow, the six microservices, the two surfaces, the documents, and the PDF book. The order does not change the success criterion. Source: [Section 6.3](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#63-priority-order-if-time-runs-short) of SRIS-P1-GOV-005.
- **BRL-13** Work not completed in its scheduled week carries forward to the next week, the final week absorbs the remaining backlog, and nothing is dropped. Source: [Section 2](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md#2-development-methodology) of SRIS-P1-GOV-007.
- **BRL-14** No task is accepted on self-test alone. The Lead Architect re-tests every task and holds the final authority on whether a task is complete. Source: [Section 6](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md#6-testing-approach) of SRIS-P1-GOV-007.

---

## 9. Delivery Requirements

The delivery requirements state what the business needs from the way Phase 1 is delivered. They are taken from [SRIS-P1-GOV-007](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md) — Project Management Plan, which holds the full schedule, roles, and testing approach.

### 9.1 Sprints and Schedule

- **DR-1** Phase 1 work is organised in one-week sprints, eight sprints for the eight weeks of Phase 1, which runs from 01 October 2026 to 30 November 2026. Source: [Section 2](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md#2-development-methodology) of SRIS-P1-GOV-007.
- **DR-2** Work follows the weekly plan in the table below. The plan is a plan and not a contract, as stated in BRL-13. Source: [Section 3](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md#3-schedule-and-work-breakdown) of SRIS-P1-GOV-007.

| Week   | Work                                                                                                                                                                                                                |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 to 2 | Documentation only. Write all UNBLOCK documents, meet with the team, and freeze initial contracts. No development work occurs.                                                                                       |
| 3      | Infrastructure setup on the first day, which blocks database work until complete. S1 IAM Service development follows, with tests at the end of the week. S1 is complete, tested, and documented by the end of the week. |
| 4      | S2 Master Data and Pricing Service: build, test, and integrate with S1. Documentation continues in parallel.                                                                                                          |
| 5      | S3 Reservation Service, Inventory module: seat matrix, availability, and seat lifecycle.                                                                                                                              |
| 6      | S3 Reservation Service, Booking module: booking state machine, PNR, waitlist, chart, cancellation, and payment callback verification. Integration tests with S1 and S2 run across Weeks 5 and 6.                       |
| 7      | S4 Search Aggregator BFF, S5 Mock Payment Gateway, and S6 Notification Service. The Customer Booking Website is completed end to end.                                                                                 |
| 8      | End-to-end booking flow tested across all six services and both surfaces. Documentation polish. PDF generation for all 180 documents. Release branch frozen at v1.0.0.                                                 |

### 9.2 Roles

- **DR-3** The Lead Architect designs contracts, writes all 180 documents, builds frontend and backend where needed, reviews all team output, runs unit, service, and integration tests, and executes all merges. Source: [Section 7](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md#7-roles-and-responsibilities) of SRIS-P1-GOV-007.
- **DR-4** The team members read documents during Weeks 1 and 2 and raise questions, join active development from Week 3 Day 1, and self-test their own work before submission. Source: [Section 7](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md#7-roles-and-responsibilities) of SRIS-P1-GOV-007.
- **DR-5** The supervisor is the evaluator only and is not involved in project decisions. No mentor is assigned for the active project. Source: [Section 7](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md#7-roles-and-responsibilities) of SRIS-P1-GOV-007.

### 9.3 Testing and Reporting

- **DR-6** Testing is enforced across three layers: unit tests written concurrently with the code, service tests run when each service is complete, and integration tests run continuously as new services are added. Source: [Section 6](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md#6-testing-approach) of SRIS-P1-GOV-007.
- **DR-7** Progress is reviewed twice a week, on Thursday and Sunday, against the plan for the week. Source: [Section 8](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md#8-reporting-and-cicd) of SRIS-P1-GOV-007.
- **DR-8** A CI/CD pipeline runs on every push to the repository. It installs dependencies, runs the test suite, and reports the result. Source: [Section 8](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md#8-reporting-and-cicd) of SRIS-P1-GOV-007.

### 9.4 Branching and Versioning

- **DR-9** Work follows a branching model with these branches: `main`, `docs`, `develop` (created in Week 3), `feature/*`, `testing/*`, and `release/*`. Source: [Section 5](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md#5-branching-and-versioning) of SRIS-P1-GOV-007.
- **DR-10** Document versions use the `MAJOR.MINOR` format, and software versions use the `MAJOR.MINOR.PATCH` format. Phase 1 delivers software v1.0.0. Source: [Section 5](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md#5-branching-and-versioning) of SRIS-P1-GOV-007.

---

## 10. Success Criteria

### 10.1 Phase 1 Success Criterion

Phase 1 is successful when all five deliverables listed in [Section 5.3](#53-surfaces-and-deliverables) exist by 30 November 2026. Delivering some of the five does not meet the criterion. The criterion is recorded in [Section 6.1](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#61-phase-1-success-criterion) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document.

### 10.2 Proposed Measurable Criteria

The criteria below are taken from [Section 6.2](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#62-proposed-measurable-criteria) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document and keep its numbering. They are proposed, pending confirmation, and are not final. Any numeric target is marked in the criterion itself.

| ID   | Criterion                                                                                                                                                            | Verification Method                                                    |
| ---- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| SC-1 | All five deliverables exist and are linked from [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map. | Inspect the links in the documentation index                           |
| SC-2 | A single demo run performs the full ten-step booking flow, from employee login to customer PNR retrieval.                                                            | Observe one uninterrupted demo run                                     |
| SC-3 | The booking flow completes without manual data patching.                                                                                                             | Confirm that no data is edited outside the two surfaces during the run |
| SC-4 | Each confirmed booking returns a 10-digit PNR, and retrieving the ticket by that PNR returns the booked ticket.                                                      | Check the PNR format and retrieval in the demo run                     |
| SC-5 | Two simultaneous requests for the last available seat in a class result in exactly one confirmed booking (proposed, pending confirmation).                           | Run a concurrent booking test                                          |
| SC-6 | All six microservices run together within 5.1 GB RAM during the demo run (proposed, pending confirmation).                                                           | Measure peak memory use of the full local environment                  |
| SC-7 | The 180-document register is complete, and every document carries a Version, an Approval row, and a Revision History row.                                            | Inspect every document in the register                                 |
| SC-8 | The consolidated PDF book contains all 180 documents.                                                                                                                | Inspect the contents of the book                                       |

### 10.3 Priority Order If Time Runs Short

If time runs short, effort is directed in the order stated in BRL-12. The order guides the allocation of effort only and does not change the criterion in [Section 10.1](#101-phase-1-success-criterion). The order is recorded in [Section 6.3](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#63-priority-order-if-time-runs-short) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document.

---

## 11. Constraints and Assumptions

### 11.1 Constraints

Constraints BC-1 to BC-7 are recorded in [Section 7](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#7-constraints) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document. Constraint BC-8 is recorded in [Section 2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#2-inputs-and-constraints) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification.

- **BC-1 Timeline:** Phase 1 runs from 01 October 2026 to 30 November 2026, a period of about eight weeks.
- **BC-2 Hardware:** the full local environment must fit within 5.1 GB RAM. This is the operative Phase 1 hardware constraint, and it shaped the decision to use six microservices.
- **BC-3 Budget:** the budget is zero. No paid services or tooling are used.
- **BC-4 Staffing:** research, documentation, architecture, and technology decisions for Phase 1 are carried out by the Lead Architect alone. The four other team members are assigned tasks against the documents that the Lead Architect produces and are not involved in Phase 1 planning.
- **BC-5 Document register:** the register is locked at 180 documents across ten waves, as recorded in [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.
- **BC-6 Independence:** SRIS is an independent academic project and is not affiliated with Indian Railways, CRIS, or IRCTC.
- **BC-7 Technology stack:** this document names no language, database, framework, or tool. The stack is decided in [SRIS-P1-ARCH-008](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md) — Technology Stack ADR and must fit within BC-2 and BC-3.
- **BC-8 Delivery capacity:** the delivery team is a small team of five members, and the delivery period is approximately two months.

### 11.2 Assumptions

Assumptions BA-1 to BA-6 are recorded in [Section 8](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#8-assumptions) of [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document. Assumptions BA-7 and BA-8 are recorded in [Section 8.1](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#81-assumptions) of [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification.

- **BA-1:** the register of 180 documents remains locked for the whole of Phase 1.
- **BA-2:** a technology stack that fits within 5.1 GB RAM and a zero budget can be selected in [SRIS-P1-ARCH-008](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md) — Technology Stack ADR.
- **BA-3:** payment remains simulated through a mock gateway, and email and SMS delivery use free-tier services that require no paid provider.
- **BA-4:** the four other team members are available to take assigned tasks against completed documents during the Phase 1 period.
- **BA-5:** the project supervisor evaluates Phase 1 against the deliverables defined in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document.
- **BA-6:** publicly known railway reservation concepts, such as the 10-digit PNR, travel classes, and quotas, are sufficient as domain reference, and no confidential railway data is needed.
- **BA-7:** the basic profile of a customer or an employee is held with the login identity in Phase 1.
- **BA-8:** the capability list is provisional. Service decisions depend on the capability domains and not on individual capabilities.

---

## 12. Risks and Open Items

### 12.1 Risks

The risks below are recorded in [Section 9](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md#9-risks-to-the-plan) of [SRIS-P1-GOV-007](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md) — Project Management Plan. The full risk register belongs to [SRIS-P1-GOV-009](../wave-0-project-foundation/SRIS-P1-GOV-009_RiskManagementPlan.md) — Risk Management Plan.

| ID   | Risk                                                                                  | Mitigation                                                                            |
| ---- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| RK-1 | Documentation load is heavy across 180 documents                                       | Strict template adherence, and focus on the UNBLOCK documents in the first two weeks   |
| RK-2 | Team members may not perform as expected on assigned tasks                            | The Lead Architect retains the capacity to build frontend and backend components where necessary to prevent blocks |
| RK-3 | Server RAM is limited to 5.1 GB, and running all six services together may exceed it   | Monitor memory footprints during integration testing, and optimise runtime usage      |
| RK-4 | Communication between developers may break down                                       | Twice-weekly reporting checkpoints and formalised API contracts                        |

### 12.2 Open Items

- **OI-1** The final list of capabilities, with its numbering and order, is fixed in [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final). The service decisions depend on the capability domains and not on individual capabilities. Source: [Section 4.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#42-phase-1-capabilities) of SRIS-P1-ARCH-001.
- **OI-2** The numeric targets in SC-5 and SC-6 are proposed and are pending confirmation. Source: [Section 6.2](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md#62-proposed-measurable-criteria) of SRIS-P1-GOV-005.
- **OI-3** Refund processing, payment reconciliation and settlement, and in-app or push notifications are expected to be deferred and are to be confirmed. Source: [Section 4.2](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md#42-phase-1-capabilities) of SRIS-P1-ARCH-001.
- **OI-4** The mechanism that protects a customer's selected seat, and the mechanism that returns money if a seat cannot be allocated after payment, are decided in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing. This document states business-level outcomes only.
- **OI-5** The order of the waitlist, the cascade rules, the promotion rule on cancellation, and any fallback to a pooled or remote waitlist are decided in [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md) — Domain Rules: Waitlist and Cancellation. This document states the business outcome only.

---

## 13. Traceability

The table below traces each business objective to the business requirements, business rules, delivery requirements, and success criteria that support or measure it. Every identifier in [Section 7](#7-business-requirements), [Section 8](#8-business-rules), and [Section 9](#9-delivery-requirements) appears in at least one row.

| Objective | Business Requirements                                                                                              | Business Rules             | Delivery Requirements                        | Success Criteria |
| --------- | ------------------------------------------------------------------------------------------------------------------ | -------------------------- | -------------------------------------------- | ---------------- |
| BO-1      | BR-1, BR-2, BR-5, BR-9, BR-10, BR-11, BR-12, BR-13, BR-15, BR-16, BR-16a, BR-17, BR-18, BR-19, BR-20, BR-21, BR-23, BR-24, BR-25 | BRL-2, BRL-3, BRL-4, BRL-5, BRL-6 | DR-6                                         | SC-2, SC-3       |
| BO-2      | BR-13, BR-14, BR-15, BR-16, BR-16a                                                                                 | BRL-1                      | None                                         | SC-5             |
| BO-3      | BR-20, BR-21, BR-22                                                                                                | BRL-4                      | None                                         | SC-4             |
| BO-4      | BR-2, BR-3, BR-4, BR-5, BR-6, BR-7, BR-8, BR-27                                                                     | BRL-7                      | None                                         | SC-2             |
| BO-5      | BR-28, BR-29                                                                                                        | BRL-8, BRL-9, BRL-10       | DR-2, DR-6, DR-10                            | SC-1, SC-6       |
| BO-6      | BR-26, BR-27, BR-28                                                                                                 | None                       | None                                         | SC-1, SC-2       |
| BO-7      | BR-30, BR-31                                                                                                        | BRL-11                     | None                                         | SC-7, SC-8       |
| BO-8      | BR-30                                                                                                               | BRL-8, BRL-9, BRL-14       | DR-6, DR-8, DR-9                             | SC-7             |
| BO-9      | BR-29                                                                                                               | BRL-11, BRL-12, BRL-13     | DR-1, DR-2, DR-3, DR-4, DR-5, DR-7            | SC-1, SC-6       |

---

## 14. Approval

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

| Seq  | Document ID                                                                                          | Document Name                                | Wave | Pri | Tag     |
| ---- | ---------------------------------------------------------------------------------------------------- | -------------------------------------------- | ---- | --- | ------- |
| 0.0  | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md)  | Documentation Index and Navigation Map       | 0    | P0  | UNBLOCK |
| 0.1  | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)            | Document Template Standard                   | 0    | P0  | UNBLOCK |
| 0.2  | [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)         | Document ID and Category Scheme              | 0    | P1  | UNBLOCK |
| 0.3  | [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md)      | Document Cross-Reference Standard            | 0    | P1  | UNBLOCK |
| 0.4  | [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)       | Project Vision and Scope Document            | 0    | P0  | UNBLOCK |
| 0.6  | [SRIS-P1-GOV-007](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md)               | Project Management Plan                      | 0    | P0  | UNBLOCK |
| 0.8  | [SRIS-P1-GOV-009](../wave-0-project-foundation/SRIS-P1-GOV-009_RiskManagementPlan.md)                  | Risk Management Plan                         | 0    | P1  | FOLLOW  |
| 1.1  | [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md)                                    | Glossary and Domain Dictionary               | 1    | P0  | UNBLOCK |
| 1.3  | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)                                          | Capability Catalog (Final)                   | 1    | P0  | UNBLOCK |
| 1.4  | [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md)                            | Software Requirements Specification (SRS)    | 1    | P0  | UNBLOCK |
| 1.5  | [SRIS-P1-REQ-005](./SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md)                               | Non-Functional Requirements (ISO 25010)      | 1    | P0  | UNBLOCK |
| 1.6  | [SRIS-P1-REQ-006](./SRIS-P1-REQ-006_UserStoriesAndUseCases.md)                                          | User Stories and Use Cases                   | 1    | P0  | UNBLOCK |
| 1.7  | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)                                      | Domain Rules: Fare Calculation               | 1    | P1  | FOLLOW  |
| 1.8  | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)                                            | Domain Rules: Ticketing                      | 1    | P1  | FOLLOW  |
| 1.9  | [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)                              | Domain Rules: Waitlist and Cancellation      | 1    | P1  | FOLLOW  |
| 1.10 | [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md)                                     | Domain Rules: Chart Preparation              | 1    | P1  | FOLLOW  |
| 1.11 | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)                               | Domain Rules: Seat Matrix and Inventory      | 1    | P1  | FOLLOW  |
| 2.1  | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)              | Microservices Identification                 | 2    | P0  | UNBLOCK |
| 2.8  | [SRIS-P1-ARCH-008](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md)                       | Technology Stack ADR                         | 2    | P0  | UNBLOCK |
| 3.18 | [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md)   | Idempotency and Retry Policy Specification   | 3    | P0  | UNBLOCK |

### B.2 Documents That Reference This Document

| Seq | Document ID                                                                                 | Document Name                          | Why It References                                                                  |
| --- | ------------------------------------------------------------------------------------------- | -------------------------------------- | ---------------------------------------------------------------------------------- |
| 0.0 | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) | Documentation Index and Navigation Map | Lists this document in the register and in the reading paths                       |
| 0.4 | [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)      | Project Vision and Scope Document      | Lists this document as unblocked by its approval                                   |
| 0.6 | [SRIS-P1-GOV-007](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md)              | Project Management Plan                | Lists this document as a Hard upstream document                                    |
| 1.1 | [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md)                           | Glossary and Domain Dictionary         | Names this document as the owner of the term Booking                               |
| 2.1 | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)             | Microservices Identification           | Lists this document as a Hard upstream document                                    |

### B.3 Documents This Document Depends On (Upstream)

| Seq | Document ID                                                                                 | Document Name                          | Dependency Type |
| --- | ------------------------------------------------------------------------------------------- | -------------------------------------- | --------------- |
| 0.0 | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) | Documentation Index and Navigation Map | Soft            |
| 0.1 | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)           | Document Template Standard             | Hard            |
| 0.2 | [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)        | Document ID and Category Scheme        | Hard            |
| 0.3 | [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md)     | Document Cross-Reference Standard      | Hard            |
| 0.4 | [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)      | Project Vision and Scope Document      | Hard            |
| 0.6 | [SRIS-P1-GOV-007](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md)              | Project Management Plan                | Soft            |
| 1.1 | [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md)                           | Glossary and Domain Dictionary         | Hard            |
| 2.1 | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)             | Microservices Identification           | Soft            |

### B.4 Documents This Document Unblocks (Downstream)

| Seq | Document ID                                                                       | Document Name                                | Blocked Until |
| --- | --------------------------------------------------------------------------------- | -------------------------------------------- | ------------- |
| 1.3 | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)                       | Capability Catalog (Final)                   | This approved |
| 1.4 | [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md)         | Software Requirements Specification (SRS)    | This approved |
| 1.6 | [SRIS-P1-REQ-006](./SRIS-P1-REQ-006_UserStoriesAndUseCases.md)                       | User Stories and Use Cases                   | This approved |
| 2.1 | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) | Microservices Identification              | This approved |

### B.5 Master Documentation Index

The complete list of Phase 1 documents is in [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

### B.6 External Reference Documents

None.

### B.7 Document Conventions

The conventions for Priority and Tag values are defined in [Section 9](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md#9-vocabulary-standards) of [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.

---

**End of Document**