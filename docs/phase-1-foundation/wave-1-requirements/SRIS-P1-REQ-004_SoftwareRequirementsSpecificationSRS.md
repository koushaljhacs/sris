<div align="center">

![Wave](https://img.shields.io/badge/Wave-1-0550AE?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-REQ-6e7781?style=for-the-badge)

</div>

# Software Requirements Specification (SRS)

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** 1.0 | **Date:** 2026-10-14 | **Document ID:** SRIS-P1-REQ-004

| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| Title              | Software Requirements Specification (SRS)                         |
| Software           | SRIS                                                              |
| Software Full Form | Sarathi Railway Information System                                |
| Team Codename      | Project Sarathi                                                   |
| Document ID        | SRIS-P1-REQ-004                                                   |
| Task               | Specify the software requirements that Phase 1 must satisfy       |
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
2. [Software Requirements Model](#2-software-requirements-model)
   - [2.1 What a Software Requirement Is](#21-what-a-software-requirement-is)
   - [2.2 The Format of a Software Requirement](#22-the-format-of-a-software-requirement)
   - [2.3 Failure Paths](#23-failure-paths)
   - [2.4 Traceability Fields](#24-traceability-fields)
3. [Identity and Access](#3-identity-and-access)
4. [Railway Master Data](#4-railway-master-data)
5. [Fare and Pricing](#5-fare-and-pricing)
6. [Inventory and Quota](#6-inventory-and-quota)
7. [Booking and Ticketing](#7-booking-and-ticketing)
8. [Payment](#8-payment)
9. [Search and Discovery](#9-search-and-discovery)
10. [Notification](#10-notification)
11. [User Surface Requirements](#11-user-surface-requirements)
12. [Cross-Cutting Software Requirements](#12-cross-cutting-software-requirements)
13. [Traceability](#13-traceability)
14. [Approval](#14-approval)

- [Revision History](#revision-history)
- [Appendix A: Not Applicable](#appendix-a-not-applicable)
- [Appendix B: Related Documents](#appendix-b-related-documents)

---

## 1. Introduction

### 1.1 Purpose

This document is the Software Requirements Specification (SRS) of Phase 1 of SRIS (Sarathi Railway Information System). It states, in software terms, what the six microservices and the two user-facing surfaces must do. Each software requirement is stated so that a reader can verify it by observing the system from the outside, without inspecting the source code.

This document translates the capabilities recorded in [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final) into software requirements, and traces each one to the business requirement recorded in [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD). It does not repeat the domain rules, the design, the API contracts, the data schemas, the UI layouts, or the test cases, each of which belongs to another document and is cited here.

### 1.2 Scope

**In scope**

- The definition and format of a software requirement in SRIS.
- The software requirements for each of the eight capability domains.
- The software requirements specific to the two user-facing surfaces.
- The software requirements that apply across services.
- The failure path of every requirement that can fail.
- The traceability of every software requirement to its capability and business requirement.

**Out of scope**

- The business requirements, which are defined in [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD).
- The capabilities and their identifiers, which are defined in [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final).
- Non-functional requirements and quality attributes, which are defined in [SRIS-P1-REQ-005](./SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md) — Non-Functional Requirements (ISO 25010).
- User stories and use cases, which are defined in [SRIS-P1-REQ-006](./SRIS-P1-REQ-006_UserStoriesAndUseCases.md) — User Stories and Use Cases.
- The domain rules for fare, ticketing, waitlist and cancellation, chart preparation, and seat matrix and inventory, which are defined in [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) to [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md).
- The full cross-wave Requirement Traceability Matrix, which belongs to [SRIS-P1-REQ-012](./SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md) — Requirement Traceability Matrix (RTM).
- The service catalogue and the service boundaries, which are defined in [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification.
- The inter-service communication design, which is defined in [SRIS-P1-ARCH-009](../wave-2-architecture/SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md) — Service Interaction and Communication Design.
- The distributed transaction and saga design, which is defined in [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md) — Distributed Transaction and Saga Pattern Design.
- The concurrency and locking strategy, which is defined in [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md) — Distributed Concurrency and Locking Strategy.
- The API contracts, which are defined in [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md) — API Contract Document (OpenAPI) and [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md) — Event Schema Document (AsyncAPI).
- The database schemas and data models, which are defined in [SRIS-P1-DATA-002](../wave-3-detailed-design/SRIS-P1-DATA-002_LogicalDataModelPerService.md) — Logical Data Model (per service) and [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md) — Physical Database Schema Document.
- The UI screens and wireframes, which are defined in [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md) to [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md).
- The authentication, authorisation, RBAC, and token design, which are defined in [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md), [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md), and [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md).
- The test cases, which are defined in [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md) — Test Cases (Functional).

### 1.3 Audience

- **Lead Architect:** maintains this document and approves every software requirement.
- **Backend and frontend developers:** build against the software requirements, with the design, API, and data documents as the second-level reference.
- **Tester (QA):** derives the functional test cases in [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md) — Test Cases (Functional) from this document.
- **Project supervisor and evaluator:** uses this document as the definitive statement of what the software must do.
- **Technical reviewers:** engineers or interviewers who open the repository and need the software baseline of Phase 1.

### 1.4 Terminology and Conventions

Every term in this document has the meaning recorded in [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary. The terms below are used with the meanings defined there and are not repeated in full.

| Term                     | Meaning                                                                                          |
| ------------------------ | ------------------------------------------------------------------------------------------------ |
| Software requirement     | A statement of what the software must do, stated so that it can be verified from outside.         |
| Capability               | An enduring business ability that a software requirement realises.                                |
| Business requirement     | A statement of a business need that a capability fulfils.                                          |
| Failure path             | The specified behaviour of the software when a requirement cannot complete on its success path.   |
| Cross-cutting requirement| A software requirement that applies to two or more services rather than to one.                  |
| Surface requirement      | A software requirement specific to the Customer Booking Website or the Employee Admin Console.    |

The identifier prefixes below are local to this document.

| Prefix | Meaning                            |
| ------ | ---------------------------------- |
| SR     | Software requirement               |

Local prefixes from other documents that appear in citations are defined in those documents.

This document follows the standards below.

- [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard, for structure, header, and style.
- [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md) — Document ID and Category Scheme, for the Document ID.
- [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md) — Document Cross-Reference Standard, for citations and links.

---

## 2. Software Requirements Model

### 2.1 What a Software Requirement Is

A software requirement states what the software must do. It is stated so that a reader can verify it by observing the system from outside: by supplying inputs and checking the resulting outputs, without inspecting the source code.

A software requirement is distinct from the following.

- **Business requirement.** A business requirement states a need of the business. A software requirement states what the software must do to satisfy that need. Business requirements belong to [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD).
- **Capability.** A capability is a business ability. A software requirement is a specific observable behaviour that realises part of that ability. Capabilities belong to [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final).
- **Domain rule.** A domain rule is a policy, calculation, or state definition that remains true irrespective of the software that enforces it. A domain rule belongs to [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) to [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md). A software requirement cites the domain rule and states the software behaviour that enforces it.
- **Design decision.** A design decision records how a capability is realised: which algorithm, which data structure, which protocol, which pattern. Design decisions belong to the ARCH category.
- **User story.** A user story frames a goal from the actor's perspective. User stories belong to [SRIS-P1-REQ-006](./SRIS-P1-REQ-006_UserStoriesAndUseCases.md) — User Stories and Use Cases.

**The verification test.** An item is a software requirement when it can be verified by observing the system from outside. If verifying the item requires inspecting the source code, the database schema, or the internal data structures, the item is not a software requirement.

### 2.2 The Format of a Software Requirement

A software requirement in this document has the following form. **SR-NNN:** `<behaviour, stated as a requirement>`

**On failure or exhaustion:**

- **Capability:** CAP-NNN
- **Business Requirement:** BR-NN
- **Rules Owner:** SRIS-P1-REQ-XXX
- **Design Owner:** SRIS-P1-XXX-NNN
- **Test Owner:** SRIS-P1-TEST-003

Each field is required.

- **SR-NNN** is a stable identifier. It is never reused.
- **The behaviour statement** is a single sentence or a short paragraph. It describes what the system does when the requirement succeeds.
- **The failure path** is required for any requirement that can fail. If the requirement cannot fail on its success path, the field states "None".
- **Capability** cites the CAP-NNN identifier from [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final).
- **Business Requirement** cites the BR identifier from [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD).
- **Rules Owner** cites the document that owns the detailed rule, where one exists. If the requirement does not touch a domain rule, the field states "None".
- **Design Owner** cites the document that will own the design realisation of this requirement.
- **Test Owner** cites the document that will own the test case for this requirement.

### 2.3 Failure Paths

Every requirement that can fail states its failure path. The failure path describes the observable behaviour of the system when the success path cannot complete.

Failure path coverage is required because a requirement that specifies only the success path cannot be tested for its full behaviour. A system whose failure paths are unspecified will produce unpredictable results and refund disputes, and will not pass a functional test suite built from this document.

Examples of failure path categories in SRIS:

- **Validation failure.** Input does not meet the rule. The system returns an error response and no state change occurs.
- **Not found.** A requested entity does not exist. The system returns a not-found response.
- **Unavailable.** A seat, a station, or a schedule is not available. The system returns the appropriate waitlist or refund path.
- **Timeout.** A synchronous dependency does not respond within the configured timeout. The system returns a timeout response and preserves state.
- **Conflict.** A concurrent request has changed the state. The system rejects the second request with a conflict response.
- **Internal failure.** An unhandled condition occurs. The system returns an internal-error response, preserves state, and emits an event for observability.

The exact failure envelope (status codes, error payload shape, idempotency semantics) belongs to [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md) — API Contract Document (OpenAPI) and [SRIS-P1-API-006](../wave-3-detailed-design/SRIS-P1-API-006_APIErrorCodeCatalog.md) — API Error Code Catalog.

### 2.4 Traceability Fields

Every software requirement carries three traceability fields. Together they link the requirement to its origin and its destination.

**Backward traceability:**

- **Capability** links the requirement to the business ability it realises, in [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final).
- **Business Requirement** links the requirement to the business need it satisfies, in [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD).

**Forward traceability:**

- **Rules Owner** links the requirement to the document that owns the detailed rule.
- **Design Owner** links the requirement to the document that will own its realisation.
- **Test Owner** links the requirement to the document that will own its verification.

The full cross-wave matrix, which spans every document in the register, belongs to [SRIS-P1-REQ-012](./SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md) — Requirement Traceability Matrix (RTM). The matrix in [Section 13](#13-traceability) of this document is local to this document and lists only the SR-to-CAP-and-BR mapping.

---

## 3. Identity and Access

This section records the software requirements for the Identity and Access capability domain. The domain is owned by S1 IAM Service. The capabilities covered are CAP-001 to CAP-005 in [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final).

The detailed design of authentication, RBAC, and token handling belongs to [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md) — Authentication and Authorization Design, [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md) — RBAC Matrix, and [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md) — JWT Token Design and Claims. It is not defined here.

---

**SR-001: Customer Registration**

The system must allow an unauthenticated customer to submit a registration request that contains a valid email address, a password, and the required profile fields. On success, the system must create a customer account in a pending state, return a confirmation response, and dispatch a verification email through the notification channel.

**On failure or exhaustion:** If the email address is already registered, the system must return a conflict response and must not create an account. If the password does not meet the minimum rule defined in [SRIS-P1-SEC-009](../wave-3-detailed-design/SRIS-P1-SEC-009_PasswordAndCredentialPolicy.md) — Password and Credential Policy, the system must return a validation response naming the failing rule. If the notification channel does not respond, the account is created and the email is queued for retry; the customer is told the account exists and the email is delayed.

**Capability:** CAP-001
**Business Requirement:** BR-1
**Rules Owner:** [SRIS-P1-SEC-009](../wave-3-detailed-design/SRIS-P1-SEC-009_PasswordAndCredentialPolicy.md)
**Design Owner:** [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-002: Customer Email Verification**

The system must allow a customer to verify a registered email address by opening a signed verification link within a bounded window. On success, the account moves from pending to active, and the customer can log in.

**On failure or exhaustion:** If the verification token is expired, already used, or malformed, the system must return an invalid-link response and offer a re-send action. If the re-send is requested, the system issues a new signed link and invalidates the previous one.

**Capability:** CAP-001
**Business Requirement:** BR-1
**Rules Owner:** [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)
**Design Owner:** [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-003: Customer Login**

The system must allow an active customer to submit login credentials and, on valid credentials, issue an access token and a refresh token.

**On failure or exhaustion:** If credentials are invalid, the system must return an authentication-failed response that does not reveal whether the email or the password was wrong. After a configurable number of consecutive failures, the system must temporarily lock the account and return a locked-account response with the unlock time. If the account is in pending state, the system must return a pending-verification response.

**Capability:** CAP-001, CAP-004
**Business Requirement:** BR-1
**Rules Owner:** [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)
**Design Owner:** [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-004: Customer Logout**

The system must allow an authenticated customer to log out. On success, the current access token is invalidated and the associated refresh token is revoked.

**On failure or exhaustion:** If the token presented at logout is already invalid, the system returns a success response to keep logout idempotent.

**Capability:** CAP-004
**Business Requirement:** BR-1
**Rules Owner:** [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)
**Design Owner:** [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-005: Employee Login**

The system must allow an active employee to submit login credentials and, on valid credentials, issue an access token and a refresh token. The token carries the employee's role.

**On failure or exhaustion:** Failure handling follows SR-003.

**Capability:** CAP-002, CAP-004
**Business Requirement:** BR-2
**Rules Owner:** [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)
**Design Owner:** [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-006: Employee Logout**

The system must allow an authenticated employee to log out and must revoke the associated tokens.

**On failure or exhaustion:** Idempotent, as in SR-004.

**Capability:** CAP-004
**Business Requirement:** BR-2
**Rules Owner:** [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)
**Design Owner:** [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-007: Token Refresh**

The system must allow a client presenting a valid refresh token to obtain a new access token without re-entering credentials.

**On failure or exhaustion:** If the refresh token is expired, revoked, or malformed, the system must return an authentication-failed response and must not issue a new access token. If the refresh token was already used once, the system must revoke the entire session (refresh token rotation) and return a re-authentication-required response.

**Capability:** CAP-004
**Business Requirement:** BR-1, BR-2, BR-3
**Rules Owner:** [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)
**Design Owner:** [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-008: Token Validation on Every Protected Request**

The system must validate the access token presented on every protected endpoint before executing the endpoint's behaviour. Validation must include signature, expiry, issuer, and revocation status.

**On failure or exhaustion:** If validation fails, the system must return an authentication-failed response and must not execute the endpoint's behaviour.

**Capability:** CAP-004
**Business Requirement:** BR-1, BR-2, BR-3
**Rules Owner:** [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)
**Design Owner:** [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-009: Role-Based Access Enforcement**

The system must determine, from the claims in the access token, whether the authenticated caller holds a role that permits the requested action. If not, the system must not execute the action.

**On failure or exhaustion:** If the caller is not permitted, the system must return a forbidden response and must not execute the action. The response must not disclose the roles that would have permitted it.

**Capability:** CAP-003
**Business Requirement:** BR-3, BRL-7
**Rules Owner:** [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md)
**Design Owner:** [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-010: Employee Role Assignment by an Administrator**

The system must allow an employee holding the administrator role to assign a role to another employee's account. The assignment takes effect on the next token issue.

**On failure or exhaustion:** If the caller does not hold the administrator role, the system must return a forbidden response. If the target account does not exist or is inactive, the system must return a not-found response. If the role is not one of the roles defined in [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md) — RBAC Matrix, the system must return a validation response.

**Capability:** CAP-003
**Business Requirement:** BR-3
**Rules Owner:** [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md)
**Design Owner:** [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-011: Customer Profile Read**

The system must allow an authenticated customer to read their own profile.

**On failure or exhaustion:** If the caller requests a profile that does not belong to them, the system must return a forbidden response.

**Capability:** CAP-005
**Business Requirement:** BR-1, BR-4, BA-7
**Rules Owner:** None
**Design Owner:** [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-012: Customer Profile Update**

The system must allow an authenticated customer to update the editable fields of their own profile: display name, phone, and preferred language. The email and the login credentials are not editable through this requirement; they are handled by SR-013 and SR-014.

**On failure or exhaustion:** If any field fails validation, the system must return a validation response naming the failing field and must not apply the update. If the caller attempts to update a profile that does not belong to them, the system must return a forbidden response.

**Capability:** CAP-005
**Business Requirement:** BR-1, BR-4
**Rules Owner:** None
**Design Owner:** [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-013: Email Change with Verification**

The system must allow an authenticated customer to change the email address on their account. The change takes effect only after the customer verifies the new address through a signed link sent to it.

**On failure or exhaustion:** If the new email address is already in use, the system must return a conflict response. If the verification link expires or is not used within the configured window, the email change must be cancelled and the original email retained. The customer must be notified.

**Capability:** CAP-005
**Business Requirement:** BR-1, BR-4
**Rules Owner:** [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)
**Design Owner:** [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-014: Password Change**

The system must allow an authenticated customer to change their password by supplying the current password and a new password that meets the policy in [SRIS-P1-SEC-009](../wave-3-detailed-design/SRIS-P1-SEC-009_PasswordAndCredentialPolicy.md) — Password and Credential Policy. On success, all other active sessions for the account must be revoked.

**On failure or exhaustion:** If the current password is wrong, the system must return an authentication-failed response. If the new password does not meet the policy, the system must return a validation response naming the failing rule. In both cases the password is not changed.

**Capability:** CAP-005
**Business Requirement:** BR-1, BR-4
**Rules Owner:** [SRIS-P1-SEC-009](../wave-3-detailed-design/SRIS-P1-SEC-009_PasswordAndCredentialPolicy.md)
**Design Owner:** [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-015: Password Reset Request**

The system must allow an unauthenticated user to request a password reset by submitting an email address. On success, the system dispatches a signed reset link to that address.

**On failure or exhaustion:** The system must always return the same success response whether the email exists or not, to prevent account enumeration. If the notification channel does not respond, the request is queued for retry.

**Capability:** CAP-001, CAP-005
**Business Requirement:** BR-1
**Rules Owner:** [SRIS-P1-SEC-009](../wave-3-detailed-design/SRIS-P1-SEC-009_PasswordAndCredentialPolicy.md)
**Design Owner:** [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-016: Password Reset Completion**

The system must allow a user to complete a password reset by presenting a valid reset token and a new password that meets the policy. On success, the password is updated and all active sessions are revoked.

**On failure or exhaustion:** If the reset token is expired, already used, or malformed, the system must return an invalid-link response. If the new password does not meet the policy, the system returns a validation response. In both cases the password is not changed.

**Capability:** CAP-005
**Business Requirement:** BR-1
**Rules Owner:** [SRIS-P1-SEC-009](../wave-3-detailed-design/SRIS-P1-SEC-009_PasswordAndCredentialPolicy.md)
**Design Owner:** [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-017: Account Deletion Request**

The system must allow an authenticated customer to request the deletion of their account. On request, the account is marked for deletion and the customer is logged out from all sessions. Data handling follows [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md) — DPDP Act Compliance Framework (Phase 1 scoped).

**On failure or exhaustion:** If the customer has any confirmed or waitlisted booking that has not yet had its departure, the system must return a conflict response naming the blocking booking.

**Capability:** CAP-005
**Business Requirement:** BR-1, BR-4
**Rules Owner:** [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md)
**Design Owner:** [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-018: Consistent Error Envelope on Authentication Endpoints**

The system must return authentication errors in a consistent envelope across every endpoint in this section. The envelope's shape is defined in [SRIS-P1-API-006](../wave-3-detailed-design/SRIS-P1-API-006_APIErrorCodeCatalog.md) — API Error Code Catalog.

**On failure or exhaustion:** None. This requirement is itself the failure path convention.

**Capability:** CAP-001, CAP-002, CAP-003, CAP-004, CAP-005
**Business Requirement:** BR-1, BR-2, BR-3
**Rules Owner:** [SRIS-P1-API-006](../wave-3-detailed-design/SRIS-P1-API-006_APIErrorCodeCatalog.md)
**Design Owner:** [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

## 4. Railway Master Data

This section records the software requirements for the Railway Master Data capability domain. The domain is owned by S2 Master Data and Pricing Service. The capabilities covered are CAP-006 to CAP-010 in [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final).

The detailed data design belongs to [SRIS-P1-DATA-002](../wave-3-detailed-design/SRIS-P1-DATA-002_LogicalDataModelPerService.md) — Logical Data Model (per service) and [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md) — Physical Database Schema Document. It is not defined here.

Every requirement in this section is executed by an authenticated employee holding the master-data administration role defined in [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md) — RBAC Matrix. Role enforcement is by SR-009.

---

**SR-019: Station Creation**

The system must allow an authorised employee to create a station by submitting a unique station code, a name, and its network attributes. On success, the station is persisted and becomes available for use in routes and searches.

**On failure or exhaustion:** If the station code is already in use, the system must return a conflict response. If any field fails validation, the system must return a validation response naming the failing field.

**Capability:** CAP-006
**Business Requirement:** BR-5, BR-6, BRL-7
**Rules Owner:** None
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-020: Station Update**

The system must allow an authorised employee to update the name and network attributes of an existing station.

**On failure or exhaustion:** If the station does not exist, the system must return a not-found response. If the update attempts to change the station code to one already in use, the system must return a conflict response.

**Capability:** CAP-006
**Business Requirement:** BR-5, BR-6
**Rules Owner:** None
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-021: Station Deactivation**

The system must allow an authorised employee to deactivate an existing station. A deactivated station does not appear in new routes or in new train schedules.

**On failure or exhaustion:** If the station is referenced by an active train schedule, the system must return a conflict response naming the referring schedules.

**Capability:** CAP-006
**Business Requirement:** BR-5, BR-6
**Rules Owner:** None
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-022: Route Creation**

The system must allow an authorised employee to create a route as an ordered list of stations from origin to destination. Each route stop carries a cumulative distance in kilometres from the origin.

**On failure or exhaustion:** If any station in the list does not exist, the system must return a not-found response naming the missing station. If the cumulative distances are not strictly increasing, the system must return a validation response. If the origin and the destination are the same station, the system must return a validation response.

**Capability:** CAP-007
**Business Requirement:** BR-5, BR-6, BR-7
**Rules Owner:** None
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-023: Route Update**

The system must allow an authorised employee to update a route's stop list and cumulative distances.

**On failure or exhaustion:** If the route is referenced by an active train schedule and the update changes the sequence of stations or the distances, the system must return a conflict response naming the referring schedules. The system must not allow changes that silently alter existing booking distances.

**Capability:** CAP-007
**Business Requirement:** BR-5, BR-6, BR-7
**Rules Owner:** None
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-024: Route Stop Insertion**

The system must allow an authorised employee to insert an intermediate stop into an existing route and to supply its cumulative distance.

**On failure or exhaustion:** If the inserted distance is not between the distances of the adjacent stops, the system must return a validation response.

**Capability:** CAP-007
**Business Requirement:** BR-5, BR-6, BR-7
**Rules Owner:** None
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-025: Train Creation**

The system must allow an authorised employee to create a train by submitting a unique five-digit train number, a train name, and a train type.

**On failure or exhaustion:** If the train number is already in use, the system must return a conflict response. If the train type is not one of the values defined in [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary, the system must return a validation response.

**Capability:** CAP-008
**Business Requirement:** BR-5, BR-6, BR-7
**Rules Owner:** None
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-026: Train Update**

The system must allow an authorised employee to update a train's name and type.

**On failure or exhaustion:** If the train does not exist, the system must return a not-found response. The train number cannot be changed through this requirement.

**Capability:** CAP-008
**Business Requirement:** BR-5, BR-6
**Rules Owner:** None
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-027: Train Schedule Creation**

The system must allow an authorised employee to create a schedule for a train by binding a route, running days, and for every stop an arrival time, a departure time, and a halt duration.

**On failure or exhaustion:** If the train or the route does not exist, the system must return a not-found response. If any stop's departure precedes its arrival, or the halt duration does not equal the difference between arrival and departure, the system must return a validation response naming the stop.

**Capability:** CAP-008
**Business Requirement:** BR-5, BR-6, BR-7
**Rules Owner:** None
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-028: Train Schedule Update**

The system must allow an authorised employee to update a train schedule's running days and timings.

**On failure or exhaustion:** If the schedule has confirmed bookings on any future journey date and the update changes the timings of that journey, the system must return a conflict response naming the affected journey dates and offering to create a new schedule instead.

**Capability:** CAP-008
**Business Requirement:** BR-5, BR-6, BR-7
**Rules Owner:** None
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-029: Coach Composition Creation**

The system must allow an authorised employee to define the coach composition of a train as an ordered list of coaches, each with a coach type, a class, and a berth or seat layout.

**On failure or exhaustion:** If the coach type or the class is not a value defined in [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary, the system must return a validation response. If the total capacity of the coach composition exceeds the limits defined in the data model, the system must return a validation response.

**Capability:** CAP-009
**Business Requirement:** BR-6, BR-7
**Rules Owner:** None
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-030: Coach Composition Update**

The system must allow an authorised employee to update the coach composition of a train.

**On failure or exhaustion:** If any future journey of the train already has a generated seat matrix, the system must return a conflict response naming the affected journey dates and the range of days on which the change would be safe.

**Capability:** CAP-009
**Business Requirement:** BR-6, BR-7
**Rules Owner:** None
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-031: Travel Class Definition**

The system must allow an authorised employee to define a travel class by supplying a class code, a class name, an air-conditioned flag, and a base fare multiplier.

**On failure or exhaustion:** If the class code is already defined, the system must return a conflict response. If the multiplier is not a positive number, the system must return a validation response.

**Capability:** CAP-010
**Business Requirement:** BR-5, BR-6, BR-7
**Rules Owner:** [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-032: Travel Class Update**

The system must allow an authorised employee to update a travel class's name and multiplier.

**On failure or exhaustion:** If the class is referenced by an active coach composition and the update changes the multiplier, the system must return a conflict response naming the referring coaches and offering the current effective date for the change.

**Capability:** CAP-010
**Business Requirement:** BR-5, BR-6, BR-7
**Rules Owner:** [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-033: Quota Definition**

The system must allow an authorised employee to define a quota by supplying a quota code, a quota name, and the class or classes to which it applies.

**On failure or exhaustion:** If the quota code is already defined for the same class, the system must return a conflict response. If the quota code is not one of the values recorded in [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary, the system must return a validation response unless the employee holds the quota-extension role defined in [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md) — RBAC Matrix.

**Capability:** CAP-010
**Business Requirement:** BR-5, BR-6, BR-7
**Rules Owner:** [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-034: Quota Update**

The system must allow an authorised employee to update a quota's name.

**On failure or exhaustion:** If the quota is currently in use by an active seat matrix, the system must return a conflict response. The quota code cannot be changed.

**Capability:** CAP-010
**Business Requirement:** BR-5, BR-6
**Rules Owner:** [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-035: Master Data Change Audit**

The system must record an audit entry for every master-data change made under SR-019 to SR-034. Each entry records the employee who made the change, the entity changed, the before and after values, and the timestamp. Audit records are readable by the audit role defined in [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md) — RBAC Matrix.

**On failure or exhaustion:** If the audit record cannot be written, the master-data change must be rejected and rolled back.

**Capability:** CAP-006, CAP-007, CAP-008, CAP-009, CAP-010
**Business Requirement:** BR-5, BR-6, BR-7
**Rules Owner:** [SRIS-P1-SEC-012](../wave-3-detailed-design/SRIS-P1-SEC-012_DataClassificationRegister.md)
**Design Owner:** [SRIS-P1-DATA-001](../wave-3-detailed-design/SRIS-P1-DATA-001_DataDesignDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

## 5. Fare and Pricing

This section records the software requirements for the Fare and Pricing capability domain. The domain is owned by S2 Master Data and Pricing Service. The capabilities covered are CAP-011 to CAP-014 in [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final).

The detailed fare calculation rules belong to [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) — Domain Rules: Fare Calculation. They are not repeated here. The requirements below state the software behaviour that invokes those rules and returns their results.

---

**SR-036: Base Fare Rule Configuration**

The system must allow an authorised employee to configure a base fare rule for a class. The rule includes a base rate per kilometre, a set of distance slabs, the class multiplier, and the applicable taxes and service charges, as specified in [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) — Domain Rules: Fare Calculation.

**On failure or exhaustion:** If the distance slabs overlap or leave a gap, the system must return a validation response naming the problematic slab. If any rate is negative, the system must return a validation response.

**Capability:** CAP-011
**Business Requirement:** BR-5, BR-6, BR-8
**Rules Owner:** [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-037: Base Fare Rule Retrieval**

The system must return the currently effective base fare rule for a requested class and date.

**On failure or exhaustion:** If no rule is in effect for the requested class on the requested date, the system must return a configuration-error response, and the calling service must refuse the fare request rather than returning zero.

**Capability:** CAP-011
**Business Requirement:** BR-6, BR-8
**Rules Owner:** [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)
**Design Owner:** [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-038: Dynamic Pricing Rule Configuration**

The system must allow an authorised employee to configure a dynamic pricing rule for a class or a quota. The rule defines the percentage increments applied to the fare as the available seat inventory depletes, as specified in [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) — Domain Rules: Fare Calculation.

**On failure or exhaustion:** If the configured increments would ever produce a fare lower than the base fare, the system must return a validation response. If two rules overlap for the same class and quota, the system must return a conflict response.

**Capability:** CAP-012
**Business Requirement:** BR-5, BR-6, BR-8
**Rules Owner:** [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-039: Concession Rule Configuration**

The system must allow an authorised employee to configure a concession rule for a passenger category. The rule defines the eligibility criteria and the percentage reduction, as specified in [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) — Domain Rules: Fare Calculation.

**On failure or exhaustion:** If the reduction is outside the range permitted by the domain rule, the system must return a validation response. If two concession rules overlap for the same passenger category, the system must return a conflict response unless the domain rule permits stacking.

**Capability:** CAP-013
**Business Requirement:** BR-6, BR-8
**Rules Owner:** [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-040: Fare Quote for Search**

The system must return a fare quote for a requested train, class, quota, journey segment, and journey date. The quote is informational and does not lock the price. The quote must be computed from the currently effective fare rules, without applying passenger-specific concessions.

**On failure or exhaustion:** If no fare rule is in effect for the requested class and date, the system must return a configuration-error response. If the train, the class, or the quota does not exist, the system must return a not-found response.

**Capability:** CAP-014
**Business Requirement:** BR-8, BRL-3
**Rules Owner:** [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)
**Design Owner:** [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-041: Fare Re-Quote at Booking**

The system must return an authoritative fare re-quote at booking time. The re-quote must incorporate the passenger details, the applicable concessions, the applicable quotas, and the currently effective dynamic pricing state. The booking must use the re-quote amount and must not use the fare quote returned by search.

**On failure or exhaustion:** If a passenger fails the eligibility criteria for a concession, the re-quote must exclude that concession and return a note naming the excluded passenger. If the total amount differs from the amount shown during search, the re-quote must return both amounts so the client can present the difference to the customer.

**Capability:** CAP-014
**Business Requirement:** BR-8, BRL-3
**Rules Owner:** [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)
**Design Owner:** [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-042: Concession Application**

The system must apply the highest-value concession for which a passenger is eligible when more than one concession could apply and the domain rule does not permit stacking.

**On failure or exhaustion:** If no concession applies, the system must apply none and return the standard fare. If the passenger's declared category cannot be verified at booking time, the concession must be applied with the verification-required flag set on the booking, and the booking must be marked as requiring verification at boarding.

**Capability:** CAP-013, CAP-014
**Business Requirement:** BR-8
**Rules Owner:** [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)
**Design Owner:** [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-043: Dynamic Pricing Application**

The system must apply the dynamic pricing rule, if any, to the fare at the moment of the fare re-quote under SR-041. The applied increment must be returned as part of the re-quote response with a reference to the rule that produced it.

**On failure or exhaustion:** If the dynamic pricing rule references an inventory count that is not available at the moment of the re-quote, the system must return the base fare without the dynamic increment and must log the missing inventory reference. The booking is not blocked.

**Capability:** CAP-012, CAP-014
**Business Requirement:** BR-8
**Rules Owner:** [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)
**Design Owner:** [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-044: Tax and Service Charge Application**

The system must compute taxes and service charges on the fare re-quote according to the configured tax rules. Taxes and service charges must appear as separate line items in the re-quote response.

**On failure or exhaustion:** If a required tax configuration is missing for the requested class or date, the system must return a configuration-error response and must not return a re-quote.

**Capability:** CAP-011, CAP-014
**Business Requirement:** BR-8
**Rules Owner:** [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)
**Design Owner:** [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-045: Refund Calculation on Cancellation**

The system must return a refund amount when a customer cancels a booking. The refund amount is computed from the fare rules in effect for the cancelled journey, less the applicable charges per [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) — Domain Rules: Fare Calculation.

**On failure or exhaustion:** If the cancellation is attempted after the journey departure, the system must return a not-allowed response and no refund is calculated. If the fare rule that applied at booking time is no longer in effect, the system must use the archived rule that was in effect at booking time and must note the archived rule reference in the response.

**Capability:** CAP-014
**Business Requirement:** BR-8, BR-23
**Rules Owner:** [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)
**Design Owner:** [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-046: Fare Configuration Audit**

The system must record an audit entry for every fare, dynamic pricing, and concession configuration change made under SR-036, SR-038, and SR-039. Each entry records the employee who made the change, the rule changed, the before and after values, and the timestamp. Audit records are readable by the audit role defined in [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md) — RBAC Matrix.

**On failure or exhaustion:** If the audit record cannot be written, the configuration change must be rejected and rolled back.

**Capability:** CAP-011, CAP-012, CAP-013
**Business Requirement:** BR-5, BR-6, BR-8
**Rules Owner:** [SRIS-P1-SEC-012](../wave-3-detailed-design/SRIS-P1-SEC-012_DataClassificationRegister.md)
**Design Owner:** [SRIS-P1-DATA-001](../wave-3-detailed-design/SRIS-P1-DATA-001_DataDesignDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

## 6. Inventory and Quota

This section records the software requirements for the Inventory and Quota capability domain. The domain is owned by S3 Reservation Service, in the Inventory module. The capabilities covered are CAP-015 to CAP-018 in [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final).

The detailed rules for the seat matrix, quota allocation, and seat lifecycle belong to [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md) — Domain Rules: Seat Matrix and Inventory. The mechanism by which a selected seat is protected during booking is decided in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing. The concurrency controls that prevent double-allocation belong to [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md) — Distributed Concurrency and Locking Strategy. None of these are defined here.

The requirements below state the observable behaviour that invokes those rules and returns their results.

---

**SR-047: Seat Matrix Generation**

The system must generate the seat matrix for a scheduled train journey from the master data schedule and the coach composition. Generation must occur automatically when the first seat request is made for a journey date that falls within the configured generation window, and it may also be triggered manually by an authorised employee.

**On failure or exhaustion:** If the master data for the train, route, or coach composition is incomplete, the system must return a configuration-error response and must not generate a partial matrix. If a matrix already exists for the same train and journey date, the system must return a conflict response and must not regenerate it.

**Capability:** CAP-015
**Business Requirement:** BR-14
**Rules Owner:** [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)
**Design Owner:** [SRIS-P1-DATA-008](../wave-3-detailed-design/SRIS-P1-DATA-008_HighConcurrencySegmentInventoryDataModel.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-048: Seat Matrix Automatic Regeneration on Coach Composition Change**

When an authorised employee changes the coach composition of a train and the change affects journey dates that have not yet had a matrix generated, the system must apply the change to those future journeys.

**On failure or exhaustion:** If a journey date already has a generated matrix, the change must not apply to that date. The system must return a conflict response naming the affected dates as defined in SR-030.

**Capability:** CAP-015
**Business Requirement:** BR-14, BR-6
**Rules Owner:** [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)
**Design Owner:** [SRIS-P1-DATA-008](../wave-3-detailed-design/SRIS-P1-DATA-008_HighConcurrencySegmentInventoryDataModel.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-049: Quota Allocation on Generation**

When a seat matrix is generated, the system must partition its seats into the quotas defined for the train's classes, according to the quota allocation rules in [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md) — Domain Rules: Seat Matrix and Inventory.

**On failure or exhaustion:** If the sum of the quota allocations exceeds the total number of seats in any class, the system must return a configuration-error response and must not generate the matrix. If a quota allocation leaves fewer seats than the minimum reserve configured for the class, the system must return a configuration-error response.

**Capability:** CAP-016
**Business Requirement:** BR-14
**Rules Owner:** [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)
**Design Owner:** [SRIS-P1-DATA-008](../wave-3-detailed-design/SRIS-P1-DATA-008_HighConcurrencySegmentInventoryDataModel.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-050: Quota Reallocation Before Booking Opens**

The system must allow an authorised employee to change the quota allocation for a journey date on which no booking has yet been confirmed. Reallocation redistributes seats between quotas within the same class.

**On failure or exhaustion:** If any booking exists for the affected journey date, the system must return a conflict response. If the reallocation would reduce a quota below the number of seats already held by that quota on that date, the system must return a validation response.

**Capability:** CAP-016
**Business Requirement:** BR-14
**Rules Owner:** [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)
**Design Owner:** [SRIS-P1-DATA-008](../wave-3-detailed-design/SRIS-P1-DATA-008_HighConcurrencySegmentInventoryDataModel.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-051: Seat Availability Enquiry**

The system must return the current availability for a requested train, journey date, class, quota, and journey segment. The response must report the count of seats that can be allocated on the requested segment and the current state of any waitlist or pooled-waitlist queues for the same scope. The response must include the timestamp of the reading.

**On failure or exhaustion:** If no seat matrix exists for the requested train and date, the system must attempt to generate one under SR-047. If generation fails, the system must return a configuration-error response. If the requested train or class does not exist, the system must return a not-found response.

**Capability:** CAP-017
**Business Requirement:** BR-13
**Rules Owner:** [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)
**Design Owner:** [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-052: Seat Availability Enquiry for a Segment**

The system must return availability for a journey segment that begins at an intermediate station and ends at a station before the destination, computed against the seat matrix for the whole journey. Segment availability must reflect seats that are free on the requested segment regardless of occupancy on other segments.

**On failure or exhaustion:** If the requested segment is not a valid ordered pair of stops on the train's route, the system must return a validation response.

**Capability:** CAP-017
**Business Requirement:** BR-13
**Rules Owner:** [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)
**Design Owner:** [SRIS-P1-DATA-008](../wave-3-detailed-design/SRIS-P1-DATA-008_HighConcurrencySegmentInventoryDataModel.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-053: Seat Protection During a Booking Attempt**

The system must protect a selected seat from allocation to any other customer while the selecting customer completes their booking attempt. The mechanism and its time bound are decided in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing. This requirement states only the observable outcome: a protected seat must not be allocated to a different booking until the protection is released or converted.

**On failure or exhaustion:** If the requested seat cannot be protected because another customer holds it, the system must return a conflict response and must not proceed with the booking. If no seat of the requested class and quota can be protected, the system must return the appropriate waitlist or refusal response as defined by the mechanism in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md).

**Capability:** CAP-018
**Business Requirement:** BR-15, BRL-1
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-054: Seat Protection Release**

The system must release a protected seat according to the release rules in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing. This requirement states only the observable outcome: once released, the seat is available to other customers for the same journey segment and quota.

**On failure or exhaustion:** If the release is requested for a seat that is already released or already confirmed, the system must return a success response and must not change state. Release is idempotent.

**Capability:** CAP-018
**Business Requirement:** BR-15, BR-16, BRL-1
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-055: Seat Allocation on Confirmation**

When a booking is confirmed, the system must allocate the protected seat to the booking and record the coach number and berth or seat number on the passenger record. Allocation must be durable and must survive a service restart.

**On failure or exhaustion:** If the protected seat has been released by the protection mechanism before confirmation, the system must attempt to allocate an alternate seat of the same class and quota. If no alternate seat exists, the system must place the booking on the waitlist path defined by [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md) — Domain Rules: Waitlist and Cancellation, and initiate the refund path in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing.

**Capability:** CAP-018
**Business Requirement:** BR-15, BR-16, BRL-1
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-056: No Double Allocation of a Seat**

The system must never allocate the same physical seat on the same journey segment to two bookings that overlap on that segment.

**On failure or exhaustion:** None. This requirement is itself the invariant. It is enforced by the concurrency controls defined in [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md) — Distributed Concurrency and Locking Strategy.

**Capability:** CAP-018
**Business Requirement:** BRL-1
**Rules Owner:** [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)
**Design Owner:** [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md)
**Test Owner:** [SRIS-P1-TEST-009](../wave-4-testing/SRIS-P1-TEST-009_LoadTestPlan.md)

---

**SR-057: Seat Release on Cancellation**

When a booking is cancelled, the system must release the allocated seat back into the inventory for the same class and quota on the same journey segment, and the released seat must become available to other customers.

**On failure or exhaustion:** If the cancellation cannot be recorded, the system must not release the seat. If the seat is already released, the release is idempotent.

**Capability:** CAP-018
**Business Requirement:** BR-23, BRL-1
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-058: Inventory Change Audit**

The system must record an audit entry for every quota reallocation under SR-050 and for every manual seat matrix generation under SR-047. Each entry records the employee, the entity changed, the before and after values, and the timestamp.

**On failure or exhaustion:** If the audit record cannot be written, the change must be rejected and rolled back.

**Capability:** CAP-016
**Business Requirement:** BR-14
**Rules Owner:** [SRIS-P1-SEC-012](../wave-3-detailed-design/SRIS-P1-SEC-012_DataClassificationRegister.md)
**Design Owner:** [SRIS-P1-DATA-001](../wave-3-detailed-design/SRIS-P1-DATA-001_DataDesignDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

## 7. Booking and Ticketing

This section records the software requirements for the Booking and Ticketing capability domain. The domain is owned by S3 Reservation Service, in the Booking module. The capabilities covered are CAP-019 to CAP-024 in [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final).

The detailed rules for the booking lifecycle, PNR generation, cancellation, and payment handling belong to [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing. The rules for the waitlist, RAC, and cascade belong to [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md) — Domain Rules: Waitlist and Cancellation. The rules for chart preparation belong to [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md) — Domain Rules: Chart Preparation. The distributed transaction semantics belong to [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md) — Distributed Transaction and Saga Pattern Design. None of these are defined here.

The requirements below state the observable behaviour that invokes those rules and returns their results.

---

**SR-059: Booking Request Initiation**

The system must accept a booking request from an authenticated customer. The request names the train, journey date, class, quota, boarding station, destination station, and one or more passengers with their details.

**On failure or exhaustion:** If any required field is missing or fails validation, the system must return a validation response naming the failing field. If the customer's account is not active, the system must return a forbidden response. If the train, date, or class is not bookable, the system must return a not-found or not-bookable response.

**Capability:** CAP-019
**Business Requirement:** BR-20, BR-22
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-060: Booking Request Validation Against Master Data**

The system must validate every booking request against master data before proceeding: the train exists, the journey date falls on a running day, the boarding and destination stations are stops on the route in the correct order, the class exists on the train, and the quota applies to the class.

**On failure or exhaustion:** If any validation fails, the system must return a validation response naming the failing check and must not proceed. No seat protection is created and no payment is initiated.

**Capability:** CAP-019
**Business Requirement:** BR-20
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-API-004](../wave-3-detailed-design/SRIS-P1-API-004_IntegrationDesignDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-061: Fare Re-Quote Invocation**

The system must request an authoritative fare re-quote from the master data and pricing service for every booking request, using the passenger details and the quota of the request, before any payment is initiated.

**On failure or exhaustion:** If the re-quote cannot be obtained because the pricing service is unavailable, the system must return a service-unavailable response and must not proceed with the booking. The customer's hold, if one exists, is released per the rules in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing.

**Capability:** CAP-019, CAP-014
**Business Requirement:** BR-8, BRL-3
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-API-004](../wave-3-detailed-design/SRIS-P1-API-004_IntegrationDesignDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-062: Seat Protection Invocation**

For every booking request, the system must invoke the seat protection mechanism defined in SR-053 before initiating payment. The mechanism and its time bound are decided in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing.

**On failure or exhaustion:** If no seat of the requested class and quota can be protected, the system must either place the booking on the appropriate waitlist queue under SR-066 or return a refusal response and not proceed, according to the rules in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md).

**Capability:** CAP-018, CAP-019
**Business Requirement:** BR-15, BRL-1
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-063: Booking State Persistence Before Payment**

The system must persist the booking in an intermediate state before initiating payment. The intermediate state records the customer, the journey, the passengers, the protected seat reference, and the re-quoted amount. The intermediate state must survive a service restart.

**On failure or exhaustion:** If the booking cannot be persisted, the system must not initiate payment. Any protected seat is released.

**Capability:** CAP-019
**Business Requirement:** BR-20, BR-22
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-064: Booking Confirmation on Payment Success**

On a verified payment success callback for a booking in the intermediate state, the system must allocate the protected seat to the booking under SR-055, drive the booking to the confirmed state, and generate a PNR under SR-065.

**On failure or exhaustion:** If the protected seat has been released before the callback arrives, the system must attempt to allocate an alternate seat of the same class and quota. If none exists, the system must place the booking on the appropriate waitlist queue under SR-066 or initiate refund under SR-087, and must return an explicit failure response.

**Capability:** CAP-019, CAP-020
**Business Requirement:** BR-16, BR-20, BRL-2
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-065: PNR Generation**

On booking confirmation, the system must generate a unique ten-digit PNR and associate it with the booking and its passengers. The PNR format and uniqueness rules belong to [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing.

**On failure or exhaustion:** If a PNR cannot be generated, the system must not confirm the booking. The seat allocation must be reversed and the refund path under SR-087 must be initiated.

**Capability:** CAP-020
**Business Requirement:** BR-20, BRL-4
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-066: Waitlist Placement**

When no seat of the requested class and quota can be protected, and the booking is not refused outright, the system must place the booking on the appropriate waitlist queue. The queue category, the position assignment, and the cascade rules belong to [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md) — Domain Rules: Waitlist and Cancellation.

**On failure or exhaustion:** If all waitlist queues for the class and quota have reached their configured maximum length, the system must refuse the booking and must not initiate payment.

**Capability:** CAP-021
**Business Requirement:** BR-16a, BR-23
**Rules Owner:** [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-067: Waitlist Position Retrieval**

The system must return the current waitlist position for a booking that is on a waitlist queue.

**On failure or exhaustion:** If the PNR is not found or the booking is not on a waitlist queue, the system must return a not-found response.

**Capability:** CAP-021
**Business Requirement:** BR-23
**Rules Owner:** [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)
**Design Owner:** [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-068: Waitlist Cascade on Cancellation**

When a seat is released by cancellation under SR-057, the system must advance the waitlist queues according to the cascade rules in [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md) — Domain Rules: Waitlist and Cancellation. This requirement states only the observable outcome: a passenger who advances receives an updated booking status and is notified by the notification channel.

**On failure or exhaustion:** If a promoted passenger cannot be reached or the notification cannot be delivered, the promotion still stands. The notification is queued for retry under SR-097.

**Capability:** CAP-021
**Business Requirement:** BR-23, BRL-5
**Rules Owner:** [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)
**Design Owner:** [SRIS-P1-ARCH-009](../wave-2-architecture/SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-069: Waitlist Promotion Notification Event**

Every waitlist promotion must publish a domain event that names the booking, the new status, and the new position. The event schema belongs to [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md) — Event Schema Document (AsyncAPI).

**On failure or exhaustion:** If the event cannot be published, the promotion must not be committed. The system must retry publication and, on continued failure, must roll back the promotion and return the queue to its prior state.

**Capability:** CAP-021
**Business Requirement:** BR-23, BRL-5
**Rules Owner:** [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)
**Design Owner:** [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md)
**Test Owner:** [SRIS-P1-TEST-004](../wave-4-testing/SRIS-P1-TEST-004_ConsumerDrivenContractTestingStrategy.md)

---

**SR-070: Chart Preparation Trigger**

The system must execute chart preparation for a scheduled journey at the time configured for that journey. The chart window and the batch behaviour belong to [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md) — Domain Rules: Chart Preparation.

**On failure or exhaustion:** If the chart preparation cannot complete, the system must record the failure, must not partially commit chart state, and must retry at the next configured attempt. If the retry also fails, the Lead Architect must be notified through the operations alerting channel defined in [SRIS-P1-OPS-003](../wave-5-devops-operations/SRIS-P1-OPS-003_MonitoringAndAlertingGuide.md) — Monitoring and Alerting Guide.

**Capability:** CAP-022
**Business Requirement:** BR-23
**Rules Owner:** [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md)
**Design Owner:** [SRIS-P1-DATA-009](../wave-3-detailed-design/SRIS-P1-DATA-009_SeatMatrixGenerationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-071: Chart Resolution of Quotas and Waitlists**

Chart preparation must resolve the remaining quota pools, RAC allocations, and waitlist positions according to [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md) — Domain Rules: Chart Preparation. This requirement states only the observable outcome: after chart preparation, unallocated seats are assigned to eligible waitlisted passengers, and every booking has a final reservation status.

**On failure or exhaustion:** If a booking cannot be resolved because the passenger record is incomplete, the booking is left in its pre-chart state and is flagged for manual attention. The chart is not fully committed until all bookings are resolved.

**Capability:** CAP-022
**Business Requirement:** BR-23
**Rules Owner:** [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md)
**Design Owner:** [SRIS-P1-DATA-009](../wave-3-detailed-design/SRIS-P1-DATA-009_SeatMatrixGenerationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-072: Chart Lock**

After chart preparation completes, the seat matrix for the journey must be locked. No seat allocation, release, or reallocation may occur on a locked matrix except as part of the no-show handling in [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md) — Domain Rules: Chart Preparation.

**On failure or exhaustion:** If a booking attempt is received for a locked journey, the system must return a not-bookable response.

**Capability:** CAP-022
**Business Requirement:** BR-23
**Rules Owner:** [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md)
**Design Owner:** [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-073: Customer-Initiated Cancellation**

The system must allow an authenticated customer to cancel a booking that they own, provided the journey has not yet departed and the booking is not in a state that prohibits cancellation per [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing.

**On failure or exhaustion:** If the customer does not own the booking, the system must return a forbidden response. If the journey has departed, the system must return a not-allowed response. If the cancellation cannot be recorded, no seat is released and the booking remains unchanged.

**Capability:** CAP-023
**Business Requirement:** BR-23
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-074: Cancellation Computation of Refund**

On cancellation, the system must compute the refund amount under SR-045 and record it against the booking.

**On failure or exhaustion:** If the refund amount cannot be computed because the fare rule that applied at booking time cannot be retrieved, the system must return a service-unavailable response and the booking must remain in its pre-cancellation state.

**Capability:** CAP-023, CAP-014
**Business Requirement:** BR-23, BR-8
**Rules Owner:** [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)
**Design Owner:** [SRIS-P1-API-011](../wave-3-detailed-design/SRIS-P1-API-011_PaymentGatewayIntegrationDesignMock.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-075: Cancellation Seat Release and Waitlist Cascade**

On successful cancellation, the system must release the allocated seat under SR-057 and trigger the waitlist cascade under SR-068.

**On failure or exhaustion:** If the seat release fails, the cancellation must not be committed. If the waitlist cascade fails, the cancellation stands but the cascade is retried; on continued failure, the Lead Architect is notified.

**Capability:** CAP-023, CAP-021, CAP-018
**Business Requirement:** BR-23
**Rules Owner:** [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)
**Design Owner:** [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-076: Cancellation Audit**

The system must record every cancellation as an audit entry that names the booking, the customer, the reason if supplied, the refund amount, and the timestamp.

**On failure or exhaustion:** If the audit record cannot be written, the cancellation must be rejected and rolled back.

**Capability:** CAP-023
**Business Requirement:** BR-23
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-DATA-001](../wave-3-detailed-design/SRIS-P1-DATA-001_DataDesignDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-077: Ticket Retrieval by PNR**

The system must allow an authenticated customer to retrieve a booking by PNR. The response must include the passenger list, the journey details, the reservation status of each passenger, and the coach and berth or seat assignment where one exists.

**On failure or exhaustion:** If the PNR does not exist, the system must return a not-found response. If the PNR exists but belongs to a different customer, the system must return a forbidden response that does not reveal whether the PNR exists.

**Capability:** CAP-024
**Business Requirement:** BR-21, BR-22
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-078: PNR Status Enquiry Without Authentication**

The system must allow an unauthenticated user to submit a PNR and a passenger surname and receive the reservation status of the booking. The response must not disclose passenger contact details or payment information.

**On failure or exhaustion:** If the PNR does not exist or the surname does not match any passenger on the booking, the system must return a not-found response that does not distinguish between the two cases.

**Capability:** CAP-024
**Business Requirement:** BR-21
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-079: Booking Lifecycle State Transition Enforcement**

The system must enforce the booking state transitions defined in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing. Any request to move a booking into a state that is not reachable from its current state must be rejected.

**On failure or exhaustion:** If a transition is requested that is not defined in the domain rules, the system must return a conflict response naming the current state and rejecting the transition. No partial state change is applied.

**Capability:** CAP-019
**Business Requirement:** BR-20, BR-22, BRL-2
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

## 8. Payment

This section records the software requirements for the Payment capability domain. The domain is split by role. The domain side is owned by S3 Reservation Service. The simulator side is owned by S5 Mock Payment Gateway. The capabilities covered are CAP-025 and CAP-026 in [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final).

The payment rules and idempotency handling belong to [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing and [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md) — Idempotency and Retry Policy Specification. The mock gateway's behaviour belongs to [SRIS-P1-API-011](../wave-3-detailed-design/SRIS-P1-API-011_PaymentGatewayIntegrationDesignMock.md) — Payment Gateway Integration Design (Mock). None of these are defined here.

The requirements below state the observable behaviour of the payment flow. The mechanism by which the flow interacts with the booking mechanism belongs to [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing.

---

**SR-080: Payment Initiation**

For every booking request that reaches the payment step, the system must initiate a payment by requesting a payment session from the mock payment gateway. The request must carry the amount from the fare re-quote, a unique idempotency key, and a callback URL.

**On failure or exhaustion:** If the mock gateway is unavailable, the system must return a service-unavailable response and must not proceed with the booking. Any protected seat is released per the rules in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing.

**Capability:** CAP-025
**Business Requirement:** BR-17, BR-19, BRL-2
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-API-011](../wave-3-detailed-design/SRIS-P1-API-011_PaymentGatewayIntegrationDesignMock.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-081: Payment Attempt Recording**

The system must record every payment attempt against the booking. Each record names the booking, the amount, the idempotency key, the gateway session reference, and the current attempt state.

**On failure or exhaustion:** If the attempt cannot be recorded, the system must not initiate the payment and must not proceed with the booking.

**Capability:** CAP-025
**Business Requirement:** BR-19
**Rules Owner:** [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md)
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-082: Payment Callback Receipt**

The system must accept a payment result callback from the mock payment gateway. The callback must be verified for signature and for the idempotency key before any state change is applied.

**On failure or exhaustion:** If the signature does not verify, the system must reject the callback with a forbidden response and must not change booking state. If the idempotency key matches a callback that has already been processed, the system must return a success response without applying a second state change.

**Capability:** CAP-025
**Business Requirement:** BR-19, BRL-2
**Rules Owner:** [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md)
**Design Owner:** [SRIS-P1-API-011](../wave-3-detailed-design/SRIS-P1-API-011_PaymentGatewayIntegrationDesignMock.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-083: Payment Result Dispatch to Booking**

On verified callback receipt, the system must dispatch the payment result to the booking flow defined in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing. The result drives the booking to confirmed, waitlisted, or failed-and-refunded according to that document.

**On failure or exhaustion:** If the booking flow cannot process the result, the callback must be acknowledged with the appropriate error response so the gateway retries, and the booking must remain in its intermediate state until the retry succeeds.

**Capability:** CAP-025
**Business Requirement:** BR-19, BRL-2
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-084: Mock Payment Processing**

The mock payment gateway must accept a payment session request and produce a configurable outcome. The outcomes are success, failure, and abandonment, and their relative frequency is configurable by the environment. The gateway must return a signed callback to the callback URL provided in the request.

**On failure or exhaustion:** If the callback cannot be delivered, the gateway must retry delivery on a bounded backoff schedule defined in [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md) — Idempotency and Retry Policy Specification. The gateway's own state must remain consistent regardless of callback delivery outcome.

**Capability:** CAP-026
**Business Requirement:** BR-18, BRL-6
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-API-011](../wave-3-detailed-design/SRIS-P1-API-011_PaymentGatewayIntegrationDesignMock.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-085: Mock Gateway Idempotency**

The mock payment gateway must treat two payment session requests with the same idempotency key as a single request. A repeated request must return the same session reference and must not create a second session.

**On failure or exhaustion:** None. This requirement is itself the idempotency guarantee.

**Capability:** CAP-026
**Business Requirement:** BR-18, BR-19
**Rules Owner:** [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md)
**Design Owner:** [SRIS-P1-API-011](../wave-3-detailed-design/SRIS-P1-API-011_PaymentGatewayIntegrationDesignMock.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-086: Payment Reversal on Booking Failure**

When the booking cannot be confirmed after payment success, the system must initiate a reversal of the payment through the mock payment gateway. The reversal must return the customer's money in full and must not apply the charges that would apply to a customer-initiated cancellation.

**On failure or exhaustion:** If the mock gateway does not acknowledge the reversal, the system must queue the reversal for retry on a bounded schedule. The booking is marked as refund-pending until the reversal is acknowledged, and the customer is notified of the pending state.

**Capability:** CAP-025, CAP-026
**Business Requirement:** BR-16, BRL-6
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-087: Refund on Cancellation Through Mock Gateway**

When a customer-initiated cancellation results in a refund under SR-074, the system must initiate the refund through the mock payment gateway. The refund amount is the value computed under SR-045.

**On failure or exhaustion:** If the mock gateway does not acknowledge the refund, the system must queue it for retry and must return a refund-pending response to the customer. The booking remains cancelled; only the refund is pending.

**Capability:** CAP-025, CAP-026
**Business Requirement:** BR-23, BRL-6
**Rules Owner:** [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)
**Design Owner:** [SRIS-P1-API-011](../wave-3-detailed-design/SRIS-P1-API-011_PaymentGatewayIntegrationDesignMock.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

## 9. Search and Discovery

This section records the software requirements for the Search and Discovery capability domain. The domain is owned by S4 Search Aggregator BFF. The capabilities covered are CAP-027 and CAP-028 in [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final).

The BFF is read-only. No requirement in this section mutates state in any downstream service. The API contract for search belongs to [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md) — API Contract Document (OpenAPI).

---

**SR-088: Train Search Initiation**

The system must accept a search request from any client and return the set of trains matching the requested origin station, destination station, journey date, and optional class filter.

**On failure or exhaustion:** If the origin or the destination station does not exist, the system must return a not-found response. If the journey date is in the past or beyond the configured booking horizon, the system must return a validation response. If the schedule service or the availability service is unavailable, the system must return a partial-results response with the fields that could not be populated marked as unavailable, and must not return an error that hides the partial result.

**Capability:** CAP-027
**Business Requirement:** BR-9, BR-11
**Rules Owner:** None
**Design Owner:** [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-089: Search Filtering by Quota**

The system must accept an optional quota filter on a search request and must return only trains and classes for which the requested quota is defined.

**On failure or exhaustion:** If the quota code is not one of the values recorded in [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary, the system must return a validation response. If the quota exists but applies to none of the matched trains, the system must return an empty result rather than an error.

**Capability:** CAP-027
**Business Requirement:** BR-12
**Rules Owner:** None
**Design Owner:** [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-090: Search Result Composition from Schedule**

For every matched train, the system must include the schedule data: train number, train name, train type, departure time from the origin, arrival time at the destination, and total journey duration.

**On failure or exhaustion:** If the schedule service cannot return the schedule for a matched train, that train must appear in the result with the schedule fields marked unavailable. The remaining trains must be returned normally.

**Capability:** CAP-028
**Business Requirement:** BR-10
**Rules Owner:** None
**Design Owner:** [SRIS-P1-API-004](../wave-3-detailed-design/SRIS-P1-API-004_IntegrationDesignDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-091: Search Result Composition with Availability**

For every matched train and every class of that train that passes the quota filter, the system must include the current seat availability from the availability service.

**On failure or exhaustion:** If the availability service cannot return a value for a matched train and class, that class must appear with availability marked unavailable rather than with a zero value. The system must not present an unavailable reading as an empty seat.

**Capability:** CAP-028
**Business Requirement:** BR-10, BR-13
**Rules Owner:** [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)
**Design Owner:** [SRIS-P1-API-004](../wave-3-detailed-design/SRIS-P1-API-004_IntegrationDesignDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-092: Search Result Composition with Fare Quote**

For every matched train and every class of that train that passes the quota filter, the system must include a fare quote computed under SR-040 for the requested journey segment.

**On failure or exhaustion:** If the fare quote cannot be computed because the pricing service is unavailable or no fare rule is in effect, that class must appear with the fare marked unavailable. The system must not return a zero fare.

**Capability:** CAP-028, CAP-014
**Business Requirement:** BR-10, BR-8
**Rules Owner:** [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)
**Design Owner:** [SRIS-P1-API-004](../wave-3-detailed-design/SRIS-P1-API-004_IntegrationDesignDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-093: Unified Search Response Assembly**

The system must return the search results as a single response in which each matched train combines its schedule, the availability of each class, and the fare quote of each class in one entry.

**On failure or exhaustion:** If any individual downstream call times out, the response must be returned within the configured search-response budget with the missing fields marked unavailable. The search must not block waiting for a slow downstream call beyond the budget.

**Capability:** CAP-028
**Business Requirement:** BR-10, BR-11
**Rules Owner:** None
**Design Owner:** [SRIS-P1-ARCH-009](../wave-2-architecture/SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-094: Search Result Pagination**

The system must paginate search results when the number of matched trains exceeds the configured page size, and must return the total count of matched trains alongside the current page.

**On failure or exhaustion:** If the requested page number is beyond the last page, the system must return an empty page with the total count, not an error.

**Capability:** CAP-027, CAP-028
**Business Requirement:** BR-9
**Rules Owner:** None
**Design Owner:** [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

## 10. Notification

This section records the software requirements for the Notification capability domain. The domain is owned by S6 Notification Service. The capabilities covered are CAP-029 and CAP-030 in [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final).

Notification must never block or fail a booking, per Business Rule BRL-5. The event schema belongs to [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md) — Event Schema Document (AsyncAPI). The integration design belongs to [SRIS-P1-API-012](../wave-3-detailed-design/SRIS-P1-API-012_NotificationIntegrationDesign.md) — Notification Integration Design.

---

**SR-095: Notification Event Consumption**

The system must consume booking-domain events from the event stream and dispatch notifications according to the templates defined for each event type. The consumed events include at minimum BookingConfirmed, BookingWaitlisted, BookingPromoted, BookingCancelled, and BookingRefunded.

**On failure or exhaustion:** If an event cannot be consumed because the payload is malformed, the system must route it to a dead-letter channel and must not silently discard it. If the template for an event type does not exist, the event must be routed to the dead-letter channel and the Lead Architect notified.

**Capability:** CAP-029, CAP-030
**Business Requirement:** BR-24, BR-25, BRL-5
**Rules Owner:** [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md)
**Design Owner:** [SRIS-P1-API-012](../wave-3-detailed-design/SRIS-P1-API-012_NotificationIntegrationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-096: Booking Confirmation Notification Dispatch**

On BookingConfirmed, the system must dispatch a confirmation to the customer by email and by SMS. The email contains the PNR, the journey details, the passenger list, the coach and berth assignments, and the amount paid. The SMS contains the PNR and the journey summary.

**On failure or exhaustion:** If the email dispatches but the SMS fails, the email is sent and the SMS is retried. If both fail, both are retried on the bounded schedule in SR-097. In no case does a failed dispatch roll back the booking.

**Capability:** CAP-029
**Business Requirement:** BR-24, BRL-5
**Rules Owner:** [SRIS-P1-API-012](../wave-3-detailed-design/SRIS-P1-API-012_NotificationIntegrationDesign.md)
**Design Owner:** [SRIS-P1-API-012](../wave-3-detailed-design/SRIS-P1-API-012_NotificationIntegrationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-097: Notification Delivery Retry**

The system must retry a failed notification dispatch on a bounded backoff schedule. The schedule and the maximum retry count belong to [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md) — Idempotency and Retry Policy Specification.

**On failure or exhaustion:** After the maximum retry count is exhausted, the notification must be marked as failed in the delivery log and must be visible to the operations role. The failure must not affect the booking state.

**Capability:** CAP-030
**Business Requirement:** BR-25, BRL-5
**Rules Owner:** [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md)
**Design Owner:** [SRIS-P1-API-012](../wave-3-detailed-design/SRIS-P1-API-012_NotificationIntegrationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-098: Notification Template Rendering**

The system must render each notification from a stored template and the payload of the triggering event. Templates must be versioned, and the version used for each dispatch must be recorded in the delivery log.

**On failure or exhaustion:** If the template cannot be rendered because a required field is missing from the event payload, the dispatch must fail and be routed to the dead-letter channel. A partial notification must never be dispatched.

**Capability:** CAP-030
**Business Requirement:** BR-25
**Rules Owner:** [SRIS-P1-API-012](../wave-3-detailed-design/SRIS-P1-API-012_NotificationIntegrationDesign.md)
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-099: Notification Delivery Logging**

The system must record every dispatch attempt in a delivery log. Each entry records the notification type, the recipient channel, the template version, the attempt number, the outcome, and the timestamp.

**On failure or exhaustion:** If the log entry cannot be written, the dispatch must not be committed. Retrying the dispatch is acceptable; logging a dispatch that was not attempted is not.

**Capability:** CAP-030
**Business Requirement:** BR-25
**Rules Owner:** [SRIS-P1-API-012](../wave-3-detailed-design/SRIS-P1-API-012_NotificationIntegrationDesign.md)
**Design Owner:** [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-100: Notification Recipient Data Minimisation**

The system must include in each notification only the data required for the notification's purpose. The confirmation email must not include payment instrument details, full passenger contact details beyond the customer's own, or any data classified above the level defined in [SRIS-P1-SEC-012](../wave-3-detailed-design/SRIS-P1-SEC-012_DataClassificationRegister.md) — Data Classification Register.

**On failure or exhaustion:** If a template attempts to render a field not permitted for the notification type, the render must fail and the dispatch must route to the dead-letter channel. No notification must be dispatched with the offending field redacted silently.

**Capability:** CAP-030
**Business Requirement:** BR-25
**Rules Owner:** [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md)
**Design Owner:** [SRIS-P1-API-012](../wave-3-detailed-design/SRIS-P1-API-012_NotificationIntegrationDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

## 11. User Surface Requirements

This section records the software requirements specific to the two user-facing surfaces: the Customer Booking Website and the Employee Admin Console. These requirements describe observable behaviour of the surfaces that is not already covered by the domain requirements in Sections 3 to 10.

The UI layouts, wireframes, and navigation belong to [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md) to [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md). They are not defined here.

---

**SR-101: Customer Surface Page Load Without Authentication**

The Customer Booking Website must render its public pages (home, search, train detail, PNR status enquiry) for an unauthenticated visitor.

**On failure or exhaustion:** If the initial asset load fails, the surface must display an error page with a retry action. It must not display a blank screen.

**Capability:** CAP-027, CAP-024
**Business Requirement:** BR-26
**Rules Owner:** None
**Design Owner:** [SRIS-P1-UI-003](../wave-3-detailed-design/SRIS-P1-UI-003_WireframesCustomerFlow.md)
**Test Owner:** [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md)

---

**SR-102: Customer Surface Authenticated Session**

The Customer Booking Website must restore an authenticated session on page reload when a valid access or refresh token is present, and must return the user to the page they were viewing.

**On failure or exhaustion:** If the session cannot be restored because the token has expired and the refresh has failed, the surface must redirect the user to the login page and must preserve the intended destination so the user is returned there after login.

**Capability:** CAP-001, CAP-004
**Business Requirement:** BR-26, BR-1
**Rules Owner:** [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)
**Design Owner:** [SRIS-P1-UI-011](../wave-3-detailed-design/SRIS-P1-UI-011_FrontendRoutingAndPageMap.md)
**Test Owner:** [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md)

---

**SR-103: Customer Surface Form Validation Feedback**

The Customer Booking Website must validate the fields of every form against the same rules that the server enforces, and must display the validation feedback beside the failing field before submitting.

**On failure or exhaustion:** If a field passes client-side validation but is rejected by the server, the surface must display the server error beside the failing field.

**Capability:** CAP-001, CAP-005, CAP-019
**Business Requirement:** BR-26
**Rules Owner:** [SRIS-P1-API-006](../wave-3-detailed-design/SRIS-P1-API-006_APIErrorCodeCatalog.md)
**Design Owner:** [SRIS-P1-UI-006](../wave-3-detailed-design/SRIS-P1-UI-006_FormFieldSpecification.md)
**Test Owner:** [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md)

---

**SR-104: Customer Surface Search Result Display**

The Customer Booking Website must display the search results in a list of train cards. Each card must show the train number, the train name, the departure time, the arrival time, and for each class the availability reading and the fare quote. The availability reading must carry its reading timestamp.

**On failure or exhaustion:** If a field is marked unavailable in the API response, the surface must display the field as "Currently unavailable" rather than as zero or blank.

**Capability:** CAP-027, CAP-028
**Business Requirement:** BR-26, BR-9, BR-10
**Rules Owner:** None
**Design Owner:** [SRIS-P1-UI-003](../wave-3-detailed-design/SRIS-P1-UI-003_WireframesCustomerFlow.md)
**Test Owner:** [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md)

---

**SR-105: Customer Surface Payment Loading State**

While a booking is in progress — from seat protection through payment callback — the Customer Booking Website must display a loading state that names the stage the booking has reached. The surface must not display a success state until the booking response confirms it.

**On failure or exhaustion:** If the booking request times out, the surface must display a timeout state with a retry action and must not display a success state.

**Capability:** CAP-019, CAP-025
**Business Requirement:** BR-26
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-UI-008](../wave-3-detailed-design/SRIS-P1-UI-008_UIErrorAndNotificationDisplayRules.md)
**Test Owner:** [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md)

---

**SR-106: Customer Surface Booking Outcome Display**

The Customer Booking Website must display the outcome of a booking attempt exactly as returned by the booking service: confirmed with a PNR, waitlisted with a position, refunded with a pending refund reference, or failed with an error message.

**On failure or exhaustion:** If the response cannot be classified into one of the known outcomes, the surface must display a generic failure state with the raw response identifier for support.

**Capability:** CAP-020, CAP-021, CAP-024
**Business Requirement:** BR-26
**Rules Owner:** [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)
**Design Owner:** [SRIS-P1-UI-003](../wave-3-detailed-design/SRIS-P1-UI-003_WireframesCustomerFlow.md)
**Test Owner:** [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md)

---

**SR-107: Employee Surface Page Load with Role Check**

The Employee Admin Console must render its pages only for an authenticated employee whose role permits the requested page. A page whose role check fails must not be reachable by URL manipulation.

**On failure or exhaustion:** If the role check fails, the surface must redirect the user to the dashboard with a permission-denied notification.

**Capability:** CAP-002, CAP-003
**Business Requirement:** BR-27, BR-3
**Rules Owner:** [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md)
**Design Owner:** [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md)
**Test Owner:** [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md)

---

**SR-108: Employee Surface Role-Scoped Navigation**

The Employee Admin Console must display navigation options that reflect the employee's role. Options that the role does not permit must not appear.

**On failure or exhaustion:** If the role cannot be determined from the session, the surface must display only the minimal navigation for the employee default role and must display a session warning.

**Capability:** CAP-003
**Business Requirement:** BR-27, BR-3
**Rules Owner:** [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md)
**Design Owner:** [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md)
**Test Owner:** [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md)

---

**SR-109: Employee Surface Configuration Form Validation**

Every configuration form in the Employee Admin Console must validate its fields against the same rules the server enforces, and must display server-side validation errors beside the failing field.

**On failure or exhaustion:** If a configuration save is rejected because of a conflict (for example, a station code already in use), the surface must display the conflict message from the server beside the field and must not clear the form.

**Capability:** CAP-006, CAP-007, CAP-008, CAP-009, CAP-010, CAP-011, CAP-012, CAP-013, CAP-016
**Business Requirement:** BR-27, BR-5, BR-6, BR-7
**Rules Owner:** [SRIS-P1-API-006](../wave-3-detailed-design/SRIS-P1-API-006_APIErrorCodeCatalog.md)
**Design Owner:** [SRIS-P1-UI-006](../wave-3-detailed-design/SRIS-P1-UI-006_FormFieldSpecification.md)
**Test Owner:** [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md)

---

**SR-110: Both Surfaces Consistent Error Display**

Both surfaces must display errors in a consistent visual format across all views. The format, placement, and colour belong to [SRIS-P1-UI-008](../wave-3-detailed-design/SRIS-P1-UI-008_UIErrorAndNotificationDisplayRules.md) — UI Error and Notification Display Rules.

**On failure or exhaustion:** None. This requirement is itself the display convention.

**Capability:** CAP-001, CAP-002, CAP-003, CAP-004, CAP-005, CAP-006, CAP-007, CAP-008, CAP-009, CAP-010, CAP-011, CAP-012, CAP-013, CAP-019, CAP-025
**Business Requirement:** BR-26, BR-27
**Rules Owner:** [SRIS-P1-UI-008](../wave-3-detailed-design/SRIS-P1-UI-008_UIErrorAndNotificationDisplayRules.md)
**Design Owner:** [SRIS-P1-UI-008](../wave-3-detailed-design/SRIS-P1-UI-008_UIErrorAndNotificationDisplayRules.md)
**Test Owner:** [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md)

---

## 12. Cross-Cutting Software Requirements

This section records software requirements that apply to two or more services rather than to a single service. Each requirement names the services it applies to.

The exact wire format of the error envelope belongs to [SRIS-P1-API-006](../wave-3-detailed-design/SRIS-P1-API-006_APIErrorCodeCatalog.md) — API Error Code Catalog. The exact logging and tracing conventions belong to [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md) — Observability and Monitoring Design (OTel/W3C). The exact security controls belong to [SRIS-P1-SEC-013](../wave-3-detailed-design/SRIS-P1-SEC-013_SecureCodingStandards.md) — Secure Coding Standards.

---

**SR-111: Standard Error Envelope**

Every service must return errors in a standard envelope that carries an error code, a human-readable message, and a correlation identifier. The envelope shape is defined in [SRIS-P1-API-006](../wave-3-detailed-design/SRIS-P1-API-006_APIErrorCodeCatalog.md) — API Error Code Catalog.

**On failure or exhaustion:** None. This requirement is itself the error convention.

**Applies to:** S1, S2, S3, S4, S5, S6
**Capability:** All capabilities
**Business Requirement:** BR-1 to BR-31
**Rules Owner:** [SRIS-P1-API-006](../wave-3-detailed-design/SRIS-P1-API-006_APIErrorCodeCatalog.md)
**Design Owner:** [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-112: Correlation Identifier Propagation**

Every service must read an incoming correlation identifier from the request, or generate one if none is present, and must propagate it to every outbound call and to every log entry produced while handling the request.

**On failure or exhaustion:** If the incoming correlation identifier is malformed, the service must generate a new one and must log the malformed value in a separate field. It must not reject the request on the basis of a malformed identifier.

**Applies to:** S1, S2, S3, S4, S5, S6
**Capability:** All capabilities
**Business Requirement:** BR-1 to BR-31
**Rules Owner:** [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)
**Design Owner:** [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-113: Structured Logging**

Every service must emit log entries in the structured format defined in [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md) — Observability and Monitoring Design (OTel/W3C). Every log entry must carry the correlation identifier of SR-112, the service name, and the timestamp.

**On failure or exhaustion:** If the log output sink is unavailable, the service must continue to serve requests. It must not fail a request because a log entry could not be written.

**Applies to:** S1, S2, S3, S4, S5, S6
**Capability:** All capabilities
**Business Requirement:** BR-1 to BR-31
**Rules Owner:** [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)
**Design Owner:** [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-114: Health Check Endpoint**

Every service must expose a health check endpoint that returns success when the service can serve requests and failure when it cannot. The endpoint must not require authentication.

**On failure or exhaustion:** If a downstream dependency required for the service's core function is unavailable, the health check must return a degraded status rather than success or failure. The exact status codes belong to [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md) — API Contract Document (OpenAPI).

**Applies to:** S1, S2, S3, S4, S5, S6
**Capability:** All capabilities
**Business Requirement:** BR-29
**Rules Owner:** [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)
**Design Owner:** [SRIS-P1-API-010](../wave-3-detailed-design/SRIS-P1-API-010_APIGatewayConfigurationDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-115: Idempotency Key Handling on State-Changing Endpoints**

Every state-changing endpoint that receives an idempotency key from the client must treat two requests with the same key as a single request. A repeated request with the same key must return the same response as the first request.

**On failure or exhaustion:** If the idempotency key store is unavailable, the service must reject the request with a service-unavailable response rather than processing it twice. The exact storage mechanism belongs to [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md) — Distributed Concurrency and Locking Strategy.

**Applies to:** S1, S2, S3, S5
**Capability:** CAP-004, CAP-011, CAP-012, CAP-013, CAP-019, CAP-020, CAP-023, CAP-025, CAP-026
**Business Requirement:** BR-19, BRL-1
**Rules Owner:** [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md)
**Design Owner:** [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-116: Distributed Tracing**

Every service must emit distributed tracing spans for every inbound request and every outbound call. The trace context must propagate across service boundaries. The exact tracing format and the OpenTelemetry and W3C conventions belong to [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md) — Observability and Monitoring Design (OTel/W3C).

**On failure or exhaustion:** If the tracing exporter is unavailable, the service must continue to serve requests. Spans may be sampled or dropped; requests must not fail because tracing failed.

**Applies to:** S1, S2, S3, S4, S5, S6
**Capability:** All capabilities
**Business Requirement:** BR-1 to BR-31
**Rules Owner:** [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)
**Design Owner:** [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-117: Request Timeout Discipline**

Every outbound call from one service to another must carry a configured timeout. The service must not wait for a downstream response beyond the configured budget.

**On failure or exhaustion:** If a downstream call times out, the calling service must return a timeout response to its caller and must not proceed with any state change that depended on the timed-out call.

**Applies to:** S1, S2, S3, S4, S5, S6
**Capability:** All capabilities
**Business Requirement:** BR-1 to BR-31
**Rules Owner:** [SRIS-P1-ARCH-011](../wave-2-architecture/SRIS-P1-ARCH-011_ErrorHandlingAndResilienceDesign.md)
**Design Owner:** [SRIS-P1-ARCH-011](../wave-2-architecture/SRIS-P1-ARCH-011_ErrorHandlingAndResilienceDesign.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-118: Bulkhead Isolation Between Callers**

Every service must isolate concurrent request handling so that a slow downstream dependency cannot exhaust the request handling capacity for other endpoints. The isolation policy belongs to [SRIS-P1-ARCH-011](../wave-2-architecture/SRIS-P1-ARCH-011_ErrorHandlingAndResilienceDesign.md) — Error Handling and Resilience Design.

**On failure or exhaustion:** If the isolated capacity for an endpoint is exhausted, further requests to that endpoint must receive a rate-limit or service-busy response. Requests to other endpoints must not be affected.

**Applies to:** S1, S2, S3, S4, S5, S6
**Capability:** All capabilities
**Business Requirement:** BR-1 to BR-31
**Rules Owner:** [SRIS-P1-ARCH-011](../wave-2-architecture/SRIS-P1-ARCH-011_ErrorHandlingAndResilienceDesign.md)
**Design Owner:** [SRIS-P1-ARCH-011](../wave-2-architecture/SRIS-P1-ARCH-011_ErrorHandlingAndResilienceDesign.md)
**Test Owner:** [SRIS-P1-TEST-009](../wave-4-testing/SRIS-P1-TEST-009_LoadTestPlan.md)

---

**SR-119: Rate Limiting on Public Endpoints**

Every service that exposes an endpoint to an unauthenticated caller must apply a rate limit per source. The rate limit values belong to [SRIS-P1-API-008](../wave-3-detailed-design/SRIS-P1-API-008_APIRateLimitingAndThrottlingRules.md) — API Rate Limiting and Throttling Rules.

**On failure or exhaustion:** If the rate limit is exceeded, the service must return a rate-limit response naming the retry-after interval. If the rate limiter itself is unavailable, the service must fail open and continue to serve requests, and must emit a warning log.

**Applies to:** S1, S3, S4
**Capability:** CAP-001, CAP-004, CAP-024, CAP-027
**Business Requirement:** BR-1, BR-9, BR-21
**Rules Owner:** [SRIS-P1-API-008](../wave-3-detailed-design/SRIS-P1-API-008_APIRateLimitingAndThrottlingRules.md)
**Design Owner:** [SRIS-P1-API-010](../wave-3-detailed-design/SRIS-P1-API-010_APIGatewayConfigurationDocument.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

**SR-120: Sensitive Field Masking in Logs**

Every service must mask sensitive fields in log output and in trace attributes. The field classification belongs to [SRIS-P1-SEC-012](../wave-3-detailed-design/SRIS-P1-SEC-012_DataClassificationRegister.md) — Data Classification Register. At minimum, passwords, tokens, payment instrument details, and full personal contact details must never appear in logs.

**On failure or exhaustion:** If a log formatter encounters a field it cannot classify, it must mask the field by default rather than log it.

**Applies to:** S1, S2, S3, S4, S5, S6
**Capability:** All capabilities
**Business Requirement:** BR-1 to BR-31
**Rules Owner:** [SRIS-P1-SEC-013](../wave-3-detailed-design/SRIS-P1-SEC-013_SecureCodingStandards.md)
**Design Owner:** [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)
**Test Owner:** [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)

---

## 13. Traceability

This section records the local traceability of every software requirement in this document. It maps each SR to the capability it realises, from [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final), and to the business requirement it satisfies, from [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD).

The full cross-wave matrix, which spans every document in the register, belongs to [SRIS-P1-REQ-012](./SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md) — Requirement Traceability Matrix (RTM), and is not repeated here.

### 13.1 SR to Capability Mapping by Domain

| Section | Capability Domain     | SR Range          | Capabilities Covered                  |
| ------- | --------------------- | ----------------- | ------------------------------------- |
| 3       | Identity and Access   | SR-001 to SR-018  | CAP-001 to CAP-005                    |
| 4       | Railway Master Data   | SR-019 to SR-035  | CAP-006 to CAP-010                    |
| 5       | Fare and Pricing      | SR-036 to SR-046  | CAP-011 to CAP-014                    |
| 6       | Inventory and Quota   | SR-047 to SR-058  | CAP-015 to CAP-018                    |
| 7       | Booking and Ticketing | SR-059 to SR-079  | CAP-019 to CAP-024                    |
| 8       | Payment               | SR-080 to SR-087  | CAP-025, CAP-026                      |
| 9       | Search and Discovery  | SR-088 to SR-094  | CAP-027, CAP-028                      |
| 10      | Notification          | SR-095 to SR-100  | CAP-029, CAP-030                      |
| 11      | User Surfaces         | SR-101 to SR-110  | Multiple (cross-domain surface rules) |
| 12      | Cross-Cutting         | SR-111 to SR-120  | All capabilities                      |

### 13.2 Coverage of Capabilities

Every capability from CAP-001 to CAP-030 is realised by at least one software requirement.

| Capability | Realised by                          |
| ---------- | ------------------------------------ |
| CAP-001    | SR-001, SR-002, SR-003, SR-015, SR-018, SR-102, SR-110 |
| CAP-002    | SR-005, SR-006, SR-018, SR-107, SR-110 |
| CAP-003    | SR-009, SR-010, SR-018, SR-107, SR-108, SR-110 |
| CAP-004    | SR-003, SR-004, SR-007, SR-008, SR-018, SR-102, SR-115 |
| CAP-005    | SR-011, SR-012, SR-013, SR-014, SR-015, SR-016, SR-017, SR-018, SR-110 |
| CAP-006    | SR-019, SR-020, SR-021, SR-035, SR-109, SR-110 |
| CAP-007    | SR-022, SR-023, SR-024, SR-035, SR-109, SR-110 |
| CAP-008    | SR-025, SR-026, SR-027, SR-028, SR-035, SR-109, SR-110 |
| CAP-009    | SR-029, SR-030, SR-035, SR-109, SR-110 |
| CAP-010    | SR-031, SR-032, SR-033, SR-034, SR-035, SR-109, SR-110 |
| CAP-011    | SR-036, SR-037, SR-044, SR-046, SR-109, SR-110 |
| CAP-012    | SR-038, SR-043, SR-046, SR-109, SR-110 |
| CAP-013    | SR-039, SR-042, SR-046, SR-109, SR-110 |
| CAP-014    | SR-040, SR-041, SR-042, SR-043, SR-044, SR-045, SR-061, SR-074, SR-092 |
| CAP-015    | SR-047, SR-048                          |
| CAP-016    | SR-049, SR-050, SR-058, SR-109          |
| CAP-017    | SR-051, SR-052                          |
| CAP-018    | SR-053, SR-054, SR-055, SR-056, SR-057, SR-062, SR-075 |
| CAP-019    | SR-059, SR-060, SR-061, SR-062, SR-063, SR-064, SR-079, SR-103, SR-105 |
| CAP-020    | SR-064, SR-065, SR-106                  |
| CAP-021    | SR-066, SR-067, SR-068, SR-069, SR-075, SR-106 |
| CAP-022    | SR-070, SR-071, SR-072                  |
| CAP-023    | SR-073, SR-074, SR-075, SR-076, SR-110  |
| CAP-024    | SR-077, SR-078, SR-101, SR-106          |
| CAP-025    | SR-080, SR-081, SR-082, SR-083, SR-086, SR-087, SR-105, SR-110, SR-115 |
| CAP-026    | SR-084, SR-085, SR-086, SR-087, SR-115  |
| CAP-027    | SR-088, SR-089, SR-094, SR-101, SR-104, SR-119 |
| CAP-028    | SR-090, SR-091, SR-092, SR-093, SR-094, SR-104 |
| CAP-029    | SR-095, SR-096                          |
| CAP-030    | SR-095, SR-097, SR-098, SR-099, SR-100  |

### 13.3 SR to Business Requirement Mapping

Every software requirement traces to a business requirement from [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD). The business requirement identifiers used in this document are BR-1 to BR-31, BRL-1 to BRL-14, and BA-1 to BA-8. Their definitions are recorded in [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) and are not repeated here.

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

| Seq  | Document ID                                                                                                | Document Name                                     | Wave | Pri | Tag     |
| ---- | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------- | ---- | --- | ------- |
| 0.0  | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md)       | Documentation Index and Navigation Map            | 0    | P0  | UNBLOCK |
| 0.1  | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)                 | Document Template Standard                        | 0    | P0  | UNBLOCK |
| 0.2  | [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)              | Document ID and Category Scheme                   | 0    | P1  | UNBLOCK |
| 0.3  | [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md)           | Document Cross-Reference Standard                 | 0    | P1  | UNBLOCK |
| 0.4  | [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)            | Project Vision and Scope Document                 | 0    | P0  | UNBLOCK |
| 0.6  | [SRIS-P1-GOV-007](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md)                    | Project Management Plan                           | 0    | P0  | UNBLOCK |
| 1.1  | [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md)                                          | Glossary and Domain Dictionary                    | 1    | P0  | UNBLOCK |
| 1.2  | [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md)                                     | Business Requirements Document (BRD)              | 1    | P0  | UNBLOCK |
| 1.3  | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)                                               | Capability Catalog (Final)                        | 1    | P0  | UNBLOCK |
| 1.5  | [SRIS-P1-REQ-005](./SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md)                                    | Non-Functional Requirements (ISO 25010)           | 1    | P0  | UNBLOCK |
| 1.6  | [SRIS-P1-REQ-006](./SRIS-P1-REQ-006_UserStoriesAndUseCases.md)                                              | User Stories and Use Cases                        | 1    | P0  | UNBLOCK |
| 1.7  | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)                                          | Domain Rules: Fare Calculation                    | 1    | P1  | FOLLOW  |
| 1.8  | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)                                                | Domain Rules: Ticketing                           | 1    | P1  | FOLLOW  |
| 1.9  | [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)                                  | Domain Rules: Waitlist and Cancellation           | 1    | P1  | FOLLOW  |
| 1.10 | [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md)                                         | Domain Rules: Chart Preparation                   | 1    | P1  | FOLLOW  |
| 1.11 | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)                                   | Domain Rules: Seat Matrix and Inventory           | 1    | P1  | FOLLOW  |
| 1.12 | [SRIS-P1-REQ-012](./SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md)                                    | Requirement Traceability Matrix (RTM)             | 1    | P2  | FOLLOW  |
| 2.1  | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)                  | Microservices Identification                      | 2    | P0  | UNBLOCK |
| 2.11 | [SRIS-P1-ARCH-011](../wave-2-architecture/SRIS-P1-ARCH-011_ErrorHandlingAndResilienceDesign.md)             | Error Handling and Resilience Design              | 2    | P1  | FOLLOW  |
| 2.12 | [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)      | Observability and Monitoring Design (OTel/W3C)    | 2    | P0  | UNBLOCK |
| 2.14 | [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md)     | Distributed Concurrency and Locking Strategy      | 2    | P0  | UNBLOCK |
| 2.15 | [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md)   | Distributed Transaction and Saga Pattern Design   | 2    | P0  | UNBLOCK |
| 3.1  | [SRIS-P1-DATA-001](../wave-3-detailed-design/SRIS-P1-DATA-001_DataDesignDocument.md)                        | Data Design Document                              | 3    | P0  | UNBLOCK |
| 3.3  | [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)            | Physical Database Schema Document                 | 3    | P0  | UNBLOCK |
| 3.8  | [SRIS-P1-DATA-008](../wave-3-detailed-design/SRIS-P1-DATA-008_HighConcurrencySegmentInventoryDataModel.md)  | High-Concurrency Segment Inventory Data Model     | 3    | P0  | UNBLOCK |
| 3.9  | [SRIS-P1-DATA-009](../wave-3-detailed-design/SRIS-P1-DATA-009_SeatMatrixGenerationDesign.md)                | Seat Matrix Generation Design                     | 3    | P1  | FOLLOW  |
| 3.14 | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)                  | API Contract Document (OpenAPI)                   | 3    | P0  | UNBLOCK |
| 3.16 | [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md)                 | Event Schema Document (AsyncAPI)                  | 3    | P0  | UNBLOCK |
| 3.17 | [SRIS-P1-API-004](../wave-3-detailed-design/SRIS-P1-API-004_IntegrationDesignDocument.md)                   | Integration Design Document                       | 3    | P0  | UNBLOCK |
| 3.18 | [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md)      | Idempotency and Retry Policy Specification        | 3    | P0  | UNBLOCK |
| 3.19 | [SRIS-P1-API-006](../wave-3-detailed-design/SRIS-P1-API-006_APIErrorCodeCatalog.md)                         | API Error Code Catalog                            | 3    | P1  | FOLLOW  |
| 3.21 | [SRIS-P1-API-008](../wave-3-detailed-design/SRIS-P1-API-008_APIRateLimitingAndThrottlingRules.md)           | API Rate Limiting and Throttling Rules            | 3    | P2  | FOLLOW  |
| 3.23 | [SRIS-P1-API-010](../wave-3-detailed-design/SRIS-P1-API-010_APIGatewayConfigurationDocument.md)             | API Gateway Configuration Document                | 3    | P1  | FOLLOW  |
| 3.24 | [SRIS-P1-API-011](../wave-3-detailed-design/SRIS-P1-API-011_PaymentGatewayIntegrationDesignMock.md)         | Payment Gateway Integration Design (Mock)         | 3    | P1  | FOLLOW  |
| 3.25 | [SRIS-P1-API-012](../wave-3-detailed-design/SRIS-P1-API-012_NotificationIntegrationDesign.md)               | Notification Integration Design                   | 3    | P1  | FOLLOW  |
| 3.27 | [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md)                      | UI/UX Requirements Document                       | 3    | P0  | UNBLOCK |
| 3.29 | [SRIS-P1-UI-003](../wave-3-detailed-design/SRIS-P1-UI-003_WireframesCustomerFlow.md)                        | Wireframes (Customer Flow)                        | 3    | P0  | UNBLOCK |
| 3.30 | [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md)                   | Wireframes (Employee/Admin Flow)                  | 3    | P0  | UNBLOCK |
| 3.32 | [SRIS-P1-UI-006](../wave-3-detailed-design/SRIS-P1-UI-006_FormFieldSpecification.md)                        | Form Field Specification                          | 3    | P1  | FOLLOW  |
| 3.34 | [SRIS-P1-UI-008](../wave-3-detailed-design/SRIS-P1-UI-008_UIErrorAndNotificationDisplayRules.md)            | UI Error and Notification Display Rules           | 3    | P1  | FOLLOW  |
| 3.37 | [SRIS-P1-UI-011](../wave-3-detailed-design/SRIS-P1-UI-011_FrontendRoutingAndPageMap.md)                     | Frontend Routing and Page Map                     | 3    | P1  | FOLLOW  |
| 3.42 | [SRIS-P1-SEC-004](../wave-3-detailed-design/SRIS-P1-SEC-004_ThreatModel.md)                                 | Threat Model                                      | 3    | P1  | FOLLOW  |
| 3.44 | [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md)      | DPDP Act Compliance Framework (Phase 1 scoped)    | 3    | P0  | UNBLOCK |
| 3.49 | [SRIS-P1-SEC-012](../wave-3-detailed-design/SRIS-P1-SEC-012_DataClassificationRegister.md)                 | Data Classification Register                      | 3    | P0  | UNBLOCK |
| 3.50 | [SRIS-P1-SEC-013](../wave-3-detailed-design/SRIS-P1-SEC-013_SecureCodingStandards.md)                      | Secure Coding Standards                           | 3    | P0  | UNBLOCK |
| 4.3  | [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)                                | Test Cases (Functional)                           | 4    | P0  | UNBLOCK |
| 4.9  | [SRIS-P1-TEST-009](../wave-4-testing/SRIS-P1-TEST-009_LoadTestPlan.md)                                       | Load Test Plan                                    | 4    | P1  | FOLLOW  |
| 5.14 | [SRIS-P1-OPS-003](../wave-5-devops-operations/SRIS-P1-OPS-003_MonitoringAndAlertingGuide.md)                 | Monitoring and Alerting Guide                     | 5    | P1  | FOLLOW  |
| 9.1  | [SRIS-P1-NFR-HOLD-001](../wave-9-supporting-artifacts/SRIS-P1-NFR-HOLD-001_LoadModelAndResourceFitCheckHolding.md) | Load Model and Resource Fit Check (Holding)  | 9    | —   | HOLD    |

### B.2 Documents That Reference This Document

| Seq  | Document ID                                                                                 | Document Name                                 | Why It References                                                       |
| ---- | ------------------------------------------------------------------------------------------- | --------------------------------------------- | ----------------------------------------------------------------------- |
| 0.0  | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) | Documentation Index and Navigation Map        | Lists this document in the register and in the reading paths            |
| 0.4  | [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)      | Project Vision and Scope Document             | Lists this document as unblocked by its approval                        |
| 1.2  | [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md)                       | Business Requirements Document (BRD)          | Lists this document as a Hard downstream document                       |
| 1.3  | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)                                 | Capability Catalog (Final)                    | Names this document as the detailed rules owner for several capabilities |
| 2.1  | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)              | Microservices Identification                  | Lists this document as a Hard upstream document                         |

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
| 2.1 | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)             | Microservices Identification           | Hard            |

### B.4 Documents This Document Unblocks (Downstream)

| Seq  | Document ID                                                                      | Document Name                                | Blocked Until |
| ---- | -------------------------------------------------------------------------------- | -------------------------------------------- | ------------- |
| 1.5  | [SRIS-P1-REQ-005](./SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md)           | Non-Functional Requirements (ISO 25010)      | This approved |
| 1.6  | [SRIS-P1-REQ-006](./SRIS-P1-REQ-006_UserStoriesAndUseCases.md)                      | User Stories and Use Cases                   | This approved |
| 1.12 | [SRIS-P1-REQ-012](./SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md)            | Requirement Traceability Matrix (RTM)        | This approved |
| 4.3  | [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)         | Test Cases (Functional)                      | This approved |

### B.5 Master Documentation Index

The complete list of Phase 1 documents is in [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

### B.6 External Reference Documents

| Reference Type         | Where It Is Documented                                                                                                                |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| IEEE 830-1998          | Recommended Practice for Software Requirements Specifications. Withdrawn and superseded, referenced historically only.                 |
| ISO/IEC/IEEE 29148-2018| Systems and software engineering — Life cycle processes — Requirements engineering. The current standard referenced for SRS structure. |
| Karl Wiegers           | "Software Requirements". Referenced for the enterprise definition of an SRS.                                                            |

### B.7 Document Conventions

The conventions for Priority and Tag values are defined in [Section 9](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md#9-vocabulary-standards) of [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.

---

**End of Document**