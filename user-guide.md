# HHS Appropriations Repository User Guide
CDC and HHS Sub-Agencies · FY2024--FY2027 <br>
Appropriations Tracking Across Budget Stages <br>

*April 2026*
<br>
## Information about HHS Appropriations Repository 

### Recommended Citation
**Public Data Observatory (2026).** *HHS Appropriations Repository: A Structured Dataset of CDC and HHS Budget Authority, FY2024-FY2027. (Version 1.0).* 
Licensed under Creative Commons Attribution 4.0 International (CC BY 4.0). 
<br>

### Public Domain Notice
This publication is open access under the [[Creative Commons BY 4.0
license]{.underline}](https://creativecommons.org/licenses/by/4.0/). It
may be reproduced or adapted with attribution. This publication may not
be reproduced or distributed for a fee without specific written
authorization from a Public Data Observatory agent.
<br>

### Data Sources
All figures are derived from publicly available federal budget documents
published by OMB, HHS, CDC, and the U.S. Congress. Source documents are
identified in the Source Registry section of this guide.
<br>

### Scope Note
This dataset currently focuses on CDC only and other HHS sub-agencies
(AHA, ATSDR, and Office of the Secretary) are included if they appear in
CDC budget submissions. Future versions will expand coverage to
additional HHS operating divisions and agencies.
<br>

### Source document authority
In all cases of discrepancy between this tracker and the original source
documents, the original source document is authoritative.
<br>

### Version History
| **Version** | **Date** | **Notes** | **Release Date**|
|-------------|----------|-----------|------------------|                                                                      
|  v1.0       |04/01/2026|This dataset includes FY2024-FY2027 CDC budget data derived from the President's Budget, House and Senate appropriations, Joint Explanatory Statements, Public Laws, and Operating Plans, *where available.*|  |               
<br>

## 1. Overview

The HHS Appropriations Repository is a structured, row-level dataset
focused on the Centers for Disease Control's (CDC) budget data. Other
HHS sub-agencies (e.g., ATSDR) may be included when they are referenced
within CDC budget documents. For FY2026, a subset of budget data for the
Administration for a Healthy America (AHA) and the Office of the
Secretary (OS) is also included, reflecting proposals to shift certain
CDC programs to these entities. It captures funding amounts from all
major stages of the federal appropriations process--from the
President's Budget Request through Congressional action to final
enactment--enabling cross-source, cross-year, and cross-program
analysis of HHS and CDC discretionary and mandatory funding. Each row
traces to a specific source document and represents a precise dollar
amount at a defined level of granularity.

### 1.1 What Is Covered

  | **Dimension** | **Coverage**                                                       |
  |--------------| --------------------------------------------------------------------|
  |Fiscal Years  |  FY2024 · FY2025 · FY2026 · FY2027                                  |
  | Sub-Agencies |  CDC · AHA (only CDC programs) · ATSDR · OS (only CDC programs)     |
  | Budget Stages | Request · Committee · Enacted · Continuing Resolution              |                                      |
  | Budget Sources|  Budget in Brief · Congressional Justification · Budget in Brief · House Report · Senate Report · Joint Explanatory Statement · Public Law · Operational Plan · Continuing Resolution |
 | Program Depth |  Aggregate → Program → Sub-Program → Sub-Program 2  → Sub-Program 3 |                                  |
 | Funding Types |  Discretionary · PPHF · PHS Evaluation · Mandatory · User Fees      |                                       |
 | Records       |   2,053 rows                                                        |

<br>

### 1.2 Budget Sources and Appropriations Process

Each row in the dataset is tied to a specific document in the federal
appropriations cycle. The table below shows which documents are included
by fiscal year and what each document represents. Where a document is
not present, the reason is noted.

  |**Document**   | **FY24**  | **FY25** |  **FY26**  |  **FY27\*** | **Stage**  | **Produced By** | **Granularity** |
  |---------------| ----------| ---------| -----------| ------------| -----------| ----------------| -----------------|
  |President’s Budget (PB): Budget in Brief (BIB) | ✓  |  ✓  |  ✓  |   ✓ |  Request  |   White House/OMB/HHS |  Program only |
  |President’s Budget (PB): Congressional Justification (CJ) | ✓  |  ✓  |  ✓  |   ✓ |  Request  |   White House/OMB/HHS |  Program + sub-program |
  |House Committee Report | N/A²  |  ✓  |  ✓  |    |  Committee  |   House Appropriations Committee |  Program + sub-program |
  |Senate Committee Report | ✓  |  ✓  |  ✓  |    |  Committee  |   Senate Appropriations Committee |  Program + sub-program |
  |Joint Explanatory Statement (JES) | ✓  |  N/A²  |  ✓  |    |  Enacted  |   Conference (H+S)  |  Program + sub-program |
  |Public Law | ✓  |  N/A²  |  ✓  |    |  Enacted  |  Congress (enrolled) |  Program only; discretionary only |
  |Operational Plan (OP) | ✓  |  Not added¹  | Not added¹  |    |  Enacted  |  CDC |  Program + sub-program |
  |Continuing Resolution (CR) |   N/A²   |  ✓  |  N/A²   |    |  CR  |  Congress |  Aggregate only |

*\* FY27 Congressional Reports will be available when they released later
in 2026.*

**¹ Not added:** *Document exists but has not yet been entered into the
dataset.*

**² N/A:** *No document of this type exists for this fiscal year.
(FY2025 was funded under a CR; no JES or Public Law was enacted).*

> **Note: CJ and BIB both represent the President's Budget Request.** Do
> not sum them--they cover the same fiscal year. Use the CJ for
> detailed analysis; use the BIB for high-level cross-checks.
>
> **Note: Public Law vs. JES:** Both are Enacted budgets. Public Law
> contains program-level lump sums (no PPHF, no sub-program detail). JES
> contains sub-program-level enacted instructions including PPHF. Use
> the JES for complete enacted sub-program figures.

<br>

## 2. Methodology

The dataset was constructed through systematic extraction of funding
figures from official federal budget publications. The following
describes the key methodological decisions.

**Source Selection**

Source documents were selected to provide complete coverage of the
annual appropriations cycle--from initial request through final
enactment--for fiscal years 2024 through 2026. For each year, we
attempted to include the Congressional Justification, Budget in Brief,
House and Senate committee reports, the enacted Joint Explanatory
Statement or Public Law, and (where available) the CDC Operational Plan.
Documents not yet added are noted in the availability matrix in Section
1.2. Refer to the source registry for the full list of data sources.

<br>

**Data Extraction**

Figures were extracted directly from the source documents at the lowest
available level of detail. For each program account, we captured amounts
by funding type (Discretionary, PPHF, PHS Evaluation, Mandatory) **where
the source document provided that breakdown.** In some instances,
documents did not provide funding type. Amounts are stored in millions
of dollars.

<br>

**Granularity and Hierarchy**

The dataset uses a five-level hierarchy: aggregate, program_level,
sub_program_level, sub_program_2_level, and sub_program_3_level. Each
level is populated only when the source document provides that detail.
Sub-program levels are entered as they appear in the source, preserving
original naming conventions. Rows at sub_program_2_level and
sub_program_3_level should not be summed with their parent rows to avoid
double-counting.

<br>

**Program Name Handling**

Program names are entered exactly as they appear in each source
document. Where the same program account is named differently across
documents or years, the variation is documented in the crosswalk table
in Section 3.8.

<br>

**FY2026 Reorganization**

The FY2026 and FY2027 President's Budget proposed transferring major CDC
programs to a newly created Administration for a Healthy America (AHA)
and moving NCHS to the Office of the Secretary. These proposed transfers
are tracked under sub_agency = 'AHA' or 'OS' in the FY2026 CJ and BIB
rows. Congress did not enact these transfers---the FY2026 JES restores
all programs to CDC. AHA BIB program areas are remapped to their
CDC-origin program names for analytical consistency; the original BIB
section heading is recorded in the notes field.

<br>

**Aggregate Construction**

Aggregate rows (granularity = 'aggregate') are calculated as the sum of
program level Total rows for a given sub-agency, source, and fiscal
year. Exclusions from the CDC aggregate are documented in Section 3.5.
Where the aggregate from the source document differs from the sum of
entered program rows, this is documented in the notes field of the
aggregate row.

<br>

## 3. Analytic Considerations

This section documents key caveats and data nuances. Ignoring these can
lead to significant double-counting or misinterpretation.

### 3.1 Non-Adds: Explicit vs. Implicit

A non-additive item ("non-add") is a budget amount that is displayed for
informational or reporting purposes but is already included within a
higher-level total and should not be added to that total. Non-adds are
used to show the distribution of funding within a program without
affecting aggregate funding levels. [Some earmarks may be classified as
non-additive because they are specific \"carve-outs\" from a larger pool
of money that has already been counted in the total.]{.mark}

Non-adds were included when explicitly referenced in the source
documents. In some cases, budget lines may function as non-adds but are
not identified as such in the documentation. Both non-adds and
sub-components are already accounted for within their parent rows.
Therefore, they should be excluded from totals during analysis to avoid
double counting. When filtering select "No" for this field.

  | **Value**   |   **Meaning**                   |    **Safe to Sum?**  |
  |-------------|--------------------------------|---------------------|
  |No           | Independent line item. Not contained within any sibling row. | Yes -- with other 'No' rows at same level |
  |Non-add      | Explicitly labeled ‘(non-add)’ in source. Already counted within a parent row. | No — will double-count |
  |Subcomponent| A sub_program_2 or sub_program_3 row that is a structural breakdown of its parent. Not necessarily labeled non-add in the source, but non-additive by definition. | No — will double-count |

  <br>

### 3.2 Comparing Across Years and Documents

Several factors require attention when comparing figures across fiscal
years or budget sources:

- **Document type:** Only compare like with like. CJ to CJ, Senate to
  Senate, JES to JES. Avoid comparing a CJ figure against a committee
  report figure without acknowledging they represent different stages of
  the process. When comparing across different document types, use the
  program level to ensure consistent, like-for-like comparisons. Also
  consider which funding types are included, as some sources may exclude
  certain categories (e.g., PPHF is not included in all budget
  documents).

- **Program names:** The same program account may be named differently
  across years and documents. Always consult the Program Crosswalk
  before joining data across sources.

- **Sub-agency shifts:** In FY2026, programs proposed for AHA transfer
  appear under sub_agency = 'AHA' in the CJ and BIB, but under
  sub_agency = 'CDC' in the enacted JES. Filter by sub_agency = 'CDC' to
  compare only enacted figures.

- **EEOICPA amounts:** The mandatory EEOICPA amount differs by year
  (\$50.763M in FY2024--2025 CJ/BIB; \$55.358M in committee reports and
  JES). Check the aggregate notes field for the exact breakdown.
  **EEOICPA is the only mandatory program included in the aggregate
  total**. This approach was used to align with the House and Senate,
  which also include EEOICPA in their aggregate totals.

  - ***Note:*** The President's Budget (Budget in Brief and
    Congressional Justification) typically excludes EEOICPA from the
    total program budget. When comparing other budgets to the
    President's Budget, be sure to exclude EEOICPA to ensure alignment
    with the reported totals.

