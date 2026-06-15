# Information Model Assurance (DfE)

IDS (Information Delivery Specification) files for automated compliance checking of IFC models against the Department for Education's (DfE) information requirements. Files are aligned with the RIBA Plan of Work delivery stages and developed to meet the DfE's Detailed Exchange Information Requirements (DEIR).

> **This repository is read-only.** To report issues with the IDS rules, contact DfE.BIM@education.gov.uk or raise a GitHub issue.

---

## Files

> The IDS files in this repository are generated from code using [Xbim.IDS.Generator](https://github.com/xBimTeam/Xbim.IDS.Generator) for maintainability.

- **Information Model Assurance Guide** (`ER-DFE-XX-XX-T-X-0030`) — full guidance on configuring and running checks
- **Combined** (`ER-DFE-XX-XX-L-X-00X0`) — all checks for a given RIBA stage in a single file
- **Combined — Core Only** (`ER-DFE-XX-XX-L-X-00X1`) — 'shall' checks for a given RIBA stage in a single file
- **Combined — Nomenclature and Classification Only** (`ER-DFE-XX-XX-L-X-00X2`) — naming conventions and classification checks for a given RIBA stage in a single file
- **[TokenReplacer/](TokenReplacer/)** (`TokenReplacer`) — basic html tool for token replacement
- **[Grouped/](Grouped/)** — one file per entity group (Project, Site, Building, Storey, Space, Zone, Object Type)
- **[Individual/](Individual/)** — one file per specification rule
- **[README.md](README.md)** — this file

---

## Document Control

| Revision | Status | Date | Amendment |
|---|---|---|---|
| Pnn | Sn | 2026-05-18 | Preparation for publication |
| C01 | A | 2026-06-16 | Initial publication of shared resource |


---

## Before use

The IDS files contain `{{token}}` placeholders for project specific values (project name, site name, storey heights, UPRN, etc.). **Tokens must be replaced before running checks** — unreplaced tokens will always fail. Use the Token Replacer tool.

### Known issues and skipped rules

Rules not implemented or with known issues are listed below. All other rules are implemented as specified.

| S21 ID | S25 ID | Rule | Issue |
|---|---|---|---|
| 04.04 | 04.04 | Building Storey Shall Have Unique Name | Skipped — IDS 1.0 has no unique constraint support |
| 05.04 | 05.04 | Space Shall Have Name That Is Unique | Skipped — IDS 1.0 has no unique constraint support |
| 05.05 | 05.05 | Space Shall Have Name Related Correctly To Each Floor | Skipped — IDS 1.0 cannot traverse spatial containment; a rule would check every Space against every floor's naming convention, producing incorrect failures |
| 06.08 | 06.08 | Zone Shall Have Spaces Allocated To It | Skipped — not expressible in IDS 1.0 (`partOf` only works from the Space side; rule 05.16 covers the inverse) |
| 07.01 | 07.01 | Object Type Shall Be Entity In Schema | Skipped — implemented but temporarily disabled due to an upstream IfcOpenShell/Bonsai bug with `xs:restriction` entity name handling in requirements |
| 07.06 | 07.06 | Object Type Shall Have Name That Is Unique | Skipped — IDS 1.0 has no unique constraint support |
| 08.03 | 08.03 | Object Occurrence Shall Have Unique Name | Skipped — IDS 1.0 has no unique constraint support |
| 08.13 | 08.19 | Object Occurrence Shall Not Contain Duplicate Names | Skipped — IDS 1.0 has no duplicate detection support |
| 08.14 | 08.20 | Object Occurrence Shall Have Layer Correctly Defined | Skipped — IDS 1.0 has no layer/presentation facet support |
