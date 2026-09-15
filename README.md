QM640 Health Outcomes Capstone
Health-System Conversion Efficiency and Healthy Life Expectancy
A Global Panel Analysis of 185 Countries Using Explainable Analytics
and Machine Learning with Application to Saudi Arabia
Author: Mohamad AboRashd  
Institution: Walsh College  
Course: QM640 -- Data Analytics Capstone  
Term: Summer 2026
Project Overview
This capstone develops an integrated explanatory, predictive, and
benchmarking framework to examine how countries convert economic
resources, demographic conditions, service reach, and health-system
capacity into healthy life expectancy (HALE) and premature
non-communicable disease (NCD) mortality outcomes.
The master longitudinal panel contains 217 countries/economies, 121
variables, and data from 2000--2023. The primary analytical frame
contains 185 countries from 2000--2021 (4,070 country-year
observations).
The project separates explanatory analysis, unseen-country prediction,
and decision-support benchmarking. The analysis is observational;
associations, predictive importance, and benchmark residuals are not
interpreted as causal policy effects.
Research Questions
RQ1 -- Resources, Demography, and Conversion Benchmark: How much
cross-country variation in HALE is associated with resources and
demography, how much remains as a benchmark residual, and does that
residual persist?
RQ2 -- Service Reach and Capacity: Among institutionally actionable
variables, are service-reach measures more strongly associated with
outcomes than capacity measures, and do the two blocks interact?
RQ3 -- Unseen-Country Prediction: Can HALE and premature NCD
mortality be predicted for countries not seen during training, do
actionable variables add predictive information beyond contextual
variables, and which variables contribute most to prediction?
RQ4 -- Spending and the Morbidity Gap: Is health spending associated
differently with healthy longevity than with total longevity, thereby
altering the morbidity gap?
Analytical Workflow
Data acquisition and harmonization
Data-quality and missingness assessment
Feature engineering and analytical-frame construction
Explanatory modeling: resource-demography benchmark, two-way fixed
effects, Mundlak decomposition, clustered inference, wild cluster
bootstrap, and BH-FDR correction
Predictive modeling: country-grouped CV, fold-specific
preprocessing, model comparison/tuning, repeated validation, locked
holdout diagnostics, ablation, and permutation importance
Evidence-based benchmarking and Saudi Arabia application
Key Results
RQ1
The resource-demography benchmark explains 77.1% of cross-country
HALE variation. The residual standard deviation is 2.89 years and
residual performance is highly persistent (r = .885). DPT
immunization is the most consistent observable correlate, although the
evidence is only partially robust after FDR correction.
RQ2
The service-reach block is jointly significant in its maximal sample
(F = 19.17, p < .001), while the capacity block is not (F = 1.95,
p = .124). The common-sample comparison is inconclusive. The UHC ×
Physicians interaction is negative (b = -0.0268, p = .0031),
consistent with diminishing or overlapping association rather than a
causal substitution effect.
RQ3
Extra Trees is selected for both outcomes under country-grouped
validation.
HALE grouped-CV R² ≈ .810
NCD mortality grouped-CV R² ≈ .600
Repeated grouped-CV HALE R² = .806 ± .064
Repeated grouped-CV NCD R² = .609 ± .070
21-feature sensitivity model: HALE ≈ .808, NCD ≈ .633
RQ4
The spending--morbidity-gap result is specification-dependent. The
adjusted cross-country association is positive (b = .8594, p =
.0318), while the two-way fixed-effects within-country estimate is not
significant (b = .0908, p = .6678).
Saudi Arabia
Saudi Arabia records observed HALE of 65.84 years compared with a
benchmark prediction of 65.03 years, producing a +0.81-year
residual, approximately the 64th percentile of the global residual
distribution.
Validation and Analytical Guardrails
Whole countries remain together during cross-validation.
Predictor imputation occurs only inside training/CV folds.
Outcomes are never imputed.
Primary RQ3 predictors require ≥70% observed data (≤30%
missingness).
Country-clustered inference and wild-cluster bootstrap checks are
used.
BH-FDR correction is applied to multiple candidate tests.
Predictive importance is not treated as causal effect size.
The benchmark residual is not labeled pure efficiency.
Suggested Repository Structure
``` text
QM640-Health-Outcomes-Capstone/
├── README.md
├── requirements.txt
├── QM640_Capstone_Final.ipynb
├── data/
│   ├── QM640_Master_Panel_v6.xlsx
│   └── QM640_Data_Dictionary_v6.xlsx
├── Outcome/
│   ├── figures/
│   ├── tables/
│   └── QM640_Final_Analysis_Outputs.xlsx
├── report/
│   └── QM640_Final_Report.pdf
└── presentation/
    └── QM640_Final_Presentation.pdf
```
The executed final notebook is the authoritative analytical record.
Reproducibility
Install dependencies:
``` bash
pip install -r requirements.txt
```
Then run the final Jupyter notebook from top to bottom. Fixed random
seeds are used where applicable and country-grouped validation prevents
leakage across countries.
Main Technologies
Python, pandas, NumPy, SciPy, statsmodels, scikit-learn, XGBoost,
Matplotlib, openpyxl, and Jupyter.
Data Sources
The harmonized panel draws primarily on internationally comparable
indicators from the World Health Organization Global Health Observatory,
World Bank World Development Indicators, and related international
demographic and development sources. See the final report and notebook
bibliography for complete references.
Interpretation
This project is intended for benchmarking, prediction, prioritization,
and decision support. It does not claim that changing a variable
identified by regression or machine-learning importance will causally
produce a specific change in HALE or NCD mortality.
Author
Mohamad AboRashd  
Walsh College -- QM640 Data Analytics Capstone  
September 2026