- **ATSDR:** The CDC director serves as the administrator of ATSDR, but
  it is considered a separate agency. In the President's Budget (Budget
  in Brief and Congressional Justification), ATSDR is sometimes included
  in the reported program totals. ATSDR [is not included]{.underline} in
  the CDC budget of congressional documents or the enacted budget.

- **PPHF:** PPHF is shown as a separate funding_type row alongside
  Discretionary rows. The program-level Total includes both. Do not add
  Total and PPHF rows together. Some budget documents exclude PPHF,
  including the enacted Public Health Law documents. FY2026 (and FY2027)
  President's Budget eliminates PPHF (\$0), while the enacted JES
  restores it at \$1,398.375M. Year-over-year comparisons of Total rows
  will reflect this shift. **PPHF is considered mandatory but is
  typically reported as a separate part of the budget.**

- **Public Law vs. JES:** Both are 'Enacted' budgets but Public Law
  excludes PPHF and has no sub-program detail. Do not compare Public Law
  totals against JES totals without adjustment. **For granular program
  data, JES is the source to use.**

- **Mandatory Programs:** Except for EEOICPA, mandatory programs are
  excluded from program totals. Mandatory programs are typically
  outlined in the President's Budget in more detail.

<br>

### 3.5 Aggregate Totals Methodology

