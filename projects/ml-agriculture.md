---
layout: page
title: Predictive Modeling for Agriculture
permalink: /projects/ml-agriculture/
---

## 1. Problem Statement
Farmers in developing agricultural economies face massive financial barriers regarding comprehensive soil testing. Testing for dozens of chemical metrics is expensive. This project aims to identify the single most predictive soil feature that can dynamically map out ideal crop classification, drastically reducing laboratory testing costs while preserving output yield efficiency.

## 2. Dataset
- **Source**: Sourced from public agricultural repositories combined with Kaggle's comprehensive soil composition datasets.
- **Dataset Size**: 2,200 unique soil samples spanning 22 distinct crop classifications.
- **Features**: Nitrogen (N), Phosphorous (P), Potassium (K) ratios, along with temperature, humidity, pH values, and rainfall.
- **Preprocessing**: Handled minor multi-collinearity issues. Removed anomalous outliers in rainfall data using Interquartile Range (IQR) clipping to standardize crop expectation metrics.

## 3. Feature Engineering
- **Interaction Ratios**: Generated features mapping the critical N/P/K ratios against baseline humidity metrics to establish compound indicators of soil health.
- **Mathematical Transformations**: Applied log-transformations to rainfall and temperature inputs which were originally heavily skewed left, ensuring they followed roughly normal distributions acceptable for linear evaluation.

## 4. Models Tested

| Model | Accuracy | F1 Score |
|-------|----------|----------|
| K-Nearest Neighbors (Baseline) | 0.65 | 0.63 |
| Logistic Regression (Multi-class)| 0.72 | 0.71 |
| Decision Tree Classifier | 0.85 | 0.84 |
| Support Vector Machine (RBF) | 0.81 | 0.79 |

## 5. Final Model
The **Decision Tree Classifier** was explicitly chosen. Not only did it achieve top-tier performance natively, but the intrinsic nature of decision trees provides absolute, transparent feature importance. Specifically, evaluating nodes immediately confirmed that 'Potassium' (K) levels carried the highest singular information gain, effectively answering the core problem statement.

## 6. Evaluation
- **Confusion Matrix**: High density along the true-positive diagonal. Misclassifications predominantly occurred strictly between biogenetically similar crops (e.g., specific pulse varieties).
- **ROC Curve**: One-vs-Rest AUC curves ranged between 0.89 to 0.94 for various crop classes.
- **Cross-Validation**: Verified resilience using 10-fold cross-validation showing minimal variance in multi-class accuracy metrics (< 0.02 delta).

## 7. System Architecture
<div class="mermaid">
graph TD
    A[Raw Soil Data Collection] --> B[Data Cleaning & IQR Outlier Removal]
    B --> C[Log Transformation & Feature Normalization]
    C --> D[Multi-model Training Phase]
    
    subgraph Feature Importance Harvesting
        D --> E[Decision Tree Classifier]
        E --> F[Information Gain Calculation]
        F --> G[Identify Top Primary Feature: Potassium]
    end
    
    subgraph Cost-Optimized Pipeline
        G --> H[Single-Feature Predictive Model]
        H --> I[Optimized Crop Recommendations]
    end
</div>

<script type="module">
  import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
  mermaid.initialize({ startOnLoad: true, theme: 'dark' });
</script>

## 8. Key Learnings
The highest accuracy isn't always the goal. While a deep neural network might squeeze out an extra 2% accuracy, it fundamentally fails the business objective of transparency and variable isolation. Understanding domain constraints (testing costs) is just as critical as algorithmic deployment.

## 9. GitHub Repository
[Source Code: Predictive Agriculture](https://github.com/anshid)

## 10. Future Improvements
- Expand the model to incorporate real-time local weather API feeds for dynamically shifting recommendations.
- Refine the decision thresholds directly into a simple mobile app calculator for farmers in remote regions disconnected from the internet.
