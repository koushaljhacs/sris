<div align="center">

![Wave](https://img.shields.io/badge/Wave-1-0550AE?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-REQ-6e7781?style=for-the-badge)

</div>

# Glossary and Domain Dictionary

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** 1.0 | **Date:** 2026-10-12 | **Document ID:** SRIS-P1-REQ-001

| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| Title              | Glossary and Domain Dictionary                                    |
| Software           | SRIS                                                              |
| Software Full Form | Sarathi Railway Information System                                |
| Team Codename      | Project Sarathi                                                   |
| Document ID        | SRIS-P1-REQ-001                                                   |
| Task               | Define the vocabulary used across the Phase 1 document register   |
| Document Type      | Reference Document                                                |
| Milestone          | Phase 1 Foundation                                                |
| Classification     | Internal                                                          |
| Version            | 1.0                                                               |
| Date               | 2026-10-12                                                        |
| Author             | Koushal Jha, Lead Architect                                       |
| Approved By        | Koushal Jha, Lead Architect                                       |
| Approval Date      | 2026-10-12                                                        |
| Supersedes         | None (first version)                                              |
| Related Documents  | See Appendix B                                                    |
| Affiliation        | Independent · Not affiliated with CRIS, IRCTC, or Indian Railways |

---

## Table of Contents

1. [Introduction](#1-introduction)
   - [1.1 Purpose](#11-purpose)
   - [1.2 Scope](#12-scope)
   - [1.3 Audience](#13-audience)
2. [How to Use This Glossary](#2-how-to-use-this-glossary)
3. [Railway Domain Terms In Scope](#3-railway-domain-terms-in-scope)
   - [3.1 Train Identity and Categories](#31-train-identity-and-categories)
   - [3.2 Route and Schedule](#32-route-and-schedule)
   - [3.3 Coach and Class](#33-coach-and-class)
   - [3.4 Berth and Seat](#34-berth-and-seat)
   - [3.5 Quota](#35-quota)
   - [3.6 Booking and Ticketing](#36-booking-and-ticketing)
   - [3.7 Waitlist and Chart](#37-waitlist-and-chart)
   - [3.8 Fare and Pricing](#38-fare-and-pricing)
   - [3.9 Employee Administration](#39-employee-administration)
4. [Railway Domain Terms Out of Scope](#4-railway-domain-terms-out-of-scope)
5. [SRIS System Terms](#5-sris-system-terms)
   - [5.1 Architecture](#51-architecture)
   - [5.2 Data](#52-data)
   - [5.3 API and Integration](#53-api-and-integration)
   - [5.4 Security and Privacy](#54-security-and-privacy)
   - [5.5 Delivery and DevOps](#55-delivery-and-devops)
   - [5.6 Testing](#56-testing)
   - [5.7 Documentation and Governance](#57-documentation-and-governance)
   - [5.8 Process](#58-process)
6. [Acronyms and Abbreviations](#6-acronyms-and-abbreviations)
7. [Boundary Cases and Term Distinctions](#7-boundary-cases-and-term-distinctions)
8. [Approval](#8-approval)

- [Revision History](#revision-history)
- [Appendix A: Not Applicable](#appendix-a-not-applicable)
- [Appendix B: Related Documents](#appendix-b-related-documents)

---

## 1. Introduction

### 1.1 Purpose

This document defines the vocabulary used across the Phase 1 document register of SRIS (Sarathi Railway Information System). It is the authoritative reference for railway domain terms and for the technical and governance terms used by the project. Every other Phase 1 document uses these terms with these meanings. Where a term carries a rule, this document states the meaning and points to the document that owns the rule.

### 1.2 Scope

**In scope**

- Railway domain terms used in the Phase 1 booking flow.
- Railway domain terms deliberately deferred to Phase 2 or later.
- SRIS system terms used in the architecture, data, API, security, testing, governance, and process documentation.
- Acronyms and abbreviations used in the register.
- Terms with conflicting or ambiguous meanings, with the SRIS resolution stated.

**Out of scope**

- The detailed rules for fare calculation, which belong to [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) — Domain Rules: Fare Calculation.
- The detailed rules for ticketing, which belong to [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md) — Domain Rules: Ticketing.
- The detailed rules for waitlist handling and cancellation, which belong to [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md) — Domain Rules: Waitlist and Cancellation.
- The detailed rules for chart preparation, which belong to [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md) — Domain Rules: Chart Preparation.
- The detailed rules for the seat matrix and inventory, which belong to [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md) — Domain Rules: Seat Matrix and Inventory.
- The service catalogue, which belongs to [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification.
- The full vision, scope, and success criteria, which belong to [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document.

### 1.3 Audience

- **Lead Architect:** maintains this document and is the source of new terms.
- **Team members:** use these terms when writing requirements, designs, and test cases.
- **Project supervisor and evaluator:** reviews the vocabulary for consistency across the register.
- **Technical reviewers:** engineers, interviewers, or recruiters who open the repository and need the project's vocabulary in one place.

---

## 2. How to Use This Glossary

Terms appear in alphabetical order inside each subsection. Each entry has three parts.

- The **term**.
- The **definition**, in plain English.
- The **owning document**, which is the document that carries the detailed rule or model for the term.

Where a term has a meaning that is not obvious from general use, the entry states the SRIS meaning plainly. Where a term appears in more than one section, the canonical entry is the one that matches the term's primary subject.

An entry whose owning document is registered but not yet written is cited by its Document ID and title. The link resolves when the file is committed, per [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md) — Document Cross-Reference Standard.

---

## 3. Railway Domain Terms In Scope

The terms in this section are used in the Phase 1 booking flow. The owning documents are the requirements documents of Wave 1 and the master data definitions held inside the service catalogue.

### 3.1 Train Identity and Categories

| Term           | Definition                                                                                                            | Owning Document                                                                          |
| -------------- | --------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Train number   | A unique five-digit identifier assigned to a specific railway service operating on a defined route.                    | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)                            |
| Train name     | The designated textual name of a railway service, used mainly for passenger-facing display.                            | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)                            |
| Train type     | The classification of a railway service that determines its speed, stopping pattern, and applicable fare structure.    | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)                            |
| Express        | A long-distance train category that halts mainly at major intermediate stations.                                        | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)                            |
| Superfast      | A train category that maintains an average speed above fifty-five kilometres per hour and carries a supplementary charge. | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)                        |
| Passenger      | A train category that halts at almost every station and uses the lowest fare distance slabs.                            | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)                            |
| Rajdhani       | A fully air-conditioned train category connecting the national capital to state capitals, with dynamic pricing.          | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)                        |
| Shatabdi       | A fully air-conditioned daytime intercity train category with chair car seating only, returning to its origin the same day. | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)                            |
| Vande Bharat   | A semi-high-speed electric multiple unit train category with distributed power and premium fare structures.             | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)                        |
| Duronto        | A long-distance train category designed to operate non-stop between its origin and destination.                          | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)                            |
| Garib Rath     | A fully air-conditioned train category with high-density coach composition and subsidised fares.                         | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)                        |

### 3.2 Route and Schedule

| Term                | Definition                                                                                                 | Owning Document                                                       |
| ------------------- | ---------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Origin              | The first station from which a specific train commences its scheduled journey.                              | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)         |
| Destination         | The final station where a specific train terminates its scheduled journey.                                  | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)         |
| Intermediate station| Any station between the origin and destination where the train is scheduled to halt.                        | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)         |
| Distance            | The cumulative route length in kilometres from the origin to a specific station, used to calculate the fare slab. | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)     |
| Route               | The ordered list of stations, distances, and track paths traversed by a train between its origin and destination. | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)         |
| Stop                | A station where a train is authorised to halt for commercial passenger activity.                            | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)         |
| Halt time           | The scheduled duration in minutes that a train remains stationary at an intermediate station.                | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)         |
| Running days        | The days of the week on which a train service originates from its source station.                           | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)         |
| Departure           | The scheduled time at which a train leaves a specific station.                                              | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)         |
| Arrival             | The scheduled time at which a train reaches a specific station.                                             | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)         |
| Schedule            | The complete chronological timetable of arrivals, departures, and halt times for a specific train across its route. | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)         |
| Timetable           | The master collection of all train schedules across the railway network.                                     | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)         |
| Frequency           | The recurrence rate of a train service, expressed as daily, weekly, or bi-weekly.                            | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)         |

### 3.3 Coach and Class

| Term           | Definition                                                                                                | Owning Document                                                           |
| -------------- | --------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Coach          | A single railway carriage attached to a train, configured internally for a specific travel class.          | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Composition    | The ordered arrangement and quantity of coach types attached to a train, determining total seat inventory.  | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Class          | The tier of passenger accommodation, determining seat layout, air conditioning, and fare multiplier.        | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| SL             | Sleeper Class. Non-air-conditioned sleeping berths in bays of eight.                                       | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| 1A             | AC First Class. Premium air-conditioned sleeping accommodation in private cabins or coupes.                 | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| 2A             | AC Two Tier. Air-conditioned sleeping berths in bays of six with privacy curtains.                          | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| 3A             | AC Three Tier. Air-conditioned sleeping berths in bays of eight.                                            | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| 3E             | AC Three Tier Economy. High-density air-conditioned sleeping accommodation with a narrower berth profile.   | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| CC             | AC Chair Car. Air-conditioned daytime seating accommodation.                                                | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| EC             | Executive Chair Car. Premium air-conditioned daytime seating with extended legroom and wider seats.          | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| 2S             | Second Seating. Non-air-conditioned daytime seating accommodation.                                          | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Coach position | The physical sequence of a coach relative to the locomotive, shown to passengers for boarding.              | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |

### 3.4 Berth and Seat

| Term              | Definition                                                                                                          | Owning Document                                                           |
| ----------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Berth             | A horizontal sleeping accommodation provided in overnight travel classes.                                            | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Lower berth       | The bottom transverse berth in a sleeping bay.                                                                       | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Middle berth      | The intermediate transverse berth in a three-tier sleeping bay.                                                      | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Upper berth       | The top transverse berth in a sleeping bay.                                                                          | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Side lower        | A longitudinal berth along the corridor, split into two daytime seats for RAC passengers.                             | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Side upper        | A longitudinal berth above the side lower berth along the corridor.                                                  | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Seat              | A seating accommodation in daytime travel classes, or the daytime configuration of a lower berth.                     | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Seat matrix       | The generated set of all physical seats and berths available for a specific train journey, derived from master data.  | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Seat allocation   | The process of assigning a specific physical seat or berth to a confirmed booking.                                    | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Seat availability | The count of unreserved seats remaining in a specific class and quota for a given journey segment.                     | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Hold              | A temporary lock on a seat during payment, preventing concurrent double bookings.                                     | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Release           | The action of returning a held or cancelled seat to the available inventory pool.                                     | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |

### 3.5 Quota

| Term              | Definition                                                                                                | Owning Document                                                           |
| ----------------- | --------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| General quota (GN)| The primary pool of seats available to the general public across the full route.                          | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Tatkal quota (TQ) | A premium pool opened one day before departure for urgent travel, carrying a flat surcharge.               | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Ladies quota (LD) | A pool of seats reserved for female passengers and accompanying children.                                  | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Senior citizen quota (SS) | A pool of lower berths reserved for senior citizens and eligible female passengers.              | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Defence quota (DF)| A pool of seats reserved for military personnel on official warrants.                                      | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |
| Premium Tatkal (PT)| A Tatkal variant with dynamic pricing that increases as seats deplete.                                    | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)         |
| Quota allocation  | The division of the total seat matrix into specific logical pools before bookings begin.                   | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)  |

### 3.6 Booking and Ticketing

| Term                 | Definition                                                                                                     | Owning Document                                                       |
| -------------------- | -------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Booking              | The end-to-end transactional flow in which a customer requests travel, holds a seat, pays, and receives a ticket. | [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md) |
| Reservation          | The act of securing a defined seat or waitlist position within the inventory matrix.                             | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md) |
| PNR                  | Passenger Name Record. A unique ten-digit identifier that locates a booking and its passengers.                  | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)           |
| Passenger            | An individual traveller associated with a booking, with attributes such as age, gender, and berth preference.    | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)           |
| Passenger details    | The personal information required to establish identity and calculate concessions for a specific traveller.       | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)           |
| Boarding station     | The station from which the passenger intends to commence the journey, which may differ from the booking origin.   | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)           |
| Reservation status   | The lifecycle state of a passenger's seat request: Waitlist, RAC, or Confirmed.                                  | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)           |
| Confirmation         | The state in which a booking has secured payment and obtained a guaranteed seat or RAC position.                 | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)           |
| Cancellation         | The termination of a booking by the customer, releasing inventory and initiating the refund calculation.         | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)           |
| Refund               | The amount returned to a customer after cancellation, less applicable charges, routed through the payment gateway. | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)     |
| Ticket               | The document or digital record proving a passenger's right to travel on a specific train.                        | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)           |
| E-ticket             | An electronic ticket issued by the booking system and delivered digitally.                                      | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)           |
| Boarding             | The act of a passenger entering the reserved carriage at the designated station.                                | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)           |

