<div align="center">

![Software](https://img.shields.io/badge/Software-SRIS-1f6feb?style=for-the-badge)
![Architecture](https://img.shields.io/badge/Architecture-Polyglot%20Microservices-6f42c1?style=for-the-badge)
![Group](https://img.shields.io/badge/Group-G320-d29922?style=for-the-badge)
![Version](https://img.shields.io/badge/Version-1.0-2ea043?style=for-the-badge)

</div>

# Documentation Index and Navigation Map

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Status:** Approved | **Version:** 1.0 | **Date:** 2026-10-10 | **Document ID:** SRIS-P1-GOV-001

| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| Title              | Documentation Index and Navigation Map                            |
| Software           | SRIS                                                              |
| Software Full Form | Sarathi Railway Information System                                |
| Team Codename      | Project Sarathi                                                   |
| Document ID        | SRIS-P1-GOV-001                                                   |
| Task               | Establish the master index for all Phase 1 documents              |
| Document Type      | Navigation and Reference Document                                 |
| Milestone          | Phase 1 Foundation                                                |
| Classification     | Internal                                                          |
| Version            | 1.0                                                               |
| Date               | 2026-10-10                                                        |
| Author             | Koushal Jha, Lead Architect                                       |
| Status             | Approved                                                          |
| Approved By        | Koushal Jha, Lead Architect                                       |
| Approval Date      | 2026-10-10                                                        |
| Supersedes         | None (first version)                                              |
| Related Documents  | All Phase 1 documents                                             |
| Affiliation        | Independent · Not affiliated with CRIS, IRCTC, or Indian Railways |

---

## Table of Contents

1. [Introduction](#1-introduction)
   - [1.1 Purpose](#11-purpose)
   - [1.2 Scope](#12-scope)
   - [1.3 Audience](#13-audience)
2. [How to Use This Index](#2-how-to-use-this-index)
   - [2.1 Reading Paths Overview](#21-reading-paths-overview)
   - [2.2 Finding a Document](#22-finding-a-document)
   - [2.3 Understanding Document IDs](#23-understanding-document-ids)
3. [Complete Document Register](#3-complete-document-register)
   - [3.1 Wave Summary](#31-wave-summary)
   - [3.2 Status Legend](#32-status-legend)
   - [3.3 Wave 0: Project Foundation](#33-wave-0-project-foundation)
   - [3.4 Wave 1: Requirements](#34-wave-1-requirements)
   - [3.5 Wave 2: Architecture](#35-wave-2-architecture)
   - [3.6 Wave 3: Detailed Design](#36-wave-3-detailed-design)
   - [3.7 Wave 4: Testing](#37-wave-4-testing)
   - [3.8 Wave 5: DevOps and Operations](#38-wave-5-devops-and-operations)
   - [3.9 Wave 6: Developer Standards](#39-wave-6-developer-standards)
   - [3.10 Wave 7: Project Tracking](#310-wave-7-project-tracking)
   - [3.11 Wave 8: User and Support](#311-wave-8-user-and-support)
   - [3.12 Wave 9: Supporting Artifacts](#312-wave-9-supporting-artifacts)
4. [Navigation by Role](#4-navigation-by-role)
   - [4.1 Database Developer](#41-database-developer)
   - [4.2 Backend Developer](#42-backend-developer)
   - [4.3 Frontend Developer](#43-frontend-developer)
   - [4.4 UI/UX Designer](#44-uiux-designer)
   - [4.5 Tester (QA)](#45-tester-qa)
   - [4.6 DevOps Engineer](#46-devops-engineer)
   - [4.7 Evaluator](#47-evaluator)
5. [Navigation by Topic](#5-navigation-by-topic)
6. [Dependency Overview](#6-dependency-overview)
7. [Document Conventions](#7-document-conventions)
   - [7.1 File Naming](#71-file-naming)
   - [7.2 Folder Structure](#72-folder-structure)
   - [7.3 Metadata Table Fields](#73-metadata-table-fields)
   - [7.4 Status Values](#74-status-values)
   - [7.5 Priority Values](#75-priority-values)
   - [7.6 Tag Values](#76-tag-values)
8. [Approval](#8-approval)

- [Revision History](#revision-history)
- [Appendix A: Document ID Category Codes](#appendix-a-document-id-category-codes)
- [Appendix B: Wave Definitions](#appendix-b-wave-definitions)

---

## 1. Introduction

### 1.1 Purpose

This document is the master index for all Phase 1 Foundation documents of SRIS (Sarathi Railway Information System). It answers one question: which Phase 1 document covers what, where it is located, and what its current status is. It does not explain the content of any document. It only points to them.

### 1.2 Scope

In scope:

- Complete list of all Phase 1 documents with Seq, Document ID, Title, Wave, Priority, Tag, and Status.
- Reading paths by role.
- Topic lookup table.
- High-level dependency overview.
- File naming and folder conventions.

Out of scope:

- Content of any individual document.
- Phase 2, Phase 3, or future-phase documents.
- Technology, architecture, or design decisions.

### 1.3 Audience

- Lead Architect: tracks the status of every document.
- Team members: find the documents that apply to their work.
- Evaluators: locate the documents to be reviewed.
- Future contributors: learn how the documentation is organised.
- AI consultants: identify the document that supplies the context for a task.

---

## 2. How to Use This Index

### 2.1 Reading Paths Overview

Every reader starts here. [Section 4](#4-navigation-by-role) gives role-based reading paths. [Section 3](#3-complete-document-register) and [Section 5](#5-navigation-by-topic) offer alternative ways to find a document.

### 2.2 Finding a Document

There are three ways to find a document:

1. **By sequence number (wave.seq):** [Section 3](#3-complete-document-register) lists every document under its wave with its sequence number.
2. **By Document ID:** the Document ID column in [Section 3](#3-complete-document-register) links to each document. The category codes are listed in [Appendix A](#appendix-a-document-id-category-codes).
3. **By topic:** [Section 5](#5-navigation-by-topic) maps topics to documents.

### 2.3 Understanding Document IDs

Format: `SRIS-P1-CATEGORY-NNN`

| Part     | Meaning                                                                  |
| -------- | ------------------------------------------------------------------------ |
| SRIS     | Software identifier — Sarathi Railway Information System                 |
| P1       | Phase identifier — Phase 1 Foundation                                    |
| CATEGORY | Category code — see [Appendix A](#appendix-a-document-id-category-codes) |
| NNN      | Three-digit sequence number within the category                          |

---

## 3. Complete Document Register

Phase 1 contains 180 documents across 10 waves. Each wave groups documents by purpose. The wave summary is given below, followed by the full register per wave.

### 3.1 Wave Summary

| Wave | Name                  | Documents |
| ---- | --------------------- | --------- |
| 0    | Project Foundation    | 21        |
| 1    | Requirements          | 16        |
| 2    | Architecture          | 16        |
| 3    | Detailed Design       | 50        |
| 4    | Testing               | 16        |
| 5    | DevOps and Operations | 21        |
| 6    | Developer Standards   | 13        |
| 7    | Project Tracking      | 17        |
| 8    | User and Support      | 8         |
| 9    | Supporting Artifacts  | 2         |
|      | **Total**             | **180**   |

### 3.2 Status Legend

| Value       | Meaning                           |
| ----------- | --------------------------------- |
| Done        | Document is complete and approved |
| In Progress | Being written or under review     |
| Not Started | Planned but not yet started       |

### 3.3 Wave 0: Project Foundation

Folder: `wave-0-project-foundation` (the folder that holds this document). Documents: 21.

| Seq  | Document ID                                                                   | Title                                     | Pri | Tag     | Status      |
| ---- | ----------------------------------------------------------------------------- | ----------------------------------------- | --- | ------- | ----------- |
| 0.0  | [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md)    | Documentation Index and Navigation Map    | P0  | UNBLOCK | Done        |
| 0.1  | [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md)              | Document Template Standard                | P0  | UNBLOCK | Not Started |
| 0.2  | [SRIS-P1-GOV-003](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)           | Document ID and Category Scheme           | P1  | UNBLOCK | Not Started |
| 0.3  | [SRIS-P1-GOV-004](./SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md)        | Document Cross-Reference Standard         | P1  | UNBLOCK | Not Started |
| 0.4  | [SRIS-P1-GOV-005](./SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)         | Project Vision and Scope Document         | P0  | UNBLOCK | Not Started |
| 0.5  | [SRIS-P1-GOV-006](./SRIS-P1-GOV-006_ProjectCharter.md)                        | Project Charter                           | P1  | FOLLOW  | Not Started |
| 0.6  | [SRIS-P1-GOV-007](./SRIS-P1-GOV-007_ProjectManagementPlan.md)                 | Project Management Plan                   | P0  | UNBLOCK | Not Started |
| 0.7  | [SRIS-P1-GOV-008](./SRIS-P1-GOV-008_ProjectStakeholderAndAudienceRegister.md) | Project Stakeholder and Audience Register | P2  | FOLLOW  | Not Started |
| 0.8  | [SRIS-P1-GOV-009](./SRIS-P1-GOV-009_RiskManagementPlan.md)                    | Risk Management Plan                      | P1  | FOLLOW  | Not Started |
| 0.9  | [SRIS-P1-GOV-010](./SRIS-P1-GOV-010_CommunicationPlan.md)                     | Communication Plan                        | P2  | FOLLOW  | Not Started |
| 0.10 | [SRIS-P1-GOV-011](./SRIS-P1-GOV-011_QualityManagementPlan.md)                 | Quality Management Plan                   | P2  | FOLLOW  | Not Started |
| 0.11 | [SRIS-P1-GOV-012](./SRIS-P1-GOV-012_ChangeManagementPlan.md)                  | Change Management Plan                    | P2  | FOLLOW  | Not Started |
| 0.12 | [SRIS-P1-GOV-013](./SRIS-P1-GOV-013_AssumptionsAndConstraintsLog.md)          | Assumptions and Constraints Log           | P1  | UNBLOCK | Not Started |
| 0.13 | [SRIS-P1-GOV-014](./SRIS-P1-GOV-014_DecisionLogMaster.md)                     | Decision Log (Master)                     | P1  | UNBLOCK | Not Started |
| 0.14 | [SRIS-P1-GOV-015](./SRIS-P1-GOV-015_BusinessCaseDocument.md)                  | Business Case Document                    | P2  | FOLLOW  | Not Started |
| 0.15 | [SRIS-P1-GOV-016](./SRIS-P1-GOV-016_LicenseDocument.md)                       | License Document                          | P2  | FOLLOW  | Not Started |
| 0.16 | [SRIS-P1-GOV-017](./SRIS-P1-GOV-017_ContributionGuidelines.md)                | Contribution Guidelines                   | P2  | FOLLOW  | Not Started |
| 0.17 | [SRIS-P1-GOV-018](./SRIS-P1-GOV-018_CodeOfConduct.md)                         | Code of Conduct                           | P2  | FOLLOW  | Not Started |
| 0.18 | [SRIS-P1-GOV-019](./SRIS-P1-GOV-019_ProductRoadmapPhase123.md)                | Product Roadmap (Phase 1, 2, 3)           | P2  | FOLLOW  | Not Started |
| 0.19 | [SRIS-P1-DEV-001](./SRIS-P1-DEV-001_DeveloperProfile.md)                      | Developer Profile                         | P0  | UNBLOCK | Not Started |
| 0.20 | [SRIS-P1-DEV-002](./SRIS-P1-DEV-002_RolesAndResponsibilitiesDocument.md)      | Roles and Responsibilities Document       | P1  | UNBLOCK | Not Started |

### 3.4 Wave 1: Requirements

Folder: `wave-1-requirements`. Documents: 16.

| Seq  | Document ID                                                                                       | Title                                     | Pri | Tag     | Status      |
| ---- | ------------------------------------------------------------------------------------------------- | ----------------------------------------- | --- | ------- | ----------- |
| 1.1  | [SRIS-P1-REQ-001](../wave-1-requirements/SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md)          | Glossary and Domain Dictionary            | P0  | UNBLOCK | Not Started |
| 1.2  | [SRIS-P1-REQ-002](../wave-1-requirements/SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md)      | Business Requirements Document (BRD)      | P0  | UNBLOCK | Not Started |
| 1.3  | [SRIS-P1-REQ-003](../wave-1-requirements/SRIS-P1-REQ-003_CapabilityCatalogFinal.md)               | Capability Catalog (Final)                | P0  | UNBLOCK | Not Started |
| 1.4  | [SRIS-P1-REQ-004](../wave-1-requirements/SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) | Software Requirements Specification (SRS) | P0  | UNBLOCK | Not Started |
| 1.5  | [SRIS-P1-REQ-005](../wave-1-requirements/SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md)    | Non-Functional Requirements (ISO 25010)   | P0  | UNBLOCK | Not Started |
| 1.6  | [SRIS-P1-REQ-006](../wave-1-requirements/SRIS-P1-REQ-006_UserStoriesAndUseCases.md)               | User Stories and Use Cases                | P0  | UNBLOCK | Not Started |
| 1.7  | [SRIS-P1-REQ-007](../wave-1-requirements/SRIS-P1-REQ-007_DomainRulesFareCalculation.md)           | Domain Rules: Fare Calculation            | P1  | FOLLOW  | Not Started |
| 1.8  | [SRIS-P1-REQ-008](../wave-1-requirements/SRIS-P1-REQ-008_DomainRulesTicketing.md)                 | Domain Rules: Ticketing                   | P1  | FOLLOW  | Not Started |
| 1.9  | [SRIS-P1-REQ-009](../wave-1-requirements/SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)   | Domain Rules: Waitlist and Cancellation   | P1  | FOLLOW  | Not Started |
| 1.10 | [SRIS-P1-REQ-010](../wave-1-requirements/SRIS-P1-REQ-010_DomainRulesChartPreparation.md)          | Domain Rules: Chart Preparation           | P1  | FOLLOW  | Not Started |
| 1.11 | [SRIS-P1-REQ-011](../wave-1-requirements/SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)    | Domain Rules: Seat Matrix and Inventory   | P1  | FOLLOW  | Not Started |
| 1.12 | [SRIS-P1-REQ-012](../wave-1-requirements/SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md)     | Requirement Traceability Matrix (RTM)     | P2  | FOLLOW  | Not Started |
| 1.13 | [SRIS-P1-REQ-013](../wave-1-requirements/SRIS-P1-REQ-013_RequirementGatheringNotes.md)            | Requirement Gathering Notes               | P2  | FOLLOW  | Not Started |
| 1.14 | [SRIS-P1-REQ-014](../wave-1-requirements/SRIS-P1-REQ-014_DataPrivacyRequirements.md)              | Data Privacy Requirements                 | P1  | FOLLOW  | Not Started |
| 1.15 | [SRIS-P1-REQ-015](../wave-1-requirements/SRIS-P1-REQ-015_AccessibilityRequirements.md)            | Accessibility Requirements                | P2  | FOLLOW  | Not Started |
| 1.16 | [SRIS-P1-REQ-016](../wave-1-requirements/SRIS-P1-REQ-016_BusinessModelDocument.md)                | Business Model Document                   | P1  | FOLLOW  | Not Started |

### 3.5 Wave 2: Architecture

Folder: `wave-2-architecture`. Documents: 16.

| Seq  | Document ID                                                                                               | Title                                           | Pri | Tag     | Status      |
| ---- | --------------------------------------------------------------------------------------------------------- | ----------------------------------------------- | --- | ------- | ----------- |
| 2.1  | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)                | Microservices Identification                    | P0  | UNBLOCK    | In Progress        |
| 2.2  | [SRIS-P1-ARCH-002](../wave-2-architecture/SRIS-P1-ARCH-002_ArchitecturePrinciples.md)                     | Architecture Principles                         | P0  | UNBLOCK | Not Started |
| 2.3  | [SRIS-P1-ARCH-003](../wave-2-architecture/SRIS-P1-ARCH-003_SystemArchitectureDocument.md)                 | System Architecture Document                    | P0  | UNBLOCK | Not Started |
| 2.4  | [SRIS-P1-ARCH-004](../wave-2-architecture/SRIS-P1-ARCH-004_BoundedContextMap.md)                          | Bounded Context Map                             | P0  | UNBLOCK | Not Started |
| 2.5  | [SRIS-P1-ARCH-005](../wave-2-architecture/SRIS-P1-ARCH-005_DomainModelDocument.md)                        | Domain Model Document                           | P0  | UNBLOCK | Not Started |
| 2.6  | [SRIS-P1-ARCH-006](../wave-2-architecture/SRIS-P1-ARCH-006_EventStormingOutput.md)                        | Event Storming Output                           | P1  | FOLLOW  | Not Started |
| 2.7  | [SRIS-P1-ARCH-007](../wave-2-architecture/SRIS-P1-ARCH-007_ArchitectureDecisionRecordsMasterIndex.md)     | Architecture Decision Records — Master Index    | P1  | FOLLOW  | Not Started |
| 2.8  | [SRIS-P1-ARCH-008](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md)                         | Technology Stack ADR                            | P0  | UNBLOCK | Not Started |
| 2.9  | [SRIS-P1-ARCH-009](../wave-2-architecture/SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md)   | Service Interaction and Communication Design    | P0  | UNBLOCK | Not Started |
| 2.10 | [SRIS-P1-ARCH-010](../wave-2-architecture/SRIS-P1-ARCH-010_SecurityArchitectureDocument.md)               | Security Architecture Document                  | P1  | FOLLOW  | Not Started |
| 2.11 | [SRIS-P1-ARCH-011](../wave-2-architecture/SRIS-P1-ARCH-011_ErrorHandlingAndResilienceDesign.md)           | Error Handling and Resilience Design            | P1  | FOLLOW  | Not Started |
| 2.12 | [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)    | Observability and Monitoring Design (OTel/W3C)  | P0  | UNBLOCK | Not Started |
| 2.13 | [SRIS-P1-ARCH-013](../wave-2-architecture/SRIS-P1-ARCH-013_DeploymentArchitectureDocument.md)             | Deployment Architecture Document                | P1  | FOLLOW  | Not Started |
| 2.14 | [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md)   | Distributed Concurrency and Locking Strategy    | P0  | UNBLOCK | Not Started |
| 2.15 | [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md) | Distributed Transaction and Saga Pattern Design | P0  | UNBLOCK | Not Started |
| 2.16 | [SRIS-P1-ARCH-016](../wave-2-architecture/SRIS-P1-ARCH-016_ServiceRegistryAndCatalog.md)                  | Service Registry and Catalog                    | P0  | UNBLOCK | Not Started |

### 3.6 Wave 3: Detailed Design

Folder: `wave-3-detailed-design`. Documents: 50.

#### Group 3A: Data Design (13)

| Seq  | Document ID                                                                                                | Title                                         | Pri | Tag     | Status      |
| ---- | ---------------------------------------------------------------------------------------------------------- | --------------------------------------------- | --- | ------- | ----------- |
| 3.1  | [SRIS-P1-DATA-001](../wave-3-detailed-design/SRIS-P1-DATA-001_DataDesignDocument.md)                       | Data Design Document                          | P0  | UNBLOCK | Not Started |
| 3.2  | [SRIS-P1-DATA-002](../wave-3-detailed-design/SRIS-P1-DATA-002_LogicalDataModelPerService.md)               | Logical Data Model (per service)              | P0  | UNBLOCK | Not Started |
| 3.3  | [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)           | Physical Database Schema Document             | P0  | UNBLOCK | Not Started |
| 3.4  | [SRIS-P1-DATA-004](../wave-3-detailed-design/SRIS-P1-DATA-004_DataDictionary.md)                           | Data Dictionary                               | P0  | UNBLOCK | Not Started |
| 3.5  | [SRIS-P1-DATA-005](../wave-3-detailed-design/SRIS-P1-DATA-005_PrimaryKeyForeignKeyMap.md)                  | Primary Key / Foreign Key Map                 | P0  | UNBLOCK | Not Started |
| 3.6  | [SRIS-P1-DATA-006](../wave-3-detailed-design/SRIS-P1-DATA-006_IndexAndConstraintSpecification.md)          | Index and Constraint Specification            | P1  | FOLLOW  | Not Started |
| 3.7  | [SRIS-P1-DATA-007](../wave-3-detailed-design/SRIS-P1-DATA-007_DataOwnershipMatrix.md)                      | Data Ownership Matrix                         | P1  | FOLLOW  | Not Started |
| 3.8  | [SRIS-P1-DATA-008](../wave-3-detailed-design/SRIS-P1-DATA-008_HighConcurrencySegmentInventoryDataModel.md) | High-Concurrency Segment Inventory Data Model | P0  | UNBLOCK | Not Started |
| 3.9  | [SRIS-P1-DATA-009](../wave-3-detailed-design/SRIS-P1-DATA-009_SeatMatrixGenerationDesign.md)               | Seat Matrix Generation Design                 | P1  | FOLLOW  | Not Started |
| 3.10 | [SRIS-P1-DATA-010](../wave-3-detailed-design/SRIS-P1-DATA-010_DataMigrationStrategy.md)                    | Data Migration Strategy                       | P2  | FOLLOW  | Not Started |
| 3.11 | [SRIS-P1-DATA-011](../wave-3-detailed-design/SRIS-P1-DATA-011_DataRetentionAndArchivalPolicy.md)           | Data Retention and Archival Policy            | P2  | FOLLOW  | Not Started |
| 3.12 | [SRIS-P1-DATA-012](../wave-3-detailed-design/SRIS-P1-DATA-012_SeedDataAndReferenceDataSpecification.md)    | Seed Data and Reference Data Specification    | P2  | FOLLOW  | Not Started |
| 3.13 | [SRIS-P1-DATA-013](../wave-3-detailed-design/SRIS-P1-DATA-013_DatabaseNamingConventions.md)                | Database Naming Conventions                   | P1  | FOLLOW  | Not Started |

#### Group 3B: API Design (13)

| Seq  | Document ID                                                                                            | Title                                      | Pri | Tag     | Status      |
| ---- | ------------------------------------------------------------------------------------------------------ | ------------------------------------------ | --- | ------- | ----------- |
| 3.14 | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)             | API Contract Document (OpenAPI)            | P0  | UNBLOCK | Not Started |
| 3.15 | [SRIS-P1-API-002](../wave-3-detailed-design/SRIS-P1-API-002_APIRequestResponseExamples.md)             | API Request / Response Examples            | P0  | UNBLOCK | Not Started |
| 3.16 | [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md)            | Event Schema Document (AsyncAPI)           | P0  | UNBLOCK | Not Started |
| 3.17 | [SRIS-P1-API-004](../wave-3-detailed-design/SRIS-P1-API-004_IntegrationDesignDocument.md)              | Integration Design Document                | P0  | UNBLOCK | Not Started |
| 3.18 | [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md) | Idempotency and Retry Policy Specification | P0  | UNBLOCK | Not Started |
| 3.19 | [SRIS-P1-API-006](../wave-3-detailed-design/SRIS-P1-API-006_APIErrorCodeCatalog.md)                    | API Error Code Catalog                     | P1  | FOLLOW  | Not Started |
| 3.20 | [SRIS-P1-API-007](../wave-3-detailed-design/SRIS-P1-API-007_APIAuthenticationAndHeaderRules.md)        | API Authentication and Header Rules        | P1  | FOLLOW  | Not Started |
| 3.21 | [SRIS-P1-API-008](../wave-3-detailed-design/SRIS-P1-API-008_APIRateLimitingAndThrottlingRules.md)      | API Rate Limiting and Throttling Rules     | P2  | FOLLOW  | Not Started |
| 3.22 | [SRIS-P1-API-009](../wave-3-detailed-design/SRIS-P1-API-009_EventCatalog.md)                           | Event Catalog                              | P1  | FOLLOW  | Not Started |
| 3.23 | [SRIS-P1-API-010](../wave-3-detailed-design/SRIS-P1-API-010_APIGatewayConfigurationDocument.md)        | API Gateway Configuration Document         | P1  | FOLLOW  | Not Started |
| 3.24 | [SRIS-P1-API-011](../wave-3-detailed-design/SRIS-P1-API-011_PaymentGatewayIntegrationDesignMock.md)    | Payment Gateway Integration Design (Mock)  | P1  | FOLLOW  | Not Started |
| 3.25 | [SRIS-P1-API-012](../wave-3-detailed-design/SRIS-P1-API-012_NotificationIntegrationDesign.md)          | Notification Integration Design            | P1  | FOLLOW  | Not Started |
| 3.26 | [SRIS-P1-API-013](../wave-3-detailed-design/SRIS-P1-API-013_APIVersioningAndDeprecationPolicy.md)      | API Versioning and Deprecation Policy      | P2  | FOLLOW  | Not Started |

#### Group 3C: UI Design (12)

| Seq  | Document ID                                                                                             | Title                                        | Pri | Tag     | Status      |
| ---- | ------------------------------------------------------------------------------------------------------- | -------------------------------------------- | --- | ------- | ----------- |
| 3.27 | [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md)                  | UI/UX Requirements Document                  | P0  | UNBLOCK | Not Started |
| 3.28 | [SRIS-P1-UI-002](../wave-3-detailed-design/SRIS-P1-UI-002_ScreenInventoryAndNavigationMap.md)           | Screen Inventory and Navigation Map          | P0  | UNBLOCK | Not Started |
| 3.29 | [SRIS-P1-UI-003](../wave-3-detailed-design/SRIS-P1-UI-003_WireframesCustomerFlow.md)                    | Wireframes (Customer Flow)                   | P0  | UNBLOCK | Not Started |
| 3.30 | [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md)               | Wireframes (Employee/Admin Flow)             | P0  | UNBLOCK | Not Started |
| 3.31 | [SRIS-P1-UI-005](../wave-3-detailed-design/SRIS-P1-UI-005_UIComponentLibrarySpecification.md)           | UI Component Library Specification           | P1  | FOLLOW  | Not Started |
| 3.32 | [SRIS-P1-UI-006](../wave-3-detailed-design/SRIS-P1-UI-006_FormFieldSpecification.md)                    | Form Field Specification                     | P1  | FOLLOW  | Not Started |
| 3.33 | [SRIS-P1-UI-007](../wave-3-detailed-design/SRIS-P1-UI-007_UIStateManagementDesign.md)                   | UI State Management Design                   | P1  | FOLLOW  | Not Started |
| 3.34 | [SRIS-P1-UI-008](../wave-3-detailed-design/SRIS-P1-UI-008_UIErrorAndNotificationDisplayRules.md)        | UI Error and Notification Display Rules      | P1  | FOLLOW  | Not Started |
| 3.35 | [SRIS-P1-UI-009](../wave-3-detailed-design/SRIS-P1-UI-009_UIAccessibilityGuidelines.md)                 | UI Accessibility Guidelines                  | P2  | FOLLOW  | Not Started |
| 3.36 | [SRIS-P1-UI-010](../wave-3-detailed-design/SRIS-P1-UI-010_UIThemingAndBrandingGuide.md)                 | UI Theming and Branding Guide                | P2  | FOLLOW  | Not Started |
| 3.37 | [SRIS-P1-UI-011](../wave-3-detailed-design/SRIS-P1-UI-011_FrontendRoutingAndPageMap.md)                 | Frontend Routing and Page Map                | P1  | FOLLOW  | Not Started |
| 3.38 | [SRIS-P1-UI-012](../wave-3-detailed-design/SRIS-P1-UI-012_InternationalizationAndLocalizationDesign.md) | Internationalization and Localization Design | P2  | FOLLOW  | Not Started |

#### Group 3D: Security Design (12)

| Seq  | Document ID                                                                                            | Title                                          | Pri | Tag     | Status      |
| ---- | ------------------------------------------------------------------------------------------------------ | ---------------------------------------------- | --- | ------- | ----------- |
| 3.39 | [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)   | Authentication and Authorization Design        | P1  | FOLLOW  | Not Started |
| 3.40 | [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md)                             | RBAC Matrix                                    | P1  | FOLLOW  | Not Started |
| 3.41 | [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)                | JWT Token Design and Claims                    | P1  | FOLLOW  | Not Started |
| 3.42 | [SRIS-P1-SEC-004](../wave-3-detailed-design/SRIS-P1-SEC-004_ThreatModel.md)                            | Threat Model                                   | P1  | FOLLOW  | Not Started |
| 3.43 | [SRIS-P1-SEC-005](../wave-3-detailed-design/SRIS-P1-SEC-005_DataPrivacyAndComplianceDocument.md)       | Data Privacy and Compliance Document           | P1  | FOLLOW  | Not Started |
| 3.44 | [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md) | DPDP Act Compliance Framework (Phase 1 scoped) | P0  | UNBLOCK | Not Started |
| 3.45 | [SRIS-P1-SEC-007](../wave-3-detailed-design/SRIS-P1-SEC-007_ConsentManagementDataModelPhase1Scoped.md) | Consent Management Data Model (Phase 1 scoped) | P0  | UNBLOCK | Not Started |
| 3.46 | [SRIS-P1-SEC-008](../wave-3-detailed-design/SRIS-P1-SEC-008_SecretsManagementPlan.md)                  | Secrets Management Plan                        | P1  | FOLLOW  | Not Started |
| 3.47 | [SRIS-P1-SEC-009](../wave-3-detailed-design/SRIS-P1-SEC-009_PasswordAndCredentialPolicy.md)            | Password and Credential Policy                 | P2  | FOLLOW  | Not Started |
| 3.48 | [SRIS-P1-SEC-010](../wave-3-detailed-design/SRIS-P1-SEC-010_SecurityIncidentResponsePlan.md)           | Security Incident Response Plan                | P1  | FOLLOW  | Not Started |
| 3.49 | [SRIS-P1-SEC-012](../wave-3-detailed-design/SRIS-P1-SEC-012_DataClassificationRegister.md)             | Data Classification Register                   | P0  | UNBLOCK | Not Started |
| 3.50 | [SRIS-P1-SEC-013](../wave-3-detailed-design/SRIS-P1-SEC-013_SecureCodingStandards.md)                  | Secure Coding Standards                        | P0  | UNBLOCK | Not Started |

### 3.7 Wave 4: Testing

Folder: `wave-4-testing`. Documents: 16.

| Seq  | Document ID                                                                                     | Title                                     | Pri | Tag     | Status      |
| ---- | ----------------------------------------------------------------------------------------------- | ----------------------------------------- | --- | ------- | ----------- |
| 4.1  | [SRIS-P1-TEST-001](../wave-4-testing/SRIS-P1-TEST-001_TestStrategyDocument.md)                  | Test Strategy Document                    | P0  | UNBLOCK | Not Started |
| 4.2  | [SRIS-P1-TEST-002](../wave-4-testing/SRIS-P1-TEST-002_TestPlan.md)                              | Test Plan                                 | P0  | UNBLOCK | Not Started |
| 4.3  | [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)                   | Test Cases (Functional)                   | P0  | UNBLOCK | Not Started |
| 4.4  | [SRIS-P1-TEST-004](../wave-4-testing/SRIS-P1-TEST-004_ConsumerDrivenContractTestingStrategy.md) | Consumer-Driven Contract Testing Strategy | P1  | UNBLOCK | Not Started |
| 4.5  | [SRIS-P1-TEST-005](../wave-4-testing/SRIS-P1-TEST-005_TestCasesAPI.md)                          | Test Cases (API)                          | P1  | FOLLOW  | Not Started |
| 4.6  | [SRIS-P1-TEST-006](../wave-4-testing/SRIS-P1-TEST-006_TestCasesDatabase.md)                     | Test Cases (Database)                     | P1  | FOLLOW  | Not Started |
| 4.7  | [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md)                           | Test Cases (UI)                           | P1  | FOLLOW  | Not Started |
| 4.8  | [SRIS-P1-TEST-008](../wave-4-testing/SRIS-P1-TEST-008_PerformanceTestPlan.md)                   | Performance Test Plan                     | P1  | FOLLOW  | Not Started |
| 4.9  | [SRIS-P1-TEST-009](../wave-4-testing/SRIS-P1-TEST-009_LoadTestPlan.md)                          | Load Test Plan                            | P1  | FOLLOW  | Not Started |
| 4.10 | [SRIS-P1-TEST-010](../wave-4-testing/SRIS-P1-TEST-010_IntegrationTestPlan.md)                   | Integration Test Plan                     | P1  | FOLLOW  | Not Started |
| 4.11 | [SRIS-P1-TEST-011](../wave-4-testing/SRIS-P1-TEST-011_UserAcceptanceTestUATPlan.md)             | User Acceptance Test (UAT) Plan           | P1  | FOLLOW  | Not Started |
| 4.12 | [SRIS-P1-TEST-012](../wave-4-testing/SRIS-P1-TEST-012_TestDataManagementPlan.md)                | Test Data Management Plan                 | P2  | FOLLOW  | Not Started |
| 4.13 | [SRIS-P1-TEST-013](../wave-4-testing/SRIS-P1-TEST-013_DefectManagementProcess.md)               | Defect Management Process                 | P2  | FOLLOW  | Not Started |
| 4.14 | [SRIS-P1-TEST-014](../wave-4-testing/SRIS-P1-TEST-014_TestSummaryReportTemplate.md)             | Test Summary Report Template              | P2  | FOLLOW  | Not Started |
| 4.15 | [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md)                     | Security Testing Plan                     | P1  | FOLLOW  | Not Started |
| 4.16 | [SRIS-P1-TEST-016](../wave-4-testing/SRIS-P1-TEST-016_PerformanceBenchmarkReport.md)            | Performance Benchmark Report              | P1  | FOLLOW  | Not Started |

### 3.8 Wave 5: DevOps and Operations

Folder: `wave-5-devops-operations`. Documents: 21.

| Seq  | Document ID                                                                                                     | Title                                             | Pri | Tag     | Status      |
| ---- | --------------------------------------------------------------------------------------------------------------- | ------------------------------------------------- | --- | ------- | ----------- |
| 5.1  | [SRIS-P1-INF-001](../wave-5-devops-operations/SRIS-P1-INF-001_InfrastructureAndTechnologyDocument.md)           | Infrastructure and Technology Document            | P0  | UNBLOCK | Not Started |
| 5.2  | [SRIS-P1-INF-002](../wave-5-devops-operations/SRIS-P1-INF-002_EnvironmentStrategyDocument.md)                   | Environment Strategy Document                     | P0  | UNBLOCK | Not Started |
| 5.3  | [SRIS-P1-INF-003](../wave-5-devops-operations/SRIS-P1-INF-003_CICDPipelineDesign.md)                            | CI/CD Pipeline Design                             | P0  | UNBLOCK | Not Started |
| 5.4  | [SRIS-P1-INF-004](../wave-5-devops-operations/SRIS-P1-INF-004_PactBrokerAndCICDPipelineIntegration.md)          | Pact Broker and CI/CD Pipeline Integration        | P1  | UNBLOCK | Not Started |
| 5.5  | [SRIS-P1-INF-005](../wave-5-devops-operations/SRIS-P1-INF-005_ConfigurationManagementPlan.md)                   | Configuration Management Plan                     | P1  | FOLLOW  | Not Started |
| 5.6  | [SRIS-P1-INF-006](../wave-5-devops-operations/SRIS-P1-INF-006_ContainerizationAndImageBuildGuide.md)            | Containerization and Image Build Guide            | P1  | FOLLOW  | Not Started |
| 5.7  | [SRIS-P1-INF-007](../wave-5-devops-operations/SRIS-P1-INF-007_RepositoryStructureAndNaming.md)                  | Repository Structure and Naming                   | P1  | FOLLOW  | Not Started |
| 5.8  | [SRIS-P1-INF-008](../wave-5-devops-operations/SRIS-P1-INF-008_BackupAndRestoreProcedure.md)                     | Backup and Restore Procedure                      | P1  | FOLLOW  | Not Started |
| 5.9  | [SRIS-P1-INF-009](../wave-5-devops-operations/SRIS-P1-INF-009_DisasterRecoveryPlan.md)                          | Disaster Recovery Plan                            | P1  | FOLLOW  | Not Started |
| 5.10 | [SRIS-P1-INF-010](../wave-5-devops-operations/SRIS-P1-INF-010_CapacityPlanningDocument.md)                      | Capacity Planning Document                        | P2  | FOLLOW  | Not Started |
| 5.11 | [SRIS-P1-INF-011](../wave-5-devops-operations/SRIS-P1-INF-011_EnvironmentVariablesAndConfigurationReference.md) | Environment Variables and Configuration Reference | P0  | UNBLOCK | Not Started |
| 5.12 | [SRIS-P1-OPS-001](../wave-5-devops-operations/SRIS-P1-OPS-001_DeploymentGuide.md)                               | Deployment Guide                                  | P1  | FOLLOW  | Not Started |
| 5.13 | [SRIS-P1-OPS-002](../wave-5-devops-operations/SRIS-P1-OPS-002_OperationsManualRunbook.md)                       | Operations Manual (Runbook)                       | P1  | FOLLOW  | Not Started |
| 5.14 | [SRIS-P1-OPS-003](../wave-5-devops-operations/SRIS-P1-OPS-003_MonitoringAndAlertingGuide.md)                    | Monitoring and Alerting Guide                     | P1  | FOLLOW  | Not Started |
| 5.15 | [SRIS-P1-OPS-004](../wave-5-devops-operations/SRIS-P1-OPS-004_LoggingGuide.md)                                  | Logging Guide                                     | P1  | FOLLOW  | Not Started |
| 5.16 | [SRIS-P1-OPS-005](../wave-5-devops-operations/SRIS-P1-OPS-005_SLODocument.md)                                   | SLO Document                                      | P2  | FOLLOW  | Not Started |
| 5.17 | [SRIS-P1-OPS-006](../wave-5-devops-operations/SRIS-P1-OPS-006_IncidentManagementProcedure.md)                   | Incident Management Procedure                     | P2  | FOLLOW  | Not Started |
| 5.18 | [SRIS-P1-OPS-007](../wave-5-devops-operations/SRIS-P1-OPS-007_ReleaseManagementPlan.md)                         | Release Management Plan                           | P1  | FOLLOW  | Not Started |
| 5.19 | [SRIS-P1-OPS-008](../wave-5-devops-operations/SRIS-P1-OPS-008_BackupAndRestoreRunbook.md)                       | Backup and Restore Runbook                        | P2  | FOLLOW  | Not Started |
| 5.20 | [SRIS-P1-OPS-009](../wave-5-devops-operations/SRIS-P1-OPS-009_KnownIssuesAndLimitationsRegister.md)             | Known Issues and Limitations Register             | P1  | FOLLOW  | Not Started |
| 5.21 | [SRIS-P1-OPS-010](../wave-5-devops-operations/SRIS-P1-OPS-010_ReleaseNotesAndChangelog.md)                      | Release Notes and Changelog                       | P1  | FOLLOW  | Not Started |

### 3.9 Wave 6: Developer Standards

Folder: `wave-6-developer-standards`. Documents: 13.

| Seq  | Document ID                                                                                               | Title                                      | Pri | Tag     | Status      |
| ---- | --------------------------------------------------------------------------------------------------------- | ------------------------------------------ | --- | ------- | ----------- |
| 6.1  | [SRIS-P1-DEV-003](../wave-6-developer-standards/SRIS-P1-DEV-003_DevelopmentEnvironmentSetupGuide.md)      | Development Environment Setup Guide        | P0  | UNBLOCK | Not Started |
| 6.2  | [SRIS-P1-DEV-004](../wave-6-developer-standards/SRIS-P1-DEV-004_CodingStandardsAndConventions.md)         | Coding Standards and Conventions           | P0  | UNBLOCK | Not Started |
| 6.3  | [SRIS-P1-DEV-005](../wave-6-developer-standards/SRIS-P1-DEV-005_GitAndBranchingStrategy.md)               | Git and Branching Strategy                 | P0  | UNBLOCK | Not Started |
| 6.4  | [SRIS-P1-DEV-006](../wave-6-developer-standards/SRIS-P1-DEV-006_DefinitionOfDoneDoD.md)                   | Definition of Done (DoD)                   | P1  | FOLLOW  | Not Started |
| 6.5  | [SRIS-P1-DEV-007](../wave-6-developer-standards/SRIS-P1-DEV-007_DefinitionOfReadyDoR.md)                  | Definition of Ready (DoR)                  | P1  | FOLLOW  | Not Started |
| 6.6  | [SRIS-P1-DEV-008](../wave-6-developer-standards/SRIS-P1-DEV-008_CodeReviewChecklist.md)                   | Code Review Checklist                      | P1  | FOLLOW  | Not Started |
| 6.7  | [SRIS-P1-DEV-009](../wave-6-developer-standards/SRIS-P1-DEV-009_FrontendCodingStandards.md)               | Frontend Coding Standards                  | P1  | FOLLOW  | Not Started |
| 6.8  | [SRIS-P1-DEV-010](../wave-6-developer-standards/SRIS-P1-DEV-010_BackendCodingStandards.md)                | Backend Coding Standards                   | P1  | FOLLOW  | Not Started |
| 6.9  | [SRIS-P1-DEV-011](../wave-6-developer-standards/SRIS-P1-DEV-011_DatabaseCodingStandards.md)               | Database Coding Standards                  | P1  | FOLLOW  | Not Started |
| 6.10 | [SRIS-P1-DEV-012](../wave-6-developer-standards/SRIS-P1-DEV-012_NewContributorOnboardingGuide.md)         | New Contributor Onboarding Guide           | P2  | FOLLOW  | Not Started |
| 6.11 | [SRIS-P1-DEV-014](../wave-6-developer-standards/SRIS-P1-DEV-014_CommentAndInlineDocumentationStandard.md) | Comment and Inline Documentation Standard  | P0  | UNBLOCK | Not Started |
| 6.12 | [SRIS-P1-DEV-015](../wave-6-developer-standards/SRIS-P1-DEV-015_CommitMessageAndPullRequestConvention.md) | Commit Message and Pull Request Convention | P0  | UNBLOCK | Not Started |
| 6.13 | [SRIS-P1-DEV-016](../wave-6-developer-standards/SRIS-P1-DEV-016_DeveloperCommunicationProtocol.md)        | Developer Communication Protocol           | P1  | UNBLOCK | Not Started |

### 3.10 Wave 7: Project Tracking

Folder: `wave-7-project-tracking`. Documents: 17.

| Seq  | Document ID                                                                               | Title                          | Pri | Tag    | Status      |
| ---- | ----------------------------------------------------------------------------------------- | ------------------------------ | --- | ------ | ----------- |
| 7.1  | [SRIS-P1-DEV-013](../wave-7-project-tracking/SRIS-P1-DEV-013_SkillMatrix.md)              | Skill Matrix                   | P2  | FOLLOW | Not Started |
| 7.2  | [SRIS-P1-PM-001](../wave-7-project-tracking/SRIS-P1-PM-001_ProjectPlanTimeline.md)        | Project Plan / Timeline        | P1  | FOLLOW | Not Started |
| 7.3  | [SRIS-P1-PM-002](../wave-7-project-tracking/SRIS-P1-PM-002_MilestoneTracker.md)           | Milestone Tracker              | P1  | FOLLOW | Not Started |
| 7.4  | [SRIS-P1-PM-003](../wave-7-project-tracking/SRIS-P1-PM-003_SprintIterationPlan.md)        | Sprint / Iteration Plan        | P1  | FOLLOW | Not Started |
| 7.5  | [SRIS-P1-PM-004](../wave-7-project-tracking/SRIS-P1-PM-004_ProgressReportTemplate.md)     | Progress Report Template       | P2  | FOLLOW | Not Started |
| 7.6  | [SRIS-P1-PM-005](../wave-7-project-tracking/SRIS-P1-PM-005_MeetingNotesAndDecisionLog.md) | Meeting Notes and Decision Log | P1  | FOLLOW | Not Started |
| 7.7  | [SRIS-P1-PM-006](../wave-7-project-tracking/SRIS-P1-PM-006_IssueLog.md)                   | Issue Log                      | P2  | FOLLOW | Not Started |
| 7.8  | [SRIS-P1-PM-007](../wave-7-project-tracking/SRIS-P1-PM-007_ChangeRequestLog.md)           | Change Request Log             | P2  | FOLLOW | Not Started |
| 7.9  | [SRIS-P1-PM-008](../wave-7-project-tracking/SRIS-P1-PM-008_RetrospectiveNotesSprint1.md)  | Retrospective Notes — Sprint 1 | P2  | FOLLOW | Not Started |
| 7.10 | [SRIS-P1-PM-009](../wave-7-project-tracking/SRIS-P1-PM-009_RetrospectiveNotesSprint2.md)  | Retrospective Notes — Sprint 2 | P2  | FOLLOW | Not Started |
| 7.11 | [SRIS-P1-PM-010](../wave-7-project-tracking/SRIS-P1-PM-010_RetrospectiveNotesSprint3.md)  | Retrospective Notes — Sprint 3 | P2  | FOLLOW | Not Started |
| 7.12 | [SRIS-P1-PM-011](../wave-7-project-tracking/SRIS-P1-PM-011_RetrospectiveNotesSprint4.md)  | Retrospective Notes — Sprint 4 | P2  | FOLLOW | Not Started |
| 7.13 | [SRIS-P1-PM-012](../wave-7-project-tracking/SRIS-P1-PM-012_RetrospectiveNotesSprint5.md)  | Retrospective Notes — Sprint 5 | P2  | FOLLOW | Not Started |
| 7.14 | [SRIS-P1-PM-013](../wave-7-project-tracking/SRIS-P1-PM-013_RetrospectiveNotesSprint6.md)  | Retrospective Notes — Sprint 6 | P2  | FOLLOW | Not Started |
| 7.15 | [SRIS-P1-PM-014](../wave-7-project-tracking/SRIS-P1-PM-014_SprintReviewNotesSprint1.md)   | Sprint Review Notes — Sprint 1 | P2  | FOLLOW | Not Started |
| 7.16 | [SRIS-P1-PM-015](../wave-7-project-tracking/SRIS-P1-PM-015_SprintReviewNotesSprint2.md)   | Sprint Review Notes — Sprint 2 | P2  | FOLLOW | Not Started |
| 7.17 | [SRIS-P1-PM-016](../wave-7-project-tracking/SRIS-P1-PM-016_SprintReviewNotesSprint3.md)   | Sprint Review Notes — Sprint 3 | P2  | FOLLOW | Not Started |

### 3.11 Wave 8: User and Support

Folder: `wave-8-user-support`. Documents: 8.

| Seq | Document ID                                                                                           | Title                                        | Pri | Tag    | Status      |
| --- | ----------------------------------------------------------------------------------------------------- | -------------------------------------------- | --- | ------ | ----------- |
| 8.1 | [SRIS-P1-USR-001](../wave-8-user-support/SRIS-P1-USR-001_CustomerUserManual.md)                       | Customer User Manual                         | P1  | FOLLOW | Not Started |
| 8.2 | [SRIS-P1-USR-002](../wave-8-user-support/SRIS-P1-USR-002_EmployeeAdminManual.md)                      | Employee Admin Manual                        | P1  | FOLLOW | Not Started |
| 8.3 | [SRIS-P1-USR-003](../wave-8-user-support/SRIS-P1-USR-003_APIDocumentationForConsumers.md)             | API Documentation for Consumers              | P2  | FOLLOW | Not Started |
| 8.4 | [SRIS-P1-USR-004](../wave-8-user-support/SRIS-P1-USR-004_FAQDocument.md)                              | FAQ Document                                 | P2  | FOLLOW | Not Started |
| 8.5 | [SRIS-P1-USR-005](../wave-8-user-support/SRIS-P1-USR-005_SupportAndMaintenanceGuide.md)               | Support and Maintenance Guide                | P2  | FOLLOW | Not Started |
| 8.6 | [SRIS-P1-USR-006](../wave-8-user-support/SRIS-P1-USR-006_TrainingMaterial.md)                         | Training Material                            | P3  | FOLLOW | Not Started |
| 8.7 | [SRIS-P1-USR-007](../wave-8-user-support/SRIS-P1-USR-007_DemoScenariosAndWalkthroughScript.md)        | Demo Scenarios and Walkthrough Script        | P1  | FOLLOW | Not Started |
| 8.8 | [SRIS-P1-USR-008](../wave-8-user-support/SRIS-P1-USR-008_InterviewAndPresentationPreparationGuide.md) | Interview and Presentation Preparation Guide | P2  | FOLLOW | Not Started |

### 3.12 Wave 9: Supporting Artifacts

Folder: `wave-9-supporting-artifacts`. Documents: 2.

| Seq | Document ID                                                                                                        | Title                                       | Pri | Tag    | Status      |
| --- | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------- | --- | ------ | ----------- |
| 9.1 | [SRIS-P1-NFR-HOLD-001](../wave-9-supporting-artifacts/SRIS-P1-NFR-HOLD-001_LoadModelAndResourceFitCheckHolding.md) | Load Model and Resource Fit Check (Holding) | —   | HOLD   | Not Started |
| 9.2 | [SRIS-P1-NOTES-AI-001](../wave-9-supporting-artifacts/SRIS-P1-NOTES-AI-001_AIConsultantLog.md)                     | AI Consultant Log                           | P2  | FOLLOW | Not Started |

---

## 4. Navigation by Role

Each role has a reading path. Read the documents in the order shown.

### 4.1 Database Developer

Designs and implements the data stores and schemas.

1. [SRIS-P1-REQ-001](../wave-1-requirements/SRIS-P1-REQ-001_GlossaryAndDomainDictionary.md) — Glossary of domain terms
2. [SRIS-P1-ARCH-005](../wave-2-architecture/SRIS-P1-ARCH-005_DomainModelDocument.md) — Domain model
3. [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md) — Concurrency and locking strategy
4. [SRIS-P1-DATA-001](../wave-3-detailed-design/SRIS-P1-DATA-001_DataDesignDocument.md) — Data design overview
5. [SRIS-P1-DATA-002](../wave-3-detailed-design/SRIS-P1-DATA-002_LogicalDataModelPerService.md) — Logical data model
6. [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md) — Physical schema
7. [SRIS-P1-DATA-004](../wave-3-detailed-design/SRIS-P1-DATA-004_DataDictionary.md) — Data dictionary
8. [SRIS-P1-DATA-005](../wave-3-detailed-design/SRIS-P1-DATA-005_PrimaryKeyForeignKeyMap.md) — Primary key and foreign key map
9. [SRIS-P1-DATA-006](../wave-3-detailed-design/SRIS-P1-DATA-006_IndexAndConstraintSpecification.md) — Indexes and constraints
10. [SRIS-P1-DATA-008](../wave-3-detailed-design/SRIS-P1-DATA-008_HighConcurrencySegmentInventoryDataModel.md) — Segment-based inventory data model
11. [SRIS-P1-DATA-013](../wave-3-detailed-design/SRIS-P1-DATA-013_DatabaseNamingConventions.md) — Naming conventions
12. [SRIS-P1-DEV-011](../wave-6-developer-standards/SRIS-P1-DEV-011_DatabaseCodingStandards.md) — Database coding standards

### 4.2 Backend Developer

Implements the microservices, APIs, and event handling.

1. [SRIS-P1-REQ-004](../wave-1-requirements/SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software requirements specification
2. [SRIS-P1-REQ-007](../wave-1-requirements/SRIS-P1-REQ-007_DomainRulesFareCalculation.md) — Fare calculation rules
3. [SRIS-P1-REQ-008](../wave-1-requirements/SRIS-P1-REQ-008_DomainRulesTicketing.md) — Ticketing rules
4. [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices identification
5. [SRIS-P1-ARCH-003](../wave-2-architecture/SRIS-P1-ARCH-003_SystemArchitectureDocument.md) — System architecture
6. [SRIS-P1-ARCH-009](../wave-2-architecture/SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md) — Service interaction and communication
7. [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md) — Distributed transaction and saga pattern
8. [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md) — API contract
9. [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md) — Event schemas
10. [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md) — Idempotency and retry rules
11. [SRIS-P1-DEV-010](../wave-6-developer-standards/SRIS-P1-DEV-010_BackendCodingStandards.md) — Backend coding standards
12. [SRIS-P1-TEST-004](../wave-4-testing/SRIS-P1-TEST-004_ConsumerDrivenContractTestingStrategy.md) — Consumer-driven contract testing

### 4.3 Frontend Developer

Implements the customer and employee interfaces.

1. [SRIS-P1-REQ-006](../wave-1-requirements/SRIS-P1-REQ-006_UserStoriesAndUseCases.md) — User stories and use cases
2. [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md) — UI/UX requirements
3. [SRIS-P1-UI-002](../wave-3-detailed-design/SRIS-P1-UI-002_ScreenInventoryAndNavigationMap.md) — Screen inventory and navigation
4. [SRIS-P1-UI-003](../wave-3-detailed-design/SRIS-P1-UI-003_WireframesCustomerFlow.md) — Customer wireframes
5. [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md) — Employee and admin wireframes
6. [SRIS-P1-UI-005](../wave-3-detailed-design/SRIS-P1-UI-005_UIComponentLibrarySpecification.md) — Component library
7. [SRIS-P1-UI-007](../wave-3-detailed-design/SRIS-P1-UI-007_UIStateManagementDesign.md) — State management
8. [SRIS-P1-UI-011](../wave-3-detailed-design/SRIS-P1-UI-011_FrontendRoutingAndPageMap.md) — Frontend routing and page map
9. [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md) — API contract
10. [SRIS-P1-DEV-009](../wave-6-developer-standards/SRIS-P1-DEV-009_FrontendCodingStandards.md) — Frontend coding standards

### 4.4 UI/UX Designer

Designs screens, flows, and interface standards.

1. [SRIS-P1-REQ-006](../wave-1-requirements/SRIS-P1-REQ-006_UserStoriesAndUseCases.md) — User stories and use cases
2. [SRIS-P1-REQ-015](../wave-1-requirements/SRIS-P1-REQ-015_AccessibilityRequirements.md) — Accessibility requirements
3. [SRIS-P1-UI-001](../wave-3-detailed-design/SRIS-P1-UI-001_UIUXRequirementsDocument.md) — UI/UX requirements
4. [SRIS-P1-UI-002](../wave-3-detailed-design/SRIS-P1-UI-002_ScreenInventoryAndNavigationMap.md) — Screen inventory and navigation
5. [SRIS-P1-UI-003](../wave-3-detailed-design/SRIS-P1-UI-003_WireframesCustomerFlow.md) — Customer wireframes
6. [SRIS-P1-UI-004](../wave-3-detailed-design/SRIS-P1-UI-004_WireframesEmployeeAdminFlow.md) — Employee and admin wireframes
7. [SRIS-P1-UI-006](../wave-3-detailed-design/SRIS-P1-UI-006_FormFieldSpecification.md) — Form fields
8. [SRIS-P1-UI-008](../wave-3-detailed-design/SRIS-P1-UI-008_UIErrorAndNotificationDisplayRules.md) — Error and notification display rules
9. [SRIS-P1-UI-009](../wave-3-detailed-design/SRIS-P1-UI-009_UIAccessibilityGuidelines.md) — Accessibility guidelines
10. [SRIS-P1-UI-010](../wave-3-detailed-design/SRIS-P1-UI-010_UIThemingAndBrandingGuide.md) — Theming and branding guide

### 4.5 Tester (QA)

Plans and runs functional, contract, and security tests.

1. [SRIS-P1-REQ-004](../wave-1-requirements/SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software requirements specification
2. [SRIS-P1-REQ-012](../wave-1-requirements/SRIS-P1-REQ-012_RequirementTraceabilityMatrixRTM.md) — Requirement traceability matrix
3. [SRIS-P1-TEST-001](../wave-4-testing/SRIS-P1-TEST-001_TestStrategyDocument.md) — Test strategy
4. [SRIS-P1-TEST-002](../wave-4-testing/SRIS-P1-TEST-002_TestPlan.md) — Test plan
5. [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md) — Functional test cases
6. [SRIS-P1-TEST-004](../wave-4-testing/SRIS-P1-TEST-004_ConsumerDrivenContractTestingStrategy.md) — Consumer-driven contract testing
7. [SRIS-P1-TEST-005](../wave-4-testing/SRIS-P1-TEST-005_TestCasesAPI.md) — API test cases
8. [SRIS-P1-TEST-006](../wave-4-testing/SRIS-P1-TEST-006_TestCasesDatabase.md) — Database test cases
9. [SRIS-P1-TEST-007](../wave-4-testing/SRIS-P1-TEST-007_TestCasesUI.md) — UI test cases
10. [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md) — Security testing plan
11. [SRIS-P1-TEST-013](../wave-4-testing/SRIS-P1-TEST-013_DefectManagementProcess.md) — Defect management

### 4.6 DevOps Engineer

Builds environments, pipelines, and deployment procedures.

1. [SRIS-P1-ARCH-008](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md) — Technology choices
2. [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md) — Observability and monitoring design
3. [SRIS-P1-INF-001](../wave-5-devops-operations/SRIS-P1-INF-001_InfrastructureAndTechnologyDocument.md) — Infrastructure and technology
4. [SRIS-P1-INF-002](../wave-5-devops-operations/SRIS-P1-INF-002_EnvironmentStrategyDocument.md) — Environment strategy
5. [SRIS-P1-INF-003](../wave-5-devops-operations/SRIS-P1-INF-003_CICDPipelineDesign.md) — CI/CD pipeline
6. [SRIS-P1-INF-006](../wave-5-devops-operations/SRIS-P1-INF-006_ContainerizationAndImageBuildGuide.md) — Containerisation and image build
7. [SRIS-P1-INF-011](../wave-5-devops-operations/SRIS-P1-INF-011_EnvironmentVariablesAndConfigurationReference.md) — Environment variables and configuration
8. [SRIS-P1-OPS-001](../wave-5-devops-operations/SRIS-P1-OPS-001_DeploymentGuide.md) — Deployment guide
9. [SRIS-P1-OPS-002](../wave-5-devops-operations/SRIS-P1-OPS-002_OperationsManualRunbook.md) — Operations runbook
10. [SRIS-P1-OPS-003](../wave-5-devops-operations/SRIS-P1-OPS-003_MonitoringAndAlertingGuide.md) — Monitoring and alerting
11. [SRIS-P1-OPS-004](../wave-5-devops-operations/SRIS-P1-OPS-004_LoggingGuide.md) — Logging guide
12. [SRIS-P1-OPS-009](../wave-5-devops-operations/SRIS-P1-OPS-009_KnownIssuesAndLimitationsRegister.md) — Known issues and limitations

### 4.7 Evaluator

Reviews the project against its requirements and design.

1. [SRIS-P1-GOV-005](./SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project vision and scope
2. [SRIS-P1-GOV-006](./SRIS-P1-GOV-006_ProjectCharter.md) — Project charter
3. [SRIS-P1-REQ-002](../wave-1-requirements/SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) — Business requirements
4. [SRIS-P1-REQ-004](../wave-1-requirements/SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md) — Software requirements specification
5. [SRIS-P1-REQ-005](../wave-1-requirements/SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md) — Non-functional requirements
6. [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices identification
7. [SRIS-P1-ARCH-003](../wave-2-architecture/SRIS-P1-ARCH-003_SystemArchitectureDocument.md) — System architecture
8. [SRIS-P1-TEST-001](../wave-4-testing/SRIS-P1-TEST-001_TestStrategyDocument.md) — Test strategy
9. [SRIS-P1-INF-001](../wave-5-devops-operations/SRIS-P1-INF-001_InfrastructureAndTechnologyDocument.md) — Infrastructure and technology
10. [SRIS-P1-USR-007](../wave-8-user-support/SRIS-P1-USR-007_DemoScenariosAndWalkthroughScript.md) — Demo scenarios and walkthrough script

---

## 5. Navigation by Topic

Find a topic in the first column. The second column links to the document that covers it.

| Topic                           | Document ID                                                                                                        | Notes                                             |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------- |
| Project identity and vision     | [SRIS-P1-GOV-005](./SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)                                              | Project Vision and Scope Document                 |
| Team and roles                  | [SRIS-P1-DEV-002](./SRIS-P1-DEV-002_RolesAndResponsibilitiesDocument.md)                                           | Roles and Responsibilities Document               |
| Business requirements           | [SRIS-P1-REQ-002](../wave-1-requirements/SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md)                       | Business Requirements Document (BRD)              |
| Functional requirements         | [SRIS-P1-REQ-004](../wave-1-requirements/SRIS-P1-REQ-004_SoftwareRequirementsSpecificationSRS.md)                  | Software Requirements Specification (SRS)         |
| Non-functional requirements     | [SRIS-P1-REQ-005](../wave-1-requirements/SRIS-P1-REQ-005_NonFunctionalRequirementsISO25010.md)                     | Non-Functional Requirements (ISO 25010)           |
| Fare calculation rules          | [SRIS-P1-REQ-007](../wave-1-requirements/SRIS-P1-REQ-007_DomainRulesFareCalculation.md)                            | Domain Rules: Fare Calculation                    |
| Ticketing rules                 | [SRIS-P1-REQ-008](../wave-1-requirements/SRIS-P1-REQ-008_DomainRulesTicketing.md)                                  | Domain Rules: Ticketing                           |
| Waitlist and cancellation rules | [SRIS-P1-REQ-009](../wave-1-requirements/SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)                    | Domain Rules: Waitlist and Cancellation           |
| Chart preparation rules         | [SRIS-P1-REQ-010](../wave-1-requirements/SRIS-P1-REQ-010_DomainRulesChartPreparation.md)                           | Domain Rules: Chart Preparation                   |
| Seat matrix and inventory rules | [SRIS-P1-REQ-011](../wave-1-requirements/SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)                     | Domain Rules: Seat Matrix and Inventory           |
| Service boundaries              | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)                         | Microservices Identification                      |
| System architecture             | [SRIS-P1-ARCH-003](../wave-2-architecture/SRIS-P1-ARCH-003_SystemArchitectureDocument.md)                          | System Architecture Document                      |
| Bounded contexts                | [SRIS-P1-ARCH-004](../wave-2-architecture/SRIS-P1-ARCH-004_BoundedContextMap.md)                                   | Bounded Context Map                               |
| Domain model                    | [SRIS-P1-ARCH-005](../wave-2-architecture/SRIS-P1-ARCH-005_DomainModelDocument.md)                                 | Domain Model Document                             |
| Technology choices              | [SRIS-P1-ARCH-008](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md)                                  | Technology Stack ADR                              |
| Sync and async APIs             | [SRIS-P1-ARCH-009](../wave-2-architecture/SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md)            | Service Interaction and Communication Design      |
| Distributed locking             | [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md)            | Distributed Concurrency and Locking Strategy      |
| Distributed transactions (Saga) | [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md)          | Distributed Transaction and Saga Pattern Design   |
| Database schema                 | [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)                   | Physical Database Schema Document                 |
| Column-level data dictionary    | [SRIS-P1-DATA-004](../wave-3-detailed-design/SRIS-P1-DATA-004_DataDictionary.md)                                   | Data Dictionary                                   |
| Segment-based seat inventory    | [SRIS-P1-DATA-008](../wave-3-detailed-design/SRIS-P1-DATA-008_HighConcurrencySegmentInventoryDataModel.md)         | High-Concurrency Segment Inventory Data Model     |
| REST API contracts              | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)                         | API Contract Document (OpenAPI)                   |
| Event contracts                 | [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md)                        | Event Schema Document (AsyncAPI)                  |
| Idempotency rules               | [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md)             | Idempotency and Retry Policy Specification        |
| Screen designs                  | [SRIS-P1-UI-002](../wave-3-detailed-design/SRIS-P1-UI-002_ScreenInventoryAndNavigationMap.md)                      | Screen Inventory and Navigation Map               |
| AuthN and AuthZ                 | [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)               | Authentication and Authorization Design           |
| Role-based access control       | [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md)                                         | RBAC Matrix                                       |
| DPDP compliance                 | [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md)             | DPDP Act Compliance Framework (Phase 1 scoped)    |
| Data classification             | [SRIS-P1-SEC-012](../wave-3-detailed-design/SRIS-P1-SEC-012_DataClassificationRegister.md)                         | Data Classification Register                      |
| Test strategy                   | [SRIS-P1-TEST-001](../wave-4-testing/SRIS-P1-TEST-001_TestStrategyDocument.md)                                     | Test Strategy Document                            |
| Contract testing                | [SRIS-P1-TEST-004](../wave-4-testing/SRIS-P1-TEST-004_ConsumerDrivenContractTestingStrategy.md)                    | Consumer-Driven Contract Testing Strategy         |
| Deployment and environments     | [SRIS-P1-INF-002](../wave-5-devops-operations/SRIS-P1-INF-002_EnvironmentStrategyDocument.md)                      | Environment Strategy Document                     |
| Environment variables           | [SRIS-P1-INF-011](../wave-5-devops-operations/SRIS-P1-INF-011_EnvironmentVariablesAndConfigurationReference.md)    | Environment Variables and Configuration Reference |
| Coding standards                | [SRIS-P1-DEV-004](../wave-6-developer-standards/SRIS-P1-DEV-004_CodingStandardsAndConventions.md)                  | Coding Standards and Conventions                  |
| Commit conventions              | [SRIS-P1-DEV-015](../wave-6-developer-standards/SRIS-P1-DEV-015_CommitMessageAndPullRequestConvention.md)          | Commit Message and Pull Request Convention        |
| Load and resource validation    | [SRIS-P1-NFR-HOLD-001](../wave-9-supporting-artifacts/SRIS-P1-NFR-HOLD-001_LoadModelAndResourceFitCheckHolding.md) | Load Model and Resource Fit Check (Holding)       |
| AI consultant provenance        | [SRIS-P1-NOTES-AI-001](../wave-9-supporting-artifacts/SRIS-P1-NOTES-AI-001_AIConsultantLog.md)                     | AI Consultant Log                                 |

---

## 6. Dependency Overview

This section shows the main dependencies between documents, one block per wave. An arrow means that the document on the left feeds the documents on the right.

```
Wave 0 Foundation
GOV-005 (Vision) -> all downstream
GOV-007 (Management) -> PM-001
DEV-001 (Developer) -> DEV-002
```

```
Wave 1 Requirements
REQ-001 (Glossary) -> REQ-002, REQ-004, REQ-007..011
REQ-002 (BRD) -> REQ-004 (SRS)
REQ-003 (Capabilities) -> ARCH-001
REQ-004 (SRS) -> REQ-005, REQ-006, domain rules
```

```
Wave 2 Architecture
ARCH-001 (Microservices) -> ARCH-003, ARCH-004, ARCH-005, ARCH-009
ARCH-005 (Domain Model) -> DATA-001, API-001, API-003
ARCH-008 (Tech Stack) -> INF-001, INF-002, INF-003
ARCH-014 (Concurrency) -> DATA-008
ARCH-015 (Saga) -> API-005
```

```
Wave 3 Detailed Design
DATA-001 (Data Design) -> DATA-002..005
API-001 (API Contract) -> API-002, API-006, UI-*
UI-002 (Screen Map) -> UI-003, UI-004
SEC-006 (DPDP) -> SEC-007, SEC-012
```

```
Wave 4 Testing
TEST-001 (Strategy) -> TEST-002, TEST-003..016
API-001 (API Contract) -> TEST-004
```

```
Wave 5 DevOps
INF-001 (Infrastructure) -> INF-002..011
INF-003 (CI/CD) -> INF-004
```

```
Wave 6 Developer Standards
DEV-003 (Env Setup) -> DEV-004..016
```

Full dependency metadata for every document will be produced in a future revision of this index once all upstream documents are final.

---

## 7. Document Conventions

### 7.1 File Naming

Source markdown naming:

```
<Document ID>_<DocumentNameInPascalCase>.md
```

Example:

```
SRIS-P1-ARCH-001_MicroservicesIdentification.md
```

PDF deliverable naming:

```
<Document ID>_<DocumentNameInPascalCase>_v<Version>.pdf
```

Example:

```
SRIS-P1-ARCH-001_MicroservicesIdentification_v1.0.pdf
```

The version is not included in the markdown filename. Git tracks history.

### 7.2 Folder Structure

```
docs
    |
    └───phase-1-foundation
        ├───wave-0-project-foundation
        │       SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md
        │       
        ├───wave-1-requirements
        ├───wave-2-architecture
        ├───wave-3-detailed-design
        ├───wave-4-testing
        ├───wave-5-devops-operations
        ├───wave-6-developer-standards
        ├───wave-7-project-tracking
        ├───wave-8-user-support
        └───wave-9-supporting-artifacts
```

### 7.3 Metadata Table Fields

| Field              | Purpose                                                       |
| ------------------ | ------------------------------------------------------------- |
| Title              | Full name of the document.                                    |
| Software           | Short name of the software the document belongs to.           |
| Software Full Form | Expanded name of the software.                                |
| Team Codename      | Codename of the team that produces the document.              |
| Document ID        | Stable identifier used in file names and cross-references.    |
| Task               | Task that the document fulfils.                               |
| Document Type      | Kind of document, for example Architecture Decision Document. |
| Milestone          | Project milestone that the document supports.                 |
| Classification     | Distribution level of the document.                           |
| Version            | Version of the document content.                              |
| Date               | Date of the current version.                                  |
| Author             | Person who wrote the document.                                |
| Status             | Current approval state of the document.                       |
| Approved By        | Person who approved the document.                             |
| Approval Date      | Date of approval.                                             |
| Supersedes         | Earlier document or version that this document replaces.      |
| Related Documents  | Pointer to the documents related to this one.                 |
| Affiliation        | Statement of independence from external organisations.        |

### 7.4 Status Values

| Value       | Meaning                                      |
| ----------- | -------------------------------------------- |
| Not Started | Work on the document has not begun.          |
| In Progress | The document is being written.               |
| In Review   | The document is written and awaiting review. |
| Completed   | The document is reviewed and approved.       |

### 7.5 Priority Values

| Value | Name     | Meaning                            |
| ----- | -------- | ---------------------------------- |
| P0    | Critical | Blocks other work. Complete first. |
| P1    | High     | Important for Phase 1 delivery.    |
| P2    | Medium   | Supports Phase 1 delivery.         |
| P3    | Low      | Can be deferred if time is short.  |

### 7.6 Tag Values

| Value   | Meaning                                                             |
| ------- | ------------------------------------------------------------------- |
| UNBLOCK | Must be complete before the dependent design or coding work starts. |
| FOLLOW  | Written during or after the work that it describes.                 |
| DONE    | Complete.                                                           |
| HOLD    | Kept as a working file until its target document exists.            |

---

## 8. Approval

| Role           | Name        | Decision | Date       |
| -------------- | ----------- | -------- | ---------- |
| Lead Architect | Koushal Jha | Approved | 2026-10-10 |

---

## Revision History

| Version | Date       | Author      | Change                         |
| ------- | ---------- | ----------- | ------------------------------ |
| 1.0     | 2026-10-10 | Koushal Jha | Approved for Phase 1 execution |

---

## Appendix A: Document ID Category Codes

| Code     | Category                    |
| -------- | --------------------------- |
| GOV      | Governance                  |
| DEV      | Developer                   |
| REQ      | Requirements                |
| ARCH     | Architecture                |
| DATA     | Data                        |
| API      | API                         |
| UI       | UI/UX                       |
| SEC      | Security                    |
| TEST     | Testing                     |
| INF      | Infrastructure              |
| OPS      | Operations                  |
| PM       | Project Management          |
| USR      | User Documentation          |
| NFR-HOLD | Non-Functional Holding File |
| NOTES-AI | AI Consultant Log           |

## Appendix B: Wave Definitions

| Wave | Name                  | Purpose                                                  |
| ---- | --------------------- | -------------------------------------------------------- |
| 0    | Project Foundation    | Governance, team identity, and document standards        |
| 1    | Requirements          | Business, functional, and non-functional requirements    |
| 2    | Architecture          | System structure, boundaries, and architecture decisions |
| 3    | Detailed Design       | Data, API, UI, and security design artifacts             |
| 4    | Testing               | Test strategy, plans, and test cases                     |
| 5    | DevOps and Operations | Infrastructure, environments, deployment, monitoring     |
| 6    | Developer Standards   | Coding standards, version control, process               |
| 7    | Project Tracking      | Living project management documents                      |
| 8    | User and Support      | Manuals and end-user support material                    |
| 9    | Supporting Artifacts  | Holding files and provenance                             |