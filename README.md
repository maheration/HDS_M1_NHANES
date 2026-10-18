# COVID-19 and Multiple Sclerosis — Cambridge MSt Module 1

## Project overview

This project forms part of the University of Cambridge MSt in Healthcare Data Science, Module 1.

The objective is to develop a documented, validated, and reproducible analysis-ready dataset (ARD) suitable for a predefined research question and analytical method.

## Research question

Among patients with multiple sclerosis currently receiving disease-modifying therapies (DMTs), is anti-CD20 therapy (ocrelizumab or rituximab) associated with recorded confirmed or suspected COVID-19 diagnosis compared with other current DMTs?

## Dataset

**Source:** COVID-19 in Multiple Sclerosis Global Data Sharing Initiative (GDSI).

**Dataset version:** 1.0.0

**Source URL:** https://physionet.org/content/patient-level-data-covid-ms/1.0.0/

**Original file:** `GDSI_OpenDataset_Final.csv`

**Dataset dimensions:** 1,141 records and 47 variables.

**Licence:** Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0). Attribution and applicable redistribution requirements must be maintained.

## Planned analytical method

Binary logistic regression.

The primary deliverable is the analysis-ready dataset, not a definitive clinical inference about treatment effects.

## Project structure

- `data/raw/` — Original source dataset
- `data/processed/` — Derived analysis-ready dataset
- `metadata/` — Data dictionary, phenotype definitions and provenance
- `outputs/figures/` — Generated figures
- `outputs/tables/` — Generated tables
- `submission/` — Assignment submission materials
- `analysis.Rmd` — Main reproducible R Markdown workflow (planned)
- `renv.lock` — R package dependency versions

## Reproducibility

The project uses R, RStudio, Git and `renv`.

Once the analysis workflow is completed:

1. Clone the repository.
2. Open `HDS_M1_COVID_MS.Rproj` in RStudio.
3. Run `renv::restore()` to install the recorded package versions.
4. Verify that the original dataset is available in `data/raw/`.
5. Knit `analysis.Rmd` to reproduce the documented data preparation, validation and analytical outputs.

These instructions will be tested and updated before submission.

## Project status

Stage 00 — Project setup and reproducibility infrastructure in progress.

## Licence and attribution

The original GDSI dataset is attributed to its respective creators and distributed through PhysioNet under CC BY-SA 4.0.

The original dataset licence does not automatically determine the licence of independently authored code. Licensing and redistribution documentation will be finalised before release or submission.
EOF