### 3.7 Waitlist and Chart

| Term               | Definition                                                                                                          | Owning Document                                                             |
| ------------------ | ------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| Waitlist (WL)      | A queue of passengers who have paid the fare but lack confirmed accommodation, awaiting cancellations.                | [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)  |
| RAC                | Reservation Against Cancellation. An intermediate status providing daytime seating with a shared berth.               | [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)  |
| Waitlist position  | The numeric rank of a passenger within a waitlist queue, determining promotion priority.                              | [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)  |
| Waitlist cascade   | The sequential logic by which a cancellation promotes the top waitlisted passenger, then the top RAC passenger.        | [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)  |
| Promotion          | The automatic upgrade of a passenger's status, from Waitlist to RAC or from RAC to Confirmed.                         | [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)  |
| No-show            | A confirmed passenger who fails to board, freeing the berth for reassignment.                                          | [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md)         |
| PQWL               | Pooled Quota Waitlist. A queue for passengers travelling between intermediate stations on a shared pool.               | [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)  |
| GNWL               | General Waitlist. The main queue for origin-to-destination passengers, with the highest chance of confirmation.         | [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)  |
| Chart preparation  | The batch finalisation of the passenger manifest shortly before departure, resolving remaining quota and waitlists.    | [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md)         |

### 3.8 Fare and Pricing

| Term               | Definition                                                                                              | Owning Document                                                   |
| ------------------ | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| Base fare          | The fundamental cost of travel calculated against total journey distance, excluding class multipliers.    | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) |
| Fare class         | The pricing tier associated with a travel class, applying a multiplier to the base distance fare.         | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) |
| Distance slab      | A predefined distance range used to assign a fixed price rather than a cost per kilometre.                | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) |
| Dynamic pricing    | A mechanism in which the fare increases incrementally as seat inventory depletes.                         | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) |
| Concession         | A fare reduction granted to a specific passenger category, supported by documented verification.          | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) |
| Service charge     | An administrative fee added to the total fare to cover online booking operation.                          | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) |
| GST                | Goods and Services Tax. A statutory levy applied to air-conditioned travel classes.                        | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) |
| Fare quote         | An estimated total price shown during search, before final quota and concession validation.                | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) |
| Fare re-quote      | The final authoritative price calculation performed before payment, incorporating all selected criteria.   | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) |

### 3.9 Employee Administration

| Term                                         | Definition                                                                                              | Owning Document                                                   |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| Master data setup                            | The administrative process of configuring static network parameters such as stations, distances, and trains. | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)     |
| Station configuration                        | The creation and management of station entities with codes, names, and geographic distances.               | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)     |
| Train configuration                          | The setup of a train's identity, service type, base route, and default coach composition.                  | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)     |
| Schedule configuration                       | The definition of a train's arrival and departure times along its route, forming a searchable itinerary.    | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)     |
| Fare configuration                           | The definition of base fares, distance slabs, dynamic pricing rules, and tax parameters.                    | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md) |
| Quota configuration                          | The division of coach inventory into commercial categories such as General and Tatkal.                      | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md) |

---

## 4. Railway Domain Terms Out of Scope

The terms in this section belong to the broader railway ecosystem but fall outside the Phase 1 booking flow. They are recorded here so that the register holds one authoritative list of what Phase 1 does not do, and so that no later document re-introduces a deferred term without a revision to this glossary and to [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md) — Project Vision and Scope Document.

