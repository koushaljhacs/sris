<div align="center">

![Wave](https://img.shields.io/badge/Wave-0-0550AE?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-GOV-6e7781?style=for-the-badge)

</div>

# Document Cross-Reference Standard

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** 1.0 | **Date:** 2026-10-12 | **Document ID:** SRIS-P1-GOV-004

| Field              | Value                                                                  |
| ------------------ | ---------------------------------------------------------------------- |
| Title              | Document Cross-Reference Standard                                      |
| Software           | SRIS                                                                   |
| Software Full Form | Sarathi Railway Information System                                     |
| Team Codename      | Project Sarathi                                                        |
| Document ID        | SRIS-P1-GOV-004                                                        |
| Task               | Define the standard for citing, linking, and listing related documents |
| Document Type      | Standard Document                                                      |
| Milestone          | Phase 1 Foundation                                                     |
| Classification     | Internal                                                               |
| Version            | 1.0                                                                    |
| Date               | 2026-10-12                                                             |
| Author             | Koushal Jha, Lead Architect                                            |
| Approved By        | Koushal Jha, Lead Architect                                            |
| Approval Date      | 2026-10-12                                                             |
| Supersedes         | None (first version)                                                   |
| Related Documents  | See Appendix B                                                         |
| Affiliation        | Independent · Not affiliated with CRIS, IRCTC, or Indian Railways      |

---

## Table of Contents

1. [Introduction](#1-introduction)
   - [1.1 Purpose](#11-purpose)
   - [1.2 Scope](#12-scope)
   - [1.3 Audience](#13-audience)
   - [1.4 Definitions and Terms](#14-definitions-and-terms)
2. [Reference Types and Citation Format](#2-reference-types-and-citation-format)
   - [2.1 Reference Types](#21-reference-types)
   - [2.2 Document Citation](#22-document-citation)
   - [2.3 First and Later Mentions](#23-first-and-later-mentions)
   - [2.4 Section References](#24-section-references)
   - [2.5 Lists and Ranges](#25-lists-and-ranges)
   - [2.6 Prohibited Forms](#26-prohibited-forms)
3. [Relative Path Rules](#3-relative-path-rules)
   - [3.1 Link Base](#31-link-base)
   - [3.2 Path Computation](#32-path-computation)
   - [3.3 Same Wave and Other Wave Links](#33-same-wave-and-other-wave-links)
   - [3.4 Wave Folder Names](#34-wave-folder-names)
   - [3.5 Target File Name](#35-target-file-name)
   - [3.6 Absolute Paths and URLs](#36-absolute-paths-and-urls)
4. [Planned Documents](#4-planned-documents)
   - [4.1 Single Reference Form](#41-single-reference-form)
   - [4.2 Deriving the Registered Path](#42-deriving-the-registered-path)
   - [4.3 Target Not Yet Present](#43-target-not-yet-present)
   - [4.4 Anchors on Planned Documents](#44-anchors-on-planned-documents)
   - [4.5 When the File Is Created](#45-when-the-file-is-created)
   - [4.6 Changes to a Registration](#46-changes-to-a-registration)
5. [Appendix B Structure](#5-appendix-b-structure)
   - [5.1 Fixed Layout](#51-fixed-layout)
   - [5.2 Common Column Rules](#52-common-column-rules)
   - [5.3 Directly Referenced Documents (B.1)](#53-directly-referenced-documents-b1)
   - [5.4 Referencing Documents (B.2)](#54-referencing-documents-b2)
   - [5.5 Upstream Documents (B.3)](#55-upstream-documents-b3)
   - [5.6 Downstream Documents (B.4)](#56-downstream-documents-b4)
   - [5.7 Master Documentation Index (B.5)](#57-master-documentation-index-b5)
   - [5.8 External Reference Documents (B.6)](#58-external-reference-documents-b6)
   - [5.9 Document Conventions (B.7)](#59-document-conventions-b7)
   - [5.10 Choosing Between Table, Prose, and None](#510-choosing-between-table-prose-and-none)
6. [Special Cases](#6-special-cases)
   - [6.1 Code Blocks and Inline Code](#61-code-blocks-and-inline-code)
   - [6.2 Tables](#62-tables)
   - [6.3 Metadata Table and Blockquote](#63-metadata-table-and-blockquote)
   - [6.4 Headings](#64-headings)
   - [6.5 Appendix A and Later Appendices](#65-appendix-a-and-later-appendices)
   - [6.6 Self References](#66-self-references)
7. [Anchor Generation](#7-anchor-generation)
   - [7.1 Derivation Algorithm](#71-derivation-algorithm)
   - [7.2 Transformation Examples](#72-transformation-examples)
   - [7.3 Title Case and Capitalisation](#73-title-case-and-capitalisation)
   - [7.4 Special Characters](#74-special-characters)
   - [7.5 Duplicate Headings](#75-duplicate-headings)
   - [7.6 Link Targets](#76-link-targets)
   - [7.7 Stability](#77-stability)
8. [Validation](#8-validation)
   - [8.1 Conformance Checks](#81-conformance-checks)
   - [8.2 Link Pattern](#82-link-pattern)
   - [8.3 Adoption and Maintenance](#83-adoption-and-maintenance)
9. [Worked Examples](#9-worked-examples)
   - [9.1 Correct Examples](#91-correct-examples)
   - [9.2 Incorrect Examples](#92-incorrect-examples)
10. [Approval](#10-approval)

- [Revision History](#revision-history)
- [Appendix A: Not Applicable](#appendix-a-not-applicable)
- [Appendix B: Related Documents](#appendix-b-related-documents)

---

## 1. Introduction

### 1.1 Purpose

This document is the standalone cross-reference standard for the Phase 1 documents of SRIS (Sarathi Railway Information System). The cross-reference rules are stated in summary in [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard. This document expands them into rules that an author can apply and a script can check, and it is written against version 1.2 of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md).

It fixes the citation format for every reference type, the relative path rules, the handling of planned documents, the structure of Appendix B, the special cases, and the generation of anchors. Each rule has an identifier and a rationale, so that a reviewer can cite the rule and an author can see why it exists.

### 1.2 Scope

**In scope**

- The citation formats for document references, section references, lists, and ranges.
- The relative path rules for links between Phase 1 documents, including the complete list of wave folder names.
- The handling of planned documents, whose files may not yet exist at the path that links name.
- The structure, columns, and forms of the seven subsections of Appendix B.
- The special cases of code, tables, metadata, headings, appendices, and self references.
- The generation of anchors from headings.
- The conformance checks and worked examples.

**Out of scope**

- The document template, the metadata fields, the numbering, and the style rules, which belong to [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md).
- The Document ID format, the category codes, and the sequence numbers, which belong to [SRIS-P1-GOV-003](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md) — Document ID and Category Scheme.
- The register of documents with their IDs, titles, waves, priorities, and tags, which belongs to [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.
- References to files that are not Phase 1 register documents, such as the repository README file, which have no Document ID.
- The implementation of any link-checking script or hook.
- References to documents of later phases.

### 1.3 Audience

- **Authors:** apply the rules when they write a citation, a link, or an Appendix B.
- **Reviewers:** use the conformance checks in [Section 8.1](#81-conformance-checks) during the Links check of the review workflow in [Section 12.1](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#121-approval-workflow) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md).
- **Tool authors:** build link checks from the derivation in [Section 7.1](#71-derivation-algorithm) and the patterns in [Section 8.2](#82-link-pattern).
- **Lead Architect:** maintains this standard and approves each change to it.
- **Evaluators and Supervisor:** check that cross-references are consistent across the documentation set.

### 1.4 Definitions and Terms

The terms below have these meanings wherever they appear in this document.

| Term                | Meaning                                                                                                                                                                               |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Reference           | A mention of a Phase 1 document by its Document ID, in any form.                                                                                                                      |
| Citation            | The written form of a reference: a link, and a title where this standard requires one.                                                                                                |
| Containing Document | The document in which a reference is written.                                                                                                                                         |
| Target Document     | The document to which a reference points.                                                                                                                                             |
| Registered Path     | The relative path to the Target Document that follows from its register entry, as derived in [Section 3](#3-relative-path-rules) and [Section 4.2](#42-deriving-the-registered-path). |
| Existing Document   | A document whose file is committed at its Registered Path.                                                                                                                            |
| Planned Document    | A document that has a register entry and whose file is not yet committed at its Registered Path.                                                                                      |
| Resolved Link       | A link whose target file exists at the path that the link names.                                                                                                                      |
| Unresolved Link     | A link whose target file does not yet exist at the path that the link names.                                                                                                          |
| Anchor              | The fragment after the hash sign in a link, which selects a heading in the target file.                                                                                               |
| Self Reference      | A mention of the Containing Document's own Document ID.                                                                                                                               |

---

## 2. Reference Types and Citation Format

### 2.1 Reference Types

Seven reference types cover every mention of a document or a section in a Phase 1 document.

| Type | Used When                                                                   |
| ---- | --------------------------------------------------------------------------- |
| T1   | A document is mentioned for the first time in a section.                    |
| T2   | The same document is mentioned again in that section.                       |
| T3   | A section of another document is cited. The document part follows T1 or T2. |
| T4   | A section or appendix of the same document is cited.                        |
| T5   | A document is named in a table row that has a Document Name column.         |
| T6   | A group of consecutive documents of one category is cited in a table cell.  |
| T7   | A source outside the project, such as a published standard, is cited.       |

### 2.2 Document Citation

These rules apply to every citation of a Phase 1 document.

- **CF-1** A reference to a document uses the full Document ID as the link text. Rationale: the ID is permanent once the document is committed ([Section 4.4](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md#44-permanence-gaps-and-reuse) of [SRIS-P1-GOV-003](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md) — Document ID and Category Scheme), whereas titles and file names can change, so it is the only stable label.
- **CF-2** The link target is the Registered Path of the Target Document. Rationale: one derivation makes every link to a document identical in form, which lets a script check it with a single pattern ([Section 8.2](#82-link-pattern)).
- **CF-3** On first mention the citation continues with one space, an em dash, one space, and the title exactly as the register gives it. Rationale: the title lets a reader recognise the document without following the link, and the register is the one place where the title is fixed.
- **CF-4** The em dash is the only separator between a citation and its title. Rationale: Document IDs contain hyphens, and two category codes contain a hyphen of their own ([Section 2.5](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md#25-reading-hyphenated-category-codes) of [SRIS-P1-GOV-003](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)), so any other separator would blur where the ID ends.
- **CF-5** A document is never identified by its title alone, by a short form made of the category and the number, or by its file name. A phrase that names a concept defined elsewhere, such as the register, is not a reference, but the section cites the owning document where it first relies on the concept. Rationale: a title or short form cannot be followed, matched by a script, or kept correct when a title changes.

### 2.3 First and Later Mentions

[Section 6.1](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#61-citation-format) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard sets the first-mention rule. The rules below fix its edges.

- **CF-6** For the first-mention rule, a section is each level-2 section and each subsection of Appendix B (B.1 to B.7). Rationale: the subsections of Appendix B are read on their own as look-ups, so each must be able to name a document without relying on an earlier subsection.
- **CF-7** Mentions are ordered by their position in the file, across prose, list items, and table cells. Rationale: a position-based order can be applied by a script without interpreting the text.
- **CF-8** A title in a Document Name column satisfies the title requirement for that row. A table without such a column carries the title in the cell, on first mention. Rationale: the title is then given once and is never repeated beside a column that already holds it.
- **CF-9** A later mention in a section may omit the title but never the link. Rationale: a reader can land on any paragraph, for example from a search result, and every ID there must stay navigable.

### 2.4 Section References

- **CF-10** A reference to a section of another document uses T3. The link text is the section number, the anchor is derived under [Section 7](#7-anchor-generation), and the document part follows CF-6 to CF-9. Rationale: the section number tells the reader where the link leads, and the anchor is the only way to reach it.
- **CF-11** A reference to a numbered section of the same document uses T4 with the link text Section followed by the number. A reference to an appendix or an appendix subsection uses the link text Appendix A or B.5. The word Section followed by a number is never written outside a link. The name of a part of the document used as a subject, as in the structure of Appendix B, is not a pointer and needs no link. Rationale: a link fails visibly when a heading changes, whereas a bare number goes stale without any signal.
- **CF-12** Each section number in a reference to several sections is linked separately. Rationale: a single link cannot point to two headings, and a partly linked range hides which end is unchecked.

### 2.5 Lists and Ranges

- **CF-13** A list of documents is a bullet list or a table, with one T1 or T2 citation, or one T5 cell, for each item. It is not written as a run-in sentence. Rationale: each citation may carry a title, and a sentence with several titles cannot be read or checked reliably.
- **CF-14** A range uses T6. It is written only in table cells. Both endpoints are linked, are joined by the word to, belong to one category, and ascend in sequence number. No title is given in a range, and no dash joins the two IDs. Rationale: IDs contain hyphens, so a dash between two IDs cannot be told from the hyphens inside them, and consecutive IDs of one category are the only range that the register can confirm.

### 2.6 Prohibited Forms

Each form below is a defect, whether or not the target file exists.

| Form                                                                                        | Why It Is a Defect                               |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------ |
| A Document ID in prose or in a table cell without a link                                    | It cannot be followed or checked (CF-1, CF-5).   |
| A link whose text is a short form of the ID                                                 | The text does not equal the full ID (CF-1).      |
| A title or file name used in place of the ID                                                | It cannot be matched to a register entry (CF-5). |
| A status marker, placeholder, or wording that says the target is absent or pending          | It records a status in the wrong place (PL-2).   |
| A link text such as here or this document                                                   | The link no longer names the ID (CF-1).          |
| A link to the register or to a folder in place of the document                              | It does not identify the target (CF-2).          |
| A link wrapped in code formatting                                                           | The link does not render (SC-7).                 |
| An absolute URL, a drive letter, a backslash, or a root-relative path to a project document | The link is not portable (PA-10).                |
| A file name with a version, or a link to a PDF                                              | The target name changes at each revision (PA-9). |

---

## 3. Relative Path Rules

### 3.1 Link Base

Every Phase 1 document sits directly inside one wave folder, with no further nesting ([Section 7.2](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md#72-folder-structure) of [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map). A Registered Path therefore has one of exactly two shapes, and the rules in this section decide between them.

- **PA-1** Every link to a Phase 1 document is relative to the folder of the Containing Document, as [Section 6.2](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#62-relative-link-rules) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard requires. Rationale: a relative link survives a clone, a fork, and a move of the whole repository, which an absolute path does not.
- **PA-2** A path contains at most one ../ segment. Rationale: the structure is two levels deep and flat, so a longer path points at a folder that does not exist.

### 3.2 Path Computation

- **PA-3** The prefix of a path is decided by comparing the wave folder of the Containing Document with the wave folder of the Target Document. Rationale: a comparison of folders gives one answer for every pair of documents, so authors do not choose a form by feel.

The path is built in five steps:

1. Read the wave of the Containing Document and the wave of the Target Document from the register.
2. If the two waves are equal, start the path with `./`.
3. If they differ, start the path with `../`, then the wave folder of the Target Document from [Section 3.4](#34-wave-folder-names), then `/`.
4. Append the target file name from [Section 3.5](#35-target-file-name).
5. Append an anchor only where [Section 4.4](#44-anchors-on-planned-documents) and [Section 7.6](#76-link-targets) allow it.

### 3.3 Same Wave and Other Wave Links

- **PA-4** A link between two documents of the same wave uses the `./` prefix and never the form that names the wave folder, even though that form would resolve. Rationale: one canonical path for each pair of documents lets a script compare paths as text, and a document that moves to another wave then needs only its prefixes changed.
- **PA-5** The wave folder of the Target Document is the wave that the register records, never a folder inferred from the category code. Rationale: [Section 5.2](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md#52-folder-structure) of [SRIS-P1-GOV-003](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md) — Document ID and Category Scheme states that the wave, not the category, decides the folder.

For example, [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md) — Security Testing Plan has category SEC but sits in Wave 4, and [SRIS-P1-DEV-013](../wave-7-project-tracking/SRIS-P1-DEV-013_SkillMatrix.md) — Skill Matrix has category DEV but sits in Wave 7.

### 3.4 Wave Folder Names

The ten wave folder names are listed below. The list is closed for Phase 1.

| Wave | Name                  | Folder Name                 |
| ---- | --------------------- | --------------------------- |
| 0    | Project Foundation    | wave-0-project-foundation   |
| 1    | Requirements          | wave-1-requirements         |
| 2    | Architecture          | wave-2-architecture         |
| 3    | Detailed Design       | wave-3-detailed-design      |
| 4    | Testing               | wave-4-testing              |
| 5    | DevOps and Operations | wave-5-devops-operations    |
| 6    | Developer Standards   | wave-6-developer-standards  |
| 7    | Project Tracking      | wave-7-project-tracking     |
| 8    | User and Support      | wave-8-user-support         |
| 9    | Supporting Artifacts  | wave-9-supporting-artifacts |

- **PA-6** Only these ten folder names are valid in a link, and each is written exactly as shown. A change to a folder name is a change to the register and to this table, made in one approved revision of each. Rationale: the register defines ten waves ([Section 3](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md#3-complete-document-register) of [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md)), so a name outside the list is a typing error, and two lists that drift apart would break links without any signal.

### 3.5 Target File Name

- **PA-7** The target file name is the Document ID, an underscore, the register title in PascalCase, and the extension .md, built by the steps in [Section 11.1](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#111-source-markdown-naming) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md). Where the computed name and the file name in the register link differ, the register link is used and the difference is corrected in the register. Rationale: the register is the one source that every author copies from, so a disagreement must be resolved at the source.

Punctuation in a title is removed, as these register titles show:

| Register Title                                 | Name Part of the File                   |
| ---------------------------------------------- | --------------------------------------- |
| Technology Stack ADR                           | TechnologyStackADR                      |
| Document ID and Category Scheme                | DocumentIDAndCategoryScheme             |
| Observability and Monitoring Design (OTel/W3C) | ObservabilityAndMonitoringDesignOTelW3C |
| API Request / Response Examples                | APIRequestResponseExamples              |

- **PA-8** The file name in a link matches the file name in the repository in every letter, including its case. Rationale: the hosting platform resolves paths with case, while some local file systems do not, so a case error can pass a local check and fail after publication.
- **PA-9** The file name carries no version, and the target is always the source markdown file and never a PDF. Rationale: versions are held in the metadata table, and PDF files are frozen deliverables whose names carry the version ([Section 11.2](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#112-pdf-naming) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md)), so a link to one would go stale at the next revision.

### 3.6 Absolute Paths and URLs

- **PA-10** A link to a project document is not an absolute URL, does not start with a drive letter, a backslash, or a slash, and does not contain a backslash. An absolute URL is allowed only for a source outside the project (T7). Rationale: an absolute URL ties a document to one host and one branch, and a backslash or drive letter works only on the machine that wrote it.

---

## 4. Planned Documents

### 4.1 Single Reference Form

Documents carry no status field ([Section 3.3](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#33-formatting-rules) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard), so a reader cannot tell from a document whether a cited file exists. One reference form for existing and planned documents removes the need to know.

- **PL-1** Every Document ID in prose and in appendices is a hyperlink, whether the target file exists in the repository yet or not. A planned document is referenced exactly as an existing document: the full ID as link text, linked to the Registered Path, with the title on first mention. This holds in prose, in tables, and in Appendix B. Rationale: a single form means that creating the file requires no edit in any document that cites it.
- **PL-2** No status marker, placeholder, or plain-text ID stands in for a link, and no wording beside a citation says that the target is absent or pending. Rationale: a marker is a status recorded in the wrong place, and it would have to be removed from every citing document when the file appears.

### 4.2 Deriving the Registered Path

- **PL-3** A document is referenced only if its ID is in the register. An ID that is not there is allocated first, as [Section 4.3](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md#43-allocation) of [SRIS-P1-GOV-003](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md) — Document ID and Category Scheme requires. Rationale: the register entry fixes the ID, the title, and the wave, and without it no Registered Path exists.
- **PL-4** The link target of a planned document is its Registered Path, derived from the register entry by the steps in [Section 3.2](#32-path-computation). For a Containing Document in Wave 0, the link in the register entry can be copied unchanged. Rationale: a path that cannot be checked by following it must be derived, not typed from memory.

### 4.3 Target Not Yet Present

A link to a planned document is an unresolved link until its file is committed. The rules below say when that state is acceptable.

- **PL-5** An unresolved link whose path equals the Registered Path is conformant. Rationale: the file is expected at that path, and the link resolves without any edit once the file exists.
- **PL-6** The Links check of [Section 12.1](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#121-approval-workflow) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) accepts a link to a planned document when its path equals the Registered Path and it carries no anchor. It accepts a link to an existing document when the file and any anchor resolve. Rationale: the first condition can be checked against the register alone, and the second against the repository.
- **PL-7** No stub, empty, or placeholder file is committed to make a link resolve. Rationale: a stub is a file without approved content, it can be mistaken for the document, and it must be replaced later.

A reader who follows an unresolved link finds the register entry in [Section 3](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md#3-complete-document-register) of [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map. Live status is tracked in the Kanban board and the Blueprint dashboard, not in any document.

### 4.4 Anchors on Planned Documents

- **PL-8** A link to a planned document carries no anchor, and T3 is not used for it. A topic inside a planned document is named in prose beside the plain link, and the anchor is added in a later approved change once the file exists. Rationale: an anchor is derived from a heading that does not exist yet, so it cannot be checked and may differ from the heading that is eventually written.

### 4.5 When the File Is Created

- **PL-9** The file is committed at its Registered Path. No citing document is edited, and the Links check for links to it changes from the path check to the file and anchor check. Rationale: this is the outcome that the single reference form of PL-1 was chosen to give.

### 4.6 Changes to a Registration

- **PL-10** If the title or the wave of a planned document changes in the register, every link to it is corrected in the same commit as the register change. Rationale: the ID stays and the file name follows the title ([Section 5.1](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md#51-file-names) of [SRIS-P1-GOV-003](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)), so a link written from the old register entry would no longer equal the Registered Path.
- **PL-11** If a planned document is withdrawn, its ID is retired and stays in the register ([Section 4.4](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md#44-permanence-gaps-and-reuse) of [SRIS-P1-GOV-003](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)). Every link to it is removed, or pointed at the document that replaces it, in the same commit. Rationale: a link to a retired ID can never resolve.

---

## 5. Appendix B Structure

### 5.1 Fixed Layout

[Section 6.4](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#64-appendix-b-structure) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard names the seven subsections of Appendix B. This section states what each is for, which columns it uses, and when its body is a table, prose, or None.

Each subsection answers one question.

| Subsection | Title                                         | Question It Answers                                          |
| ---------- | --------------------------------------------- | ------------------------------------------------------------ |
| B.1        | Directly Referenced Documents                 | Which documents does this document cite?                     |
| B.2        | Documents That Reference This Document        | Which documents cite this document?                          |
| B.3        | Documents This Document Depends On (Upstream) | Which documents must be approved before this one?            |
| B.4        | Documents This Document Unblocks (Downstream) | Which documents wait for this one?                           |
| B.5        | Master Documentation Index                    | Where is the complete register?                              |
| B.6        | External Reference Documents                  | Where are the topics that this document excludes documented? |
| B.7        | Document Conventions                          | Where are the vocabulary conventions defined?                |

- **AB-1** Appendix B has the heading Appendix B: Related Documents and the seven subsections above, in that order and with those titles, in every document. A subsection with nothing to state is kept. Rationale: the anchors of Appendix B and of its subsections are then the same in every document, so a link such as B.5 never needs checking.
- **AB-2** The body of each subsection is one of three things: a table, prose, or the exact text `None.` with a full stop and nothing else. [Section 5.10](#510-choosing-between-table-prose-and-none) says which applies. Rationale: a fixed vocabulary lets a script test a subsection without interpreting free text.

### 5.2 Common Column Rules

Four columns recur in the tables of Appendix B: Seq, Document Name, Wave, and the pair Pri and Tag.

- **AB-3** Seq, Document Name, Wave, Pri, and Tag are copied from the register entry, without change, including for planned documents. Rationale: a second source for these values would drift from the register.
- **AB-4** Seq has the form wave.number with no padding, such as 0.4, 2.1, or 4.15. It is read as two integers, so 0.9 comes before 0.10. Rationale: the register numbers documents by wave and by position in the wave, and a plain counter would not identify the same document across tables.
- **AB-5** Rows are in ascending order of Seq. Rationale: a stable order lets a change to a table show in version control as an added or removed row.
- **AB-6** The Document ID cell is a link. The Document Name cell is plain text equal to the register title, with no link and no suffix. Where the register shows no priority, the Pri cell holds the same dash character as the register. Rationale: the link belongs to the ID alone (SC-6), and any suffix would be a marker (PL-2).

### 5.3 Directly Referenced Documents (B.1)

- **AB-7** B.1 is a table with the columns Seq, Document ID, Document Name, Wave, Pri, and Tag. It lists every document cited outside Appendix B, and no other document. A citation in the metadata table, the Approval section, the Revision History, or any appendix other than Appendix B counts as outside. The document's own ID is not listed. Rationale: B.1 is then the complete and checkable index of the citations in the file, and a row for the document itself carries no relationship.

### 5.4 Referencing Documents (B.2)

- **AB-8** B.2 is a table with the columns Seq, Document ID, Document Name, and Why It References. Why It References is one short clause. Rationale: a reader can see the reason for each reference without opening the citing document.
- **AB-9** B.2 records the citations known when the version was approved. A later citation does not by itself require a revision. B.2 is corrected at the next revision made for another reason, and it is reconciled once at the Phase 1 baseline defined in [Section 7.2](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#72-when-to-add-rows) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md). Rationale: otherwise each new document would force a new version of every document that it cites.

### 5.5 Upstream Documents (B.3)

- **AB-10** B.3 is a table with the columns Seq, Document ID, Document Name, and Dependency Type. Dependency Type is Hard or Soft. Hard applies when the content or form of this document cannot be written or cannot be approved without the upstream document. A template or a register that governs this document's structure is Hard. A document that informs the subject but could be omitted without breaking the current document is Soft. Rationale: [Section 6.4](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#64-appendix-b-structure) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) names the two values and does not define them, and approval order depends on the difference.
- **AB-11** No document lists itself in B.3, and the Hard dependencies among all documents form no cycle. Rationale: a cycle would make an approval order impossible.

### 5.6 Downstream Documents (B.4)

- **AB-12** B.4 is a table with the columns Seq, Document ID, Document Name, and Blocked Until. It lists the documents for which this document is a Hard upstream document. Soft dependents are not listed. Rationale: only a Hard dependency blocks approval, and a Soft dependent is not blocked.
- **AB-13** The Blocked Until value is `This approved`. Every document that lists this document as Hard upstream in its own B.3 is covered by B.4, either as a row or inside a group statement. Rationale: B.3 and B.4 are two views of the same dependency, and each must agree with the other.

### 5.7 Master Documentation Index (B.5)

- **AB-14** B.5 is the single sentence The complete list of Phase 1 documents is in followed by a T1 citation of the register and a full stop. In the register itself B.5 states that the document is the master index. Rationale: one sentence, identical in every document, can be tested by exact match.

### 5.8 External Reference Documents (B.6)

- **AB-15** B.6 is a table with the columns Reference Type and Where It Is Documented. It holds sources outside the Phase 1 register only, such as published standards (e.g., ISO 25010), laws (e.g., DPDP Act), or third-party specifications (e.g., OpenTelemetry, W3C). A source outside the project has the Reference Type Third-party source and a cell that holds its name and its absolute URL (T7). Phase 1 documents are never listed in B.6; they belong in B.1. Rationale: external means external to the Phase 1 register, so B.6 clearly separates external dependencies from internal project cross-references.

### 5.9 Document Conventions (B.7)

B.7 is one sentence with two citations, in this form:

```
The conventions for Priority and Tag values are defined in [Section 9](<path>#9-vocabulary-standards) of SRIS-P1-GOV-002 — Document Template Standard.

```

- **AB-16** The sentence above is used in every document, with the placeholder path replaced by the Registered Path of the template standard. In the template standard itself, the sentence points to its own vocabulary section with T4. Rationale: the vocabulary has one owner, and copying its tables into other documents would create versions that can differ.

### 5.10 Choosing Between Table, Prose, and None

| Subsection | Table                                                             | Prose                                                                             | None.                                 |
| ---------- | ----------------------------------------------------------------- | --------------------------------------------------------------------------------- | ------------------------------------- |
| B.1        | At least one document is cited.                                   | Only in the master index, which cites every document in the register and says so. | The document cites no other document. |
| B.2        | The citing documents are known one by one and number at most ten. | The citing documents are a whole group, and the sentence points to B.5.           | No citing document is known.          |
| B.3        | At least one upstream document exists.                            | Never.                                                                            | No upstream document exists.          |
| B.4        | The Hard dependents are known one by one and number at most ten.  | The dependents are a whole group, and the sentence points to B.5.                 | There is no Hard dependent.           |
| B.5        | Never.                                                            | Always, in the sentence of AB-14.                                                 | Never.                                |
| B.6        | At least one row exists.                                          | Never.                                                                            | No row exists.                        |
| B.7        | Never.                                                            | Always, in the sentence of AB-16.                                                 | Never.                                |

- **AB-17** The group form of B.2 and B.4 is one or two sentences that name the group, such as every other document or a whole wave, and point to B.5 with a T4 link. A table of more than ten rows is not used in B.2 or B.4. Rationale: beyond ten rows a table repeats the register and goes stale.

---

## 6. Special Cases

### 6.1 Code Blocks and Inline Code

- **SC-1** A Document ID inside a fenced code block or inline code is not a reference and is not linked. It may be written in full or in short form there. Rationale: link syntax does not render inside code, and [Section 6.1](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#61-citation-format) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard confines short forms to code.
- **SC-2** A document that the text relies on is also cited in the same section, outside code. Rationale: code is for illustration, so a citation held only there would be invisible to a reader and to the checks of [Section 8](#8-validation).
- **SC-3** An ID invented for an example appears only in code format. Rationale: this is the convention of [Section 6](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md#6-examples) of [SRIS-P1-GOV-003](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md) — Document ID and Category Scheme, and it stops an illustration from being read as a reference to a register entry.
- **SC-4** A link example is shown as raw markdown, in a fenced block or inline code, and angle-bracket placeholders appear only there. Rationale: [Section 10.4](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#104-markdown-only) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) restricts angle brackets to code.

### 6.2 Tables

- **SC-5** Every cell of every table follows the citation rules, including the Change cells of a Revision History and the cells of the approval block. A short form in such a cell is a plain-text reference. Rationale: a table cell is part of the text, and a reference in it is as followable as one in prose.
- **SC-6** A table with a Document ID column links the ID in that column and gives the title in the Document Name column. The same document is not linked a second time in the row. Rationale: one link and one title for each row keeps the row checkable.
- **SC-7** A link is never wrapped in code formatting. Rationale: code formatting turns off link rendering, so the cell would show raw syntax.

### 6.3 Metadata Table and Blockquote

- **SC-8** The metadata table and the metadata blockquote hold plain text only ([Section 3.3](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#33-formatting-rules) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md)). The Document ID in them is the document's own ID. The Related Documents cell reads See Appendix B and is not linked. Rationale: the metadata is a record of identity, and identity does not need navigation.
- **SC-9** The Supersedes cell is the only metadata cell that may hold a link. When the document replaces a different document, the cell cites it as [Section 12.2](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#122-superseding-rules) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) requires. Rationale: the specific rule for the field overrides the general rule for the table.

### 6.4 Headings

- **SC-10** A heading contains no Document ID and no link. Rationale: IDs contain hyphens, which [Section 5.2](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#52-section-numbering) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) excludes from headings, and a link in a heading complicates the table of contents and the derivation of the anchor.

### 6.5 Appendix A and Later Appendices

- **SC-11** Appendix A and every later appendix follow the same rules as the body. A document cited only in an appendix is listed in B.1. An Appendix A that states Not applicable. contains no reference. Rationale: an appendix is part of the document, and B.1 must list every citation outside Appendix B (AB-7).
- **SC-12** Appendix subsections are numbered A.1, C.1, and so on ([Section 5.3](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#53-appendix-structure) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md)), and they are link targets like numbered subsections (AN-7). Rationale: their anchors are derived in the same way as those of the body.

### 6.6 Self References

- **SC-13** A document does not link its own ID or its own file. This is the one exception to CF-1. Rationale: a link from a document to itself carries no information and would have to be changed whenever the file moves.
- **SC-14** The document's own ID appears in plain text in the header, in the metadata table, and in prose only where the text must name the document. Elsewhere the text says this document or this standard. Rationale: the ID is then a rare token that a reader can notice.
- **SC-15** A reference to a section of the document itself uses T4 (CF-11). Rationale: a same-document anchor is checked against the headings of the same file.
- **SC-16** The document's own ID is not listed in B.1 to B.6. A reference to an earlier version of the document is plain text, as in the Supersedes cell. Rationale: a row for the document itself has no relationship to record.

---

## 7. Anchor Generation

### 7.1 Derivation Algorithm

[Section 5.4](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#54-table-of-contents-formatting) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard describes a heading anchor in one line. The steps below are the full derivation, which a script can reproduce.

- **AN-1** An anchor is derived from the heading text by the steps below and is never written by hand. No other anchor mechanism is used. Rationale: [Section 10.4](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#104-markdown-only) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) allows no HTML, so explicit anchor elements are not available and the heading is the only source of an anchor.

1. Take the heading text without the leading hash marks and without leading or trailing spaces.
2. Drop formatting marks and keep the text that they enclose.
3. Convert every letter to lower case.
4. Remove every character that is not a letter, a digit, a space, a hyphen, or an underscore.
5. Replace each space with one hyphen.
6. If the result equals an anchor produced earlier in the same file, append a hyphen and a counter that starts at 1.
7. Put a hash sign in front of the result when it is used in a link.

### 7.2 Transformation Examples

The headings below, written as the code format shows them, give the anchors beside them.

| Heading Text                                            | Anchor                                           |
| ------------------------------------------------------- | ------------------------------------------------ |
| `## 1. Introduction`                                    | `1-introduction`                                 |
| `### 1.1 Purpose`                                       | `11-purpose`                                     |
| `## 9. Vocabulary Standards`                            | `9-vocabulary-standards`                         |
| `### 3.2 Wave 0: Project Foundation`                    | `32-wave-0-project-foundation`                   |
| `### 4.6 Tester (QA)`                                   | `46-tester-qa`                                   |
| `### 4.4 UI/UX Designer`                                | `44-uiux-designer`                               |
| `## Appendix B: Related Documents`                      | `appendix-b-related-documents`                   |
| `### B.3 Documents This Document Depends On (Upstream)` | `b3-documents-this-document-depends-on-upstream` |
| `## Revision History`                                   | `revision-history`                               |
| `## 5. Scope — Limits`                                  | `5-scope--limits`                                |

### 7.3 Title Case and Capitalisation

- **AN-2** Anchors are lower case. A change of capitalisation in a heading does not change its anchor and needs no link update, whereas a change of any word does. The capitalisation of headings follows [Section 5.2](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#52-section-numbering) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md). Rationale: step 3 of the derivation removes the difference between upper and lower case.

### 7.4 Special Characters

- **AN-3** Full stops, colons, commas, parentheses, slashes, apostrophes, and ampersands are removed and leave no hyphen. The full stop in a section number therefore disappears, and 1.1 becomes 11. Rationale: step 4 of the derivation removes them before spaces are turned into hyphens.
- **AN-4** A dash character such as an em dash is removed but the spaces around it stay, which produces a double hyphen. [Section 5.2](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#52-section-numbering) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) excludes dashes from headings so that this case does not arise. Rationale: a double hyphen is easy to mistype in a link.
- **AN-5** Hyphens, underscores, and digits in a heading are kept. Rationale: step 4 of the derivation keeps them.

### 7.5 Duplicate Headings

- **AN-6** No two headings in one document produce the same anchor before the counter of step 6 is applied. Two headings can collide when their numbers have equal digits once the full stop is removed, such as 1.12 and 11.2 with the same title. Rationale: a counter makes an anchor depend on the order of headings, so inserting a heading would retarget a link without any signal.

### 7.6 Link Targets

- **AN-7** A link to a heading targets a level-2 heading or a numbered level-3 heading, including appendix subsections such as A.1 and B.5. A level-4 heading is never a target. Rationale: level-4 headings are unnumbered, are not listed in the table of contents ([Section 5.4](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#54-table-of-contents-formatting) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md)), and may repeat, so their anchors are not stable.
- **AN-8** An anchor link into another document points only at a heading of an existing file (PL-8), and its link text restates the section number. Rationale: a reader then sees which section was meant even if a later renumbering breaks the anchor.

### 7.7 Stability

- **AN-9** When a heading is renamed, renumbered, or removed, every link to its anchor is found and corrected in the same commit. The change is an approved change with its own Revision History row ([Section 7.2](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#72-when-to-add-rows) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md)). Rationale: an anchor depends on nothing but the heading text, so a heading edit is a link change.
- **AN-10** A new section is added at the end of its parent where possible. An insertion in the middle is treated as a renumbering under AN-9. Rationale: section numbers run in sequence with no gaps, so an insertion renumbers every later section and changes their anchors.

---

## 8. Validation

### 8.1 Conformance Checks

Check V-1 (Link Stability Check) formally validates document references. 
- **What it checks:** It verifies that every Phase 1 Document ID mentioned in the text (outside of code blocks and self-references) is wrapped in a valid link matching the derived Registered Path, and that anchors are formatted correctly.
- **What it does not check:** It does not check if the target file actually exists in the repository, because planned documents use the exact same link format as existing ones.

A script applies check V-1 in four steps:

1. Remove fenced code blocks and inline code.
2. Remove every substring that matches the document link pattern or the section link pattern.
3. Search what remains for the ID pattern.
4. Report every match except the document's own ID.

The link patterns are removed first because the file name inside a link contains the ID, and it would otherwise be reported as an unlinked ID.

### 8.2 Link Pattern

Links to a document or to a section of a document are found by searching for the text with the patterns below. Each pattern matches a complete markdown link, including the parentheses around the target and the file extension .md.

```regex
\[(SRIS-P1-(?:GOV|DEV|REQ|ARCH|DATA|API|UI|SEC|TEST|INF|OPS|PM|USR|NFR-HOLD|NOTES-AI)-(?!000)[0-9]{3})\]\((?:\./|\.\./(?:wave-0-project-foundation|wave-1-requirements|wave-2-architecture|wave-3-detailed-design|wave-4-testing|wave-5-devops-operations|wave-6-developer-standards|wave-7-project-tracking|wave-8-user-support|wave-9-supporting-artifacts)/)\1_[A-Za-z0-9]+\.md(?:#[a-z0-9_-]+)?\)
\[(?:Section [0-9]+(?:\.[0-9]+)?|[A-Z]\.[0-9]+|Appendix [A-Z])\]\((?:\./|\.\./(?:wave-0-project-foundation|wave-1-requirements|wave-2-architecture|wave-3-detailed-design|wave-4-testing|wave-5-devops-operations|wave-6-developer-standards|wave-7-project-tracking|wave-8-user-support|wave-9-supporting-artifacts)/)SRIS-P1-(?:GOV|DEV|REQ|ARCH|DATA|API|UI|SEC|TEST|INF|OPS|PM|USR|NFR-HOLD|NOTES-AI)-(?!000)[0-9]{3}_[A-Za-z0-9]+\.md#[a-z0-9_-]+\)
```

### 8.3 Adoption and Maintenance

- **MN-1** A document written before this standard is corrected to it. Each correction is an approved change with a new Revision History row, and the minor version increases by one ([Section 7.3](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#73-version-numbering-rules) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md)). Rationale: [Section 9.3](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#93-exact-term-usage) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) applies the same precedent to the vocabulary rules, and the version rules give every correction a record.
- **MN-2** A renamed or moved file is renamed with git mv, and every link to it is corrected in the same commit ([Section 11.4](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#114-naming-non-conformance) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md)). Rationale: a link that is corrected later breaks every build that runs between the two commits.
- **MN-3** Links to a document are found by searching for its ID, and not for its file name. Rationale: the ID is permanent and the file name is not.
- **MN-4** The conformance checks are run on a document before approval. Rationale: a defect found after approval costs a new Revision History row.

---

## 9. Worked Examples

The examples are shown in code format, so the IDs in them are not references (SC-1). Unless stated otherwise, the Containing Document is in Wave 0.

### 9.1 Correct Examples

- **Correct 1** `[SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map`. Reason: First mention of a document of the same wave. The text is the full ID, the prefix is ./, the file name is the register name, and the title follows an em dash (CF-1 to CF-4, PA-3, PA-4).
- **Correct 2** `[SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md)`. Reason: A later mention in the same section. The link stays and the title is omitted (CF-9).
- **Correct 3** `[SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) — Microservices Identification`. Reason: A document of another wave. There is one ../ segment and the folder is from the table in [Section 3.4](#34-wave-folder-names) (PA-2, PA-3, PA-6).
- **Correct 4** `[SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard` written in a Wave 2 document. Reason: The rule applies in the other direction. The Containing Document is in Wave 2, so the folder of Wave 0 is named (PA-3).
- **Correct 5** `[SRIS-P1-ARCH-008](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md) — Technology Stack ADR`. Reason: A planned document, written whether or not the file exists. The path comes from the register, and there is no marker and no anchor (PL-1, PL-2, PL-4, PL-8).
- **Correct 6** `[Section 9](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#9-vocabulary-standards) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard`. Reason: A section of another document, first mention. The anchor is derived from the heading of an existing file (CF-10, AN-8).
- **Correct 7** `[Section 7](#7-anchor-generation)`. Reason: A section of the same document, in the T4 form (CF-11, SC-15).
- **Correct 8** `[SRIS-P1-REQ-007](../wave-1-requirements/SRIS-P1-REQ-007_DomainRulesFareCalculation.md) to [SRIS-P1-REQ-011](../wave-1-requirements/SRIS-P1-REQ-011_DomainRulesSeatMatrixAndInventory.md)`. Reason: A range in a table cell. Both ends are linked, the IDs are of one category in ascending order, and no title is given (CF-14).
- **Correct 9** `git grep -n "SRIS-P1-ARCH-008" -- docs`. Reason: An ID inside a code block is not a reference and is not linked (SC-1).
- **Correct 10** `This standard (SRIS-P1-GOV-004) applies to every Phase 1 document.` written in this document. Reason: A self reference is plain text and is not linked (SC-13, SC-14).

### 9.2 Incorrect Examples

- **Incorrect 1** `See SRIS-P1-GOV-001 for the register.`. Reason: The ID is plain text and has no link (CF-1, CF-5).
- **Incorrect 2** `See [GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md).`. Reason: The link text is a short form and not the full ID (CF-1).
- **Incorrect 3** `[SRIS-P1-GOV-001](https://github.com/example/sris/blob/main/docs/SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md)`. Reason: The target is an absolute URL to a project document (PA-10).
- **Incorrect 4** `[SRIS-P1-ARCH-001](./SRIS-P1-ARCH-001_MicroservicesIdentification.md)` written in a Wave 0 document. Reason: The prefix is for the same wave, but the target is in Wave 2 and the path points to a file that cannot exist (PA-3, PA-5).
- **Incorrect 5** `[SRIS-P1-GOV-002](../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md)` written in a Wave 0 document. Reason: The target is in the same wave, so the prefix must be ./ (PA-4).
- **Incorrect 6** `SRIS-P1-ARCH-008 (planned, not yet written)`. Reason: The ID is plain text, and the wording is a status marker (PL-1, PL-2).
- **Incorrect 7** `[SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap_v1.1.md)`. Reason: The file name carries a version (PA-9).
- **Incorrect 8** `[SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap_v1.1.pdf)`. Reason: The target is a PDF, and its name carries a version (PA-9).
- **Incorrect 9** `[Section 3](../wave-2-architecture/SRIS-P1-ARCH-008_TechnologyStackADR.md#3-technology-selection)`. Reason: An anchor into a planned document, whose headings do not exist yet (PL-8).
- **Incorrect 10** `[Section 1.1](#1.1-purpose)`. Reason: The anchor keeps the full stop. The derived anchor is 11-purpose (AN-1, AN-3).
- **Incorrect 11** `[Section 1.1](#11-Purpose)`. Reason: The anchor has an upper-case letter and does not equal the derived anchor (AN-1, AN-2).
- **Incorrect 12** `See the Documentation Index and Navigation Map.`. Reason: The document is identified by title alone (CF-5).
- **Incorrect 13** `[SRIS-P1-GOV-099](./SRIS-P1-GOV-099_UnregisteredDocument.md)`. Reason: The ID is not in the register (PL-3).
- **Incorrect 14** `[SRIS-P1-GOV-002](./SRIS-P1-GOV-002_documenttemplatestandard.md)`. Reason: The file name differs from the register name in case (PA-8).
- **Incorrect 15** `[SRIS-P1-GOV-004](./SRIS-P1-GOV-004_DocumentCrossReferenceStandard.md)` written in this document. Reason: A document links its own ID (SC-13).
- **Incorrect 16** `See section 6.4.` written for a section of the same document. Reason: A bare section number is used instead of a T4 link (CF-11).

---

## 10. Approval

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

| Seq  | Document ID                                                                  | Document Name                          | Wave | Pri | Tag     |
| ---- | ---------------------------------------------------------------------------- | -------------------------------------- | ---- | --- | ------- |
| 0.0  | [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md)   | Documentation Index and Navigation Map | 0    | P0  | UNBLOCK |
| 0.1  | [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md)             | Document Template Standard             | 0    | P0  | UNBLOCK |
| 0.2  | [SRIS-P1-GOV-003](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)          | Document ID and Category Scheme        | 0    | P1  | UNBLOCK |
| 4.15 | [SRIS-P1-SEC-011](../wave-4-testing/SRIS-P1-SEC-011_SecurityTestingPlan.md)  | Security Testing Plan                  | 4    | P1  | FOLLOW  |
| 7.1  | [SRIS-P1-DEV-013](../wave-7-project-tracking/SRIS-P1-DEV-013_SkillMatrix.md) | Skill Matrix                           | 7    | P2  | FOLLOW  |

### B.2 Documents That Reference This Document

Every Phase 1 document that cites another document follows this standard, so the citing documents are too many to list one by one. The complete list is in the register described in [B.5](#b5-master-documentation-index).

### B.3 Documents This Document Depends On (Upstream)

| Seq | Document ID                                                                | Document Name                          | Dependency Type |
| --- | -------------------------------------------------------------------------- | -------------------------------------- | --------------- |
| 0.0 | [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) | Documentation Index and Navigation Map | Hard            |
| 0.1 | [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md)           | Document Template Standard             | Hard            |
| 0.2 | [SRIS-P1-GOV-003](./SRIS-P1-GOV-003_DocumentIDAndCategoryScheme.md)        | Document ID and Category Scheme        | Hard            |

### B.4 Documents This Document Unblocks (Downstream)

Every Phase 1 document that cites another document is written against this standard, so the dependent documents are a whole group. The complete list is in the register described in [B.5](#b5-master-documentation-index).

### B.5 Master Documentation Index

The complete list of Phase 1 documents is in [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

### B.6 External Reference Documents

None.

### B.7 Document Conventions

The conventions for Priority and Tag values are defined in [Section 9](./SRIS-P1-GOV-002_DocumentTemplateStandard.md#9-vocabulary-standards) of [SRIS-P1-GOV-002](./SRIS-P1-GOV-002_DocumentTemplateStandard.md) — Document Template Standard.