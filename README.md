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


References: 

Fairness Foundations & Theory

Narayanan, A. (2018). Tutorial: 21 Fairness Definitions and Their Politics.
Barocas, S., Hardt, M., & Narayanan, A. (2019). Fairness and Machine Learning.
Barocas, S., & Selbst, A. D. (2016). Big Data's Disparate Impact.
Berk, R. A., Heidari, H., Jabbari, S., Kearns, M., & Roth, A. (2021). Fairness in Criminal Justice Risk Assessments: The State of the Art.

Bias Mitigation & Fairness Tools

Bellamy, R. K. E., Dey, K., Hind, M., et al. (2018). AI Fairness 360: An Extensible Toolkit for Detecting, Understanding, and Mitigating Unwanted Algorithmic Bias.
Zhang, B. H., Lemoine, B., & Mitchell, M. (2018). Mitigating Unwanted Biases with Adversarial Learning. AAAI/ACM Conference on AI, Ethics, and Society.
Bird, S., Dudík, M., Edgar, R., et al. (2020). Fairlearn: A Toolkit for Assessing and Improving Fairness in AI.
Bantilan, N. (2021). Themis-ML: A Fairness-aware Machine Learning Interface for End-to-end Discrimination Discovery and Mitigation.
Alvarez, J. M., et al. (2024). Policy Advice and Best Practices on Bias and Fairness in AI.

Gender & Intersectionality

Buolamwini, J., & Gebru, T. (2018). Gender Shades: Intersectional Accuracy Disparities in Commercial Gender Classification. FAT* Conference.
Bickel, P. J., Hammel, E. A., & O'Connell, J. W. (1975). Sex Bias in Graduate Admissions: Data from Berkeley.
Benthall, S., & Haynes, B. D. (2017). Racial Categories in Machine Learning. Proceedings of FAT*.
Zhao, J., Wang, T., Yatskar, M., Ordonez, V., & Chang, K.-W. (2017). Men Also Like Shopping: Reducing Gender Bias Amplification Using Corpus-level Constraints.

Fairness in Decision-Making & Social Change

Abebe, R., Barocas, S., Kleinberg, J., Levy, K., Raghavan, M., & Robinson, D. G. (2020). Roles for Computing in Social Change. FAT* Conference.
Andrus, M., Spitzer, E., Brown, J., & Xiang, A. (2021). What We Can't Measure, We Can't Understand: Challenges to Demographic Data Procurement in the Pursuit of Fairness. FAT* Conference.
Ahn, Y., & Lin, Y.-R. (2019). Fairsight: Visual Analytics for Fairness in Decision Making. IEEE Transactions on Visualization and Computer Graphics.
Ashurst, C., Barocas, S., Campbell, R., & Raji, D. (2022). Disentangling the Components of Ethical Research in Machine Learning. FAT* Conference.

Algorithmic Auditing & Testing

Adebayo, J. (2018). FairML: Auditing Black-Box Predictive Models.
Angwin, J., Larson, J., Mattu, S., & Kirchner, L. (2016). Machine Bias.

Explainability & Interpretability

Xin, D., Eckert, C., Huang, F., & Wang, A. (2022). Exploring Rashomon Sets for Model Interpretability. arXiv:2209.08040.
UBC Systopia Lab. (2022). Tree Farms: Exploring Rashomon Sets for Model Interpretability. GitHub.

Data Ethics & Responsible AI

Zook, M., Barocas, S., Boyd, D., et al. (2017). Ten Simple Rules for Responsible Big Data Research. PLOS Computational Biology.
Birhane, A., Ruane, E., Laurent, T., et al. (2022). The Forgotten Margins of AI Ethics. FAT* Conference.
Arnold, M., Bellamy, R. K. E., Hind, M., et al. (2019). FactSheets: Increasing Trust in AI Services through Supplier's Declarations of Conformity.
Ashurst, C., Hine, E., Sedille, P., & Carlier, A. (2022). AI Ethics Statements: Analysis and Lessons Learnt from NeurIPS Broader Impact Statements. FAT* Conference.

Fairness Benchmarking & Datasets

Baumann, J., Castelnovo, A., Crupi, R., Inverardi, N., & Regoli, D. (2023). Bias on Demand: A Modelling Framework That Generates Synthetic Data With Bias. FAT* Conference.

Fairness Trade-offs & Impossibility Results

Bell, A., Bynum, L., Drushchak, N., Zakharchenko, T., Rosenblatt, L., & Stoyanovich, J. (2023). The Possibility of Fairness: Revisiting the Impossibility Theorem in Practice. FAT* Conference.
Blili-Hamelin, B., & Hancox-Li, L. (2023). Making Intelligence: Ethical Values in IQ and ML Benchmarks. FAT* Conference.

Causal Reasoning & Simpson's Paradox

Arah, O. A. (2008). The Role of Causal Reasoning in Understanding Simpson's Paradox, Lord's Paradox, and the Suppression Effect.
Alin, A. (2010). Simpson's Paradox. Wiley Interdisciplinary Reviews: Computational Statistics.
Alipourfard, N., Fennell, P. G., & Lerman, K. (2018). Can You Trust the Trend: Discovering Simpson's Paradoxes in Social Data. WSDM.

LLM & Code Generation Fairness

Chiang, W.-L., Zheng, L., Sheng, Y., et al. (2024). Chatbot Arena: An Open Platform for Evaluating LLMs by Human Preference. arXiv:2403.04132.
Huang, D., Bu, Q., Zhang, J., Xie, X., Chen, J., & Cui, H. (2024). Bias Testing and Mitigation in LLM-based Code Generation. arXiv:2309.14345.
Yu, Y., Rong, G., Shen, H., et al. (2024). Fine-Tuning Large Language Models to Improve Accuracy and Comprehensibility of Automated Code Review. ACM Transactions on Software Engineering and Methodology.

Machine Learning Foundations

Arlot, S., & Celisse, A. (2010). A Survey of Cross-Validation Procedures for Model Selection.
Anandkumar, A., Foster, D. P., Hsu, D., Kakade, S. M., & Liu, Y. K. (2014). A Spectral Algorithm for Latent Dirichlet Allocation.

Contributors
Ritta Neg-Mfa and Jeena Weber Langstaff