| Term                    | Definition                                                                                        | Deferred To | Reason                                                                                     |
| ----------------------- | ------------------------------------------------------------------------------------------------- | ----------- | ------------------------------------------------------------------------------------------ |
| Train running status    | Real-time tracking of a train's location and its delay against the published schedule.             | Phase 2     | Requires live integration outside the static booking flow.                                  |
| Delay                   | The gap between scheduled and actual arrival or departure during live operation.                  | Phase 2     | Live telemetry is not part of the transactional engine.                                     |
| Disruption              | An operational event that halts or alters the railway's ability to run scheduled services.        | Phase 2     | Recovery logic is not required to prove the booking flow.                                   |
| Diversion               | The rerouting of a train along an alternative path due to blockage or disruption.                 | Phase 2     | Dynamic route recalculation is not required in Phase 1.                                     |
| Rescheduling            | The administrative alteration of a train's departure time to mitigate a late incoming rake.        | Phase 2     | Post-publish schedule mutations add consistency risk and are deferred.                      |
| Train cancellation      | The annulment of a scheduled train run, triggering full refunds for all booked passengers.         | Phase 2     | Batch cancellation and mass refund processing are outside Phase 1.                          |
| Platform allocation     | The operational assignment of specific station tracks to incoming and outgoing trains.            | Future      | Physical station operations are independent of the logical inventory matrix.                |
| Platform number         | The identifier of the specific boarding edge where a train halts at a station.                    | Future      | Handled by station displays at arrival time, not by the booking application.                |
| Station facilities      | Physical amenities such as waiting rooms, escalators, and retiring rooms.                          | Future      | Facility management is a supplementary service.                                             |
| Station master          | The senior employee responsible for the safe operation of trains within the station area.         | Future      | Operational roles do not enter the Phase 1 access model.                                    |
| Employee records        | Human resources data covering employment history, payroll, and personal details.                   | Future      | Phase 1 models only the authentication profile, not full human resource management.         |
| Department              | The internal organisational grouping of railway employees by function.                             | Future      | Internal structures are not needed for the employee admin console to function.              |
| Crew                    | The staff operating the train, including pilots, guards, and on-board commercial staff.            | Phase 2     | Operational staffing is a separate domain from passenger reservations.                      |
| Crew rostering          | The scheduling of crew to specific train runs under statutory rest rules.                          | Future      | Rostering requires a distinct bounded context not present in Phase 1.                       |
| Duty assignment         | The allocation of a specific operational shift or task to an employee.                             | Future      | Task management is not part of the reservation scope.                                       |
| Leave                   | The authorised absence of an employee from the scheduled roster.                                   | Future      | Leave management adds scope unrelated to the booking engine.                                |
| Attendance              | The recorded presence of an employee at a scheduled shift.                                         | Future      | Time tracking is excluded from Phase 1.                                                     |
| Operational dashboard   | A visual interface displaying network health, punctuality, and revenue metrics.                    | Phase 2     | Live aggregation requires reporting infrastructure not provisioned in Phase 1.              |
| Report                  | A generated analytical document summarising historical performance.                                | Phase 2     | Batch analytics compete for resources with the transactional database.                      |
| Analytics               | The computational evaluation of data to identify trends and profitability.                         | Future      | Data warehousing and complex aggregation are outside the transactional datastore.           |
| Occupancy               | The ratio of occupied seats to total available seats on a train.                                    | Phase 2     | System-wide occupancy requires chart aggregation and reporting services.                    |
| Load factor             | A commercial metric measuring capacity utilisation across distance segments.                        | Future      | Commercial efficiency modelling is secondary to proving the booking engine.                 |
| Grievance               | A formal complaint raised by a customer about a service deficiency.                                 | Future      | Customer service workflows sit outside the reservation path.                                |
| Complaint               | A documented allegation of failure or misconduct directed at a department or individual.           | Future      | Feedback and disciplinary workflows require separate bounded contexts.                      |
| Catering                | The provision of meals, beverages, and pantry car services during a journey.                        | Future      | Food service logistics are not part of the transactional core.                              |
| On-board services       | Facilities during travel such as bedrolls, cleanliness, and maintenance assistance.                 | Future      | Phase 1 ends at chart preparation and ticket issuance.                                      |
| Vendor                  | A third-party entity contracted to provide auxiliary railway services.                              | Future      | Third-party contracts are outside the domain model.                                          |
| Vendor management       | The oversight, licensing, and evaluation of third-party contractors.                                | Future      | Commercial contracting is excluded from the foundational scope.                              |

---

## 5. SRIS System Terms

The terms in this section are the project's own vocabulary. They appear in the architecture, data, API, security, delivery, testing, governance, and process documents. Where a term is specific to SRIS and has no external authority, the entry states that the usage is internal.

### 5.1 Architecture

| Term                 | Definition                                                                                            | Owning Document                                                                                 |
| -------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| Service              | An independently deployable component that owns a specific business capability and its data.          | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)      |
| Microservice         | An architectural style that structures an application as a set of loosely coupled services.           | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)      |
| Bounded context      | A boundary within which a domain model and its vocabulary are consistent.                              | [SRIS-P1-ARCH-004](../wave-2-architecture/SRIS-P1-ARCH-004_BoundedContextMap.md)                 |
| Aggregate            | A cluster of domain objects treated as a single unit for data changes.                                  | [SRIS-P1-ARCH-005](../wave-2-architecture/SRIS-P1-ARCH-005_DomainModelDocument.md)               |
| Entity               | A domain object with a continuous identity that persists across state changes.                          | [SRIS-P1-ARCH-005](../wave-2-architecture/SRIS-P1-ARCH-005_DomainModelDocument.md)               |
| Value object         | An immutable domain object defined entirely by its attributes, without persistent identity.             | [SRIS-P1-ARCH-005](../wave-2-architecture/SRIS-P1-ARCH-005_DomainModelDocument.md)               |
| Domain event         | A message describing a significant business action within a bounded context.                            | [SRIS-P1-ARCH-009](../wave-2-architecture/SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md) |
| Saga                 | A sequence of local transactions coordinated across services through events and compensating actions.   | [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md) |
| Compensating transaction | A reverse action that undoes the effect of a completed local transaction when a later step fails. | [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md) |
| Anti-corruption layer| A translation component that insulates a domain model from an external system.                          | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)      |
| BFF                  | Backend-For-Frontend. A service that aggregates and formats data for a specific client.                 | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)      |
| API gateway          | The single external entry point that routes client traffic to internal services.                        | [SRIS-P1-ARCH-003](../wave-2-architecture/SRIS-P1-ARCH-003_SystemArchitectureDocument.md)        |
| Idempotency          | The property whereby executing an operation multiple times yields the same result as executing it once. | [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md) |
| Eventual consistency | A guarantee that, absent new updates, dependent services will converge to the same state.              | [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md) |
| Distributed transaction | A transaction spanning multiple services, typically enforced through two-phase commit.              | [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md) |
| Optimistic lock      | A concurrency control method that checks for a version conflict at commit time rather than locking earlier. | [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md) |
| Pessimistic lock     | A concurrency control method that acquires a lock before reading or writing a shared resource.          | [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md) |
| Distributed lock     | A lock held across service boundaries to protect a shared resource from concurrent access.              | [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md) |
| Trace                | The record of a single request as it passes through multiple services.                                  | [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)  |
| Span                 | One operation inside a trace, with a start time, duration, and parent.                                  | [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)  |
| Correlation ID       | An identifier attached to a request and propagated across services to link their logs.                   | [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)  |
| OpenTelemetry        | A vendor-neutral standard for producing and collecting traces, metrics, and logs.                        | [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)  |

### 5.2 Data

| Term              | Definition                                                                                              | Owning Document                                                                                 |
| ----------------- | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| Schema            | The formal structural definition of a database: tables, fields, constraints, and relationships.          | [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md) |
| Table             | A relational data structure of columns and rows that stores entities.                                    | [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md) |
| Primary key       | A column or set of columns that uniquely identifies each row in a table.                                 | [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md) |
| Foreign key       | A column that references the primary key of another table, enforcing referential integrity.              | [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md) |
| Index             | An auxiliary data structure used by the database engine to accelerate data retrieval.                    | [SRIS-P1-DATA-006](../wave-3-detailed-design/SRIS-P1-DATA-006_IndexAndConstraintSpecification.md) |
| Logical model     | An abstract representation of entities and relationships, independent of any database engine.            | [SRIS-P1-DATA-002](../wave-3-detailed-design/SRIS-P1-DATA-002_LogicalDataModelPerService.md)     |
| Physical model    | A logical model implemented for a specific database engine, with types and indexes fixed.                | [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md) |
| Data dictionary   | A catalogue defining the format, meaning, and usage of every data element.                               | [SRIS-P1-DATA-004](../wave-3-detailed-design/SRIS-P1-DATA-004_DataDictionary.md)                 |
| Migration         | A version-controlled script that evolves a database schema from one state to the next.                   | [SRIS-P1-DATA-010](../wave-3-detailed-design/SRIS-P1-DATA-010_DataMigrationStrategy.md)         |
| Seed data         | Initial records inserted when a database is created, to establish a baseline configuration.              | [SRIS-P1-DATA-012](../wave-3-detailed-design/SRIS-P1-DATA-012_SeedDataAndReferenceDataSpecification.md) |
| Reference data    | Static or slowly changing data used to categorise other data, such as train types.                       | [SRIS-P1-DATA-012](../wave-3-detailed-design/SRIS-P1-DATA-012_SeedDataAndReferenceDataSpecification.md) |
| Data retention    | The defined period for which data is kept before archival or deletion.                                   | [SRIS-P1-DATA-011](../wave-3-detailed-design/SRIS-P1-DATA-011_DataRetentionAndArchivalPolicy.md) |
| Data principal    | The individual whose personal data is processed, under the DPDP framework.                               | [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md) |
| Data fiduciary    | The entity that determines the purpose and means of processing personal data, under the DPDP framework.  | [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md) |
| Purpose limitation | The principle that personal data is collected only for a stated, lawful purpose.                       | [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md) |

