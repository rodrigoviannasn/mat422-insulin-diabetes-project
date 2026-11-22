# Decision Log

This file will record important project decisions, such as preprocessing choices, model settings, and changes made after testing.
## Modeling-Stage Decisions and Findings

### Evaluation design

- The primary analysis compared models with and without two-hour serum insulin.
- The three planned model families were Logistic Regression, Elastic-Net Logistic Regression, and Random Forest.
- Each model was evaluated using five outer stratified folds and three inner stratified folds for hyperparameter selection.
- ROC-AUC was the primary metric. PR-AUC, accuracy, balanced accuracy, sensitivity, specificity, Brier score, calibration curves, and fit time were secondary measures.
- The same outer folds were used for each with-insulin versus without-insulin comparison.

### Preprocessing decisions

- The raw-zero approach retained the released values as recorded.
- A second approach treated zero values in glucose, blood pressure, skin thickness, insulin, and BMI as possible missing values, then used median imputation and missingness indicators within each training fold.
- Zero values were not assumed to be confirmed missing values.
- A KNN-imputation sensitivity analysis was also performed with Logistic Regression to test whether the main conclusion depended on the imputation method.

### Primary findings

- Across the primary analyses, adding two-hour serum insulin did not produce a material or consistent improvement in out-of-sample performance when glucose was included.
- The paired ROC-AUC differences between models with and without insulin were close to zero across the three model families and both primary preprocessing approaches.
- The KNN-imputation sensitivity analysis reached the same overall conclusion.
- Random Forest required substantially more fitting time than the logistic models but did not provide a clear performance advantage.

### Additional sensitivity analysis

- Because glucose was the strongest predictor, a secondary Logistic Regression analysis excluded glucose from every feature set.
- Model performance declined after excluding glucose, confirming its importance to prediction in this dataset.
- Under possible-missing median preprocessing, insulin showed a modest improvement when glucose was excluded, including a mean paired ROC-AUC difference of 0.016.
- This glucose-excluded result is treated as a secondary, preprocessing-dependent finding. It does not override the primary conclusion.

### Feature influence and interpretation limits

- Held-out permutation importance showed that glucose was the dominant predictor, followed by BMI.
- Insulin had small permutation importance in the primary median-preprocessed models compared with glucose and BMI.
- Importance and ablation results describe predictive contribution within this dataset and model design only. They do not establish causation, clinical utility, or a recommendation about diabetes testing or treatment.
- The originally planned models and sensitivity analyses were retained rather than changing the methods after observing the primary near-zero insulin result.
