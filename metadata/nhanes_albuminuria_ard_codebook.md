# Variable Dictionary and Codebook

**Analysis-ready dataset:** `nhanes_albuminuria_ard.rds`  
**Version:** 1.0 (29 October 2026)  
**Rows × columns:** 3,370 × 33  

## Dataset description

This analysis-ready dataset contains one row per participant from the National Health and Nutrition Examination Survey (NHANES), August 2021–August 2023 public-use files.  

It was constructed from the following NHANES component files:  
DEMO_L, ALB_CR_L, BIOPRO_L, GHB_L, BMX_L, BPXO_L, DIQ_L, BPQ_L and SMQ_L.  

**Population:** Adults aged ≥ 20 years with a valid urine albumin-to-creatinine ratio and serum creatinine measurement, estimated glomerular filtration rate (eGFR) ≥ 60 mL/min/1.73 m² (CKD-EPI 2021 creatinine equation), at least one metabolic risk factor (diabetes, hypertension or obesity), and not identified as pregnant.  

**Primary outcome:** Elevated albuminuria, defined as urine albumin-to-creatinine ratio (URDACT) ≥ 30 mg/g.  
**Events:** 417  

**Pregnancy exclusion:** Participants with RIDEXPRG = 1 were excluded. RIDEXPRG (pregnancy status at examination) is released only for females aged 20–44 years (1 = pregnant, 2 = not pregnant, 3 = cannot ascertain). All other participants were retained.  

## Variable dictionary

| Variable | Type | Study role | Source / Derivation | Definition / Coding | Units | NA count (%) |
|----------|------|------------|---------------------|---------------------|-------|--------------|
| SEQN | numeric | Identifier | DEMO_L | Unique participant sequence number | — | 0 (0%) |
| RIDAGEYR | numeric | Predictor | DEMO_L | Age at screening; top-coded at 80 in public-use file | years | 0 (0%) |
| RIAGENDR | numeric | Predictor | DEMO_L | Sex (1 = Male, 2 = Female) | — | 0 (0%) |
| RIDRETH3 | numeric | Predictor | DEMO_L | Race/ethnicity (1 = Mexican American, 2 = Other Hispanic, 3 = Non-Hispanic White, 4 = Non-Hispanic Black, 6 = Non-Hispanic Asian, 7 = Other/Multi) | — | 0 (0%) |
| URDACT | numeric | Outcome input | ALB_CR_L | Urine albumin/creatinine ratio | mg/g | 0 (0%) |
| elevated_acr | logical | Outcome | Derived | TRUE if URDACT ≥ 30; FALSE otherwise | — | 0 (0%) |
| LBXSCR | numeric | Eligibility | BIOPRO_L | Serum creatinine | mg/dL | 0 (0%) |
| egfr | numeric | Eligibility | Derived (CKD-EPI 2021) | Estimated GFR (race-free). See notes. | mL/min/1.73 m² | 0 (0%); all ≥ 60 |
| LBXGH | numeric | Predictor | GHB_L | Glycohemoglobin (HbA1c) | % | 0 (0%) |
| BPXOSY1 | numeric | Phenotype input | BPXO_L | Systolic BP, 1st reading | mmHg | 73 (2.2%) |
| BPXOSY2 | numeric | Phenotype input | BPXO_L | Systolic BP, 2nd reading | mmHg | 76 (2.3%) |
| BPXOSY3 | numeric | Phenotype input | BPXO_L | Systolic BP, 3rd reading | mmHg | 85 (2.5%) |
| BPXODI1 | numeric | Phenotype input | BPXO_L | Diastolic BP, 1st reading | mmHg | 73 (2.2%) |
| BPXODI2 | numeric | Phenotype input | BPXO_L | Diastolic BP, 2nd reading | mmHg | 76 (2.3%) |
| BPXODI3 | numeric | Phenotype input | BPXO_L | Diastolic BP, 3rd reading | mmHg | 85 (2.5%) |
| mean_sbp | numeric | Predictor | Derived | Mean of available systolic readings (BPXOSY1–3). NA if none available. | mmHg | 73 (2.2%) |
| mean_dbp | numeric | Predictor | Derived | Mean of available diastolic readings (BPXODI1–3). NA if none available. | mmHg | 73 (2.2%) |
| BMXBMI | numeric | Predictor | BMX_L | Body mass index | kg/m² | 23 (0.7%) |
| DIQ010 | numeric | Phenotype input | DIQ_L | Doctor ever told diabetes (1 = Yes, 2 = No, 3 = Borderline) | — | 0 (0%) |
| DIQ050 | numeric | Phenotype input | DIQ_L | Now taking insulin (1 = Yes, 2 = No) | — | 2,778 (82.4%) |
| DIQ070 | numeric | Phenotype input | DIQ_L | Now taking diabetic pills (1 = Yes, 2 = No) | — | 2,149 (63.8%) |
| BPQ020 | numeric | Phenotype input | BPQ_L | Ever told high blood pressure (1 = Yes, 2 = No) | — | 0 (0%) |
| BPQ150 | numeric | Phenotype input | BPQ_L | Now taking prescribed medicine for high BP (1 = Yes, 2 = No) | — | 1,700 (50.4%) |
| SMQ020 | numeric | Phenotype input | SMQ_L | Smoked ≥ 100 cigarettes in life (1 = Yes, 2 = No) | — | 0 (0%) |
| SMQ040 | numeric | Phenotype input | SMQ_L | Now smoke cigarettes (1 = Every day, 2 = Some days, 3 = Not at all) | — | 1,885 (55.9%) |
| smoking_status | factor | Predictor | Derived | Never / Former / Current. See notes. | — | 6 (0.2%) |
| diabetes | numeric | Phenotype | Derived | 1 = present, 0 = absent. See notes. | — | 0 (0%) |
| hypertension | numeric | Phenotype | Derived | 1 = present, 0 = absent, NA = indeterminate. See notes. | — | 30 (0.9%) |
| obesity | numeric | Phenotype | Derived | 1 = present (BMI ≥ 30), 0 = absent, NA = indeterminate. See notes. | — | 23 (0.7%) |
| metabolic_risk | numeric | Eligibility | Derived | 1 = ≥ 1 of diabetes, hypertension or obesity present. See notes. | — | 0 (0%); all = 1 |
| WTPH2YR | numeric | Survey design | BIOPRO_L | Phlebotomy two-year sample weight | — | 0 (0%) |
| SDMVSTRA | numeric | Survey design | DEMO_L | Masked variance pseudo-stratum | — | 0 (0%) |
| SDMVPSU | numeric | Survey design | DEMO_L | Masked variance pseudo-PSU | — | 0 (0%) |