### 5.3 API and Integration

| Term              | Definition                                                                                              | Owning Document                                                                                     |
| ----------------- | ------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| REST              | Representational State Transfer. An architectural style for stateless web APIs.                          | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)         |
| Endpoint          | A specific URL where an API exposes a resource or operation.                                             | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)         |
| Request           | A message sent by a client to an API endpoint, with parameters, headers, and an optional body.           | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)         |
| Response          | A message returned by an API endpoint, with a status code and result payload.                            | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)         |
| OpenAPI           | A specification standard for describing RESTful APIs.                                                    | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)         |
| AsyncAPI          | A specification standard for describing message-driven and event-driven APIs.                            | [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md)        |
| Webhook           | An HTTP callback pushed by one system to another when a specific event occurs.                           | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)         |
| Callback          | A URI provided in a request, instructing the server where to deliver an eventual asynchronous response.  | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)         |
| Contract-first    | A development approach in which the interface is specified and frozen before implementation begins.      | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)         |
| Versioning        | The assignment of version identifiers to API contracts to manage structural change.                      | [SRIS-P1-API-013](../wave-3-detailed-design/SRIS-P1-API-013_APIVersioningAndDeprecationPolicy.md)  |
| Deprecation       | The formal marking of an API element as obsolete while supporting it for a defined period.                | [SRIS-P1-API-013](../wave-3-detailed-design/SRIS-P1-API-013_APIVersioningAndDeprecationPolicy.md)  |
| Rate limit        | A control that restricts the number of requests a client can make within a time window.                  | [SRIS-P1-API-008](../wave-3-detailed-design/SRIS-P1-API-008_APIRateLimitingAndThrottlingRules.md)  |
| Integration design| The specification of how two or more services exchange data, including retry and failure behaviour.      | [SRIS-P1-API-004](../wave-3-detailed-design/SRIS-P1-API-004_IntegrationDesignDocument.md)          |
| Error code        | A defined identifier for a specific failure class, returned in an API error response.                    | [SRIS-P1-API-006](../wave-3-detailed-design/SRIS-P1-API-006_APIErrorCodeCatalog.md)                |
| Event catalog     | The register of all domain events published and consumed across the services.                            | [SRIS-P1-API-009](../wave-3-detailed-design/SRIS-P1-API-009_EventCatalog.md)                       |

### 5.4 Security and Privacy

| Term              | Definition                                                                                              | Owning Document                                                                                     |
| ----------------- | ------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| Authentication    | The process of verifying the identity of a user or system.                                              | [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md) |
| Authorisation     | The process of determining whether an authenticated party may perform a requested action.                | [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md) |
| RBAC              | Role-Based Access Control. Access restricted by the roles assigned to a user.                            | [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md)                          |
| JWT               | JSON Web Token. A compact signed token that carries claims between parties.                              | [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)            |
| Token             | A credential presented to prove identity without transmitting raw secrets.                               | [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)            |
| Claims            | Key-value assertions inside a JWT that describe the authenticated party and its role.                    | [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)            |
| Refresh token     | A long-lived credential used to obtain a new access token without re-authentication.                     | [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)            |
| Secrets           | Sensitive configuration such as passwords, API keys, and signing keys.                                   | [SRIS-P1-SEC-008](../wave-3-detailed-design/SRIS-P1-SEC-008_SecretsManagementPlan.md)              |
| Credential        | The private proof of identity, such as a password, submitted during authentication.                       | [SRIS-P1-SEC-009](../wave-3-detailed-design/SRIS-P1-SEC-009_PasswordAndCredentialPolicy.md)        |
| Consent           | The recorded agreement by a user to allow processing of their personal data.                              | [SRIS-P1-SEC-007](../wave-3-detailed-design/SRIS-P1-SEC-007_ConsentManagementDataModelPhase1Scoped.md) |
| Consent notice    | The statement shown to a user before consent is captured, describing the purpose of processing.          | [SRIS-P1-SEC-007](../wave-3-detailed-design/SRIS-P1-SEC-007_ConsentManagementDataModelPhase1Scoped.md) |
| Data minimisation | The principle that only data necessary for a stated purpose is collected and processed.                   | [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md) |
| Data classification| The categorisation of data by sensitivity, governing its handling and access.                           | [SRIS-P1-SEC-012](../wave-3-detailed-design/SRIS-P1-SEC-012_DataClassificationRegister.md)         |
| Threat model      | A structured analysis of the threats a system must defend against.                                       | [SRIS-P1-SEC-004](../wave-3-detailed-design/SRIS-P1-SEC-004_ThreatModel.md)                        |
| Secure coding     | The set of coding rules that reduce the risk of introducing vulnerabilities.                              | [SRIS-P1-SEC-013](../wave-3-detailed-design/SRIS-P1-SEC-013_SecureCodingStandards.md)              |

### 5.5 Delivery and DevOps

| Term            | Definition                                                                                              | Owning Document                                                                                 |
| --------------- | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| CI/CD           | Continuous Integration and Continuous Delivery. Automated build, test, and delivery of changes.          | [SRIS-P1-INF-003](../wave-5-devops-operations/SRIS-P1-INF-003_CICDPipelineDesign.md)            |
| Pipeline        | A defined sequence of automated steps that compiles, tests, and packages software.                       | [SRIS-P1-INF-003](../wave-5-devops-operations/SRIS-P1-INF-003_CICDPipelineDesign.md)            |
| Build           | The automated conversion of source code into an executable artefact.                                     | [SRIS-P1-INF-003](../wave-5-devops-operations/SRIS-P1-INF-003_CICDPipelineDesign.md)            |
| Artefact        | The output of a build, ready for testing or deployment.                                                  | [SRIS-P1-INF-003](../wave-5-devops-operations/SRIS-P1-INF-003_CICDPipelineDesign.md)            |
| Container       | A standalone executable package containing code, runtime, and dependencies.                              | [SRIS-P1-INF-001](../wave-5-devops-operations/SRIS-P1-INF-001_InfrastructureAndTechnologyDocument.md) |
| Image           | A read-only template from which a container is instantiated.                                              | [SRIS-P1-INF-001](../wave-5-devops-operations/SRIS-P1-INF-001_InfrastructureAndTechnologyDocument.md) |
| Deployment      | The action of installing, configuring, and starting a release in a target environment.                    | [SRIS-P1-OPS-001](../wave-5-devops-operations/SRIS-P1-OPS-001_DeploymentGuide.md)               |
| Environment     | An isolated configuration of infrastructure that hosts the application at a specific stage.                | [SRIS-P1-INF-002](../wave-5-devops-operations/SRIS-P1-INF-002_EnvironmentStrategyDocument.md)     |
| Release         | A tested and frozen distribution of the software made available as a versioned deliverable.                | [SRIS-P1-OPS-007](../wave-5-devops-operations/SRIS-P1-OPS-007_ReleaseManagementPlan.md)          |
| SLO             | Service Level Objective. A target for a measurable aspect of service quality.                             | [SRIS-P1-OPS-005](../wave-5-devops-operations/SRIS-P1-OPS-005_SLODocument.md)                    |

### 5.6 Testing

