---
layout: page
title: Netflix Movies Data Analysis
permalink: /projects/da-netflix/
---

## 1. Problem Statement
Netflix executives require clear, data-driven narratives regarding historical programming to inform current production strategies. Specifically, they need to know if the industry-wide assumption that "movies are getting shorter" holds true over time and how genre attributes impact runtime distributions, allowing them to optimize pacing for modern streaming audiences.

## 2. Dataset
- **Source**: Kaggle 'Netflix Movies and TV Shows' extended dataset.
- **Dataset Size**: ~9,000 titles originally, filtered strictly to 4,200 movies released post-1990.
- **Features**: Title, duration, release year, genre/category tags, director, cast, and IMDB rating.
- **Preprocessing**: Filtered out all TV shows to isolate film runtime variables. Dropped rows with null values in critical duration or release-year columns to maintain statistical integrity.

## 3. Feature Engineering
- **Genre Bucketization**: Exploded the multi-label 'listed_in' genre tags and mapped them to core aggregated categories (Action, Drama, Comedy, Documentary) to simplify aggregation.
- **Decade Grouping**: Created a categorical 'Decade' feature mapping raw release years into distinct bins (1990s, 2000s, 2010s) to perform cohort analysis over time.

## 4. Models Tested

*(Note: As an Exploratory Data Analysis project, inferential statistical models were prioritized over predictive ones.)*

| Model | R-Squared | Mean Squared Error |
|-------|-----------|--------------------|
| Linear Regression (Baseline Runtime Trend) | 0.42 | 520.4 |
| Polynomial Regression (Degree 2) | 0.58 | 390.1 |
| ARIMA (Time Series Runtime Forecasting) | N/A | 342.7 |

## 5. Final Model
The **Polynomial Regression** effectively captured a slight downward curve in runtime starting in the late 2010s, but the primary findings relied on **Kruskal-Wallis H-tests** proving that differences in median runtimes across decades were statistically significant, not just random fluctuations.

## 6. Evaluation
- **Visual Distributions**: Plotted KDE and violin plots clearly showing the tightening of runtime variance in the modern era (clustering around 90-100 minutes) compared to the wide spread of the 1990s.
- **Correlation**: Identified a weak negative correlation (-0.18) between release year and movie duration specifically for Action/Drama genres, while Documentaries maintained a flat trendline.
- **Cross-Validation**: N/A for raw EDA.

## 7. System Architecture
<div class="mermaid">
graph TD
    A[Raw Netflix CSV] --> B[Pandas Data Filtering]
    B --> C[TV Show Removal & Null Handling]
    C --> D[Explode Genre Columns into Bins]
    
    subgraph Analytical Pipeline
        D --> E[Matplotlib Temporal Aggregation]
        D --> F[Seaborn Distribution Plots]
        F --> G[Statistical Significance Testing]
    end
    
    subgraph Business Narrative
        E --> H[Generate Executive Dashboard]
        G --> H
        H --> I[Actionable Content Output Rules]
    end
</div>

<script type="module">
  import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs';
  mermaid.initialize({ startOnLoad: true, theme: 'dark' });
</script>

## 8. Key Learnings
Data scaling visually impacts the narrative. Correctly anchoring axes and identifying anomalies (like 10-hour avant-garde films) before generating standard plots prevents executives from misinterpreting the average viewer's experience.

## 9. GitHub Repository
[Source Code: Netflix EDA](https://github.com/anshid)

## 10. Future Improvements
- Scrape IMDB to pull in exact production budgets to identify ROI metrics correlated with film length.
- Build an interactive Plotly dashboard so stakeholders can dynamically filter runtimes by their specific country of origin.
