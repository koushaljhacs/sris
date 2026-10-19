<div align="center">

![Wave](https://img.shields.io/badge/Wave-2-0550AE?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-ARCH-6e7781?style=for-the-badge)

</div>

# System Architecture Document

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** 1.0 | **Date:** 2026-10-19 | **Document ID:** SRIS-P1-ARCH-003

| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| Title              | System Architecture Document                                      |
| Software           | SRIS                                                              |
| Software Full Form | Sarathi Railway Information System                                |
| Team Codename      | Project Sarathi                                                   |
| Document ID        | SRIS-P1-ARCH-003                                                  |
| Task               | Define the physical and structural architecture of Phase 1        |
| Document Type      | Architecture Document                                             |
| Milestone          | Phase 1 Foundation                                                |
| Classification     | Internal                                                          |
| Version            | 1.0                                                               |
| Date               | 2026-10-19                                                        |
| Author             | Koushal Jha, Lead Architect                                       |
| Approved By        | Koushal Jha, Lead Architect                                       |
| Approval Date      | 2026-10-19                                                        |
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
2. [Architectural Vision and Locked Decisions](#2-architectural-vision-and-locked-decisions)
   - [2.1 Modular 3-Tier Code Structure](#21-modular-3-tier-code-structure)
   - [2.2 Service Discovery and Developer Workflow](#22-service-discovery-and-developer-workflow)
   - [2.3 Database Architecture and Isolation](#23-database-architecture-and-isolation)
   - [2.4 Edge Security and Observability](#24-edge-security-and-observability)
3. [System Context (C4 Level 1)](#3-system-context-c4-level-1)
4. [Container Architecture (C4 Level 2)](#4-container-architecture-c4-level-2)
5. [Component Architecture (C4 Level 3)](#5-component-architecture-c4-level-3)
6. [Deployment Topology and Resource Envelope](#6-deployment-topology-and-resource-envelope)
7. [Core Sequence Flows](#7-core-sequence-flows)
8. [Approval](#8-approval)

- [Revision History](#revision-history)
- [Appendix A: Not Applicable](#appendix-a-not-applicable)
- [Appendix B: Related Documents](#appendix-b-related-documents)

---

## 1. Introduction

### 1.1 Purpose

This document records the System Architecture of Phase 1 of SRIS. It serves as the physical blueprint for the software, bridging the gap between the conceptual domain model ([SRIS-P1-ARCH-005](./SRIS-P1-ARCH-005_DomainModelDocument.md) — Domain Model Document), the service boundaries ([SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification), and the technology stack ([SRIS-P1-ARCH-008](./SRIS-P1-ARCH-008_TechnologyStackADR.md) — Technology Stack ADR).

It dictates exactly how the 6 microservices are structured internally, how they communicate across the network, and how they are physically deployed within a strict 5.1 GB RAM envelope. It is written so that a new developer joining in Phase 2 can understand the entire structural and behavioural flow of the system without needing to reverse-engineer the code.

### 1.2 Scope

**In scope**

- The internal code structure and directory naming conventions for Java and Node.js services.
- The service discovery and internal routing mechanisms.
- The database isolation strategy and concurrency controls.
- The C4 Model diagrams (Context, Container, Component, and Deployment).
- The core behavioural Sequence Diagrams (Authentication and Post-Payment Allocation).
- The provisional memory allocation envelope for Docker containers.

**Out of scope**

- The detailed API contracts, which belong to [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md) — API Contract Document (OpenAPI).
- The physical database schemas and entity-relationship diagrams, which belong to [SRIS-P1-DATA-003](./SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md) — Physical Database Schema Document.
- Edge case sequence diagrams (e.g., session expiry, partial notifications), which belong to [SRIS-P1-ARCH-009](./SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md) — Service Interaction and Communication Design.

### 1.3 Audience

- **Lead Architect:** maintains this document and is the authority on architectural changes.
- **Backend and frontend developers:** must build the software using the exact structural patterns and diagrams defined here.
- **DevOps engineer:** uses the deployment topology and memory limits to configure the Docker environment.
- **Project supervisor and evaluator:** verifies that the system architecture is realistic, logically sound, and adheres to enterprise standards.

### 1.4 Terminology and Conventions

Every term in this document has the meaning recorded in [SRIS-P1-REQ-001](../wave-1-requirements/SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary and Domain Dictionary. The terms below carry the most weight in this document.

| Term | Meaning |
| :--- | :--- |
| ACID | Atomicity, Consistency, Isolation, Durability. The properties of a reliable database transaction. |
| C4 Model | Context, Containers, Components, and Code. A standard method for visualizing software architecture. |
| DNS | Domain Name System. In Docker, it allows containers to resolve each other by name. |
| FIFO | First-In-First-Out. A queueing discipline where the first request to arrive is the first to be processed. |
| OOM | Out Of Memory. A state where the operating system kills a process because it exceeded its memory limit. |
| TOCTOU | Time-of-Check to Time-of-Use. A race condition where a resource changes state between the moment it is checked and the moment it is used. |

This document follows the standards below.

- [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.
- [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md) — Document ID and Category Scheme.
- [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md) — Document Cross-Reference Standard.

---

## 2. Architectural Vision and Locked Decisions

To maintain FAANG-grade rigour and ensure the system survives the 5.1 GB RAM constraint, this section locks the strict architectural patterns that all developers must follow. These decisions are final and any deviation requires a formal revision of this document.

### 2.1 Modular 3-Tier Code Structure

Enterprise systems require a balance between strict separation of concerns and development velocity. We explicitly reject the verbose boilerplate of pure Hexagonal Architecture because it would consume too much of the 8-week timeline. Instead, we mandate a **Modular 3-Tier Architecture** for all 6 microservices.

The directory structure is strictly defined. For Java (Spring Boot) and Node.js (NestJS), the following folders are mandatory:
- `api/` (or `controller/`): Handles HTTP routing, request validation, and response formatting.
- `core/` (or `service/`): Contains the pure business logic, algorithms (e.g., the RAC/WL cascade), and orchestration.
- `data/` (or `repository/`): Handles all database interactions (JPA/Prisma). No SQL or database queries may exist outside this folder.
- `domain/` (or `model/`): Contains Entities, DTOs, and Enums.
- `security/`: Contains only granular authorization logic (e.g., verifying JWT claims). Heavy bot detection is offloaded to Nginx.
- `config/`: Application configurations (Redis, DB, external APIs).

This structure ensures that a Phase 2 developer can instantly locate any logic. Security is isolated, database access is isolated, and business logic is isolated. No file may cross these boundaries.

### 2.2 Service Discovery and Developer Workflow

- **Service Discovery:** Services find each other using Docker's embedded DNS (e.g., `http://s3-reservation:8080`). Heavy service registries like Eureka are explicitly rejected to save approximately 500 MB of RAM.
- **Developer Workflow (Sprint Isolation):** The infrastructure is split into modular Docker Compose files (`infra`, `services`, `gateway`, `monitoring`). We mandate the use of Docker **Profiles**. A developer building S1 in Sprint 3 will run `docker compose --profile sprint-3 up`, which starts *only* S1, PostgreSQL, and Redis. The other services remain off. The full stack only boots when the `all` profile is selected, preventing the laptop from crashing during early development.

### 2.3 Database Architecture and Isolation

To prevent kernel OOM (Out-Of-Memory) crashes while maintaining the "Own Your Data" principle, the architecture mandates **one** PostgreSQL container. Running four separate physical database containers would duplicate shared memory and exhaust the 5.1 GB limit.

Inside this single container, four isolated logical databases exist:
1.  `sris_iam`
2.  `sris_master_data`
3.  `sris_reservation`
4.  `sris_notification`

**Strict Rules:**
- Each service authenticates to its own database using a dedicated role. S3 cannot read `sris_iam`.
- Direct database-to-database querying is strictly forbidden. Cross-domain data must flow through REST APIs or Redis Streams.
- **Concurrency Control:** We explicitly **BAN** Pessimistic Locking (`SELECT ... FOR UPDATE`). All inventory updates must use **Optimistic Concurrency Control** (e.g., `UPDATE seats SET available = available - 1 WHERE available > 0`) to prevent connection pool exhaustion under extreme load.

### 2.4 Edge Security and Observability

- **Edge Security:** Nginx handles all ingress routing, rate-limiting, and anti-bot behavioral checks. The microservices remain lean and only perform micro-authorization (checking if the JWT role matches the endpoint).
- **Observability:** Promtail and Loki aggregate logs. Grafana is embedded in the Next.js Admin Console. To support non-technical employees (Operations Head), Grafana uses **Dashboard Variables** (dropdowns for Service, Log Level, and Time Range), ensuring zero-query syntax is required.

---

## 3. System Context (C4 Level 1)

The System Context diagram defines the highest-level view of SRIS. It illustrates how the platform interacts with its users and external simulators, treating the entire 6-microservice architecture as a single black box. 

This view is critical because it establishes the trust boundaries. The public internet is outside the black box, and the internal microservices are inside. 

```mermaid
flowchart TD
    %% Styling for high visibility on light and dark screens
    classDef person fill:#E1F5FE,stroke:#0288D1,stroke-width:2px,color:#000;
    classDef system fill:#C8E6C9,stroke:#1B5E20,stroke-width:4px,color:#000;
    classDef external fill:#FFE0B2,stroke:#E65100,stroke-width:2px,color:#000;

    %% Nodes (Larger, descriptive)
    Customer["Customer<br/>Public Web Browser"]:::person
    Employee["Employee<br/>Admin Console"]:::person
    
    SRIS[["SRIS Platform<br/>6 Microservices<br/>Phase 1 Foundation"]]:::system
    
    Payment["Mock Payment Gateway<br/>External Simulator"]:::external
    SMS["Android SMS Gateway<br/>External Simulator"]:::external

    %% Relationships
    Customer ==>|"1. Searches & Books Tickets"| SRIS
    Employee ==>|"1. Manages Master Data<br/>& Operations"| SRIS

    SRIS ==>|"2. Initiates Payment"| Payment
    Payment -.->|"3. Webhook Callback<br/>(Payment Success/Fail)"| SRIS

    SRIS -.->|"4. Publish Event (SMS)<br/>via Redis Streams"| SMS
```

---

## 4. Container Architecture (C4 Level 2)

The Container diagram zooms into the SRIS Platform. It shows the high-level technical building blocks (the 6 microservices, the gateway, the frontend, and the data stores) and how they communicate with each other over the network.

This diagram enforces the strict boundary rules defined in Section 2:
1. The frontend never talks directly to a database.
2. The microservices never query each other's databases.
3. Synchronous communication happens via REST (Nginx), and asynchronous communication happens via Redis Streams.

```mermaid
flowchart TD
    %% Styling for high visibility
    classDef client fill:#E1F5FE,stroke:#0288D1,stroke-width:2px,color:#000;
    classDef gateway fill:#FFF3E0,stroke:#F57C00,stroke-width:2px,color:#000;
    classDef backend fill:#E8F5E9,stroke:#388E3C,stroke-width:2px,color:#000;
    classDef database fill:#FCE4EC,stroke:#C2185B,stroke-width:2px,color:#000;
    classDef stream fill:#F3E5F5,stroke:#7B1FA2,stroke-width:2px,color:#000;

    %% Clients
    Frontend["Next.js Frontend<br/>(Customer Website &<br/>Employee Admin Console)"]:::client
    
    %% Gateway
    Gateway["Nginx API Gateway<br/>(Rate Limiting, SSL,<br/>Passive Health Checks)"]:::gateway

    %% Microservices
    S1["S1 IAM Service<br/>(Node.js NestJS)<br/>Auth & Tokens"]:::backend
    S2["S2 Master Data Service<br/>(Java Spring Boot)<br/>Stations, Trains, Fares"]:::backend
    S3["S3 Reservation Service<br/>(Java Spring Boot)<br/>Booking, Allocation, Saga"]:::backend
    S4["S4 Search BFF<br/>(Node.js NestJS)<br/>Aggregation & Search"]:::backend
    S5["S5 Mock Payment<br/>(Node.js NestJS)<br/>Payment Simulator"]:::backend
    S6["S6 Notification Service<br/>(Node.js NestJS)<br/>Email, SMS & Python Daemon"]:::backend

    %% Databases
    DB[("PostgreSQL Container<br/>(4 Isolated Logical DBs:<br/>IAM, Master, Reservation, Log)")]:::database
    Redis[("Redis Streams & Cache<br/>(Event Broker &<br/>Hot Seat Counters)")]:::stream
    
    %% Edges (Synchronous)
    Frontend ==>|"HTTPS Requests"| Gateway
    
    Gateway ==>|"/api/auth/*"| S1
    Gateway ==>|"/api/master-data/*"| S2
    Gateway ==>|"/api/booking/*"| S3
    Gateway ==>|"/api/search/*"| S4
    Gateway ==>|"/api/payment/*"| S5

    %% Edges (Service-to-Service Synchronous)
    S4 -->|"Fetch Schedules<br/>& Fares"| S2
    S4 -->|"Check Availability<br/>via Cache"| S3
    S3 -->|"Request Fare<br/>Re-quote"| S2
    S3 -->|"Initiate Payment"| S5
    S5 -.->|"Webhook Callback"| S3

    %% Edges (Data Layer)
    S1 -->|"Read/Write<br/>sris_iam"| DB
    S2 -->|"Read/Write<br/>sris_master_data"| DB
    S3 -->|"ACID Transactions<br/>sris_reservation"| DB
    S6 -->|"Log Events<br/>JSONB"| DB

    %% Edges (Asynchronous via Redis Streams)
    S3 -->|"Publish Booking<br/>Events (Transactional Outbox)"| Redis
    Redis -->|"Consume Events"| S6
    S4 -->|"Read Seat<br/>Availability"| Redis
```

---

## 5. Component Architecture (C4 Level 3)

The Component diagram zooms into a single microservice to show its internal structure. We mandate a **Modular 3-Tier Architecture** for all services. This balances the speed of development with enterprise separation of concerns.

The diagram below uses the Java Reservation Service (S3) as the reference implementation. The Node.js services (NestJS) follow the exact same logical structure, simply using the equivalent NestJS terminology (Controllers, Providers, Modules).

This structure ensures that security is isolated, business logic is protected, and database queries are centralised in one layer.

```mermaid
%%{init: {
  "flowchart": {
    "nodeSpacing": 70,
    "rankSpacing": 100,
    "padding": 30,
    "curve": "basis",
    "htmlLabels": true
  },
  "themeVariables": {
    "fontSize": "15px",
    "fontFamily": "Segoe UI, Arial, sans-serif"
  }
}}%%
flowchart TD
    %% Styling for high visibility on light and dark screens
    classDef component fill:#D1C4E9,stroke:#512DA8,stroke-width:2px,color:#000;
    classDef database fill:#F8BBD0,stroke:#C2185B,stroke-width:2px,color:#000;
    classDef external fill:#FFE0B2,stroke:#E65100,stroke-width:2px,color:#000;

    %% External nodes declared up-front so they render OUTSIDE S3
    Client["Next.js Frontend"]:::external
    DB[("PostgreSQL<br/>sris_reservation")]:::database
    Redis[("Redis Streams")]:::database

    subgraph S3 ["S3 Reservation Service Container (Java Spring Boot)"]
        direction TB
        
        subgraph API_Layer ["API Layer - api"]
            Controller["Booking Controller<br/>Handles HTTP POST /booking<br/>Validates Request DTOs"]:::component
        end
        
        subgraph Security_Layer ["Security Layer - security"]
            Guard["JWT Guard<br/>Verifies JWT Claims<br/>Checks Role Permissions"]:::component
        end

        subgraph Core_Layer ["Core Layer - core"]
            Service["Booking Service<br/>Executes Atomic SQL Update<br/>Generates PNR"]:::component
            Saga["Saga Orchestrator<br/>Cascades RAC / WL<br/>Triggers Refund on Failure"]:::component
        end

        subgraph Data_Layer ["Data Layer - data"]
            Repo["Booking Repository<br/>JPA / Hibernate<br/>Executes SQL Queries"]:::component
        end

        subgraph Domain_Layer ["Domain Layer - domain"]
            Entity["Booking Entity<br/>Maps to PostgreSQL Table<br/>Defines State Fields"]:::component
        end

        %% Internal Connections
        Controller -.->|"1. Passes Request"| Guard
        Guard -.->|"2. Authorized"| Service
        Service -->|"3. On Quota Exhausted"| Saga
        Service -->|"4. Saves Booking"| Repo
        Repo -->|"5. Reads/Writes"| Entity
    end

    %% External Connections
    Client -->|"HTTPS Request"| Controller
    Repo -->|"ACID Transaction"| DB
    Saga -->|"Publish Outbox Event"| Redis
    
    %% Subgraph Styling
    style S3 fill:#F8F9FA,stroke:#343A40,stroke-width:3px,color:#000
    style API_Layer fill:#FFFFFF,stroke:#6C757D,stroke-width:1px,stroke-dasharray:5 5,color:#000
    style Security_Layer fill:#FFFFFF,stroke:#6C757D,stroke-width:1px,stroke-dasharray:5 5,color:#000
    style Core_Layer fill:#FFFFFF,stroke:#6C757D,stroke-width:1px,stroke-dasharray:5 5,color:#000
    style Data_Layer fill:#FFFFFF,stroke:#6C757D,stroke-width:1px,stroke-dasharray:5 5,color:#000
    style Domain_Layer fill:#FFFFFF,stroke:#6C757D,stroke-width:1px,stroke-dasharray:5 5,color:#000
```

---

## 6. Deployment Topology and Resource Envelope

This section defines the physical deployment of SRIS. The entire architecture runs within a single **Docker Engine** on a local laptop, strictly bounded by the **5.1 GB RAM envelope** (Constraint C-2 in [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document).

### 6.1 Memory Allocation Strategy (Provisional Targets)

To prevent the Linux kernel's Out-Of-Memory (OOM) killer from terminating containers (Exit Code 137), we mandate hard memory limits using the modern Docker Compose `deploy.resources.limits.memory` syntax. 

The limits below are **Provisional Targets**. They are calculated baselines derived from the technology stack. During Week 4 of Phase 1, these limits will be monitored via Grafana and tuned dynamically to match actual runtime behaviour.

| Container | Initial Memory Limit | Rationale |
| :--- | :--- | :--- |
| **Java Services (S2, S3)** | 350 MB each | Requires headroom for JVM heap, Metaspace, and native memory. |
| **Node.js Services (S1, S4, S5, S6)** | 150 MB each | Lightweight V8 heap and Rust Prisma engine. |
| **Next.js Frontend** | 100 MB | Static server and Node runtime. |
| **PostgreSQL** | 512 MB | Shared buffer cache for all 4 logical databases. |
| **Redis** | 128 MB | In-memory cache and Streams. |
| **Nginx** | 64 MB | Edge routing and rate limiting. |
| **Observability (Grafana, Loki, Prometheus)** | 500 MB (total) | Combined limit for the monitoring stack. |
| **Python Agent** | 100 MB | Lightweight SRE daemon. |
| **Total Allocated** | **~4,050 MB (4.05 GB)** | Leaves ~1 GB for OS, Docker daemon, and unexpected spikes. |

### 6.2 Physical Deployment Diagram

The diagram below illustrates how the Docker containers are physically mapped onto the laptop's operating system. It explicitly shows the memory limits applied to each component and the internal Docker network that connects them.

Notice that the PostgreSQL container hosts all 4 logical databases, while Nginx acts as the strict perimeter for all inbound traffic. The Python Agent runs as a sidecar inside the S6 container, monitoring the overall resource envelope.

### 6.2 Physical Deployment Diagram

The diagram below illustrates how the Docker containers are physically mapped onto the laptop's operating system. It explicitly shows the memory limits applied to each component and the internal Docker network that connects them.

Notice the explicit data connections: S1, S2, S3, and S6 connect to their respective logical databases inside the single PostgreSQL container. S3 and S4 connect to Redis for caching and event streams. All services send metrics to Prometheus/Grafana.

```mermaid
%%{init: {
  "flowchart": {
    "nodeSpacing": 70,
    "rankSpacing": 120,
    "padding": 30,
    "curve": "basis",
    "htmlLabels": true
  },
  "themeVariables": {
    "fontSize": "15px",
    "fontFamily": "Segoe UI, Arial, sans-serif"
  }
}}%%
flowchart TD
    %% Styling
    classDef laptop fill:#E0F7FA,stroke:#006064,stroke-width:4px,color:#000;
    classDef docker fill:#F3E5F5,stroke:#4A148C,stroke-width:2px,stroke-dasharray:5 5,color:#000;
    classDef container fill:#FFF9C4,stroke:#F57F17,stroke-width:2px,color:#000;
    classDef database fill:#FFCDD2,stroke:#B71C1C,stroke-width:2px,color:#000;
    classDef gateway fill:#C8E6C9,stroke:#1B5E20,stroke-width:2px,color:#000;
    classDef monitor fill:#E1BEE7,stroke:#6A1B9A,stroke-width:2px,color:#000;

    %% External Nodes (Hoisted)
    PublicUser["Public Internet<br/>Customers & Employees"]:::container
    
    subgraph Laptop ["Local Laptop Environment (Strict 5.1 GB RAM Envelope)"]
        direction TB
        
        subgraph Docker ["Docker Engine & Network (sris-net)"]
            direction TB
            
            Nginx["Nginx Gateway<br/>Limit: 64 MB<br/>Routes /api/* traffic"]:::gateway
            
            subgraph Services ["Microservices Layer"]
                S1["S1 IAM<br/>Node.js | 150 MB"]:::container
                S2["S2 Master Data<br/>Java | 350 MB"]:::container
                S3["S3 Reservation<br/>Java | 350 MB"]:::container
                S4["S4 Search BFF<br/>Node.js | 150 MB"]:::container
                S5["S5 Mock Payment<br/>Node.js | 150 MB"]:::container
                S6["S6 Notification<br/>Node.js + Python<br/>Total: 250 MB"]:::container
            end
            
            subgraph Data ["Data Layer"]
                DB[("PostgreSQL Container<br/>Limit: 512 MB<br/>sris_iam, sris_master_data,<br/>sris_reservation, sris_notification")]:::database
                Redis[("Redis Container<br/>Limit: 128 MB<br/>Streams & Cache")]:::database
            end
            
            subgraph Observability ["Monitoring Layer"]
                Monitor["Grafana + Loki + Prometheus<br/>Limit: 500 MB"]:::monitor
            end
        end
    end
    
    %% Routing Connections
    PublicUser -->|"HTTPS"| Nginx
    Nginx -->|"/auth"| S1
    Nginx -->|"/master-data"| S2
    Nginx -->|"/booking"| S3
    Nginx -->|"/search"| S4
    Nginx -->|"/payment"| S5

    %% Explicit Database Connections
    S1 -->|"sris_iam"| DB
    S2 -->|"sris_master_data"| DB
    S3 -->|"sris_reservation"| DB
    S6 -->|"sris_notification"| DB

    %% Explicit Redis Connections
    S3 -->|"Publish Events"| Redis
    S4 -->|"Read Cache"| Redis
    Redis -->|"Consume Events"| S6

    %% Explicit Monitoring Connections
    S1 -.->|"Metrics"| Monitor
    S2 -.->|"Metrics"| Monitor
    S3 -.->|"Metrics"| Monitor
    S4 -.->|"Metrics"| Monitor
    S5 -.->|"Metrics"| Monitor
    S6 -.->|"Metrics"| Monitor
    
    %% Subgraph Styling
    style Laptop fill:#E0F7FA,stroke:#006064,stroke-width:4px,color:#000
    style Docker fill:#F3E5F5,stroke:#4A148C,stroke-width:2px,stroke-dasharray:5 5,color:#000
    style Services fill:#FFFFFF,stroke:#6C757D,stroke-width:1px,stroke-dasharray:5 5,color:#000
    style Data fill:#FFFFFF,stroke:#6C757D,stroke-width:1px,stroke-dasharray:5 5,color:#000
    style Observability fill:#FFFFFF,stroke:#6C757D,stroke-width:1px,stroke-dasharray:5 5,color:#000
```

---

## 7. Core Sequence Flows

Structure is meaningless without behaviour. This section provides the Sequence Diagrams for the two most critical flows in SRIS: Authentication and Post-Payment Allocation.

### 7.1 Authentication and Automatic Routing Flow

This flow demonstrates the strict portal separation. There is no role-selection dropdown on the login screen. The identity is verified by S1 IAM, and the Next.js Route Guard automatically intercepts the JWT to route the user to the correct dashboard based on their embedded role claim.

```mermaid
%%{init: {
  "theme": "base",
  "themeVariables": {
    "primaryColor": "#E1F5FE",
    "primaryTextColor": "#000",
    "primaryBorderColor": "#0288D1",
    "lineColor": "#000",
    "secondaryColor": "#FFF3E0",
    "tertiaryColor": "#FCE4EC"
  },
  "sequence": {
    "messageMargin": 40,
    "actorMargin": 60
  }
}}%%
sequenceDiagram
    autonumber
    actor User as Customer / Employee
    participant NextJS as Next.js Frontend
    participant Nginx as Nginx API Gateway
    participant S1 as S1 IAM Service (Node.js)
    participant DB as PostgreSQL (sris_iam)

    User->>NextJS: Enters Username & Password
    NextJS->>Nginx: POST /api/auth/login
    Nginx->>S1: Forward Request
    S1->>DB: SELECT * FROM users WHERE email = ?
    DB-->>S1: User Record (Hash & Role)
    
    alt Invalid Credentials
        S1-->>Nginx: 401 Unauthorized
        Nginx-->>NextJS: 401 Unauthorized
        NextJS-->>User: Show Error Message
    else Valid Credentials
        S1->>S1: Generate JWT (Contains Role Claim)
        S1-->>Nginx: 200 OK + JWT
        Nginx-->>NextJS: 200 OK + JWT
        NextJS->>NextJS: Route Guard (Decode JWT)
        
        alt Role = Customer
            NextJS-->>User: Auto-Redirect to /customer/dashboard
        else Role = ER-02 (Data Entry)
            NextJS-->>User: Auto-Redirect to /employee/dashboard
        else Role = AD-01 (Super Admin)
            NextJS-->>User: Auto-Redirect to /admin/central-command
        end
    end
```

---

### 7.2 Post-Payment Allocation and Saga Cascade Flow

This flow demonstrates how the system handles extreme concurrency (e.g., hundreds of users paying at the same time). It proves the **Post-Payment Allocation** model: seats are not locked during browsing. Allocation happens only after the payment webhook arrives.

The Java Worker executes a single ACID transaction that:
1.  Atomically updates the seat status (using optimistic concurrency, not row locks).
2.  Generates the PNR.
3.  Writes passenger details to the database.
4.  Writes the Outbox event (ensuring the notification is never lost, even if the server crashes).

If the Confirmed quota is exhausted, the algorithm cascades to RAC, then Waitlist, then RLWL, and finally triggers a Saga Refund.

```mermaid
%%{init: {
  "theme": "base",
  "themeVariables": {
    "primaryColor": "#E8F5E9",
    "primaryTextColor": "#000",
    "primaryBorderColor": "#388E3C",
    "lineColor": "#000",
    "secondaryColor": "#FFF3E0",
    "tertiaryColor": "#FCE4EC",
    "actorBkg": "#E1F5FE",
    "actorBorder": "#0288D1"
  },
  "sequence": {
    "messageMargin": 40,
    "actorMargin": 60
  }
}}%%
sequenceDiagram
    autonumber
    actor User as Customer
    participant Next as Next.js Frontend
    participant Nginx as Nginx Gateway
    participant S5 as S5 Mock Payment
    participant Stream as Redis Streams
    participant S3 as S3 Reservation (Java)
    participant DB as PostgreSQL (Reservation)
    participant S6 as S6 Notification

    User->>Next: Clicks "Pay"
    Next->>Nginx: POST /api/payment/initiate
    Nginx->>S5: Forward Payment Request
    S5-->>User: Show Payment UI
    
    Note over User, S5: User completes bank authentication (3-30 seconds)
    
    S5->>Nginx: POST /api/payment/webhook (Success)
    Nginx->>Stream: Push Webhook to Redis Stream (FIFO)
    Nginx-->>Next: 202 Accepted (Processing)
    Next-->>User: Spinner Continues Loading
    
    Note over Stream, S3: Java Worker Pool (10 Threads) Picks Up Webhook
    
    S3->>Stream: XREADGROUP (Pull Message)
    Stream-->>S3: Webhook Payload (BookingID, Passengers)
    
    rect rgb(232, 245, 233)
    Note right of S3: Single ACID Transaction Begins
    S3->>DB: BEGIN TRANSACTION
    S3->>DB: UPDATE seats SET status = 'BOOKED' WHERE id = (SELECT ... LIMIT 1) RETURNING seat_number
    DB-->>S3: Seat Allocated (S6/B3)
    
    alt Confirmed Seats Available
        S3->>DB: INSERT INTO bookings (passenger details, seat, PNR)
        S3->>DB: INSERT INTO outbox (BookingConfirmed event)
        DB-->>S3: COMMIT SUCCESS
    else Confirmed Full (Check RAC)
        S3->>DB: UPDATE rac_seats SET status = 'BOOKED' WHERE ...
        DB-->>S3: RAC Allocated
        S3->>DB: INSERT INTO bookings (passenger details, RAC, PNR)
        S3->>DB: INSERT INTO outbox (BookingConfirmed event)
        DB-->>S3: COMMIT SUCCESS
    else RAC Full (Check Waitlist)
        S3->>DB: INSERT INTO waitlist (passenger details, position, PNR)
        S3->>DB: INSERT INTO outbox (BookingWaitlisted event)
        DB-->>S3: COMMIT SUCCESS
    else All Quotas Exhausted (Saga Refund)
        S3->>DB: ROLLBACK
        S3->>S5: POST /api/payment/reverse
        S5-->>User: Refund Initiated (3-4 days)
    end
    end
    
    Note over S3, Stream: Post-Transaction Actions
    S3->>Stream: XACK (Acknowledge Message)
    S3->>DB: Background Job reads outbox and pushes to Notification Stream
    DB-->>S6: Consume BookingConfirmed Event
    S6->>S6: Send Email (SMTP) + SMS (Android Gateway)
    
    Next->>S3: GET /api/booking/status/{bookingID}
    S3-->>Next: 200 OK (Status: CONFIRMED, PNR: 1234567890)
    Next-->>User: Spinner Stops. Show Ticket with PNR.
```

---

### 7.3 Post-Payment Allocation Flowchart (Algorithmic Deep Dive)

While the Sequence Diagram (Section 7.2) shows the chronological interaction between containers, the flowchart below illustrates the exact decision logic executed by the Java Worker inside the S3 Reservation Service. 

It explicitly demonstrates the **ACID Transaction Boundary** and the **All-or-Nothing Rollback** rule. If a group of passengers cannot be fully accommodated across the quota tiers, the entire database transaction is rolled back, and a Saga Refund is triggered.

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
    "fontSize": "15px",
    "fontFamily": "Segoe UI, Arial, sans-serif"
  }
}}%%
flowchart TD
    %% Styling
    classDef process fill:#E1F5FE,stroke:#0288D1,stroke-width:2px,color:#000;
    classDef decision fill:#FFF3E0,stroke:#F57C00,stroke-width:2px,color:#000;
    classDef db fill:#FCE4EC,stroke:#C2185B,stroke-width:2px,color:#000;
    classDef success fill:#E8F5E9,stroke:#388E3C,stroke-width:2px,color:#000;
    classDef fail fill:#FFEBEE,stroke:#D32F2F,stroke-width:2px,color:#000;
    classDef stream fill:#F3E5F5,stroke:#7B1FA2,stroke-width:2px,color:#000;

    %% Nodes
    Start(("Webhook Arrives")):::stream
    Queue[("Redis Stream<br/>Strict FIFO Queue")]:::stream
    Worker["Java Worker Thread<br/>Pulls Webhook"]:::process
    
    subgraph ACID ["PostgreSQL ACID Transaction (Single Scope)"]
        direction TB
        CheckConf{"Confirmed<br/>Seats > 0?"}:::decision
        LockConf["Atomic UPDATE<br/>Seats = Seats - 1"]:::db
        
        CheckRAC{"RAC<br/>Seats > 0?"}:::decision
        LockRAC["Atomic UPDATE<br/>RAC = RAC - 1"]:::db
        
        CheckWL{"Waitlist<br/>Seats > 0?"}:::decision
        LockWL["INSERT INTO<br/>Waitlist"]:::db
        
        GenPNR["Generate PNR &<br/>Save Booking"]:::process
        Rollback["ROLLBACK<br/>All Seats Released"]:::fail
    end

    Commit["COMMIT<br/>Database Saved"]:::success
    UpdateCache["Update Redis<br/>Hot Counters"]:::db
    Notify["Push to Outbox<br/>Send Email & SMS"]:::success
    XACK["XACK Redis Stream<br/>Remove Message"]:::stream
    UserScreen(("Spinner Stops<br/>User Sees Ticket")):::success

    %% Flow
    Start --> Queue
    Queue --> Worker
    Worker --> CheckConf
    
    CheckConf -->|Yes| LockConf
    LockConf --> GenPNR
    
    CheckConf -->|No| CheckRAC
    CheckRAC -->|Yes| LockRAC
    LockRAC --> GenPNR
    
    CheckRAC -->|No| CheckWL
    CheckWL -->|Yes| LockWL
    LockWL --> GenPNR
    
    CheckWL -->|No| Rollback
    Rollback --> SagaRefund(("Saga Refund<br/>3-4 Days"))
    
    GenPNR --> Commit
    Commit --> UpdateCache
    Commit --> Notify
    UpdateCache --> XACK
    Notify --> XACK
    XACK --> UserScreen
```

---

## 8. Approval

| Role           | Name        | Decision | Date       |
| -------------- | ----------- | -------- | ---------- |
| Lead Architect | Koushal Jha | Approved | 2026-10-19 |

---

## Revision History

| Version | Date       | Author      | Change           |
| ------- | ---------- | ----------- | ---------------- |
| 1.0     | 2026-10-19 | Koushal Jha | Initial release. |

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
| 2.5  | [SRIS-P1-ARCH-005](./SRIS-P1-ARCH-005_DomainModelDocument.md)                                                   | Domain Model Document                             | 2    | P0  | UNBLOCK |
| 2.8  | [SRIS-P1-ARCH-008](./SRIS-P1-ARCH-008_TechnologyStackADR.md)                                                    | Technology Stack ADR                              | 2    | P0  | UNBLOCK |
| 2.9  | [SRIS-P1-ARCH-009](./SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md)                              | Service Interaction and Communication Design      | 2    | P0  | UNBLOCK |
| 3.2  | [SRIS-P1-DATA-002](./SRIS-P1-DATA-002_LogicalDataModelPerService.md)                                            | Logical Data Model (per service)                  | 3    | P0  | UNBLOCK |
| 3.3  | [SRIS-P1-DATA-003](./SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)                                        | Physical Database Schema Document                 | 3    | P0  | UNBLOCK |
| 3.14 | [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md)                                              | API Contract Document (OpenAPI)                   | 3    | P0  | UNBLOCK |

### B.2 Documents That Reference This Document

| Seq  | Document ID                                                                             | Document Name                                | Why It References                                                                 |
| ---- | --------------------------------------------------------------------------------------- | -------------------------------------------- | --------------------------------------------------------------------------------- |
| 2.4  | [SRIS-P1-ARCH-004](./SRIS-P1-ARCH-004_BoundedContextMap.md)                                 | Bounded Context Map                          | Uses the container boundaries defined here to map contexts                        |
| 2.9  | [SRIS-P1-ARCH-009](./SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md)          | Service Interaction and Communication Design | Expands on the sequence flows and algorithm logic defined in Section 7            |
| 2.12 | [SRIS-P1-ARCH-012](./SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)           | Observability and Monitoring Design          | Details the Prometheus/Grafana integration mentioned in Section 2.4               |
| 3.2  | [SRIS-P1-DATA-002](./SRIS-P1-DATA-002_LogicalDataModelPerService.md)                        | Logical Data Model (per service)             | Maps the logical databases described in Section 2.3 to physical schemas           |
| 3.14 | [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md)                          | API Contract Document (OpenAPI)              | Defines the exact REST endpoints for the communication paths shown in Section 4    |
| 6.2  | [SRIS-P1-DEV-004](../wave-6-developer-standards/SRIS-P1-DEV-004_CodingStandardsAndConventions.md) | Coding Standards and Conventions             | Enforces the Modular 3-Tier directory structure defined in Section 2.1            |

### B.3 Documents This Document Depends On (Upstream)

| Seq | Document ID                                                                                 | Document Name                          | Dependency Type |
| --- | ------------------------------------------------------------------------------------------- | -------------------------------------- | --------------- |
| 0.1 | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)           | Document Template Standard             | Hard            |
| 2.1 | [SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md)                                 | Microservices Identification           | Hard            |
| 2.5 | [SRIS-P1-ARCH-005](./SRIS-P1-ARCH-005_DomainModelDocument.md)                                         | Domain Model Document                  | Hard            |
| 2.8 | [SRIS-P1-ARCH-008](./SRIS-P1-ARCH-008_TechnologyStackADR.md)                                          | Technology Stack ADR                   | Hard            |
| 0.4 | [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)      | Project Vision and Scope Document      | Soft            |

### B.4 Documents This Document Unblocks (Downstream)

| Seq  | Document ID                                                                             | Document Name                                | Blocked Until |
| ---- | --------------------------------------------------------------------------------------- | -------------------------------------------- | ------------- |
| 2.4  | [SRIS-P1-ARCH-004](./SRIS-P1-ARCH-004_BoundedContextMap.md)                                 | Bounded Context Map                          | This approved |
| 2.9  | [SRIS-P1-ARCH-009](./SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md)          | Service Interaction and Communication Design | This approved |
| 2.12 | [SRIS-P1-ARCH-012](./SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)           | Observability and Monitoring Design          | This approved |
| 3.2  | [SRIS-P1-DATA-002](./SRIS-P1-DATA-002_LogicalDataModelPerService.md)                        | Logical Data Model (per service)             | This approved |
| 3.14 | [SRIS-P1-API-001](./SRIS-P1-API-001_APIContractDocumentOpenAPI.md)                          | API Contract Document (OpenAPI)              | This approved |
| 5.1  | [SRIS-P1-INF-001](../wave-5-devops-operations/SRIS-P1-INF-001_InfrastructureAndTechnologyDocument.md) | Infrastructure and Technology Document       | This approved |

### B.5 Master Documentation Index

The complete list of Phase 1 documents is in [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

### B.6 External Reference Documents

| Reference Type | Where It Is Documented                                                                                                                                                                                                                                     |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Website        | Mermaid JS Documentation. https://mermaid.js.org/. Referenced for the C4 model, sequence diagram syntax, and flowchart configuration.                                                                                                                      |

### B.7 Document Conventions

The conventions for Priority and Tag values are defined in [Section 9](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md#9-vocabulary-standards) of [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.