| Term             | Definition                                                                                              | Owning Document                                                                                     |
| ---------------- | ------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| Unit test        | An automated check of a single function, method, or class in isolation.                                  | [SRIS-P1-TEST-001](../wave-4-testing/SRIS-P1-TEST-001_TestStrategyDocument.md)                      |
| Service test     | A check of one service against its API contract, with external dependencies mocked.                      | [SRIS-P1-TEST-001](../wave-4-testing/SRIS-P1-TEST-001_TestStrategyDocument.md)                      |
| Integration test | A check that multiple services exchange data correctly across network boundaries.                        | [SRIS-P1-TEST-010](../wave-4-testing/SRIS-P1-TEST-010_IntegrationTestPlan.md)                       |
| Contract test    | A check that a provider honours the contract expected by a consumer.                                      | [SRIS-P1-TEST-004](../wave-4-testing/SRIS-P1-TEST-004_ConsumerDrivenContractTestingStrategy.md)     |
| Performance test | An evaluation of responsiveness and stability under a defined workload.                                   | [SRIS-P1-TEST-008](../wave-4-testing/SRIS-P1-TEST-008_PerformanceTestPlan.md)                       |
| Load test        | An evaluation of system behaviour under expected peak concurrency.                                        | [SRIS-P1-TEST-009](../wave-4-testing/SRIS-P1-TEST-009_LoadTestPlan.md)                               |
| UAT              | User Acceptance Testing. The final validation against business requirements by the intended users.        | [SRIS-P1-TEST-011](../wave-4-testing/SRIS-P1-TEST-011_UserAcceptanceTestUATPlan.md)                 |
| Test case        | A specification of inputs, conditions, and expected results for validating a capability.                   | [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)                       |
| Defect           | A deviation between the observed behaviour of the software and its specification.                         | [SRIS-P1-TEST-013](../wave-4-testing/SRIS-P1-TEST-013_DefectManagementProcess.md)                   |
| Regression       | The reappearance of a resolved defect, or the introduction of a new one, after a change.                   | [SRIS-P1-TEST-001](../wave-4-testing/SRIS-P1-TEST-001_TestStrategyDocument.md)                      |

### 5.7 Documentation and Governance

| Term                 | Definition                                                                                              | Owning Document                                                                                       |
| -------------------- | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Register             | The authoritative index of all Phase 1 documents with sequence, ID, wave, priority, and tag.              | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) |
| Wave                 | A grouping of documents by their position in the lifecycle, from foundation to support.                   | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) |
| Blueprint            | A local status overview maintained outside version control, tracking document state.                      | [SRIS-P1-GOV-007](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md)              |
| Document ID          | A unique, permanent identifier assigned to a document before it is written.                                | [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)        |
| Category code        | The part of a Document ID that identifies the document's subject category.                                 | [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)        |
| Sequence number      | The three-digit number inside a Document ID, unique within its category.                                    | [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)        |
| Priority             | A value from P0 to P3 indicating how urgent a document is.                                                  | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)            |
| Tag                  | A fixed lifecycle marker, one of UNBLOCK, FOLLOW, or HOLD.                                                 | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)            |
| Template standard    | The rule set that governs the structure and style of every document in the register.                       | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)            |
| Cross-reference      | A hyperlink from one register document to another, following the relative path rules.                     | [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md)      |
| Revision history     | A table at the end of a document listing every approved change to it.                                       | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)            |
| Approval block       | The table in which the approver records their decision and its date.                                       | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)            |
| Supersede            | A change in which a document or version replaces an earlier one, recorded in the metadata table.           | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)            |
| Metadata table       | The fixed seventeen-field table that records the identity of each document.                                 | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)            |
| Badge                | A small image at the top of a document showing its wave, phase, and category.                              | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)            |
| ADR                  | Architecture Decision Record. A short document capturing one architectural decision.                      | [SRIS-P1-ARCH-007](../wave-2-architecture/SRIS-P1-ARCH-007_ArchitectureDecisionRecordsMasterIndex.md) |

### 5.8 Process

| Term              | Definition                                                                                              | Owning Document                                                                          |
| ----------------- | ------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Sprint            | A fixed, time-boxed iteration with a defined outcome. In SRIS, one week.                                  | [SRIS-P1-GOV-007](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md) |
| Backlog           | The list of work not yet complete. In SRIS, the register rows not yet done.                               | [SRIS-P1-GOV-007](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md) |
| Milestone         | A point marking the completion of a phase or a set of deliverables.                                       | [SRIS-P1-GOV-007](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md) |
| Retrospective     | A review after a sprint in which the team evaluates what worked and what did not.                         | [SRIS-P1-GOV-007](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md) |
| Definition of Done| The criteria a task must meet before it is complete.                                                      | [SRIS-P1-DEV-006](../wave-6-developer-standards/SRIS-P1-DEV-006_DefinitionOfDoneDoD.md)  |
| Definition of Ready| The criteria a task must meet before it enters a sprint.                                                 | [SRIS-P1-DEV-007](../wave-6-developer-standards/SRIS-P1-DEV-007_DefinitionOfReadyDoR.md) |
| Code review       | The examination of source changes by a reviewer before they are merged.                                    | [SRIS-P1-DEV-008](../wave-6-developer-standards/SRIS-P1-DEV-008_CodeReviewChecklist.md)  |
| Commit message    | The text that accompanies a Git commit, describing the change it contains.                                 | [SRIS-P1-DEV-015](../wave-6-developer-standards/SRIS-P1-DEV-015_CommitMessageAndPullRequestConvention.md) |
| Branch            | A parallel line of development in Git, named by its purpose.                                               | [SRIS-P1-DEV-005](../wave-6-developer-standards/SRIS-P1-DEV-005_GitAndBranchingStrategy.md) |

---

## 6. Acronyms and Abbreviations

The acronyms below appear in the Phase 1 register or in the railway domain that Phase 1 models. Where an acronym carries more than one meaning, the SRIS meaning is stated.

### 6.1 Railway Acronyms

| Acronym | Expansion                                | Used In                                     |
| ------- | ---------------------------------------- | ------------------------------------------- |
| PNR     | Passenger Name Record                    | Railway domain, booking                     |
| RAC     | Reservation Against Cancellation          | Railway domain, waitlist and ticketing      |
| SL      | Sleeper Class                            | Railway domain, coach and class             |
| 1A      | AC First Class                            | Railway domain, coach and class             |
| 2A      | AC Two Tier                               | Railway domain, coach and class             |
| 3A      | AC Three Tier                             | Railway domain, coach and class             |
| 3E      | AC Three Tier Economy                     | Railway domain, coach and class             |
| 2S      | Second Seating                            | Railway domain, coach and class             |
| CC      | AC Chair Car                              | Railway domain, coach and class             |
| EC      | Executive Chair Car                       | Railway domain, coach and class             |
| GN      | General Quota                             | Railway domain, quota                       |
| TQ      | Tatkal Quota                              | Railway domain, quota                       |
| LD      | Ladies Quota                              | Railway domain, quota                       |
| SS      | Senior Citizen Quota                      | Railway domain, quota                       |
| DF      | Defence Quota                             | Railway domain, quota                       |
| PT      | Premium Tatkal                            | Railway domain, quota                       |
| NT      | Not Turned Up                             | Railway domain, passenger status            |
| CNF     | Confirmed                                 | Railway domain, reservation status          |
| CAN     | Cancelled                                 | Railway domain, reservation status          |
| MOD     | Modified                                  | Railway domain, reservation status          |
| WL      | Waiting List                              | Railway domain, waitlist                    |
| GNWL    | General Waitlist                          | Railway domain, waitlist                    |
| PQWL    | Pooled Quota Waitlist                     | Railway domain, waitlist                    |
| RLWL    | Remote Location Waitlist                  | Railway domain, waitlist                    |
| RQWL    | Roadside Quota Waitlist                   | Railway domain, waitlist                    |
| TQWL    | Tatkal Quota Waitlist                     | Railway domain, waitlist                    |
| DPWL    | Duty Pass Waitlist                        | Railway domain, waitlist                    |
| TDR     | Ticket Deposit Receipt                    | Railway domain, cancellation and refund     |
| IRCTC   | Indian Railway Catering and Tourism Corporation | External reference (not affiliated)  |
| CRIS    | Centre for Railway Information Systems    | External reference (not affiliated)         |

### 6.2 Technical Acronyms

