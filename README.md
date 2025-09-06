#  HR Analytics Exploration: From EDA to PCA & Clustering

##  Project Overview

This project explores HR data using exploratory data analysis (EDA), visualization, dimensionality reduction (PCA), and clustering (K-Means). The goal is to uncover patterns in employee engagement, satisfaction, absenteeism, performance, and departmental structure — and to evaluate whether these traits can be condensed into meaningful components for modeling and segmentation.

---

##  Dataset Source

This project uses the [HR Analytics Dataset on Kaggle](https://www.kaggle.com/datasets/anshika2301/hr-analytics-dataset), which contains employee-level data including:

- Salary, engagement survey scores, satisfaction ratings  
- Absenteeism, lateness, and employment status  
- Departmental and performance metrics  

---

##  Workflow Summary

###  Load and Inspect Data
- Loaded HR dataset (`hr_data`) and inspected structure.
- Identified numeric and categorical features for analysis.

---

##  Exploratory Data Analysis & Visualization

###  Correlation Heatmap
- Created a heatmap of correlations between numeric variables.
- Found strong relationships between salary, engagement, satisfaction, and performance.

###  Engagement vs Satisfaction
- Scatter plot showed a positive relationship between engagement survey score and employee satisfaction.
- Departmental coloring revealed cultural or managerial clustering.

###  Employment Status by Department
- Stacked bar chart visualized employee status (e.g., Active, Terminated) across departments.
- Highlighted retention and turnover hotspots.

###  Absenteeism Distribution
- Histogram showed a right-skewed distribution — most employees had low absences.
- Outliers flagged for potential intervention.

---

##  PCA: Dimensionality Reduction

###  Standardize Numeric Features
- Used `StandardScaler` to normalize all numeric features before PCA.

###  Handle Missing Values
- Imputed missing values using `SimpleImputer(strategy='mean')` to ensure PCA compatibility.

###  Apply PCA
- Applied PCA to standardized data.
- Extracted principal components and explained variance ratios.

###  Explained Variance Ratios
- PC1: ~40%, PC2: ~33%, PC3: ~26%
- No single component dominated — confirmed multi-dimensional structure.

###  Reduce to 2D and Visualize
- Reduced dataset to 2 dimensions using PCA.
- Plotted employees in PCA space, colored by department.

###  Feature Contributions to PC1
- Top contributors: `PerfScoreID`, `EngagementSurvey`, `EmpSatisfaction`, `Salary`
- PC1 interpreted as a “workforce value axis.”

###  Visualize PCA Loadings
- Bar chart of loadings for `Salary`, `Absences`, and `EngagementSurvey` on PC1 and PC2:
  - Salary: +0.30 (PC1), +0.25 (PC2)
  - EngagementSurvey: +0.30 (PC1), –0.30 (PC2)
  - Absences: –0.01 (PC1), –0.05 (PC2)

###  PCA on 3 Features
- Applied PCA to `EngagementSurvey`, `EmpSatisfaction`, and `Absences`.
- Explained variance: [0.40, 0.33, 0.26] — no single dominant component.

---

##  Clustering Analysis

###  K-Means on Original vs PCA Data
- Applied K-Means clustering (k=3) on both original and PCA-reduced data.
- Compared performance using silhouette scores:
  - Original Data: **0.1468**
  - PCA-Reduced Data: **0.5879**
- PCA significantly improved cluster quality and separation.

###  Cluster Employees by PerformanceScore
- Projected employees into PCA space and grouped by `PerformanceScore`.
- Revealed separation between high performers and departmental clusters.

---

##  Strategic Interpretation

### PC1: Workforce Value Axis
- Driven by salary, engagement, satisfaction, and performance.
- High PC1 scores reflect high-value, engaged employees.

###  PC2: Engagement vs Compensation Tension
- Salary loads positively, engagement loads negatively.
- Highlights potential morale mismatches or compensation misalignment.

###  Absenteeism: Minimal Influence
- Very low loadings on both components — not a dominant behavioral signal in PCA space.

---

##  When PCA Is Appropriate in HR Analytics

- **Survey compression**: Reduce dozens of engagement questions into latent dimensions.
- **Multicollinearity handling**: Transform correlated features into uncorrelated components.
- **Clustering enhancement**: Improve segmentation quality and interpretability.
- **Feature engineering**: Use components as inputs for predictive models.
- **Visualization**: Project high-dimensional employee data into 2D for insight.

---
