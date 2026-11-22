# MAT 422 Final Project: Assessing the Value of Two-Hour Serum Insulin for Diabetes Classification

## Project question

This project examines whether adding the Pima dataset's two-hour serum insulin variable improves diabetes classification compared with otherwise identical models that do not use insulin.

The project is a dataset-label prediction study. It does not make causal claims about insulin biology and does not provide clinical testing or treatment recommendations.

## Main finding

Across the primary analyses, adding two-hour serum insulin did not produce a material or consistent improvement in out-of-sample performance when glucose was included as a predictor.

A secondary glucose-excluded sensitivity analysis found that insulin showed a modest improvement under possible-missing median preprocessing. This result is interpreted cautiously because it depends on the preprocessing approach and deliberately removes the dataset's strongest predictor.

## Methods

The project compares three candidate models:

- Logistic Regression
- Elastic-Net Logistic Regression
- Random Forest

The primary experiment compares feature sets with and without insulin under two preprocessing approaches:

- Raw-zero values: retains released values as recorded.
- Possible-missing median: treats selected zero values as possible missing values, then applies training-fold median imputation and missingness indicators.

Additional sensitivity analyses use KNN imputation and exclude glucose from all feature sets.

Model evaluation uses nested stratified cross-validation with five outer folds and three inner folds. ROC-AUC is the primary performance metric. Secondary metrics include PR-AUC, accuracy, balanced accuracy, sensitivity, specificity, Brier score, calibration curves, and held-out permutation importance.

## Repository structure

```text
data/
  diabetes.csv                 Unchanged project dataset
  README.md                    Data source and variable information

notebooks/
  01_data_audit_eda.ipynb      Data audit and exploratory analysis
  02_modeling_results.ipynb    Modeling, sensitivity analyses, and figures
  README.md                    Notebook information

results/
  figures/                     Saved project figures
  tables/                      Saved result tables

docs/
  decision_log.md              Modeling decisions and interpretation limits
  ai_usage_log.md              Codex-use and human-review record

requirements.txt               Python package versions used in Colab
```

## Reproducing the analysis

1. Open `notebooks/01_data_audit_eda.ipynb` in Google Colab and run every cell from top to bottom.
2. Open `notebooks/02_modeling_results.ipynb` in Google Colab and run every cell from top to bottom.
3. The modeling notebook loads the unchanged dataset from this repository.
4. Saved tables and figures are written to `results/tables/` and `results/figures/`.

For a non-Colab environment, install the documented packages with:

```bash
pip install -r requirements.txt
```

## Important interpretation limits

- A zero measurement was treated as a possible missing value only in designated sensitivity analyses; zero was not assumed to mean confirmed missing data.
- Model performance and feature-importance results describe this dataset and modeling design only.
- Feature importance is not a causal measure.
- The project results should not be used as clinical advice.

## AI-use transparency

Codex assisted with workflow planning, code organization, debugging, visualization design, and documentation. The code was run and reviewed in Google Colab, and the project results were checked before interpretation.

See [docs/ai_usage_log.md](docs/ai_usage_log.md) for the detailed AI-use and iteration record, and [docs/decision_log.md](docs/decision_log.md) for modeling decisions.