| Acronym | Expansion                                | Used In                                     |
| ------- | ---------------------------------------- | ------------------------------------------- |
| API     | Application Programming Interface        | SRIS technical                              |
| REST    | Representational State Transfer           | SRIS technical                              |
| JSON    | JavaScript Object Notation                | SRIS technical                              |
| XML     | Extensible Markup Language                | SRIS technical (legacy reference)           |
| HTTP    | Hypertext Transfer Protocol               | SRIS technical                              |
| HTTPS   | Hypertext Transfer Protocol Secure        | SRIS technical                              |
| SSH     | Secure Shell                              | SRIS technical, infrastructure              |
| SQL     | Structured Query Language                 | SRIS technical, data                        |
| NoSQL   | Not Only SQL                              | SRIS technical, data                        |
| ACID    | Atomicity, Consistency, Isolation, Durability | SRIS technical, data                    |
| CAP     | Consistency, Availability, Partition Tolerance | SRIS technical, distributed systems     |
| JWT     | JSON Web Token                            | SRIS technical, security                    |
| RBAC    | Role-Based Access Control                 | SRIS technical, security                    |
| OAuth   | Open Authorization                        | SRIS technical, security                    |
| SSO     | Single Sign-On                            | SRIS technical, security                    |
| MFA     | Multi-Factor Authentication               | SRIS technical, security                    |
| TLS     | Transport Layer Security                  | SRIS technical, security                    |
| SSL     | Secure Sockets Layer                      | SRIS technical, security (legacy reference) |
| DDD     | Domain-Driven Design                      | SRIS architecture                           |
| BFF     | Backend-For-Frontend                      | SRIS architecture                           |
| ACL     | Anti-Corruption Layer                     | SRIS architecture                           |
| CQRS    | Command Query Responsibility Segregation  | SRIS architecture                           |
| SOA     | Service-Oriented Architecture             | SRIS architecture                           |
| ESB     | Enterprise Service Bus                    | SRIS architecture (comparison only)         |
| SLA     | Service Level Agreement                   | SRIS architecture                           |
| SLO     | Service Level Objective                   | SRIS architecture                           |
| SLI     | Service Level Indicator                   | SRIS architecture                           |
| OTel    | OpenTelemetry                             | SRIS observability                          |
| W3C     | World Wide Web Consortium                 | SRIS observability                          |
| CI      | Continuous Integration                    | SRIS delivery                               |
| CD      | Continuous Deployment                     | SRIS delivery                               |

### 6.3 Project and Documentation Acronyms

| Acronym   | Expansion                                | Used In                                     |
| --------- | ---------------------------------------- | ------------------------------------------- |
| SRIS      | Sarathi Railway Information System        | Project core identifier                     |
| P1        | Phase 1                                   | Project phase code                          |
| BRD       | Business Requirements Document           | SRIS documentation                          |
| SRS       | Software Requirements Specification       | SRIS documentation                          |
| RTM       | Requirements Traceability Matrix          | SRIS documentation                          |
| NFR       | Non-Functional Requirement                | SRIS documentation                          |
| UAT       | User Acceptance Testing                   | SRIS documentation                          |
| QA        | Quality Assurance                         | SRIS process                                |
| DoD       | Definition of Done                        | SRIS process                                |
| DoR       | Definition of Ready                       | SRIS process                                |
| WIP       | Work In Progress                          | SRIS process                                |
| ADR       | Architecture Decision Record              | SRIS documentation                          |
| DPDP      | Digital Personal Data Protection Act, 2023 | SRIS compliance framework                  |

### 6.4 SRIS Category Codes

The expansions below are fixed by [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md) — Document ID and Category Scheme. They must not be altered.

| Code      | Expansion                          |
| --------- | ---------------------------------- |
| GOV       | Governance                         |
| DEV       | Developer Standards                |
| REQ       | Requirements                       |
| ARCH      | Architecture                       |
| DATA      | Data Design                        |
| API       | API Design                         |
| UI        | User Interface Design              |
| SEC       | Security                           |
| TEST      | Testing                            |
| INF       | Infrastructure                     |
| OPS       | Operations                         |
| PM        | Project Management                 |
| USR       | User Support                       |
| NFR-HOLD  | Non-Functional Requirements, Held  |
| NOTES-AI  | AI Working Notes                   |

---

## 7. Boundary Cases and Term Distinctions

The terms in this section are used in general English in ways that diverge from their railway or architectural meaning. The SRIS resolution states which meaning the project adopts and why.

| Term Pair                          | General Meaning                                    | Railway or Architectural Meaning                                                                                              | SRIS Resolution                                                                                                                            |
| ---------------------------------- | -------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Reservation vs booking             | Used interchangeably for securing a space.         | Booking is the whole transaction including payment. Reservation is the confirmed physical allocation of a berth or seat.        | SRIS uses booking for the passenger-facing state machine and reservation for the inventory-allocation module inside S3.                    |
| Train cancellation vs ticket cancellation | Both mean the journey is not happening.     | Train cancellation is administrative and triggers automatic refunds. Ticket cancellation is customer-initiated and incurs charges. | SRIS scopes cancellation to customer-initiated ticket cancellation. Train cancellation is deferred to Phase 2.                              |
| Waitlist vs RAC                    | Both imply a queue for unavailable space.          | Waitlist grants no boarding right. RAC grants boarding with a shared side-lower berth until a full berth frees up.             | SRIS models RAC as a distinct confirmed state that decrements a specific side-lower inventory unit.                                        |
| Berth vs seat                      | Both mean a place to sit.                          | A berth is a flat bed for sleeping. A seat is a chair for sitting.                                                              | SRIS models both as a single inventory unit with a boolean attribute that records whether the unit is a berth or a seat.                    |
| Class vs coach                     | Both mean the carriage the passenger travels in.   | A class is a service tier and fare bucket. A coach is the physical carriage assigned to a class.                                | SRIS separates the class definition from the coach blueprint in S2, so fare calculation uses the class independently of physical carriage.  |
| Route vs schedule                  | Both mean the path and timing of a journey.        | A route is the ordered set of stations and distances. A schedule binds times to a route.                                        | SRIS models them as separate entities in S2, so one route can serve multiple trains with different schedules.                              |
| Confirmation vs chart preparation  | Both mean the ticket is final.                     | Confirmation occurs at booking if inventory exists. Chart preparation is a batch that resolves quotas and waitlists near departure. | SRIS handles confirmation synchronously in REQ-008 and chart preparation as a scheduled batch in REQ-010.                                 |
| Hold vs reserve                    | Both mean securing inventory.                      | A hold is a temporary lock during payment. A reservation is the durable allocation after payment succeeds.                       | SRIS enforces hold as a transient lock with a time-to-live, and reservation as the durable state committed after payment.                   |
| Refund vs reversal                 | Both mean returning money.                         | A refund is a business action after cancellation, subject to charges. A reversal is a technical compensation when a step fails.  | SRIS records refund under REQ-007 as a business rule, and reversal under ARCH-015 as a saga compensation.                                   |
| Passenger vs customer              | Both mean the person using the service.            | A customer is the account holder. Passengers are the individuals travelling under one booking.                                   | SRIS manages customers in S1 IAM and passengers in S3 Reservation, linked by the PNR.                                                       |
| User vs employee vs admin          | Generic words for the person operating the system.| Employees configure the network. Administrators operate the underlying infrastructure.                                           | SRIS uses employee for the actor on the Employee Admin Console. The word admin is not used to avoid confusion with database administration. |
| General quota vs pooled quota      | Both mean a shared pool of seats.                  | General quota serves full-route passengers. Pooled quota serves intermediate-station passengers from a smaller shared pool.       | SRIS models both as separate decrementing pools in the S3 seat matrix, with no logical overlap during availability calculation.             |
| Entity vs value object             | Technical terms without railway meaning.           | Entity has identity that persists across changes. Value object is immutable and defined by its attributes.                        | SRIS follows Domain-Driven Design. Bookings and passengers are entities. Money and PNR strings are value objects.                            |
| Saga vs distributed transaction    | Both coordinate changes across systems.            | A distributed transaction uses two-phase commit and blocks. A saga is a sequence of local transactions with compensations.        | SRIS avoids two-phase commit due to memory constraints and standardises on the saga pattern.                                                |
| Token vs credential                | Both grant access to a secured system.             | Credential is the secret used at login. Token is the signed artefact issued after login.                                        | SRIS accepts credentials only in S1 IAM. Downstream services accept tokens only.                                                            |

---

## 8. Approval

| Role           | Name        | Decision | Date       |
| -------------- | ----------- | -------- | ---------- |
| Lead Architect | Koushal Jha | Approved | 2026-10-12 |

---

## Revision History

| Version | Date       | Author      | Change           |
| ------- | ---------- | ----------- | ---------------- |
| 1.0     | 2026-10-12 | Koushal Jha | Initial release. |

