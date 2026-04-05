# CDC Budget & Workforce Reduction Dataset

**FY2026 Operational Plan and FY2027 Congressional Justification linked to CDC Reduction in Force (RIF) data**

This dataset links CDC budget data — drawn from two sources across FY2026 and FY2027 — to data from the 2025 CDC RIF. It enables program-level analysis of which CDC budget lines were simultaneously subject to enacted funding levels and workforce reductions.

Maintained by [Public Data Observatory](https://github.com/PublicDataObservatory).


## Contents

| File | Description |
|------|-------------|
| `hhs-budget-rif-op-cj.csv` | Subset budget data containing FY2026 Operational Plan and FY2027 CJ data linked to CDC 2025 RIF data. (see below) |
| `hhs-appropriations-repository-fy24-fy26.csv` | Main dataset with budget data from FY24–FY26 across eight budget source types and stages. Data can be linked via the unique_id. |
| `hhs-appropriations-source-registry.csv` | List of all sources used to create the HHS appropriations repository. |
| `data-dictionary.csv` | Data dictionary for budget and RIF fields. |
| `hhs-appropriations-repository-user-guide.md` | Full user guide including analytic considerations and filter reference for budget data only. |


## Dataset Overview

| Attribute | Value |
|-----------|-------|
| Fiscal years | FY2026, FY2027 |
| Budget sources | Operational Plan (OP) · Congressional Justification (CJ) |
| Sub-agencies | CDC · AHA (FY2027 CJ only — see reorganization note below) |
| Total rows | 314 |
| FY2026 OP rows | 169 |
| FY2027 CJ rows | 145 |

### FY2027 Reorganization Note

The FY2027 President's Budget proposes a significant structural reorganization of CDC programs. Key changes reflected in this dataset:

- **Administration for a Healthy America (AHA):** Several CDC programs are proposed for transfer to AHA. These appear under `sub_agency = 'AHA'` in the FY2027 CJ rows, including Chronic Disease and Health Prevention, HIV/AIDS, and Injury Prevention and Control. These transfers are proposals only and have not been enacted.
- **National Center for Chemicals and Toxins (NCCT):** A new proposed center that consolidates sub-programs previously housed across Environmental Health, Occupational Safety and Health, and Agency for Toxic Substances and Disease Registry (ATSDR). Sub-programs within NCCT are matched to their corresponding RIF center based on their original organizational home.
- **Program name changes:** Several programs appear under different names in the FY2027 CJ compared to prior years (e.g. "Viral Hepatitis, Sexually Transmitted Infections, and Tuberculosis Prevention" vs. the FY2026 name; "HIV/AIDS, Viral Hepatitis, STI and TB Prevention" in the FY2026 OP). See the crosswalk_note field for details.

### Programs Covered

**FY2026 Operational Plan (CDC)**
- Birth Defects, Developmental Disabilities, Disability and Health
- Buildings and Facilities
- Chronic Disease Prevention and Health Promotion
- Cross-Cutting Activities and Program Support
- Emerging and Zoonotic Infectious Diseases
- Environmental Health
- Global Health
- HIV/AIDS, Viral Hepatitis, STI and TB Prevention
- Immunization and Respiratory Diseases
- Injury Prevention and Control
- Occupational Safety and Health
- Public Health Preparedness and Response
- Public Health Scientific Services

**FY2027 Congressional Justification (CDC and AHA)**
- Birth Defects, Developmental Disabilities, Disability and Health *(AHA)*
- Buildings and Facilities
- CDC-Wide Activities and Program Support
- Chronic Disease and Health Prevention *(AHA)*
- Emerging and Zoonotic Infectious Diseases
- Global Health
- HIV/AIDS *(AHA)*
- Immunization and Respiratory Diseases
- Injury Prevention and Control *(AHA)*
- National Center for Chemicals and Toxins *(new proposed center — see reorganization note)*
- Public Health Preparedness and Response
- Public Health Scientific Services
- Viral Hepatitis, Sexually Transmitted Infections, and Tuberculosis Prevention


## Data Sources

### Budget Data

| Source | Fiscal Year | Stage | Released |
|--------|------------|-------|---------|
| FY2026 CDC Operational Plan | FY2026 | Enacted (post-enactment allocation) | 2026 |
| FY2027 CDC Congressional Justification | FY2027 | Request | March 2026 |
| FY2027 AHA Congressional Justification | FY2027 | Request | March 2026 |
| FY2027 OS Congressional Justification | FY2027 | Request | March 2026 |


### RIF Workforce Data
**Sources:**
- American Federation of Government Employees (AGFE) union tracking data
- CDC Data Project (independent tracking from public sources and direct reporting)
- Publicly available CDC organizational charts used to link work units to budget program areas

RIF data reflects the status of CDC employees as of the data capture date following the 2025 Reduction in Force actions. Figures represent FTEs across 125 unique program/work unit combinations. RIF data is linked to both budget sources using the same program-level matching methodology.

## Column Reference

### Budget Columns (23)

| Column | Type | Description |
|--------|------|-------------|
| `unique_id` | Text | Unique row identifier (e.g. CDC-000001). Can use to link to main HHS Appropriations Repository file. |
| `record_id` | Integer | Sequential record number |
| `fiscal_year` | Integer | Federal fiscal year (2026 = Oct 2025 – Sep 2026; 2027 = Oct 2026 – Sep 2027) |
| `agency` | Text | HHS |
| `sub_agency` | Text | CDC \| AHA |
| `program` | Text | Program account name as written in source |
| `sub_program` | Text | Sub-program level detail (where provided) |
| `sub_program_2` | Text | Second sub-program level (where provided) |
| `sub_program_3` | Text | Third sub-program level (rare) |
| `budget_source` | Text | Operational Plan \| Congressional Justification |
| `budget_stage` | Text | Enacted \| Request |
| `granularity` | Text | sub\_program\_level \| sub\_program\_2\_level \| sub\_program\_3\_level |
| `amount_millions` | Number | Funding in millions of dollars |
| `funding_type` | Text | Discretionary \| PPHF \| Total \| PHS Evaluation \| Mandatory |
| `program_status` | Text | Active \| Proposed Elimination \| Proposed Transfer to AHA \| etc. |
| `is_non_add` | Text | No \| Non-add \| Subcomponent |
| `notes` | Text | Qualitative context and source notes |
| `source_id` | Text | Reference to source registry |
| `source_page` | Integer | Page number in source document |
| `date_entered` | Date | Date record was entered (YYYY-MM-DD) |
| `entered_by` | Text | Initials of data entry person |
| `verified` | Text | Yes \| No |
| `crosswalk_note` | Text | Notes on program name variants across sources |

### RIF Data Columns (11)

| Column | Description |
|--------|-------------|
| `rif_center_abbrev` | Center/office abbreviation (e.g. NCIRD, NCCDPHP) |
| `rif_work_unit` | Specific work unit name within the center |
| `rif_certainty_level` | Confidence in work unit assignment (High / Medium / Low) |
| `rif_pct_rifd` | % of FTEs currently RIFd (admin leave + separated) |
| `rif_currently_rifd_count` | Count of FTEs currently under RIF action |
| `rif_not_impacted` | FTEs not impacted by the RIF |
| `rif_admin_leave` | FTEs on administrative leave |
| `rif_reinstated` | FTEs reinstated after RIF action |
| `rif_separated` | FTEs separated (terminated) |
| `rif_unclear` | FTEs with unclear RIF status |
| `rif_total_fte` | Total FTEs in the matched work unit |



## Important Caveats

**RIF figures are work-unit level, not program-budget level.** The RIF data tracks FTEs by CDC work unit (e.g. a specific division or center). When a work unit maps to multiple budget programs, the same FTE figures will appear on multiple budget rows. Do not sum RIF columns across rows without first deduplicating on `rif_matched_center` + `rif_matched_program`.

**`is_non_add` rows are non-additive.** Rows where `is_non_add = Non-add` or `Subcomponent` are already counted within a parent row. Filter `is_non_add = 'No'` for non-overlapping totals.

**RIF data reflects a point-in-time snapshot.** Reinstatement and separation figures may have changed after the data was captured.

**FY2027 CJ figures are proposed, not enacted.** All FY2027 rows represent the President's Budget Request and do not reflect Congressional action. Program transfers to AHA, the creation of NCCT, and any proposed eliminations or funding changes are proposals only.

**NCCT sub-programs are matched to their original RIF centers.** Because the National Center for Chemicals and Toxins did not exist as an organizational unit at the time of the RIF, its sub-programs are matched to the RIF center that housed them prior to the proposed reorganization (Environmental Health or Occupational Safety and Health). Some NCCT sub-programs have no RIF equivalent and will have null RIF values.


## License

This dataset is released under a Creative Commons Attribution ([CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.en)) license. Users are free to share, adapt, and build upon the material for any purpose, provided appropriate credit is given to Public Data Observatory.

**Suggested citation:**  
> **Public Data Observatory (2026).** *CDC Budget & Workforce Reduction Dataset: FY2026–FY2027 Budget Data Linked to CDC RIF Data. Version 1.0.* Licensed under Creative Commons Attribution 4.0 International (CC BY 4.0).


## Contact & Contributing

Questions or corrections: contact us at info@data-obs.org.
