# Notebook Guide

Run the notebooks in the following order.

## 1. `01_data_audit_eda.ipynb`

This notebook documents the dataset before modeling.

It:

- Loads the unchanged Pima diabetes dataset.
- Checks dimensions, duplicate records, and explicit missing values.
- Counts zero values in measurement variables.
- Examines outcome balance, distributions, correlations, and insulin patterns.
- Saves exploratory tables to `results/tables/`.
- Saves exploratory figures to `results/figures/`.

## 2. `02_modeling_results.ipynb`

This notebook runs the main project experiments.

It:

- Defines preprocessing pipelines and candidate models.
- Compares models with and without two-hour serum insulin.
- Uses nested stratified cross-validation for hyperparameter selection and evaluation.
- Runs raw-zero, possible-missing median, KNN-imputation, and glucose-excluded sensitivity analyses.
- Produces model-comparison tables, paired insulin-ablation tables, calibration results, feature-importance results, and final figures.
- Saves all modeling artifacts to `results/tables/` and `results/figures/`.

## Execution notes

- Run each notebook from top to bottom in Google Colab.
- Use `01_data_audit_eda.ipynb` before `02_modeling_results.ipynb`.
- The notebooks use fixed random seeds where applicable.
- The saved CSV tables and PNG figures are the evidence used in the final paper.
- Results should be interpreted as dataset-level predictive findings, not causal or clinical conclusions.
