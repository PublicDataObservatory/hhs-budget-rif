# HHS Appropriations Repository

A structured dataset tracking CDC and HHS budget authority across all stages of the federal appropriations process, from the President's Budget Request through Congressional action and final enactment.

Maintained by [Public Data Observatory](github website).

---

## Overview

This dataset covers fiscal years 2024–2027 and includes funding figures from eight budget source types: Congressional Justifications, Budgets in Brief, House and Senate committee reports, Joint Explanatory Statements, Public Laws, the CDC Operational Plan, and Continuing Resolutions. Each row traces to a specific source document and represents a dollar amount at a defined level of granularity — from agency-wide aggregates down to individual sub-program line items.

The current version focuses on CDC. Sub-agencies (AHA, ATSDR, Office of the Secretary) are included where they appear in CDC budget documents. Coverage will expand to additional HHS operating divisions in future versions.

---

## Contents

| File | Description |
|---|---|
| `hhs_appropriations_repository_fy24_fy27_v2.csv` | Main dataset with budget data from FY24–FY27 across eight budget source types and stages. |
| `hhs_appropriations_source_registry_v2.csv` | List of all sources used to create the HHS Appropriations Repository. |
| `datadictionary_v2.csv` | Data dictionary for budget fields. |
| `hhs_appropriations_repository_user_guide_v2.pdf` | Full user guide including analytic considerations and filter reference for budget data only. |

---

## Dataset at a Glance

- **2,698 rows** across FY2024, FY2025, FY2026, and FY2027
- **8 budget sources** covering all stages of the appropriations cycle
- **5 levels of granularity**: aggregate → program → sub-program → sub-program 2 → sub-program 3
- **5 funding types**: Discretionary, PPHF, PHS Evaluation, Mandatory, User Fees
- All amounts in **millions of dollars**

---

## Key Fields

| Field | Description |
|---|---|
| `fiscal_year` | Federal fiscal year (e.g., 2026 = Oct 2025 – Sep 2026) |
| `budget_source` | Source document (e.g., Congressional Justification, Joint Explanatory Statement) |
| `budget_stage` | Stage in appropriations process: Request, Committee, Enacted, or Continuing Resolution |
| `program` | Program account name as written in the source document |
| `amount_millions` | Dollar amount in millions. `$0` = explicitly zeroed; blank = not reported |
| `funding_type` | Discretionary, PPHF, PHS Evaluation, Mandatory, User Fees, or Total |
| `granularity` | Level of detail: aggregate, program_level, sub_program_level, sub_program_2_level, sub_program_3_level |
| `is_non_add` | `No` = safe to sum; `Non-add` or `Subcomponent` = already counted in a parent row |

---

## Quick Start

To get clean, non-overlapping program totals for a single source and year, filter:
```
granularity = 'program_level'
AND funding_type = 'Total'
AND is_non_add = 'No'
AND fiscal_year = [YEAR]
AND budget_source = [SOURCE]
```

See the user guide for a full filter reference and analytic considerations.

---

## Important Notes

- **Do not sum the Budget in Brief and Congressional Justification together** — both represent the President's Budget Request for the same fiscal year.
- **Public Law figures exclude PPHF** and contain no sub-program detail. Use the Joint Explanatory Statement for enacted sub-program figures.
- **FY2026 reorganization**: The President's Budget proposed transferring major CDC programs to a new Administration for a Healthy America (AHA). Congress did not enact these transfers. Filter `sub_agency = 'CDC'` when comparing FY2026 enacted figures against prior years.
- **FY2027 President's Budget**: Includes a major proposed reorganization. CDC programs covering HIV/AIDS, Chronic Disease, Injury Prevention, and Birth Defects are proposed for transfer to AHA. Environmental Health, Occupational Safety and Health, and ATSDR are consolidated into a new CDC center (National Center for Chemicals and Toxins). Health Statistics is proposed for transfer to the HHS Office of the Secretary. PPHF is proposed for elimination ($0). FY2027 data reflects President's Budget Request and the House Appropriations Committee recommendation — Senate committee report, JES, Public Law, and Operational Plan are not yet available.
- **FY2027 House Appropriations Committee Report** (added June 2026): The House LHHS Subcommittee recommendation for FY2027 is included (197 rows, source S028). The Committee recommends a total CDC program level of $8,164,411,000, compared to the FY2026 enacted level of $9,202,991,000 and the President's Budget request of $6,345,461,000. The FY2027 House report restores PPHF ($1,398,375,000) and does not enact the proposed AHA or OS transfers. Senate committee report not yet available.

---

## Sources

All data is derived from publicly available federal budget documents. Full source list with URLs is available in Section 6 of the user guide.

---

## License

This dataset is in the public domain. Citation of the source is appreciated:

> Public Data Observatory (2026). *HHS Appropriations Repository: A Structured Dataset of CDC and HHS Budget Authority, FY2024–FY2027*. Version 1.1.

---

## Contact

Questions or corrections: contact us at info@data-obs.org.
