# 03 — Data Science Process

## Project Title

**Association among 3 factors of wellness**

## 1. Introduction

This project follows the **CRISP-DM (Cross-Industry Standard Process for Data Mining)** framework to investigate associations among mental, physical, and nutritional wellbeing among university students.

CRISP-DM provides a systematic approach to solving data-driven problems through six interconnected phases:

1. Business Understanding
2. Data Understanding
3. Data Preparation
4. Modelling
5. Evaluation
6. Deployment

The project applies these phases iteratively, allowing insights from data exploration and evaluation to guide preprocessing and analysis decisions.

---

## 2. Phase 1 — Business Understanding

### Problem Identification

University students may experience academic stress, irregular sleep patterns, prolonged screen exposure, inconsistent dietary habits, and varying levels of physical activity.

The project investigates statistical relationships among these factors.

### Problem Statement

**How are mental, physical, and nutritional wellbeing factors associated among university students, and which lifestyle characteristics are related to higher reported stress and lower physical energy?**

### Research Objectives

- Understand patterns in student wellness data.
- Investigate relationships among lifestyle and wellbeing variables.
- Apply statistical and multivariate analytical techniques.
- Interpret results while acknowledging limitations.

**Outcome:** The research problem, objectives, scope, and analytical direction were established.

---

## 3. Phase 2 — Data Understanding

### Data Collection

Primary data were collected using an online Google Form distributed among university students.

| Attribute | Description |
|---|---|
| Total responses | 100 |
| Original variables | 22 |
| Collection period | 14–18 August 2026 |
| Data source | Primary survey |
| Dataset type | Cross-sectional |
| Measurement method | Self-reported responses |

### Data Inspection

The dataset was examined to identify:

- Variable names and measurement scales.
- Numerical, categorical, and free-text variables.
- Missing and inconsistent responses.
- Mixed measurement units.
- Duplicate records.
- Unusual values and possible outliers.

### Variable Classification

Variables were classified using nominal, ordinal, interval, ratio, discrete, and continuous measurement concepts.

The classification also distinguished structured, semi-structured, and unstructured responses.

**Outcome:** The dataset structure and major data-quality challenges were identified.

---

## 4. Phase 3 — Data Preparation

Data preparation was completed in two stages.

### 4.1 Initial Data Cleaning

The initial cleaning stage involved:

- Renaming long survey questions into shorter column names.
- Inspecting missing values and duplicates.
- Creating respondent identifiers.
- Parsing sleep duration, entertainment screen time, and water intake.
- Converting numerical ranges into midpoint values.
- Applying IQR-based outlier treatment.
- Using median imputation for selected numerical variables.

**Output:** Initial cleaned dataset containing 100 rows and 25 columns.

### 4.2 Extended Data Cleaning

Extended cleaning addressed additional variables that remained in mixed formats.

**Academic Screen Time**

Converted numerical responses, hour/minute formats, and ranges into standardized hours.

Result: 97 valid values and 3 missing values.

**Consecutive Sitting Duration**

Standardized hours, minutes, and numerical ranges.

Result: 94 valid values and 6 missing values.

**Physical Activity**

Separated activity measurements into:

- Daily step counts.
- Walking duration in minutes.
- Walking distance in kilometres.

Additional inference and status fields were created to preserve uncertainty in responses without explicit units.

**Dietary Encoding**

Seven dietary categories were converted into binary indicator features using multi-hot encoding.

**Free-Text Normalization**

Emotional-wellbeing responses were normalized through lowercasing, whitespace trimming, and removal of repeated spaces.

### 4.3 Validation

The extended cleaning process included:

- Numerical range checks.
- Duplicate respondent-ID checks.
- Dietary binary-feature validation.
- Original-column preservation checks.
- Correction of a known step-count parsing error.
- Identification of ambiguous and lower-bound activity responses.

**Output:** Extended cleaned dataset containing 100 rows and 42 columns.

---

## 5. Phase 4 — Modelling

The project implemented statistical and multivariate techniques to investigate the collected data.

### 5.1 Exploratory Data Analysis

EDA included:

- Frequency distributions.
- Descriptive statistics.
- Group comparisons.
- Boxplots and bar charts.
- Correlation heatmaps.
- Scatter plots and survey-response visualizations.

### 5.2 Statistical Hypothesis Testing

Four statistical procedures were implemented:

