---
layout: page
title: Data Storytelling - College Majors
permalink: /projects/da-majors/
---

## 1. Problem Statement
Incoming college students are often overwhelmed by the economic implications of choosing distinct college majors. Universities possess volumes of historical graduate tracking data but fail to translate it into actionable visualizations for high school students. This project cleans and visualizes 173 unique majors to construct an interactive narrative comparing salary distributions versus employment rates.

## 2. Dataset
- **Source**: 'FiveThirtyEight' College Majors Dataset compiled from the American Community Survey (ACS).
- **Dataset Size**: 173 recorded college majors aggregated across 3 million graduates.
- **Features**: Major category, total enrolled, proportion of women, strict employment rate, median salary, and 25th/75th percentile earnings.
- **Preprocessing**: Removed smaller datasets with sample coverage below the statistical threshold of 100 participants. Computed unemployment vectors specifically relative to the size of the major's total graduating class.

## 3. Feature Engineering
- **Salary/Employment Ratios**: Engineered 'Risk-Reward Index' by dividing median salary by the specific field's unemployment rate.
- **Dimensionality Reduction**: Grouped 173 specific majors into 16 broad overarching domains (e.g., STEM, Humanities, Business) prior to calculating aggregate category medians.
- **Gender Disparity Metric**: Subtracted the proportion of women from 0.5 to quantify fields explicitly over-representing a singular gender to analyze correlations with pay gaps.

## 4. Models Tested

*(Note: Focused on linear causal relationships and narrative storytelling.)*

| Model | Adjusted R-Squared | Mean Absolute Error |
|-------|--------------------|---------------------|
| Ordinary Least Squares (OLS) | 0.61 | $8,400 |
| Ridge Regression (Alpha 1.0) | 0.60 | $8,500 |
| Random Forest Regressor | 0.74 | $6,100 |

## 5. Final Model
**Random Forest Regressor** demonstrated the strongest capability to predict median salary based on domain metadata. OLS regression struggled heavily with the massive variance in engineering salaries skewing the linear trajectory compared to humanities fields. The Random Forest naturally bucketed the distinctly non-linear relationships.

## 6. Evaluation
- **Feature Importance**: Ranked 'Proportion of Women' and 'Share of STEM' as the two highest contributing features determining the median salary output.
- **Visual Distributions**: Plotted comparative histograms and scatter plots tracking unemployment rates on the X-axis against median salaries on the Y-axis.
- **Cross-Validation**: 5-fold CV yielding an R-squared variance of just 0.05, validating the stability of the model.

## 7. System Architecture
<div class="mermaid">
graph TD
    A[FiveThirtyEight Raw ACS Dataset] --> B[Data Cleaning & Null Pruning]
    B --> C[Categorical Grouping 173 -> 16 Bins]
    
    subgraph Narrative Visualization
        C --> D[Scatter Plots Plotly]
        C --> E[Histogram Overlays Seaborn]
    end
    
    subgraph Regression Modeling
        C --> F[Random Forest Regressor]
        F --> G[Extract Feature Importances]
        G --> H[Correlate Demographics vs Salary]
    end
    
    subgraph Dashboard Output
        D --> I[Jupyter Notebook Report]
        E --> I
        H --> I
    end
</div>

<script type="module">
  import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
  mermaid.initialize({ startOnLoad: true, theme: 'dark' });
</script>

## 8. Key Learnings
Data scaling visually hides complex relationships. OLS linear regression is overly sensitive to categorical high-earning clusters (like Petroleum Engineering). By switching to tree-based regressors, the distinct wage groupings per academic domain became trivial to map mathematically. The strongest realization was that visualizing the error margin of salaries (25th to 75th percentile) is far more informative to a student than a strict median point.

## 9. GitHub Repository
[Source Code: College Majors Data Storytelling](https://github.com/anshid)

## 10. Future Improvements
- Scrape university tuition datasets to map "Return on Investment (ROI)" by combining degree cost against expected graduate salary.
- Build an interactive web app using Streamlit allowing students to filter majors by their expected budget and personal risk tolerance.
