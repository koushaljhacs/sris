<div align="center">

![Wave](https://img.shields.io/badge/Wave-1-0550AE?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-REQ-6e7781?style=for-the-badge)

</div>

# User Stories and Use Cases

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** 1.0 | **Date:** 2026-10-15 | **Document ID:** SRIS-P1-REQ-006

| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| Title              | User Stories and Use Cases                                        |
| Software           | SRIS                                                              |
| Software Full Form | Sarathi Railway Information System                                |
| Team Codename      | Project Sarathi                                                   |
| Document ID        | SRIS-P1-REQ-006                                                   |
| Task               | Record the journeys of Phase 1 as user stories and use cases      |
| Document Type      | Requirements Document                                             |
| Milestone          | Phase 1 Foundation                                                |
| Classification     | Internal                                                          |
| Version            | 1.0                                                               |
| Date               | 2026-10-15                                                        |
| Author             | Koushal Jha, Lead Architect                                       |
| Approved By        | Koushal Jha, Lead Architect                                       |
| Approval Date      | 2026-10-15                                                        |
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
2. [Actors and Personas](#2-actors-and-personas)
   - [2.1 The Four Parent Role Types](#21-the-four-parent-role-types)
   - [2.2 Customer Roles](#22-customer-roles)
   - [2.3 Employee Roles](#23-employee-roles)
   - [2.4 Administrator Roles](#24-administrator-roles)
   - [2.5 System Roles](#25-system-roles)
   - [2.6 Role Assignment in Phase 1](#26-role-assignment-in-phase-1)
3. [User Story Format](#3-user-story-format)
   - [3.1 The Three Sentence Forms](#31-the-three-sentence-forms)
   - [3.2 INVEST Criteria](#32-invest-criteria)
   - [3.3 Acceptance Criteria](#33-acceptance-criteria)
   - [3.4 Story Metadata Fields](#34-story-metadata-fields)
   - [3.5 What a Story Does Not Contain](#35-what-a-story-does-not-contain)
4. [Use Case Format](#4-use-case-format)
   - [4.1 The Structure of a Use Case](#41-the-structure-of-a-use-case)
   - [4.2 Main Flow and Alternate Flows](#42-main-flow-and-alternate-flows)
   - [4.3 Use Case Metadata Fields](#43-use-case-metadata-fields)
   - [4.4 What a Use Case Does Not Contain](#44-what-a-use-case-does-not-contain)
5. [Use Cases](#5-use-cases)
   - [5.1 Customer Use Cases](#51-customer-use-cases)
   - [5.2 Employee Use Cases](#52-employee-use-cases)
   - [5.3 Administrator Use Cases](#53-administrator-use-cases)
   - [5.4 System Use Cases](#54-system-use-cases)
6. [Customer Stories](#6-customer-stories)
   - [6.1 Authentication and Account](#61-authentication-and-account)
   - [6.2 Search and Selection](#62-search-and-selection)
   - [6.3 Booking and Payment](#63-booking-and-payment)
   - [6.4 Ticket Retrieval](#64-ticket-retrieval)
   - [6.5 Cancellation](#65-cancellation)
7. [Employee Stories](#7-employee-stories)
   - [7.1 Master Data Manager Stories (ER-02)](#71-master-data-manager-stories-er-02)
   - [7.2 Service Manager Stories (ER-03)](#72-service-manager-stories-er-03)
   - [7.3 Pricing Manager Stories (ER-05)](#73-pricing-manager-stories-er-05)
   - [7.4 Operations Manager Stories (ER-06)](#74-operations-manager-stories-er-06)
   - [7.5 Super Admin Stories (AD-01)](#75-super-admin-stories-ad-01)
8. [System Stories](#8-system-stories)
   - [8.1 Seat Matrix Generation](#81-seat-matrix-generation)
   - [8.2 Waitlist Cascade](#82-waitlist-cascade)
   - [8.3 Notification Dispatch](#83-notification-dispatch)
9. [Cross-References to Other Documents](#9-cross-references-to-other-documents)
   - [9.1 How Stories Link to the UI Documents](#91-how-stories-link-to-the-ui-documents)
   - [9.2 How Use Cases Link to the API Documents](#92-how-use-cases-link-to-the-api-documents)
   - [9.3 How Stories and Use Cases Link to the Test Documents](#93-how-stories-and-use-cases-link-to-the-test-documents)
   - [9.4 How the Reference Dataset Is Used](#94-how-the-reference-dataset-is-used)
   - [9.5 What This Document Does Not Contain](#95-what-this-document-does-not-contain)
10. [Traceability](#10-traceability)
   - [10.1 Use Case Summary](#101-use-case-summary)
   - [10.2 Capability Coverage](#102-capability-coverage)
   - [10.3 Coverage Notes](#103-coverage-notes)
   - [10.4 Story-to-Capability Index](#104-story-to-capability-index)
   - [10.5 Role-to-Document Index](#105-role-to-document-index)
11. [Approval](#11-approval)

- [Revision History](#revision-history)
- [Appendix A: Not Applicable](#appendix-a-not-applicable)
- [Appendix B: Related Documents](#appendix-b-related-documents)

---

## 1. Introduction

### 1.1 Purpose

This document records the user journeys of Phase 1 of SRIS (Sarathi Railway Information System) as user stories and use cases. It states, for each actor, what they want to achieve and in what order they move through the system. It provides the source material that the Wave 3 UI documents draw on for screen inventory, and that the Wave 4 test documents draw on for acceptance criteria.

This document does not define the mechanism by which the system fulfils a journey. The booking mechanism, the fare rules, the waitlist cascade, and the chart resolution are defined in [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) to [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md). The screens and wireframes belong to [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md) to [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md). The API contracts belong to [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md). Every such topic is cited to its owner and not repeated here.

### 1.2 Scope

**In scope**

- The role hierarchy of Phase 1: four parent role types and fourteen child roles.
- The user story format and its acceptance criteria.
- The use case format, with main flows and alternate flows.
- The complete set of use cases for Phase 1.
- The complete set of user stories, grouped by actor.
- The traceability of every story and use case to its capability and software requirement.
- The role-specific reference dataset that each employee role reads from.

**Out of scope**

- The business requirements, which are defined in [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD).
- The capabilities and their identifiers, which are defined in [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final).
- The software requirements, which are defined in [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software Requirements Specification (SRS).
- The non-functional requirements, which are defined in [SRIS-P1-REQ-005](./SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md) — Non-Functional Requirements (ISO 25010).
- The domain rules for fare, ticketing, waitlist and cancellation, chart preparation, and seat matrix and inventory, which are defined in [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) to [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md).
- The full cross-wave Requirement Traceability Matrix, which belongs to [SRIS-P1-REQ-012](./SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md) — Requirement Traceability Matrix (RTM).
- The service catalogue and the service boundaries, which are defined in [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification.
- The authentication, authorisation, RBAC, and token design, which are defined in [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md), [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md), and [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md).
- The UI screens, wireframes, and navigation, which are defined in [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md) to [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md).
- The API contracts and event schemas, which are defined in [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md) and [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md).
- The test cases, which are defined in [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md) — Test Cases (Functional).
- The dataset that the employee reads from, which belongs to [SRIS-P1-DATA-012](../wave-3-detailed-design/SRIS-P1-DATA-012_SeedDataAndReferenceDataSpecification.md) — Seed Data and Reference Data Specification.

### 1.3 Audience

- **Lead Architect:** maintains this document and approves every story and use case.
- **Frontend developers:** build the two surfaces against the journeys recorded here, with the UI documents as the second-level reference.
- **Backend developers:** understand which journey each service call serves.
- **UI designer:** draws the screen inventory from the journeys recorded here.
- **Tester (QA):** derives the functional test cases from the acceptance criteria of each story and the alternate flows of each use case.
- **Project supervisor and evaluator:** uses this document to confirm that every capability is exercised by a human or system journey.
- **Technical reviewers:** engineers or interviewers who open the repository and need the user-facing journeys of Phase 1.

### 1.4 Terminology and Conventions

Every term in this document has the meaning recorded in [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary. The terms below carry the most weight in this document and are used with the meanings defined there.

| Term                | Meaning                                                                                                              |
| ------------------- | -------------------------------------------------------------------------------------------------------------------- |
| Actor               | A person or system that interacts with the SRIS software to achieve a goal.                                          |
| Parent role         | One of the four top-level role types: Customer, Employee, Administrator, System.                                     |
| Child role          | A specific role inside a parent role, such as Registered Customer or Pricing Manager.                                |
| User story          | A short statement of what an actor wants to achieve, in the actor's own voice.                                       |
| Use case            | A structured journey that describes an actor's interaction with the system from a starting condition to a final outcome. |
| Acceptance criteria | The observable conditions that must be true for a user story to be considered complete.                              |
| Main flow           | The happy-path sequence of steps in a use case, with no errors or exceptions.                                        |
| Alternate flow      | A deviation from the main flow, caused by an error, an exception, or an alternative user choice.                     |
| Reference dataset   | The soft-copy source document that an employee reads from when entering master data.                                 |

Two identifier prefixes are local to this document.

| Prefix | Meaning                |
| ------ | ---------------------- |
| US     | User story             |
| UC     | Use case               |

Role identifiers are also local to this document. They are recorded in [Section 2](#2-actors-and-personas) and are cited throughout the register.

| Prefix | Meaning       |
| ------ | ------------- |
| CU     | Customer role |
| ER     | Employee role |
| AD     | Administrator role |
| SY     | System role   |

This document follows the standards below.

- [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard, for structure, header, and style.
- [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md) — Document ID and Category Scheme, for the Document ID.
- [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md) — Document Cross-Reference Standard, for citations and links.
- **ISO/IEC/IEEE 29148:2018** — Systems and software engineering — Life cycle processes — Requirements engineering. Referenced for the requirement-format rules.
- **Mike Cohn, "User Stories Applied"** — Referenced for the canonical three-part user story form and the INVEST criteria.
- **Bill Wake, "INVEST in Good Stories, and SMART Tasks"** — Referenced for the INVEST acronym.
- **Ivar Jacobson, "Use-Case 2.0"** — Referenced for the use case structure and the slicing pattern.

---

## 2. Actors and Personas

The actors of Phase 1 are organised into four parent role types. Each parent role type contains one or more child roles. A child role is the unit that the register's RBAC matrix uses, that the UI documents design a dashboard for, and that the user stories are grouped under.

The role hierarchy is stable across Phase 1 and Phase 2. Additional child roles may be added in later phases without changing the four parent role types.

### 2.1 The Four Parent Role Types

| Parent Role Type  | Nature                    | Logs In? | Phase 1 Status |
| ----------------- | ------------------------- | -------- | -------------- |
| Customer          | External human user       | Partly   | Active         |
| Employee          | Internal human operator   | Yes      | Active         |
| Administrator     | Internal human manager    | Yes      | Active         |
| System            | Autonomous process        | No       | Active         |

The four parent role types exist because the actors of a reservation system fall into four categories: those who buy, those who configure and operate, those who manage the system itself, and the software's own autonomous behaviour. No fifth category applies to Phase 1.

### 2.2 Customer Roles

The Customer parent role covers the human users who interact with the Customer Booking Website.

| Role ID | Role Name            | Login | What the role can do                                                                                          |
| ------- | -------------------- | ----- | -------------------------------------------------------------------------------------------------------------- |
| CU-01   | Visitor              | No    | Search trains, view schedules, check the status of a PNR with the PNR and a passenger surname, view public pages. Cannot book. |
| CU-02   | Registered Customer  | Yes   | Everything a Visitor can do, plus: book tickets, cancel bookings, view own booking history, manage own profile, change password, request account deletion. |
| CU-03   | Passenger            | No    | A domain entity. The traveller on whose behalf the booking is made. Not a login role. Entered by a Registered Customer. |

**Notes on CU-03.** A Passenger is not a system user. They do not log in. Their details are entered by a Registered Customer when booking. Passenger is defined as a domain entity in [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary. It appears here because a use case may name a Passenger as the subject of an interaction that the Registered Customer initiates.

### 2.3 Employee Roles

The Employee parent role covers the internal human operators who configure and run the system through the Employee Admin Console. Every employee role is scoped by domain. Each has a role-specific dashboard and can perform Create, Read, Update, and Deactivate operations only on the entities that role owns.

| Role ID | Role Name             | Owns                                                                                              | Dashboard Shows                                                                                                                    |
| ------- | --------------------- | ------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| ER-01   | Operations Head       | Central command. No direct CRUD. Approves all master-data changes. Views analytics. Manages the exception queue. | Everything: master-data state, operational metrics, audit log, all pending approvals, all exceptions, all analytics views.             |
| ER-02   | Master Data Manager   | Stations, Routes, Route Stops, Cumulative Distances                                              | Station list, route list with distances, distance matrix. CRUD on stations and routes only.                                          |
| ER-03   | Service Manager       | Trains, Schedules, Running Days                                                                  | Train list, schedule list, calendar view of running days. CRUD on trains and schedules only.                                        |
| ER-04   | Composition Manager   | Classes, Quotas, Coach Composition, Berth Layout                                                 | Class list, quota list, coach blueprint editor, berth layout preview. CRUD on classes, quotas, and coach composition.                 |
| ER-05   | Pricing Manager       | Fare Rules, Dynamic Pricing Rules, Concession Rules                                              | Fare table, distance slab editor, dynamic pricing curve editor, concession matrix. CRUD on fare entities.                            |
| ER-06   | Operations Manager    | Chart Preparation, Cancellation Exceptions, No-Show Handling                                     | Upcoming departures, chart queue, exception log, cancellation queue. Trigger and review actions only.                                |

**Role scoping is enforced.** ER-02 does not see fare rules. ER-05 does not see coach composition. ER-01 sees everything but edits nothing directly. This is the maker-checker separation that enterprise practice requires for master data.

**Reference dataset per role.** Each employee role reads from a specific reference document when entering data. The employee does not invent the data.

| Role  | Reference Dataset the Employee Reads From                                       |
| ----- | -------------------------------------------------------------------------------- |
| ER-02 | Station list with codes and names; route list with ordered stops and distances    |
| ER-03 | Train list with numbers, names, and types; timetable and running-days policy      |
| ER-04 | Coach composition specification; class and quota policy                            |
| ER-05 | Fare policy; distance slab table; concession policy                                |
| ER-06 | Departure schedule; exception handling policy                                     |

The reference dataset itself belongs to [SRIS-P1-DATA-012](../wave-3-detailed-design/SRIS-P1-DATA-012_SeedDataAndReferenceDataSpecification.md) — Seed Data and Reference Data Specification and is stored in the repository. It is created by the project. It is not obtained from any external railway system. SRIS does not reproduce the data, the systems, or the operations of any external organisation.

**Dependency order of employee actions.** The employee roles are ordered by the dependency chain of the master data. A role cannot proceed before the roles upstream of it have completed their work.

Stations (ER-02) → Routes (ER-02) → Trains (ER-03) → Schedules (ER-03) → Classes and Quotas (ER-04) → Coach Composition (ER-04) → Fare Rules (ER-05) → Dynamic Pricing and Concessions (ER-05) → Chart Preparation (ER-06).

The console enforces this order. An employee cannot create a schedule before the route and the train exist. An employee cannot configure a fare rule before the class and the distance data exist.

### 2.4 Administrator Roles

The Administrator parent role covers the internal human users who manage the system's identities, roles, and access. The Administrator is distinct from the Operations Head. The Operations Head runs the railway operation. The Administrator keeps the console secure and correctly staffed.

| Role ID | Role Name       | What the role can do                                                                                                                            |
| ------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| AD-01   | Super Admin     | Create employee accounts, assign employee roles (ER-01 to ER-06), deactivate employee accounts, reset credentials, view the audit trail of role changes. Cannot edit master data. |
| AD-02   | Audit Officer   | Read-only access to the full audit log across every role. Cannot create, update, or deactivate anything.                                          |

**Separation of powers.** The Administrator manages identities and permissions. The Operations Head manages operations. Neither has the other's privileges. This is the separation that enterprise practice requires. A Super Admin cannot edit railway data; an Operations Head cannot create new users or assign roles.

### 2.5 System Roles

The System parent role covers the autonomous processes that act on the register's behalf. The System actor is not a person. It does not log in. It appears in user stories under the "When [trigger], the system must…" form. It runs inside the microservices themselves.

| Role ID | Role Name         | What the role does                                                                                                                                |
| ------- | ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| SY-01   | Scheduled Job     | Time-triggered processes: chart preparation at the configured window, seat matrix generation for upcoming journeys, cleanup of expired sessions.    |
| SY-02   | Event Consumer    | Event-triggered processes: waitlist cascade on cancellation, notification dispatch on booking confirmation, audit entries on master-data change.    |
| SY-03   | Batch Process     | Periodic processes: retained-data cleanup, delivery-log compaction.                                                                                |

**Not a login user.** The System actor has no credentials. It is treated as an actor in the register so that its actions are traceable, but it is not a user in the access-control sense.

### 2.6 Role Assignment in Phase 1

All fourteen roles are defined and active in Phase 1. In the Phase 1 demo environment, the Lead Architect holds every human role. The system is designed for the full role set so that Phase 2 can add real staff without an architectural change.

| Role Category                     | Phase 1                                                                                       |
| --------------------------------- | --------------------------------------------------------------------------------------------- |
| Customer (CU-01, CU-02, CU-03)    | Exercised in the demo by the Lead Architect and by test accounts                              |
| Employee (ER-01 to ER-06)          | Held by the Lead Architect across all six roles                                               |
| Administrator (AD-01, AD-02)      | AD-01 held by the Lead Architect; AD-02 optionally held by the supervisor or evaluator         |
| System (SY-01, SY-02, SY-03)      | Runs inside the services. No human holder.                                                     |

The RBAC matrix in [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md) — RBAC Matrix will define the permissions that each role carries. This document defines the roles themselves; the RBAC matrix defines what each role may do.

---

## 3. User Story Format

A user story is a short statement of what an actor wants to achieve. The form depends on which parent role the actor belongs to.

**Customer and Employee forms.** For human actors who initiate an action with intent, the story uses the canonical three-part form.

As a <role name>, I want to <goal> so that <benefit>.

Two examples:

    US-014: As a Registered Customer, I want to search for trains by
    origin, destination, and date so that I can see the services
    that match my journey.

    US-042: As a Master Data Manager, I want to create a station with a
    unique code and name so that it can be referenced by routes
    and schedules.

**System form.** For autonomous processes that react to a condition, the story uses the trigger-and-response form. It is not natural to write "As a System, I want to…" because the System does not want. The correct form is:

When <trigger>, the system must <action> so that <outcome>.

One example:

    US-071: When the chart preparation window opens for a journey, the
    system must resolve the remaining quota pools, RAC allocations,
    and waitlist positions so that the final reservation manifest
    is produced before departure.

**All three forms are user stories.** They share the same numbering scheme (US-NNN), the same metadata fields, and the same traceability pattern. Only the sentence form differs, because the actor differs.

### 3.2 INVEST Criteria

Every user story in this document satisfies the INVEST criteria defined by Bill Wake. The criteria are applied as follows.

| Criterion       | What it means in SRIS                                                                                                                            |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Independent** | A story can be built, tested, and delivered without requiring the simultaneous completion of another story. Where two stories share a capability, each still has its own observable acceptance criteria. |
| **Negotiable**  | A story states what the actor wants and why, but does not dictate how it is delivered. Screen layouts, API payloads, and caching strategies are decided in later documents. |
| **Valuable**    | Every story delivers observable value to the actor or to the business. Technical tasks that have no actor-facing or system-facing value are not stories; they are tasks. |
| **Estimable**   | A story is clear enough that its relative size can be estimated. Where a story is not estimable, it is split.                                     |
| **Small**       | A story fits within one sprint. In SRIS, the sprint is one week. Stories that do not fit are split into thinner stories or become a use case with its slices. |
| **Testable**    | A story carries acceptance criteria that make it verifiable by observation. A story without acceptance criteria is not complete.                 |

### 3.3 Acceptance Criteria

Every user story carries acceptance criteria. The acceptance criteria are the observable conditions that must be true for the story to be considered complete.

Rules for acceptance criteria in SRIS:

- A story carries between three and seven acceptance criteria. A story that needs more than seven is too large and is split.
- Each criterion is written in the `Given / When / Then` form.
- Each criterion is observable from outside the system.
- Each criterion is testable. No criterion uses vague words such as "fast" or "easy".
- The criteria cover both the success case and the failure case where the story can fail.

Example for US-014:

    Given a Visitor or Registered Customer is on the search page,
    When the customer enters a valid origin, destination, and date
    and submits the search,
    Then the system returns a list of matching trains within the search
    latency budget defined in SRIS-P1-REQ-005.

    Given the customer enters an origin and destination that do not exist,
    When the customer submits the search,
    Then the system returns a not-found response and displays a message
    instructing the customer to select a valid station.

    Given the customer enters a date in the past,
    When the customer submits the search,
    Then the system returns a validation response and does not execute the
    search.


The full acceptance criteria for every story live in the story entry in Sections 6 to 8.

### 3.4 Story Metadata Fields

Every user story carries the following fields.

| Field                | Value                                                                                                    |
| -------------------- | -------------------------------------------------------------------------------------------------------- |
| **US-NNN**           | A stable identifier. Never reused.                                                                        |
| **Story title**      | A short name for the story.                                                                               |
| **Actor**            | The role ID from Section 2 that the story belongs to.                                                    |
| **Story body**       | The story statement in one of the three forms.                                                            |
| **Acceptance criteria** | The Given/When/Then conditions.                                                                       |
| **Use Case**         | The UC-NNN identifier of the parent use case, if the story belongs to one. If the story does not belong to a use case, this field states "None". |
| **Capability**       | The CAP-NNN identifier from [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final). |
| **Software Requirement** | The SR-NNN identifier from [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software Requirements Specification (SRS). |
| **Non-Functional Requirement** | The NFR-NNN identifier from [SRIS-P1-REQ-005](./SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md) — Non-Functional Requirements (ISO 25010), where one applies. |
| **UI Owner**         | The UI document that will design the screens for this story. Planned until Wave 3.                       |
| **Test Owner**       | The test document that will verify this story.                                                            |

### 3.5 What a Story Does Not Contain

A user story does not contain:

- Screen layouts, wireframe descriptions, or UI field specifications. These belong to [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md) to [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md).
- API payloads, endpoints, or HTTP methods. These belong to [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md).
- Database tables, columns, or indexes. These belong to [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md).
- Algorithms or calculation rules. These belong to [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) to [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md).
- Test scripts or test data. These belong to [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md).
- Implementation mechanics such as caching strategies, concurrency controls, or messaging patterns. These belong to Wave 2 and Wave 3 documents.

A story states what the actor wants and why. The how belongs elsewhere.

---

## 4. Use Case Format

### 4.1 The Structure of a Use Case

A use case is a structured journey that describes an actor's interaction with the system from a starting condition to a final outcome. It is longer and more rigorous than a user story. It captures the entire path, including the failure paths, in one place.

Every use case in this document has the following fields.

| Field              | Purpose                                                                                                                   |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------- |
| **UC-NNN**         | A stable identifier. Never reused.                                                                                         |
| **Use case title** | A short name that describes the goal.                                                                                      |
| **Primary actor**  | The role ID from Section 2 that initiates the use case.                                                                    |
| **Secondary actors** | Any additional role IDs that participate.                                                                                |
| **Goal**           | What the primary actor is trying to achieve.                                                                               |
| **Preconditions**  | The conditions that must be true before the use case begins.                                                              |
| **Trigger**        | The event that starts the use case.                                                                                        |
| **Main flow**      | The numbered sequence of steps when nothing goes wrong.                                                                    |
| **Alternate flows** | The deviations from the main flow, each numbered and named.                                                              |
| **Postconditions** | What is guaranteed to be true after the use case completes, on success and on failure.                                    |
| **Capability**     | The CAP-NNN identifiers of the capabilities the use case exercises.                                                        |
| **Software Requirement** | The SR-NNN identifiers of the software requirements the use case exercises.                                          |
| **Child stories**  | The US-NNN identifiers of the user stories that decompose this use case.                                                   |

### 4.2 Main Flow and Alternate Flows

**Main flow.** The happy-path sequence of steps. The main flow assumes that all inputs are valid, all downstream dependencies are available, and the actor's goal is achieved without error. In SRIS, the main flow of a use case contains between three and fifteen steps. A use case with more than fifteen steps is split into two use cases.

**Alternate flows.** Every deviation from the main flow. Each alternate flow is numbered (A1, A2, A3, …), named, and described. An alternate flow starts from a specific step of the main flow and describes what the system must do when that step cannot complete on its success path.

Every alternate flow describes observable behaviour. It states what the system does, in what order, and with what result. It does not describe the internal mechanism of the response.

Every alternate flow cites the software requirement that defines its behaviour. Where an alternate flow exercises a domain rule, it cites the domain rule document rather than restating the rule.

### 4.3 Use Case Metadata Fields

The metadata fields are recorded in the table of Section 4.1. Every use case in this document carries all of them.

### 4.4 What a Use Case Does Not Contain

A use case does not contain:

- Screen layouts or wireframe descriptions. These belong to the UI documents.
- API payloads or endpoints. These belong to the API documents.
- Database schemas. These belong to the DATA documents.
- Algorithms. These belong to the domain rule documents.
- The exact error message text. This belongs to [SRIS-P1-API-006](../wave-3-detailed-design/SRIS-P1-API-006_APIErrorCodeCatalog.md) — API Error Code Catalog and [SRIS-P1-UI-008](../wave-3-detailed-design/SRIS-P1-UI-008_UIErrorAndNotificationDisplayRules.md) — UI Error and Notification Display Rules.
- Any mechanism whose specification belongs to another document. The use case cites the owner and moves on.

A use case describes an actor's journey. It does not design the system that serves the journey.

---

## 5. Use Cases

This section records the use cases of Phase 1. A use case describes an actor's journey from a starting condition to a final outcome. The structure and metadata fields are defined in [Section 4](#4-use-case-format).

The use cases are grouped by the parent role of their primary actor: customer, employee, administrator, or system. Each use case carries the metadata fields listed in [Section 4.1](#41-the-structure-of-a-use-case). The child user stories that decompose each use case are listed in Sections 6 to 8.

---

### 5.1 Customer Use Cases

---

**UC-001: Register a Customer Account**

**Primary actor:** CU-01 Visitor
**Secondary actors:** SY-02 Event Consumer (email verification)
**Goal:** To create a customer account so that the visitor can book tickets.

**Preconditions:** The visitor is not already registered with the same email address.

**Trigger:** The visitor selects Register on the Customer Booking Website.

**Main flow:**

1. The visitor provides an email address, a password, and the required profile fields.
2. The system validates the email address against the format rule and the uniqueness rule.
3. The system validates the password against the policy in [SRIS-P1-SEC-009](../wave-3-detailed-design/SRIS-P1-SEC-009_PasswordAndCredentialPolicy.md) — Password and Credential Policy.
4. The system creates a customer account in the pending state.
5. The system dispatches a verification email to the address.
6. The system returns a confirmation response to the visitor.

**Alternate flows:**

- **A1 — Email already registered.** At step 2, if the email address already exists, the system returns a conflict response and does not create an account.
- **A2 — Password does not meet policy.** At step 3, the system returns a validation response naming the failing rule and does not create an account.
- **A3 — Verification email dispatch fails.** At step 5, if the notification channel does not respond, the account is created and the email is queued for retry. The visitor is told the account exists and the email is delayed.

**Postconditions:**

- On success: a customer account exists in the pending state.
- On failure: no account is created.

**Capability:** CAP-001
**Software Requirement:** SR-001
**Child stories:** US-001

---

**UC-002: Book a Train Ticket**

**Primary actor:** CU-02 Registered Customer
**Secondary actors:** SY-02 Event Consumer (notification dispatch)
**Goal:** To book a seat on a scheduled train and receive a confirmed ticket with a PNR.

**Preconditions:**
- The customer is registered and logged in.
- The employee has configured the station, route, train, and schedule for the journey.
- The customer has not exceeded the booking limit defined in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing.

**Trigger:** The customer selects Book Ticket on the customer home screen.

**Main flow:**

1. The system presents the train search form.
2. The customer enters origin, destination, journey date, class, and quota.
3. The customer submits the search.
4. The system validates the search parameters and returns the matching trains.
5. The system displays each matching train with its schedule, class-level availability, and fare quote.
6. The customer selects a train, a class, and a quota.
7. The system presents the passenger entry form.
8. The customer enters passenger details and confirms.
9. The system presents the review page with all details and the authoritative fare re-quote.
10. The customer selects a payment method and submits payment.
11. The system processes the payment through the mock payment gateway.
12. On payment success, the system protects a seat, allocates it to the booking, and generates a 10-digit PNR.
13. The system displays the confirmed ticket.
14. The system dispatches confirmation by email and SMS.

**Alternate flows:**

- **A1 — No trains match the search.** At step 4, if no trains match, the system displays an empty state and suggests adjusting the search criteria.
- **A2 — Selected class has no availability.** At step 6, if the class has no confirmed seats, the system offers the customer a place on the waitlist or an alternate class.
- **A3 — Passenger details fail validation.** At step 8, if a passenger field fails validation, the system returns a validation response and does not proceed.
- **A4 — The fare re-quote differs from the fare quote.** At step 9, if the re-quote is higher, the system presents both amounts and asks the customer to confirm the new amount before payment.
- **A5 — Payment fails.** At step 11, if the payment does not succeed, the system returns the customer to the payment step with the failure reason and preserves the booking in its intermediate state.
- **A6 — No seat can be allocated after payment.** At step 12, if payment succeeds but no seat is available, the system places the customer on the appropriate waitlist queue. If the waitlist queues are also full, the system initiates a refund and returns a failure response.
- **A7 — The customer abandons before payment.** If the customer leaves the flow before step 10, the booking is not created and no seat is committed.

**Postconditions:**

- On success: a confirmed booking exists with a PNR, and a seat is allocated.
- On waitlist: a waitlisted booking exists with a PNR, and no seat is allocated.
- On failure: no booking exists, and any payment is reversed.

**Capability:** CAP-014, CAP-017, CAP-018, CAP-019, CAP-020, CAP-021, CAP-025, CAP-027, CAP-028
**Software Requirement:** SR-059, SR-060, SR-061, SR-062, SR-063, SR-064, SR-065, SR-080, SR-081, SR-082, SR-083, SR-086, SR-087, SR-088, SR-089, SR-090, SR-091, SR-092, SR-093
**Child stories:** US-005 to US-024

---

**UC-003: Retrieve a Ticket by PNR**

**Primary actor:** CU-02 Registered Customer
**Secondary actors:** None
**Goal:** To retrieve a previously booked ticket using its PNR.

**Preconditions:** A booking exists with the stated PNR and belongs to the requesting customer.

**Trigger:** The customer enters a PNR on the ticket retrieval page.

**Main flow:**

1. The customer submits a PNR.
2. The system validates the PNR format.
3. The system locates the booking and confirms the customer's ownership.
4. The system returns the passenger list, journey details, reservation status, and coach and berth assignment.
5. The system displays the ticket.

**Alternate flows:**

- **A1 — PNR format is invalid.** At step 2, the system returns a validation response.
- **A2 — PNR not found.** At step 3, the system returns a not-found response.
- **A3 — PNR belongs to another customer.** At step 3, the system returns a forbidden response that does not reveal whether the PNR exists.

**Postconditions:** On success, the ticket is displayed. No state changes in any case.

**Capability:** CAP-024
**Software Requirement:** SR-077
**Child stories:** US-025

---

**UC-004: Cancel a Booking**

**Primary actor:** CU-02 Registered Customer
**Secondary actors:** SY-02 Event Consumer (waitlist cascade and notification)
**Goal:** To cancel a confirmed booking and receive the applicable refund.

**Preconditions:**
- The customer owns the booking.
- The journey has not departed.
- The booking is in a state that permits cancellation, per [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing.

**Trigger:** The customer selects Cancel on the booking.

**Main flow:**

1. The system displays the cancellation summary, including the refund amount from the fare rules.
2. The customer confirms cancellation.
3. The system terminates the booking, releases the seat, and triggers the waitlist cascade.
4. The system records the audit entry.
5. The system initiates the refund through the mock payment gateway.
6. The system dispatches a cancellation confirmation to the customer by email and SMS.

**Alternate flows:**

- **A1 — The customer does not own the booking.** At step 1, the system returns a forbidden response.
- **A2 — The journey has departed.** At step 1, the system returns a not-allowed response and does not display the cancellation option.
- **A3 — Refund acknowledgment fails.** At step 5, if the mock gateway does not acknowledge the refund, the system queues it for retry and returns a refund-pending response.
- **A4 — Waitlist cascade fails.** At step 3, if the cascade cannot complete, the cancellation stands and the cascade is retried. On continued failure, the Lead Architect is notified.

**Postconditions:**
- On success: the booking is cancelled, the seat is released, and the refund is initiated.
- On failure: the booking remains unchanged.

**Capability:** CAP-014, CAP-018, CAP-021, CAP-023, CAP-025
**Software Requirement:** SR-057, SR-068, SR-073, SR-074, SR-075, SR-076, SR-087
**Child stories:** US-026 to US-029

---

### 5.2 Employee Use Cases

---

**UC-005: Configure Foundation Master Data**

**Primary actor:** ER-02 Master Data Manager
**Secondary actors:** ER-01 Operations Head (approval)
**Goal:** To configure the stations, routes, and distance data that the rest of the master data depends on.

**Preconditions:** The employee is authenticated and holds the Master Data Manager role.

**Trigger:** The employee selects Foundation Setup on the Employee Admin Console.

**Main flow:**

1. The employee reads the reference dataset provided for the role.
2. The employee creates each station with a unique code and name.
3. The employee creates each route as an ordered list of stations.
4. The employee assigns a cumulative distance to each route stop.
5. The employee submits the changes for approval.
6. The Operations Head approves the changes.

**Alternate flows:**

- **A1 — Duplicate station code.** At step 2, if the code already exists, the system returns a conflict response.
- **A2 — Route stop list is invalid.** At step 3, if a station is missing or the origin and destination are the same, the system returns a validation response.
- **A3 — Cumulative distances are not strictly increasing.** At step 4, the system returns a validation response naming the failing stop.
- **A4 — The Operations Head rejects the change.** At step 6, if the change is rejected, the system returns the reason and the change is not committed.

**Postconditions:** On success, the stations and routes are recorded and available to Service Managers and Composition Managers.

**Capability:** CAP-006, CAP-007
**Software Requirement:** SR-019 to SR-024, SR-035
**Child stories:** US-030 to US-036

---

**UC-006: Configure a Train Service**

**Primary actor:** ER-03 Service Manager
**Secondary actors:** ER-01 Operations Head (approval)
**Goal:** To configure a train, its schedule, and its coach composition so that it can be sold to customers.

**Preconditions:**
- The employee is authenticated and holds the Service Manager role.
- Stations and routes exist.
- Classes exist, or the Composition Manager has completed class setup.

**Trigger:** The employee selects Train Service Setup on the Employee Admin Console.

**Main flow:**

1. The employee reads the reference dataset for the train and its timetable.
2. The employee creates a train with a unique five-digit number, a name, and a type.
3. The employee creates a schedule that binds the train to a route with running days and timings.
4. The employee configures the coach composition of the train, using the classes set up by the Composition Manager.
5. The employee submits the changes for approval.
6. The Operations Head approves the changes.

**Alternate flows:**

- **A1 — Duplicate train number.** At step 2, the system returns a conflict response.
- **A2 — Invalid schedule timings.** At step 3, if a departure precedes its arrival or the halt duration does not match, the system returns a validation response.
- **A3 — Referenced class does not exist.** At step 4, the system returns a not-found response naming the missing class.
- **A4 — The Operations Head rejects the change.** At step 6, the system returns the reason and the change is not committed.

**Postconditions:** On success, the train, schedule, and coach composition are recorded. The train becomes searchable by customers once the seat matrix is generated.

**Capability:** CAP-008, CAP-009
**Software Requirement:** SR-025 to SR-030, SR-035
**Child stories:** US-037 to US-045

---

**UC-007: Configure Pricing Rules**

**Primary actor:** ER-05 Pricing Manager
**Secondary actors:** ER-01 Operations Head (approval)
**Goal:** To configure the fare rules, dynamic pricing rules, and concession rules that determine the price of a ticket.

**Preconditions:**
- The employee is authenticated and holds the Pricing Manager role.
- Classes and distances exist.

**Trigger:** The employee selects Pricing Setup on the Employee Admin Console.

**Main flow:**

1. The employee reads the fare policy, the distance slab table, and the concession policy.
2. The employee configures base fare rules per class.
3. The employee configures dynamic pricing rules where applicable.
4. The employee configures concession rules.
5. The employee submits the changes for approval.
6. The Operations Head approves the changes.

**Alternate flows:**

- **A1 — Distance slabs overlap or leave a gap.** At step 2, the system returns a validation response naming the failing slab.
- **A2 — Dynamic pricing rule would produce a fare below the base.** At step 3, the system returns a validation response.
- **A3 — Two concession rules overlap without stacking permitted.** At step 4, the system returns a conflict response.
- **A4 — The Operations Head rejects the change.** At step 6, the system returns the reason and the change is not committed.

**Postconditions:** On success, the fare rules are recorded and become effective for future bookings.

**Capability:** CAP-011, CAP-012, CAP-013
**Software Requirement:** SR-036 to SR-039, SR-046
**Child stories:** US-046 to US-052

---

**UC-008: Trigger Chart Preparation**

**Primary actor:** ER-06 Operations Manager
**Secondary actors:** SY-01 Scheduled Job (automatic trigger)
**Goal:** To finalise the passenger manifest for a departing journey, either on schedule or on demand.

**Preconditions:** The journey exists and its departure is within the chart preparation window defined in [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md) — Domain Rules: Chart Preparation.

**Trigger:** The chart preparation window opens automatically, or the Operations Manager triggers the chart manually.

**Main flow:**

1. The system identifies the journeys that are within the chart window.
2. The system resolves the remaining quota pools, RAC allocations, and waitlist positions.
3. The system locks the seat matrix for each journey.
4. The system records the chart preparation as an audit entry.
5. The system dispatches notification events for any passengers whose status changed.

**Alternate flows:**

- **A1 — A booking cannot be resolved.** At step 2, if a booking cannot be resolved because a passenger record is incomplete, the booking is flagged for manual attention and the chart is not fully committed until resolved.
- **A2 — Chart preparation fails.** At step 2, if the process fails, no partial commit occurs, the failure is logged, and the process retries on the next scheduled attempt.
- **A3 — Both retries fail.** The Lead Architect is notified through the operations alerting channel defined in [SRIS-P1-OPS-003](../wave-5-devops-operations/SRIS-P1-OPS-003_MonitoringAndAlertingGuide.md) — Monitoring and Alerting Guide.

**Postconditions:** On success, the seat matrix for the journey is locked and every booking has a final reservation status.

**Capability:** CAP-022
**Software Requirement:** SR-070, SR-071, SR-072
**Child stories:** US-053 to US-055

---

### 5.3 Administrator Use Cases

---

**UC-009: Manage Employee Accounts and Roles**

**Primary actor:** AD-01 Super Admin
**Goal:** To create employee accounts, assign roles, deactivate accounts, and reset credentials.

**Preconditions:** The Super Admin is authenticated and holds the Super Admin role.

**Trigger:** The Super Admin selects User Management on the Employee Admin Console.

**Main flow:**

1. The Super Admin creates an employee account with the employee's name, email, and initial credentials.
2. The Super Admin assigns one or more employee roles (ER-01 to ER-06) to the account.
3. The system records the assignment in the audit log.
4. The system dispatches an invitation email to the employee with a link to set a password.

**Alternate flows:**

- **A1 — Email already registered.** At step 1, the system returns a conflict response.
- **A2 — Role ID is not one of the defined roles.** At step 2, the system returns a validation response.
- **A3 — Invitation email dispatch fails.** At step 4, the account is created and the email is queued for retry. The Super Admin is informed of the delay.

**Postconditions:** On success, the employee account exists and the employee can log in with the assigned roles.

**Capability:** CAP-002, CAP-003
**Software Requirement:** SR-010
**Child stories:** US-056 to US-058

---

### 5.4 System Use Cases

---

**UC-010: Automatic Seat Matrix Generation**

**Primary actor:** SY-01 Scheduled Job
**Goal:** To generate the seat matrix for a scheduled journey so that customers can search, see availability, and book.

**Preconditions:**
- The journey's schedule exists and its date falls within the generation window.
- The coach composition of the train is configured.

**Trigger:** The generation window opens for a journey, or a customer requests availability for a journey whose matrix does not yet exist.

**Main flow:**

1. The system identifies the journey and its train.
2. The system expands the coach composition into physical seats and berths.
3. The system partitions the seats into the quotas defined for each class.
4. The system records the seat matrix for the journey.
5. The seat matrix becomes available to the availability service.

**Alternate flows:**

- **A1 — Master data incomplete.** At step 2, if the coach composition or the class configuration is incomplete, the system returns a configuration error and does not generate a partial matrix.
- **A2 — Matrix already exists.** At step 3, if a matrix already exists for the same train and journey date, the system does not regenerate it.
- **A3 — Quota allocation is invalid.** At step 3, if the quota allocation exceeds the seat count or leaves fewer seats than the minimum reserve, the system returns a configuration error.

**Postconditions:** On success, the seat matrix exists for the journey and is queryable by the availability service.

**Capability:** CAP-015, CAP-016
**Software Requirement:** SR-047, SR-048, SR-049
**Child stories:** US-059 to US-061

---

**UC-011: Waitlist Cascade on Cancellation**

**Primary actor:** SY-02 Event Consumer
**Goal:** To advance the waitlist queues when a seat becomes available, so that a waitlisted passenger is promoted.

**Preconditions:** A seat has been released by a cancellation, an expiry, or a chart preparation resolution.

**Trigger:** The system receives the seat-released event.

**Main flow:**

1. The system identifies the released seat, its class, its quota, and its journey segment.
2. The system identifies the highest-ranked eligible passenger on the waitlist queue for that class, quota, and segment.
3. The system promotes the passenger, updates the booking, and allocates the seat.
4. The system publishes a promotion event.
5. The system dispatches a promotion notification to the customer.

**Alternate flows:**

- **A1 — No eligible passenger on the queue.** At step 2, if no passenger is eligible, the seat remains available in the general pool.
- **A2 — Promotion event cannot be published.** At step 4, if the event cannot be published, the promotion is not committed and is retried. On continued failure, the promotion is rolled back and the queue is restored.
- **A3 — Notification dispatch fails.** At step 5, the promotion stands and the notification is queued for retry.

**Postconditions:** On success, the promoted passenger holds a confirmed seat and their booking status is updated.

**Capability:** CAP-021
**Software Requirement:** SR-068, SR-069
**Child stories:** US-062, US-063

---

**UC-012: Notification Dispatch on Booking Events**

**Primary actor:** SY-02 Event Consumer
**Goal:** To dispatch booking-related notifications to customers in response to domain events.

**Preconditions:** A domain event of a notification-triggering type has been published.

**Trigger:** The system consumes a domain event of type BookingConfirmed, BookingWaitlisted, BookingPromoted, BookingCancelled, or BookingRefunded.

**Main flow:**

1. The system identifies the template for the event type.
2. The system renders the notification from the template and the event payload.
3. The system dispatches the notification by email and by SMS.
4. The system records the dispatch in the delivery log.

**Alternate flows:**

- **A1 — Template missing.** At step 1, if the template does not exist, the event is routed to the dead-letter channel and the Lead Architect is notified.
- **A2 — Template rendering fails.** At step 2, if a required field is missing from the event payload, the dispatch fails and is routed to the dead-letter channel.
- **A3 — Notification channel does not respond.** At step 3, the system retries on the bounded backoff schedule defined in [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md) — Idempotency and Retry Policy Specification. After the maximum retry count, the notification is marked as failed.
- **A4 — Sensitive field not permitted.** At step 2, if the template attempts to render a field that is not permitted for the notification type, the render fails and the dispatch routes to the dead-letter channel.

**Postconditions:** On success, every triggered notification is dispatched and logged. On failure, the failure is logged and does not affect the underlying booking.

**Capability:** CAP-029, CAP-030
**Software Requirement:** SR-095 to SR-100
**Child stories:** US-064 to US-068

---

## 6. Customer Stories

This section records the user stories for the Customer parent role. Each story carries the metadata fields defined in [Section 3.4](#34-story-metadata-fields). Every story is a child of the use case named in its metadata, unless the metadata states None.

The stories are grouped by the phase of the customer journey they belong to.

### 6.1 Authentication and Account

---

**US-001: Register an Account**

**Actor:** CU-01 Visitor
**Story:** As a Visitor, I want to register a customer account so that I can book tickets.

**Acceptance criteria:**

- Given I am on the registration page, when I provide a valid email address, a policy-compliant password, and the required profile fields and submit, then the system creates a pending account and dispatches a verification email.
- Given the email is already registered, when I submit the form, then the system returns a conflict response and does not create an account.
- Given the password does not meet the policy, when I submit the form, then the system returns a validation response naming the failing rule.

**Use Case:** UC-001
**Capability:** CAP-001
**Software Requirement:** SR-001
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-002: Verify Email**

**Actor:** CU-01 Visitor
**Story:** As a Visitor, I want to verify my email address so that my account becomes active.

**Acceptance criteria:**

- Given I received a verification email, when I open the signed link within the valid window, then my account moves to active and I can log in.
- Given the link is expired or already used, when I open it, then the system shows an invalid-link page and offers a re-send action.
- Given I request a re-send, then the system issues a new signed link and invalidates the previous one.

**Use Case:** None
**Capability:** CAP-001
**Software Requirement:** SR-002
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-003: Log In**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to log in with my credentials so that I can access my account.

**Acceptance criteria:**

- Given I provide valid credentials, when I submit, then the system issues an access token and a refresh token.
- Given I provide an invalid credential, when I submit, then the system returns an authentication-failed response that does not reveal which field was wrong.
- Given I have failed three consecutive times, when I submit again, then the system temporarily locks my account and returns the unlock time.
- Given my account is pending, when I submit, then the system returns a pending-verification response.

**Use Case:** None
**Capability:** CAP-001, CAP-004
**Software Requirement:** SR-003
**Non-Functional Requirement:** NFR-007
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-004: Log Out**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to log out so that my session is closed.

**Acceptance criteria:**

- Given I am logged in, when I select Logout, then my access token is invalidated and my refresh token is revoked.
- Given I am already logged out, when Logout is invoked again, then the system returns a success response.

**Use Case:** None
**Capability:** CAP-004
**Software Requirement:** SR-004
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

### 6.2 Search and Selection

---

**US-005: Search for Trains**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to search for trains by origin, destination, date, class, and quota so that I can see the services that match my journey.

**Acceptance criteria:**

- Given I enter a valid origin, destination, and date and submit, then the system returns matching trains within the search latency budget defined in NFR-005.
- Given the origin or destination does not exist, when I submit, then the system returns a not-found response and asks me to select a valid station.
- Given the date is in the past or beyond the booking horizon, when I submit, then the system returns a validation response.

**Use Case:** UC-002
**Capability:** CAP-027
**Software Requirement:** SR-088
**Non-Functional Requirement:** NFR-005, NFR-011
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-006: View Search Results**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to see the matching trains in a list so that I can compare them.

**Acceptance criteria:**

- Given matching trains exist, when the results return, then each train is shown with its number, name, departure, and arrival.
- Given a field could not be populated, then that field is marked "Currently unavailable" rather than shown as zero.
- Given no trains match, then the system displays an empty state with a suggestion to adjust the criteria.

**Use Case:** UC-002
**Capability:** CAP-027, CAP-028
**Software Requirement:** SR-090, SR-093
**Non-Functional Requirement:** NFR-005
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-007

---

**US-007: Filter Search Results by Class**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to filter search results by class so that I only see trains that offer the class I want.

**Acceptance criteria:**

- Given I select a class filter, when I apply it, then only trains offering that class are shown.
- Given the class filter matches no trains, then the system returns an empty result rather than an error.

**Use Case:** UC-002
**Capability:** CAP-027, CAP-028
**Software Requirement:** SR-089
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-008: View Class Availability**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to see the availability of a specific class so that I know whether I can book.

**Acceptance criteria:**

- Given a class has seats, when I select the class, then the system displays the current seat count with the reading timestamp.
- Given a class has no seats but has a waitlist, then the system displays the waitlist position and offers it as an option.
- Given the availability reading is unavailable, then the class is marked unavailable rather than shown as zero.

**Use Case:** UC-002
**Capability:** CAP-017
**Software Requirement:** SR-051, SR-052
**Non-Functional Requirement:** NFR-005
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-009: View Fare Quote**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to see the fare for a specific class so that I can make a booking decision.

**Acceptance criteria:**

- Given I select a class, then the fare quote for the requested segment is shown.
- Given the fare quote cannot be computed, then the fare is marked unavailable rather than shown as zero.

**Use Case:** UC-002
**Capability:** CAP-014
**Software Requirement:** SR-040, SR-092
**Non-Functional Requirement:** NFR-001
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-010: Select a Train, Class, and Quota**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to select a train, class, and quota so that I can proceed to book.

**Acceptance criteria:**

- Given I select all three, then the system proceeds to the passenger entry form.
- Given the class has no seats, then the system offers waitlist or alternate class.
- Given the quota is not one of the defined values, then the system returns a validation response.

**Use Case:** UC-002
**Capability:** CAP-027
**Software Requirement:** SR-089
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-011: Start Booking from Search Result**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to book directly from a search result so that I do not lose my selection.

**Acceptance criteria:**

- Given I select Book on a result card, then the booking flow opens with the train, class, and quota pre-filled.
- Given I abandon the flow before entering passengers, then no booking is created.

**Use Case:** UC-002
**Capability:** CAP-019
**Software Requirement:** SR-059
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-012: Search from Home Screen**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to reach the search form from the home screen in one action so that I can start quickly.

**Acceptance criteria:**

- Given I am on the customer home screen, when I select Search Train, then the search form opens.
- Given I am on the customer home screen, when I select Book Ticket, then the search form opens with the booking intent set.

**Use Case:** None
**Capability:** CAP-027
**Software Requirement:** SR-101
**Non-Functional Requirement:** NFR-029
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-007

---

### 6.3 Booking and Payment

---

**US-013: Enter Passenger Details**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to enter passenger details so that the ticket is issued in the correct names.

**Acceptance criteria:**

- Given I enter name, age, gender, and berth preference for each passenger, when I submit, then the system validates the details and proceeds.
- Given a required field is missing, then the system returns a validation response naming the field.
- Given the passenger count exceeds the allowed maximum, then the system returns a validation response.

**Use Case:** UC-002
**Capability:** CAP-019
**Software Requirement:** SR-059
**Non-Functional Requirement:** NFR-028
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-014: Review Booking Before Payment**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to review the full booking details before payment so that I can confirm them.

**Acceptance criteria:**

- Given I proceed from passenger entry, then the system shows train, journey date, passenger list, class, quota, and fare re-quote.
- Given the fare re-quote differs from the search-time quote, then both amounts are shown with the difference.
- Given the review screen is shown, then I must confirm before payment is enabled.

**Use Case:** UC-002
**Capability:** CAP-014, CAP-019
**Software Requirement:** SR-061
**Non-Functional Requirement:** NFR-027
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-007

---

**US-015: Select Payment Method**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to select a payment method so that I can complete the payment.

**Acceptance criteria:**

- Given the review is confirmed, then the payment page shows the available mock payment methods.
- Given I select a method, then the system initiates the payment through the mock gateway.

**Use Case:** UC-002
**Capability:** CAP-025
**Software Requirement:** SR-080
**Non-Functional Requirement:** NFR-006
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-016: View Payment Loading State**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to see the progress of my payment so that I know the system is working.

**Acceptance criteria:**

- Given payment is in progress, then the surface shows a loading state naming the current stage.
- Given the request times out, then a timeout state is shown with a retry action.
- Given the response is not a success, the surface does not show a success state.

**Use Case:** UC-002
**Capability:** CAP-025
**Software Requirement:** SR-105
**Non-Functional Requirement:** NFR-027
**UI Owner:** SRIS-P1-UI-008 (planned)
**Test Owner:** SRIS-P1-TEST-007

---

**US-017: Receive Confirmation and PNR**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to receive confirmation with a PNR so that I have a valid ticket.

**Acceptance criteria:**

- Given payment succeeds and a seat is allocated, then the system displays the PNR and the ticket.
- Given payment succeeds but no seat can be allocated, then the system places me on the waitlist queue or initiates a refund and returns an explicit response.
- Given confirmation completes, then the system dispatches email and SMS confirmations asynchronously.

**Use Case:** UC-002
**Capability:** CAP-019, CAP-020, CAP-021
**Software Requirement:** SR-064, SR-065, SR-066
**Non-Functional Requirement:** NFR-006, NFR-038
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-018: View Confirmed Ticket**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to view my confirmed ticket so that I can check the details.

**Acceptance criteria:**

- Given a booking is confirmed, then the ticket shows PNR, journey details, passengers, coach and berth assignment.
- Given a booking is waitlisted, then the ticket shows PNR, journey details, passengers, and waitlist position.

**Use Case:** UC-002
**Capability:** CAP-024
**Software Requirement:** SR-077
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-007

---

**US-019: Book on Behalf of Another Passenger**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to book on behalf of other passengers so that I can book for family or friends.

**Acceptance criteria:**

- Given I add multiple passengers, then each passenger is recorded separately with their details.
- Given the total passenger count exceeds the allowed maximum, then the system returns a validation response.

**Use Case:** UC-002
**Capability:** CAP-019
**Software Requirement:** SR-059
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-020: Abandon a Booking Attempt**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to leave the booking flow before payment so that no charge is made.

**Acceptance criteria:**

- Given I close the flow before payment, then no booking is created.
- Given any seat protection was created during the flow, then it is released per the mechanism in SRIS-P1-REQ-008.

**Use Case:** UC-002
**Capability:** CAP-019
**Software Requirement:** SR-059
**Non-Functional Requirement:** NFR-076
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-021: Recover from Payment Failure**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to retry payment after a failure so that I can complete my booking.

**Acceptance criteria:**

- Given payment fails, then the system returns me to the payment step with the failure reason.
- Given I retry, then the system uses the same booking attempt and a new idempotency key.

**Use Case:** UC-002
**Capability:** CAP-025
**Software Requirement:** SR-082, SR-083
**Non-Functional Requirement:** NFR-077
**UI Owner:** SRIS-P1-UI-008 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-022: Receive Refund When No Seat is Allocated**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want my payment reversed when no seat can be allocated so that I do not lose money.

**Acceptance criteria:**

- Given payment succeeds but no seat can be allocated and the waitlists are full, then the system initiates a reversal.
- Given the reversal succeeds, then the customer is notified of the reversal.
- Given the reversal cannot be acknowledged immediately, then the booking is marked refund-pending and the customer is notified of the pending state.

**Use Case:** UC-002
**Capability:** CAP-025, CAP-026
**Software Requirement:** SR-086
**Non-Functional Requirement:** NFR-076
**UI Owner:** SRIS-P1-UI-008 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-023: See the Difference Between Search-Time and Booking-Time Fare**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to see if the fare changed since search so that I decide whether to proceed.

**Acceptance criteria:**

- Given the fare re-quote is higher than the search quote, then both amounts are shown with the difference.
- Given the fare re-quote is equal, then a single amount is shown.
- Given the customer does not confirm the higher amount, then the booking does not proceed.

**Use Case:** UC-002
**Capability:** CAP-014
**Software Requirement:** SR-041
**Non-Functional Requirement:** NFR-001
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-024: Book with a Concession**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to book with an applicable concession so that I pay the correct reduced fare.

**Acceptance criteria:**

- Given I declare a passenger category that qualifies for a concession, then the concession is applied to that passenger's fare.
- Given two concessions apply and stacking is not permitted, then the higher concession is applied.
- Given the concession cannot be verified at booking time, then the concession is applied and the booking is flagged for verification.

**Use Case:** UC-002
**Capability:** CAP-013, CAP-014
**Software Requirement:** SR-042
**Non-Functional Requirement:** NFR-001
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

### 6.4 Ticket Retrieval

---

**US-025: Retrieve Ticket by PNR**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to retrieve my ticket by PNR so that I can see the booking details.

**Acceptance criteria:**

- Given I submit a valid PNR that belongs to me, then the system returns passenger list, journey details, status, and coach and berth assignment.
- Given the PNR is invalid format, then the system returns a validation response.
- Given the PNR belongs to another customer, then the system returns a forbidden response that does not reveal whether the PNR exists.

**Use Case:** UC-003
**Capability:** CAP-024
**Software Requirement:** SR-077
**Non-Functional Requirement:** NFR-078
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

### 6.5 Cancellation

---

**US-026: Cancel a Confirmed Booking**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to cancel a confirmed booking so that I can recover part of the fare.

**Acceptance criteria:**

- Given the journey has not departed, when I confirm cancellation, then the booking is cancelled, the seat is released, and the refund is initiated.
- Given the journey has departed, then the system returns a not-allowed response.
- Given I do not own the booking, then the system returns a forbidden response.

**Use Case:** UC-004
**Capability:** CAP-023, CAP-018
**Software Requirement:** SR-073, SR-057
**Non-Functional Requirement:** NFR-076
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-027: View the Refund Amount Before Confirming Cancellation**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to see the refund amount before I confirm cancellation so that I understand the cost.

**Acceptance criteria:**

- Given I open the cancellation flow, then the refund amount computed from the applicable fare rules is shown.
- Given the fare rule that applied at booking time is no longer in effect, then the archived rule is used and the reference is noted.

**Use Case:** UC-004
**Capability:** CAP-014, CAP-023
**Software Requirement:** SR-074, SR-045
**Non-Functional Requirement:** NFR-001
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-028: Receive Refund Confirmation**

**Actor:** CU-02 Registered Customer
**Story:** As a Registered Customer, I want to be notified when my refund is processed so that I know the money is on the way.

**Acceptance criteria:**

- Given the cancellation succeeds and the refund is initiated, then the system dispatches a refund confirmation.
- Given the refund cannot be acknowledged, then a refund-pending notification is dispatched.

**Use Case:** UC-004
**Capability:** CAP-029, CAP-023
**Software Requirement:** SR-087, SR-096
**Non-Functional Requirement:** NFR-038
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-029: Recover Waitlist Promotion After Cancellation**

**Actor:** CU-02 Registered Customer
**Story:** As a waitlisted Registered Customer, I want to be promoted when a seat becomes available so that I can travel confirmed.

**Acceptance criteria:**

- Given a seat is released on my class, quota, and segment, then if I am the highest-ranked eligible passenger, I am promoted.
- Given I am promoted, then my status changes to confirmed and I am notified.

**Use Case:** UC-011
**Capability:** CAP-021
**Software Requirement:** SR-068, SR-069
**Non-Functional Requirement:** NFR-037
**UI Owner:** SRIS-P1-UI-003 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

## 7. Employee Stories

This section records the user stories for the Employee parent role. Each story carries the metadata fields defined in [Section 3.4](#34-story-metadata-fields). Stories are grouped by the employee role (ER-01 to ER-06) they belong to, and within a role, in the dependency order of the master data.

### 7.1 Master Data Manager Stories (ER-02)

---

**US-030: Create a Station**

**Actor:** ER-02 Master Data Manager
**Story:** As a Master Data Manager, I want to create a station with a unique code and name so that it can be used in routes and schedules.

**Acceptance criteria:**

- Given I submit a new station code and name, then the station is recorded and becomes available for route creation.
- Given the station code already exists, then the system returns a conflict response.
- Given any field fails validation, then the system returns a validation response naming the field.

**Use Case:** UC-005
**Capability:** CAP-006
**Software Requirement:** SR-019
**Non-Functional Requirement:** NFR-008
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-031: Update a Station**

**Actor:** ER-02 Master Data Manager
**Story:** As a Master Data Manager, I want to update an existing station so that corrections can be made.

**Acceptance criteria:**

- Given the station exists, when I update the name or attributes, then the change is recorded.
- Given the update changes the station code to one already in use, then the system returns a conflict response.

**Use Case:** UC-005
**Capability:** CAP-006
**Software Requirement:** SR-020
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-032: Deactivate a Station**

**Actor:** ER-02 Master Data Manager
**Story:** As a Master Data Manager, I want to deactivate a station so that it no longer appears in new routes and schedules.

**Acceptance criteria:**

- Given the station is not referenced by an active schedule, when I deactivate it, then it is removed from the active list.
- Given the station is referenced by an active schedule, then the system returns a conflict response naming the referring schedules.

**Use Case:** UC-005
**Capability:** CAP-006
**Software Requirement:** SR-021
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-033: Create a Route**

**Actor:** ER-02 Master Data Manager
**Story:** As a Master Data Manager, I want to create a route as an ordered list of existing stations so that trains can run on it.

**Acceptance criteria:**

- Given I select an ordered list of stations from origin to destination, then the route is recorded.
- Given any station in the list does not exist, then the system returns a not-found response naming the missing station.
- Given the origin and destination are the same, then the system returns a validation response.

**Use Case:** UC-005
**Capability:** CAP-007
**Software Requirement:** SR-022
**Non-Functional Requirement:** NFR-008
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-034: Assign Cumulative Distances to Route Stops**

**Actor:** ER-02 Master Data Manager
**Story:** As a Master Data Manager, I want to assign a cumulative distance to each route stop so that fares can be calculated from any origin to any destination.

**Acceptance criteria:**

- Given I enter cumulative distances, then they are validated to be strictly increasing from origin to destination.
- Given the distances are not strictly increasing, then the system returns a validation response naming the failing stop.

**Use Case:** UC-005
**Capability:** CAP-007
**Software Requirement:** SR-022
**Non-Functional Requirement:** NFR-008
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-035: Insert an Intermediate Stop into a Route**

**Actor:** ER-02 Master Data Manager
**Story:** As a Master Data Manager, I want to insert an intermediate stop into an existing route so that a new halt can be added.

**Acceptance criteria:**

- Given I insert a stop and supply its cumulative distance between the adjacent stops, then the route is updated.
- Given the inserted distance is not between the adjacent distances, then the system returns a validation response.

**Use Case:** UC-005
**Capability:** CAP-007
**Software Requirement:** SR-024
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-036: Submit Master Data Changes for Approval**

**Actor:** ER-02 Master Data Manager
**Story:** As a Master Data Manager, I want to submit my changes to the Operations Head for approval so that the changes take effect.

**Acceptance criteria:**

- Given I have pending changes, when I submit them, then they are queued for Operations Head approval.
- Given the changes are rejected, then the reason is shown to me and the changes are not committed.

**Use Case:** UC-005
**Capability:** CAP-006, CAP-007
**Software Requirement:** SR-035
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

### 7.2 Service Manager Stories (ER-03)

---

**US-037: Create a Train**

**Actor:** ER-03 Service Manager
**Story:** As a Service Manager, I want to create a train with a unique number, name, and type so that it can be scheduled on a route.

**Acceptance criteria:**

- Given I submit a new five-digit train number, name, and type, then the train is recorded.
- Given the train number is already in use, then the system returns a conflict response.
- Given the type is not one of the defined values, then the system returns a validation response.

**Use Case:** UC-006
**Capability:** CAP-008
**Software Requirement:** SR-025
**Non-Functional Requirement:** NFR-008
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-038: Update a Train**

**Actor:** ER-03 Service Manager
**Story:** As a Service Manager, I want to update a train's name and type so that corrections can be made.

**Acceptance criteria:**

- Given the train exists, when I update name or type, then the change is recorded.
- Given I attempt to change the train number, then the system does not permit it.

**Use Case:** UC-006
**Capability:** CAP-008
**Software Requirement:** SR-026
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-039: Create a Train Schedule**

**Actor:** ER-03 Service Manager
**Story:** As a Service Manager, I want to create a schedule by binding a train to a route with running days and timings so that the train is searchable by customers.

**Acceptance criteria:**

- Given I submit a schedule with running days and per-stop arrival, departure, and halt timings, then the schedule is recorded.
- Given any stop's departure precedes its arrival, then the system returns a validation response naming the stop.
- Given the halt duration does not match arrival-to-departure difference, then the system returns a validation response.

**Use Case:** UC-006
**Capability:** CAP-008
**Software Requirement:** SR-027
**Non-Functional Requirement:** NFR-008
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-040: Update a Schedule**

**Actor:** ER-03 Service Manager
**Story:** As a Service Manager, I want to update a schedule's running days or timings so that changes can be made safely.

**Acceptance criteria:**

- Given no confirmed bookings exist for the affected future dates, when I update timings, then the schedule is updated.
- Given confirmed bookings exist for a future date whose timings are affected, then the system returns a conflict response naming the date and suggesting a new schedule.

**Use Case:** UC-006
**Capability:** CAP-008
**Software Requirement:** SR-028
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-041: View the Impact of a Schedule Change**

**Actor:** ER-03 Service Manager
**Story:** As a Service Manager, I want to see the impact of a schedule change before committing it so that I avoid unintended effects.

**Acceptance criteria:**

- Given I propose a change, then the system shows the affected future journeys and the bookings on them.
- Given the change is not confirmed, then no change is applied.

**Use Case:** UC-006
**Capability:** CAP-008
**Software Requirement:** SR-028
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-007

---

**US-042: Configure Coach Composition**

**Actor:** ER-03 Service Manager
**Story:** As a Service Manager, I want to define the coach composition of a train so that the seat inventory can be generated from it.

**Acceptance criteria:**

- Given I define an ordered list of coaches with their class and berth layout, then the composition is recorded.
- Given a referenced class does not exist, then the system returns a not-found response naming the missing class.
- Given the total capacity exceeds the allowed maximum, then the system returns a validation response.

**Use Case:** UC-006
**Capability:** CAP-009
**Software Requirement:** SR-029
**Non-Functional Requirement:** NFR-008
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-043: Update Coach Composition Before Generation**

**Actor:** ER-03 Service Manager
**Story:** As a Service Manager, I want to update the coach composition before a seat matrix is generated so that I can adjust capacity.

**Acceptance criteria:**

- Given no future journey of the train has a generated seat matrix, when I update the composition, then the change is applied.
- Given any future journey has a generated matrix, then the system returns a conflict response naming the affected dates.

**Use Case:** UC-006
**Capability:** CAP-009
**Software Requirement:** SR-030
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-044: Submit a Train Service for Approval**

**Actor:** ER-03 Service Manager
**Story:** As a Service Manager, I want to submit a train service configuration to the Operations Head for approval so that it becomes effective.

**Acceptance criteria:**

- Given the configuration is complete, when I submit it, then it is queued for approval.
- Given the Operations Head rejects it, then the reason is shown and no changes are committed.

**Use Case:** UC-006
**Capability:** CAP-008, CAP-009
**Software Requirement:** SR-035
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-045: View Train List**

**Actor:** ER-03 Service Manager
**Story:** As a Service Manager, I want to see all trains I have configured so that I can manage them.

**Acceptance criteria:**

- Given trains exist, then they are shown in a list with number, name, type, and status.
- Given a train is pending approval, then the status reflects that.

**Use Case:** None
**Capability:** CAP-008
**Software Requirement:** SR-026
**Non-Functional Requirement:** NFR-030
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-007

---

### 7.3 Pricing Manager Stories (ER-05)

---

**US-046: Configure Base Fare Rule**

**Actor:** ER-05 Pricing Manager
**Story:** As a Pricing Manager, I want to configure a base fare rule for a class so that fares can be calculated from distance.

**Acceptance criteria:**

- Given I submit a base rate per kilometre, distance slabs, and class multiplier, then the rule is recorded.
- Given distance slabs overlap or leave a gap, then the system returns a validation response naming the slab.
- Given a rate is negative, then the system returns a validation response.

**Use Case:** UC-007
**Capability:** CAP-011
**Software Requirement:** SR-036
**Non-Functional Requirement:** NFR-001
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-047: Configure Dynamic Pricing Rule**

**Actor:** ER-05 Pricing Manager
**Story:** As a Pricing Manager, I want to configure a dynamic pricing rule so that fares rise as inventory depletes.

**Acceptance criteria:**

- Given I submit a rule with percentage increments per inventory level, then it is recorded.
- Given the increments would ever produce a fare below the base, then the system returns a validation response.
- Given the rule overlaps with another for the same class and quota, then the system returns a conflict response.

**Use Case:** UC-007
**Capability:** CAP-012
**Software Requirement:** SR-038
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-048: Configure Concession Rule**

**Actor:** ER-05 Pricing Manager
**Story:** As a Pricing Manager, I want to configure a concession rule so that eligible passenger categories receive a fare reduction.

**Acceptance criteria:**

- Given I submit a rule with eligibility criteria and a percentage reduction, then it is recorded.
- Given the reduction is outside the permitted range, then the system returns a validation response.
- Given two concession rules overlap and stacking is not permitted, then the system returns a conflict response.

**Use Case:** UC-007
**Capability:** CAP-013
**Software Requirement:** SR-039
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-049: View Active Fare Rules**

**Actor:** ER-05 Pricing Manager
**Story:** As a Pricing Manager, I want to see the currently active fare rules so that I can review them.

**Acceptance criteria:**

- Given rules exist, then the active rules are listed by class with their effective dates.
- Given a rule is scheduled for a future date, then it is shown separately.

**Use Case:** None
**Capability:** CAP-011
**Software Requirement:** SR-037
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-007

---

**US-050: Preview the Effect of a Fare Change**

**Actor:** ER-05 Pricing Manager
**Story:** As a Pricing Manager, I want to preview the effect of a fare change before committing it so that I understand the impact.

**Acceptance criteria:**

- Given I propose a change, then the system shows the new fare for representative distances and classes.
- Given the change is not confirmed, then no change is applied.

**Use Case:** UC-007
**Capability:** CAP-011, CAP-014
**Software Requirement:** SR-036
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-007

---

**US-051: Submit a Pricing Change for Approval**

**Actor:** ER-05 Pricing Manager
**Story:** As a Pricing Manager, I want to submit a pricing change to the Operations Head for approval so that it becomes effective.

**Acceptance criteria:**

- Given the change is complete, when I submit, then it is queued for approval.
- Given it is rejected, then the reason is shown and no change is committed.

**Use Case:** UC-007
**Capability:** CAP-011, CAP-012, CAP-013
**Software Requirement:** SR-046
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-052: View the Fare Configuration Audit Trail**

**Actor:** ER-05 Pricing Manager
**Story:** As a Pricing Manager, I want to see who changed a fare rule and when so that changes are traceable.

**Acceptance criteria:**

- Given audit entries exist, then each shows the employee, the rule changed, the before and after values, and the timestamp.
- Given no changes have been made, then the audit trail is empty rather than absent.

**Use Case:** None
**Capability:** CAP-011, CAP-012, CAP-013
**Software Requirement:** SR-046
**Non-Functional Requirement:** NFR-042
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

### 7.4 Operations Manager Stories (ER-06)

---

**US-053: View Upcoming Departures**

**Actor:** ER-06 Operations Manager
**Story:** As an Operations Manager, I want to see upcoming departures so that I know which journeys are approaching chart preparation.

**Acceptance criteria:**

- Given journeys exist, then those within the chart window are highlighted.
- Given no journeys are approaching, then the list shows the next upcoming set.

**Use Case:** None
**Capability:** CAP-022
**Software Requirement:** SR-070
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-007

---

**US-054: Trigger Chart Preparation Manually**

**Actor:** ER-06 Operations Manager
**Story:** As an Operations Manager, I want to trigger chart preparation manually for a journey so that I can prepare it ahead of schedule when needed.

**Acceptance criteria:**

- Given a journey is within the chart window, when I trigger preparation, then the chart is prepared.
- Given the journey is not within the chart window, then the system returns a not-allowed response.
- Given chart preparation fails, then the failure is logged and no partial commit occurs.

**Use Case:** UC-008
**Capability:** CAP-022
**Software Requirement:** SR-070
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-055: View the Chart Queue and Exceptions**

**Actor:** ER-06 Operations Manager
**Story:** As an Operations Manager, I want to see the chart queue and any flagged exceptions so that I can resolve them before departure.

**Acceptance criteria:**

- Given a booking could not be resolved during chart preparation, then it appears in the exception queue with the reason.
- Given an exception is resolved, then it is removed from the queue.

**Use Case:** UC-008
**Capability:** CAP-022, CAP-023
**Software Requirement:** SR-071
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-007

---

### 7.5 Super Admin Stories (AD-01)

---

**US-056: Create an Employee Account**

**Actor:** AD-01 Super Admin
**Story:** As a Super Admin, I want to create an employee account so that a new employee can access the console.

**Acceptance criteria:**

- Given I submit a new employee's name and email, then the account is created and an invitation email is dispatched.
- Given the email is already registered, then the system returns a conflict response.

**Use Case:** UC-009
**Capability:** CAP-002
**Software Requirement:** SR-010
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-057: Assign an Employee Role**

**Actor:** AD-01 Super Admin
**Story:** As a Super Admin, I want to assign one or more roles to an employee account so that the employee can perform their duties.

**Acceptance criteria:**

- Given I assign one or more valid role IDs, then the assignment takes effect on the next login.
- Given the role ID is not defined, then the system returns a validation response.

**Use Case:** UC-009
**Capability:** CAP-003
**Software Requirement:** SR-010
**Non-Functional Requirement:** None
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

**US-058: View the Role Assignment Audit Trail**

**Actor:** AD-02 Audit Officer
**Story:** As an Audit Officer, I want to see the audit trail of role assignments so that access changes are traceable.

**Acceptance criteria:**

- Given role changes have occurred, then each entry shows the Super Admin, the employee affected, the before and after roles, and the timestamp.
- Given I attempt any write action, then the system rejects it because my role is read-only.

**Use Case:** None
**Capability:** CAP-003
**Software Requirement:** SR-010
**Non-Functional Requirement:** NFR-046
**UI Owner:** SRIS-P1-UI-004 (planned)
**Test Owner:** SRIS-P1-TEST-003

---

## 8. System Stories

This section records the user stories for the System parent role. System stories use the "When [trigger], the system must…" form. They are triggered autonomously and have no human actor.

### 8.1 Seat Matrix Generation

---

**US-059: Generate Seat Matrix for Upcoming Journey**

**Actor:** SY-01 Scheduled Job
**Story:** When the generation window opens for a scheduled journey, the system must generate the seat matrix from the schedule and coach composition so that availability can be served.

**Acceptance criteria:**

- Given the master data for the journey is complete, when the generation window opens, then the matrix is generated and becomes queryable.
- Given the master data is incomplete, then the system returns a configuration error and does not generate a partial matrix.
- Given a matrix already exists for the same train and journey date, then the system does not regenerate it.

**Use Case:** UC-010
**Capability:** CAP-015
**Software Requirement:** SR-047
**Non-Functional Requirement:** NFR-013
**UI Owner:** None
**Test Owner:** SRIS-P1-TEST-003

---

**US-060: Generate Seat Matrix on First Availability Request**

**Actor:** SY-01 Scheduled Job
**Story:** When a customer requests availability for a journey whose matrix does not yet exist, the system must generate the matrix on demand so that availability can be answered.

**Acceptance criteria:**

- Given the master data is complete, when availability is requested, then the matrix is generated and the availability response returns.
- Given the master data is incomplete, then a configuration error is returned.

**Use Case:** UC-010
**Capability:** CAP-015
**Software Requirement:** SR-047
**Non-Functional Requirement:** NFR-013
**UI Owner:** None
**Test Owner:** SRIS-P1-TEST-003

---

**US-061: Partition Seat Matrix into Quotas**

**Actor:** SY-01 Scheduled Job
**Story:** When a seat matrix is generated, the system must partition it into the quotas defined for each class so that quota-level availability can be served.

**Acceptance criteria:**

- Given quota allocation rules exist, when the matrix is generated, then the seats are partitioned per class and quota.
- Given the quota allocation exceeds the seat count or leaves fewer seats than the minimum reserve, then a configuration error is returned and no matrix is generated.

**Use Case:** UC-010
**Capability:** CAP-016
**Software Requirement:** SR-049
**Non-Functional Requirement:** NFR-013
**UI Owner:** None
**Test Owner:** SRIS-P1-TEST-003

---

### 8.2 Waitlist Cascade

---

**US-062: Promote Waitlisted Passenger on Seat Release**

**Actor:** SY-02 Event Consumer
**Story:** When a seat is released on a journey, the system must promote the highest-ranked eligible waitlisted passenger so that the seat is filled.

**Acceptance criteria:**

- Given a seat is released and an eligible passenger is on the queue, then the top-ranked passenger is promoted.
- Given no eligible passenger exists, then the seat remains available.
- Given the promotion event cannot be published, then the promotion is not committed and is retried.

**Use Case:** UC-011
**Capability:** CAP-021
**Software Requirement:** SR-068, SR-069
**Non-Functional Requirement:** NFR-037
**UI Owner:** None
**Test Owner:** SRIS-P1-TEST-003

---

**US-063: Notify the Promoted Passenger**

**Actor:** SY-02 Event Consumer
**Story:** When a passenger is promoted, the system must notify the customer so that they know their status changed.

**Acceptance criteria:**

- Given the promotion is committed, then the notification is dispatched.
- Given the notification dispatch fails, then it is retried per the retry policy and does not affect the promotion.

**Use Case:** UC-011
**Capability:** CAP-021
**Software Requirement:** SR-069
**Non-Functional Requirement:** NFR-038
**UI Owner:** None
**Test Owner:** SRIS-P1-TEST-003

---

### 8.3 Notification Dispatch

---

**US-064: Dispatch Booking Confirmation**

**Actor:** SY-02 Event Consumer
**Story:** When a booking is confirmed, the system must dispatch a confirmation by email and SMS so that the customer receives the PNR.

**Acceptance criteria:**

- Given a BookingConfirmed event is consumed, then the confirmation is dispatched by both channels.
- Given one channel fails, the other is dispatched and the failed one is retried.
- Given both fail, both are retried and the booking is not affected.

**Use Case:** UC-012
**Capability:** CAP-029
**Software Requirement:** SR-095, SR-096
**Non-Functional Requirement:** NFR-009, NFR-038
**UI Owner:** None
**Test Owner:** SRIS-P1-TEST-003

---

**US-065: Dispatch Cancellation Notification**

**Actor:** SY-02 Event Consumer
**Story:** When a booking is cancelled, the system must dispatch a cancellation notification to the customer.

**Acceptance criteria:**

- Given a BookingCancelled event is consumed, then the notification is dispatched.
- Given the notification fails, then it is retried and does not affect the cancellation.

**Use Case:** UC-012
**Capability:** CAP-029
**Software Requirement:** SR-095
**Non-Functional Requirement:** NFR-009
**UI Owner:** None
**Test Owner:** SRIS-P1-TEST-003

---

**US-066: Dispatch Refund Notification**

**Actor:** SY-02 Event Consumer
**Story:** When a refund is initiated, the system must dispatch a refund notification to the customer so that they know the money is on the way.

**Acceptance criteria:**

- Given a BookingRefunded event is consumed, then the notification is dispatched.
- Given the refund cannot be acknowledged, then a refund-pending notification is dispatched instead.

**Use Case:** UC-012
**Capability:** CAP-029
**Software Requirement:** SR-095, SR-087
**Non-Functional Requirement:** NFR-009
**UI Owner:** None
**Test Owner:** SRIS-P1-TEST-003

---

**US-067: Retry Failed Notifications**

**Actor:** SY-02 Event Consumer
**Story:** When a notification dispatch fails, the system must retry it on a bounded schedule so that transient failures do not lose the notification.

**Acceptance criteria:**

- Given a dispatch fails, then it is queued for retry.
- Given the retry count is exhausted, then the notification is marked failed and is visible to operations.

**Use Case:** UC-012
**Capability:** CAP-030
**Software Requirement:** SR-097
**Non-Functional Requirement:** NFR-009
**UI Owner:** None
**Test Owner:** SRIS-P1-TEST-003

---

**US-068: Log Every Notification Dispatch**

**Actor:** SY-02 Event Consumer
**Story:** When a notification is dispatched, the system must record the attempt in the delivery log so that dispatches are auditable.

**Acceptance criteria:**

- Given a dispatch is attempted, then the log records the type, channel, template version, attempt number, outcome, and timestamp.
- Given the log cannot be written, then the dispatch is not committed and is retried.

**Use Case:** UC-012
**Capability:** CAP-030
**Software Requirement:** SR-099
**Non-Functional Requirement:** NFR-052
**UI Owner:** None
**Test Owner:** SRIS-P1-TEST-003

---

## 9. Cross-References to Other Documents

This section records how the user stories and use cases in this document link to the documents that realise and verify them. The stories and use cases do not contain screens, APIs, database schemas, test cases, or implementation mechanics. Each belongs to another document, cited here.

### 9.1 How Stories Link to the UI Documents

Every user story carries a UI Owner field. The UI Owner names the Wave 3 document that will design the screens serving that story. The UI documents do not yet exist.

| UI Owner                              | Stories That Point to It                                                                                                    |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| [SRIS-P1-UI-003](../wave-3-detailed-design/SRIS-P1-UI-003_WireframesCustomerFlow.md) — Wireframes (Customer Flow) | All Customer stories (US-001 to US-029)                                                                                     |
| [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md) — Wireframes (Employee/Admin Flow) | All Employee stories (US-030 to US-058)                                                                                     |
| [SRIS-P1-UI-008](../wave-3-detailed-design/SRIS-P1-UI-008_UIErrorAndNotificationDisplayRules.md) — UI Error and Notification Display Rules | US-016, US-021, US-022                                                                                                       |

Every story is served by exactly one UI document. When a story appears in a use case that spans both surfaces (for example, the notification dispatch triggered by a customer booking), the UI Owner is the surface where the actor sees the outcome, not the service that runs behind the scenes.

### 9.2 How Use Cases Link to the API Documents

Every use case exercises one or more services. The services expose API endpoints and publish events. The exact endpoints and event schemas belong to [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md) — API Contract Document (OpenAPI) and [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md) — Event Schema Document (AsyncAPI).

| Use Case | Services Exercised                    | API Owner           |
| -------- | ------------------------------------- | ------------------- |
| UC-001   | S1 IAM, S6 Notification               | API-001, API-003    |
| UC-002   | S1, S2, S3, S4, S5, S6                | API-001, API-003    |
| UC-003   | S1, S3                                | API-001             |
| UC-004   | S1, S3, S5, S6                        | API-001, API-003    |
| UC-005   | S1, S2                                | API-001             |
| UC-006   | S1, S2                                | API-001             |
| UC-007   | S1, S2                                | API-001             |
| UC-008   | S1, S3, S6                            | API-001, API-003    |
| UC-009   | S1                                    | API-001             |
| UC-010   | S2, S3                                | API-001             |
| UC-011   | S3, S6                                | API-001, API-003    |
| UC-012   | S3, S6                                | API-003             |

The use case names the service, not the endpoint. Endpoint-level detail belongs to the API documents.

### 9.3 How Stories and Use Cases Link to the Test Documents

Every user story carries a Test Owner field. The Test Owner names the Wave 4 document that will verify the story's acceptance criteria.

| Test Owner                                                                                        | Stories Verifying Under It                                     |
| ------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md) — Test Cases (Functional) | The majority of stories, exercising functional behaviour        |
| [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md) — Test Cases (UI)             | Stories that are principally UI behaviour (US-006, US-012, US-014, US-016, US-018, US-041, US-045, US-049, US-050, US-053, US-055) |

Test cases are derived from the Given/When/Then acceptance criteria of each story and from the alternate flows of each use case. The test document cites the US-NNN or UC-NNN identifiers from this document.

### 9.4 How the Reference Dataset Is Used

The employee roles read from a reference dataset. The dataset is created by the project. It is not obtained from any external railway system.

The dataset itself belongs to [SRIS-P1-DATA-012](../wave-3-detailed-design/SRIS-P1-DATA-012_SeedDataAndReferenceDataSpecification.md) — Seed Data and Reference Data Specification (planned). That document will define the format of the dataset, the file location in the repository, and the loading procedure.

| Employee Role | Reads From                                   |
| ------------- | -------------------------------------------- |
| ER-02         | Station list; route list with distances       |
| ER-03         | Train list; timetable and running-days policy |
| ER-04         | Class and quota policy; coach composition     |
| ER-05         | Fare policy; distance slab table; concession policy |
| ER-06         | Departure schedule; exception handling policy |

### 9.5 What This Document Does Not Contain

For clarity, the following do not appear in this document, and are cited to their owners.

| Topic                                | Owner                                                                                         |
| ------------------------------------ | --------------------------------------------------------------------------------------------- |
| Screen layouts and wireframes        | [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md) to [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md) |
| API payloads and endpoints           | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)    |
| Event schemas                        | [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md)   |
| Database schemas                     | [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md) |
| Fare, ticketing, waitlist, chart, seat matrix rules | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) to [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md) |
| Booking mechanism                    | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)                                 |
| RBAC permission matrix               | [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md)                    |
| Authentication design                | [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md) |
| Token design                         | [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)       |
| Test cases                           | [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)                  |
| Error messages                       | [SRIS-P1-API-006](../wave-3-detailed-design/SRIS-P1-API-006_APIErrorCodeCatalog.md) and [SRIS-P1-UI-008](../wave-3-detailed-design/SRIS-P1-UI-008_UIErrorAndNotificationDisplayRules.md) |

---

## 10. Traceability

This section records the local traceability of every use case and user story in this document. It maps each to the capability it realises, from [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final), and to the software requirement that supports it, from [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software Requirements Specification (SRS).

The full cross-wave matrix, which spans every document in the register, belongs to [SRIS-P1-REQ-012](./SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md) — Requirement Traceability Matrix (RTM), and is not repeated here.

### 10.1 Use Case Summary

| Use Case | Title                                       | Primary Actor | Child Stories                    | Capabilities                     |
| -------- | ------------------------------------------- | ------------- | -------------------------------- | -------------------------------- |
| UC-001   | Register a Customer Account                 | CU-01         | US-001                           | CAP-001                          |
| UC-002   | Book a Train Ticket                         | CU-02         | US-005 to US-024                 | CAP-014, 017, 018, 019, 020, 021, 025, 027, 028 |
| UC-003   | Retrieve a Ticket by PNR                    | CU-02         | US-025                           | CAP-024                          |
| UC-004   | Cancel a Booking                            | CU-02         | US-026 to US-028                 | CAP-014, 018, 021, 023, 025      |
| UC-005   | Configure Foundation Master Data            | ER-02         | US-030 to US-036                 | CAP-006, 007                     |
| UC-006   | Configure a Train Service                   | ER-03         | US-037 to US-045                 | CAP-008, 009                     |
| UC-007   | Configure Pricing Rules                     | ER-05         | US-046 to US-052                 | CAP-011, 012, 013                |
| UC-008   | Trigger Chart Preparation                   | ER-06         | US-053 to US-055                 | CAP-022                          |
| UC-009   | Manage Employee Accounts and Roles          | AD-01         | US-056 to US-058                 | CAP-002, 003                     |
| UC-010   | Automatic Seat Matrix Generation            | SY-01         | US-059 to US-061                 | CAP-015, 016                     |
| UC-011   | Waitlist Cascade on Cancellation            | SY-02         | US-029, US-062, US-063           | CAP-021                          |
| UC-012   | Notification Dispatch on Booking Events     | SY-02         | US-064 to US-068                 | CAP-029, 030                     |

**Total:** 12 use cases, 68 user stories.

### 10.2 Capability Coverage

Every capability from CAP-001 to CAP-030 is exercised by at least one use case or user story.

| Capability | Title                                              | Covered By                                                              |
| ---------- | -------------------------------------------------- | ----------------------------------------------------------------------- |
| CAP-001    | Customer Registration and Login                    | US-001, US-002, US-003, UC-001                                          |
| CAP-002    | Employee Authentication                            | US-056, US-057, UC-009                                                  |
| CAP-003    | Role-Based Access Control                          | US-057, US-058, UC-009                                                  |
| CAP-004    | Token Issuance, Refresh, and Revocation            | US-003, US-004                                                          |
| CAP-005    | Basic User Profile Management                      | UC-001, UC-009 (exercised through registration and account lifecycle)    |
| CAP-006    | Station Configuration                              | US-030, US-031, US-032, US-036, UC-005                                  |
| CAP-007    | Route and Stop Management with Distances           | US-033, US-034, US-035, US-036, UC-005                                  |
| CAP-008    | Train and Schedule Configuration                   | US-037 to US-041, US-044, US-045, UC-006                                |
| CAP-009    | Coach Composition and Berth Layout                 | US-042, US-043, UC-006                                                  |
| CAP-010    | Class and Quota Definition                         | US-042, US-046, UC-006 (exercised as precondition)                      |
| CAP-011    | Base Fare Configuration by Class                   | US-046, US-049, US-050, US-051, US-052, UC-007                          |
| CAP-012    | Dynamic Pricing Rule Configuration                 | US-047, US-051, UC-007                                                  |
| CAP-013    | Concession Rule Configuration                      | US-048, US-051, UC-007                                                  |
| CAP-014    | Fare Quote and Re-Quote Calculation                | US-009, US-014, US-023, US-024, US-027, UC-002, UC-004                  |
| CAP-015    | Seat Matrix Generation                             | US-059, US-060, UC-010                                                  |
| CAP-016    | Quota Allocation                                   | US-061, UC-010                                                          |
| CAP-017    | Seat Availability Enquiry                          | US-008, UC-002                                                          |
| CAP-018    | Seat Hold, Confirmation, and Release               | US-022, US-026, UC-002, UC-004                                          |
| CAP-019    | Booking Lifecycle State Management                 | US-011, US-013, US-020, UC-002                                          |
| CAP-020    | PNR Generation                                     | US-017, UC-002                                                          |
| CAP-021    | Waitlist Handling and Cascade                      | US-017, US-022, US-029, US-062, US-063, UC-011                          |
| CAP-022    | Chart Preparation                                  | US-053, US-054, US-055, UC-008                                          |
| CAP-023    | Ticket Cancellation                                | US-026, US-027, US-028, UC-004                                          |
| CAP-024    | Ticket and PNR Status Retrieval                    | US-018, US-025, UC-003                                                  |
| CAP-025    | Payment Initiation, Attempt Tracking, Verification | US-015, US-016, US-021, US-022, UC-002                                  |
| CAP-026    | Simulated Payment Processing and Result Callback   | US-022, UC-002                                                          |
| CAP-027    | Train Search by Route and Date                     | US-005, US-006, US-007, US-010, US-012, UC-002                          |
| CAP-028    | Unified Search Response Aggregation                | US-006, US-007, UC-002                                                  |
| CAP-029    | Booking Confirmation Notification                  | US-028, US-064, US-065, US-066, UC-012                                  |
| CAP-030    | Message Template Management, Delivery Logging, Retry | US-067, US-068, UC-012                                                |

**All 30 capabilities are covered.**

### 10.3 Coverage Notes

Three coverage observations are recorded here so that a reviewer sees a decision, not an omission.

**CAP-005 Basic User Profile Management.** The customer profile lifecycle is exercised through UC-001 (registration creates the initial profile) and through the account management behaviour that the customer performs outside the booking flow. Phase 1 does not include dedicated user stories for profile read, profile update, email change, password change, password reset, and account deletion. These functions are supported by [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software Requirements Specification (SRS) SR-011 to SR-017 and belong to [SRIS-P1-UI-003](../wave-3-detailed-design/SRIS-P1-UI-003_WireframesCustomerFlow.md) — Wireframes (Customer Flow) for their screens. A future revision of this document may add the corresponding stories if the UI documents require them as anchors.

**CAP-010 Class and Quota Definition.** The definition of travel classes and quotas is exercised as a precondition to UC-006 (train service setup) and UC-007 (pricing). Phase 1 does not include dedicated user stories for class creation and quota creation. These functions are supported by [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software Requirements Specification (SRS) SR-031 to SR-034 and belong to [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md) — Wireframes (Employee/Admin Flow). A future revision of this document may add the corresponding stories if the UI documents require them as anchors.

**ER-04 Composition Manager.** The Composition Manager role is defined in [Section 2.3](#23-employee-roles) with ownership of classes, quotas, coach composition, and berth layout. Phase 1 does not include dedicated user stories grouped under ER-04 in [Section 7](#7-employee-stories). The role's capabilities (CAP-009 and CAP-010) are exercised through UC-006 (train service setup), where the coach composition is configured, and through the precondition of UC-007 (pricing), where classes must exist before fare rules can be configured. These functions are supported by [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software Requirements Specification (SRS) SR-029 to SR-034 and belong to [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md) — Wireframes (Employee/Admin Flow). A future revision of this document may add the corresponding stories under ER-04 if the UI documents require them as anchors, or if the Composition Manager role is split from the Service Manager role in a later phase.

### 10.4 Story-to-Capability Index

| Story Range | Capability Range                       | Actor Group     |
| ----------- | -------------------------------------- | --------------- |
| US-001–004  | CAP-001, CAP-004                       | Customer        |
| US-005–012  | CAP-014, CAP-017, CAP-027, CAP-028     | Customer        |
| US-013–024  | CAP-013, CAP-014, CAP-019, CAP-020, CAP-021, CAP-023, CAP-025, CAP-026 | Customer |
| US-025–029  | CAP-014, CAP-018, CAP-021, CAP-023, CAP-024, CAP-029 | Customer |
| US-030–036  | CAP-006, CAP-007                       | Employee (ER-02) |
| US-037–045  | CAP-008, CAP-009                       | Employee (ER-03) |
| US-046–052  | CAP-011, CAP-012, CAP-013, CAP-014     | Employee (ER-05) |
| US-053–055  | CAP-022, CAP-023                       | Employee (ER-06) |
| US-056–058  | CAP-002, CAP-003                       | Administrator (AD-01, AD-02) |
| US-059–061  | CAP-015, CAP-016                       | System (SY-01)  |
| US-062–063  | CAP-021                                | System (SY-02)  |
| US-064–068  | CAP-029, CAP-030                       | System (SY-02)  |

### 10.5 Role-to-Document Index

| Role ID | Role Name              | Stories                        | Use Cases                            |
| ------- | ---------------------- | ------------------------------ | ------------------------------------ |
| CU-01   | Visitor                | US-001, US-002                 | UC-001                               |
| CU-02   | Registered Customer    | US-003 to US-029               | UC-002, UC-003, UC-004               |
| CU-03   | Passenger              | (domain entity — no stories)   | (referenced in UC-002)               |
| ER-01   | Operations Head        | (approval actions only)        | Secondary actor on UC-005 to UC-007  |
| ER-02   | Master Data Manager    | US-030 to US-036               | UC-005                               |
| ER-03   | Service Manager        | US-037 to US-045               | UC-006                               |
| ER-04   | Composition Manager    | (capability exercised via UC-006) | UC-006                             |
| ER-05   | Pricing Manager        | US-046 to US-052               | UC-007                               |
| ER-06   | Operations Manager     | US-053 to US-055               | UC-008                               |
| AD-01   | Super Admin            | US-056, US-057                 | UC-009                               |
| AD-02   | Audit Officer          | US-058                         | None                                 |
| SY-01   | Scheduled Job          | US-059 to US-061               | UC-010                               |
| SY-02   | Event Consumer         | US-062 to US-068               | UC-011, UC-012                       |
| SY-03   | Batch Process          | (deferred to future revision)  | None                                 |

---

## 11. Approval

| Role           | Name        | Decision | Date       |
| -------------- | ----------- | -------- | ---------- |
| Lead Architect | Koushal Jha | Approved | 2026-10-15 |

---

## Revision History

| Version | Date       | Author      | Change           |
| ------- | ---------- | ----------- | ---------------- |
| 1.0     | 2026-10-15 | Koushal Jha | Initial release. |

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
| 1.1  | [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md)                                          | Glossary and Domain Dictionary                    | 1    | P0  | UNBLOCK |
| 1.2  | [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md)                                     | Business Requirements Document (BRD)              | 1    | P0  | UNBLOCK |
| 1.3  | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)                                               | Capability Catalog (Final)                        | 1    | P0  | UNBLOCK |
| 1.4  | [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md)                                 | Software Requirements Specification (SRS)         | 1    | P0  | UNBLOCK |
| 1.5  | [SRIS-P1-REQ-005](./SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md)                                    | Non-Functional Requirements (ISO 25010)           | 1    | P0  | UNBLOCK |
| 1.7  | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)                                          | Domain Rules: Fare Calculation                    | 1    | P1  | FOLLOW  |
| 1.8  | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)                                                | Domain Rules: Ticketing                           | 1    | P1  | FOLLOW  |
| 1.9  | [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)                                  | Domain Rules: Waitlist and Cancellation           | 1    | P1  | FOLLOW  |
| 1.10 | [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md)                                         | Domain Rules: Chart Preparation                   | 1    | P1  | FOLLOW  |
| 1.11 | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)                                   | Domain Rules: Seat Matrix and Inventory           | 1    | P1  | FOLLOW  |
| 1.12 | [SRIS-P1-REQ-012](./SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md)                                    | Requirement Traceability Matrix (RTM)             | 1    | P2  | FOLLOW  |
| 2.1  | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)                  | Microservices Identification                      | 2    | P0  | UNBLOCK |
| 3.14 | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)                  | API Contract Document (OpenAPI)                   | 3    | P0  | UNBLOCK |
| 3.16 | [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md)                 | Event Schema Document (AsyncAPI)                  | 3    | P0  | UNBLOCK |
| 3.18 | [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md)      | Idempotency and Retry Policy Specification        | 3    | P0  | UNBLOCK |
| 3.19 | [SRIS-P1-API-006](../wave-3-detailed-design/SRIS-P1-API-006_APIErrorCodeCatalog.md)                         | API Error Code Catalog                            | 3    | P1  | FOLLOW  |
| 3.27 | [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md)                      | UI/UX Requirements Document                       | 3    | P0  | UNBLOCK |
| 3.29 | [SRIS-P1-UI-003](../wave-3-detailed-design/SRIS-P1-UI-003_WireframesCustomerFlow.md)                        | Wireframes (Customer Flow)                        | 3    | P0  | UNBLOCK |
| 3.30 | [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md)                   | Wireframes (Employee/Admin Flow)                  | 3    | P0  | UNBLOCK |
| 3.34 | [SRIS-P1-UI-008](../wave-3-detailed-design/SRIS-P1-UI-008_UIErrorAndNotificationDisplayRules.md)            | UI Error and Notification Display Rules           | 3    | P1  | FOLLOW  |
| 3.39 | [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)        | Authentication and Authorization Design           | 3    | P1  | FOLLOW  |
| 3.40 | [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md)                                   | RBAC Matrix                                       | 3    | P1  | FOLLOW  |
| 3.41 | [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)                      | JWT Token Design and Claims                       | 3    | P1  | FOLLOW  |
| 3.47 | [SRIS-P1-SEC-009](../wave-3-detailed-design/SRIS-P1-SEC-009_PasswordAndCredentialPolicy.md)                 | Password and Credential Policy                    | 3    | P2  | FOLLOW  |
| 3.5  | [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)            | Physical Database Schema Document                 | 3    | P0  | UNBLOCK |
| 3.12 | [SRIS-P1-DATA-012](../wave-3-detailed-design/SRIS-P1-DATA-012_SeedDataAndReferenceDataSpecification.md)     | Seed Data and Reference Data Specification        | 3    | P2  | FOLLOW  |
| 4.3  | [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)                                | Test Cases (Functional)                           | 4    | P0  | UNBLOCK |
| 4.7  | [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md)                                       | Test Cases (UI)                                   | 4    | P1  | FOLLOW  |
| 5.14 | [SRIS-P1-OPS-003](../wave-5-devops-operations/SRIS-P1-OPS-003_MonitoringAndAlertingGuide.md)                 | Monitoring and Alerting Guide                     | 5    | P1  | FOLLOW  |

### B.2 Documents That Reference This Document

| Seq  | Document ID                                                                                | Document Name                                 | Why It References                                                              |
| ---- | ------------------------------------------------------------------------------------------ | --------------------------------------------- | ------------------------------------------------------------------------------ |
| 0.0  | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) | Documentation Index and Navigation Map | Lists this document in the register and in the reading paths                  |
| 1.4  | [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md)                  | Software Requirements Specification (SRS) | Names this document as a downstream consumer of its requirements             |

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
| 1.3 | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)                                | Capability Catalog (Final)             | Hard            |
| 1.4 | [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md)                  | Software Requirements Specification (SRS) | Hard         |
| 1.5 | [SRIS-P1-REQ-005](./SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md)                     | Non-Functional Requirements (ISO 25010) | Hard           |
| 2.1 | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)             | Microservices Identification           | Soft            |

### B.4 Documents This Document Unblocks (Downstream)

| Seq  | Document ID                                                                      | Document Name                                | Blocked Until |
| ---- | -------------------------------------------------------------------------------- | -------------------------------------------- | ------------- |
| 1.12 | [SRIS-P1-REQ-012](./SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md)            | Requirement Traceability Matrix (RTM)        | This approved |
| 3.27 | [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md) | UI/UX Requirements Document               | This approved |
| 3.28 | [SRIS-P1-UI-002](../wave-3-detailed-design/SRIS-P1-UI-002_ScreenInventoryAndNavigationMap.md) | Screen Inventory and Navigation Map  | This approved |
| 3.29 | [SRIS-P1-UI-003](../wave-3-detailed-design/SRIS-P1-UI-003_WireframesCustomerFlow.md)   | Wireframes (Customer Flow)                | This approved |
| 3.30 | [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md) | Wireframes (Employee/Admin Flow)       | This approved |
| 4.3  | [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)         | Test Cases (Functional)                   | This approved |
| 4.7  | [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md)                | Test Cases (UI)                           | This approved |
| 8.7  | [SRIS-P1-USR-007](../wave-8-user-support/SRIS-P1-USR-007_DemoScenariosAndWalkthroughScript.md) | Demo Scenarios and Walkthrough Script | This approved |

### B.5 Master Documentation Index

The complete list of Phase 1 documents is in [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

### B.6 External Reference Documents

| Reference Type                        | Where It Is Documented                                                                                                                  |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| ISO/IEC/IEEE 29148:2018               | Systems and software engineering — Life cycle processes — Requirements engineering. Referenced for requirement quality rules and the definition of verifiability. |
| Mike Cohn, "User Stories Applied"     | Addison-Wesley, 2004. Referenced for the canonical three-part user story form.                                                          |
| Bill Wake, "INVEST in Good Stories, and SMART Tasks" | XP Magazine, 2003. Referenced for the INVEST criteria.                                                                    |
| Ivar Jacobson, "Use-Case 2.0"         | Ivar Jacobson International, 2011. Referenced for the use case structure and the slicing pattern that relates stories to use cases.      |
| Alistair Cockburn, "Writing Effective Use Cases" | Addison-Wesley, 2000. Referenced for the use case format with main flow and alternate flows.                                  |

### B.7 Document Conventions

The conventions for Priority and Tag values are defined in [Section 9](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md#9-vocabulary-standards) of [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.

---

**End of Document**