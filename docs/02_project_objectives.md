# 02 — Project Objectives

## Project Title

**Association among 3 factors of wellness**

## 1. Primary Objective

To investigate statistical associations among **mental, physical, and nutritional wellbeing** among university students using self-collected survey data and Data Science techniques.

The project focuses on understanding patterns, examining relationships, and interpreting results rather than developing a clinical diagnostic system.

## 2. Specific Objectives

### Objective 1 — Data Collection and Understanding

- Collect primary survey data from university students.
- Examine demographic, mental wellness, physical activity, nutrition, and lifestyle variables.
- Identify variable types and measurement scales.
- Understand the dataset's structure and limitations.

**Completed:** 100 survey responses containing 22 original variables.

### Objective 2 — Data Cleaning and Preprocessing

- Identify missing, inconsistent, and unusual responses.
- Standardize numerical measurements and units.
- Apply appropriate outlier detection and missing-value treatment.
- Process mixed-format physical activity responses.
- Encode multi-select dietary categories.
- Preserve original responses for traceability.

**Completed:** Initial cleaning produced 25 columns, followed by extended preprocessing resulting in 42 columns.

### Objective 3 — Exploratory Data Analysis

- Calculate descriptive statistics.
- Examine response distributions and group differences.
- Generate appropriate statistical visualizations.
- Identify preliminary relationships among wellness variables.

**Completed:** Frequency analysis, descriptive statistics, boxplots, bar charts, correlation heatmaps, and scatter plots.

### Objective 4 — Statistical Hypothesis Testing

Apply statistical tests to investigate specific research questions.

| Statistical Test | Research Objective |
|---|---|
| F-test | Compare entertainment screen-time variances by gender |
| Independent two-sample t-test | Compare mean entertainment screen time by gender |
| One-sample Z-test | Compare average sleep duration against a 7-hour reference |
| Chi-square test | Investigate the association between gender and meal regularity |

**Completed:** All four procedures were implemented and interpreted.

### Objective 5 — Correlation and Regression

- Examine correlations among selected wellness variables.
- Apply simple linear regression to investigate the relationship between sleep duration and evening physical energy.
- Interpret the direction and strength of relationships.
- Distinguish statistical association from causation.

**Completed:** Simple linear regression and Pearson correlation analysis.

### Objective 6 — Data Quality Assessment

Evaluate the dataset across eight dimensions:

1. Completeness
2. Validity
3. Consistency
4. Uniqueness
5. Accuracy
6. Timeliness
7. Integrity
8. Relevance

**Completed:** Eight-dimensional assessment of the initial cleaned dataset, with additional validation performed during extended cleaning.

### Objective 7 — Principal Component Analysis

- Standardize selected numerical features.
- Calculate covariance matrices, eigenvalues, and eigenvectors.
- Perform dimensionality reduction.
- Examine explained variance.
- Verify the mathematical implementation using scikit-learn.

**Completed:** PCA reduced 10 features to 8 principal components while retaining approximately 92.73% of the variance.

### Objective 8 — Linear Discriminant Analysis

- Define exploratory stress-frequency classes.
- Calculate within-class and between-class scatter matrices.
- Implement discriminant analysis mathematically.
- Evaluate classification performance.
- Compare manual predictions with scikit-learn.

**Completed:** LDA achieved 68% test accuracy and approximately 53.31% balanced accuracy, indicating limited classification performance.

### Objective 9 — Documentation and Reproducibility

- Maintain organized project files and notebooks.
- Document preprocessing decisions and statistical methods.
- Preserve original data and derived outputs appropriately.
- Prepare technical reports and project documentation.
- Maintain the project repository on GitHub.

## 3. Expected Outcomes

The project aims to produce:

- A documented student wellness dataset and preprocessing workflow.
- Descriptive summaries of mental, physical, and nutritional wellbeing.
- Statistical evidence of selected associations.
- Visual representations of observed patterns.
- A systematic data-quality assessment.
- Mathematical implementations of PCA and LDA.
- Reproducible code and academic documentation.

## 4. Scope and Boundaries

The study is based on 100 self-selected, self-reported survey responses collected between 14 and 18 August 2026.

Its findings describe associations within this sample and should not be generalized automatically to all university students.

The project does not establish causation, provide medical diagnoses, or claim reliable individual mental-health prediction.

## 5. Objective Completion Summary

| Project Area | Status |
|---|---|
| Data collection and understanding | Completed |
| Initial and extended cleaning | Completed |
| Exploratory data analysis | Completed |
| Hypothesis testing | Completed |
| Correlation and regression | Completed |
| Data quality assessment | Completed |
| PCA | Completed |
| LDA | Completed |
| Technical documentation | Completed |
| GitHub final integration | In progress |

The project has completed its principal analytical objectives. Final repository organization and submission verification remain part of the concluding workflow.
