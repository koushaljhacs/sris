<div align="center">

![Wave](https://img.shields.io/badge/Wave-2-0550AE?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-ARCH-6e7781?style=for-the-badge)

</div>

# Service Registry and Catalog

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** 1.0 | **Date:** 2026-10-21 | **Document ID:** SRIS-P1-ARCH-016

| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| Title              | Service Registry and Catalog                                      |
| Software           | SRIS                                                              |
| Software Full Form | Sarathi Railway Information System                                |
| Team Codename      | Project Sarathi                                                   |
| Document ID        | SRIS-P1-ARCH-016                                                  |
| Task               | Define the static catalog of services, ports, and dependencies    |
| Document Type      | Architecture Document                                             |
| Milestone          | Phase 1 Foundation                                                |
| Classification     | Internal                                                          |
| Version            | 1.0                                                               |
| Date               | 2026-10-21                                                        |
| Author             | Koushal Jha, Lead Architect                                       |
| Approved By        | Koushal Jha, Lead Architect                                       |
| Approval Date      | 2026-10-21                                                        |
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
2. [Catalog Structure and Authority](#2-catalog-structure-and-authority)
   - [2.1 What the Catalog Owns and What It Defers](#21-what-the-catalog-owns-and-what-it-defers)
   - [2.2 Field Definitions](#22-field-definitions)
   - [2.3 How Conflicts With Other Documents Are Resolved](#23-how-conflicts-with-other-documents-are-resolved)
3. [The Service Catalog](#3-the-service-catalog)
   - [3.1 Service Catalog](#31-service-catalog)
   - [3.2 Bounded Context Map](#32-bounded-context-map)
4. [Service Discovery](#4-service-discovery)
   - [4.1 Docker Internal DNS](#41-docker-internal-dns)
   - [4.2 Configuration Sourcing for Ports and Hosts](#42-configuration-sourcing-for-ports-and-hosts)
5. [Startup Dependency Order](#5-startup-dependency-order)
   - [5.1 The Health Gate Rule](#51-the-health-gate-rule)
   - [5.2 The Startup Sequence](#52-the-startup-sequence)
6. [The Service Dependency Diagram](#6-the-service-dependency-diagram)
7. [Contract Ownership and References](#7-contract-ownership-and-references)
8. [Catalog Maintenance](#8-catalog-maintenance)
   - [8.1 Port or Path Change Procedure](#81-port-or-path-change-procedure)
   - [8.2 When a Service Is Added or Removed](#82-when-a-service-is-added-or-removed)
9. [Approval](#9-approval)

- [Revision History](#revision-history)
- [Appendix A: External Systems](#appendix-a-external-systems)
- [Appendix B: Related Documents](#appendix-b-related-documents)

---

## 1. Introduction

### 1.1 Purpose

This document is the definitive Service Registry and Catalog for Phase 1 of SRIS. It provides a single, static, authoritative reference for every operational detail a Week 3 developer needs: which services exist, what ports they expose, what base paths Nginx routes to them, which health and metrics endpoints they publish, and the exact order in which they must start.

It also serves as the operational contract for the Deployment Architecture ([SRIS-P1-ARCH-013](./SRIS-P1-ARCH-013_DeploymentArchitectureDocument.md) — Deployment Architecture Document) and the Environment Variables Reference ([SRIS-P1-INF-011](../wave-5-devops-operations/SRIS-P1-INF-011_EnvironmentVariablesAndConfigurationReference.md) — Environment Variables and Configuration Reference).

### 1.2 Scope

**In scope**

- The static 6-row Service Catalog (one row per service) containing ports, base paths, health endpoints, and metrics paths.
- The 8-row Bounded Context Map (one row per context) summarising the DDD classification from [SRIS-P1-ARCH-004](./SRIS-P1-ARCH-004_BoundedContextMap.md) — Bounded Context Map.
- Service discovery via Docker internal DNS.
- The strict startup dependency order, governed by health checks.
- The runtime call graph showing which service talks to which.
- The contract ownership references (which document owns which interface).
- The catalog maintenance procedure for port changes or service additions.

**Out of scope**

- The technology stack choice (languages, frameworks, databases), which belongs to [SRIS-P1-ARCH-008](./SRIS-P1-ARCH-008_TechnologyStackADR.md) — Technology Stack ADR.
- The physical deployment topology and Docker Compose files, which belong to [SRIS-P1-ARCH-013](./SRIS-P1-ARCH-013_DeploymentArchitectureDocument.md) — Deployment Architecture Document.
- The detailed API contracts, which belong to [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md) — API Contract Document (OpenAPI) and [SRIS-P1-API-003](./SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md) — Event Schema Document (AsyncAPI).
- The full environment variable list, which belongs to [SRIS-P1-INF-011](../wave-5-devops-operations/SRIS-P1-INF-011_EnvironmentVariablesAndConfigurationReference.md) — Environment Variables and Configuration Reference.
- Capacity planning or memory headroom beyond the Phase 1 5.1 GB ceiling, which belongs to [SRIS-P1-INF-010](../wave-5-devops-operations/SRIS-P1-INF-010_CapacityPlanningDocument.md) — Capacity Planning Document.

### 1.3 Audience

- **Backend and Frontend developers:** use the catalog to configure their local Docker environment, routing, and API calls.
- **DevOps engineer:** uses the port assignments and startup order to write the Docker Compose files.
- **QA engineers:** use the health and metrics paths to set up monitoring and integration tests.
- **Project supervisor and evaluator:** verifies that the service topology is fully documented and conflict-free.

### 1.4 Terminology and Conventions

Every term in this document has the meaning recorded in [SRIS-P1-REQ-001](../wave-1-requirements/SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary. The terms below carry the most weight in this document.

| Term | Meaning |
| :--- | :--- |
| Service Catalog | The operational table listing every running process, its port, its base path, and its dependencies. |
| Bounded Context | A boundary within which a domain model and its vocabulary are consistent. |
| Liveness Check | A health endpoint confirming the process is alive (used by Load Balancer / Docker). |
| Docker DNS | The internal mechanism that allows containers to resolve each other by name. |
| CQRS | Command Query Responsibility Segregation (write to DB0, read from DB1). |

This document follows the standards below.

- [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.
- [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md) — Document ID and Category Scheme.
- [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md) — Document Cross-Reference Standard.

---

## 2. Catalog Structure and Authority

### 2.1 What the Catalog Owns and What It Defers

To prevent conflict and drift, this document operates under the **Single-Owner-Per-Field** rule.

| Field | Owner |
| :--- | :--- |
| Container port, host port, base path, health endpoint, metrics path | **ARCH-016 (This Document)** |
| Language, runtime, framework, ORM, database engine | [SRIS-P1-ARCH-008](./SRIS-P1-ARCH-008_TechnologyStackADR.md) — Technology Stack ADR |
| Bounded context classification (Core/Supporting/Generic) | [SRIS-P1-ARCH-004](./SRIS-P1-ARCH-004_BoundedContextMap.md) — Bounded Context Map |
| Environment variable values (DATABASE_URL, etc.) | [SRIS-P1-INF-011](../wave-5-devops-operations/SRIS-P1-INF-011_EnvironmentVariablesAndConfigurationReference.md) — Environment Variables and Configuration Reference |

### 2.2 Field Definitions

| Field | Definition |
| :--- | :--- |
| Service ID | The identifier (S1 to S6) assigned in ARCH-001. |
| Language | The runtime (Node.js or Java). |
| Container Port | The internal port the service listens on inside the Docker network. |
| Host Port | The port mapped to the host machine (can vary per environment, defined in INF-011). |
| Base Path | The Nginx routing prefix (e.g., `/booking/*`). |
| Health Liveness | The path Nginx and Docker use to check if the process is alive. |
| Health Detailed | The path Prometheus uses to scrape circuit-breaker and dependency states. |
| Metrics | The path Prometheus uses to scrape performance metrics. |
| Contract | The Document ID that owns the OpenAPI/AsyncAPI schema. |
| Category | The DDD classification (from ARCH-004). |
| Depends On | The services required for this service to function. |

### 2.3 How Conflicts With Other Documents Are Resolved

- **Port and Path Conflicts:** If ARCH-008 or any other document specifies a different port or path, **ARCH-016 wins**. This document is the operational truth for Week 3.
- **Technology Conflicts:** If this document accidentally lists a different language or database than ARCH-008, **ARCH-008 wins**. This document must be amended to match.
- **DDD Classification Conflicts:** If this document and ARCH-004 disagree on context naming, **ARCH-004 wins**.

---

## 3. The Service Catalog

### 3.1 Service Catalog

The table below is the authoritative operational record for all running processes in the Phase 1 environment. A dash (—) indicates the field does not apply to that process.

| ID | Service | Language | Container Port | Host Port | Base Path | Health Liveness | Health Detailed | Metrics | Contract | Category | Depends On |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| S1 | IAM Service | Node.js | 3001 | 3001 | `/auth/*` | `/health/liveness` | `/health` | `/metrics` | [API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md) | Generic | PostgreSQL (sris_iam) |
| S2 | Master Data & Pricing | Java | 8081 | 8081 | `/master-data/*` | `/health/liveness` | `/health` | `/actuator/prometheus` | [API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md) | Supporting | PostgreSQL (sris_master_data), S1 (Token) |
| S3 | Reservation | Java | 8082 | 8082 | `/booking/*` | `/health/liveness` | `/health` | `/actuator/prometheus` | [API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md) | Core | PostgreSQL (sris_reservation), S1, S2, S5, Redis |
| S4 | Search BFF | Node.js | 3004 | 3004 | `/search/*` | `/health/liveness` | `/health` | `/metrics` | [API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md) | Supporting | S1, S2, Redis DB1 (CQRS) |
| S5 | Mock Payment | Node.js | 3005 | 3005 | `/payment/*` | `/health/liveness` | `/health` | `/metrics` | [API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md) | External Simulator | PostgreSQL (sris_payment), S1 |
| S6 | Notification (+ Python Daemon) | Node.js | 3006 | 3006 | — | `/health/liveness` | `/health` | `/metrics` | [API-003](./SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md) | Generic | Redis DB0 (Streams), PostgreSQL (sris_notification) |
| — | Nginx | — | 80 | 8080 | — | — | — | /metrics (Phase 2) | — | — | S1, S2, S3, S4, S5 (upstreams) |
| — | PostgreSQL | — | 5432 | 5432 | — | — | — | — | — | — | — |
| — | Redis | — | 6379 | 6379 | — | — | — | — | — | — | — |
| — | Prometheus | — | 9090 | 9090 | — | — | — | — | — | — | — |
| — | Grafana | — | 3000 | 3000 | — | — | — | — | — | — | — |
| — | Loki | — | 3100 | 3100 | — | — | — | — | — | — | — |
| — | Promtail | — | 9080 | 9080 | — | — | — | — | — | — | — |

**Note on S6:** S6 is an event-driven consumer. It does not expose an inbound HTTP base path. Its health and metrics endpoints are still required for Docker and Prometheus to monitor the process.

**Note on S4 ↔ S3:** Per the approved architecture ([SRIS-P1-ARCH-004](./SRIS-P1-ARCH-004_BoundedContextMap.md) — Bounded Context Map), S4 does not make synchronous calls to S3. It depends on S2 (sync) and Redis DB1 (CQRS materialized view). This supersedes the synchronous edge shown in ARCH-001 §6.4.

**Note on Redis DB0/DB1:** The single Redis container hosts DB0 (S3 internal hot counters) and DB1 (S4 CQRS materialized view).

**Note on Nginx Metrics:** In Phase 1, Nginx does not expose a native Prometheus metrics endpoint. Passive health checks (`max_fails`, `fail_timeout`) are configured per the Error Handling and Resilience Design ([SRIS-P1-ARCH-011](./SRIS-P1-ARCH-011_ErrorHandlingAndResilienceDesign.md) — Error Handling and Resilience Design). In Phase 2, the `nginx-prometheus-exporter` sidecar will expose Nginx metrics on `/metrics` for Prometheus to scrape.

**Note on S6 Python Daemon:** The S6 container includes the embedded Python automation daemon (the SRIS Autonomous Operations Engine). This daemon monitors CPU/RAM and detects anomaly patterns per the Technology Stack ADR ([SRIS-P1-ARCH-008](./SRIS-P1-ARCH-008_TechnologyStackADR.md) — Technology Stack ADR). When configuring the Docker Compose memory limit for S6, the combined limit must account for both the Node.js runtime and the Python daemon.

### 3.2 Bounded Context Map

The table below summarises the 8 bounded contexts and their owning services, as defined in [SRIS-P1-ARCH-004](./SRIS-P1-ARCH-004_BoundedContextMap.md) — Bounded Context Map. This table is for quick reference only; ARCH-004 remains the authoritative source for DDD classification.

| Context | Category | Owning Service | Responsibility |
| :--- | :--- | :--- | :--- |
| Identity and Access | Generic | S1 | Authenticate and authorize users. |
| Railway Master Data | Supporting | S2 | Stations, routes, trains, schedules. |
| Fare and Pricing | Supporting | S2 | Tariff rules, concessions, fare quotes. |
| Inventory and Quota | Core | S3 (Inventory module) | Seat matrix, availability, allocation. |
| Booking and Ticketing | Core | S3 (Booking module) | Booking lifecycle, PNR, waitlist. |
| Payment | External Simulator | S3 (domain) + S5 (simulator) | Payment processing and callback. |
| Search and Discovery | Supporting | S4 | Unified search composition. |
| Notification | Generic | S6 | Email, SMS, event consumer. |

---

## 4. Service Discovery

### 4.1 Docker Internal DNS

Within the Docker Compose network, services resolve each other by their **container name** (e.g., `http://s2-master-data:8081`). There are no hardcoded IP addresses, no `/etc/hosts` entries, and no runtime service registries.

This mechanism satisfies [SRIS-P1-REQ-005](../wave-1-requirements/SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md) — Non-Functional Requirements (ISO 25010) NFR-070 ("no hardcoded hostnames or ports").

### 4.2 Configuration Sourcing for Ports and Hosts

While the container ports are fixed in this catalog, the **host ports** (the ports exposed to the developer's laptop) can be overridden via the `.env` file. The exact environment variables are owned by [SRIS-P1-INF-011](../wave-5-devops-operations/SRIS-P1-INF-011_EnvironmentVariablesAndConfigurationReference.md) — Environment Variables and Configuration Reference.

---

## 5. Startup Dependency Order

### 5.1 The Health Gate Rule

A service is considered "ready" only when its `/health/liveness` endpoint returns a `200 OK`. Docker Compose's `depends_on` directive with `condition: service_healthy` enforces this rule. A service that fails its liveness check will block the startup of its dependents, preventing partial-boot chaos.

### 5.2 The Startup Sequence

The services must start in the following order:

1. **Data Layer:** PostgreSQL, Redis
2. **Foundation Services:** S1 IAM, S2 Master Data (can start in parallel), S5 Mock Payment
3. **Core Transactional:** S3 Reservation (depends on S1, S2, S5, PostgreSQL, Redis)
4. **Read Layer:** S4 Search BFF (depends on S1, S2, Redis DB1)
5. **Notification:** S6 Notification (depends on Redis DB0)
6. **Edge Gateway:** Nginx (depends on S1, S2, S3, S4, S5)
7. **Observability:** Prometheus, Grafana, Loki, Promtail (do not block services)

**Mermaid diagram showing the exact startup dependency order (top-to-bottom).**

```mermaid
%%{init: {
  "flowchart": {
    "nodeSpacing": 60,
    "rankSpacing": 80,
    "padding": 20,
    "curve": "basis",
    "htmlLabels": true
  },
  "themeVariables": {
    "fontSize": "14px",
    "fontFamily": "Segoe UI, Arial, sans-serif"
  }
}}%%
flowchart TD
    classDef data fill:#FCE4EC,stroke:#C2185B,stroke-width:2px,color:#000;
    classDef service fill:#E8F5E9,stroke:#388E3C,stroke-width:2px,color:#000;
    classDef gateway fill:#FFF3E0,stroke:#F57C00,stroke-width:2px,color:#000;
    classDef obs fill:#F3E5F5,stroke:#7B1FA2,stroke-width:2px,color:#000;

    subgraph DataLayer ["1. Data Layer"]
        PG[("PostgreSQL")]:::data
        Redis[("Redis DB0 & DB1")]:::data
    end

    subgraph Foundation ["2. Foundation Services"]
        S1["S1 IAM (Node)"]:::service
        S2["S2 Master Data (Java)"]:::service
        S5["S5 Mock Payment (Node)"]:::service
    end

    subgraph Core ["3. Core Transactional"]
        S3["S3 Reservation (Java)"]:::service
    end

    subgraph Read ["4. Read Layer"]
        S4["S4 Search BFF (Node)"]:::service
    end

    subgraph Notify ["5. Notification"]
        S6["S6 Notification (Node)"]:::service
    end

    subgraph Edge ["6. Edge Gateway"]
        Nginx["Nginx Gateway"]:::gateway
    end

    subgraph Obs ["7. Observability (Non-blocking)"]
        Prom["Prometheus"]:::obs
        Graf["Grafana"]:::obs
        Loki["Loki / Promtail"]:::obs
    end

    %% Startup Order
    PG --> S1
    PG --> S2
    PG --> S5
    Redis --> S6
    
    S1 --> S3
    S2 --> S3
    S5 --> S3
    
    S1 --> S4
    S2 --> S4
    Redis --> S4
    
    S1 --> Nginx
    S2 --> Nginx
    S3 --> Nginx
    S4 --> Nginx
    S5 --> Nginx
    
    PG -.-> Prom
    Redis -.-> Prom
    S1 -.-> Prom
    S2 -.-> Prom
    S3 -.-> Prom
    S4 -.-> Prom
    S5 -.-> Prom
    S6 -.-> Prom
```

---

## 6. The Service Dependency Diagram

While Section 5 showed the startup order, this diagram shows the **runtime call graph**. It answers the question: *"When a request is processed, which service talks to which service?"*

**Critical Note:** S4 (Search BFF) does **not** make synchronous calls to S3 (Reservation) at runtime. Per [SRIS-P1-ARCH-004](./SRIS-P1-ARCH-004_BoundedContextMap.md) — Bounded Context Map §5.5, S4 depends on S2 (sync) and Redis DB1 (CQRS materialized view). S6 consumes events from Redis DB0. S3 publishes events to Redis DB0 via the Transactional Outbox.

```mermaid
%%{init: {
  "flowchart": {
    "nodeSpacing": 60,
    "rankSpacing": 80,
    "padding": 20,
    "curve": "basis",
    "htmlLabels": true
  },
  "themeVariables": {
    "fontSize": "14px",
    "fontFamily": "Segoe UI, Arial, sans-serif"
  }
}}%%
flowchart TD
    classDef client fill:#E1F5FE,stroke:#0288D1,stroke-width:2px,color:#000;
    classDef gateway fill:#FFF3E0,stroke:#F57C00,stroke-width:2px,color:#000;
    classDef service fill:#E8F5E9,stroke:#388E3C,stroke-width:2px,color:#000;
    classDef db fill:#FCE4EC,stroke:#C2185B,stroke-width:2px,color:#000;
    classDef stream fill:#F3E5F5,stroke:#7B1FA2,stroke-width:2px,color:#000;

    Frontend["Next.js Frontend"]:::client
    Nginx["Nginx Gateway"]:::gateway

    S1["S1 IAM"]:::service
    S2["S2 Master Data"]:::service
    S3["S3 Reservation"]:::service
    S4["S4 Search BFF"]:::service
    S5["S5 Mock Payment"]:::service
    S6["S6 Notification"]:::service

    PG[("PostgreSQL")]:::db
    RedisDB0[("Redis DB0<br/>S3 Hot Counters & Streams")]:::stream
    RedisDB1[("Redis DB1<br/>S4 CQRS Read Model")]:::stream

    Frontend --> Nginx
    Nginx --> S1
    Nginx --> S2
    Nginx --> S3
    Nginx --> S4
    Nginx --> S5

    S1 --> PG
    S2 --> PG
    S3 --> PG
    S6 --> PG

    S4 --> S2
    S3 --> S2
    S3 --> S5
    S5 -.-> S3

    S3 --> RedisDB0
    RedisDB0 -.-> S6
    RedisDB0 -.-> S4
    S4 --> RedisDB1
```

---

## 7. Contract Ownership and References

Every service interface is owned by a specific Wave 3 document. This table ensures developers know exactly where to find the schema.

| Service | Contract Type | Owning Document |
| :--- | :--- | :--- |
| S1 IAM | REST (OpenAPI) | [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md) — API Contract Document (OpenAPI) |
| S2 Master Data | REST (OpenAPI) | [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md) |
| S3 Reservation | REST (OpenAPI) | [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md) |
| S4 Search BFF | REST (OpenAPI) | [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md) |
| S5 Mock Payment | REST (OpenAPI) | [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md) |
| S6 Notification | Async (AsyncAPI) | [SRIS-P1-API-003](./SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md) — Event Schema Document (AsyncAPI) |
| Booking Events | Async (AsyncAPI) | [SRIS-P1-API-003](./SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md) |
| Payment Events | Async (AsyncAPI) | [SRIS-P1-API-003](./SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md) |

---

## 8. Catalog Maintenance

This catalog is normative for Week 3 developers, but it must remain agile. The following procedures apply.

### 8.1 Port or Path Change Procedure

If a service port or base path needs to change during Phase 1:

1. The Lead Architect amends this document (ARCH-016) with a new Revision History row and bumps the minor version (e.g., v1.0 to v1.1).
2. The DevOps engineer updates the `docker-compose.yml` and `.env` files.
3. The Nginx configuration (`nginx.conf`) is updated to match the new base path.
4. The affected service's health check and metrics scrape targets are updated in Prometheus.
5. The change is communicated to the team via the standard channel.

### 8.2 When a Service Is Added or Removed

If a new service is introduced in a later phase (Phase 2 or Phase 3):

1. The Lead Architect must first issue an amendment to [SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification to justify the new boundary and update the 6-service count.
2. This catalog (ARCH-016) is amended to include the new row, port assignment, and base path.
3. The Deployment Architecture ([SRIS-P1-ARCH-013](./SRIS-P1-ARCH-013_DeploymentArchitectureDocument.md) — Deployment Architecture Document) is amended to add the new container.
4. The Environment Variables Reference ([SRIS-P1-INF-011](../wave-5-devops-operations/SRIS-P1-INF-011_EnvironmentVariablesAndConfigurationReference.md) — Environment Variables and Configuration Reference) is amended to add the new service's required environment variables.

No service may be added to the running environment without completing all four steps.

---

## 9. Approval

| Role           | Name        | Decision | Date       |
| -------------- | ----------- | -------- | ---------- |
| Lead Architect | Koushal Jha | Approved | 2026-10-21 |

---

## Revision History

| Version | Date       | Author      | Change           |
| ------- | ---------- | ----------- | ---------------- |
| 1.0     | 2026-10-21 | Koushal Jha | Initial release. |

---

## Appendix A: External Systems

The following systems are outside the Docker Compose network but are part of the Phase 1 environment. They are not microservices and do not have container ports or Nginx base paths.

| System | Protocol | Calling Service | Purpose |
| :--- | :--- | :--- | :--- |
| Android SMS Gateway | HTTPS (via Tailscale) | S6 Notification | Dispatch SMS to customers. |
| Tailscale VPN | WireGuard | — | Zero-Trust administrative access to the host. |

These are documented here so that a Week 3 developer understands what S6 calls when it sends an SMS, but they are not part of the Docker Compose network.

---

## Appendix B: Related Documents

### B.1 Directly Referenced Documents

| Seq  | Document ID                                                                                                    | Document Name                                     | Wave | Pri | Tag     |
| ---- | -------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- | ---- | --- | ------- |
| 0.1  | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)                     | Document Template Standard                        | 0    | P0  | UNBLOCK |
| 0.2  | [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)                  | Document ID and Category Scheme                   | 0    | P1  | UNBLOCK |
| 0.3  | [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md)               | Document Cross-Reference Standard                 | 0    | P1  | UNBLOCK |
| 1.1  | [SRIS-P1-REQ-001](../wave-1-requirements/SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md)                        | Glossary and Domain Dictionary                    | 1    | P0  | UNBLOCK |
| 1.5  | [SRIS-P1-REQ-005](../wave-1-requirements/SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md)                   | Non-Functional Requirements (ISO 25010)           | 1    | P0  | UNBLOCK |
| 2.1  | [SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md)                                           | Microservices Identification                      | 2    | P0  | UNBLOCK |
| 2.4  | [SRIS-P1-ARCH-004](./SRIS-P1-ARCH-004_BoundedContextMap.md)                                                     | Bounded Context Map                               | 2    | P0  | UNBLOCK |
| 2.8  | [SRIS-P1-ARCH-008](./SRIS-P1-ARCH-008_TechnologyStackADR.md)                                                    | Technology Stack ADR                              | 2    | P0  | UNBLOCK |
| 2.11 | [SRIS-P1-ARCH-011](./SRIS-P1-ARCH-011_ErrorHandlingAndResilienceDesign.md)                                      | Error Handling and Resilience Design              | 2    | P1  | FOLLOW  |
| 2.13 | [SRIS-P1-ARCH-013](./SRIS-P1-ARCH-013_DeploymentArchitectureDocument.md)                                        | Deployment Architecture Document                  | 2    | P1  | FOLLOW  |
| 3.14 | [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md)                                              | API Contract Document (OpenAPI)                   | 3    | P0  | UNBLOCK |
| 3.16 | [SRIS-P1-API-003](./SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md)                                             | Event Schema Document (AsyncAPI)                  | 3    | P0  | UNBLOCK |
| 5.10 | [SRIS-P1-INF-010](../wave-5-devops-operations/SRIS-P1-INF-010_CapacityPlanningDocument.md)                       | Capacity Planning Document                        | 5    | P2  | FOLLOW  |
| 5.11 | [SRIS-P1-INF-011](../wave-5-devops-operations/SRIS-P1-INF-011_EnvironmentVariablesAndConfigurationReference.md)  | Environment Variables and Configuration Reference | 5    | P0  | UNBLOCK |

### B.2 Documents That Reference This Document

| Seq  | Document ID                                                                             | Document Name                                | Why It References                                                                 |
| ---- | --------------------------------------------------------------------------------------- | -------------------------------------------- | --------------------------------------------------------------------------------- |
| 2.13 | [SRIS-P1-ARCH-013](./SRIS-P1-ARCH-013_DeploymentArchitectureDocument.md)                    | Deployment Architecture Document             | Uses the port assignments and startup order to build Compose files                |
| 5.11 | [SRIS-P1-INF-011](../wave-5-devops-operations/SRIS-P1-INF-011_EnvironmentVariablesAndConfigurationReference.md) | Environment Variables and Configuration Reference | Uses the catalog to define PORT and SERVICE_NAME variables per service       |
| 3.14 | [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md)                          | API Contract Document (OpenAPI)              | Uses the base paths to define endpoint URLs                                       |
| 3.16 | [SRIS-P1-API-003](./SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md)                         | Event Schema Document (AsyncAPI)             | Uses the S6 catalog entry to define async contracts                               |

### B.3 Documents This Document Depends On (Upstream)

| Seq | Document ID                                                                                 | Document Name                          | Dependency Type |
| --- | ------------------------------------------------------------------------------------------- | -------------------------------------- | --------------- |
| 0.1 | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)           | Document Template Standard             | Hard            |
| 2.1 | [SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md)                                 | Microservices Identification           | Hard            |
| 2.4 | [SRIS-P1-ARCH-004](./SRIS-P1-ARCH-004_BoundedContextMap.md)                                           | Bounded Context Map                    | Hard            |
| 2.8 | [SRIS-P1-ARCH-008](./SRIS-P1-ARCH-008_TechnologyStackADR.md)                                          | Technology Stack ADR                   | Hard            |
| 2.11 | [SRIS-P1-ARCH-011](./SRIS-P1-ARCH-011_ErrorHandlingAndResilienceDesign.md)                            | Error Handling and Resilience Design   | Soft            |
| 1.5 | [SRIS-P1-REQ-005](../wave-1-requirements/SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md)          | Non-Functional Requirements (ISO 25010) | Soft           |

### B.4 Documents This Document Unblocks (Downstream)

| Seq  | Document ID                                                                             | Document Name                                | Blocked Until |
| ---- | --------------------------------------------------------------------------------------- | -------------------------------------------- | ------------- |
| 2.13 | [SRIS-P1-ARCH-013](./SRIS-P1-ARCH-013_DeploymentArchitectureDocument.md)                    | Deployment Architecture Document             | This approved |
| 5.11 | [SRIS-P1-INF-011](../wave-5-devops-operations/SRIS-P1-INF-011_EnvironmentVariablesAndConfigurationReference.md) | Environment Variables and Configuration Reference | This approved |
| 3.14 | [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md)                          | API Contract Document (OpenAPI)              | This approved |
| 3.16 | [SRIS-P1-API-003](./SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md)                         | Event Schema Document (AsyncAPI)             | This approved |

### B.5 Master Documentation Index

The complete list of Phase 1 documents is in [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

### B.6 External Reference Documents

| Reference Type | Where It Is Documented                                                                                                                                                                                                                                     |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Website        | Docker Documentation — Networking. https://docs.docker.com/network/. Referenced for the internal DNS resolution mechanism between containers.                                                                                                            |
| Website        | Docker Documentation — Compose depends_on. https://docs.docker.com/compose/compose-file/05-services/#depends_on. Referenced for the health-gated startup order.                                                                                           |

### B.7 Document Conventions

The conventions for Priority and Tag values are defined in [Section 9](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md#9-vocabulary-standards) of [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.