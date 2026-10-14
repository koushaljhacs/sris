<div align="center">

![Wave](https://img.shields.io/badge/Wave-1-0550AE?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-REQ-6e7781?style=for-the-badge)

</div>

# Non-Functional Requirements (ISO 25010)

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** 1.0 | **Date:** 2026-10-15 | **Document ID:** SRIS-P1-REQ-005

| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| Title              | Non-Functional Requirements (ISO 25010)                           |
| Software           | SRIS                                                              |
| Software Full Form | Sarathi Railway Information System                                |
| Team Codename      | Project Sarathi                                                   |
| Document ID        | SRIS-P1-REQ-005                                                   |
| Task               | Specify the quality attributes that Phase 1 must satisfy          |
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
2. [Quality Model and Measurement](#2-quality-model-and-measurement)
   - [2.1 The ISO/IEC 25010:2023 Model](#21-the-isoiec-250102023-model)
   - [2.2 The Format of a Non-Functional Requirement](#22-the-format-of-a-non-functional-requirement)
   - [2.3 Provisional Numeric Targets](#23-provisional-numeric-targets)
   - [2.4 Boundary Rules](#24-boundary-rules)
3. [Functional Suitability](#3-functional-suitability)
4. [Performance Efficiency](#4-performance-efficiency)
   - [4.1 Latency](#41-latency)
   - [4.2 Throughput](#42-throughput)
   - [4.3 Memory Footprint](#43-memory-footprint)
   - [4.4 Resource Utilisation](#44-resource-utilisation)
5. [Compatibility](#5-compatibility)
   - [5.1 Browser Compatibility](#51-browser-compatibility)
   - [5.2 API Versioning](#52-api-versioning)
6. [Interaction Capability](#6-interaction-capability)
   - [6.1 Accessibility](#61-accessibility)
   - [6.2 Error Recovery](#62-error-recovery)
   - [6.3 Learnability](#63-learnability)
7. [Reliability](#7-reliability)
   - [7.1 Availability](#71-availability)
   - [7.2 Recovery](#72-recovery)
   - [7.3 Fault Isolation](#73-fault-isolation)
8. [Security](#8-security)
   - [8.1 Password Handling](#81-password-handling)
   - [8.2 Token Handling](#82-token-handling)
   - [8.3 DPDP Compliance](#83-dpdp-compliance)
   - [8.4 Field Masking](#84-field-masking)
   - [8.5 Rate Limiting](#85-rate-limiting)
9. [Maintainability](#9-maintainability)
   - [9.1 Modularity](#91-modularity)
   - [9.2 Testability](#92-testability)
   - [9.3 Code Documentation](#93-code-documentation)
10. [Flexibility](#10-flexibility)
    - [10.1 Environment Parity](#101-environment-parity)
    - [10.2 Cloud Swap by Orchestration Configuration](#102-cloud-swap-by-orchestration-configuration)
11. [Safety](#11-safety)
12. [Cross-Characteristic Trade-offs](#12-cross-characteristic-trade-offs)
13. [Traceability](#13-traceability)
14. [Approval](#14-approval)

- [Revision History](#revision-history)
- [Appendix A: ISO/IEC 25010:2023 Mapping Matrix](#appendix-a-isoiec-250102023-mapping-matrix)
- [Appendix B: Related Documents](#appendix-b-related-documents)

---

## 1. Introduction

### 1.1 Purpose

This document is the Non-Functional Requirements (NFR) specification of Phase 1 of SRIS (Sarathi Railway Information System). It states the quality attributes that the six microservices and the two user-facing surfaces must satisfy, structured against the product quality model of **ISO/IEC 25010:2023**.

The document does not restate the functional behaviour of the system. That behaviour is defined in [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software Requirements Specification (SRS), which specifies what the software must do. This document specifies how well the software must do it: its performance, its reliability, its security, its portability, and the other quality characteristics that determine whether the system is fit for its intended use. Every non-functional requirement is stated so that a reader can verify it by observation, inspection, or a named test method.

This document is the only register document that names a version of ISO 25010. Downstream documents cite this document for the quality model rather than citing the standard directly, so that any future revision of the standard affects only this document.

### 1.2 Scope

**In scope**

- The non-functional requirements of Phase 1, stated against the nine quality characteristics of ISO/IEC 25010:2023.
- The format of a non-functional requirement, including its identifier, its verification method, and its traceability fields.
- The marking of numeric targets as provisional until measurement data exists.
- The boundary rules that keep non-functional requirements distinct from design decisions, from test plans, and from service level objectives.
- The cross-characteristic trade-offs that apply when two quality requirements pull against each other.
- The traceability of every non-functional requirement to the capability or service that owns it.

**Out of scope**

- The business requirements, which are defined in [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD).
- The capabilities and their identifiers, which are defined in [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md) — Capability Catalog (Final).
- The functional software requirements, which are defined in [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software Requirements Specification (SRS).
- The user stories and use cases, which are defined in [SRIS-P1-REQ-006](./SRIS-P1-REQ-006_UserStoriesAndUseCases.md) — User Stories and Use Cases.
- The load model and resource fit numbers, which belong to [SRIS-P1-NFR-HOLD-001](../wave-9-supporting-artifacts/SRIS-P1-NFR-HOLD-001_LoadModelAndResourceFitCheckHolding.md) — Load Model and Resource Fit Check (Holding).
- The choice of technology stack, which belongs to [SRIS-P1-ARCH-008](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md) — Technology Stack ADR.
- The observability and tracing design, which belongs to [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md) — Observability and Monitoring Design (OTel/W3C).
- The concurrency and locking strategy, which belongs to [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md) — Distributed Concurrency and Locking Strategy.
- The authentication and authorisation design, which belongs to [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md) — Authentication and Authorization Design, [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md) — RBAC Matrix, and [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md) — JWT Token Design and Claims.
- The service level objectives, which belong to [SRIS-P1-OPS-005](../wave-5-devops-operations/SRIS-P1-OPS-005_SLODocument.md) — SLO Document.
- The performance test plan, which belongs to [SRIS-P1-TEST-008](../wave-4-testing/SRIS-P1-TEST-008_PerformanceTestPlan.md) — Performance Test Plan.
- The load test plan, which belongs to [SRIS-P1-TEST-009](../wave-4-testing/SRIS-P1-TEST-009_LoadTestPlan.md) — Load Test Plan.
- The security testing plan, which belongs to [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md) — Security Testing Plan.

### 1.3 Audience

- **Lead Architect:** maintains this document and approves every non-functional requirement.
- **Backend and frontend developers:** build the system so that the quality attributes stated here are satisfied.
- **Tester (QA):** derives the performance, security, and accessibility test cases from this document and executes them against the verification methods stated here.
- **DevOps engineer:** uses the portability requirements in [Section 10](#10-flexibility) to shape the deployment configuration and the environment strategy.
- **Project supervisor and evaluator:** uses this document to judge whether Phase 1 satisfies its quality obligations, not only its functional obligations.
- **Technical reviewers:** engineers or interviewers who open the repository and need the quality baseline of Phase 1.

### 1.4 Terminology and Conventions

Every term in this document has the meaning recorded in [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary. The terms below carry the most weight in this document, and are used with the meanings defined there.

| Term                        | Meaning                                                                                                            |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Quality characteristic      | A broad category of software quality, such as Performance Efficiency or Security.                                   |
| Quality sub-characteristic  | A measurable attribute inside a quality characteristic, such as latency inside Performance Efficiency.              |
| Non-functional requirement  | A statement of an observable quality property that the system must satisfy, with a verification method.              |
| Provisional target          | A numeric value written before measurement exists, marked as "proposed, pending confirmation" and revised later.    |
| Verification method         | The observable test, inspection, or analysis by which the requirement is proven.                                    |
| Service level objective     | An operational percentage target measured over a rolling time window. It is distinct from a non-functional requirement. |

The identifier prefix below is local to this document.

| Prefix | Meaning                  |
| ------ | ------------------------ |
| NFR    | Non-functional requirement |

This document follows the standards below.

- [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard, for structure, header, and style.
- [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md) — Document ID and Category Scheme, for the Document ID.
- [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md) — Document Cross-Reference Standard, for citations and links.
- **ISO/IEC 25010:2023** — Systems and software engineering — Systems and software Quality Requirements and Evaluation (SQuaRE) — Product quality model. Published 2023-11-15. This is the current version of the standard and the one used in this document. The 2011 version that preceded it is withdrawn.

---

## 2. Quality Model and Measurement

### 2.1 The ISO/IEC 25010:2023 Model

ISO/IEC 25010:2023 defines nine quality characteristics. Each characteristic is a broad category of software quality, and each is decomposed into sub-characteristics that can be measured. This document uses the 2023 model, not the 2011 model, because the 2011 edition is withdrawn and the 2023 edition adds Safety as a first-class characteristic and expands several existing ones.

The nine characteristics used in this document are listed below, with the sub-characteristics that apply to SRIS Phase 1. The mapping to the register is recorded in [Appendix A](#appendix-a-isoiec-250102023-mapping-matrix).

| # | Characteristic         | Sub-characteristics Relevant to SRIS Phase 1                                              |
| - | ---------------------- | ------------------------------------------------------------------------------------------ |
| 1 | Functional Suitability | Functional correctness, functional appropriateness                                         |
| 2 | Performance Efficiency | Time behaviour, resource utilisation, capacity                                             |
| 3 | Compatibility          | Co-existence, interoperability                                                             |
| 4 | Interaction Capability | Appropriateness recognisability, learnability, operability, user error protection, inclusivity |
| 5 | Reliability            | Faultlessness, availability, fault tolerance, recoverability                               |
| 6 | Security               | Confidentiality, integrity, non-repudiation, accountability, authenticity, resistance       |
| 7 | Maintainability        | Modularity, reusability, analysability, modifiability, testability                         |
| 8 | Flexibility            | Adaptability, scalability, installability, replaceability                                  |
| 9 | Safety                 | Operational constraint, risk identification, fail-safe, hazard warning, safe integration    |

Two sub-characteristics are intentionally excluded because Phase 1 has no applicable requirement:

- **Appropriateness recognisability** under Interaction Capability — the surfaces have no requirement to teach the user what the software can do, since the deliverable is a working transaction, not a product launch.
- **Non-repudiation** under Security — every transaction in Phase 1 is executed by an authenticated customer against a mock payment gateway, and no external party can repudiate a transaction that is not real.

The exclusions are recorded here so that a reviewer sees a decision, not an omission. If a later revision introduces either sub-characteristic, this subsection is where it is recorded.

### 2.2 The Format of a Non-Functional Requirement

A non-functional requirement in this document has the following form.

**NFR-NNN:** `<quality property that the system must satisfy>`

- **Target:** `<the measurable value the property must meet, or the observable condition that the property must hold>`
- **Verification:** `<the observable method by which the property is proven>`
- **Quality Characteristic:** `<one of the nine ISO/IEC 25010:2023 characteristics>`
- **Sub-characteristic:** `<the specific sub-characteristic within it>`
- **Applies To:** `<services, surfaces, or the system as a whole>`


Every field is required.

- **NFR-NNN** is a stable identifier. It is never reused.
- **The quality property** is stated so that a reader can verify it from outside. It describes the observable condition the system must meet.
- **Target** is either a numeric value (marked "proposed, pending confirmation" if measurement does not exist yet) or a binary observable condition (such as "deployable to a cloud host by changing only the orchestration configuration").
- **Verification** names the specific method by which the target is proven. The method is one of: **test** (with the test owner named), **inspection** (with the document inspected), **analysis** (with the analysis method named), or **demonstration** (with the demo scene named).
- **Quality Characteristic** names the ISO/IEC 25010:2023 characteristic this requirement sits under.
- **Sub-characteristic** names the specific sub-characteristic within that characteristic.
- **Applies To** names the services, the surfaces, or the whole system that must satisfy the requirement.

### 2.3 Provisional Numeric Targets

Phase 1 begins without measurement data. The system has not been built and no benchmark exists. Every numeric target in this document is therefore written as a **provisional target**, marked **"proposed, pending confirmation"**, following the precedent already set in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document for SC-5 and SC-6.

A provisional target is not an arbitrary guess. It is derived from one of:

- A fixed constraint already in the register, such as the 5.1 GB RAM ceiling in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) constraint C-2.
- A domain standard, such as the ten-digit PNR format defined in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing.
- An industry reference point, such as the p95 latency target of a public web service.
- A judgement by the Lead Architect, stated as a judgement.

The register's procedure for provisional targets is:

1. **v1.0 of this document** writes each numeric target as provisional.
2. **Week 4 of Phase 1** runs the first measurement under [SRIS-P1-TEST-009](../wave-4-testing/SRIS-P1-TEST-009_LoadTestPlan.md) — Load Test Plan.
3. **v1.1 of this document** replaces every provisional target that has been measured with its measured value, and adds a Revision History row that records the replacement.
4. Every downstream document that cites a numeric target cites the current version of this document.

A provisional target that has not been measured by the end of Phase 1 remains marked "proposed, pending confirmation" in the final version. It is not promoted to a confirmed value by default.

### 2.4 Boundary Rules

A non-functional requirement sits at a specific point in the register. Three boundary rules decide what belongs in this document and what does not. Each rule is stated so that a reviewer can apply it.

**Rule 1 — NFR versus design decision.**

If a statement describes **how** the system achieves a quality, it is a design decision and belongs in an ARCH document. If a statement describes **what observable quality** the system must achieve, it is a non-functional requirement and belongs here.

An example: *"The system must return a search response in under two seconds"* is an NFR. *"The system must cache station data in memory to reduce search latency"* is a design decision and belongs in [SRIS-P1-ARCH-003](../wave-2-architecture/SRIS-P1-ARCH-003_SystemArchitectureDocument.md) — System Architecture Document or in [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md) — Observability and Monitoring Design (OTel/W3C).

**Rule 2 — NFR versus test plan.**

If a statement describes the environment, the tooling, the load simulation parameters, or the procedural steps to measure a metric, it is a test plan and belongs in a TEST document. If a statement states the threshold that must be met during that test, it is a non-functional requirement and belongs here.

An example: *"The load test must simulate 100 concurrent users for 30 minutes using k6"* belongs in [SRIS-P1-TEST-009](../wave-4-testing/SRIS-P1-TEST-009_LoadTestPlan.md) — Load Test Plan. *"The system must sustain 100 concurrent bookings with a p95 confirmation latency of three seconds"* belongs here.

**Rule 3 — NFR versus service level objective.**

If a statement defines an **absolute, structural constraint** required for release, it is a non-functional requirement and belongs here. If a statement defines an **ongoing, operational percentage target** measured over a rolling time window, it is a service level objective and belongs in [SRIS-P1-OPS-005](../wave-5-devops-operations/SRIS-P1-OPS-005_SLODocument.md) — SLO Document.

An example: *"The system must isolate failures between microservices so that the failure of one service does not crash another"* is an NFR. *"99.5% of booking confirmations over a 30-day window must complete successfully"* is an SLO.

These three rules are the only test a reviewer needs when deciding whether a proposed statement belongs in this document, in a design document, in a test plan, or in the SLO document.

---

## 3. Functional Suitability

The Functional Suitability characteristic covers the degree to which the system provides functions that meet stated and implied needs when used under specified conditions. In SRIS the functional behaviour itself is defined in [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software Requirements Specification (SRS). This section covers only the quality slice that REQ-004 does not own: the correctness and appropriateness of the algorithms that those functions exercise, as an observable quality property rather than a functional behaviour.

The requirements below are few in number, because Functional Suitability is largely a functional concern and would otherwise duplicate REQ-004. They are recorded here only because they state a quality obligation that survives any change to the functional specification.

---

**NFR-001: Fare Re-Quote Determinism**

The system must produce the same fare re-quote for the same set of inputs — same train, same class, same quota, same journey segment, same passenger list, same applicable rule versions — on every invocation, with no variance between calls made inside the same second.

**Target:** 100% identical responses for identical inputs inside the same second, verified across 100 consecutive calls.

**Verification:** Test. Executed by [SRIS-P1-TEST-008](../wave-4-testing/SRIS-P1-TEST-008_PerformanceTestPlan.md) — Performance Test Plan.

**Quality Characteristic:** Functional Suitability
**Sub-characteristic:** Functional Correctness
**Applies To:** S2 Master Data and Pricing Service

---

**NFR-002: PNR Format Correctness**

Every generated PNR must satisfy the format rules defined in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing. No PNR may be generated that violates the format, regardless of load.

**Target:** 100% of generated PNRs conform to the format rule. Zero non-conforming PNRs across the full Phase 1 demo run.

**Verification:** Test. Executed by [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md) — Test Cases (Functional).

**Quality Characteristic:** Functional Suitability
**Sub-characteristic:** Functional Correctness
**Applies To:** S3 Reservation Service

---

**NFR-003: Booking State Machine Integrity**

A booking must never occupy a state that the state machine in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing does not define, and must never move between two states that the machine does not permit.

**Target:** Zero invalid states and zero illegal transitions across the full Phase 1 demo run.

**Verification:** Test. Executed by [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md) — Test Cases (Functional), using an invariant checker that runs after every transition.

**Quality Characteristic:** Functional Suitability
**Sub-characteristic:** Functional Correctness
**Applies To:** S3 Reservation Service

---

**NFR-004: Functional Completeness of the Booking Flow**

The ten-step booking flow defined in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document must be executable end to end without manual data intervention at any step.

**Target:** A single demo run executes all ten steps with zero manual data edits. This target is binary and does not require measurement.

**Verification:** Demonstration. Executed during the Phase 1 demo run as defined in [SRIS-P1-USR-007](../wave-8-user-support/SRIS-P1-USR-007_DemoScenariosAndWalkthroughScript.md) — Demo Scenarios and Walkthrough Script.

**Quality Characteristic:** Functional Suitability
**Sub-characteristic:** Functional Completeness
**Applies To:** System-wide

---

## 4. Performance Efficiency

The Performance Efficiency characteristic covers the degree to which the system uses time and resources under stated conditions. In SRIS this characteristic is constrained on both sides: by the 5.1 GB RAM ceiling in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document constraint C-2, and by the user experience expected of a reservation system. The load and resource fit numbers themselves belong to [SRIS-P1-NFR-HOLD-001](../wave-9-supporting-artifacts/SRIS-P1-NFR-HOLD-001_LoadModelAndResourceFitCheckHolding.md) — Load Model and Resource Fit Check (Holding). The requirements below state the thresholds that load and resource validation must confirm.

Every numeric target in this section is provisional. It is derived from the fixed constraint, from an industry reference point, or from the Lead Architect's judgement. Each is revised after Week 4 measurement.

### 4.1 Latency

---

**NFR-005: Search Response Latency**

The system must return a search response to the client within the stated budget. The budget covers the whole round trip from the client request to the client response, including the aggregation across [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification S2 and S3.

**Target:** p95 search latency of 2,000 milliseconds; p99 of 4,000 milliseconds. Both proposed, pending confirmation.

**Verification:** Test. Executed by [SRIS-P1-TEST-008](../wave-4-testing/SRIS-P1-TEST-008_PerformanceTestPlan.md) — Performance Test Plan.

**Quality Characteristic:** Performance Efficiency
**Sub-characteristic:** Time Behaviour
**Applies To:** S4 Search Aggregator BFF

---

**NFR-006: Booking Confirmation Latency**

The system must return a booking confirmation response within the stated budget. The budget covers the whole sequence from the customer submitting payment to the client receiving the PNR.

**Target:** p95 booking confirmation latency of 3,000 milliseconds; p99 of 6,000 milliseconds. Both proposed, pending confirmation.

**Verification:** Test. Executed by [SRIS-P1-TEST-008](../wave-4-testing/SRIS-P1-TEST-008_PerformanceTestPlan.md) — Performance Test Plan.

**Quality Characteristic:** Performance Efficiency
**Sub-characteristic:** Time Behaviour
**Applies To:** S3 Reservation Service, S5 Mock Payment Gateway

---

**NFR-007: Authentication Response Latency**

The system must return the result of a login or token refresh request within the stated budget.

**Target:** p95 authentication latency of 500 milliseconds; p99 of 1,000 milliseconds. Both proposed, pending confirmation.

**Verification:** Test. Executed by [SRIS-P1-TEST-008](../wave-4-testing/SRIS-P1-TEST-008_PerformanceTestPlan.md) — Performance Test Plan.

**Quality Characteristic:** Performance Efficiency
**Sub-characteristic:** Time Behaviour
**Applies To:** S1 IAM Service

---

**NFR-008: Master Data Write Latency**

The system must return the result of a master-data create or update request to the employee within the stated budget. The budget does not cover the persistence of the accompanying audit entry, which is written before the response is returned.

**Target:** p95 master-data write latency of 800 milliseconds; p99 of 1,500 milliseconds. Both proposed, pending confirmation.

**Verification:** Test. Executed by [SRIS-P1-TEST-008](../wave-4-testing/SRIS-P1-TEST-008_PerformanceTestPlan.md) — Performance Test Plan.

**Quality Characteristic:** Performance Efficiency
**Sub-characteristic:** Time Behaviour
**Applies To:** S2 Master Data and Pricing Service

---

**NFR-009: Notification Dispatch Latency**

Once a booking is confirmed, the system must dispatch the confirmation email and SMS within the stated budget, measured from the moment the booking event is published.

**Target:** p95 notification dispatch latency of 30,000 milliseconds; p99 of 60,000 milliseconds. Both proposed, pending confirmation.

**Verification:** Test. Executed by [SRIS-P1-TEST-010](../wave-4-testing/SRIS-P1-TEST-010_IntegrationTestPlan.md) — Integration Test Plan.

**Quality Characteristic:** Performance Efficiency
**Sub-characteristic:** Time Behaviour
**Applies To:** S6 Notification Service

---

### 4.2 Throughput

---

**NFR-010: Concurrent Booking Throughput**

The system must sustain concurrent booking confirmations during the Phase 1 demo load. The load model itself belongs to [SRIS-P1-NFR-HOLD-001](../wave-9-supporting-artifacts/SRIS-P1-NFR-HOLD-001_LoadModelAndResourceFitCheckHolding.md) — Load Model and Resource Fit Check (Holding). This requirement states the observable throughput the system must hold.

**Target:** The system must complete 50 concurrent booking confirmations without error, within a five-minute window. Proposed, pending confirmation.

**Verification:** Test. Executed by [SRIS-P1-TEST-009](../wave-4-testing/SRIS-P1-TEST-009_LoadTestPlan.md) — Load Test Plan.

**Quality Characteristic:** Performance Efficiency
**Sub-characteristic:** Capacity
**Applies To:** S3 Reservation Service

---

**NFR-011: Concurrent Search Throughput**

The system must sustain concurrent search requests from the demo load without producing error responses.

**Target:** The system must serve 200 concurrent search requests without error, within a five-minute window. Proposed, pending confirmation.

**Verification:** Test. Executed by [SRIS-P1-TEST-009](../wave-4-testing/SRIS-P1-TEST-009_LoadTestPlan.md) — Load Test Plan.

**Quality Characteristic:** Performance Efficiency
**Sub-characteristic:** Capacity
**Applies To:** S4 Search Aggregator BFF

---

**NFR-012: Concurrent Authentication Throughput**

The system must sustain concurrent login and token-refresh requests during the demo load.

**Target:** The system must serve 100 concurrent authentication requests without error, within a five-minute window. Proposed, pending confirmation.

**Verification:** Test. Executed by [SRIS-P1-TEST-009](../wave-4-testing/SRIS-P1-TEST-009_LoadTestPlan.md) — Load Test Plan.

**Quality Characteristic:** Performance Efficiency
**Sub-characteristic:** Capacity
**Applies To:** S1 IAM Service

---

### 4.3 Memory Footprint

---

**NFR-013: Combined Memory Footprint of the Six Services**

The complete Phase 1 environment — six microservices, their data stores, the event backbone, and the API gateway — must run within the RAM ceiling fixed in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document constraint C-2.

**Target:** Combined peak memory footprint of the running environment must not exceed 5.1 GB. This target is fixed, not provisional, because it is drawn from a register constraint.

**Verification:** Test. Executed by [SRIS-P1-NFR-HOLD-001](../wave-9-supporting-artifacts/SRIS-P1-NFR-HOLD-001_LoadModelAndResourceFitCheckHolding.md) — Load Model and Resource Fit Check (Holding).

**Quality Characteristic:** Performance Efficiency
**Sub-characteristic:** Resource Utilisation
**Applies To:** System-wide

---

**NFR-014: Per-Service Memory Ceiling**

Each of the six microservices must stay within a per-service memory ceiling during the demo load, so that no single service monopolises the shared budget.

**Target:** No single service must exceed 800 MB resident memory during the demo run. Proposed, pending confirmation.

**Verification:** Test. Executed by [SRIS-P1-NFR-HOLD-001](../wave-9-supporting-artifacts/SRIS-P1-NFR-HOLD-001_LoadModelAndResourceFitCheckHolding.md) — Load Model and Resource Fit Check (Holding).

**Quality Characteristic:** Performance Efficiency
**Sub-characteristic:** Resource Utilisation
**Applies To:** S1, S2, S3, S4, S5, S6

---

**NFR-015: No Memory Leak Across the Demo Run**

The system must not exhibit unbounded memory growth during the demo run. Resident memory after sustained load must not grow beyond a bounded envelope.

**Target:** Memory growth after 30 minutes of sustained load must not exceed 10% of the starting resident memory. Proposed, pending confirmation.

**Verification:** Test. Executed by [SRIS-P1-TEST-009](../wave-4-testing/SRIS-P1-TEST-009_LoadTestPlan.md) — Load Test Plan.

**Quality Characteristic:** Performance Efficiency
**Sub-characteristic:** Resource Utilisation
**Applies To:** S1, S2, S3, S4, S5, S6

---

### 4.4 Resource Utilisation

---

**NFR-016: CPU Utilisation During Sustained Load**

The system must sustain the demo load without saturating the available CPU on the local server.

**Target:** Average CPU utilisation across the sustained-load window must remain below 75% on the local server. Proposed, pending confirmation.

**Verification:** Test. Executed by [SRIS-P1-NFR-HOLD-001](../wave-9-supporting-artifacts/SRIS-P1-NFR-HOLD-001_LoadModelAndResourceFitCheckHolding.md) — Load Model and Resource Fit Check (Holding).

**Quality Characteristic:** Performance Efficiency
**Sub-characteristic:** Resource Utilisation
**Applies To:** System-wide

---

**NFR-017: Database Connection Pool Bounds**

Every service that owns a data store must operate within a bounded database connection pool. The service must not open unbounded connections under load.

**Target:** Zero unbounded connection growth across the sustained-load window. The exact pool size belongs to [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md) — Distributed Concurrency and Locking Strategy.

**Verification:** Inspection. The pool configuration is inspected against the concurrency strategy.

**Quality Characteristic:** Performance Efficiency
**Sub-characteristic:** Resource Utilisation
**Applies To:** S1, S2, S3

---

## 5. Compatibility

The Compatibility characteristic covers the degree to which the system can exchange information with other products, systems, or components, and perform its required functions while sharing the same environment. In SRIS this covers two things: the browser and device envelope of the two surfaces, and the version-compatibility rules between the six microservices.

### 5.1 Browser Compatibility

---

**NFR-018: Customer Surface Browser Support**

The Customer Booking Website must operate correctly on the current and prior major versions of the mainstream browsers used by Indian consumers.

**Target:** Correct operation on Chrome, Edge, Firefox, and Safari, at the current and one prior major version of each. This target is binary and does not require measurement.

**Verification:** Test. Executed by [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md) — Test Cases (UI).

**Quality Characteristic:** Compatibility
**Sub-characteristic:** Interoperability
**Applies To:** Customer Booking Website

---

**NFR-019: Employee Surface Browser Support**

The Employee Admin Console must operate correctly on the same browser envelope as the Customer Booking Website.

**Target:** Correct operation on Chrome, Edge, Firefox, and Safari, at the current and one prior major version of each. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md) — Test Cases (UI).

**Quality Characteristic:** Compatibility
**Sub-characteristic:** Interoperability
**Applies To:** Employee Admin Console

---

**NFR-020: Mobile Viewport Compatibility**

The Customer Booking Website must render without horizontal scroll and without overlap on viewports as narrow as 360 CSS pixels.

**Target:** No horizontal scroll and no overlapping elements at 360 CSS pixels width, on every screen in the customer flow. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md) — Test Cases (UI).

**Quality Characteristic:** Compatibility
**Sub-characteristic:** Adaptability
**Applies To:** Customer Booking Website

---

### 5.2 API Versioning

---

**NFR-021: API Version Co-existence**

The system must support two API versions of the same service co-existing simultaneously during the transition window, so that a client on the older version is not broken by a newer version.

**Target:** Both the current and the previous major version of every service API must be available simultaneously for the duration of the transition window. The transition window and the versioning scheme belong to [SRIS-P1-API-013](../wave-3-detailed-design/SRIS-P1-API-013_APIVersioningAndDeprecationPolicy.md) — API Versioning and Deprecation Policy.

**Verification:** Inspection. The API versioning policy document is inspected against this requirement.

**Quality Characteristic:** Compatibility
**Sub-characteristic:** Co-existence
**Applies To:** S1, S2, S3, S4

---

**NFR-022: Deprecation Window**

When a service API version is deprecated, the system must continue to serve the deprecated version for at least the minimum window defined in [SRIS-P1-API-013](../wave-3-detailed-design/SRIS-P1-API-013_APIVersioningAndDeprecationPolicy.md) — API Versioning and Deprecation Policy.

**Target:** A deprecated version must be served for at least the window stated in the policy. Binary target.

**Verification:** Inspection. The API versioning policy document is inspected against this requirement.

**Quality Characteristic:** Compatibility
**Sub-characteristic:** Co-existence
**Applies To:** S1, S2, S3, S4

---

## 6. Interaction Capability

The Interaction Capability characteristic covers the degree to which the system can be used by specified users to achieve specified goals with effectiveness, efficiency, and satisfaction in a specified context of use. In the 2023 version of ISO/IEC 25010 the former Usability characteristic was renamed and expanded to include inclusivity, self-descriptiveness, and user engagement. In SRIS the applicable sub-characteristics are accessibility, error recovery, and learnability. Visual design and wireframes belong to [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md) to [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md) and are not defined here.

### 6.1 Accessibility

---

**NFR-023: WCAG Colour Contrast**

Every text and interactive element on both surfaces must meet the WCAG 2.2 AA colour contrast requirement against its background.

**Target:** Minimum contrast ratio of 4.5:1 for normal text, and 3:1 for large text and interactive elements, on every screen. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md) — Test Cases (UI), using an automated contrast checker on every screen.

**Quality Characteristic:** Interaction Capability
**Sub-characteristic:** Inclusivity
**Applies To:** Customer Booking Website, Employee Admin Console

---

**NFR-024: Keyboard Operability**

Every action available through the mouse on both surfaces must be reachable by keyboard alone, in a logical tab order.

**Target:** Every interactive element is keyboard-reachable, and the tab order matches the visual reading order, on every screen. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md) — Test Cases (UI).

**Quality Characteristic:** Interaction Capability
**Sub-characteristic:** Operability
**Applies To:** Customer Booking Website, Employee Admin Console

---

**NFR-025: Screen Reader Announcement of Errors**

Every form validation error on both surfaces must be announced to assistive technology, not only displayed visually.

**Target:** Every server-side and client-side validation error is announced through the appropriate ARIA mechanism. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md) — Test Cases (UI).

**Quality Characteristic:** Interaction Capability
**Sub-characteristic:** Inclusivity
**Applies To:** Customer Booking Website, Employee Admin Console

---

### 6.2 Error Recovery

---

**NFR-026: No Stack Trace Disclosure**

No error response returned by any service to any client may include a stack trace, a source file path, a database query, or any internal identifier that reveals the internal implementation.

**Target:** Zero disclosures across the full Phase 1 demo run and across every security test. Binary target.

**Verification:** Test. Executed by [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md) — Security Testing Plan.

**Quality Characteristic:** Interaction Capability
**Sub-characteristic:** User Error Protection
**Applies To:** S1, S2, S3, S4, S5, S6

---

**NFR-027: Customer-Recoverable Errors**

Every validation error and every recoverable business error shown on the Customer Booking Website must present a corrective action the customer can take, not only a description of the failure.

**Target:** Every recoverable error includes at least one actionable next step. Binary target.

**Verification:** Inspection. The error catalogue in [SRIS-P1-API-006](../wave-3-detailed-design/SRIS-P1-API-006_APIErrorCodeCatalog.md) — API Error Code Catalog is inspected against this requirement, and the display rules are inspected in [SRIS-P1-UI-008](../wave-3-detailed-design/SRIS-P1-UI-008_UIErrorAndNotificationDisplayRules.md) — UI Error and Notification Display Rules.

**Quality Characteristic:** Interaction Capability
**Sub-characteristic:** User Error Protection
**Applies To:** Customer Booking Website

---

**NFR-028: Preserve Form State on Recoverable Failure**

When a form submission fails on a recoverable error, the surface must preserve the user's input so that the user does not retype it.

**Target:** Every recoverable form failure preserves all previously entered values in the form. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md) — Test Cases (UI).

**Quality Characteristic:** Interaction Capability
**Sub-characteristic:** User Error Protection
**Applies To:** Customer Booking Website, Employee Admin Console

---

### 6.3 Learnability

---

**NFR-029: First-Time Booking Without Documentation**

A first-time customer must be able to complete a booking from search to confirmed PNR without external documentation or help.

**Target:** A first-time user completes the booking flow in under 8 minutes, unaided. Proposed, pending confirmation.

**Verification:** Demonstration. Executed during the Phase 1 demo run as defined in [SRIS-P1-USR-007](../wave-8-user-support/SRIS-P1-USR-007_DemoScenariosAndWalkthroughScript.md) — Demo Scenarios and Walkthrough Script.

**Quality Characteristic:** Interaction Capability
**Sub-characteristic:** Learnability
**Applies To:** Customer Booking Website

---

**NFR-030: First-Time Master Data Entry Without Documentation**

A first-time employee must be able to complete a station creation, a route creation, and a schedule creation without external documentation or help.

**Target:** A first-time employee completes all three master-data tasks in under 15 minutes, unaided. Proposed, pending confirmation.

**Verification:** Demonstration. Executed during the Phase 1 demo run as defined in [SRIS-P1-USR-007](../wave-8-user-support/SRIS-P1-USR-007_DemoScenariosAndWalkthroughScript.md) — Demo Scenarios and Walkthrough Script.

**Quality Characteristic:** Interaction Capability
**Sub-characteristic:** Learnability
**Applies To:** Employee Admin Console

---

**NFR-031: Consistent Interaction Vocabulary**

The two surfaces must use the same term for the same concept wherever a concept appears on both. The vocabulary is fixed by [SRIS-P1-REQ-001](./SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary.

**Target:** Zero cases where the same concept is named by two different terms across the two surfaces. Binary target.

**Verification:** Inspection. Every screen label is checked against the glossary.

**Quality Characteristic:** Interaction Capability
**Sub-characteristic:** Appropriateness Recognisability
**Applies To:** Customer Booking Website, Employee Admin Console

---

## 7. Reliability

The Reliability characteristic covers the degree to which a system performs specified functions under specified conditions for a specified period of time. In SRIS the reliability requirements cover three things: availability during the demo phase, recovery after failure, and isolation of failure between services. The service level objectives — the rolling percentage targets measured over time — belong to [SRIS-P1-OPS-005](../wave-5-devops-operations/SRIS-P1-OPS-005_SLODocument.md) — SLO Document. The requirements below state the structural reliability properties that the system must hold at all times.

### 7.1 Availability

---

**NFR-032: Continuous Availability During the Demo Run**

The system must remain available throughout the Phase 1 demonstration run, with no unplanned outage between the start and the end of the demo.

**Target:** Zero unplanned outages during a demo run of up to sixty minutes. Binary target.

**Verification:** Demonstration. Observed during the Phase 1 demo run as defined in [SRIS-P1-USR-007](../wave-8-user-support/SRIS-P1-USR-007_DemoScenariosAndWalkthroughScript.md) — Demo Scenarios and Walkthrough Script.

**Quality Characteristic:** Reliability
**Sub-characteristic:** Availability
**Applies To:** System-wide

---

**NFR-033: All Six Services Available Simultaneously**

Every one of the six microservices defined in [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification must be reachable and healthy at the start of the demo run.

**Target:** All six health check endpoints return a healthy status within 60 seconds of the demo environment starting up. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-010](../wave-4-testing/SRIS-P1-TEST-010_IntegrationTestPlan.md) — Integration Test Plan.

**Quality Characteristic:** Reliability
**Sub-characteristic:** Availability
**Applies To:** S1, S2, S3, S4, S5, S6

---

### 7.2 Recovery

---

**NFR-034: State Recovery After Service Restart**

Every service that owns persistent state must recover that state correctly after an unplanned restart, with no loss of committed data.

**Target:** Every committed transaction is present after a service restart. Zero data loss for committed state. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-010](../wave-4-testing/SRIS-P1-TEST-010_IntegrationTestPlan.md) — Integration Test Plan.

**Quality Characteristic:** Reliability
**Sub-characteristic:** Recoverability
**Applies To:** S1, S2, S3, S6

---

**NFR-035: Booking Recovery After Database Restart**

If the Reservation Service's data store restarts while a booking is in an intermediate state, the booking must be recoverable to a consistent state on the next request, with either confirmation or release per the mechanism in [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing.

**Target:** Every booking that was in an intermediate state at the moment of a data-store restart is resolved to either confirmed, waitlisted, or refunded within two minutes of the service returning. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-010](../wave-4-testing/SRIS-P1-TEST-010_IntegrationTestPlan.md) — Integration Test Plan.

**Quality Characteristic:** Reliability
**Sub-characteristic:** Recoverability
**Applies To:** S3 Reservation Service

---

**NFR-036: Idempotent Recovery of In-Flight Requests**

If a client retries a request after a network timeout, the system must not create a duplicate state change, provided the retry carries the same idempotency key. The mechanism belongs to [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md) — Idempotency and Retry Policy Specification.

**Target:** Zero duplicate state changes across 100 consecutive retry tests. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-004](../wave-4-testing/SRIS-P1-TEST-004_ConsumerDrivenContractTestingStrategy.md) — Consumer-Driven Contract Testing Strategy.

**Quality Characteristic:** Reliability
**Sub-characteristic:** Fault Tolerance
**Applies To:** S1, S2, S3, S5

---

### 7.3 Fault Isolation

---

**NFR-037: Failure of One Service Does Not Cascade**

A failure of any single microservice must not cause the other five to fail. The system must continue to serve requests that do not depend on the failed service.

**Target:** When any one of the six services is taken down, the other five remain healthy and continue to serve their endpoints. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-010](../wave-4-testing/SRIS-P1-TEST-010_IntegrationTestPlan.md) — Integration Test Plan.

**Quality Characteristic:** Reliability
**Sub-characteristic:** Fault Tolerance
**Applies To:** S1, S2, S3, S4, S5, S6

---

**NFR-038: Notification Failure Does Not Block Booking**

A failure of the Notification Service must not fail or block a booking. This requirement enforces Business Rule BRL-5 in [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD) at the reliability layer.

**Target:** With the Notification Service taken down, every booking still completes successfully, and the customer still receives the PNR in the response. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-010](../wave-4-testing/SRIS-P1-TEST-010_IntegrationTestPlan.md) — Integration Test Plan.

**Quality Characteristic:** Reliability
**Sub-characteristic:** Fault Tolerance
**Applies To:** S3 Reservation Service, S6 Notification Service

---

**NFR-039: Payment Gateway Failure Does Not Corrupt Booking**

A failure of the Mock Payment Gateway must not leave a booking in an inconsistent state. The booking must resolve to either confirmed with a valid payment record, or refunded with no seat held.

**Target:** Every booking whose payment attempt fails at the gateway is resolved to confirmed or refunded within two minutes. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-010](../wave-4-testing/SRIS-P1-TEST-010_IntegrationTestPlan.md) — Integration Test Plan.

**Quality Characteristic:** Reliability
**Sub-characteristic:** Fault Tolerance
**Applies To:** S3 Reservation Service, S5 Mock Payment Gateway

---

**NFR-040: Graceful Degradation of Search**

If the Master Data and Pricing Service is slow or unavailable, the Search Aggregator BFF must return the parts of the search result that it can serve, with the missing parts marked as unavailable, rather than returning an error that hides the partial result.

**Target:** Every search response under partial dependency failure returns at least the schedule data or returns a partial-response marker; it never returns an empty error. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-010](../wave-4-testing/SRIS-P1-TEST-010_IntegrationTestPlan.md) — Integration Test Plan.

**Quality Characteristic:** Reliability
**Sub-characteristic:** Fault Tolerance
**Applies To:** S4 Search Aggregator BFF

---

## 8. Security

The Security characteristic covers the degree to which a system protects information and data so that persons or other products have the degree of data access appropriate to their types and levels of authorisation. In SRIS the security requirements are constrained by the Data Protection framework in [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md) — DPDP Act Compliance Framework (Phase 1 scoped) and by the register's own commitment to data minimisation. The design of authentication, RBAC, and token handling belongs to [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md) to [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md). The requirements below state the observable security properties that the design must satisfy.

### 8.1 Password Handling

---

**NFR-041: Password Hashing Algorithm Strength**

Every stored password must be protected by a strong, memory-hard cryptographic hash, and must never be stored in plaintext, encrypted with a reversible algorithm, or stored as a hash produced by a fast general-purpose function.

**Target:** Every stored password uses a hash produced by a memory-hard algorithm. No plaintext, symmetric-encrypted, or fast-hash password is present in any data store. Binary target.

**Verification:** Inspection. The stored data is inspected against the policy in [SRIS-P1-SEC-009](../wave-3-detailed-design/SRIS-P1-SEC-009_PasswordAndCredentialPolicy.md) — Password and Credential Policy.

**Quality Characteristic:** Security
**Sub-characteristic:** Confidentiality
**Applies To:** S1 IAM Service

---

**NFR-042: Password Never Logged**

A password, a password hash, and a password reset token must never appear in a log entry, a trace attribute, a metric label, or an error response, on any service.

**Target:** Zero password values or password hashes in any log across the full Phase 1 run. Binary target.

**Verification:** Test. Executed by [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md) — Security Testing Plan.

**Quality Characteristic:** Security
**Sub-characteristic:** Confidentiality
**Applies To:** S1, S3, S6

---

**NFR-043: Password Reset Token Single Use**

Every password reset token must be invalidated after first successful use. A second use of the same token must fail.

**Target:** Zero successful reuse of a reset token across every scenario in the security test plan. Binary target.

**Verification:** Test. Executed by [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md) — Security Testing Plan.

**Quality Characteristic:** Security
**Sub-characteristic:** Authenticity
**Applies To:** S1 IAM Service

---

### 8.2 Token Handling

---

**NFR-044: Access Token Time Bound**

Every access token issued by the system must carry a bounded expiry, and the system must reject an access token after its expiry.

**Target:** Every access token is rejected after its configured expiry with 100% reliability across the security tests. The exact expiry value belongs to [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md) — JWT Token Design and Claims. Binary target.

**Verification:** Test. Executed by [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md) — Security Testing Plan.

**Quality Characteristic:** Security
**Sub-characteristic:** Authenticity
**Applies To:** S1 IAM Service, S2, S3, S4

---

**NFR-045: Refresh Token Rotation**

Every use of a refresh token must invalidate that refresh token and issue a new one, so that a stolen refresh token cannot be reused after the legitimate owner has refreshed.

**Target:** Every refresh token is single-use. A second use of the same refresh token invalidates the session. Binary target.

**Verification:** Test. Executed by [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md) — Security Testing Plan.

**Quality Characteristic:** Security
**Sub-characteristic:** Authenticity
**Applies To:** S1 IAM Service

---

**NFR-046: Token Signature Verification**

Every service that accepts a JWT must verify the token's signature before trusting any claim in it. A service must reject a token whose signature does not verify.

**Target:** Every service rejects every unsigned, wrong-key-signed, or algorithm-substituted token. Binary target.

**Verification:** Test. Executed by [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md) — Security Testing Plan.

**Quality Characteristic:** Security
**Sub-characteristic:** Integrity
**Applies To:** S1, S2, S3, S4, S6

---

**NFR-047: Session Invalidation on Password Change**

When a user changes their password or completes a password reset, every active session for that user must be invalidated. No previously issued token for the account may remain valid.

**Target:** Zero previously issued tokens work after a password change, verified across every account in the security test plan. Binary target.

**Verification:** Test. Executed by [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md) — Security Testing Plan.

**Quality Characteristic:** Security
**Sub-characteristic:** Accountability
**Applies To:** S1 IAM Service

---

### 8.3 DPDP Compliance

---

**NFR-048: Purpose-Limited Data Collection**

Every personal data field collected by the system must map to a stated purpose recorded in [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md) — DPDP Act Compliance Framework (Phase 1 scoped). No field may be collected without a stated purpose.

**Target:** Every collected field appears in the purpose register. Zero unregistered fields across the security inspection. Binary target.

**Verification:** Inspection. The registration forms and the data model are inspected against the purpose register.

**Quality Characteristic:** Security
**Sub-characteristic:** Confidentiality
**Applies To:** S1 IAM Service, S3 Reservation Service

---

**NFR-049: Consent Recorded Before Personal Data Processing**

The system must record a customer's consent to the processing of their personal data before that data is stored or processed, in the form defined in [SRIS-P1-SEC-007](../wave-3-detailed-design/SRIS-P1-SEC-007_ConsentManagementDataModelPhase1Scoped.md) — Consent Management Data Model (Phase 1 scoped).

**Target:** Zero personal-data records exist without a corresponding consent record. Binary target.

**Verification:** Test. Executed by [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md) — Security Testing Plan.

**Quality Characteristic:** Security
**Sub-characteristic:** Accountability
**Applies To:** S1 IAM Service

---

**NFR-050: Data Retention Boundary**

The system must not retain personal data beyond the retention period defined in [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md) — DPDP Act Compliance Framework (Phase 1 scoped). Data that reaches the end of its retention period must be removed or anonymised.

**Target:** Every personal-data record past its retention period is removed or anonymised in the retention sweep. Binary target.

**Verification:** Inspection. The retention sweep logic and its execution log are inspected.

**Quality Characteristic:** Security
**Sub-characteristic:** Confidentiality
**Applies To:** S1 IAM Service, S3 Reservation Service

---

**NFR-051: Right-to-Erasure Handling**

When a customer requests deletion of their account, the system must remove or anonymise the customer's personal data in accordance with [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md) — DPDP Act Compliance Framework (Phase 1 scoped). The requirement is not to delete transactional records that the business must keep for accounting, but to remove the customer's identifying information from them.

**Target:** After an approved deletion request, no personal identifier remains accessible in the customer's records, except where a legal retention obligation applies and is recorded. Binary target.

**Verification:** Test. Executed by [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md) — Security Testing Plan.

**Quality Characteristic:** Security
**Sub-characteristic:** Confidentiality
**Applies To:** S1 IAM Service, S3 Reservation Service

---

### 8.4 Field Masking

---

**NFR-052: Sensitive Field Masking in Logs and Traces**

Every service must mask sensitive fields in log output and trace attributes. The classification of a field as sensitive is recorded in [SRIS-P1-SEC-012](../wave-3-detailed-design/SRIS-P1-SEC-012_DataClassificationRegister.md) — Data Classification Register. At minimum, passwords, tokens, payment instrument details, and full personal contact details must be masked.

**Target:** Zero unmasked sensitive values across the full Phase 1 run. Binary target.

**Verification:** Test. Executed by [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md) — Security Testing Plan.

**Quality Characteristic:** Security
**Sub-characteristic:** Confidentiality
**Applies To:** S1, S2, S3, S4, S5, S6

---

**NFR-053: Sensitive Field Masking in API Responses**

An API response must not include a field that the caller is not authorised to see, even if the field exists on the underlying entity. Masking is enforced at the API boundary, not only in the client.

**Target:** Zero unauthorised field disclosures across every API test in the security test plan. Binary target.

**Verification:** Test. Executed by [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md) — Security Testing Plan.

**Quality Characteristic:** Security
**Sub-characteristic:** Confidentiality
**Applies To:** S1, S2, S3, S4

---

**NFR-054: Masked Payment Details**

The system must store only a truncated or tokenised reference to a payment instrument. A full card number, expiry, or CVV must never be stored in any data store.

**Target:** Zero full card data in any data store. Binary target.

**Verification:** Inspection. The data model is inspected against the payment gateway integration design in [SRIS-P1-API-011](../wave-3-detailed-design/SRIS-P1-API-011_PaymentGatewayIntegrationDesignMock.md) — Payment Gateway Integration Design (Mock).

**Quality Characteristic:** Security
**Sub-characteristic:** Confidentiality
**Applies To:** S3 Reservation Service, S5 Mock Payment Gateway

---

### 8.5 Rate Limiting

---

**NFR-055: Rate Limit on Public Endpoints**

Every endpoint that accepts unauthenticated traffic must enforce a rate limit per source. The specific rate limit values belong to [SRIS-P1-API-008](../wave-3-detailed-design/SRIS-P1-API-008_APIRateLimitingAndThrottlingRules.md) — API Rate Limiting and Throttling Rules.

**Target:** Every public endpoint enforces a rate limit. A client that exceeds the limit receives a rate-limit response. Binary target.

**Verification:** Test. Executed by [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md) — Security Testing Plan.

**Quality Characteristic:** Security
**Sub-characteristic:** Resistance
**Applies To:** S1 IAM Service, S3 Reservation Service, S4 Search Aggregator BFF

---

**NFR-056: Rate Limit Does Not Block Normal Traffic**

The rate limit must be set so that legitimate customer traffic during the demo load is not throttled.

**Target:** Zero legitimate requests receive a rate-limit response during the demo load test. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-009](../wave-4-testing/SRIS-P1-TEST-009_LoadTestPlan.md) — Load Test Plan.

**Quality Characteristic:** Security
**Sub-characteristic:** Resistance
**Applies To:** S1 IAM Service, S3 Reservation Service, S4 Search Aggregator BFF

---

**NFR-057: Rate Limit Response Disclosure**

A rate-limit response must not disclose the internal rate-limit configuration beyond the retry-after interval. The response must not reveal the identity of the rate-limit implementation or its storage.

**Target:** Zero internal configuration disclosures in any rate-limit response. Binary target.

**Verification:** Test. Executed by [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md) — Security Testing Plan.

**Quality Characteristic:** Security
**Sub-characteristic:** Confidentiality
**Applies To:** S1 IAM Service, S3 Reservation Service, S4 Search Aggregator BFF

---

## 9. Maintainability

The Maintainability characteristic covers the degree of effectiveness and efficiency with which the system can be modified by the intended maintainers. In SRIS the maintainers are the Lead Architect and the project team, and the standard is set by [SRIS-P1-DEV-004](../wave-6-developer-standards/SRIS-P1-DEV-004_CodingStandardsAndConventions.md) — Coding Standards and Conventions. The maintainability requirements below state the observable structural properties that the code must satisfy. The concurrency and tracing designs belong to [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md) — Observability and Monitoring Design (OTel/W3C) and [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md) — Distributed Concurrency and Locking Strategy.

### 9.1 Modularity

---

**NFR-058: Service Module Boundaries**

Every internal module of a microservice — in particular the Inventory module and the Booking module of S3 — must respect the module boundary rules in [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification section 7.4. No module may read another module's tables, and modules may interact only through a public interface or in-process domain events.

**Target:** Zero cross-module table accesses. Zero cross-module direct state reads. Binary target.

**Verification:** Inspection. The code structure is inspected against the module boundary rules.

**Quality Characteristic:** Maintainability
**Sub-characteristic:** Modularity
**Applies To:** S2 Master Data and Pricing Service, S3 Reservation Service

---

**NFR-059: Service Data Ownership**

No service may read another service's data store directly. All cross-service data access must be through an API or an event, as required by Business Rule BRL-9 in [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD).

**Target:** Zero direct cross-service data-store accesses. Binary target.

**Verification:** Inspection. The database access patterns are inspected against BRL-9.

**Quality Characteristic:** Maintainability
**Sub-characteristic:** Modularity
**Applies To:** S1, S2, S3, S4, S5, S6

---

**NFR-060: Contract-First Interfaces**

Every service must define its interfaces as OpenAPI or AsyncAPI contracts before implementation begins, in line with the contract-first approach adopted in the register.

**Target:** Every service API is defined in a contract before the corresponding code is written. The contracts are stored in [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md) — API Contract Document (OpenAPI) and [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md) — Event Schema Document (AsyncAPI). Binary target.

**Verification:** Inspection. The commit history is inspected to confirm that the contract was committed before the implementation.

**Quality Characteristic:** Maintainability
**Sub-characteristic:** Modifiability
**Applies To:** S1, S2, S3, S4, S5, S6

---

### 9.2 Testability

---

**NFR-061: Unit Test Coverage**

Every service must maintain unit test coverage over its business logic. The coverage requirement is defined in [SRIS-P1-DEV-006](../wave-6-developer-standards/SRIS-P1-DEV-006_DefinitionOfDoneDoD.md) — Definition of Done (DoD).

**Target:** The coverage threshold stated in the Definition of Done is met by every service at the point of merge. Binary target.

**Verification:** Inspection. The CI/CD pipeline reports coverage on every pull request.

**Quality Characteristic:** Maintainability
**Sub-characteristic:** Testability
**Applies To:** S1, S2, S3, S4, S5, S6

---

**NFR-062: Business Logic Testable Without External Dependencies**

Every piece of business logic must be testable without a running external dependency. External dependencies must be mockable at the interface boundary.

**Target:** Every unit test suite runs to completion without a running database, message bus, or downstream service. Binary target.

**Verification:** Inspection. The unit test suites are run in an isolated environment without external services.

**Quality Characteristic:** Maintainability
**Sub-characteristic:** Testability
**Applies To:** S1, S2, S3, S4, S5, S6

---

**NFR-063: Deterministic Tests**

Every automated test must be deterministic. A test that fails intermittently must be treated as a defect in the test, not re-run until it passes.

**Target:** Zero flaky tests in the CI pipeline across the full Phase 1 run. Binary target.

**Verification:** Inspection. The CI pipeline history is inspected for retried or flaky tests.

**Quality Characteristic:** Maintainability
**Sub-characteristic:** Testability
**Applies To:** S1, S2, S3, S4, S5, S6

---

### 9.3 Code Documentation

---

**NFR-064: Public Interface Documentation**

Every public interface — every service endpoint, every event schema, every published function — must carry documentation that states its purpose, its inputs, its outputs, and its failure responses.

**Target:** Every public interface is documented. The comment standard is defined in [SRIS-P1-DEV-014](../wave-6-developer-standards/SRIS-P1-DEV-014_CommentAndInlineDocumentationStandard.md) — Comment and Inline Documentation Standard. Binary target.

**Verification:** Inspection. The code is inspected against the comment standard.

**Quality Characteristic:** Maintainability
**Sub-characteristic:** Analysability
**Applies To:** S1, S2, S3, S4, S5, S6

---

**NFR-065: Business Rule Citations in Code**

Every piece of code that implements a domain rule must cite the rule it implements, by identifier, in a comment. The rule identifiers are defined in [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) to [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md).

**Target:** Every business-rule implementation carries a citation to the rule it implements. Binary target.

**Verification:** Inspection. The code is inspected against the rule register.

**Quality Characteristic:** Maintainability
**Sub-characteristic:** Analysability
**Applies To:** S2, S3

---

**NFR-066: No Dead Code in Release**

The release branch must contain no commented-out code, no unreferenced public functions, and no unreachable branches.

**Target:** Zero dead code at the freeze of the release branch. Binary target.

**Verification:** Inspection. The release branch is inspected with a static analysis tool before the freeze.

**Quality Characteristic:** Maintainability
**Sub-characteristic:** Modifiability
**Applies To:** S1, S2, S3, S4, S5, S6

---

## 10. Flexibility

The Flexibility characteristic covers the degree to which the system can be adapted to changes in its environment, its load, or its intended use without modifying the system itself. In the 2023 version of ISO/IEC 25010 the former Portability characteristic was renamed to Flexibility and expanded to include scalability, adaptability, and replaceability alongside installability. In SRIS the Flexibility requirements cover two things: the ability to run the same software in a different environment without code change, and the ability to replace one component without replacing the others.

The strongest non-functional requirement of Phase 1 is stated in this section. It is binary and does not depend on any measurement. It is the requirement that makes the local demo and the future cloud deployment the same artefact.

### 10.1 Environment Parity

---

**NFR-067: Identical Image Across Environments**

The container image that runs in the local environment must be the same image that runs in any other environment. No environment-specific rebuild is permitted.

**Target:** The image built by the CI pipeline is the image deployed to every environment, byte-identical. Binary target.

**Verification:** Inspection. The image digest in the local environment is compared with the image digest in the target environment.

**Quality Characteristic:** Flexibility
**Sub-characteristic:** Installability
**Applies To:** S1, S2, S3, S4, S5, S6

---

**NFR-068: Configuration Externalised**

Every service must read its entire configuration — database URLs, broker URLs, port bindings, feature flags, third-party endpoints, secrets — from environment variables or from a mounted configuration file. No configuration value may be baked into the image.

**Target:** Zero configuration values are compiled into any image. The environment contract is defined in [SRIS-P1-INF-011](../wave-5-devops-operations/SRIS-P1-INF-011_EnvironmentVariablesAndConfigurationReference.md) — Environment Variables and Configuration Reference. Binary target.

**Verification:** Inspection. The image contents are inspected for any hardcoded configuration.

**Quality Characteristic:** Flexibility
**Sub-characteristic:** Adaptability
**Applies To:** S1, S2, S3, S4, S5, S6

---

**NFR-069: No Local Filesystem State**

No service may persist data to the container's own filesystem. All persistent state must live in a database, in a named volume, or in an external object store. Temporary scratch space is permitted only when the service can recover cleanly from its loss.

**Target:** Zero persistent state written to the container filesystem. Binary target.

**Verification:** Inspection. Every service is restarted with a wiped filesystem, and all committed state survives.

**Quality Characteristic:** Flexibility
**Sub-characteristic:** Adaptability
**Applies To:** S1, S2, S3, S4, S5, S6

---

**NFR-070: No Hardcoded Hostnames or Ports**

No service may contain a hardcoded hostname, IP address, or port. Every network address must come from configuration.

**Target:** Zero hardcoded hostnames, IP addresses, or ports in the source code. Binary target.

**Verification:** Inspection. The source code is scanned for address literals.

**Quality Characteristic:** Flexibility
**Sub-characteristic:** Adaptability
**Applies To:** S1, S2, S3, S4, S5, S6

---

### 10.2 Cloud Swap by Orchestration Configuration

---

**NFR-071: Cloud Deployment by Configuration Change Alone**

The full SRIS stack must be deployable to a single cloud host by changing only the orchestration configuration file. No application code, no container image, and no API contract may change when moving from the local environment to the cloud host.

**Target:** A complete deployment to the target cloud host is achieved by editing only the orchestration configuration file. Zero code, image, or contract changes are required. The target cloud host is the Oracle Cloud Always Free tier, with four ARM cores and 24 GB RAM. This target is binary and does not require measurement.

**Verification:** Demonstration. Executed as a manual deployment during Week 8 of Phase 1. The step-by-step procedure is recorded in [SRIS-P1-OPS-001](../wave-5-devops-operations/SRIS-P1-OPS-001_DeploymentGuide.md) — Deployment Guide.

**Quality Characteristic:** Flexibility
**Sub-characteristic:** Replaceability
**Applies To:** System-wide

---

**NFR-072: Orchestration Configuration Portability**

The orchestration configuration must use only portable primitives — service definitions, environment variables, network definitions, volume mounts — and no host-specific directive.

**Target:** The orchestration configuration contains no host-specific directive. Binary target.

**Verification:** Inspection. The orchestration configuration is inspected against the portability checklist.

**Quality Characteristic:** Flexibility
**Sub-characteristic:** Installability
**Applies To:** System-wide

---

**NFR-073: Startup Order Declared in Orchestration**

The orchestration configuration must declare the startup order of the six services and their dependencies, so that the stack starts correctly on any host without manual sequencing.

**Target:** The full stack starts to a healthy state on a fresh host without manual intervention, in every environment. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-010](../wave-4-testing/SRIS-P1-TEST-010_IntegrationTestPlan.md) — Integration Test Plan, on a fresh environment.

**Quality Characteristic:** Flexibility
**Sub-characteristic:** Installability
**Applies To:** System-wide

---

**NFR-074: Health Check Declared Per Service**

Every service must declare a health check in the orchestration configuration so that the orchestrator can determine whether the service is ready to receive traffic.

**Target:** Every service has a declared health check. The orchestrator waits for the health check to succeed before routing traffic. Binary target.

**Verification:** Inspection. The orchestration configuration is inspected for a health check on every service.

**Quality Characteristic:** Flexibility
**Sub-characteristic:** Installability
**Applies To:** S1, S2, S3, S4, S5, S6

---

**NFR-075: Cloud Deployment Documentation**

The Deployment Guide must contain a complete, step-by-step procedure for deploying the stack to the target cloud host by changing only the orchestration configuration file. The procedure must be executable by a reader who has not deployed the stack before.

**Target:** A reader who has not deployed SRIS before can deploy it to the cloud host by following the Deployment Guide alone. Binary target.

**Verification:** Demonstration. Executed during Week 8, with a second engineer following the guide.

**Quality Characteristic:** Flexibility
**Sub-characteristic:** Replaceability
**Applies To:** System-wide

---

## 11. Safety

The Safety characteristic was added as a first-class characteristic in the 2023 version of ISO/IEC 25010. It covers the degree to which the system, under defined conditions, does not cause harm to persons, business, property, or the environment. For SRIS the physical operation of trains is outside the system's scope, and railway safety is not a property of this software. Safety for SRIS means the narrower property that the software must not cause **financial harm to a customer** and must not **expose personal data in a way that causes harm**. These are the safety properties the system must guarantee.

---

**NFR-076: No Silent Financial Loss**

Every payment that succeeds must result either in a confirmed booking or in a refund being initiated. A payment must never succeed without a corresponding booking record or refund record.

**Target:** Zero payments without a corresponding booking or refund record. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-010](../wave-4-testing/SRIS-P1-TEST-010_IntegrationTestPlan.md) — Integration Test Plan, across fault-injection scenarios.

**Quality Characteristic:** Safety
**Sub-characteristic:** Risk Identification
**Applies To:** S3 Reservation Service, S5 Mock Payment Gateway

---

**NFR-077: No Silent Double Charge**

A customer must never be charged twice for the same booking attempt, even if the client retries the payment request or the network delivers the same payment callback twice.

**Target:** Zero double charges across every retry and duplicate-callback scenario in the test suite. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-004](../wave-4-testing/SRIS-P1-TEST-004_ConsumerDrivenContractTestingStrategy.md) — Consumer-Driven Contract Testing Strategy, using duplicated callbacks.

**Quality Characteristic:** Safety
**Sub-characteristic:** Risk Identification
**Applies To:** S3 Reservation Service, S5 Mock Payment Gateway

---

**NFR-078: Fail-Safe on Payment Uncertainty**

If the payment gateway returns an ambiguous outcome — neither success nor failure — the system must treat the payment as **not completed** until the outcome is clarified. The seat must not be allocated and the customer must not be charged on an ambiguous payment.

**Target:** Zero seat allocations on an ambiguous payment outcome. Binary target.

**Verification:** Test. Executed by [SRIS-P1-TEST-010](../wave-4-testing/SRIS-P1-TEST-010_IntegrationTestPlan.md) — Integration Test Plan, using an ambiguous-outcome simulator.

**Quality Characteristic:** Safety
**Sub-characteristic:** Fail-Safe
**Applies To:** S3 Reservation Service

---

**NFR-079: Hazard Warning on Irreversible Action**

Every irreversible action presented to the user — cancellation of a confirmed booking, deletion of an account, change of a confirmed email — must display a clear warning before the action is applied, and must require explicit confirmation.

**Target:** Every irreversible action presents a confirmation step. Zero irreversible actions applied without confirmation. Binary target.

**Verification:** Inspection. The wireframes and the interaction specification in [SRIS-P1-UI-003](../wave-3-detailed-design/SRIS-P1-UI-003_WireframesCustomerFlow.md) — Wireframes (Customer Flow) and [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md) — Wireframes (Employee/Admin Flow) are inspected against this requirement.

**Quality Characteristic:** Safety
**Sub-characteristic:** Hazard Warning
**Applies To:** Customer Booking Website, Employee Admin Console

---

**NFR-080: Safe Integration of the Mock Payment Gateway**

The Mock Payment Gateway is a simulator and must never be connected to a real payment provider without an explicit code change and a formal register revision. The system must not contain a configuration option that silently turns the simulator into a real provider.

**Target:** Zero configuration paths that connect the system to a real payment provider. Binary target.

**Verification:** Inspection. The configuration schema is inspected against this requirement.

**Quality Characteristic:** Safety
**Sub-characteristic:** Safe Integration
**Applies To:** S3 Reservation Service, S5 Mock Payment Gateway

---

## 12. Cross-Characteristic Trade-offs

Where two quality characteristics pull against each other, this section records the priority the Phase 1 register adopts. Trade-offs are recorded so that a future design decision that favours one characteristic over another does not become a silent change.

| Trade-off                                                | Resolution in Phase 1                                                                                          |
| -------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| **Performance versus Reliability.** Making the system faster often means fewer synchronous confirmations. | Reliability wins. A booking confirmation that takes 3 seconds but never loses state is preferred over a 1-second confirmation that can fail silently under load.   |
| **Performance versus Security.** Strong signature verification and rate limiting add latency.            | Security wins. The latency budgets in §4 already include the security cost of signature verification and rate-limit evaluation.                                    |
| **Performance versus Maintainability.** Denormalised data and cached aggregates speed reads but make the model harder to change. | Maintainability wins where the two conflict, except where the memory ceiling forces a cache. Any cache must be documented in [SRIS-P1-ARCH-003](../wave-2-architecture/SRIS-P1-ARCH-003_SystemArchitectureDocument.md) — System Architecture Document. |
| **Reliability versus Flexibility.** A stack that is easy to redeploy may hold less state and be more sensitive to restart. | Flexibility wins for the specific property of cloud deployment, because the portability requirement is a Phase 1 commitment. Reliability is preserved by ensuring state lives in a database, not in memory. |
| **Security versus Interaction Capability.** Strict session expiry and forced re-authentication reduce convenience. | Security wins, with the mitigation that the interaction design must make the re-authentication step clear and non-frustrating.                                    |
| **Flexibility versus Performance.** A portable stack that runs on a smaller cloud host may not meet the local performance budgets. | The performance budgets are set for the local environment and are expected to be met or exceeded on the cloud host, which has more resources. The trade-off is one-directional. |

Two rules govern any future trade-off decision:

1. **A trade-off is resolved in favour of the characteristic that supports the Phase 1 success criterion**, defined in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document §6.
2. **A resolution that changes a numeric target requires a revision to this document**, with a new row in the Revision History recording which target changed and why.

---

## 13. Traceability

This section records the local traceability of every non-functional requirement in this document. It maps each NFR to the ISO/IEC 25010:2023 characteristic and sub-characteristic it satisfies, and to the service or surface it applies to. The full cross-wave matrix, which spans every document in the register, belongs to [SRIS-P1-REQ-012](./SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md) — Requirement Traceability Matrix (RTM), and is not repeated here.

### 13.1 NFR Ranges by Characteristic

| Section | Characteristic         | NFR Range         | Count |
| ------- | ---------------------- | ----------------- | ----- |
| 3       | Functional Suitability | NFR-001 to NFR-004 | 4     |
| 4       | Performance Efficiency | NFR-005 to NFR-017 | 13    |
| 5       | Compatibility          | NFR-018 to NFR-022 | 5     |
| 6       | Interaction Capability | NFR-023 to NFR-031 | 9     |
| 7       | Reliability            | NFR-032 to NFR-040 | 9     |
| 8       | Security               | NFR-041 to NFR-057 | 17    |
| 9       | Maintainability        | NFR-058 to NFR-066 | 9     |
| 10      | Flexibility            | NFR-067 to NFR-075 | 9     |
| 11      | Safety                 | NFR-076 to NFR-080 | 5     |
| **Total** |                      |                   | **80** |

### 13.2 Characteristic Coverage

Every one of the nine ISO/IEC 25010:2023 characteristics is represented by at least one non-functional requirement in this document.

| # | Characteristic         | Covered by         |
| - | ---------------------- | ------------------ |
| 1 | Functional Suitability | NFR-001 to NFR-004 |
| 2 | Performance Efficiency | NFR-005 to NFR-017 |
| 3 | Compatibility          | NFR-018 to NFR-022 |
| 4 | Interaction Capability | NFR-023 to NFR-031 |
| 5 | Reliability            | NFR-032 to NFR-040 |
| 6 | Security               | NFR-041 to NFR-057 |
| 7 | Maintainability        | NFR-058 to NFR-066 |
| 8 | Flexibility            | NFR-067 to NFR-075 |
| 9 | Safety                 | NFR-076 to NFR-080 |

### 13.3 Verification Owner Map

The verification of an NFR is owned by one of a small set of documents. The map below shows the count of NFRs each verification owner is responsible for. Every count is verified by scanning the Verification field of every NFR in Sections 3 to 11.

| Verification Owner                                                                        | Wave | NFR Count |
| ----------------------------------------------------------------------------------------- | ---- | --------- |
| [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md) — Test Cases (Functional) | 4    | 2         |
| [SRIS-P1-TEST-004](../wave-4-testing/SRIS-P1-TEST-004_ConsumerDrivenContractTestingStrategy.md) — Consumer-Driven Contract Testing Strategy | 4 | 2 |
| [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md) — Test Cases (UI)   | 4    | 7         |
| [SRIS-P1-TEST-008](../wave-4-testing/SRIS-P1-TEST-008_PerformanceTestPlan.md) — Performance Test Plan | 4 | 5 |
| [SRIS-P1-TEST-009](../wave-4-testing/SRIS-P1-TEST-009_LoadTestPlan.md) — Load Test Plan   | 4    | 5         |
| [SRIS-P1-TEST-010](../wave-4-testing/SRIS-P1-TEST-010_IntegrationTestPlan.md) — Integration Test Plan | 4 | 11 |
| [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md) — Security Testing Plan | 4 | 13 |
| [SRIS-P1-NFR-HOLD-001](../wave-9-supporting-artifacts/SRIS-P1-NFR-HOLD-001_LoadModelAndResourceFitCheckHolding.md) — Load Model and Resource Fit Check (Holding) | 9 | 3 |
| Inspection (code or configuration review)                                                | —    | 26        |
| Demonstration (demo run)                                                                   | —    | 6         |
| **Total**                                                                                  |      | **80**    |

### 13.4 Provisional Target Register

Every numeric target marked "proposed, pending confirmation" in this document is recorded here so that the v1.1 revision can find and update them all.

| NFR     | Provisional Target                                                                                     |
| ------- | -------------------------------------------------------------------------------------------------------- |
| NFR-005 | p95 search latency 2,000 ms; p99 4,000 ms                                                               |
| NFR-006 | p95 booking confirmation latency 3,000 ms; p99 6,000 ms                                                 |
| NFR-007 | p95 authentication latency 500 ms; p99 1,000 ms                                                         |
| NFR-008 | p95 master-data write latency 800 ms; p99 1,500 ms                                                      |
| NFR-009 | p95 notification dispatch latency 30,000 ms; p99 60,000 ms                                              |
| NFR-010 | 50 concurrent booking confirmations within 5 minutes                                                    |
| NFR-011 | 200 concurrent search requests within 5 minutes                                                         |
| NFR-012 | 100 concurrent authentication requests within 5 minutes                                                 |
| NFR-014 | 800 MB per-service ceiling                                                                               |
| NFR-015 | Memory growth below 10% after 30 minutes sustained load                                                  |
| NFR-016 | Average CPU below 75% during sustained load                                                              |
| NFR-029 | First-time booking completes in under 8 minutes, unaided                                                |
| NFR-030 | First-time master-data tasks complete in under 15 minutes, unaided                                      |

The register of provisional targets is the input to the v1.1 revision. When measurement data exists, each row in this table is either confirmed, updated, or replaced by the measured value, and the Revision History records the change.

---

## 14. Approval

| Role           | Name        | Decision | Date       |
| -------------- | ----------- | -------- | ---------- |
| Lead Architect | Koushal Jha | Approved | 2026-10-15 |

---

## Revision History

| Version | Date       | Author      | Change           |
| ------- | ---------- | ----------- | ---------------- |
| 1.0     | 2026-10-15 | Koushal Jha | Initial release. |

---

## Appendix A: ISO/IEC 25010:2023 Mapping Matrix

This appendix records the mapping between the nine ISO/IEC 25010:2023 characteristics and the SRIS documents that own or cite each characteristic. It is the reference a reader uses to find where any given quality property is stated.

| # | Characteristic         | SRIS NFR Section | Owning Document for the Numeric Data                                                                                     |
| - | ---------------------- | ---------------- | ------------------------------------------------------------------------------------------------------------------------ |
| 1 | Functional Suitability | §3 NFR-001 to NFR-004 | This document. The functional correctness details belong to [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software Requirements Specification (SRS). |
| 2 | Performance Efficiency | §4 NFR-005 to NFR-017 | Numeric targets in this document. Load and resource fit numbers belong to [SRIS-P1-NFR-HOLD-001](../wave-9-supporting-artifacts/SRIS-P1-NFR-HOLD-001_LoadModelAndResourceFitCheckHolding.md) — Load Model and Resource Fit Check (Holding). |
| 3 | Compatibility          | §5 NFR-018 to NFR-022 | This document. Browser support details belong to [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md) — UI/UX Requirements Document. |
| 4 | Interaction Capability | §6 NFR-023 to NFR-031 | This document. Accessibility and error-display details belong to [SRIS-P1-UI-008](../wave-3-detailed-design/SRIS-P1-UI-008_UIErrorAndNotificationDisplayRules.md) — UI Error and Notification Display Rules and [SRIS-P1-UI-009](../wave-3-detailed-design/SRIS-P1-UI-009_UIAccessibilityGuidelines.md) — UI Accessibility Guidelines. |
| 5 | Reliability            | §7 NFR-032 to NFR-040 | This document. The rolling percentage targets belong to [SRIS-P1-OPS-005](../wave-5-devops-operations/SRIS-P1-OPS-005_SLODocument.md) — SLO Document. |
| 6 | Security               | §8 NFR-041 to NFR-057 | This document. The design of authentication, RBAC, and tokens belongs to [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md) to [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md). DPDP compliance details belong to [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md). |
| 7 | Maintainability        | §9 NFR-058 to NFR-066 | This document. Code-level conventions belong to [SRIS-P1-DEV-004](../wave-6-developer-standards/SRIS-P1-DEV-004_CodingStandardsAndConventions.md) — Coding Standards and Conventions and [SRIS-P1-DEV-014](../wave-6-developer-standards/SRIS-P1-DEV-014_CommentAndInlineDocumentationStandard.md) — Comment and Inline Documentation Standard. |
| 8 | Flexibility            | §10 NFR-067 to NFR-075 | This document. The deployment topology belongs to [SRIS-P1-ARCH-013](../wave-2-architecture/SRIS-P1-ARCH-013_DeploymentArchitectureDocument.md) — Deployment Architecture Document. The environment contract belongs to [SRIS-P1-INF-011](../wave-5-devops-operations/SRIS-P1-INF-011_EnvironmentVariablesAndConfigurationReference.md) — Environment Variables and Configuration Reference. |
| 9 | Safety                 | §11 NFR-076 to NFR-080 | This document. The payment handling and refund rules belong to [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing. |

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
| 1.6  | [SRIS-P1-REQ-006](./SRIS-P1-REQ-006_UserStoriesAndUseCases.md)                                              | User Stories and Use Cases                        | 1    | P0  | UNBLOCK |
| 1.7  | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)                                          | Domain Rules: Fare Calculation                    | 1    | P1  | FOLLOW  |
| 1.8  | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)                                                | Domain Rules: Ticketing                           | 1    | P1  | FOLLOW  |
| 1.9  | [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)                                  | Domain Rules: Waitlist and Cancellation           | 1    | P1  | FOLLOW  |
| 1.10 | [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md)                                         | Domain Rules: Chart Preparation                   | 1    | P1  | FOLLOW  |
| 1.11 | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)                                   | Domain Rules: Seat Matrix and Inventory           | 1    | P1  | FOLLOW  |
| 1.12 | [SRIS-P1-REQ-012](./SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md)                                    | Requirement Traceability Matrix (RTM)             | 1    | P2  | FOLLOW  |
| 2.1  | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)                  | Microservices Identification                      | 2    | P0  | UNBLOCK |
| 2.3  | [SRIS-P1-ARCH-003](../wave-2-architecture/SRIS-P1-ARCH-003_SystemArchitectureDocument.md)                   | System Architecture Document                      | 2    | P0  | UNBLOCK |
| 2.12 | [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)      | Observability and Monitoring Design (OTel/W3C)    | 2    | P0  | UNBLOCK |
| 2.13 | [SRIS-P1-ARCH-013](../wave-2-architecture/SRIS-P1-ARCH-013_DeploymentArchitectureDocument.md)               | Deployment Architecture Document                  | 2    | P1  | FOLLOW  |
| 2.14 | [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md)     | Distributed Concurrency and Locking Strategy      | 2    | P0  | UNBLOCK |
| 3.14 | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)                  | API Contract Document (OpenAPI)                   | 3    | P0  | UNBLOCK |
| 3.16 | [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md)                 | Event Schema Document (AsyncAPI)                  | 3    | P0  | UNBLOCK |
| 3.18 | [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md)      | Idempotency and Retry Policy Specification        | 3    | P0  | UNBLOCK |
| 3.19 | [SRIS-P1-API-006](../wave-3-detailed-design/SRIS-P1-API-006_APIErrorCodeCatalog.md)                         | API Error Code Catalog                            | 3    | P1  | FOLLOW  |
| 3.21 | [SRIS-P1-API-008](../wave-3-detailed-design/SRIS-P1-API-008_APIRateLimitingAndThrottlingRules.md)           | API Rate Limiting and Throttling Rules            | 3    | P2  | FOLLOW  |
| 3.24 | [SRIS-P1-API-011](../wave-3-detailed-design/SRIS-P1-API-011_PaymentGatewayIntegrationDesignMock.md)         | Payment Gateway Integration Design (Mock)         | 3    | P1  | FOLLOW  |
| 3.26 | [SRIS-P1-API-013](../wave-3-detailed-design/SRIS-P1-API-013_APIVersioningAndDeprecationPolicy.md)           | API Versioning and Deprecation Policy             | 3    | P2  | FOLLOW  |
| 3.27 | [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md)                      | UI/UX Requirements Document                       | 3    | P0  | UNBLOCK |
| 3.29 | [SRIS-P1-UI-003](../wave-3-detailed-design/SRIS-P1-UI-003_WireframesCustomerFlow.md)                        | Wireframes (Customer Flow)                        | 3    | P0  | UNBLOCK |
| 3.30 | [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md)                   | Wireframes (Employee/Admin Flow)                  | 3    | P0  | UNBLOCK |
| 3.34 | [SRIS-P1-UI-008](../wave-3-detailed-design/SRIS-P1-UI-008_UIErrorAndNotificationDisplayRules.md)            | UI Error and Notification Display Rules           | 3    | P1  | FOLLOW  |
| 3.35 | [SRIS-P1-UI-009](../wave-3-detailed-design/SRIS-P1-UI-009_UIAccessibilityGuidelines.md)                     | UI Accessibility Guidelines                       | 3    | P2  | FOLLOW  |
| 3.39 | [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)        | Authentication and Authorization Design           | 3    | P1  | FOLLOW  |
| 3.40 | [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md)                                   | RBAC Matrix                                       | 3    | P1  | FOLLOW  |
| 3.41 | [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)                      | JWT Token Design and Claims                       | 3    | P1  | FOLLOW  |
| 3.44 | [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md)      | DPDP Act Compliance Framework (Phase 1 scoped)    | 3    | P0  | UNBLOCK |
| 3.45 | [SRIS-P1-SEC-007](../wave-3-detailed-design/SRIS-P1-SEC-007_ConsentManagementDataModelPhase1Scoped.md)      | Consent Management Data Model (Phase 1 scoped)    | 3    | P0  | UNBLOCK |
| 3.47 | [SRIS-P1-SEC-009](../wave-3-detailed-design/SRIS-P1-SEC-009_PasswordAndCredentialPolicy.md)                 | Password and Credential Policy                    | 3    | P2  | FOLLOW  |
| 3.49 | [SRIS-P1-SEC-012](../wave-3-detailed-design/SRIS-P1-SEC-012_DataClassificationRegister.md)                 | Data Classification Register                      | 3    | P0  | UNBLOCK |
| 3.50 | [SRIS-P1-SEC-013](../wave-3-detailed-design/SRIS-P1-SEC-013_SecureCodingStandards.md)                      | Secure Coding Standards                           | 3    | P0  | UNBLOCK |
| 4.3  | [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)                                | Test Cases (Functional)                           | 4    | P0  | UNBLOCK |
| 4.4  | [SRIS-P1-TEST-004](../wave-4-testing/SRIS-P1-TEST-004_ConsumerDrivenContractTestingStrategy.md)             | Consumer-Driven Contract Testing Strategy         | 4    | P1  | UNBLOCK |
| 4.7  | [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md)                                       | Test Cases (UI)                                   | 4    | P1  | FOLLOW  |
| 4.8  | [SRIS-P1-TEST-008](../wave-4-testing/SRIS-P1-TEST-008_PerformanceTestPlan.md)                               | Performance Test Plan                             | 4    | P1  | FOLLOW  |
| 4.9  | [SRIS-P1-TEST-009](../wave-4-testing/SRIS-P1-TEST-009_LoadTestPlan.md)                                      | Load Test Plan                                    | 4    | P1  | FOLLOW  |
| 4.10 | [SRIS-P1-TEST-010](../wave-4-testing/SRIS-P1-TEST-010_IntegrationTestPlan.md)                               | Integration Test Plan                             | 4    | P1  | FOLLOW  |
| 4.15 | [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md)                                 | Security Testing Plan                             | 4    | P1  | FOLLOW  |
| 5.12 | [SRIS-P1-OPS-001](../wave-5-devops-operations/SRIS-P1-OPS-001_DeploymentGuide.md)                           | Deployment Guide                                  | 5    | P1  | FOLLOW  |
| 5.16 | [SRIS-P1-OPS-005](../wave-5-devops-operations/SRIS-P1-OPS-005_SLODocument.md)                               | SLO Document                                      | 5    | P2  | FOLLOW  |
| 6.2  | [SRIS-P1-DEV-004](../wave-6-developer-standards/SRIS-P1-DEV-004_CodingStandardsAndConventions.md)           | Coding Standards and Conventions                  | 6    | P0  | UNBLOCK |
| 6.4  | [SRIS-P1-DEV-006](../wave-6-developer-standards/SRIS-P1-DEV-006_DefinitionOfDoneDoD.md)                     | Definition of Done (DoD)                          | 6    | P1  | FOLLOW  |
| 6.11 | [SRIS-P1-DEV-014](../wave-6-developer-standards/SRIS-P1-DEV-014_CommentAndInlineDocumentationStandard.md)   | Comment and Inline Documentation Standard         | 6    | P0  | UNBLOCK |
| 8.7  | [SRIS-P1-USR-007](../wave-8-user-support/SRIS-P1-USR-007_DemoScenariosAndWalkthroughScript.md)              | Demo Scenarios and Walkthrough Script             | 8    | P1  | FOLLOW  |
| 9.1  | [SRIS-P1-NFR-HOLD-001](../wave-9-supporting-artifacts/SRIS-P1-NFR-HOLD-001_LoadModelAndResourceFitCheckHolding.md) | Load Model and Resource Fit Check (Holding)  | 9    | —   | HOLD    |

### B.2 Documents That Reference This Document

| Seq  | Document ID                                                                                | Document Name                                 | Why It References                                                             |
| ---- | ------------------------------------------------------------------------------------------ | --------------------------------------------- | ----------------------------------------------------------------------------- |
| 0.0  | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) | Documentation Index and Navigation Map | Lists this document in the register and in the reading paths                  |
| 0.4  | [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)      | Project Vision and Scope Document      | Lists this document as a downstream document                                  |
| 1.4  | [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md)                  | Software Requirements Specification (SRS) | Lists this document as a downstream document                              |
| 2.1  | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)             | Microservices Identification           | Lists this document as a Soft downstream document                             |

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
| 1.3 | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)                                | Capability Catalog (Final)             | Soft            |
| 1.4 | [SRIS-P1-REQ-004](./SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md)                  | Software Requirements Specification (SRS) | Hard         |
| 2.1 | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)             | Microservices Identification           | Hard            |

### B.4 Documents This Document Unblocks (Downstream)

| Seq  | Document ID                                                                      | Document Name                                | Blocked Until |
| ---- | -------------------------------------------------------------------------------- | -------------------------------------------- | ------------- |
| 1.6  | [SRIS-P1-REQ-006](./SRIS-P1-REQ-006_UserStoriesAndUseCases.md)                      | User Stories and Use Cases                   | This approved |
| 1.12 | [SRIS-P1-REQ-012](./SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md)            | Requirement Traceability Matrix (RTM)        | This approved |
| 2.12 | [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md) | Observability and Monitoring Design (OTel/W3C) | This approved |
| 4.8  | [SRIS-P1-TEST-008](../wave-4-testing/SRIS-P1-TEST-008_PerformanceTestPlan.md)         | Performance Test Plan                        | This approved |
| 4.9  | [SRIS-P1-TEST-009](../wave-4-testing/SRIS-P1-TEST-009_LoadTestPlan.md)                | Load Test Plan                               | This approved |
| 5.16 | [SRIS-P1-OPS-005](../wave-5-devops-operations/SRIS-P1-OPS-005_SLODocument.md)         | SLO Document                                 | This approved |

### B.5 Master Documentation Index

The complete list of Phase 1 documents is in [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

### B.6 External Reference Documents

| Reference Type                | Where It Is Documented                                                                                            |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| ISO/IEC 25010:2023            | Systems and software engineering — Systems and software Quality Requirements and Evaluation (SQuaRE) — Product quality model. Published 2023-11-15. The current version of the standard and the one used in this document. The 2011 version is withdrawn. |
| ISO/IEC/IEEE 29148:2018       | Systems and software engineering — Life cycle processes — Requirements engineering. Referenced for the standard requirement-format definitions and the definition of verifiability. |
| ISO/IEC 25040                 | Systems and software Quality Requirements and Evaluation (SQuaRE) — Evaluation process. Referenced for the assessment process that complements this document. |
| ISO/IEC 25023                 | Systems and software Quality Requirements and Evaluation (SQuaRE) — Measurement of system and software product quality. Referenced for the measurement methods that will be applied during the v1.1 revision. |
| Google Site Reliability Engineering | Referenced in [Section 2.3](#23-provisional-numeric-targets) for the practice of provisional targets refined by measurement. The book is by Betsy Beyer, Chris Jones, Jennifer Petoff, and Niall Richard Murphy, published by O'Reilly. |

### B.7 Document Conventions

The conventions for Priority and Tag values are defined in [Section 9](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md#9-vocabulary-standards) of [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.

---

**End of Document** 