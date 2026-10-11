
# SRIS

**Sarathi Railway Information System**

An Independent Railway Management Platform

*Inspired by CRIS and IRCTC · Not affiliated with either organization*

---

## Overview

SRIS is a microservices-based unified railway management platform built
as an independent academic project. It is inspired by the architecture
and systems of CRIS (Centre for Railway Information Systems) and the
booking experience of IRCTC, but is not affiliated with either
organization.

The platform delivers two primary surfaces:

| Surface | Users | Core Function |
|---------|-------|---------------|
| Customer Booking Website | Passengers | Search, seat selection, payment, PNR generation |
| Employee Admin Console | Railway Employees | Master data, schedules, fares, quotas, chart preparation |

Both surfaces are powered by a single backend designed using Domain-
Driven Design, contract-first development, and event-driven integration.

---

## Project Information

| Field | Details |
|-------|---------|
| Software Name | SRIS |
| Full Form | Sarathi Railway Information System |
| Team Codename | Project Sarathi |
| Architecture | Polyglot Microservices (Hybrid) |
| Research Area | Software Engineering & Distributed Systems |
| Group | G320 |
| Institution | GLA University, Mathura, Uttar Pradesh |
| Semester | VII — Final Year Major Project |
| Duration | 01 October 2026 — 30 November 2026 |
| Project Version | Phase 1 Foundation |

---

## Team

| Name | Role | Notes |
|------|------|-------|
| Koushal Jha | Lead Architect | Architecture, Backend, Database, Infrastructure |
| Chandra Shekhar Bansal | UI/UX Designer | |
| Harshvardhan | UI/UX | |
| Hitanshu Dhakrey | Backend | Java |
| Shivanshu Dhakrey | Backend | Node.js |

Full team details: to be added later.

---

## Supervisor

| Field | Details |
|-------|---------|
| Supervisor | Anupam Yadav |
| Institution | GLA University |
| Contact | 9690480615 |

---

## Documentation

All project documentation is stored in the `docs/` folder.

### Source Documents (Markdown)

Source documents do not carry a version in the filename. Version
information is stored inside each document and tracked by Git.

Naming convention:

`<Document ID>_<DocumentNameInPascalCase>.md`

Example:

`SRIS-P1-ARCH-001_MicroservicesIdentification.md`


### Phase Deliverables (PDF)

PDFs are generated once at the end of each phase, when all documents
in the phase are complete and approved. They are not produced during
development.

Two sets are generated per phase. Each wave folder holds its own
deliverables subfolder for that wave's individual PDFs. The phase
folder holds the combined book.

1. **Individual PDFs** — one per document, stored inside the wave folder
   of the document's own wave.

   - Location: `docs/phase-1-foundation/wave-N-<wave-name>/deliverables/`
   - Naming: `SRIS-P1-<CATEGORY>-<NNN>_<DocumentNameInPascalCase>_v<Version>.pdf`
   - Example: `docs/phase-1-foundation/wave-2-architecture/deliverables/SRIS-P1-ARCH-001_MicroservicesIdentification_v1.1.pdf`

2. **Combined Book PDF** — all 180 documents in one file, stored at the
   phase folder.

   - Location: `docs/phase-1-foundation/deliverables/`
   - Naming: `SRIS-Phase1-Foundation-Book_v<Version>.pdf`
   - Example: `docs/phase-1-foundation/deliverables/SRIS-Phase1-Foundation-Book_v1.0.pdf`

---

## Disclaimer

SRIS is an independent academic project. It is not affiliated with,
endorsed by, or sponsored by CRIS (Centre for Railway Information
Systems), IRCTC, or Indian Railways. The project is inspired by their
systems for learning and demonstration purposes only.

---

## Revision History

| Version | Date       | Author      | Change                                                                                                                                                          |
| ------- | ---------- | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.0     | 2026-10-10 | Koushal Jha | Initial release — project overview, team, documentation conventions.                                                                                            |
| 1.1     | 2026-10-11 | Koushal Jha | Aligned PDF deliverables with wave folder structure, fixed placeholder syntax, corrected research area, clarified version field, updated team roles and notes. |

---

**© 2026 Project Sarathi · GLA University · Group G320**