<div align="center">

![Wave](https://img.shields.io/badge/Wave-2-0550AE?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-ARCH-6e7781?style=for-the-badge)

</div>

# Architecture Principles

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** 1.0 | **Date:** 2026-10-15 | **Document ID:** SRIS-P1-ARCH-002

| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| Title              | Architecture Principles                                           |
| Software           | SRIS                                                              |
| Software Full Form | Sarathi Railway Information System                                |
| Team Codename      | Project Sarathi                                                   |
| Document ID        | SRIS-P1-ARCH-002                                                  |
| Task               | Fix the architectural principles that every architecture decision respects |
| Document Type      | Architecture Document                                             |
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
2. [Principle Format and Governance](#2-principle-format-and-governance)
   - [2.1 What a Principle Is](#21-what-a-principle-is)
   - [2.2 What a Principle Is Not](#22-what-a-principle-is-not)
   - [2.3 Structure of a Principle](#23-structure-of-a-principle)
   - [2.4 Binding and Advisory Principles](#24-binding-and-advisory-principles)
   - [2.5 How a Principle Is Cited](#25-how-a-principle-is-cited)
3. [Architecture Principles](#3-architecture-principles)
   - [3.1 Principle 1: Bounded Context First](#31-principle-1-bounded-context-first)
   - [3.2 Principle 2: Own Your Data](#32-principle-2-own-your-data)
   - [3.3 Principle 3: Contract-First Interface](#33-principle-3-contract-first-interface)
   - [3.4 Principle 4: Asynchronous by Default](#34-principle-4-asynchronous-by-default)
   - [3.5 Principle 5: Fail Isolated](#35-principle-5-fail-isolated)
   - [3.6 Principle 6: Security Is Every Layer](#36-principle-6-security-is-every-layer)
   - [3.7 Principle 7: Observe Everything](#37-principle-7-observe-everything)
   - [3.8 Principle 8: Deploy by Configuration Alone](#38-principle-8-deploy-by-configuration-alone)
   - [3.9 Principle 9: Prefer Simplicity Under Constraint](#39-principle-9-prefer-simplicity-under-constraint)
4. [Conflict Resolution and Exceptions](#4-conflict-resolution-and-exceptions)
   - [4.1 How Conflicts Between Principles Are Resolved](#41-how-conflicts-between-principles-are-resolved)
   - [4.2 When a Principle Cannot Be Met](#42-when-a-principle-cannot-be-met)
   - [4.3 Recording an Exception](#43-recording-an-exception)
5. [Traceability](#5-traceability)
6. [Approval](#6-approval)

- [Revision History](#revision-history)
- [Appendix A: Not Applicable](#appendix-a-not-applicable)
- [Appendix B: Related Documents](#appendix-b-related-documents)

---

## 1. Introduction

### 1.1 Purpose

This document fixes the architectural principles of Phase 1 of SRIS (Sarathi Railway Information System). A principle is a binding rule that constrains every architecture decision made in the register. The nine principles recorded here are the frame within which every later architecture document — system architecture, bounded context map, domain model, technology stack, service interaction, security, observability, concurrency, saga design, and service registry — is written.

A principle is not a design. It states a rule and a reason. The design that satisfies the rule is recorded in the document that owns the design. This document states the rule; it does not state the design.

### 1.2 Scope

**In scope**

- The definition of an architecture principle and its distinction from a decision, a tactic, and a pattern.
- The structure of a principle: Name, Statement, Rationale, Implications, and Related Principles.
- The nine binding principles of Phase 1.
- The rule for resolving conflicts between two principles.
- The rule for recording an exception when a principle cannot be met.
- The lifecycle of a principle: addition, revision, and retirement.

**Out of scope**

- The service catalogue and the justification for the service count, which are defined in [SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification.
- The system architecture itself, which is defined in [SRIS-P1-ARCH-003](./SRIS-P1-ARCH-003_SystemArchitectureDocument.md) — System Architecture Document.
- The bounded context map, which is defined in [SRIS-P1-ARCH-004](./SRIS-P1-ARCH-004_BoundedContextMap.md) — Bounded Context Map.
- The domain model, which is defined in [SRIS-P1-ARCH-005](./SRIS-P1-ARCH-005_DomainModelDocument.md) — Domain Model Document.
- The individual architecture decision records, which belong to [SRIS-P1-ARCH-007](./SRIS-P1-ARCH-007_ArchitectureDecisionRecordsMasterIndex.md) — Architecture Decision Records — Master Index.
- The technology stack choice, which is defined in [SRIS-P1-ARCH-008](./SRIS-P1-ARCH-008_TechnologyStackADR.md) — Technology Stack ADR.
- The service interaction and communication design, which is defined in [SRIS-P1-ARCH-009](./SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md) — Service Interaction and Communication Design.
- The security architecture, which is defined in [SRIS-P1-ARCH-010](./SRIS-P1-ARCH-010_SecurityArchitectureDocument.md) — Security Architecture Document.
- The observability design, which is defined in [SRIS-P1-ARCH-012](./SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md) — Observability and Monitoring Design (OTel/W3C).
- The deployment architecture, which is defined in [SRIS-P1-ARCH-013](./SRIS-P1-ARCH-013_DeploymentArchitectureDocument.md) — Deployment Architecture Document.
- The concurrency and locking strategy, which is defined in [SRIS-P1-ARCH-014](./SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md) — Distributed Concurrency and Locking Strategy.
- The distributed transaction design, which is defined in [SRIS-P1-ARCH-015](./SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md) — Distributed Transaction and Saga Pattern Design.
- The service registry, which is defined in [SRIS-P1-ARCH-016](./SRIS-P1-ARCH-016_ServiceRegistryAndCatalog.md) — Service Registry and Catalog.
- The infrastructure and network topology that enforces the network layer of security, which is defined in [SRIS-P1-INF-001](../wave-5-devops-operations/SRIS-P1-INF-001_InfrastructureAndTechnologyDocument.md) — Infrastructure and Technology Document.
- The functional requirements, which are defined in [SRIS-P1-REQ-004](../wave-1-requirements/SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software Requirements Specification (SRS).
- The non-functional requirements, which are defined in [SRIS-P1-REQ-005](../wave-1-requirements/SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md) — Non-Functional Requirements (ISO 25010).

### 1.3 Audience

- **Lead Architect:** maintains this document and approves every principle.
- **Backend and frontend developers:** apply the principles when making design decisions that are not covered by a downstream document.
- **UI designer:** understands the principles that constrain the interfaces.
- **Tester (QA):** uses the principles as one input when judging whether an implementation is conformant.
- **Project supervisor and evaluator:** uses this document as the frame within which every architecture decision was made.
- **Technical reviewers:** engineers or interviewers who open the repository and need to understand the architectural discipline of Phase 1.

### 1.4 Terminology and Conventions

Every term in this document has the meaning recorded in [SRIS-P1-REQ-001](../wave-1-requirements/SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary. The terms below carry the most weight in this document and are used with the meanings defined here.

| Term                  | Meaning                                                                                                                                |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Architecture principle | A binding rule that constrains every architectural decision in a system.                                                                |
| Architectural decision | A specific choice made in a specific context to satisfy a principle or resolve a problem. Recorded in an Architecture Decision Record. |
| Architectural tactic  | A specific design technique that contributes to a single quality attribute. Tactics are the mechanics that implement a principle.        |
| Architectural pattern | A reusable solution to a recurring problem, composed of multiple tactics.                                                               |
| Binding principle     | A principle that must be satisfied. Deviation requires an exception.                                                                    |
| Advisory principle    | A principle that names the target state but does not require compliance in Phase 1. Deviation does not require an exception.            |
| Exception             | A formally recorded decision to deviate from a binding principle, with the reason and the reversal plan.                                 |
| Trust boundary        | A line across which trust is not assumed. The server is the outermost trust boundary of SRIS.                                            |

The identifier prefix below is local to this document.

| Prefix | Meaning               |
| ------ | --------------------- |
| P      | Architecture principle |

This document follows the standards below.

- [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard, for structure, header, and style.
- [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md) — Document ID and Category Scheme, for the Document ID.
- [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md) — Document Cross-Reference Standard, for citations and links.
- **The Open Group Architecture Framework (TOGAF), 10th Edition** — referenced for the four-part structure of an architecture principle.
- **Bass, Clements, and Kazman, "Software Architecture in Practice", 4th Edition** — referenced for the distinction between a principle, a tactic, and a pattern.
- **Michael Nygard, "Documenting Architecture Decisions"** — referenced for the exception-recording mechanism.

---

## 2. Principle Format and Governance

### 2.1 What a Principle Is

A principle is a general rule that constrains every architecture decision in a system. It is enduring: it does not depend on the technology of the moment. It is universal within its scope: every architecture decision in Phase 1 must respect it. It is stated in plain language so that a non-specialist can understand it.

A principle is prescriptive, not descriptive. It does not describe what the system currently does. It dictates how the system must be built. Its purpose is to reduce the space of decisions available to the architect, so that every decision that survives is compatible with the rest.

In SRIS Phase 1, a principle is one of nine. It is binding unless it is explicitly marked advisory. It applies to the whole of the architecture, not to a single service.

### 2.2 What a Principle Is Not

A principle is distinct from three other things that are often confused with it.

**A principle is not an architectural decision.** A decision is a specific choice made in a specific context: "Use PostgreSQL as the data store for S2 Master Data and Pricing Service." A decision satisfies a principle, or it is an exception to one. Decisions are recorded in Architecture Decision Records in [SRIS-P1-ARCH-007](./SRIS-P1-ARCH-007_ArchitectureDecisionRecordsMasterIndex.md) — Architecture Decision Records — Master Index.

**A principle is not an architectural tactic.** A tactic is a specific technique that contributes to one quality attribute: a timeout, a circuit breaker, a retry with backoff. Tactics are the mechanics used to satisfy principles. A principle such as Fail Isolated is satisfied by the tactics of timeouts, bulkheads, and circuit breakers.

**A principle is not an architectural pattern.** A pattern is a reusable solution composed of multiple tactics: Saga, BFF, Anti-Corruption Layer, Event Sourcing. A pattern is chosen when the principles require it and the tactics support it.

The distinction matters because each of the four lives in a different document. Principles live here. Decisions live in the ADR index. Tactics live in the architecture documents that use them. Patterns live in the design documents that apply them.

### 2.3 Structure of a Principle

Every principle in this document carries five fields.

| Field                | Purpose                                                                                                                       |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **Name**             | A short phrase that captures the rule. Two to five words. Title case.                                                          |
| **Statement**        | One sentence that states the rule in plain language. No technical jargon, no conditions.                                       |
| **Rationale**        | Two to four sentences that state why the rule exists. The rationale is written for a non-specialist reader.                    |
| **Implications**     | A short list of the concrete consequences of adopting the principle. Each implication is a fact, not a suggestion.             |
| **Related Principles** | One sentence that names the other principles this one interacts with most, so that the shape of the set is visible.         |

The four-field structure of Name, Statement, Rationale, and Implications is drawn from The Open Group Architecture Framework (TOGAF). The Related Principles field is a register convention, added so that a reader can see how the nine principles interlock.

A principle without a rationale is an aspiration. A principle without implications is a preference. Both are mandatory.

### 2.4 Binding and Advisory Principles

A principle is **binding** by default. Every architecture decision in the register must satisfy a binding principle, or the decision requires a recorded exception.

A principle may be **advisory** when the target state cannot be achieved in Phase 1 but must be preserved for later phases. An advisory principle does not require an exception. It states the direction.

In SRIS Phase 1, all nine principles in [Section 3](#3-architecture-principles) are binding. No advisory principles are recorded in this version. If an advisory principle is added in a later revision, it is marked at the top of its section with the word **Advisory**, and its implications are marked as direction rather than requirement.

### 2.5 How a Principle Is Cited

A principle is cited by its identifier and its name. For example:

> "The decision to isolate the Notification Service satisfies [Principle 5](#35-principle-5-fail-isolated) — Fail Isolated."

A downstream document cites a principle by name and does not restate the rationale or the implications. Restating a principle in another document creates two versions of the same rule, which will eventually drift. Every principle in the register has one home: this document.

A principle is cited when:

- A design decision is made in a way that satisfies the principle and the reason is not obvious.
- A design decision is made that appears to conflict with the principle, and the conflict needs to be addressed.
- A reviewer needs to know which principles a document was written against.

A principle is not cited in every sentence. The register's citation pattern requires the first mention in a section to carry the citation; later mentions in the same section may refer to the principle by name only.

---

## 3. Architecture Principles

The nine principles of Phase 1 are recorded below. Each is binding. Each is stated in the five-field form defined in [Section 2.3](#23-structure-of-a-principle).

The principles are numbered for stable citation. The number is permanent. If a principle is retired in a later revision, its number is retired and is not reused.

### 3.1 Principle 1: Bounded Context First

**Statement.** Service boundaries must align with business capabilities and bounded contexts, not with technical layers.

**Rationale.** A service sliced by technical layer — a frontend service, a backend service, a database service — cannot own its data, cannot be deployed independently, and cannot isolate failure. A service sliced by business capability can do all three. The service boundary is the most consequential decision in a microservices architecture, because every other principle depends on it. A service that is not a bounded context cannot satisfy any of the remaining eight principles.

**Implications.**

- Each service is named after a business capability, not a technical role.
- One bounded context corresponds to one service. The mapping is one to one.
- Technical layers (UI, API, persistence, authentication) live inside each service, not as separate services.
- A service's data is owned by that service's bounded context alone.
- Cross-service interactions are determined by capability relationships, not by data dependencies.

**Related Principles.** [Principle 2](#32-principle-2-own-your-data) depends on this one — a bounded context that does not own its data is not a bounded context. [Principle 4](#34-principle-4-asynchronous-by-default) is meaningful only after this principle has fixed which services exist.

**Sources.** [SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification defines the six bounded contexts and their boundaries; the boundary decisions are recorded in its [Section 6](./SRIS-P1-ARCH-001_MicroservicesIdentification.md#6-finalized-microservices-for-phase-1) and [Section 7](./SRIS-P1-ARCH-001_MicroservicesIdentification.md#7-justification-of-service-boundaries). [SRIS-P1-REQ-002](../wave-1-requirements/SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD) states the capability ownership rule in Business Rule BRL-8.

---

### 3.2 Principle 2: Own Your Data

**Statement.** Each service owns its data and no service reads another service's data store directly.

**Rationale.** A shared database is a shared decision surface. Any service that can read another service's tables is coupled to that service's schema. Any change to that schema breaks the reader. Shared databases destroy the deployment independence that a microservices architecture exists to provide. The cost of the discipline is small: a service that needs data it does not own asks the owner for it, through an API or an event.

**Implications.**

- Each service has its own schema or schemas. No tables are shared across services.
- Cross-service data access goes through an API or an event. It never goes through a direct database read.
- A schema change in one service does not require a schema change in another.
- The foreign key constraint never crosses a service boundary. It is used only inside a single service's schema.
- Data ownership is documented in [SRIS-P1-DATA-007](./SRIS-P1-DATA-007_DataOwnershipMatrix.md) — Data Ownership Matrix when that document is written.

**Related Principles.** [Principle 1](#31-principle-1-bounded-context-first) is the precondition — without a bounded context, there is nothing for data to belong to. [Principle 3](#33-principle-3-contract-first-interface) provides the mechanism by which a service asks for data it does not own. [Principle 5](#35-principle-5-fail-isolated) depends on this one — a service whose data has been read by another service cannot fail in isolation.

**Sources.** [SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification states the rule in its [Section 6.5](./SRIS-P1-ARCH-001_MicroservicesIdentification.md#65-supporting-infrastructure). [SRIS-P1-REQ-002](../wave-1-requirements/SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD) states the same rule as Business Rule BRL-9.

---

### 3.3 Principle 3: Contract-First Interface

**Statement.** Every service interface is specified, reviewed, and frozen before implementation begins.

**Rationale.** A contract is the only artefact that allows two teams to build against each other before either has written code. In an eight-week window, parallel development is the difference between success and failure. A frozen contract also makes mocks possible, makes tests possible, and makes the interface auditable. The alternative — describing the interface after the code exists — defers the discovery of mismatch to the moment of integration, when the cost of fixing it is highest.

**Implications.**

- Every synchronous API is specified in OpenAPI before the code that implements it.
- Every asynchronous event is specified in AsyncAPI before the code that publishes or consumes it.
- The frozen contracts live in [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md) — API Contract Document (OpenAPI) and [SRIS-P1-API-003](./SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md) — Event Schema Document (AsyncAPI).
- A contract change after freezing is a versioned change, not an in-place edit. The versioning rule belongs to [SRIS-P1-API-013](./SRIS-P1-API-013_APIVersioningAndDeprecationPolicy.md) — API Versioning and Deprecation Policy.
- The idempotency and retry rules for state-changing endpoints belong to [SRIS-P1-API-005](./SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md) — Idempotency and Retry Policy Specification and are specified with the contract, not after it.

**Related Principles.** [Principle 2](#32-principle-2-own-your-data) is enforced through this one — the contract is how a service asks for data it does not own. [Principle 6](#36-principle-6-security-is-every-layer) requires the contract to state its security requirements. [Principle 4](#34-principle-4-asynchronous-by-default) uses the contract as its medium, whether the contract is synchronous or asynchronous.

**Sources.** The register's commitment to the contract-first approach is recorded throughout Wave 3 and confirmed by [SRIS-P1-REQ-005](../wave-1-requirements/SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md) — Non-Functional Requirements (ISO 25010) in requirement NFR-060.

---

### 3.4 Principle 4: Asynchronous by Default

**Statement.** Where the system can tolerate a delay, it must communicate by events rather than by synchronous calls.

**Rationale.** A synchronous call makes the caller wait for the callee. If the callee is slow, the caller is slow. If the callee is down, the caller fails. An event removes both the wait and the coupling: the publisher emits and continues, the consumer processes when it can. The choice between synchronous and asynchronous is the choice between tight coupling and independence. In a system that must survive partial failure, asynchronous is the default.

**Implications.**

- Notification dispatch is event-driven. A failed notification never fails the booking that triggered it.
- Waitlist cascade is event-driven. A cancellation is not blocked by the cascade that follows it.
- Audit entries are event-driven. A master data change is not blocked by the audit that records it.
- Synchronous calls are reserved for cases where the caller cannot proceed without an immediate answer. The search flow is synchronous because the customer is waiting. Booking confirmation is synchronous because the customer is waiting. Notification is not.
- The choice between synchronous and asynchronous is stated in [SRIS-P1-ARCH-009](./SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md) — Service Interaction and Communication Design.

**Related Principles.** [Principle 5](#35-principle-5-fail-isolated) is the direct beneficiary — an asynchronous integration is what allows a downstream service to fail without taking its caller with it. [Principle 1](#31-principle-1-bounded-context-first) is the precondition — the choice of what can be asynchronous follows from the boundary structure.

**Sources.** [SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification establishes the asynchronous integration in its [Section 6.2](./SRIS-P1-ARCH-001_MicroservicesIdentification.md#62-service-specifications). [SRIS-P1-REQ-002](../wave-1-requirements/SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD) states the isolation rule as Business Rule BRL-5.

---

### 3.5 Principle 5: Fail Isolated

**Statement.** A failure in one service must not cascade into the others.

**Rationale.** In a distributed system, failure is not the exception — it is the steady state at some fraction of the system at any given moment. The question is not whether a service will fail, but whether its failure takes the rest of the system with it. A failure that cascades is a failure that doubles, triples, or multiplies. A failure that is contained is a failure that has one cost. The principle states that containment is mandatory.

**Implications.**

- Every synchronous call carries a timeout. A caller never waits indefinitely.
- Every service that calls another exposes its dependency to a bulkhead, so that a slow dependency cannot consume all the caller's threads.
- Every critical dependency is wrapped by a circuit breaker. A repeatedly failing dependency is bypassed, and the caller returns a fallback response rather than waiting again.
- Every service declares a health check. The orchestrator removes a failing service from traffic before the failure propagates.
- A failed service restarts and recovers without operator intervention.
- The tactics that implement this principle — timeouts, bulkheads, circuit breakers, health checks, graceful restart — belong to [SRIS-P1-ARCH-011](./SRIS-P1-ARCH-011_ErrorHandlingAndResilienceDesign.md) — Error Handling and Resilience Design.

**Related Principles.** [Principle 4](#34-principle-4-asynchronous-by-default) is the primary mechanism — asynchronous integration is the default way to break a cascade. [Principle 2](#32-principle-2-own-your-data) is the precondition — a service whose data has been read by another service cannot fail in isolation. [Principle 6](#36-principle-6-security-is-every-layer) is the security counterpart — an attack on one service must not compromise the others.

**Sources.** [SRIS-P1-REQ-002](../wave-1-requirements/SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business Requirements Document (BRD) states the isolation rule as Business Rule BRL-5. [SRIS-P1-REQ-005](../wave-1-requirements/SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md) — Non-Functional Requirements (ISO 25010) states the reliability targets in requirements NFR-032 to NFR-040.

---

### 3.6 Principle 6: Security Is Every Layer

**Statement.** Security is enforced at every layer of the architecture, including the layers that are not exposed to the public internet.

**Rationale.** Internal networks are not trusted networks. A service inside a cluster is as exposed to compromise as a service at the edge, because a single compromised service can call every other service. Enterprise practice treats the internal network as untrusted and applies the same authentication, authorisation, and encryption rules inside as outside. The principle prevents the common failure where only the outer edge is protected and the internal calls run unauthenticated.

**Implications.**

- Every service authenticates every inbound request, whether the request comes from the internet or from another service.
- Service-to-service calls carry an identity and a role, not only a network address.
- All traffic in transit is encrypted, including internal traffic.
- Secrets are injected from a dedicated store, not embedded in configuration or code.
- Client-side controls — form validation, captcha, rate limits visible in the browser — are treated as user-experience aids, not security controls. Every security decision that matters is enforced on the server. The server is the outermost trust boundary of SRIS.
- The security design is recorded in [SRIS-P1-ARCH-010](./SRIS-P1-ARCH-010_SecurityArchitectureDocument.md) — Security Architecture Document, [SRIS-P1-SEC-001](./SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md) — Authentication and Authorization Design, and [SRIS-P1-SEC-008](./SRIS-P1-SEC-008_SecretsManagementPlan.md) — Secrets Management Plan.
- The infrastructure that enforces the network layer — firewall rules, TLS termination, and ingress controls — is recorded in [SRIS-P1-INF-001](../wave-5-devops-operations/SRIS-P1-INF-001_InfrastructureAndTechnologyDocument.md) — Infrastructure and Technology Document.
- The threats this principle defends against, and the controls that implement the defence, are enumerated in [SRIS-P1-SEC-004](./SRIS-P1-SEC-004_ThreatModel.md) — Threat Model and [SRIS-P1-SEC-013](./SRIS-P1-SEC-013_SecureCodingStandards.md) — Secure Coding Standards.

**Related Principles.** [Principle 1](#31-principle-1-bounded-context-first) — a bounded context that is not isolated cannot enforce its own security. [Principle 3](#33-principle-3-contract-first-interface) — a contract that does not state its security requirements is not complete. [Principle 5](#35-principle-5-fail-isolated) — an attack on one service must not compromise the others, which is the security form of failure isolation.

**Sources.** The rule is a general enterprise architecture principle. Applied to SRIS, it is recorded in the security documents of Wave 3 and the infrastructure document of Wave 5. The specific implementation of the trust boundary — server-side validation, identity on every call, encrypted transit, externalised secrets — belongs to those documents and is not restated here.

---

### 3.7 Principle 7: Observe Everything

**Statement.** Every service produces structured traces, logs, and metrics by default, from the first commit.

**Rationale.** A microservices architecture cannot be debugged by reading source code. A single user action passes through multiple services, each with its own state and its own failure modes. Without distributed tracing, a failed booking cannot be traced to the service that failed. Without structured logs, the trace cannot be read. Without metrics, the failure cannot be seen before it is reported by a customer. Observability is added at inception or it is never added well.

**Implications.**

- Every service emits a trace span for every inbound request and every outbound call.
- The trace context is propagated across every service boundary, using the OpenTelemetry and W3C conventions.
- Every log entry is structured and carries the correlation identifier of its request.
- Sensitive fields are masked in logs and traces at the point of emission, not filtered downstream.
- Every service exposes a health check endpoint that reflects its actual ability to serve traffic, not only whether the process is running.
- The conventions are recorded in [SRIS-P1-ARCH-012](./SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md) — Observability and Monitoring Design (OTel/W3C).
- The masking rules are recorded in [SRIS-P1-SEC-012](./SRIS-P1-SEC-012_DataClassificationRegister.md) — Data Classification Register.

**Related Principles.** [Principle 5](#35-principle-5-fail-isolated) — a failed service cannot be isolated if its failure cannot be seen. [Principle 6](#36-principle-6-security-is-every-layer) — masked sensitive fields are a security requirement, not only an observability one. [Principle 9](#39-principle-9-prefer-simplicity-under-constraint) — the observability stack must fit within the same resource budget as the services it observes.

**Sources.** [SRIS-P1-REQ-005](../wave-1-requirements/SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md) — Non-Functional Requirements (ISO 25010) states the observability requirements in NFR-112, NFR-113, and NFR-116.

---

### 3.8 Principle 8: Deploy by Configuration Alone

**Statement.** The full SRIS stack is deployable to a new host by changing only the orchestration configuration file, with no change to any service's code, image, or contract.

**Rationale.** Environment-specific builds are a hidden form of coupling. If a service behaves differently in one environment than another, every test that passed in the first environment is suspect in the second. A service that carries its configuration from outside its own artefact behaves identically wherever it runs, so that a demo on a local server and a deployment to a cloud host produce the same result. The principle is what makes the local demo a valid demonstration of the cloud-ready system.

**Implications.**

- Every container image is built once and deployed everywhere. The image is byte-identical across environments.
- Every configuration value — database URL, broker URL, port, feature flag, third-party endpoint, secret — is read from an environment variable or from a mounted configuration file. Nothing is baked into the image.
- No service writes persistent state to the container's filesystem. Persistent state lives in a database, a named volume, or an external store.
- No hostname, IP address, or port is hardcoded in the source code.
- The orchestration configuration declares the startup order, the health checks, the network, and the volumes for every service. It contains no host-specific directive.
- The environment contract is recorded in [SRIS-P1-INF-011](../wave-5-devops-operations/SRIS-P1-INF-011_EnvironmentVariablesAndConfigurationReference.md) — Environment Variables and Configuration Reference.
- The deployment procedure is recorded in [SRIS-P1-OPS-001](../wave-5-devops-operations/SRIS-P1-OPS-001_DeploymentGuide.md) — Deployment Guide and its target topology in [SRIS-P1-ARCH-013](./SRIS-P1-ARCH-013_DeploymentArchitectureDocument.md) — Deployment Architecture Document.

**Related Principles.** [Principle 6](#36-principle-6-security-is-every-layer) — an externalised secret is both a portability mechanism and a security requirement. [Principle 7](#37-principle-7-observe-everything) — the observability exporter is also configured from environment, not baked in. [Principle 9](#39-principle-9-prefer-simplicity-under-constraint) — portability is not achieved with proprietary platform features; it is achieved with portable primitives.

**Sources.** [SRIS-P1-REQ-005](../wave-1-requirements/SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md) — Non-Functional Requirements (ISO 25010) states the portability requirements in NFR-067 to NFR-075, including the cloud-swap requirement at NFR-071.

---

### 3.9 Principle 9: Prefer Simplicity Under Constraint

**Statement.** When two designs satisfy the same requirement, the simpler one is chosen, and any complexity added must be justified against the resource envelope.

**Rationale.** SRIS Phase 1 runs within a 5.1 GB RAM envelope, a zero budget, and an eight-week window. Every additional process, every additional library, and every additional abstraction has a cost in memory, time, or both. Complexity that is not paid for by a corresponding benefit is waste that the system cannot afford. The principle does not forbid complexity; it requires that complexity be justified, recorded, and bounded. This is the principle that keeps the other eight achievable.

**Implications.**

- Every service is written in a runtime whose baseline memory footprint fits within the per-service ceiling defined in [SRIS-P1-REQ-005](../wave-1-requirements/SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md) — Non-Functional Requirements (ISO 25010) at NFR-014.
- A new library, framework, or tool is added only when it satisfies a requirement that cannot be met more simply.
- The build uses the minimum tooling that produces a working, tested artefact. Build-time convenience is subordinate to runtime envelope.
- No service is split into a separate deployable process unless the split is required by a bounded context and permitted by the memory envelope.
- Where two capabilities share a bounded context, they live in one service. Where they do not, they may still be consolidated as internal modules of a single deployable if the consolidation is required to fit the envelope. The module boundary rules of [SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification apply and preserve the extraction path.
- Any complexity that is accepted is recorded in [SRIS-P1-ARCH-007](./SRIS-P1-ARCH-007_ArchitectureDecisionRecordsMasterIndex.md) — Architecture Decision Records — Master Index, with the reason and the reversal plan.

**Related Principles.** [Principle 1](#31-principle-1-bounded-context-first) — the boundary is decided first; consolidation is a delivery decision that follows, not a boundary decision. [Principle 5](#35-principle-5-fail-isolated) — fault isolation is achieved through tactics inside the code, not by adding redundant deployables that exceed the envelope. [Principle 8](#38-principle-8-deploy-by-configuration-alone) — portability is reached through portable primitives, not by adding a platform-specific layer.

**Sources.** [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document fixes the operative constraints: C-2 (5.1 GB RAM), C-3 (zero budget), and C-1 (eight-week window). [SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification applies the consolidation principle in its [Section 7.2](./SRIS-P1-ARCH-001_MicroservicesIdentification.md#72-consolidations) and preserves the extraction path in its [Section 7.4](./SRIS-P1-ARCH-001_MicroservicesIdentification.md#74-internal-module-boundary-rules).

---

## 4. Conflict Resolution and Exceptions

### 4.1 How Conflicts Between Principles Are Resolved

Two principles can pull in opposite directions. For example, [Principle 4](#34-principle-4-asynchronous-by-default) favours asynchronous communication, while [Principle 5](#35-principle-5-fail-isolated) may favour a synchronous call with a short timeout when a caller cannot proceed without an immediate answer. [Principle 9](#39-principle-9-prefer-simplicity-under-constraint) favours consolidation, while [Principle 1](#31-principle-1-bounded-context-first) favours splitting.

When two principles conflict, the resolution follows a fixed order.

| Order | Rule |
| ----- | ---- |
| 1 | The conflict is resolved by the Lead Architect, who is the decision authority for Phase 1 as recorded in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document. |
| 2 | A principle that protects the system's ability to satisfy its Phase 1 success criterion takes precedence over a principle that improves the system's quality. |
| 3 | Where the precedence is not clear, the principle with the larger number yields to the principle with the smaller number. The numbering is not arbitrary: principles one to five are structural, principles six to eight are operational, and principle nine is a delivery constraint. Structural principles come first because every operational principle depends on the structure being correct. |
| 4 | The resolution is recorded in [SRIS-P1-ARCH-007](./SRIS-P1-ARCH-007_ArchitectureDecisionRecordsMasterIndex.md) — Architecture Decision Records — Master Index as an ADR. |
| 5 | The affected documents that cite either principle are reviewed and updated if the resolution changes their content. |

A conflict that is resolved silently is not a conflict that has been resolved. It is a conflict that will be resolved twice, in two different ways, in two different documents.

### 4.2 When a Principle Cannot Be Met

A principle may be impossible to satisfy in Phase 1 because of a fixed constraint. For example:

- [Principle 5](#35-principle-5-fail-isolated) prescribes physical fault isolation. The 5.1 GB RAM constraint (C-2 in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document) does not permit running duplicate instances of every service. Fault isolation is achieved logically through timeouts, bulkheads, and circuit breakers rather than physically through replica count.
- [Principle 6](#36-principle-6-security-is-every-layer) prescribes authenticated service-to-service calls. A service may not be able to authenticate every inbound call in Phase 1 if the token infrastructure is still being built. In that case, the gap is recorded and the service is brought into compliance as soon as the infrastructure exists.

A constraint does not cancel a principle. A constraint means the principle is satisfied by an adaptation, and the adaptation is recorded. A principle that is neither satisfied nor adapted is a principle that has been abandoned without a decision, which is the failure mode the exception mechanism exists to prevent.

### 4.3 Recording an Exception

Every exception to a binding principle is recorded in [SRIS-P1-ARCH-007](./SRIS-P1-ARCH-007_ArchitectureDecisionRecordsMasterIndex.md) — Architecture Decision Records — Master Index, using the Architecture Decision Record format defined in that document. The exception record states:

| Field | Content |
| ----- | ------- |
| **Principle** | The identifier and name of the principle that is not being satisfied. |
| **Context** | The constraint or condition that makes full satisfaction impossible in Phase 1. |
| **Decision** | The adaptation that is adopted instead of full compliance. |
| **Consequence** | What the adaptation costs the system, stated honestly. |
| **Reversal plan** | The condition under which full compliance is restored. |
| **Status** | Accepted, Pending, or Superseded. |

An exception is not a retirement of the principle. The principle remains binding. The exception records that, for a stated reason and for a stated duration, the principle is satisfied by an adaptation rather than literally. When the condition in the reversal plan is met, the exception is superseded and the principle is satisfied without adaptation.

An exception without a reversal plan is a silent replacement of the principle. That is not permitted. A principle is either satisfied, or satisfied by adaptation, or formally retired in a revision of this document. There is no fourth state.

---

## 5. Traceability

This section records the local traceability of every principle in this document. It maps each principle to the documents that cite it, to the quality attributes it protects, and to the requirements that give it a measurable form.

The full cross-wave matrix, which spans every document in the register, belongs to [SRIS-P1-REQ-012](../wave-1-requirements/SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md) — Requirement Traceability Matrix (RTM), and is not repeated here.

### 5.1 Principles and the Documents That Apply Them

| Principle | Name | Applied By |
| --------- | ---- | ---------- |
| 1 | Bounded Context First | [SRIS-P1-ARCH-003](./SRIS-P1-ARCH-003_SystemArchitectureDocument.md) — System Architecture Document; [SRIS-P1-ARCH-004](./SRIS-P1-ARCH-004_BoundedContextMap.md) — Bounded Context Map |
| 2 | Own Your Data | [SRIS-P1-DATA-001](./SRIS-P1-DATA-001_DataDesignDocument.md) — Data Design Document; [SRIS-P1-DATA-007](./SRIS-P1-DATA-007_DataOwnershipMatrix.md) — Data Ownership Matrix |
| 3 | Contract-First Interface | [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md) — API Contract Document (OpenAPI); [SRIS-P1-API-003](./SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md) — Event Schema Document (AsyncAPI) |
| 4 | Asynchronous by Default | [SRIS-P1-ARCH-009](./SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md) — Service Interaction and Communication Design |
| 5 | Fail Isolated | [SRIS-P1-ARCH-011](./SRIS-P1-ARCH-011_ErrorHandlingAndResilienceDesign.md) — Error Handling and Resilience Design |
| 6 | Security Is Every Layer | [SRIS-P1-ARCH-010](./SRIS-P1-ARCH-010_SecurityArchitectureDocument.md) — Security Architecture Document; [SRIS-P1-SEC-001](./SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md) — Authentication and Authorization Design; [SRIS-P1-INF-001](../wave-5-devops-operations/SRIS-P1-INF-001_InfrastructureAndTechnologyDocument.md) — Infrastructure and Technology Document |
| 7 | Observe Everything | [SRIS-P1-ARCH-012](./SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md) — Observability and Monitoring Design (OTel/W3C) |
| 8 | Deploy by Configuration Alone | [SRIS-P1-ARCH-013](./SRIS-P1-ARCH-013_DeploymentArchitectureDocument.md) — Deployment Architecture Document; [SRIS-P1-INF-011](../wave-5-devops-operations/SRIS-P1-INF-011_EnvironmentVariablesAndConfigurationReference.md) — Environment Variables and Configuration Reference |
| 9 | Prefer Simplicity Under Constraint | [SRIS-P1-ARCH-008](./SRIS-P1-ARCH-008_TechnologyStackADR.md) — Technology Stack ADR; [SRIS-P1-ARCH-014](./SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md) — Distributed Concurrency and Locking Strategy |

### 5.2 Principles and the Quality Attributes They Protect

| Principle | Primary ISO/IEC 25010:2023 Attribute |
| --------- | ------------------------------------ |
| 1 | Maintainability (Modularity) |
| 2 | Maintainability (Modularity); Reliability (Fault Tolerance) |
| 3 | Maintainability (Modifiability); Compatibility (Interoperability) |
| 4 | Reliability (Fault Tolerance); Performance Efficiency (Time Behaviour) |
| 5 | Reliability (Fault Tolerance); Reliability (Recoverability) |
| 6 | Security (Confidentiality, Integrity, Authenticity) |
| 7 | Maintainability (Analysability); Reliability (Recoverability) |
| 8 | Flexibility (Adaptability, Installability) |
| 9 | Performance Efficiency (Resource Utilisation); Flexibility (Adaptability) |

The quality attributes are defined in [SRIS-P1-REQ-005](../wave-1-requirements/SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md) — Non-Functional Requirements (ISO 25010).

### 5.3 Principles and the Requirements That Give Them Measurable Form

The non-functional requirements cited in this table are defined in [SRIS-P1-REQ-005](../wave-1-requirements/SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md) — Non-Functional Requirements (ISO 25010). Each row maps a principle to the requirement that measures it, or states that the principle is verified by inspection.

| Principle | Non-Functional Requirement That Measures It |
| --------- | ------------------------------------------ |
| 1 | No direct measure. Verified by inspection of the service boundary structure against [SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification. |
| 2 | No direct measure. Verified by inspection of the data model against [SRIS-P1-DATA-007](./SRIS-P1-DATA-007_DataOwnershipMatrix.md) — Data Ownership Matrix. |
| 3 | NFR-060 — Contract-First Interfaces. |
| 4 | NFR-038 — Notification Failure Does Not Block Booking. |
| 5 | NFR-037 — Failure of One Service Does Not Cascade. |
| 6 | NFR-041 to NFR-057 — the security requirements. |
| 7 | NFR-112, NFR-113, NFR-116 — correlation, structured logging, and distributed tracing. |
| 8 | NFR-067 to NFR-075 — the portability requirements, including NFR-071 (cloud deployment by configuration change alone). |
| 9 | NFR-013 — Combined Memory Footprint of the Six Services; NFR-014 — Per-Service Memory Ceiling. |

A principle that has no measurable form is not a principle that cannot be verified. It is a principle that is verified by inspection of the structure rather than by a numeric target. Both forms are valid.

---

## 6. Approval

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
| 1.1  | [SRIS-P1-REQ-001](../wave-1-requirements/SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md)                     | Glossary and Domain Dictionary                    | 1    | P0  | UNBLOCK |
| 1.2  | [SRIS-P1-REQ-002](../wave-1-requirements/SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md)                | Business Requirements Document (BRD)              | 1    | P0  | UNBLOCK |
| 1.4  | [SRIS-P1-REQ-004](../wave-1-requirements/SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md)            | Software Requirements Specification (SRS)         | 1    | P0  | UNBLOCK |
| 1.5  | [SRIS-P1-REQ-005](../wave-1-requirements/SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md)               | Non-Functional Requirements (ISO 25010)           | 1    | P0  | UNBLOCK |
| 1.12 | [SRIS-P1-REQ-012](../wave-1-requirements/SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md)               | Requirement Traceability Matrix (RTM)             | 1    | P2  | FOLLOW  |
| 2.1  | [SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md)                                       | Microservices Identification                      | 2    | P0  | UNBLOCK |
| 2.3  | [SRIS-P1-ARCH-003](./SRIS-P1-ARCH-003_SystemArchitectureDocument.md)                                        | System Architecture Document                      | 2    | P0  | UNBLOCK |
| 2.4  | [SRIS-P1-ARCH-004](./SRIS-P1-ARCH-004_BoundedContextMap.md)                                                 | Bounded Context Map                               | 2    | P0  | UNBLOCK |
| 2.5  | [SRIS-P1-ARCH-005](./SRIS-P1-ARCH-005_DomainModelDocument.md)                                               | Domain Model Document                             | 2    | P0  | UNBLOCK |
| 2.7  | [SRIS-P1-ARCH-007](./SRIS-P1-ARCH-007_ArchitectureDecisionRecordsMasterIndex.md)                            | Architecture Decision Records — Master Index      | 2    | P1  | FOLLOW  |
| 2.8  | [SRIS-P1-ARCH-008](./SRIS-P1-ARCH-008_TechnologyStackADR.md)                                                 | Technology Stack ADR                              | 2    | P0  | UNBLOCK |
| 2.9  | [SRIS-P1-ARCH-009](./SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md)                           | Service Interaction and Communication Design      | 2    | P0  | UNBLOCK |
| 2.10 | [SRIS-P1-ARCH-010](./SRIS-P1-ARCH-010_SecurityArchitectureDocument.md)                                      | Security Architecture Document                    | 2    | P1  | FOLLOW  |
| 2.11 | [SRIS-P1-ARCH-011](./SRIS-P1-ARCH-011_ErrorHandlingAndResilienceDesign.md)                                  | Error Handling and Resilience Design              | 2    | P1  | FOLLOW  |
| 2.12 | [SRIS-P1-ARCH-012](./SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)                           | Observability and Monitoring Design (OTel/W3C)    | 2    | P0  | UNBLOCK |
| 2.13 | [SRIS-P1-ARCH-013](./SRIS-P1-ARCH-013_DeploymentArchitectureDocument.md)                                    | Deployment Architecture Document                  | 2    | P1  | FOLLOW  |
| 2.14 | [SRIS-P1-ARCH-014](./SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md)                          | Distributed Concurrency and Locking Strategy      | 2    | P0  | UNBLOCK |
| 2.15 | [SRIS-P1-ARCH-015](./SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md)                        | Distributed Transaction and Saga Pattern Design   | 2    | P0  | UNBLOCK |
| 2.16 | [SRIS-P1-ARCH-016](./SRIS-P1-ARCH-016_ServiceRegistryAndCatalog.md)                                         | Service Registry and Catalog                      | 2    | P0  | UNBLOCK |
| 3.1  | [SRIS-P1-DATA-001](./SRIS-P1-DATA-001_DataDesignDocument.md)                                                | Data Design Document                              | 3    | P0  | UNBLOCK |
| 3.7  | [SRIS-P1-DATA-007](./SRIS-P1-DATA-007_DataOwnershipMatrix.md)                                               | Data Ownership Matrix                             | 3    | P1  | FOLLOW  |
| 3.14 | [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md)                                          | API Contract Document (OpenAPI)                   | 3    | P0  | UNBLOCK |
| 3.16 | [SRIS-P1-API-003](./SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md)                                         | Event Schema Document (AsyncAPI)                  | 3    | P0  | UNBLOCK |
| 3.18 | [SRIS-P1-API-005](./SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md)                              | Idempotency and Retry Policy Specification        | 3    | P0  | UNBLOCK |
| 3.26 | [SRIS-P1-API-013](./SRIS-P1-API-013_APIVersioningAndDeprecationPolicy.md)                                   | API Versioning and Deprecation Policy             | 3    | P2  | FOLLOW  |
| 3.39 | [SRIS-P1-SEC-001](./SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)                                | Authentication and Authorization Design           | 3    | P1  | FOLLOW  |
| 3.42 | [SRIS-P1-SEC-004](./SRIS-P1-SEC-004_ThreatModel.md)                                                         | Threat Model                                      | 3    | P1  | FOLLOW  |
| 3.46 | [SRIS-P1-SEC-008](./SRIS-P1-SEC-008_SecretsManagementPlan.md)                                               | Secrets Management Plan                           | 3    | P1  | FOLLOW  |
| 3.49 | [SRIS-P1-SEC-012](./SRIS-P1-SEC-012_DataClassificationRegister.md)                                          | Data Classification Register                      | 3    | P0  | UNBLOCK |
| 3.50 | [SRIS-P1-SEC-013](./SRIS-P1-SEC-013_SecureCodingStandards.md)                                               | Secure Coding Standards                           | 3    | P0  | UNBLOCK |
| 5.1  | [SRIS-P1-INF-001](../wave-5-devops-operations/SRIS-P1-INF-001_InfrastructureAndTechnologyDocument.md)         | Infrastructure and Technology Document            | 5    | P0  | UNBLOCK |
| 5.11 | [SRIS-P1-INF-011](../wave-5-devops-operations/SRIS-P1-INF-011_EnvironmentVariablesAndConfigurationReference.md) | Environment Variables and Configuration Reference | 5    | P0  | UNBLOCK |
| 5.12 | [SRIS-P1-OPS-001](../wave-5-devops-operations/SRIS-P1-OPS-001_DeploymentGuide.md)                             | Deployment Guide                                  | 5    | P1  | FOLLOW  |

### B.2 Documents That Reference This Document

| Seq  | Document ID                                                                                | Document Name                          | Why It References                                                                 |
| ---- | ------------------------------------------------------------------------------------------ | -------------------------------------- | --------------------------------------------------------------------------------- |
| 0.0  | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) | Documentation Index and Navigation Map | Lists this document in the register and in the reading paths                       |
| 0.4  | [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)      | Project Vision and Scope Document      | Names this document as a downstream document                                       |
| 2.1  | [SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md)                           | Microservices Identification           | Lists this document as a Hard downstream document                                  |

Every Wave 2 architecture document from ARCH-003 to ARCH-016 is written against these principles and cites them where a design decision is made. The complete list is in [B.5](#b5-master-documentation-index).

### B.3 Documents This Document Depends On (Upstream)

| Seq | Document ID                                                                                 | Document Name                          | Dependency Type |
| --- | ------------------------------------------------------------------------------------------- | -------------------------------------- | --------------- |
| 0.0 | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) | Documentation Index and Navigation Map | Soft            |
| 0.1 | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)           | Document Template Standard             | Hard            |
| 0.2 | [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)        | Document ID and Category Scheme        | Hard            |
| 0.3 | [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md)     | Document Cross-Reference Standard      | Hard            |
| 0.4 | [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)      | Project Vision and Scope Document      | Hard            |
| 1.1 | [SRIS-P1-REQ-001](../wave-1-requirements/SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md)             | Glossary and Domain Dictionary         | Hard            |
| 1.2 | [SRIS-P1-REQ-002](../wave-1-requirements/SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md)        | Business Requirements Document (BRD)   | Hard            |
| 1.5 | [SRIS-P1-REQ-005](../wave-1-requirements/SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md)      | Non-Functional Requirements (ISO 25010) | Hard            |
| 2.1 | [SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md)                                 | Microservices Identification           | Hard            |

### B.4 Documents This Document Unblocks (Downstream)

| Seq  | Document ID                                                                      | Document Name                                | Blocked Until |
| ---- | -------------------------------------------------------------------------------- | -------------------------------------------- | ------------- |
| 2.3  | [SRIS-P1-ARCH-003](./SRIS-P1-ARCH-003_SystemArchitectureDocument.md)                | System Architecture Document                 | This approved |
| 2.4  | [SRIS-P1-ARCH-004](./SRIS-P1-ARCH-004_BoundedContextMap.md)                        | Bounded Context Map                          | This approved |
| 2.5  | [SRIS-P1-ARCH-005](./SRIS-P1-ARCH-005_DomainModelDocument.md)                      | Domain Model Document                        | This approved |
| 2.7  | [SRIS-P1-ARCH-007](./SRIS-P1-ARCH-007_ArchitectureDecisionRecordsMasterIndex.md)    | Architecture Decision Records — Master Index  | This approved |
| 2.8  | [SRIS-P1-ARCH-008](./SRIS-P1-ARCH-008_TechnologyStackADR.md)                        | Technology Stack ADR                         | This approved |
| 2.9  | [SRIS-P1-ARCH-009](./SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md)  | Service Interaction and Communication Design  | This approved |
| 2.12 | [SRIS-P1-ARCH-012](./SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)   | Observability and Monitoring Design (OTel/W3C) | This approved |
| 2.13 | [SRIS-P1-ARCH-013](./SRIS-P1-ARCH-013_DeploymentArchitectureDocument.md)            | Deployment Architecture Document              | This approved |
| 2.14 | [SRIS-P1-ARCH-014](./SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md)  | Distributed Concurrency and Locking Strategy  | This approved |
| 2.15 | [SRIS-P1-ARCH-015](./SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md) | Distributed Transaction and Saga Pattern Design | This approved |
| 2.16 | [SRIS-P1-ARCH-016](./SRIS-P1-ARCH-016_ServiceRegistryAndCatalog.md)                 | Service Registry and Catalog                 | This approved |

### B.5 Master Documentation Index

The complete list of Phase 1 documents is in [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

### B.6 External Reference Documents

| Reference Type                                                       | Where It Is Documented                                                                                                                       |
| -------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| The Open Group Architecture Framework (TOGAF), 10th Edition          | The Open Group. Referenced for the four-part structure of an architecture principle: Name, Statement, Rationale, and Implications.           |
| Bass, Clements, and Kazman, "Software Architecture in Practice", 4th Edition | Addison-Wesley, 2021. Referenced for the distinction between an architecture principle, an architectural tactic, and an architectural pattern. |
| Michael Nygard, "Documenting Architecture Decisions"                 | Cognitect, 2011. Referenced for the Architecture Decision Record format used by the exception mechanism.                                     |

### B.7 Document Conventions

The conventions for Priority and Tag values are defined in [Section 9](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md#9-vocabulary-standards) of [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.

---

**End of Document**