The following shows what is included and excluded from CDC aggregate
rows:

 | **Program / Item**        |    **CJ / BIB**     |   **House / Senate / JES**  |       **Notes**               |    
 |---------------------------| --------------------|-----------------------------|-------------------------------|
 | CDC discretionary programs|    Included         |      Included               | All standard program accounts |
 | EEOICPA mandatory         |    Included         |      Included               | Included for cross-source comparability. Typically, not included as part of the discretionary CDC total in President’s Budget documents. |
 | ATSDR                     |    Excluded         |      N/A                    | Has its own separate aggregate row. Not in committee reports. Sometimes included in CDC total in President’s Budget documents. |
 | VFC, VFA, WTC, PHSSEF, CVI|    Excluded         |      Excluded               | Mandatory or proposed programs not in committee report CDC total. |
 | PPHF                      |    Included         |      Included               | Considered mandatory but typically reported separately as part of budget. Part of Total; also shown as separate PPHF aggregate row. |
 | PHS Evaluation            |    Included         |      Included               | Where available, has its own separate aggregate and program row. |

 <br>
 
### 3.6 Sub-Program Hierarchy and Double-Counting Risk

The dataset uses up to five levels of hierarchy. Rows at deeper levels
are always subcomponents of their parent and must not be summed with the
parent row.

  |**Source**                   | **Aggregate** |  **Program**  | **Sub-Prog** |  **Sub-Prog\_2**  | **Sub-Prog_3\***  | **Notes**           |
  |-----------------------------|---------------|---------------|--------------|-------------------|-------------------|---------------------|
  | Budget in Brief             |     ✓         |      ✓        |     ---      |      ---          |       ---         |                     | 
  | Congressional Justification |     ✓         |      ✓        |     ✓        |      ✓            |       Rare        |                     |
  |House/Senate Committee Report|     ✓         |      ✓        |     ✓        |      ✓            |       Rare        |                     |
  |Joint Explanatory Statement  |     ✓         |      ✓        |     ✓        |      Limited      |       ---         |                     |
  |Public Law                   |     ✓         |      ✓        |     ---      |      ---          |       ---         | Bill text only      |
  |Operational Plan             |     ✓         |      ✓        |     ✓        |      ✓            |       Rare        | FY2024 only         |
  |Continuing Resolution        |     ✓         |      ---      |     ---      |      ---          |       ---         | Single aggregate row| 

  
  \* Sub-program_3 rows exist in only a small number of cases:
  - Injury Prevention › Intentional Injury › Domestic Violence and Sexual Violence › Child Maltreatment / Child Sexual Abuse Prevention
  - Chronic Disease › Cancer Prevention and Control › Breast and Cervical Cancer › WISEWOMAN
  - Environmental Health › Environmental Health Activities › Environmental Health Capacity › Climate and Health

  > Note: If your query includes both sub_program_3_level rows and their
  > sub_program_2_level parents, you will double-count. Filter WHERE
  > sub_program_3 IS NULL, or filter WHERE is_non_add = 'No' for clean
  > totals.

