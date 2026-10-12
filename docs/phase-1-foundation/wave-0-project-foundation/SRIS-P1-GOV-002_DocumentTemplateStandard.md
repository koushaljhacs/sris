<div align="center">

![Wave](https://img.shields.io/badge/Wave-0-0550AE?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-GOV-6e7781?style=for-the-badge)

</div>

# Document Template Standard

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** 1.3 | **Date:** 2026-10-12 | **Document ID:** SRIS-P1-GOV-002

| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| Title              | Document Template Standard                                        |
| Software           | SRIS                                                              |
| Software Full Form | Sarathi Railway Information System                                |
| Team Codename      | Project Sarathi                                                   |
| Document ID        | SRIS-P1-GOV-002                                                   |
| Task               | Define the standard template for all Phase 1 documents            |
| Document Type      | Standard Document                                                 |
| Milestone          | Phase 1 Foundation                                                |
| Classification     | Internal                                                          |
| Version            | 1.3                                                               |
| Date               | 2026-10-12                                                        |
| Author             | Koushal Jha, Lead Architect                                       |
| Approved By        | Koushal Jha, Lead Architect                                       |
| Approval Date      | 2026-10-12                                                        |
| Supersedes         | Version 1.2 of this document                                      |
| Related Documents  | See Appendix B                                                    |
| Affiliation        | Independent · Not affiliated with CRIS, IRCTC, or Indian Railways |

---

## Table of Contents

1. [Introduction](#1-introduction)
   - [1.1 Purpose](#11-purpose)
   - [1.2 Scope](#12-scope)
   - [1.3 Audience](#13-audience)
2. [Document Header Standard](#2-document-header-standard)
   - [2.1 Title Line](#21-title-line)
   - [2.2 Subtitle](#22-subtitle)
   - [2.3 Tagline](#23-tagline)
   - [2.4 Affiliation Line](#24-affiliation-line)
   - [2.5 Metadata Blockquote](#25-metadata-blockquote)
3. [Metadata Table Standard](#3-metadata-table-standard)
   - [3.1 Field List](#31-field-list)
   - [3.2 Field Descriptions](#32-field-descriptions)
   - [3.3 Formatting Rules](#33-formatting-rules)
4. [Badge Policy](#4-badge-policy)
   - [4.1 Decision](#41-decision)
   - [4.2 Required Badges](#42-required-badges)
   - [4.3 Placement and Formatting](#43-placement-and-formatting)
5. [Body Structure Standard](#5-body-structure-standard)
   - [5.1 Standard Section Layout](#51-standard-section-layout)
   - [5.2 Section Numbering](#52-section-numbering)
   - [5.3 Appendix Structure](#53-appendix-structure)
   - [5.4 Table of Contents Formatting](#54-table-of-contents-formatting)
6. [Cross-Reference Standard](#6-cross-reference-standard)
   - [6.1 Citation Format](#61-citation-format)
   - [6.2 Relative Link Rules](#62-relative-link-rules)
   - [6.3 Same-Wave and Other-Wave Paths](#63-same-wave-and-other-wave-paths)
   - [6.4 Appendix B Structure](#64-appendix-b-structure)
7. [Revision History Standard](#7-revision-history-standard)
   - [7.1 Format](#71-format)
   - [7.2 When to Add Rows](#72-when-to-add-rows)
   - [7.3 Version Numbering Rules](#73-version-numbering-rules)
8. [Approval Block Standard](#8-approval-block-standard)
   - [8.1 Format](#81-format)
   - [8.2 Sign-off Procedure](#82-sign-off-procedure)
9. [Vocabulary Standards](#9-vocabulary-standards)
   - [9.1 Priority Values](#91-priority-values)
   - [9.2 Tag Values](#92-tag-values)
   - [9.3 Exact Term Usage](#93-exact-term-usage)
10. [Style Rules](#10-style-rules)
    - [10.1 No Emojis](#101-no-emojis)
    - [10.2 No Marketing Language](#102-no-marketing-language)
    - [10.3 British English](#103-british-english)
    - [10.4 Markdown Only](#104-markdown-only)
    - [10.5 Table Formatting](#105-table-formatting)
    - [10.6 Paragraph Length](#106-paragraph-length)
11. [File Naming and Folder Rules](#11-file-naming-and-folder-rules)
    - [11.1 Source Markdown Naming](#111-source-markdown-naming)
    - [11.2 PDF Naming](#112-pdf-naming)
    - [11.3 Folder Structure](#113-folder-structure)
    - [11.4 Naming Non-Conformance](#114-naming-non-conformance)
12. [Document Lifecycle](#12-document-lifecycle)
    - [12.1 Approval Workflow](#121-approval-workflow)
    - [12.2 Superseding Rules](#122-superseding-rules)
13. [Approval](#13-approval)

- [Revision History](#revision-history)
- [Appendix A: Metadata Table Template](#appendix-a-metadata-table-template)
- [Appendix B: Related Documents](#appendix-b-related-documents)

---

## 1. Introduction

### 1.1 Purpose

This document defines the standard template for every Phase 1 document of SRIS (Sarathi Railway Information System). It fixes the header, metadata table, body structure, cross-reference format, revision history, approval block, vocabulary, style rules, and file naming.

It also records two decisions that apply to all documents: the badge policy in [Section 4](#4-badge-policy) and the priority and tag vocabulary in [Section 9](#9-vocabulary-standards). The documents it governs are listed in [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map.

### 1.2 Scope

In scope:

- Document header, badges, and metadata table.
- Body structure, numbering, appendices, and table of contents.
- Cross-references and relative links.
- Revision history, versioning, approval, and lifecycle.
- Vocabulary for priority and tag values.
- Style rules, file naming, and folder rules.

Out of scope:

- The content of any individual document.
- Railway domain content.
- Technology, architecture, and design decisions.

### 1.3 Audience

- Lead Architect: maintains this standard and approves documents.
- Team members: write documents against this standard.
- Evaluators and Supervisor: check that all documents follow one consistent format.
- Future contributors: learn the conventions before adding a document.

---

## 2. Document Header Standard

Every document starts with the same header block. The elements appear in this order: badge block, title line, subtitle, tagline, affiliation line, metadata blockquote, and metadata table.

### 2.1 Title Line

The title line is the only level-1 heading in the document. It repeats the Title field of the metadata table exactly, in Title Case.

### 2.2 Subtitle

The subtitle is an italic line below the title. It is identical in every document: `*SRIS — Sarathi Railway Information System*`.

### 2.3 Tagline

The tagline is an italic line below the subtitle. It is identical in every document: `*A Unified Railway Management Platform*`.

### 2.4 Affiliation Line

The affiliation line is an italic line below the tagline: `*Inspired by CRIS and IRCTC · Independent project*`. It states that the project is independent. The full statement is in the Affiliation field of the metadata table.

### 2.5 Metadata Blockquote

The metadata blockquote is one line below the affiliation line. Its Version, Date, and Document ID values must equal the same fields in the metadata table.

The complete header template, including the badge block, is shown below.

```
<div align="center">

![Wave](https://img.shields.io/badge/Wave-<WaveNumber>-<WaveColor>?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-1%20Foundation-6f42c1?style=for-the-badge)
![Category](https://img.shields.io/badge/Category-<Category>-<CategoryColor>?style=for-the-badge)

</div>

# <Document Title>

*SRIS — Sarathi Railway Information System*

*A Unified Railway Management Platform*

*Inspired by CRIS and IRCTC · Independent project*

> **Version:** <Version> | **Date:** <YYYY-MM-DD> | **Document ID:** <Document ID>
```

---

## 3. Metadata Table Standard

The metadata table follows the metadata blockquote. It has two columns, Field and Value, and exactly 17 rows. A copy-paste template is in [Appendix A](#appendix-a-metadata-table-template).

### 3.1 Field List

| No  | Field              |
| --- | ------------------ |
| 1   | Title              |
| 2   | Software           |
| 3   | Software Full Form |
| 4   | Team Codename      |
| 5   | Document ID        |
| 6   | Task               |
| 7   | Document Type      |
| 8   | Milestone          |
| 9   | Classification     |
| 10  | Version            |
| 11  | Date               |
| 12  | Author             |
| 13  | Approved By        |
| 14  | Approval Date      |
| 15  | Supersedes         |
| 16  | Related Documents  |
| 17  | Affiliation        |

The fields appear in this order in every document. No field is optional and no field is added or removed.

### 3.2 Field Descriptions

| Field              | Description                                   | Value Rule                                                           |
| ------------------ | --------------------------------------------- | -------------------------------------------------------------------- |
| Title              | Full name of the document.                    | Same text as the title line.                                         |
| Software           | Short name of the software.                   | Fixed: SRIS.                                                         |
| Software Full Form | Expanded name of the software.                | Fixed: Sarathi Railway Information System.                           |
| Team Codename      | Codename of the team.                         | Fixed: Project Sarathi.                                              |
| Document ID        | Stable identifier of the document.            | Format `SRIS-P1-CATEGORY-NNN`. An ID is never reused.                |
| Task               | Task that the document fulfils.               | One sentence.                                                        |
| Document Type      | Kind of document.                             | Short noun phrase, for example Standard Document.                    |
| Milestone          | Project milestone that the document supports. | Phase 1 Foundation.                                                  |
| Classification     | Distribution level.                           | Internal.                                                            |
| Version            | Version of the document content.              | `MAJOR.MINOR`, see [Section 7](#7-revision-history-standard).        |
| Date               | Date of the current version.                  | `YYYY-MM-DD`.                                                        |
| Author             | Person who wrote the document.                | Name, role.                                                          |
| Approved By        | Person who approved the document.             | Name, role. Pending until approval.                                  |
| Approval Date      | Date of approval.                             | `YYYY-MM-DD`. Pending until approval.                                |
| Supersedes         | Document or version that this one replaces.   | See [Section 12.2](#122-superseding-rules).                          |
| Related Documents  | Pointer to related documents.                 | See Appendix B.                                                      |
| Affiliation        | Statement of independence.                    | Fixed text, as in [Appendix A](#appendix-a-metadata-table-template). |

Fixed values are copied exactly. They are the same in every document.

### 3.3 Formatting Rules

- Field names use the exact spelling and order in [Section 3.1](#31-field-list).
- Dates use the ISO 8601 format `YYYY-MM-DD`.
- No cell is empty. Use Pending or None where a value does not exist yet.
- The Version, Date, and Document ID values equal the metadata blockquote.
- The table is pipe-aligned, as described in [Section 10.5](#105-table-formatting).
- Metadata cells contain plain text and no links.
- The metadata table does not carry a Status field. Live status is tracked in the Kanban board and the Blueprint dashboard, not in the document.

---

## 4. Badge Policy

### 4.1 Decision

**Decision:** badges are required. Every Phase 1 document carries the three badges in [Section 4.2](#42-required-badges). There is no exemption.

The badges carry identity information that varies per document. The metadata table carries document identity. The two are complementary. Each shows a different dimension of the document.

- Badges show: Wave number, Phase, Category.
- Metadata shows: Title, Software, Version, Author, and other identity fields.

### 4.2 Required Badges

| Badge    | Value                                    | Colour Mapping | Rule                                |
| -------- | ---------------------------------------- | -------------- | ----------------------------------- |
| Wave     | Wave 0 to Wave 9                         | Fixed `0550AE` | Fixed for the document's wave.      |
| Phase    | 1 Foundation                             | Fixed `6f42c1` | Fixed: Phase 1 Foundation.          |
| Category | GOV / DEV / REQ / ARCH / DATA / API / UI / SEC / TEST / INF / OPS / PM / USR / NFR-HOLD / NOTES-AI | Fixed `6e7781` | Fixed for the document's category.  |

The badge URL uses URL-encoded values. For example, `1%20Foundation` for the Phase badge.

The badges are images loaded from shields.io. A document stays readable without them.

### 4.3 Placement and Formatting

1. The badge block is the first element of the file, before the title line.
2. The block is wrapped in a centred `div`. This is the only HTML allowed in a document.
3. A blank line follows the opening `div` and a blank line precedes the closing `div`.
4. Each badge is one line of markdown. The alternative text is the badge label.
5. The Wave badge uses the wave number (0 to 9) and the fixed blue colour.
6. The Phase badge is the same in every Phase 1 document.
7. The Category badge uses the document's category code (GOV, ARCH, etc.).
8. The exact block is part of the header template in [Section 2.5](#25-metadata-blockquote).

---

## 5. Body Structure Standard

### 5.1 Standard Section Layout

Every document has the elements below, in this order.

| Order | Element                       | Rule                                                                                                              |
| ----- | ----------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| 1     | Header block                  | Badges, title, subtitle, tagline, affiliation line, metadata blockquote ([Section 2](#2-document-header-standard)). |
| 2     | Metadata table                | 17 fields ([Section 3](#3-metadata-table-standard)).                                                              |
| 3     | Horizontal rule               | `---`                                                                                                             |
| 4     | Table of Contents             | See [Section 5.4](#54-table-of-contents-formatting).                                                              |
| 5     | Horizontal rule               | `---`                                                                                                             |
| 6     | Section 1: Introduction       | Subsections 1.1 Purpose, 1.2 Scope, 1.3 Audience, in this order.                                                  |
| 7     | Content sections              | Numbered from 2. A horizontal rule separates sections.                                                            |
| 8     | Approval                      | A numbered section, or a subsection inside a closing section ([Section 8](#8-approval-block-standard)).           |
| 9     | Revision History              | Unnumbered ([Section 7](#7-revision-history-standard)).                                                           |
| 10    | Appendix A                    | Document-specific material. If there is none, the appendix states Not applicable.                                 |
| 11    | Appendix B: Related Documents | Required in every document ([Section 6.4](#64-appendix-b-structure)).                                             |
| 12    | Appendix C onwards            | Further document-specific appendices, if needed.                                                                  |

Out-of-scope statements belong inside 1.2 Scope as a second list. Optional subsections, such as Definitions and Abbreviations, may follow 1.3 Audience.

The outline of a document is shown below.

```
Badge block
# <Document Title>
Subtitle, tagline, affiliation line, metadata blockquote
Metadata table
---
## Table of Contents
---
## 1. Introduction
### 1.1 Purpose
### 1.2 Scope
### 1.3 Audience
---
## 2. <Section Title>
### 2.1 <Subsection Title>
---
## <N>. Approval
## Revision History
## Appendix A: <Title>
## Appendix B: Related Documents
```

### 5.2 Section Numbering

- The title line is the only level-1 heading.
- Sections use level-2 headings with a number and a full stop: `## 1. Introduction`.
- Subsections use level-3 headings with a two-part number: `### 1.1 Purpose`.
- Level-4 headings are not numbered and are not listed in the table of contents.
- Numbers run in sequence with no gaps.
- Headings use Title Case.
- Headings contain no dashes or special characters, so that link anchors stay predictable. Use a colon where a separator is needed.
- Revision History and appendices are not numbered.

### 5.3 Appendix Structure

- Appendix headings have the form `## Appendix A: Title`. Appendix subsections have the form `### A.1 Title`.
- Appendix letters run in sequence.
- Appendix A holds document-specific material. When there is none, Appendix A is kept and contains the words Not applicable.
- Appendix B is always Related Documents, so its anchor is the same in every document.
- Further document-specific appendices follow as Appendix C, Appendix D, and so on.

### 5.4 Table of Contents Formatting

The table of contents lists every level-2 heading and every numbered level-3 heading. Numbered sections use an ordered list, and subsections use nested bullets. Revision History and the appendices follow as bullets after a blank line.

Each entry is a link to a GitHub heading anchor, which is the heading in lower case with spaces replaced by hyphens and punctuation removed.

```
1. [Introduction](#1-introduction)
   - [1.1 Purpose](#11-purpose)
   - [1.2 Scope](#12-scope)
2. [Section Title](#2-section-title)

- [Revision History](#revision-history)
- [Appendix A: Title](#appendix-a-title)
- [Appendix B: Related Documents](#appendix-b-related-documents)
```

---

## 6. Cross-Reference Standard

### 6.1 Citation Format

A reference to another document gives the Document ID, then a dash, then the title. The Document ID is a clickable link. Prose uses the full ID, never a short form such as GOV-001. Short forms appear only inside code blocks.

Example: see [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map for the complete register.

```
<Document ID> — <Title>

See [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map for the complete register.
```

The first mention in a section gives the ID and the title. Later mentions in the same section may give the ID only.

### 6.2 Relative Link Rules

- Every document reference is a clickable link.
- Links are relative to the folder of the document that contains the link.
- Absolute URLs are not used for project documents.
- The link text is the Document ID.
- The link target is the file name defined in [Section 11.1](#111-source-markdown-naming).
- A link to a section ends with the GitHub heading anchor of that section.
- Every Document ID in prose and in appendices is a hyperlink, whether the target file exists in the repository yet or not. The path follows the file-naming rules in [Section 11.1](#111-source-markdown-naming) and the wave-folder rules in [Section 11.3](#113-folder-structure). Links to files not yet committed resolve correctly once those files are committed.

### 6.3 Same-Wave and Other-Wave Paths

A document in Wave 0 links to another Wave 0 document with `./`. A link to any other wave goes up one folder with `../` and then into the wave folder. The wave folder names are listed in the register of [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md).

| Case             | Template                       | Example                                                                                |
| ---------------- | ------------------------------ | -------------------------------------------------------------------------------------- |
| Same wave        | `./<File Name>`                | `./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md`                              |
| Other wave       | `../<wave-folder>/<File Name>` | `../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md`               |
| Wave 2 to Wave 0 | `../<wave-folder>/<File Name>` | `../wave-0-project-foundation/SRIS-P1-GOV-002_DocumentTemplateStandard.md`             |
| Section anchor   | `<path>#<anchor>`              | `./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md#3-complete-document-register` |

Live examples from this document: [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) (same wave) and [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) (other wave).

### 6.4 Appendix B Structure

Appendix B is titled Related Documents and has seven subsections, in this order. A subsection with no entries is kept and states None.

| Subsection | Title                                         | Content                                                                                                |
| ---------- | --------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| B.1        | Directly Referenced Documents                 | Table: Seq, Document ID, Document Name, Wave, Pri, Tag.                                                |
| B.2        | Documents That Reference This Document        | Table: Seq, Document ID, Document Name, Why It References.                                             |
| B.3        | Documents This Document Depends On (Upstream) | Table: Seq, Document ID, Document Name, Dependency Type (Hard or Soft).                                |
| B.4        | Documents This Document Unblocks (Downstream) | Table: Seq, Document ID, Document Name, Blocked Until.                                                 |
| B.5        | Master Documentation Index                    | A link to the documentation index.                                                                     |
| B.6        | External Reference Documents                  | Table: Reference Type, Where It Is Documented. A source outside the Phase 1 register, such as a published standard, a law, or a third-party specification. Phase 1 documents belong in B.1. |                                                         |
| B.7        | Document Conventions                          | A link to [Section 9](#9-vocabulary-standards) of this standard. The convention tables are not copied. |

Every Document ID in B.1 to B.6 is a clickable link, except the ID of the document itself. The Tag column uses the values in [Section 9.2](#92-tag-values).

---

## 7. Revision History Standard

### 7.1 Format

The revision history is an unnumbered level-2 section titled Revision History. It is a table with four columns: Version, Date, Author, and Change. Rows are in ascending order, with the newest row last.

```
## Revision History

| Version   | Date         | Author        | Change                                          |
| --------- | ------------ | ------------- | ----------------------------------------------- |
| <Version> | <YYYY-MM-DD> | <Author Name> | <One to three sentences describing the change.> |
```

### 7.2 When to Add Rows

A document that has never been committed keeps a single row at version 1.0. Each edit updates the Date field and the Change cell of that row. No new row is added.

Once a document has been committed and pushed, each approved change adds a new row. The version increases by one minor digit. The previous rows are preserved. They are never removed or rewritten.

The Phase 1 baseline is the point at which the Lead Architect declares the Phase 1 documents frozen, planned for the end of Phase 1. The rule above applies before and after the baseline. The baseline does not change how rows are added.

### 7.3 Version Numbering Rules

- Versions have the form `MAJOR.MINOR`.
- The major digit is the phase number. Phase 1 uses major digit 1. Phase 2 uses major digit 2. Phase 3 uses major digit 3.
- The minor digit starts at 0 and increases by one for each approved change during the phase.
- The first version of every Phase 1 document is 1.0.
- No Phase 1 document uses major digit 2 or higher. A major bump happens only when a document is carried forward to a later phase, or when a new phase begins with its own documents.
- The Version field, the metadata blockquote, and the latest revision row show the same version.
- The PDF file name carries the version ([Section 11.2](#112-pdf-naming)).

---

## 8. Approval Block Standard

### 8.1 Format

The approval block is a numbered section titled Approval, placed before Revision History. A document may instead hold it as a subsection titled Approval inside a closing section. The block is a table with four columns: Role, Name, Decision, and Date.

The Decision column holds Pending or Approved. The Date column holds the date of the decision, or Pending.

```
## <N>. Approval

| Role           | Name            | Decision              | Date                    |
| -------------- | --------------- | --------------------- | ----------------------- |
| Lead Architect | <Approver Name> | <Pending or Approved> | <YYYY-MM-DD or Pending> |
```

### 8.2 Sign-off Procedure

1. The author completes the review checklist in [Section 12.1](#121-approval-workflow).
2. The approver named in the Approved By field reads the document against the checklist.
3. The approver records the decision and its date in the approval block.
4. On approval, the author fills the Approved By and Approval Date fields.
5. The author updates the Date field, the metadata blockquote, and the revision history, then commits the file.

In Phase 1 the approver is the Lead Architect.

---

## 9. Vocabulary Standards

These terms are fixed for all documents. This section records the priority and tag vocabulary decision. Document status is not part of a document. Live status is tracked in the Kanban board and the Blueprint dashboard.

### 9.1 Priority Values

| Value | Name     | Meaning                            |
| ----- | -------- | ---------------------------------- |
| P0    | Critical | Blocks other work. Complete first. |
| P1    | High     | Important for Phase 1 delivery.    |
| P2    | Medium   | Supports Phase 1 delivery.         |
| P3    | Low      | Can be deferred if time is short.  |

### 9.2 Tag Values

Tag values describe the lifecycle bucket a document belongs to. A Tag never changes.

| Value   | Meaning                                                             |
| ------- | ------------------------------------------------------------------- |
| UNBLOCK | Must be complete before the dependent design or coding work starts. |
| FOLLOW  | Written during or after the work that it describes.                 |
| HOLD    | Kept as a working file until its target document exists.            |

### 9.3 Exact Term Usage

- Every table, list, and field that gives a Priority or Tag uses the exact values in this section, with the same spelling and capitalisation.
- These words are not used as a Tag value: DONE, UNBLOCKED, FOLLOWED.
- Pending is valid only in the Approved By field, the Approval Date field, and the approval block.
- The Approved By and Approval Date fields record approval.
- The Tag field is fixed at document creation and never changes.
- Documents written before this standard are corrected to these terms.

---

## 10. Style Rules

### 10.1 No Emojis

No emoji appears in headings, text, tables, or code blocks. The badge images are the only pictures. Use words such as Pass and Fail instead of symbols.

### 10.2 No Marketing Language

Documents are descriptive and neutral. They describe what a document or a system does in plain terms, without praise or superlatives.

These words are not used: cutting-edge, world-class, revolutionary, seamless, robust, powerful, next-generation, leverage, unlock, and empower.

| Correct                                                      | Not Correct                                                     |
| ------------------------------------------------------------ | --------------------------------------------------------------- |
| This document is the master index for all Phase 1 documents. | This powerful, cutting-edge document revolutionises navigation. |

### 10.3 British English

Documents use British spelling: authorisation, organisation, behaviour, colour, centre, licence (noun), standardise, and summarise. Product names, quoted text, and registered document titles keep their original spelling.

### 10.4 Markdown Only

- Documents use markdown only. The badge `div` is the only HTML.
- Tags such as `br`, `span`, `table`, `hr`, and `u` are not used. Use blank lines and markdown tables.
- Templates and examples are in fenced code blocks.
- Angle-bracket placeholders appear only inside fenced code blocks or inline code.

### 10.5 Table Formatting

- Tables use pipes, a header row, and a separator row such as `| --- |`.
- The table is pipe-aligned: cells are padded with spaces so that the pipes line up in the source.
- A blank line precedes and follows each table.
- Use a table for structured data. Use a list for a sequence of steps.
- Column headings use Title Case.

### 10.6 Paragraph Length

A paragraph has two to four sentences and holds one idea. A single sentence is allowed as a lead-in to a table, list, or code block.

---

## 11. File Naming and Folder Rules

### 11.1 Source Markdown Naming

```
<Document ID>_<DocumentNameInPascalCase>.md
```

The document name is derived from the title in four steps: remove punctuation, split the title into words, capitalise the first letter of each word, and join the words without spaces. Acronyms keep their letters. The file name contains no version.

| Title                        | File Name                                         |
| ---------------------------- | ------------------------------------------------- |
| Document Template Standard   | `SRIS-P1-GOV-002_DocumentTemplateStandard.md`     |
| Microservices Identification | `SRIS-P1-ARCH-001_MicroservicesIdentification.md` |
| Sample Report (Draft/Final)  | `<Document ID>_SampleReportDraftFinal.md`         |

Git tracks the history of a file. The version is held in the metadata table.

### 11.2 PDF Naming

```
<Document ID>_<DocumentNameInPascalCase>_v<Version>.pdf
```

PDF files carry the version because they are frozen deliverables. They are produced at the end of Phase 1. The version in the file name equals the Version field at the time of generation.

```
SRIS-P1-GOV-002_DocumentTemplateStandard_v1.0.pdf
```

### 11.3 Folder Structure

Documents are stored under `docs/phase-1-foundation/`, in one folder per wave. The wave folder names and the full tree are in [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md), in the [register](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md#3-complete-document-register) and in [Section 7.2](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md#72-folder-structure).

The folder path template is below.

```
docs/phase-1-foundation/<wave-folder>/<Document ID>_<DocumentNameInPascalCase>.md
```

The path of this document, shown as a tree:

```
docs/
`-- phase-1-foundation/
    `-- wave-0-project-foundation/
        `-- SRIS-P1-GOV-002_DocumentTemplateStandard.md
```

### 11.4 Naming Non-Conformance

A file name or folder that does not follow this section is a defect. It is corrected before the file is committed.

If the file is already committed, it is renamed with `git mv` so that its history is kept. Every link that points to the old name is then updated, and the check in [Section 12.1](#121-approval-workflow) is repeated.

```
git mv <old file name> <new file name>
```

---

## 12. Document Lifecycle

### 12.1 Approval Workflow

The review checklist has six checks. All six must pass before a document is approved.

| Check      | Question                                                                                                                         |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Header     | Do the badges, title, subtitle, tagline, affiliation line, and metadata blockquote match [Section 2](#2-document-header-standard)? |
| Metadata   | Does the table have the 17 fields, in order, and do its values match the metadata blockquote?                                    |
| Structure  | Does the body follow [Section 5](#5-body-structure-standard)?                                                                    |
| Vocabulary | Are all Priority and Tag values from [Section 9](#9-vocabulary-standards)?                                                       |
| Links      | Does every Document ID in prose resolve to the correct relative path, whether the target file exists yet or not?                 |
| Style      | Does the document follow [Section 10](#10-style-rules)?                                                                          |

The sign-off steps are in [Section 8.2](#82-sign-off-procedure).

### 12.2 Superseding Rules

The Supersedes field records what the document replaces. The first version of a document states None (first version). A later version of the same document states the previous version, for example Version 1.0 of this document.

A document that replaces a different document cites that document in the citation format of [Section 6.1](#61-citation-format). The replaced file is removed in the same commit and the register is updated. Git keeps its history.

---

## 13. Approval

| Role           | Name        | Decision | Date       |
| -------------- | ----------- | -------- | ---------- |
| Lead Architect | Koushal Jha | Approved | 2026-10-12 |

---

## Revision History

| Version | Date       | Author      | Change                                                                                                                                                                            |
| ------- | ---------- | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.0     | 2026-10-11 | Koushal Jha | Initial release.                                                                                                                                                                  |
| 1.1     | 2026-10-11 | Koushal Jha | Removed Status from the standard: badges, metadata table, metadata blockquote, vocabulary, lifecycle, templates, and Appendix B.                                                  |
| 1.2     | 2026-10-12 | Koushal Jha | Removed the rule that forbids linking to files that do not exist yet. Every Document ID is now a hyperlink, whether the target file is committed or planned. |
| 1.3     | 2026-10-12 | Koushal Jha | Clarified that B.6 External Reference Documents holds sources outside the Phase 1 register. Phase 1 documents belong in B.1. |

---

## Appendix A: Metadata Table Template

Copy the table below into a new document. It has 17 rows. Replace each placeholder in angle brackets. Do not change the fixed values.

```
| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| Title              | <Document Title>                                                  |
| Software           | SRIS                                                              |
| Software Full Form | Sarathi Railway Information System                                |
| Team Codename      | Project Sarathi                                                   |
| Document ID        | <Document ID>                                                     |
| Task               | <One sentence describing the task>                                |
| Document Type      | <Document Type>                                                   |
| Milestone          | Phase 1 Foundation                                                |
| Classification     | Internal                                                          |
| Version            | <MAJOR.MINOR>                                                     |
| Date               | <YYYY-MM-DD>                                                      |
| Author             | <Name>, <Role>                                                    |
| Approved By        | <Name>, <Role> or Pending                                         |
| Approval Date      | <YYYY-MM-DD> or Pending                                           |
| Supersedes         | None (first version) or <Previous Version>                        |
| Related Documents  | See Appendix B                                                    |
| Affiliation        | Independent · Not affiliated with CRIS, IRCTC, or Indian Railways |
```

## Appendix B: Related Documents

### B.1 Directly Referenced Documents

| Seq | Document ID                                                                                | Document Name                          | Wave | Pri | Tag     |
| --- | ------------------------------------------------------------------------------------------ | -------------------------------------- | ---- | --- | ------- |
| 0.0 | [SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md)                 | Documentation Index and Navigation Map | 0    | P0  | UNBLOCK |
| 2.1 | [SRIS-P1-ARCH-001](../wave-2-architecture/SRIS-P1-ARCH-001_MicroservicesIdentification.md) | Microservices Identification           | 2    | P0  | UNBLOCK |

### B.2 Documents That Reference This Document

All other Phase 1 documents follow this standard. The complete list is in [B.5](#b5-master-documentation-index).

### B.3 Documents This Document Depends On (Upstream)

None.

### B.4 Documents This Document Unblocks (Downstream)

All other Phase 1 documents are written against this standard.

### B.5 Master Documentation Index

For the complete list of Phase 1 documents with sequence, ID, wave, priority, and tag, see:

[SRIS-P1-GOV-001](./SRIS-P1-GOV-001_DocumentationIndexAndNavigationMap.md) — Documentation Index and Navigation Map

### B.6 External Reference Documents

None.

### B.7 Document Conventions

The conventions for Priority and Tag values are defined in [Section 9](#9-vocabulary-standards) of this document.

---

**End of Document**