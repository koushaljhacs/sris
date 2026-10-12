<div align="center">

![Wave](https://img.shields.io/badge/Wave-0-0550AE?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-GOV-6e7781?style=for-the-badge)

</div>

# Project Management Plan

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** 1.0 | **Date:** 2026-10-12 | **Document ID:** SRIS-P1-GOV-007

| Field | Value |
| ------ | ------ |
| Title | Project Management Plan |
| Software | SRIS |
| Software Full Form | Sarathi Railway Information System |
| Team Codename | Project Sarathi |
| Document ID | SRIS-P1-GOV-007 |
| Task | Define the schedule, workflow, and management of Phase 1 |
| Document Type | Governance Document |
| Milestone | Phase 1 Foundation |
| Classification | Internal |
| Version | 1.0 |
| Date | 2026-10-12 |
| Author | Koushal Jha, Lead Architect |
| Approved By | Koushal Jha, Lead Architect |
| Approval Date | 2026-10-12 |
| Supersedes | None (first version) |
| Related Documents | See Appendix B |
| Affiliation | Independent · Not affiliated with CRIS, IRCTC, or Indian Railways |

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [Development Methodology](#2-development-methodology)
3. [Schedule and Work Breakdown](#3-schedule-and-work-breakdown)
4. [Deliverables and Acceptance](#4-deliverables-and-acceptance)
5. [Branching and Versioning](#5-branching-and-versioning)
6. [Testing Approach](#6-testing-approach)
7. [Roles and Responsibilities](#7-roles-and-responsibilities)
8. [Reporting and CI/CD](#8-reporting-and-cicd)
9. [Risks to the Plan](#9-risks-to-the-plan)
- [Approval](#approval)
- [Revision History](#revision-history)
- [Appendix A: Not Applicable](#appendix-a-not-applicable)
- [Appendix B: Related Documents](#appendix-b-related-documents)

---

## 1. Introduction
This document defines the master management plan for Phase 1 of SRIS. It sets out how the eight-week window is scheduled, the order in which services and documents are built, and the rules governing testing, branching, versioning, and roles. It is the central operational standard for Phase 1. 

---

## 2. Development Methodology
Phase 1 officially runs from 01 October 2026 to 30 November 2026. The college portal opened on 7 October 2026, and active work began on 8 October 2026. This plan is enacted on Monday 12 October 2026, which falls inside Week 1.

The project operates on one-week sprints. There are eight sprints for the eight weeks of Phase 1. 

**The backlog principle**
The weekly schedule is a plan, not a contract. Work not completed in its scheduled week carries forward to the next week. The final week absorbs the remaining backlog. Nothing is dropped. The deliverables committed to in [SRIS-P1-GOV-005](./SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document are fixed and must be met.

---

## 3. Schedule and Work Breakdown

* **Weeks 1 to 2 (Documentation only):** Write all 60 UNBLOCK documents. Meet with the team. Freeze initial contracts. Team members read documents passively and raise questions. No development work occurs.
* **Week 3 (Infrastructure and S1 IAM):** 
  * Day 1: Infrastructure setup (servers, credentials, IP addresses, permissions). This blocks database work until complete. Team members join active work.
  * Days 2 to 5: S1 IAM Service development. Frontend, backend, and database streams work in parallel on the same service.
  * Days 6 to 7: S1 IAM service tests and integration tests with the infrastructure. S1 IAM is complete, tested, and documented by the end of Week 3.
* **Week 4 (S2 Master Data and Pricing Service):** Follow the Week 3 pattern. Build, test, and integrate with S1 IAM. Documentation continues in parallel.
* **Weeks 5 and 6 (S3 Reservation Service):** This is the largest service with two internal modules, so it spans two weeks.
  * Week 5: Inventory module (seat matrix, availability, hold, confirm, release).
  * Week 6: Booking module (state machine, PNR, waitlist, chart, cancellation, payment callback verification). Integration tests with S1 and S2 run across both weeks.
* **Week 7 (Remaining services and UI):** Development of S4 Search Aggregator BFF, S5 Mock Payment Gateway, and S6 Notification Service. Completion of the Customer Booking Website end-to-end pages.
* **Week 8 (Full system integration and finalisation):** End-to-end booking flow tested across all six services and both surfaces. Documentation polish. PDF generation for all 180 documents. Software release branch frozen at v1.0.0.

---

## 4. Deliverables and Acceptance
The five fixed Phase 1 deliverables and their acceptance criteria are strictly defined in [SRIS-P1-GOV-005](./SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document. Deliverables are only accepted when they meet the success criteria established in that document. 

---

## 5. Branching and Versioning

**Branching model**
* `main`: permanent stable snapshot.
* `docs`: permanent documentation branch.
* `develop`: created in Week 3, used for the integration of feature branches.
* `feature/*`: one branch per task, deleted after it is merged.
* `testing/*`: test code retained for Phase 1 reference.
* `release/*`: frozen release snapshots, never deleted.

**Version schemes**
Versioning follows two independent streams.
* **Document versions:** MAJOR.MINOR format. The first version is 1.0. The major digit always equals the phase number.
* **Software versions:** MAJOR.MINOR.PATCH format following Semantic Versioning. Phase 1 delivers software v1.0.0. Bug fixes become 1.0.1, new features become 1.1.0, and Phase 2 becomes 2.0.0.

---

## 6. Testing Approach
Testing is enforced across three layers:
1. **Unit tests:** Written concurrently with the code.
2. **Service tests:** Run when each individual service is complete.
3. **Integration tests:** Run continuously as new services are added to the environment.

A developer self-tests their own work before submitting it for review. The Lead Architect re-tests every task. Nothing is accepted on self-test alone. The Lead Architect holds the final authority on whether a task is complete.

---

## 7. Roles and Responsibilities
* **Lead Architect (Koushal Jha):** Designs contracts, writes all 180 documents, builds frontend and backend where needed, reviews all team output, runs unit, service, and integration tests, and executes all merges.
* **Team members:** Read documents during Weeks 1 and 2, and raise questions. Join active development from Week 3 Day 1. Responsible for self-testing their own work before submission.
* **Supervisor (Anupam Yadav):** Evaluator only. Not involved in project decisions.
* **Mentor:** None assigned for the active project.

---

## 8. Reporting and CI/CD
Progress is reviewed twice a week on Thursday and Sunday. The team reports against the week's plan, with development continuing between these checkpoints via online and offline collaboration.

A full CI/CD pipeline runs on every push to the repository. It installs dependencies, runs the test suite, and reports the result. The team learns the pipeline as they build, and mistakes are expected and fixed as they occur. The specific pipeline tooling and design are documented in [SRIS-P1-INF-003](../wave-5-devops-operations/SRIS-P1-INF-003_CICDPipelineDesign.md) — CI/CD Pipeline Design. 

---

## 9. Risks to the Plan
1. **Documentation load is heavy.** AI limits, occasional misunderstanding, and time pressure apply across the 180 documents. 
   * *Mitigation:* Prioritise strict template adherence and focus on UNBLOCK documents in the first two weeks.
2. **Team members may not perform as expected on assigned tasks.** 
   * *Mitigation:* The Lead Architect retains the capacity to build frontend and backend components where necessary to prevent blocks.
3. **Server RAM is limited to 5.1 GB.** Running all six services together may exceed it. Storage is not a concern.
   * *Mitigation:* Monitor memory footprints aggressively during integration testing and optimise runtime usage.
4. **Communication between developers may break down.** 
   * *Mitigation:* Rely on the twice-weekly reporting checkpoints and formalised API contracts to synchronise the team.

---

## Approval

| Role | Name | Decision | Date |
| ------ | ------ | ------ | ------ |
| Lead Architect | Koushal Jha | Approved | 2026-10-12 |

---

## Revision History

| Version | Date | Author | Change |
| ------ | ------ | ------ | ------ |
| 1.0 | 2026-10-12 | Koushal Jha | Initial release. |

---

## Appendix A: Not Applicable

Not applicable.

---

## Appendix B: Related Documents

### B.1 Directly Referenced Documents

| Seq | Document ID | Document Name | Wave | Pri | Tag |
| ------ | ------ | ------ | ------ | ------ | ------ |
| 0.1 | [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) | Document Template Standard | 0 | P0 | UNBLOCK |
| 0.4 | [SRIS-P1-GOV-005](./SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) | Project Vision and Scope Document | 0 | P0 | UNBLOCK |
| 2.1 | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) | Microservices Identification | 2 | P0 | UNBLOCK |
| 5.3 | [SRIS-P1-INF-003](../wave-5-devops-operations/SRIS-P1-INF-003_CICDPipelineDesign.md) | CI/CD Pipeline Design | 5 | P0 | UNBLOCK |

### B.2 Documents That Reference This Document
All subsequent Phase 1 planning, scheduling, and risk tracking documents reference this management plan as the governing timeline. The complete list is in the register described in [B.5](#b5-master-documentation-index).

### B.3 Documents This Document Depends On (Upstream)

| Seq | Document ID | Document Name | Dependency Type |
| ------ | ------ | ------ | ------ |
| 0.0 | [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) | Documentation Index and Navigation Map | Soft |
| 0.1 | [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) | Document Template Standard | Hard |
| 0.4 | [SRIS-P1-GOV-005](./SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) | Project Vision and Scope Document | Hard |

### B.4 Documents This Document Unblocks (Downstream)

| Seq | Document ID | Document Name | Blocked Until |
| ------ | ------ | ------ | ------ |
| 0.8 | [SRIS-P1-GOV-009](./SRIS-P1-GOV-009_RiskManagementPlan.md) | Risk Management Plan | This approved |
| 0.9 | [SRIS-P1-GOV-010](./SRIS-P1-GOV-010_CommunicationPlan.md) | Communication Plan | This approved |
| 0.10 | [SRIS-P1-GOV-011](./SRIS-P1-GOV-011_QualityManagementPlan.md) | Quality Management Plan | This approved |

### B.5 Master Documentation Index
The master documentation index is [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

### B.6 External Reference Documents
None.

### B.7 Document Conventions
The conventions for Priority and Tag values are defined in [Section 9](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#9-vocabulary-standards) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.