<br> 

### 3.7 \$0 vs. Blank

- **\$0.000 ---** The source document explicitly shows this program at
  zero funding (e.g., programs proposed for elimination in FY2026 PB, or
  PPHF set to \$0)

- **Blank (null) ---** The source did not report a figure. Does not mean
  zero funding---it means detail was not provided at that level.

<br>

### 3.8 Funding Types Available by Budget Source

The table below depicts funding types available by budget source. When
analyzing data, consider which funding types are included, as some
sources may exclude certain categories (e.g., PPHF is not included in
all budget documents).

  | **Budget Source**                  | **Stage**     |  **Discretionary** |  **PPHF**  |    **PHS Evaluation**   |   **Mandatory\*** |  **User Fees** |
  |------------------------------------|---------------|--------------------|------------|-------------------------|-------------------|----------------|
  |**Budget in Brief (BIB)**           |  Request      |      X             |   X        |    X                    | X                 | X              |                                                                                        
  |**Congressional Justification (CJ)**|  Request      |      X             |   X        |    X                    | X                 | X              | 
  | **House Committee Report**         |  Committee    |      X             |   X        |    X                    | X                 | ---            | 
  | **Senate Committee Report**        |  Committee    |      X             |   X        |    X                    | X                 | ---            | 
  | **Joint Explanatory Statement (JES)**|  Enacted    |      X             |   X        |    X                    | X                 | ---            | 
  | **Public Law**                     |  Enacted      |      X             |   ---      |    X                    | X                 | ---            |
  |**Operational Plan (OP)**           |  Enacted      |      X             |   X        |    X                    | X                 | ---            |
  |**Continuing Resolution (CR)**      |  CR           |      ---           |   ---      |    ---                  | ---               | ---            |

  \* The BIB and CJ provide the most comprehensive list of mandatory
