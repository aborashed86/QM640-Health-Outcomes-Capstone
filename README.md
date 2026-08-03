# QM640-Health-Outcomes-Capstone

Panel-data and machine-learning analysis of life expectancy and premature NCD mortality in Saudi Arabia and 15 GCC/MENA comparator countries, 2000–2023 (QM640 Capstone, Walsh College — Mohamad AboRashd).

## Corrected dataset note

The `HealthExpPC` (health expenditure per capita) variable was corrected for four countries with previously missing/placeholder values. This expanded the usable panel from 12 to **16 countries** (N=233 for the LifeExpectancy models, N=222 for NCDMortality). All results in the interim report and in this repository reflect the corrected 16-country panel. RQ1's fixed-effects predictors (UHCIndex, OOPExpenditure), significant on the original 12-country draft, did **not** replicate on the corrected panel; RQ3's UHCIndex finding did replicate. This non-replication is discussed explicitly in the report as a methodological finding, not smoothed over.

## Repository structure

```
data/
  raw/          Original merged raw indicator workbook (World Bank / WHO sources, one sheet per indicator plus the merged Master_Panel_Data sheet before cleaning)
  processed/    Cleaned, analysis-ready dataset (Master_Capstone_Dataset_V4_Final_Clean.csv) and the annotated preprocessing workbook (data dictionary, missingness recap, coverage report, correlation matrix)
Notebooks/
  QM640_Capstone_V4_Final_Full_Analysis.ipynb   End-to-end analysis notebook: cleaning audit, EDA, RQ1-RQ4 fixed-effects models, grouped cross-validated ML models, hyperparameter tuning, final evaluation
Outcomes/
  tables/        All exported result tables (CSV/JSON) referenced in the interim report and notebook
  figures/       All exported figures (PNG) referenced in the interim report and notebook
  deployment/    Final tuned model artifacts (joblib) and deployment metadata for LifeExpectancy and NCDMortality
  QM640_V4_Full_Analysis_Outputs.xlsx   Consolidated workbook of all tables above, one sheet each
requirements.txt
README.md
```

## Reproducing the analysis

1. Clone the repository and install dependencies:
   ```
   pip install -r requirements.txt
   ```
2. Open `Notebooks/QM640_Capstone_V4_Final_Full_Analysis.ipynb` in Jupyter (or Colab — update the `DATA_FILE` path in the setup cell to point at `data/processed/Master_Capstone_Dataset_V4_Final_Clean.csv`).
3. Run all cells top to bottom. The notebook regenerates every table and figure into a local `qm640_v4_outputs/` folder, matching the contents of `Outcomes/`.

## Research questions

- **RQ1**: Which country-level predictors are associated with, and predict, life expectancy?
- **RQ2**: How does Saudi Arabia's life-expectancy trajectory compare to GCC/MENA peers?
- **RQ3**: Which country-level predictors are associated with, and predict, premature NCD mortality?
- **RQ4**: Does universal health coverage (UHC) moderate the relationship between health expenditure and outcomes?

Full methodology, results, and limitations are documented in the interim report (`QM640_Interim_Report_Mohamad_AboRashd.docx`, submitted separately for the course).

## Data dictionary

See the `Data_Dictionary` sheet in `data/processed/Master_Capstone_Dataset_V4_Preprocessed_UPDATED.xlsx` for variable names, units, and sources for all 22 variables in the panel.

## Status

Interim submission. Outstanding next steps (wild-cluster bootstrap standard-error correction, hypertension-prevalence data sourcing, mentor-feedback incorporation) are tracked in the interim report's "Next Steps" section and will be closed out for the final submission.