---

## Appendix A: Not Applicable

Not applicable.

---

## Appendix B: Related Documents

### B.1 Directly Referenced Documents

| Seq  | Document ID                                                                                                                 | Document Name                                | Wave | Pri | Tag     |
| ---- | --------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------- | ---- | --- | ------- |
| 0.0  | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md)                        | Documentation Index and Navigation Map       | 0    | P0  | UNBLOCK |
| 0.1  | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)                                  | Document Template Standard                   | 0    | P0  | UNBLOCK |
| 0.2  | [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)                               | Document ID and Category Scheme              | 0    | P1  | UNBLOCK |
| 0.3  | [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md)                            | Document Cross-Reference Standard            | 0    | P1  | UNBLOCK |
| 0.4  | [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)                             | Project Vision and Scope Document            | 0    | P0  | UNBLOCK |
| 0.6  | [SRIS-P1-GOV-007](../wave-0-project-foundation/SRIS-P1-GOV-007_ProjectManagementPlan.md)                                     | Project Management Plan                      | 0    | P0  | UNBLOCK |
| 1.2  | [SRIS-P1-REQ-002](./SRIS-P1-REQ-002_BusinessRequirementsDocumentBRD.md)                                                       | Business Requirements Document (BRD)         | 1    | P0  | UNBLOCK |
| 1.3  | [SRIS-P1-REQ-003](./SRIS-P1-REQ-003_CapabilityCatalogFinal.md)                                                                | Capability Catalog (Final)                   | 1    | P0  | UNBLOCK |
| 1.7  | [SRIS-P1-REQ-007](./SRIS-P1-REQ-007_DomainRulesFareCalculation.md)                                                            | Domain Rules: Fare Calculation               | 1    | P1  | FOLLOW  |
| 1.8  | [SRIS-P1-REQ-008](./SRIS-P1-REQ-008_DomainRulesTicketing.md)                                                                  | Domain Rules: Ticketing                      | 1    | P1  | FOLLOW  |
| 1.9  | [SRIS-P1-REQ-009](./SRIS-P1-REQ-009_DomainRulesWaitlistAndCancellation.md)                                                    | Domain Rules: Waitlist and Cancellation      | 1    | P1  | FOLLOW  |
| 1.10 | [SRIS-P1-REQ-010](./SRIS-P1-REQ-010_DomainRulesChartPreparation.md)                                                           | Domain Rules: Chart Preparation              | 1    | P1  | FOLLOW  |
| 1.11 | [SRIS-P1-REQ-011](./SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)                                                     | Domain Rules: Seat Matrix and Inventory      | 1    | P1  | FOLLOW  |
| 2.1  | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md)                                    | Microservices Identification                 | 2    | P0  | UNBLOCK |
| 2.3  | [SRIS-P1-ARCH-003](../wave-2-architecture/SRIS-P1-ARCH-003_SystemArchitectureDocument.md)                                     | System Architecture Document                 | 2    | P0  | UNBLOCK |
| 2.4  | [SRIS-P1-ARCH-004](../wave-2-architecture/SRIS-P1-ARCH-004_BoundedContextMap.md)                                              | Bounded Context Map                          | 2    | P0  | UNBLOCK |
| 2.5  | [SRIS-P1-ARCH-005](../wave-2-architecture/SRIS-P1-ARCH-005_DomainModelDocument.md)                                            | Domain Model Document                        | 2    | P0  | UNBLOCK |
| 2.7  | [SRIS-P1-ARCH-007](../wave-2-architecture/SRIS-P1-ARCH-007_ArchitectureDecisionRecordsMasterIndex.md)                         | Architecture Decision Records — Master Index | 2    | P1  | FOLLOW  |
| 2.9  | [SRIS-P1-ARCH-009](../wave-2-architecture/SRIS-P1-ARCH-009_ServiceInteractionAndCommunicationDesign.md)                       | Service Interaction and Communication Design | 2    | P0  | UNBLOCK |
| 2.12 | [SRIS-P1-ARCH-012](../wave-2-architecture/SRIS-P1-ARCH-012_ObservabilityAndMonitoringDesignOTelW3C.md)                        | Observability and Monitoring Design (OTel/W3C) | 2  | P0  | UNBLOCK |
| 2.14 | [SRIS-P1-ARCH-014](../wave-2-architecture/SRIS-P1-ARCH-014_DistributedConcurrencyAndLockingStrategy.md)                       | Distributed Concurrency and Locking Strategy | 2    | P0  | UNBLOCK |
| 2.15 | [SRIS-P1-ARCH-015](../wave-2-architecture/SRIS-P1-ARCH-015_DistributedTransactionAndSagaPatternDesign.md)                     | Distributed Transaction and Saga Pattern Design | 2 | P0  | UNBLOCK |
| 3.2  | [SRIS-P1-DATA-002](../wave-3-detailed-design/SRIS-P1-DATA-002_LogicalDataModelPerService.md)                                  | Logical Data Model (per service)              | 3    | P0  | UNBLOCK |
| 3.3  | [SRIS-P1-DATA-003](../wave-3-detailed-design/SRIS-P1-DATA-003_PhysicalDatabaseSchemaDocument.md)                              | Physical Database Schema Document            | 3    | P0  | UNBLOCK |
| 3.4  | [SRIS-P1-DATA-004](../wave-3-detailed-design/SRIS-P1-DATA-004_DataDictionary.md)                                              | Data Dictionary                              | 3    | P0  | UNBLOCK |
| 3.6  | [SRIS-P1-DATA-006](../wave-3-detailed-design/SRIS-P1-DATA-006_IndexAndConstraintSpecification.md)                             | Index and Constraint Specification           | 3    | P1  | FOLLOW  |
| 3.10 | [SRIS-P1-DATA-010](../wave-3-detailed-design/SRIS-P1-DATA-010_DataMigrationStrategy.md)                                       | Data Migration Strategy                      | 3    | P2  | FOLLOW  |
| 3.11 | [SRIS-P1-DATA-011](../wave-3-detailed-design/SRIS-P1-DATA-011_DataRetentionAndArchivalPolicy.md)                              | Data Retention and Archival Policy           | 3    | P2  | FOLLOW  |
| 3.12 | [SRIS-P1-DATA-012](../wave-3-detailed-design/SRIS-P1-DATA-012_SeedDataAndReferenceDataSpecification.md)                       | Seed Data and Reference Data Specification   | 3    | P2  | FOLLOW  |
| 3.14 | [SRIS-P1-API-001](../wave-3-detailed-design/SRIS-P1-API-001_APIContractDocumentOpenAPI.md)                                    | API Contract Document (OpenAPI)              | 3    | P0  | UNBLOCK |
| 3.16 | [SRIS-P1-API-003](../wave-3-detailed-design/SRIS-P1-API-003_EventSchemaDocumentAsyncAPI.md)                                   | Event Schema Document (AsyncAPI)             | 3    | P0  | UNBLOCK |
| 3.17 | [SRIS-P1-API-004](../wave-3-detailed-design/SRIS-P1-API-004_IntegrationDesignDocument.md)                                     | Integration Design Document                  | 3    | P0  | UNBLOCK |
| 3.18 | [SRIS-P1-API-005](../wave-3-detailed-design/SRIS-P1-API-005_IdempotencyAndRetryPolicySpecification.md)                        | Idempotency and Retry Policy Specification   | 3    | P0  | UNBLOCK |
| 3.19 | [SRIS-P1-API-006](../wave-3-detailed-design/SRIS-P1-API-006_APIErrorCodeCatalog.md)                                           | API Error Code Catalog                       | 3    | P1  | FOLLOW  |
| 3.21 | [SRIS-P1-API-008](../wave-3-detailed-design/SRIS-P1-API-008_APIRateLimitingAndThrottlingRules.md)                             | API Rate Limiting and Throttling Rules       | 3    | P2  | FOLLOW  |
| 3.22 | [SRIS-P1-API-009](../wave-3-detailed-design/SRIS-P1-API-009_EventCatalog.md)                                                  | Event Catalog                                | 3    | P1  | FOLLOW  |
| 3.26 | [SRIS-P1-API-013](../wave-3-detailed-design/SRIS-P1-API-013_APIVersioningAndDeprecationPolicy.md)                             | API Versioning and Deprecation Policy        | 3    | P2  | FOLLOW  |
| 3.39 | [SRIS-P1-SEC-001](../wave-3-detailed-design/SRIS-P1-SEC-001_AuthenticationAndAuthorizationDesign.md)                         | Authentication and Authorization Design      | 3    | P1  | FOLLOW  |
| 3.40 | [SRIS-P1-SEC-002](../wave-3-detailed-design/SRIS-P1-SEC-002_RBACMatrix.md)                                                    | RBAC Matrix                                  | 3    | P1  | FOLLOW  |
| 3.41 | [SRIS-P1-SEC-003](../wave-3-detailed-design/SRIS-P1-SEC-003_JWTTokenDesignAndClaims.md)                                       | JWT Token Design and Claims                  | 3    | P1  | FOLLOW  |
| 3.42 | [SRIS-P1-SEC-004](../wave-3-detailed-design/SRIS-P1-SEC-004_ThreatModel.md)                                                   | Threat Model                                 | 3    | P1  | FOLLOW  |
| 3.44 | [SRIS-P1-SEC-006](../wave-3-detailed-design/SRIS-P1-SEC-006_DPDPActComplianceFrameworkPhase1Scoped.md)                        | DPDP Act Compliance Framework (Phase 1 scoped) | 3  | P0  | UNBLOCK |
| 3.45 | [SRIS-P1-SEC-007](../wave-3-detailed-design/SRIS-P1-SEC-007_ConsentManagementDataModelPhase1Scoped.md)                        | Consent Management Data Model (Phase 1 scoped) | 3  | P0  | UNBLOCK |
| 3.46 | [SRIS-P1-SEC-008](../wave-3-detailed-design/SRIS-P1-SEC-008_SecretsManagementPlan.md)                                        | Secrets Management Plan                      | 3    | P1  | FOLLOW  |
| 3.47 | [SRIS-P1-SEC-009](../wave-3-detailed-design/SRIS-P1-SEC-009_PasswordAndCredentialPolicy.md)                                   | Password and Credential Policy               | 3    | P2  | FOLLOW  |
| 3.49 | [SRIS-P1-SEC-012](../wave-3-detailed-design/SRIS-P1-SEC-012_DataClassificationRegister.md)                                   | Data Classification Register                 | 3    | P0  | UNBLOCK |
| 3.50 | [SRIS-P1-SEC-013](../wave-3-detailed-design/SRIS-P1-SEC-013_SecureCodingStandards.md)                                        | Secure Coding Standards                      | 3    | P0  | UNBLOCK |
| 4.1  | [SRIS-P1-TEST-001](../wave-4-testing/SRIS-P1-TEST-001_TestStrategyDocument.md)                                                | Test Strategy Document                       | 4    | P0  | UNBLOCK |
| 4.3  | [SRIS-P1-TEST-003](../wave-4-testing/SRIS-P1-TEST-003_TestCasesFunctional.md)                                                 | Test Cases (Functional)                      | 4    | P0  | UNBLOCK |
| 4.4  | [SRIS-P1-TEST-004](../wave-4-testing/SRIS-P1-TEST-004_ConsumerDrivenContractTestingStrategy.md)                               | Consumer-Driven Contract Testing Strategy    | 4    | P1  | UNBLOCK |
| 4.8  | [SRIS-P1-TEST-008](../wave-4-testing/SRIS-P1-TEST-008_PerformanceTestPlan.md)                                                 | Performance Test Plan                        | 4    | P1  | FOLLOW  |
| 4.9  | [SRIS-P1-TEST-009](../wave-4-testing/SRIS-P1-TEST-009_LoadTestPlan.md)                                                        | Load Test Plan                               | 4    | P1  | FOLLOW  |
| 4.10 | [SRIS-P1-TEST-010](../wave-4-testing/SRIS-P1-TEST-010_IntegrationTestPlan.md)                                                 | Integration Test Plan                        | 4    | P1  | FOLLOW  |
| 4.11 | [SRIS-P1-TEST-011](../wave-4-testing/SRIS-P1-TEST-011_UserAcceptanceTestUATPlan.md)                                           | User Acceptance Test (UAT) Plan              | 4    | P1  | FOLLOW  |
| 4.13 | [SRIS-P1-TEST-013](../wave-4-testing/SRIS-P1-TEST-013_DefectManagementProcess.md)                                            | Defect Management Process                    | 4    | P2  | FOLLOW  |
| 5.1  | [SRIS-P1-INF-001](../wave-5-devops-operations/SRIS-P1-INF-001_InfrastructureAndTechnologyDocument.md)                         | Infrastructure and Technology Document       | 5    | P0  | UNBLOCK |
| 5.2  | [SRIS-P1-INF-002](../wave-5-devops-operations/SRIS-P1-INF-002_EnvironmentStrategyDocument.md)                                 | Environment Strategy Document                | 5    | P0  | UNBLOCK |
| 5.3  | [SRIS-P1-INF-003](../wave-5-devops-operations/SRIS-P1-INF-003_CICDPipelineDesign.md)                                          | CI/CD Pipeline Design                        | 5    | P0  | UNBLOCK |
| 5.12 | [SRIS-P1-OPS-001](../wave-5-devops-operations/SRIS-P1-OPS-001_DeploymentGuide.md)                                             | Deployment Guide                             | 5    | P1  | FOLLOW  |
| 5.16 | [SRIS-P1-OPS-005](../wave-5-devops-operations/SRIS-P1-OPS-005_SLODocument.md)                                                 | SLO Document                                 | 5    | P2  | FOLLOW  |
| 5.18 | [SRIS-P1-OPS-007](../wave-5-devops-operations/SRIS-P1-OPS-007_ReleaseManagementPlan.md)                                       | Release Management Plan                      | 5    | P1  | FOLLOW  |
| 6.3  | [SRIS-P1-DEV-005](../wave-6-developer-standards/SRIS-P1-DEV-005_GitAndBranchingStrategy.md)                                   | Git and Branching Strategy                   | 6    | P0  | UNBLOCK |
| 6.4  | [SRIS-P1-DEV-006](../wave-6-developer-standards/SRIS-P1-DEV-006_DefinitionOfDoneDoD.md)                                       | Definition of Done (DoD)                     | 6    | P1  | FOLLOW  |
| 6.5  | [SRIS-P1-DEV-007](../wave-6-developer-standards/SRIS-P1-DEV-007_DefinitionOfReadyDoR.md)                                      | Definition of Ready (DoR)                    | 6    | P1  | FOLLOW  |
| 6.6  | [SRIS-P1-DEV-008](../wave-6-developer-standards/SRIS-P1-DEV-008_CodeReviewChecklist.md)                                       | Code Review Checklist                        | 6    | P1  | FOLLOW  |
| 6.12 | [SRIS-P1-DEV-015](../wave-6-developer-standards/SRIS-P1-DEV-015_CommitMessageAndPullRequestConvention.md)                     | Commit Message and Pull Request Convention   | 6    | P0  | UNBLOCK |