programs. In contrast, congressional budget documents (House, Senate,
and public law) typically include only EEOICPA and exclude other
mandatory programs.

<br>

### 3.9 Program Names Across Sources

All name variants are entered exactly as they appear in the source. Key
examples:

- HIV/AIDS, Viral Hepatitis... program: abbreviated in most CJ/BIB
  sources; full name in FY2025 House, FY2026 Senate, and JES.

- Quarantine → Travel and Port Health Protection: renamed in FY2026 CJ
  and House; reverted in FY2026 Senate and JES.

- Antibiotic Resistance Initiative → Antimicrobial Resistance
  Initiative: only in FY2026 CJ and House.

- CDC-Wide Activities → Cross-Cutting Activities: varies within FY2026
  documents.

The table below summarizes how each major program account is named
across sources. 'Same' = identical to the canonical name shown in the
first column. When comparing budgets across documents and/or years,
consider naming changes.

  
  | **Canonical Name**  |  **CJ**        |     **BIB**        |    **House**   |   **Senate**  |  **JES**     |     **OP**    |
  |---------------------|----------------|--------------------|----------------|---------------|--------------|---------------|
  |Immunization and Respiratory Diseases	|Same	|Same	|Same	|Same	|Same	|Same|
  |HIV/AIDS, Viral Hepatitis, STI and TB Prevention	| FY24–25: changed in FY26: Viral Hepatitis, STI and TB	|Same as CJ	|FY25: Full name FY26: abbreviated |	FY25: abbreviated FY26: Full name	| Full name	Same as CJ|
  |Emerging and Zoonotic Infectious Diseases |	Same |	Same	|Same	| Same |	Same |	Same|
  |Chronic Disease Prevention and Health Promotion |	FY24–25: Same FY26: Proposed to AHA	| FY24: Same FY25: drops Prevention FY26: AHA programs |	Same |	Same |	Restored to CDC	Same|
  |Birth Defects, DD, Disability and Health |	Singular: Disability |	FY24: Singular FY25–: Plural	| Plural: Disabilities	| Plural	| Plural | 	Singular|
  |Public Health Scientific Services |	Same |	FY24–25: inserts ‘and’ |	Same |	Same |	Same |	Same|
  |Occupational Safety and Health |	Same |	Same	| FY25: NIOSH name FY26: OSH	| Same	| Same |	Same|
  |CDC-Wide Activities and Program Support |	FY24–25: CDC-Wide FY26: Cross-Cutting | 	FY24: CDC-Wide FY25: Crosscutting	| Same |	Sam e|	Same | Cross-Cutting|
  |ATSDR |	sub_agency=ATSDR |	sub_agency=ATSDR |	N/A |	N/A |	N/A |	N/A|
  |EEOICPA |	FY24–25: CDC FY26: AHA (proposed) |	sub_agency=CDC |	Full name in committee |	Same |	sub_agency=CDC |	Same|
  |National Center for Health Statistics|	FY26: sub_agency=OS PHS Eval $175.297M |	FY26: sub_agency=OS $175M |	In PHSS $187.397M |	In PHSS	In PHSS |	N/A|

> **Tip:** Always use the crosswalk when joining data across sources or years.

<br>

## 3.10 FY2026 Reorganization Caveats

The FY2026 President's Budget proposed creating the Administration for a
Healthy America (AHA) and transferring major CDC programs to it. Key
tracking considerations:

- **AHA programs:** sub_agency = 'AHA', program_status = 'Proposed
  Transfer to AHA' in FY2026 CJ and BIB. None were enacted. Proposed
  again for FY2027.

- **OS transfer:** NCHS tracked under sub_agency = 'OS' in FY2026
  CJ/BIB. Not enacted. Proposed again for FY2027.

- **Enacted (JES):** All programs restored to sub_agency = 'CDC' under
  original names.

- **AHA BIB remapping:** AHA BIB programs are remapped to CDC-origin
  program areas for consistency. The original BIB section heading is
  recorded in the notes field (e.g., Alzheimer's appears under 'Policy,
  Research and Oversight' in BIB but is tracked under Chronic Disease
  and Health Prevention).