## Accompanying notes

### Special response codes
The following non-response codes are retained in the source columns and are **not** counted as NA:  
- 7 = refused  
- 9 = don’t know  

Observed in this dataset:  
- DIQ070 (diabetic pills): 2 responses coded 9  
- BPQ020 (told high blood pressure): 2 responses coded 9  
- BPQ150 (taking BP medication): 2 responses coded 9  
- SMQ020 (smoked ≥ 100 cigarettes): 3 responses coded 7 and 3 coded 9  

### eGFR — CKD-EPI 2021 creatinine equation (race-free)
Calculated from serum creatinine (LBXSCR, mg/dL), age (RIDAGEYR) and sex (RIAGENDR) for adults with non-missing values:

\[
\text{eGFR} = 142 \times \min(\text{Scr}/\kappa, 1)^{\alpha} \times \max(\text{Scr}/\kappa, 1)^{-1.200} \times 0.9938^{\text{Age}} \times 1.012^{\text{[female]}}
\]

where \(\kappa = 0.7\) (female) or \(0.9\) (male), and \(\alpha = -0.241\) (female) or \(-0.302\) (male).

### Blood pressure
- `mean_sbp` is the mean of all available systolic readings (BPXOSY1, BPXOSY2, BPXOSY3).  
- `mean_dbp` is the mean of all available diastolic readings (BPXODI1, BPXODI2, BPXODI3).  
- The mean is set to NA if no readings are available for that component.  
- Elevated measured blood pressure is defined as mean_sbp ≥ 130 mmHg **or** mean_dbp ≥ 80 mmHg.

### Diabetes phenotype
Positive criteria take precedence.  

- **1 (present)** if DIQ010 = 1 **or** LBXGH ≥ 6.5 **or** DIQ050 = 1 **or** DIQ070 = 1.  
- **0 (absent)** if:  
  - DIQ010 = 2 and LBXGH is non-missing and < 6.5, **or**  
  - DIQ010 = 3 and LBXGH is non-missing and < 6.5 and the participant is not on insulin or diabetes pills.  

Structural missingness on medication items (questions not asked because of survey routing) is treated as non-informative.  
Among eligible participants: 770 present, 2,600 absent; no indeterminate values.

### Hypertension phenotype
- **1 (present)** if BPQ020 = 1 **or** BPQ150 = 1 **or** mean_sbp ≥ 130 **or** mean_dbp ≥ 80.  
- **0 (absent)** only if BPQ020 = 2 **and** both mean systolic and mean diastolic blood pressure are non-missing and below the thresholds.  
- **NA (indeterminate)** otherwise.  

Structural missingness on BPQ150 is treated as non-informative.

### Obesity phenotype
- **1** if BMXBMI ≥ 30.  
- **0** if BMXBMI is non-missing and < 30.  
- **NA** if BMXBMI is missing.

### Metabolic risk
A participant is classified as having metabolic risk if at least one of the diabetes, hypertension or obesity phenotypes is present. The indicator is negative only when all three phenotypes are negative, and indeterminate otherwise.  
All participants retained in this analysis-ready dataset meet the metabolic-risk eligibility criterion (metabolic_risk = 1).

### Smoking status
- Never: SMQ020 = 2  
- Former: SMQ020 = 1 and SMQ040 = 3  
- Current: SMQ020 = 1 and SMQ040 ∈ {1, 2}  
- NA if the required responses are missing or inconsistent.

### Analysis-use note
The primary analysis covariates are age, sex, race/ethnicity, HbA1c, mean systolic blood pressure, BMI and smoking status.  
Of the 3,370 eligible participants, 3,270 have complete data on these covariates and 100 have incomplete data. All 3,370 participants are retained in the analysis-ready dataset.