### B.2 Documents That Reference This Document

Every requirements, architecture, data, API, security, testing, infrastructure, operations, and developer-standards document in the register uses the vocabulary defined here. The citing documents are therefore a whole group, and the complete list is in the register described in [B.5](#b5-master-documentation-index).

### B.3 Documents This Document Depends On (Upstream)

| Seq | Document ID                                                                            | Document Name                          | Dependency Type |
| --- | -------------------------------------------------------------------------------------- | -------------------------------------- | --------------- |
| 0.0 | [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md)  | Documentation Index and Navigation Map | Soft            |
| 0.1 | [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)            | Document Template Standard             | Hard            |
| 0.2 | [SRIS-P1-GOV-003](../wave-0-project-foundation/SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)         | Document ID and Category Scheme        | Hard            |
| 0.3 | [SRIS-P1-GOV-004](../wave-0-project-foundation/SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md)      | Document Cross-Reference Standard      | Hard            |
| 0.4 | [SRIS-P1-GOV-005](../wave-0-project-foundation/SRIS-P1-GOV-005_ProjectVisionAndScopeDocument.md)       | Project Vision and Scope Document      | Soft            |

### B.4 Documents This Document Unblocks (Downstream)

Every requirements, architecture, data, API, security, testing, infrastructure, operations, and developer-standards document written after this glossary is written against its vocabulary. The dependent documents are therefore a whole group, and the complete list is in the register described in [B.5](#b5-master-documentation-index).

### B.5 Master Documentation Index

The complete list of Phase 1 documents is in [SRIS-P1-GOV-001](../wave-0-project-foundation/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

### B.6 External Reference Documents

None.

### B.7 Document Conventions

The conventions for Priority and Tag values are defined in [Section 9](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md#9-vocabulary-standards) of [SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.

---

**End of Document**