- **MAHA Initiative:** Three programs in the AHA CJ appear under the
  MAHA Initiative (p.29): Alzheimer's Disease Program (\$35M), Childhood
  Lead Poisoning Prevention (\$51M), and Lead Exposure Registry (\$5M).
  All are tracked under their standard CDC program areas with notes
  referencing their MAHA location.

> **Note:** When comparing FY2026 President's Budget or Congressional
> Justification data to prior years or enacted amounts, CDC-related
> programs proposed for transfer to AHA and OS should be included to
> ensure comparability across years. Although these programs appear
> under AHA and OS in FY2026 budget documents, the proposed transfers
> were not implemented, and the programs remain historically part of
> CDC. In the filter, make sure all relevant sub-agencies are selected
> (e.g., AHA, CDC, OS) when comparing across years. The President's
> Budget in FY2027 also proposes move to AHA and OS for these programs
> pending approval from Congress.

<br>

## 4. Analyzing the Data

This section covers common analytical tasks.

### 4.1 Comparing Across Budget Stages

Use the budget_stage field to compare the same year across stages:

- **Request ---** President\'s Budget (CJ or BIB). Do not sum both.

- **Committee ---** House or Senate markup. Neither is law; useful for
  tracking Congressional intent.

- **Enacted ---** JES (sub-program detail), Public Law (program-level
  bill text), or Operational Plan (post-enactment allocation).

- **Continuing Resolution ---** CR placeholder aggregate only; no
  program-level detail.

> **Note: Public Law vs. JES:** Both are Enacted budgets. Public Law
> shows program-level lump sums from bill text (excludes PPHF). JES
> shows sub-program-level conference instructions (includes PPHF). Use
> JES for complete enacted sub-program figures.

<br>

### 4.2 Tracking Programs Across Years

When tracking a single program from FY2024 to FY2027 use the
crosswalk_note field and Program Crosswalk sheet to identify name
variants. Example: 'Quarantine' in FY2024/2025 = 'Travel and Port Health
Protection' in FY2026 CJ/House---the same account under a renamed line.

<br>

### 4.3 Mandatory Programs

Mandatory programs (funding_type = 'Mandatory') are tracked for
completeness but are typically not included in budget documents' stated
discretionary totals. Programs include:

- **Vaccines for Children (VFC):** FY2024-FY2027; remains with CDC.

- **World Trade Center Health Program:** FY2024/2025 CJ/BIB; proposed to
  AHA in FY2026 CJ.

- **EEOICPA:** All years. FY2026 CJ sub_agency=AHA; all other sources
  sub_agency=CDC.

- **VFA, PHSSEF, CVI:** Proposed law only; never enacted.

> **Tip:** Mandatory programs also have a funding_type = 'Total' row
> (same amount) for pivot table visibility. Filter WHERE funding_type =
> 'Mandatory' to work with mandatory amounts directly. Filter WHERE
> funding_type = 'Discretionary' AND is_non_add = 'No' to exclude
> mandatory from totals.

<br>

### 4.4 Filter Reference

**Granularity --- Field Population Rules**

  |**granularity**       |  **program**       |   **sub_program** |  **sub_program_2** |  **sub_program_3** |
  |----------------------|--------------------|-------------------|--------------------|--------------------|
  | aggregate            |   CDC/AHA/ATSDR/OS |  blank            | blank              | blank              |
  | program_level        |   Populated        |  blank            | blank              | blank              |
  | sub_program_level    |   Populated        |  Populated        | blank              | blank              |
  | sub_program_2_level  |   Populated        |  Populated        | Populated          | blank              |
  | sub_program_3_level\*|   Populated        |  Populated        | Populated          | Populated          |

\* Same something about the risk of double counting

<br>

**Common Filter Recipes**

|  **Use Case**                         |         **Filter**                                                          |
|---------------------------------------|-----------------------------------------------------------------------------|
| Program totals — one year, one source	    | granularity='program_level' AND funding_type='Total' AND is_non_add='No' |
| Discretionary only (excl. PPHF/Mandatory) |	funding_type='Discretionary' AND is_non_add='No'                        |
| Exclude sub-component rows	              | is_non_add='No'
| Exclude proposed/eliminated programs	    | program_status='Active'
| CDC programs only (exclude ATSDR)*	      | sub_agency='CDC'
| FY2026 enacted sub-program detail	        | fiscal_year=2026 AND budget_source='Joint Explanatory Statement'
| Enacted program-level totals (bill text)	| budget_source='Public Law' AND granularity='program_level'
| All mandatory programs	                  | funding_type='Mandatory' AND granularity='program_level'
| FY2026 PB proposed AHA transfers	        | sub_agency='AHA' AND budget_source IN ('Congressional Justification','Budget in Brief')
| Aggregate totals across all sources	      | granularity='aggregate' AND funding_type='Total' AND is non_add='No'