| Test | Purpose |
|---|---|
| F-test | Compare entertainment screen-time variances by gender |
| Independent two-sample t-test | Compare mean entertainment screen time by gender |
| One-sample Z-test | Compare mean sleep duration with a 7-hour reference |
| Chi-square test | Examine association between gender and meal regularity |

### 5.3 Correlation and Regression

Pearson correlation analysis was used to investigate linear associations among selected numerical variables.

Simple linear regression examined the relationship between sleep duration and evening physical energy.

### 5.4 Principal Component Analysis

PCA was implemented mathematically using:

- Feature standardization.
- Covariance matrix calculation.
- Eigenvalue and eigenvector decomposition.
- Explained-variance calculation.
- Projection onto principal components.

Ten numerical features were reduced to eight principal components while retaining approximately 92.73% of total variance.

### 5.5 Linear Discriminant Analysis

LDA was implemented using:

- Exploratory stress-frequency classes.
- Class-wise means.
- Within-class and between-class scatter matrices.
- Discriminant directions.
- Classification and evaluation.

The manual implementation was compared with scikit-learn.

---

## 6. Phase 5 — Evaluation

### Statistical Evaluation

The project interpreted statistical-test results using test statistics, p-values, and the selected significance level.

Correlation and regression results were evaluated in terms of direction, strength, and explained variance.

### Data Quality Assessment

Eight data-quality dimensions were assessed:

1. Completeness
2. Validity
3. Consistency
4. Uniqueness
5. Accuracy
6. Timeliness
7. Integrity
8. Relevance

The assessment was performed on the initial cleaned dataset, while the extended dataset underwent additional structural and transformation checks.

### PCA Evaluation

The manual PCA implementation was verified against NumPy and scikit-learn.

Eight components retained 92.73% of the original variance.

### LDA Evaluation

| Metric | Result |
|---|---|
| Test accuracy | 68% |
| Balanced accuracy | 53.31% |
| Manual vs scikit-learn prediction agreement | 100% |
| Higher-stress class recall | 12.5% |

Although the manual and library implementations agreed, the model showed weak sensitivity to the higher-stress-frequency class.

Therefore, LDA was treated as an exploratory academic experiment rather than a reliable student-risk prediction system.

---

## 7. Phase 6 — Deployment and Delivery

For this academic project, deployment refers to delivering the completed analytical work and supporting documentation.

The project deliverables include:

- Original survey data and classification records.
- Initial and extended data-cleaning workflows.
- Exploratory analysis and statistical implementations.
- Data Quality Assessment, PCA, and LDA notebooks.
- Visualizations and analytical findings.
- Final project report.
- Technical documentation.
- GitHub repository containing the project files and development history.

**No production website, mobile application, or clinical prediction system was deployed.**

---

## 8. Iterative Nature of the Process

Although CRISP-DM is presented in six phases, the project did not follow a strictly linear workflow.

For example:

- Initial data inspection identified inconsistent numerical responses.
- Cleaning revealed additional data-quality challenges.
- Extended preprocessing introduced new analytical features.
- Model evaluation highlighted limitations in classification performance.
- Final documentation incorporated the findings and limitations of earlier stages.

This iterative approach allowed the project to evolve as new problems and requirements were identified.

---

## 9. Project Outcomes

The completed workflow demonstrates how Data Science can be used to investigate relationships among student wellness factors.

The project produced:

- A documented preprocessing workflow.
- Descriptive and inferential statistical results.
- Visual representations of observed relationships.
- Data-quality evaluation.
- Mathematical implementations of PCA and LDA.
- Technical reports and reproducibility documentation.

The findings remain exploratory and specific to the collected sample.

---

## 10. Limitations

- The dataset contains 100 self-selected respondents.
- Responses are self-reported and may contain measurement errors.
- The survey is cross-sectional.
- Some physical-activity responses have uncertain measurement units.
- Midpoint conversion and median imputation introduce assumptions.
- Likert-scale responses are ordinal, although some analyses treat them numerically.
- The LDA model has limited classification performance.
- Statistical associations do not establish causal relationships.

The project is non-clinical and must not be used to diagnose or assess individual students' mental-health conditions.

---

## 11. Conclusion

The CRISP-DM framework provided a systematic foundation for the project, connecting problem identification, data understanding, preprocessing, statistical analysis, evaluation, and documentation.

Through this workflow, the project investigated associations among mental, physical, and nutritional wellbeing using self-collected university student data.

The completed work demonstrates practical application of Data Science concepts while recognizing the limitations of the dataset and analytical methods.
