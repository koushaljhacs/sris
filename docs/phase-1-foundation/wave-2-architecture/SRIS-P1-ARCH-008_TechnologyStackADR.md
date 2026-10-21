<div align="center">

![Wave](https://img.shields.io/badge/Wave-2-0550AE?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-ARCH-6e7781?style=for-the-badge)

</div>

# Technology Stack ADR

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** 1.0 | **Date:** 2026-10-17 | **Document ID:** SRIS-P1-ARCH-008

| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| Title              | Technology Stack ADR                                              |
| Software           | SRIS                                                              |
| Software Full Form | Sarathi Railway Information System                                |
| Team Codename      | Project Sarathi                                                   |
| Document ID        | SRIS-P1-ARCH-008                                                  |
| Task               | Record the architecture decision for the Phase 1 technology stack |
| Document Type      | Architecture Decision Document                                    |
| Milestone          | Phase 1 Foundation                                                |
| Classification     | Internal                                                          |
| Version            | 1.0                                                               |
| Date               | 2026-10-17                                                        |
| Author             | Koushal Jha, Lead Architect                                       |
| Approved By        | Koushal Jha, Lead Architect                                       |
| Approval Date      | 2026-10-17                                                        |
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
2. [Decision Drivers and Constraints](#2-decision-drivers-and-constraints)
   - [2.1 The Resource Envelope](#21-the-resource-envelope)
   - [2.2 Architectural Principles](#22-architectural-principles)
   - [2.3 Team and Timeline](#23-team-and-timeline)
3. [Considered Options](#3-considered-options)
   - [3.1 Frontend Frameworks](#31-frontend-frameworks)
   - [3.2 Backend Languages and Runtimes](#32-backend-languages-and-runtimes)
   - [3.3 Databases and Message Brokers](#33-databases-and-message-brokers)
4. [Decision Outcome](#4-decision-outcome)
   - [4.1 The Final Stack](#41-the-final-stack)
   - [4.2 Justification by Layer](#42-justification-by-layer)
   - [4.3 System Topology](#43-system-topology)
5. [Consequences](#5-consequences)
6. [Approval](#6-approval)

- [Revision History](#revision-history)
- [Appendix A: Not Applicable](#appendix-a-not-applicable)
- [Appendix B: Related Documents](#appendix-b-related-documents)

---

## 1. Introduction

### 1.1 Purpose

This document is the Technology Stack Architecture Decision Record (ADR) for Phase 1 of SRIS. It records the definitive technology choices for the frontend, backend, data, and infrastructure layers. It explains why each technology was selected, evaluates the alternatives that were rejected, and confirms how the chosen stack satisfies the strict operational constraints of Phase 1. 

### 1.2 Scope

**In scope**

- The programming languages and frameworks for the backend and frontend.
- The database technologies, caching, and messaging mechanisms.
- The API gateway, VPN, and observability tools.
- The anti-bot and anomaly detection mechanisms.

**Out of scope**

- The detailed API contracts, which belong to [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md) — API Contract Document (OpenAPI).
- The physical database schemas, which belong to [SRIS-P1-DATA-003](./SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md) — Physical Database Schema Document.
- The deployment pipeline mechanics, which belong to [SRIS-P1-INF-003](../wave-5-devops-operations/SRIS-P1-INF-003_CICDPipelineDesign.md) — CI/CD Pipeline Design.

### 1.3 Audience

- **Lead Architect:** maintains this document and is the authority on technology changes.
- **Backend and frontend developers:** must build using the exact technologies specified here. Deviations require a new ADR.
- **DevOps engineer:** uses the infrastructure choices (Docker, Nginx, Tailscale) to provision the environment.
- **Project supervisor and evaluator:** verifies that the chosen stack is realistic, justified, and fits the constraints.

### 1.4 Terminology and Conventions

Every term in this document has the meaning recorded in [SRIS-P1-REQ-001](../wave-1-requirements/SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary. The terms below carry the most weight in this document.

| Term | Meaning |
| :--- | :--- |
| ADR | Architecture Decision Record. A document capturing a critical architectural choice. |
| SPA | Single Page Application. A web application that loads a single HTML page and dynamically updates content. |
| JVM | Java Virtual Machine. The runtime environment that executes Java bytecode. |
| Streams | A Redis data structure that acts as an append-only log for guaranteed message delivery. |
| TTL | Time-To-Live. A mechanism that automatically deletes a data key after a specified period. |
| OOM | Out Of Memory. A state where the operating system kills a process because it exceeded its memory limit. |

---

## 2. Decision Drivers and Constraints

To maintain FAANG-grade rigour, technology choices cannot be based on preference. They must be driven by hard constraints and architectural principles.

### 2.1 The Resource Envelope

The absolute governing constraint for Phase 1 is hardware. The entire 6-service architecture, its databases, and its background processes must run on a single **local laptop environment** with a strict **5.1 GB of RAM** (Constraint C-2 in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document). 

This constraint immediately eliminates many enterprise technologies. Apache Kafka and heavy ML libraries are forbidden. Every chosen technology must be inherently lightweight or strictly memory-capped using Docker to prevent Linux Out-Of-Memory (OOM) terminations.

### 2.2 Architectural Principles

The stack must natively support the nine binding rules in [SRIS-P1-ARCH-002](./SRIS-P1-ARCH-002_ArchitecturePrinciples.md) — Architecture Principles. Specifically:
- **Principle 1 (Bounded Context First):** The stack must allow 6 independently deployable services.
- **Principle 2 (Own Your Data):** The databases must support logical separation per service.
- **Principle 3 (Contract-First):** The stack must support OpenAPI (REST) and AsyncAPI (Events).
- **Principle 4 (Asynchronous by Default):** The stack requires a lightweight, persistent message broker.
- **Principle 8 (Deploy by Configuration Alone):** The stack must be containerised (Docker) to guarantee environment parity.

### 2.3 Team and Timeline

The project must be delivered by a small team of five members in approximately eight weeks (Constraints C-1 and C-4). The chosen technologies must balance rapid development velocity with the ability to enforce strict domain invariants (such as the double-booking prevention rule in S3).

---

## 3. Considered Options

We evaluated multiple technologies across the frontend, backend, and data layers.

### 3.1 Frontend Frameworks

- **Plain HTML/CSS/JavaScript:** Rejected. While lightweight, it requires full-page reloads, which wipes passenger data during the multi-step booking flow. It is also difficult to implement invisible behavioral biometrics for bot detection.
- **Vue.js:** Considered. It is lightweight and easy to learn. However, it lacks the mature enterprise ecosystem and component libraries available in the React ecosystem.
- **Next.js (React):** Selected. It provides server-side rendering (SSR) for fast initial loads, client-side routing to prevent data loss during the booking flow, and the ability to intercept API errors for graceful degradation.

### 3.2 Backend Languages and Runtimes

- **Java 17 with Spring Boot:** Selected for core transactional services. It provides strong typing, mature ACID transaction management, and the ability to handle heavy multi-threaded database row locking required for post-payment seat allocation.
- **Node.js with NestJS:** Selected for the API Gateway, Search BFF, and IAM. NestJS provides a structured, modular architecture mirroring Spring Boot, while using a non-blocking event loop for highly efficient I/O-bound operations.
- **Python:** Selected for the automation daemon. It is used for system monitoring and anomaly detection (bot pattern recognition) via the `psutil` and `scikit-learn` libraries.
- **Go:** Rejected. While highly performant, the team's proficiency is lower, and the ecosystem lacks the mature ORMs and testing frameworks we need for rapid delivery.

### 3.3 Databases and Message Brokers

- **Apache Kafka:** Rejected. It is the enterprise standard for event streaming, but it is far too heavy for a 5.1 GB environment.
- **Redis Pub/Sub:** Rejected. It operates on an "At-Most-Once" delivery model. If a consumer goes offline, messages are permanently lost.
- **Redis Streams:** Selected. It provides an append-only log with consumer groups and message acknowledgment (At-Least-Once delivery). This ensures zero data loss for the integration events while staying within RAM limits.
- **MongoDB:** Rejected. MongoDB's WiredTiger engine aggressively reserves host memory (often 50% of RAM). Running a separate document database solely for logs is a waste of the 5.1 GB envelope.
- **PostgreSQL:** Selected. The industry standard for ACID-compliant relational data. It is also used for storing unstructured notification logs via the JSONB data type, eliminating the need for MongoDB.

---

## 4. Decision Outcome

### 4.1 The Final Stack

The following technologies are locked for Phase 1. Any deviation requires a new version of this ADR.

| Layer | Technology |
| :--- | :--- |
| Frontend | Next.js (React) + Tailwind CSS |
| Frontend Hosting | GitHub Pages (Static Export) |
| Core Backend | Java 17 + Spring Boot + Hibernate ORM |
| API Backend | Node.js + NestJS + Prisma ORM |
| Automation | Python (Lightweight Daemon with psutil) |
| Transactional Database | PostgreSQL (with JSONB for logs) |
| Cache & Messaging | Redis Streams (Event Broker) |
| API Gateway & VPN | Nginx (Passive Health Checks) + Tailscale |
| Real-Time Dashboard | Grafana + Loki + Promtail |
| Metrics Collection | Prometheus |
| Database Migrations | Flyway (Java) + Prisma Migrate (Node.js) |
| API Documentation | Swagger / OpenAPI 3 (Springdoc & NestJS Swagger) |
| Testing Frameworks | JUnit 5 & Mockito (Java), Jest (Node.js), PyTest (Python) |
| Anti-Bot Strategy | Behavioral Biometrics (Next.js) + Nginx Rate Limiting |
| Custom SMS Gateway | Android SMS Manager App (Connected via Tailscale) |
| CI/CD | GitHub Actions |
| Containerisation | Docker + Docker Compose |

### 4.2 Justification by Layer

**Java 17 + Spring Boot (S2 Master Data, S3 Reservation):**
Java is selected for the core transactional services because the Reservation Service (S3) enforces the most critical invariant in SRIS: *"A seat is never allocated to two active reservations on the same journey segment."* SRIS uses a **Post-Payment Allocation** model. When 700 users pay at the same time, 700 webhooks hit S3 simultaneously. S3 must handle these webhooks with strict multi-threaded ACID transactions, cascading from Confirmed seats to RAC, then Waitlist, then automatic Refund (Saga Pattern). Node.js would struggle under this CPU-bound row-locking load. Java's strong typing and Spring Boot's transaction management are essential here. 

**Node.js + NestJS (S1 IAM, S4 Search BFF, S6 Notification):**
Node.js is selected for these services because they are highly I/O-bound. The Search BFF must aggregate data from multiple services concurrently, and S1 IAM must handle high-throughput token validation. NestJS is specifically chosen over bare Express because its built-in Dependency Injection and modular architecture mirror Spring Boot.

**Python (Embedded Automation Daemon):**
Python runs inside the S6 container to monitor CPU/RAM usage and detect anomaly patterns (bot attacks). It uses `psutil` to ensure the server does not exceed the 5.1 GB ceiling, and `scikit-learn` to detect rapid-fire API requests from botnets. Heavy AI/ML libraries like TensorFlow are strictly deferred to Phase 2.

**PostgreSQL (S1, S2, S3, S5, S6):**
PostgreSQL is selected for all data. Each service operates its own logical schema to enforce the "Own Your Data" principle. To protect the 5.1 GB envelope, MongoDB was eliminated; the Notification Service (S6) stores logs in a PostgreSQL `JSONB` column. **To prevent PostgreSQL's multi-process architecture from exhausting the host RAM, strict connection pooling is mandated: HikariCP for Java services (capped at 5 connections) and Prisma client limits for Node.js (capped at 3 connections).**

**Redis Streams & Transactional Outbox (Cache & Messaging):**
Redis is selected for two critical functions: caching seat availability and acting as the persistent message broker for the 8 integration events. It replaces Apache Kafka (too heavy) and Redis Pub/Sub (which drops messages). 
To prevent the **Dual-Write Problem** (where the database saves the booking but the Redis event fails to publish), the Reservation Service (S3) implements the **Transactional Outbox Pattern**. S3 writes the domain event to a dedicated `outbox` table within the exact same PostgreSQL ACID transaction as the seat allocation. A separate background relay process then reads from this outbox table and publishes to Redis Streams. This guarantees absolute consistency and "At-Least-Once" delivery.

**Nginx (API Gateway & Passive Health Checks):**
Nginx is selected as the API Gateway because it has a virtually zero-RAM footprint while providing enterprise-grade routing and SSL termination. It relies on open-source **passive health checks** (`max_fails` and `fail_timeout`) to detect when a backend service is down. Unlike paid NGINX Plus, which proactively pings services, the open-source version detects failures only when a live request fails. Once the threshold is reached, Nginx temporarily removes the service from the load balancer and returns a `503 Service Unavailable`, mimicking a circuit breaker. Nginx also enforces **Rate Limiting** based on the user's JWT token, preventing botnets from spamming the APIs.

**Next.js (React) + Tailwind CSS (Graceful Degradation & Anti-Bot):**
Next.js is selected for client-side routing, which allows the frontend to intercept `503` errors and execute graceful degradation without forcing a full page reload. Furthermore, Next.js is selected to implement **Invisible Behavioral Biometrics**. It tracks mouse trajectories, keystroke dynamics, and time-on-page, sending a `client_signature` to the backend to detect and block automated bots without using intrusive Captchas. Tailwind CSS is chosen for styling because it purges unused CSS during the static build, ensuring fast loading on mobile networks.

**Custom Android SMS Gateway (External System Simulator):**
To maintain a zero-budget Phase 1, a custom Android application will be built using the native `SmsManager` API. It connects securely to the local infrastructure via Tailscale. When S6 publishes an OTP or booking confirmation, the app automatically sends the SMS using the host's SIM card. Strict rate limiting (max 5 SMS/minute) is enforced to prevent carrier throttling.

**Docker + Docker Compose (Memory Enforcement):**
Docker is selected to guarantee environment parity and to strictly enforce the 5.1 GB memory limit on the local laptop. The architecture mandates the use of the modern Docker Compose v2 syntax (`deploy.resources.limits.memory`) to cap each container. Furthermore, to prevent the Linux kernel from executing the Out-Of-Memory (OOM) killer:
*   **Java** containers must set `-XX:MaxRAMPercentage=75.0` and `-XX:+UseSerialGC` to strictly limit heap size and reduce Metaspace overhead.
*   **Node.js** containers must set `NODE_OPTIONS=--max-old-space-size=192` to prevent the V8 engine from expanding into the memory space reserved for the Prisma Rust binary. 

### 4.3 System Topology

The diagram below illustrates how the client applications, the API Gateway, the microservices, and the data layer interact.

```mermaid
flowchart TD
    %% Styling for high visibility on dark/light screens
    classDef client fill:#e1f5fe,stroke:#0288d1,stroke-width:2px,color:#000;
    classDef gateway fill:#fff3e0,stroke:#f57c00,stroke-width:2px,color:#000;
    classDef backend fill:#e8f5e9,stroke:#388e3c,stroke-width:2px,color:#000;
    classDef database fill:#fce4ec,stroke:#c2185b,stroke-width:2px,color:#000;
    classDef infra fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px,color:#000;
    classDef external fill:#e0e0e0,stroke:#616161,stroke-width:2px,color:#000;

    %% Clients
    Customer["Customer Website<br/>(Next.js)"]:::client --> |HTTPS| Nginx["Nginx API Gateway<br/>(Rate Limiting, SSL)"]:::gateway
    Employee["Employee Console<br/>(Next.js)"]:::client --> |HTTPS| Nginx
    Admin["Admin Dashboard<br/>(Grafana)"]:::client --> |Query| Prometheus["Prometheus<br/>(Metrics Scraper)"]:::infra

    %% Gateway to Services
    Nginx --> |"/auth/*"| S1["S1 IAM Service<br/>(Node.js)"]:::backend
    Nginx --> |"/master-data/*"| S2["S2 Master Data<br/>(Java)"]:::backend
    Nginx --> |"/booking/*"| S3["S3 Reservation<br/>(Java)"]:::backend
    Nginx --> |"/search/*"| S4["S4 Search BFF<br/>(Node.js)"]:::backend
    Nginx --> |"/payment/*"| S5["S5 Mock Payment<br/>(Node.js)"]:::backend

    %% Synchronous Service-to-Service Communication
    S4 --> |"Fetch Schedules/Fares"| S2
    S4 --> |"Check Availability"| S3
    S3 --> |"Request Fare Re-quote"| S2
    S3 --> |"Initiate Payment"| S5
    S5 -.-> |"Callback (Webhook)"| S3

    %% Asynchronous Events (Redis Streams)
    S3 -.-> |"Publish 8 Integration Events"| Redis[("Redis Streams<br/>& Cache")]:::database
    S2 -.-> |"Publish Config Updates"| Redis
    Redis -.-> |"Consume Events"| S6["S6 Notification<br/>(Node.js + Python Daemon)"]:::backend

    %% External SMS Gateway
    S6 -.-> |"Trigger SMS via Tailscale"| SMS["Custom Android SMS Gateway<br/>(Zero Budget)"]:::external

    %% Databases (Own Your Data)
    S1 --> DB_IAM[("PostgreSQL<br/>(IAM)")]:::database
    S2 --> DB_MD[("PostgreSQL<br/>(Master Data)")]:::database
    S3 --> DB_RES[("PostgreSQL<br/>(Reservation)")]:::database
    S6 --> DB_LOG[("PostgreSQL<br/>(Logs / JSONB)")]:::database
    
    %% Metrics Collection
    S1 -.-> |"Metrics"| Prometheus
    S2 -.-> |"Metrics"| Prometheus
    S3 -.-> |"Metrics"| Prometheus
    S4 -.-> |"Metrics"| Prometheus
    S5 -.-> |"Metrics"| Prometheus
    S6 -.-> |"Metrics"| Prometheus

    %% Infrastructure Security
    Tailscale["Tailscale VPN<br/>(Zero-Trust)"]:::infra -.-> |"Secure Admin Access"| DB_RES
    Tailscale -.-> |"Secure Admin Access"| Redis   
   ```

   ---

## 5. Consequences

- **Positive:** The chosen stack is highly optimised for the 5.1 GB RAM constraint on the local laptop. By eliminating MongoDB (saving ~500 MB of WiredTiger cache) and Apache Kafka (saving 2-4 GB of JVM overhead), the architecture ensures the 6 microservices and their PostgreSQL schemas can run stably alongside the host OS.
- **Positive:** The use of Docker with modern `deploy.resources.limits` and explicit JVM/V8 memory flags guarantees that the Linux kernel OOM (Out-Of-Memory) killer will not unexpectedly crash the services. This ensures deterministic resource enforcement.
- **Positive:** The Post-Payment Allocation model ensures that fast internet users do not hold seats hostage, while the Java-driven RAC/Waitlist/Refund cascade handles extreme race conditions gracefully without crashing the database.
- **Positive:** The Custom Android SMS Gateway provides a fully automated, zero-budget OTP and ticketing delivery mechanism for Phase 1, demonstrating a deep understanding of system integration and network security (via Tailscale).
- **Negative:** The Polyglot nature of the stack (Java, Node.js, Python) increases the cognitive load on the development team. Managing three distinct package managers and testing frameworks requires strict discipline.
- **Mitigation:** The use of contract-first OpenAPI ensures that the services can communicate seamlessly regardless of the language. Furthermore, the GitHub Actions CI/CD pipeline runs automated tests for all three languages on every commit, catching integration bugs early.

---

## 6. Approval

| Role           | Name        | Decision | Date       |
| -------------- | ----------- | -------- | ---------- |
| Lead Architect | Koushal Jha | Approved | 2026-10-17 |

---

## Revision History

| Version | Date       | Author      | Change           |
| ------- | ---------- | ----------- | ---------------- |
| 1.0     | 2026-10-17 | Koushal Jha | Initial release. |

---

## Appendix A: Not Applicable

Not applicable.

---

## Appendix B: Related Documents

### B.1 Directly Referenced Documents

| Seq  | Document ID                                                                                                    | Document Name                                     | Wave | Pri | Tag     |
| ---- | -------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- | ---- | --- | ------- |
| 0.1  | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)                     | Document Template Standard                        | 0    | P0  | UNBLOCK |
| 0.2  | [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)                  | Document ID and Category Scheme                   | 0    | P1  | UNBLOCK |
| 0.3  | [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md)               | Document Cross-Reference Standard                 | 0    | P1  | UNBLOCK |
| 0.4  | [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)                | Project Vision and Scope Document                 | 0    | P0  | UNBLOCK |
| 1.1  | [SRIS-P1-REQ-001](../wave-1-requirements/SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md)                        | Glossary and Domain Dictionary                    | 1    | P0  | UNBLOCK |
| 2.1  | [SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md)                                           | Microservices Identification                      | 2    | P0  | UNBLOCK |
| 2.2  | [SRIS-P1-ARCH-002](./SRIS-P1-ARCH-002_ArchitecturePrinciples.md)                                                | Architecture Principles                           | 2    | P0  | UNBLOCK |
| 2.3  | [SRIS-P1-ARCH-003](./SRIS-P1-ARCH-003_SystemArchitectureDocument.md)                                            | System Architecture Document                      | 2    | P0  | UNBLOCK |
| 2.11 | [SRIS-P1-ARCH-011](./SRIS-P1-ARCH-011_ErrorHandlingAndResilienceDesign.md)                                      | Error Handling and Resilience Design              | 2    | P1  | FOLLOW  |
| 2.14 | [SRIS-P1-ARCH-014](./SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md)                              | Distributed Concurrency and Locking Strategy      | 2    | P0  | UNBLOCK |
| 2.15 | [SRIS-P1-ARCH-015](./SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md)                            | Distributed Transaction and Saga Pattern Design   | 2    | P0  | UNBLOCK |
| 3.14 | [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md)                                               | API Contract Document (OpenAPI)                   | 3    | P0  | UNBLOCK |
| 3.3  | [SRIS-P1-DATA-003](./SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)                                         | Physical Database Schema Document                 | 3    | P0  | UNBLOCK |
| 5.3  | [SRIS-P1-INF-003](../wave-5-devops-operations/SRIS-P1-INF-003_CICDPipelineDesign.md)                            | CI/CD Pipeline Design                             | 5    | P0  | UNBLOCK |

### B.2 Documents That Reference This Document

| Seq  | Document ID                                                                             | Document Name                                | Why It References                                                                 |
| ---- | --------------------------------------------------------------------------------------- | -------------------------------------------- | --------------------------------------------------------------------------------- |
| 2.3  | [SRIS-P1-ARCH-003](./SRIS-P1-ARCH-003_SystemArchitectureDocument.md)                        | System Architecture Document                 | Uses the technology choices to build the component diagrams                      |
| 2.9  | [SRIS-P1-ARCH-009](./SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md)          | Service Interaction and Communication Design | Defines the exact API contracts for the chosen Node.js/Java stack                 |
| 2.14 | [SRIS-P1-ARCH-014](./SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md)          | Distributed Concurrency and Locking Strategy | Configures the PostgreSQL and Redis locking mechanisms based on this stack        |
| 3.2  | [SRIS-P1-DATA-002](./SRIS-P1-DATA-002_LogicalDataModelPerService.md)                        | Logical Data Model (per service)             | Implements the schemas for PostgreSQL and JSONB                                   |
| 6.2  | [SRIS-P1-DEV-004](../wave-6-developer-standards/SRIS-P1-DEV-004_CodingStandardsAndConventions.md) | Coding Standards and Conventions             | Enforces the coding styles for Java, Node.js, and Python                          |

### B.3 Documents This Document Depends On (Upstream)

| Seq | Document ID                                                                                 | Document Name                          | Dependency Type |
| --- | ------------------------------------------------------------------------------------------- | -------------------------------------- | --------------- |
| 0.1 | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)           | Document Template Standard             | Hard            |
| 2.1 | [SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md)                                 | Microservices Identification           | Hard            |
| 2.2 | [SRIS-P1-ARCH-002](./SRIS-P1-ARCH-002_ArchitecturePrinciples.md)                                      | Architecture Principles                | Hard            |
| 0.4 | [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)      | Project Vision and Scope Document      | Hard            |

### B.4 Documents This Document Unblocks (Downstream)

| Seq  | Document ID                                                                             | Document Name                                | Blocked Until |
| ---- | --------------------------------------------------------------------------------------- | -------------------------------------------- | ------------- |
| 2.3  | [SRIS-P1-ARCH-003](./SRIS-P1-ARCH-003_SystemArchitectureDocument.md)                        | System Architecture Document                 | This approved |
| 2.4  | [SRIS-P1-ARCH-004](./SRIS-P1-ARCH-004_BoundedContextMap.md)                                 | Bounded Context Map                          | This approved |
| 2.9  | [SRIS-P1-ARCH-009](./SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md)          | Service Interaction and Communication Design | This approved |
| 2.12 | [SRIS-P1-ARCH-012](./SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)           | Observability and Monitoring Design          | This approved |
| 3.1  | [SRIS-P1-DATA-001](./SRIS-P1-DATA-001_DataDesignDocument.md)                                | Data Design Document                         | This approved |
| 5.1  | [SRIS-P1-INF-001](../wave-5-devops-operations/SRIS-P1-INF-001_InfrastructureAndTechnologyDocument.md) | Infrastructure and Technology Document       | This approved |

### B.5 Master Documentation Index

The complete list of Phase 1 documents is in [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

### B.6 External Reference Documents

| Reference Type | Where It Is Documented                                                                                                                                                                                                                                     |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Website        | Spring Boot Documentation. https://spring.io/projects/spring-boot. Referenced for the Java runtime and transaction management.                                                                                                                           |
| Website        | Next.js Documentation. https://nextjs.org/docs. Referenced for the React framework and static export configuration.                                                                                                                                      |
| Website        | Redis Documentation. https://redis.io/documentation. Referenced for the Streams messaging and caching mechanisms.                                                                                                                                        |
| Website        | Tailscale Documentation. https://tailscale.com/kb. Referenced for Zero-Trust VPN configuration.                                                                                                                                                          |

### B.7 Document Conventions

The conventions for Priority and Tag values are defined in [Section 9](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md#9-vocabulary-standards) of [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.