\*FY2026 and FY2027 President's Budget contains some CDC programs in AHA
and OS.

<br>

## 5. Aggregate Structure

This section illustrates how the dataset's hierarchy is structured and
what is included at each level. Understanding this is essential for
avoiding double-counting when building pivot tables or summary analyses.

### 5.1 Hierarchy Overview Table

 | **Level**        | **granularity value** | **Includes**       |  **Key Notes**              |
|-------------------|-----------------------|--------------------|-----------------------------|
| Aggregate	        | aggregate	| Sum of all program-level Totals for a sub-agency, source, and year | Excludes ATSDR, VFC, VFA, WTC, PHSSEF, CVI, User Fees. Includes EEOICPA for cross-source comparability. Separate aggregate rows for CDC, AHA, ATSDR, OS.|
| Program Level     |	program_level	| All programs including mandatory | Mandatory programs (EEOICPA) are included but typically not part of the discretionary budget total in PB documents. Filter funding_type = ‘Discretionary’ to exclude.|
| Sub-Program Level |	sub_program_level	| Program broken into sub-accounts	| Not all programs have sub-program detail. Availability varies by source. is_non_add = ‘No’ for standard sub-program rows.|
| Sub-Program 2     |	sub_program_2_level |	Further breakdown within sub-program	| Always Subcomponent (non-additive with parent). Present in CJ, committee reports, and OP for selected programs.|
| Sub-Program 3     |	sub_program_3_level | 	Deepest available detail	| Very rare. Non-additive with sub-program 2 parent. Present only for Injury (DV), Chronic Disease (Cancer), and Environmental Health.|

  <br>

### 5.2 What Is and Is Not in the CDC Aggregate Total

The figure below illustrates the composition of the CDC aggregate Total
row for a typical enacted source (e.g., JES):

```
CDC Aggregate Total
├─ Discretionary Programs (all program accounts)
  ├─ Immunization and Respiratory Diseases
  ├─ HIV/AIDS, Viral Hepatitis, STI and TB Prevention
  ├─ Emerging and Zoonotic Infectious Diseases
  ├─ … [all other program accounts] …
  └─ CDC-Wide Activities and Program Support
├─ PPHF (Prevention and Public Health Fund)
├─ PHS Evaluation (Section 241 — PHSS only)
├─ EEOICPA Mandatory ($50.763M or $55.358M depending on source)
└─ ──────────────────────── = **CDC Aggregate Total**

NOT included in CDC aggregate:
ATSDR (separate aggregate row)  ·  VFC  ·  VFA  ·  WTC Health Program  ·  PHSSEF  ·  CVI  ·  User Fees

```

> **Note: Mandatory programs and discretionary totals:** EEOICPA is
> included in CDC aggregate Total rows in this dataset for cross-source
> comparability. However, mandatory programs are typically not part of
> the discretionary budget total as presented in Presidential Budget
> documents. To get a discretionary-only total, filter funding_type =
> 'Discretionary' AND is_non_add = 'No' at program_level.

<br>

### 5.3 PPHF at the Program Level

At the program level, PPHF-funded amounts appear as a separate
funding_type = 'PPHF' row alongside the Discretionary row for the same
program. The program-level Total row already includes both. The
structure is:

  | **Row**             |  **funding_type**  | **amount_millions**  |  **is_non_add** |
  |---------------------|--------------------|----------------------|-----------------|
  |Chronic Disease Prevention and Health Promotion	| Discretionary	| $1,192.647M| 	No|
  |Chronic Disease Prevention and Health Promotion	|PPHF	|$241.267M |	No |
  |Chronic Disease Prevention and Health Promotion	|Total	|$1,433.914M |	No |

> Note: Do not sum the Discretionary, PPHF, and Total rows together. The
> Total already includes Discretionary + PPHF. Filter funding_type =
> 'Total' at program_level for non-overlapping program sums.
