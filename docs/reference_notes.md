# Verified Reference Notes

These notes list sources reviewed for the final paper. They are planning notes, not yet the final formatted References section.

## Dataset lineage and project context

1. Smith, J. W., Everhart, J. E., Dickson, W. C., Knowler, W. C., & Johannes, R. S. (1988). *Using the ADAP learning algorithm to forecast the onset of diabetes mellitus*. Proceedings of the Annual Symposium on Computer Application in Medical Care, 261–265.  
   Link: https://pmc.ncbi.nlm.nih.gov/articles/PMC2245318/  
   Use: Historical source for the Pima dataset lineage and the term “two-hour serum insulin.”  
   Caution: The historical source describes a five-year forecasting task. In this project, `Outcome` should be called the recorded binary dataset outcome rather than a general present-time clinical diagnosis.

2. Rajendra, P., & Latifi, S. (2021). *Prediction of diabetes using logistic regression and ensemble techniques*. Computer Methods and Programs in Biomedicine Update, 1, 100032.  
   Link: https://doi.org/10.1016/j.cmpbup.2021.100032  
   Use: Professor-provided example paper using logistic regression, feature selection, ensemble methods, and Pima data.  
   Caution: Its train/test design and metrics differ from this project’s nested cross-validation design, so numerical accuracy results should not be compared directly.

## Related work on diabetes classification

3. Sisodia, D., & Sisodia, D. S. (2018). *Prediction of diabetes using classification algorithms*. Procedia Computer Science, 132, 1578–1585.  
   Link: https://doi.org/10.1016/j.procs.2018.05.122  
   Use: Example of comparative classifier research using the Pima dataset.

4. Maniruzzaman, M., Rahman, M. J., Al-MehediHasan, M., et al. (2018). *Accurate diabetes risk stratification using machine learning: Role of missing value and outliers*. Journal of Medical Systems, 42, 92.  
   Link: https://doi.org/10.1007/s10916-018-0940-7  
   Use: Supports discussing why missing-value handling can influence diabetes-prediction results.  
   Caution: It does not prove that zero values in this CSV are confirmed missing values.

5. Chang, V., Bailey, J., Xu, Q. A., & Sun, Z. (2023). *Pima Indians diabetes mellitus classification based on machine learning (ML) algorithms*. Neural Computing and Applications, 35, 16157–16173.  
   Link: https://doi.org/10.1007/s00521-022-07049-z  
   Use: Related Pima classification study comparing machine-learning algorithms and preprocessing choices.  
   Caution: Its preprocessing and train/test split differ from this project, so results are not directly interchangeable.

## Method references

6. Zou, H., & Hastie, T. (2005). *Regularization and variable selection via the elastic net*. Journal of the Royal Statistical Society: Series B, 67(2), 301–320.  
   Link: https://doi.org/10.1111/j.1467-9868.2005.00503.x  
   Use: Justifies elastic-net regularization.

7. Breiman, L. (2001). *Random forests*. Machine Learning, 45, 5–32.  
   Link: https://doi.org/10.1023/A:1010933404324  
   Use: Justifies Random Forest as the nonlinear ensemble comparison.

8. Varma, S., & Simon, R. (2006). *Bias in error estimation when using cross-validation for model selection*. BMC Bioinformatics, 7, 91.  
   Link: https://doi.org/10.1186/1471-2105-7-91  
   Use: Supports nested cross-validation and separating hyperparameter tuning from outer-fold evaluation.

9. Steyerberg, E. W., Vickers, A. J., Cook, N. R., et al. (2010). *Assessing the performance of prediction models: A framework for traditional and novel measures*. Epidemiology, 21(1), 128–138.  
   Link: https://doi.org/10.1097/EDE.0b013e3181c30fb2  
   Use: Supports reporting discrimination, calibration, and Brier score.

10. Van Calster, B., McLernon, D. J., van Smeden, M., Wynants, L., & Steyerberg, E. W. (2019). *Calibration: the Achilles heel of predictive analytics*. BMC Medicine, 17, 230.  
    Link: https://doi.org/10.1186/s12916-019-1466-7  
    Use: Supports calibration curves and the importance of reporting more than discrimination alone.

11. Altmann, A., Toloşi, L., Sander, O., & Lengauer, T. (2010). *Permutation importance: A corrected feature importance measure*. Bioinformatics, 26(10), 1340–1347.  
    Link: https://doi.org/10.1093/bioinformatics/btq134  
    Use: Supports describing held-out permutation importance.  
    Caution: This project uses permutation importance for interpretation and does not report formal importance p-values.

## Focused research gap

The reviewed Pima studies commonly compare algorithms, feature-selection methods, or preprocessing choices. This project focuses more narrowly on the incremental predictive contribution of two-hour serum insulin through matched with-insulin versus without-insulin nested cross-validation comparisons under multiple zero-value treatments.
