# Final Paper Evidence Map

This document maps the final paper sections to completed code, tables, figures, and references.

## Planned paper structure

| Final paper section | Main purpose | Evidence to use | Approximate length |
|---|---|---|---|
| 1. Introduction | State the diabetes-classification question, insulin-ablation objective, scope, and importance of careful evaluation. | Dataset overview, research question, outcome balance, scope statement. | 2–3 pages |
| 2. Related Work | Review the historical Pima source, diabetes-classification studies, preprocessing studies, and method references. | `docs/reference_notes.md` | 3–4 pages |
| 3. Proposed Methodology | Explain data, predictors, preprocessing, models, nested cross-validation, metrics, and interpretation limits. | `notebooks/01_data_audit_eda.ipynb`, `notebooks/02_modeling_results.ipynb`, `docs/decision_log.md` | 4–5 pages |
| 4. Experiment Setups and Result Discussion | Present exploratory findings, primary model results, calibration, permutation importance, and sensitivity analyses. | Saved tables and figures in `results/` | 6–7 pages |
| 5. Comparison | Compare the three model families, preprocessing approaches, insulin ablations, and carefully compare the project design with related studies. | `primary_model_comparison_summary.csv`, `primary_insulin_ablation_summary.csv`, Rajendra and Latifi (2021) | 2–3 pages |
| 6. Conclusion | Directly answer the research question, state limitations, and suggest future work. | All completed evidence | 1–2 pages |
| 7. Acknowledgments | Thank the instructor, course resources, and tools as appropriate. | Final author review | Short section |
| 8. Author Contributions | State that this is an individual project and describe the student's work. | Final author review | Short section |
| 9. Data Availability | State where the unchanged data, code, results, and notebooks are available. | GitHub repository | Short section |
| 10. References | Include only sources actually cited in the paper. | `docs/reference_notes.md` | 1–2 pages |

## Results evidence map

### Exploratory analysis

- `results/tables/data_quality_summary.csv`
- `results/tables/possible_missing_zero_summary.csv`
- `results/tables/outcome_balance_summary.csv`
- `results/tables/outcome_correlations.csv`
- `results/tables/median_by_outcome.csv`
- `results/figures/outcome_balance.png`
- `results/figures/zero_value_counts.png`
- `results/figures/correlation_heatmap.png`
- `results/figures/insulin_patterns_by_outcome.png`
- `results/figures/key_predictor_distributions.png`

Use these results to explain the dataset, outcome balance, possible zero-value issues, and why insulin requires careful interpretation.

### Primary model comparison

- `results/tables/primary_model_comparison_summary.csv`
- `results/tables/primary_insulin_ablation_summary.csv`
- `results/figures/primary_roc_auc_ablation.png`
- `results/figures/primary_roc_auc_comparison.png`
- `results/figures/primary_roc_curves.png`
- `results/figures/primary_precision_recall_curves.png`
- `results/figures/primary_calibration_curves.png`

Use these results to support the primary conclusion: adding two-hour serum insulin did not produce a material or consistent improvement when glucose was included.

### Sensitivity analyses

- `results/tables/knn_logistic_sensitivity_summary.csv`
- `results/tables/knn_logistic_insulin_ablation_summary.csv`
- `results/tables/glucose_excluded_logistic_summary.csv`
- `results/tables/glucose_excluded_insulin_ablation_summary.csv`
- `results/figures/glucose_excluded_sensitivity.png`

Use these results to show that the primary conclusion was stable under KNN imputation, while insulin showed a modest secondary benefit under possible-missing median preprocessing after glucose was excluded.

### Feature influence

- `results/tables/held_out_permutation_importance_summary.csv`
- `results/figures/held_out_permutation_importance.png`

Use these results to explain that glucose was the dominant predictor, BMI was the next strongest predictor, and insulin had small incremental held-out importance in the primary models.

## Core interpretation statement

The primary conclusion should remain narrow:

> In this Pima dataset and evaluation design, adding two-hour serum insulin did not provide a material or consistent out-of-sample classification improvement when glucose and the other available predictors were included. A modest insulin benefit appeared only in a secondary glucose-excluded, possible-missing median-preprocessing analysis.

Do not make causal, diagnostic, treatment, or clinical-testing recommendations.
