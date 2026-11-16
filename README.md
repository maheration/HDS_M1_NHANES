# NHANES Albuminuria Study — Cambridge MSt Module 1

## Project overview

This project forms part of the University of Cambridge MSt in Healthcare Data Science, Module 1.

It constructs a documented, validated and reproducible analysis-ready dataset (ARD) for investigating clinical and metabolic characteristics associated with elevated albuminuria, and applies it in an illustrative survey-weighted analysis.

## Research question

Among U.S. adults aged ≥20 years with at least one metabolic risk factor (diabetes, hypertension or obesity) and preserved eGFR (≥60 mL/min/1.73 m²), which clinical and metabolic characteristics are associated with elevated albuminuria (urine ACR ≥30 mg/g)?

## Dataset

**Source:** National Health and Nutrition Examination Survey (NHANES), August 2021–August 2023.

**Provider:** US Centers for Disease Control and Prevention (CDC), National Center for Health Statistics (NCHS).

**Website:** https://wwwn.cdc.gov/nchs/nhanes/

Nine public-use component files are linked by participant identifier (SEQN): DEMO_L, ALB_CR_L, BIOPRO_L, GHB_L, BMX_L, BPXO_L, DIQ_L, BPQ_L and SMQ_L.

## Study design

Cross-sectional observational association study.

### Eligibility criteria

- Adults aged ≥20 years.
- Not pregnant at examination (participants with RIDEXPRG = 1 excluded).
- Valid urine ACR and serum creatinine measurements.
- eGFR ≥60 mL/min/1.73 m² using the 2021 race-free CKD-EPI creatinine equation.
- At least one of diabetes, hypertension or obesity.

### Study-defined phenotypes

- **Diabetes:** Self-reported diagnosis, HbA1c ≥6.5%, or current diabetes medication.
- **Hypertension:** Self-reported diagnosis, average measured systolic BP ≥130 mmHg, average measured diastolic BP ≥80 mmHg, or current antihypertensive medication.
- **Obesity:** BMI ≥30 kg/m².
- **Elevated albuminuria:** Urine ACR ≥30 mg/g.

Full implementation rules, including indeterminate categories, are documented in the report and the codebook.

## Analysis-ready dataset

- **File:** `data/processed/nhanes_albuminuria_ard.rds`
- **Size:** 3,370 participants × 33 variables; 417 with elevated albuminuria.
- **Documentation:** `metadata/codebook_metadata.md` (variable definitions, source files, derivation rules, missingness and the CKD-EPI 2021 equation).

The eligible-only ARD must be used with the supplied workflow, which reconstructs the broader phlebotomy-weighted survey design before selecting the eligible subpopulation.

## Analysis

Survey-weighted descriptive analysis and multivariable logistic regression (`survey::svyglm()`, quasibinomial family) using phlebotomy weights (WTPH2YR), strata (SDMVSTRA) and PSUs (SDMVPSU).

## Files

- `HDS_M1_NHANES.Rproj` — RStudio project (open this first)
- `renv.lock`, `.Rprofile`, `renv/` — Package versions and environment (renv)
- `HDS_M1_MaherAldemerdash_2611.Rmd` — Complete workflow: package installation, data import, ARD construction, validation, analysis and report
- `HDS_M1_MaherAldemerdash_2611.html` — Knitted report
- `references.bib`, `vancouver.csl` — References and citation style
- `styles.css` — Report styling
- `data/raw/` — The nine NHANES source files (`.XPT`)
- `data/processed/nhanes_albuminuria_ard.rds` — Analysis-ready dataset
- `metadata/codebook_metadata.md` — Codebook

## Reproducing the report

Requirements: R (version 4.6.1 was used) and RStudio, with an internet connection.

1. Extract the submitted ZIP file, or download the GitHub repository (**Code → Download ZIP**) and extract it. Keep the folder structure intact.
2. Open `HDS_M1_NHANES.Rproj` in RStudio (not the .Rmd). The project uses **renv**, which installs itself automatically on first opening.
3. In the Console, run `renv::restore()` and answer `Y`. This installs the exact package versions recorded in `renv.lock`.
4. Open `HDS_M1_MaherAldemerdash_2611.Rmd` and click **Knit**.

The source data are read from `data/raw/`; any missing file is downloaded from the CDC website. Knitting rebuilds the ARD, saves it to `data/processed/nhanes_albuminuria_ard.rds`, runs all validation checks and produces the HTML report. Knitting stops with an error if any validation check fails.

## Data provenance and use

NHANES data are publicly released by CDC/NCHS and were collected under NCHS Ethics Review Board approval. This project uses public-use, de-identified files only; no linkage to identifiable information was attempted.
