
# NHANES Albuminuria Study — Cambridge MSt Module 1

## Project overview

This project forms part of the University of Cambridge MSt in Healthcare Data Science, Module 1.

The objective is to construct a documented, validated and reproducible analysis-ready dataset (ARD) for investigating clinical and metabolic characteristics associated with elevated albuminuria.

## Research question

Among adults with metabolic risk factors and preserved eGFR (≥60 mL/min/1.73 m²), which clinical and metabolic characteristics are associated with elevated albuminuria (urine ACR ≥30 mg/g)?

## Dataset

**Source:** National Health and Nutrition Examination Survey (NHANES), August 2021–August 2023.

**Provider:** US Centers for Disease Control and Prevention (CDC), National Center for Health Statistics (NCHS).

**Website:** https://wwwn.cdc.gov/nchs/nhanes/

The analysis uses publicly available participant-level data from multiple NHANES components, linked using participant identifiers.

## Study design

Cross-sectional observational association study.

### Eligibility criteria

- Adults aged ≥20 years.
- Valid urine ACR and serum creatinine measurements.
- eGFR ≥60 mL/min/1.73 m² using the 2021 race-free CKD-EPI creatinine equation.
- At least one of diabetes, hypertension or obesity.

### Study-defined phenotypes

- **Diabetes:** Self-reported diagnosis, HbA1c ≥6.5%, or current diabetes medication.
- **Hypertension:** Self-reported diagnosis, average measured systolic BP ≥130 mmHg, average measured diastolic BP ≥80 mmHg, or current antihypertensive medication.
- **Obesity:** BMI ≥30 kg/m².
- **Elevated albuminuria:** Urine ACR ≥30 mg/g.

Phenotype implementation rules and validation will be documented in the analysis workflow and metadata.

## Planned analysis

Survey-weighted descriptive analysis and multivariable logistic regression, accounting for the NHANES complex survey design.

The primary deliverable is the validated analysis-ready dataset.

## Project structure

- `data/raw/` — Original NHANES source files
- `data/processed/` — Derived analysis-ready dataset
- `metadata/` — Data dictionary, phenotype definitions and provenance
- `outputs/figures/` — Generated figures
- `outputs/tables/` — Generated tables
- `submission/` — Assignment submission materials
- `analysis.Rmd` — Main reproducible R Markdown workflow (planned)
- `renv.lock` — R package dependency versions

## Reproducibility

The project uses R, RStudio, Git and `renv`.

Once the workflow is completed:

1. Clone the repository.
2. Open `HDS_M1_NHANES.Rproj` in RStudio.
3. Run `renv::restore()` to install the recorded package versions.
4. Obtain the required NHANES source files in `data/raw/`.
5. Knit `analysis.Rmd` to reproduce data preparation, validation and analytical outputs.

These instructions will be tested and updated before submission.

## Project status

- Stage 00 — Project setup completed.
- Stage 01 — Dataset selection and feasibility completed.
- Stage 02 — Literature review and study design pending.

## Data provenance

NHANES data are publicly released by CDC/NCHS. The final report and metadata will document source files, variable definitions, download information and applicable data-use guidance.
