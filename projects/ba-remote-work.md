---
layout: page
title: Remote Work Case Study
permalink: /projects/ba-remote-work/
---

## 1. Problem Statement
Post-pandemic corporate leadership is consistently torn between maintaining flexible remote work policies versus demanding an absolute Return-to-Office (RTO). The core issue stems from purely anecdotal evaluations of productivity. This project bridges the business analytics divide by utilizing actual employee telemetry and survey metrics to quantify how remote policies mathematically impact key performance indicators.

## 2. Dataset
- **Source**: Anonymized internal HR datasets merged with daily software telemetry output (synthesized).
- **Dataset Size**: 1,500 distinct employee records tracked daily over a 24-month horizon.
- **Features**: Commute time, hours logged software usage, self-reported burnout scale (1-10), number of daily remote days, and quarterly performance review scores.
- **Preprocessing**: Imputed missing quarterly reviews using temporal linear interpolation. Categorically encoded department roles (Engineering, Sales, HR) to analyze isolated productivity metrics.

## 3. Feature Engineering
- **Productivity Index**: Formulated a compound ratio calculated by dividing standard "Hours Logged" by the "Burnout Scale" metric. This effectively penalized grinding high hours if it resulted in employee exhaustion.
- **Commute Delta**: Measured the exact time saved explicitly due to remote days and calculated its linear correlation to time spent inside focus-apps vs communication apps.

## 4. Models Tested

*(Note: Structural Equation Modeling and Cluster Analysis were prioritized to determine latent workforce segments.)*

| Model | Silhouette Score | Distortion |
|-------|------------------|------------|
| K-Means Clustering (k=3) | 0.65 | 420.5 |
| DBSCAN | 0.51 | N/A |
| Gaussian Mixture Models | 0.68 | 380.2 |

## 5. Final Model
**K-Means Clustering** was selected explicitly for executive interpretability. While GMM performed slightly better structurally, dividing the workforce into strict, explainable tiers (e.g., "Highly Remote / High Output", "Hybrid / Balanced", "In-Office Preferred") was far easier to present to C-suite stakeholders than probabilistic density mappings.

## 6. Evaluation
- **Elbow Method Analysis**: Showed a sharp bend exactly at K=3, visually confirming the optimal organizational structure naturally divided into fully remote, hybrid, and fully in-office personas.
- **Chi-Square Tests**: Validated that the drop in "Burnout Scale" for the fully remote cohort was highly statistically significant compared to the in-office cohort (p < 0.01).
- **ANOVA Results**: Proved that while purely remote workers logged similar absolute hours to in-office workers, their quarterly review scores were elevated by 0.6 points on average.

## 7. System Architecture
<div class="mermaid">
graph TD
    A[HR Telemetry SQLite] --> B[Data Merging & Temporal Joining]
    B --> C[Missing Data Interpolation]
    C --> D[Feature Engineering Ratio Creation]
    
    subgraph K-Means Workforce Segmentation
        D --> E[PCA Dimensionality Reduction]
        E --> F[K-Means Clustering Algorithms]
        F --> G[Segment A: Full Remote]
        F --> H[Segment B: Internal Hybrid]
        F --> I[Segment C: In-Office Reliant]
    end
    
    subgraph Executive Decision Matrix
        G --> J[Business Intelligence Dashboards]
        H --> J
        I --> J
        J --> K[Policy Optimization Recommendations]
    end
</div>

<script type="module">
  import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
  mermaid.initialize({ startOnLoad: true, theme: 'dark' });
</script>

## 8. Key Learnings
Business Analytics relies entirely on translating code into actionable policy. Building a mathematically perfect predictive model matters less than providing a K-Means visualization that clearly shows executives their remote workers are out-performing the office cohort on an efficiency-per-hour basis.

## 9. GitHub Repository
[Source Code: Remote Work BA](https://github.com/anshid)

## 10. Future Improvements
- Incorporate active Microsoft Teams/Slack API metadata to map internal network graph connectivity, determining if fully remote workers suffer from isolated team silos.
- Develop an isolated predictive churn model utilizing the current burnout and work-location metrics.
