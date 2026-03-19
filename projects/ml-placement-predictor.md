---
layout: page
title: Placement Predictor ML System
permalink: /projects/ml-placement-predictor/
---

## 1. Problem Statement
Educational institutions often struggle to identify which students are at risk of not securing a placement during campus recruitment drives. Failing to identify these students early prevents targeted intervention, such as extra training or interview preparation. This project solves that problem by providing an end-to-end classification system predicting the likelihood of a student being placed based on their academic and demographic profiles.

## 2. Dataset
- **Source**: Internal university academic records (anonymized) supplemented by historic placement data.
- **Dataset Size**: Approximately 10,000 student records spanning 5 years.
- **Features**: Includes numerical features (CGPA, high school marks, aptitude test scores) and categorical features (branch of study, internships completed, backlogs).
- **Preprocessing**: Handled missing values using median imputation for continuous variables and mode imputation for categorical ones. Scaled numerical features using standard scaling.

## 3. Feature Engineering
- **Polynomial Features**: Applied degree-2 polynomial interactions between aptitude scores and CGPA to capture non-linear relationships.
- **Categorical Encoding**: Used target-guided ordinal encoding for categorical features like "branch" strictly based on historical placement rates for that branch.
- **Feature Selection**: Used Recursive Feature Elimination (RFE) to whittle down 24 initial features to the 12 most predictive ones, ensuring the model remains computationally efficient and robust against overfitting.

## 4. Models Tested

| Model | Accuracy | F1 Score |
|-------|----------|----------|
| Logistic Regression (Baseline) | 0.82 | 0.78 |
| Decision Tree Classifier | 0.88 | 0.86 |
| Random Forest Classifier | 0.94 | 0.93 |
| XGBoost | 0.93 | 0.92 |

## 5. Final Model
The **Random Forest Classifier** was selected as the final model. Despite XGBoost performing similarly, Random Forest proved slightly more resilient to outliers in our specific academic domain without requiring extensive hyperparameter tuning. It strikes an excellent balance of high precision (avoiding false placement hopes) and high recall (catching at-risk students), which is precisely what university administration requires.

## 6. Evaluation
- **Confusion Matrix Details**: Showed a very low False Positive Rate (predicting placed when they weren't), which was critical for ensuring all at-risk students were captured.
- **ROC Curve**: Reached an Area Under Curve (AUC) score of 0.95.
- **Cross-Validation**: Implemented 5-fold stratified cross-validation, resulting in a stable accuracy variance of ±0.012 across folds, proving the model generalizes well to unseen cohorts.

## 7. System Architecture
<div class="mermaid">
graph TD
    A[Raw Student Data] --> B[Data Imputation Pipeline]
    B --> C[Feature Engineering & Scaling]
    C --> D[Random Forest Model]
    
    subgraph Model Training and Evaluation
        D --> E[Stratified K-Fold CV]
        E --> F[Hyperparameter Optimization]
        F --> G[Saved Model .pkl]
    end
    
    subgraph Inference System
        G --> H[FastAPI Endpoint]
        H --> I[Admin Dashboard Prediction]
    end
</div>

<script type="module">
  import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
  mermaid.initialize({ startOnLoad: true, theme: 'dark' });
</script>

## 8. Key Learnings
Implementing a robust baseline model early saved weeks of debugging later. I learned the critical importance of preventing data leakage in the context of academic data, specifically ensuring that temporal splits (training on older years, testing on the newest year) were used instead of random splits to simulate true real-world deployment.

## 9. GitHub Repository
[Source Code: Placement Predictor ML](https://github.com/anshid/placement-predictor-ml)

## 10. Future Improvements
- Integrate NLP analysis on student resumes to extract additional features.
- Migrate the inference pipeline from FastAPI to a fully containerized Kubernetes deployment to handle large concurrent query bursts during peak recruitment seasons.
