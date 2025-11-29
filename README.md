# -Fair-and-Explainable-Heart-Disease-Risk-Prediction-Using-Machine-Learning
CSC461- Final Project

Overview: 
This project applies bias mitigation to improve fairness in heart disease risk prediction. We achieved a 78% reduction in Equal Opportunity Difference while maintaining strong predictive performance, demonstrating that fairness and accuracy are compatible goals in healthcare ML.

Methodology:
Dataset: Cleveland Heart Disease (303 patients, 14 features). Significant gender imbalance (68% male, 32% female) with AIF360 Maximum Unfairness Score of 47.0015.
Models: Logistic Regression, KNN, Random Forest, SVM, XGBoost. Trained with GridSearchCV (3-5 fold CV, ROC-AUC scoring).
Bias Mitigation: Applied reweighting and resampling to balance demographic representation during training.
Evaluation: Fairness metrics (EOD, AOD, Disparate Impact, Theil Index), performance metrics (Accuracy, Recall, ROC-AUC), and explainability tools (SHAP, LIME, Rashomon analysis with 20 model instances per algorithm).

Results:
Key Achievement: 78% reduction in EOD, 93% reduction in AOD
Baseline (Before Mitigation): Logistic Regression showed EOD = 0.312, DI = 2.600. KNN had worst fairness (EOD = 0.545, DI = 3.25). XGBoost best baseline (EOD = 0.221, DI = 1.950).
After Mitigation: Logistic Regression improved to EOD = 0.097 (69% reduction), DI = 1.671, maintaining strong recall (0.952) and ROC-AUC (0.947). XGBoost achieved lowest disparities (EOD = 0.058, DI = 1.430) with accuracy = 0.826.
Key Insight: SHAP and LIME confirmed fairness improvements came from legitimate feature weighting. Clinical features (thalassemia, chest pain, vessels) ranked highest, while sex showed minimal importance (4-9.6%) across both genders.

Technical Stack: 
Python | scikit-learn, XGBoost | pandas, numpy | AI Fairness 360 | SHAP, LIME | GridSearchCV


Key Findings:
1.)Baseline bias was substantial: Fairness gaps ranged from EOD = 0.221 to 0.545 across algorithms, indicating systematic gender-based disparities in the imbalanced dataset (68% male, 32% female).
2.)Reweighting effectively reduced bias: Logistic Regression improved 69% on EOD (0.312 → 0.097) and 36% on Disparate Impact (2.600 → 1.671), while maintaining high recall (0.952) and strong ROC-AUC (0.947).
3.)Improvements were legitimate: SHAP/LIME analysis confirmed clinical features (thalassemia, chest pain, vessels) drove decisions for all genders, with sex showing minimal importance (4-9.6%), validating equitable learning rather than demographic masking.

Limitations & Future Work: 
Limitations: Small dataset (303 samples), binary gender classification only, pre-processing mitigation only, no clinical validation.
Future Work: Larger datasets, multi-group fairness (age, race), advanced mitigation techniques (Disparate Impact Remover, adversarial debiasing), clinical validation, intersectional fairness analysis.

