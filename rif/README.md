# CDC FTE RIF Branch-Level Dataset

**Branch-level FTE tracking data for the 2025 CDC Reduction in Force (RIF)**

This dataset tracks the workforce impact of the 2025 CDC Reduction in Force (RIF) at the branch level — the most granular organizational unit available. Each row represents a single CDC branch (or division/office where branch-level detail was not available) and records how many full-time employees (FTEs) fell into each RIF status category. RIFs of entire branches occurred on 4/1/2025 and 10/10/2025 and reinstatements occurred multiple times between May 2025 through Jan 2026.

Reductions in federal employees due to other reasons of attrition is not captured in this dataset. As of April 3, 2026, the Office of Personnel Management reports a loss of 3,087 federal employees in 2025 and 2026 combined, amounting to a 24% loss of the 12,820 federal employees in 2024.

Maintained by [Public Data Observatory][(https://github.com/PublicDataObservatory].

---

## File

| File | Description |
|------|-------------|
| `cdc-fte-rif-branch-2025.csv` | Branch-level RIF FTE counts — 576 rows, 8 columns |

---

## Dataset Overview

| Attribute | Value |
|-----------|-------|
| Rows | 576 |
| Columns | 8 |
| Granularity | Branch (where available); Division or Office otherwise |
| Centers covered | 27 named CDC centers/offices + 1 "Unclear" category |
| Total FTEs tracked | ~12,910 across all status categories |
| Source | AGFE union data and CDC Data Project (see Sources below) |

---

## Centers Covered

| Center / Office |
|----------------|
| Agency for Toxic Substances and Disease Registry |
| Global Health Center |
| National Center for Chronic Disease Prevention and Health Promotion |
| National Center for Emerging and Zoonotic Infectious Diseases |
| National Center for Environmental Health |
| National Center for HIV, Viral Hepatitis, STD, and TB Prevention |
| National Center for Health Statistics |
| National Center for Immunization and Respiratory Diseases |
| National Center for Injury Prevention and Control |
| National Center on Birth Defects and Developmental Disabilities |
| National Institute for Occupational Safety and Health |
| Office of Communications |
| Office of Equal Employment Opportunity |
| Office of Financial Resources |
| Office of Health Equity |
| Office of Human Resources |
| Office of Laboratory Science and Safety |
| Office of Policy, Performance, and Evaluation |
| Office of Public Health Data, Surveillance, and Technology |
| Office of Readiness and Response |
| Office of Safety, Security, and Asset Management |
| Office of Science |
| Office of the Chief Information Officer |
| Office of the Chief Operating Officer |
| Office of the Chief of Staff |
| Office of the Director |
| Public Health Infrastructure Center |
| Unclear *(see notes)* |

---

## Column Reference

| Column | Type | Description |
|--------|------|-------------|
| `Center` | Text | CDC center or office name (top-level organizational unit) |
| `Division` | Text | Division or sub-office within the center |
| `Branch` | Text | Branch within the division. Null (~42 rows) where branch-level detail was not available — the row represents the division or office directly |
| `fte_not_impacted` | Number | FTEs confirmed as not impacted by the RIF |
| `fte_reinstated` | Number | FTEs reinstated following an initial RIF action |
| `fte_admin_leave` | Number | FTEs currently on administrative leave as part of the RIF process |
| `fte_separated` | Number | FTEs separated (terminated) through the RIF |
| `fte_unclear` | Number | FTEs whose RIF status could not be determined from available sources |

> **Note on nulls:** A null value in any FTE column means no FTEs of that status were recorded for that branch — it does not necessarily mean zero. See the Caveats section below.

---

## FTE Totals

| Status | Total FTEs | Rows with data |
|--------|-----------|---------------|
| Not impacted | 8,622 | 370 |
| Reinstated | 3,188 | 144 |
| Admin leave | 329 | 17 |
| Separated | 730 | 45 |
| Unclear | 41 | 2 |

> These totals are row-level sums. Because RIF actions unfolded over time and some individuals moved between statuses (e.g. separated → reinstated), the categories are not mutually exclusive. Do not sum all five columns together to derive a total headcount.

---

## Data Sources

RIF status data was compiled from two tracking sources:

- **AGFE union data** — RIF actions reported through American Federation of Government Employees union representation channels
- **CDC Data Project** — independent tracking effort compiling RIF status from publicly available sources and crowd sourcing.

Publicly available CDC organizational charts were used to assign branches and divisions to the correct center-level hierarchy.

---

## Caveats and Limitations


**Point-in-time snapshot.** RIF actions continued to evolve after this data was captured. Reinstatement and separation figures in particular may not reflect the current state of affected employees.

**Null ≠ zero.** A null in an FTE column means the status was not recorded for that branch, not necessarily that no employees had that status. Data completeness varies by center and division.

**Branch-level data not available for all units.** Approximately 42 rows (7%) represent divisions or offices directly because branch-level breakdowns were not available in the source data. The `Branch` column is null for these rows.

**"Unclear" center row.** One row has `Center = Division = Branch = "Unclear"` (65 FTEs not impacted). These are employees whose organizational unit could not be determined from available sources.

**Double-counting risk across status categories.** Some employees may appear across multiple status columns if their status changed over the course of the RIF (e.g. initially separated, then reinstated). Interpret status columns independently rather than summing them to derive a total workforce figure.

**Coverage is not exhaustive.** Not all CDC branches are represented. Gaps reflect limitations in the underlying source data, not confirmation that those units were unaffected.

---

## Quick-Start Filter Recipes

```
# All rows for a specific center
Center = 'National Center for Immunization and Respiratory Diseases'

# Only rows with branch-level detail
Branch IS NOT NULL

# Branches with any separated FTEs
fte_separated > 0

# Branches with any ongoing RIF action (admin leave or separated)
fte_admin_leave > 0 OR fte_separated > 0

# Exclude the "Unclear" catch-all row
Center != 'Unclear'
```

---

## Relationship to Other Files

This file provides the most granular available view of the 2025 CDC RIF — at the branch level within each center. It complements the `fy2026-jes-rif-linked.csv` dataset, which links RIF data aggregated to the program/budget-line level to enacted FY2026 funding figures from the Joint Explanatory Statement.

| File | Granularity | Primary use |
|------|-------------|-------------|
| `cdc-fte-rif-branch-2025.csv` | Branch | Workforce impact analysis by organizational unit |
| `fy2026-jes-rif-linked.` | Budget program | Budget-to-workforce linkage analysis |

---

## License

This dataset is released under a Creative Commons Attribution ([CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.en)) license. Users are free to share, adapt, and build upon the material for any purpose, provided appropriate credit is given to Public Data Observatory.

**Suggested citation:**  
> **Public Data Observatory (2026).** *CDC FTE RIF Branch-Level Dataset: 2025 CDC Reduction in Force by Branch. Version 1.0.* Licensed under Creative Commons Attribution 4.0 International (CC BY 4.0).

---

## Contact & Contributing

Questions or corrections: contact us at info@data-obs.org.
