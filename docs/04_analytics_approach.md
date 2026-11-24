# 04 — Analytics Approach

## Project Title

**Association among 3 factors of wellness**

## 1. Overview

This project uses descriptive statistics, exploratory data analysis, hypothesis testing, correlation, regression, Principal Component Analysis (PCA), and Linear Discriminant Analysis (LDA) to investigate associations among mental, physical, and nutritional wellbeing among university students.

The analytical approach is primarily **exploratory and statistical**, supported by mathematical implementations of multivariate techniques.

The study uses 100 self-reported survey responses collected between 14 and 18 August 2026.

---

## 2. Data Preparation

Two stages of preprocessing were performed.

| Stage | Dataset Dimensions | Work Completed |
|---|---|---|
| Original survey | 100 × 22 | Primary data collection |
| Initial cleaning | 100 × 25 | Sleep, entertainment screen time, water intake |
| Extended cleaning | 100 × 42 | Additional lifestyle features, dietary encoding, activity classification |

### Techniques Applied

- Rule-based numerical parsing using regular expressions.
- Standardization of numerical measurements.
- Range midpoint conversion.
- IQR-based outlier treatment for selected variables.
- Median imputation.
- Validation of categorical responses.
- Multi-hot encoding of seven dietary categories.
- Classification of ambiguous physical-activity responses.
- Free-text normalization.

The initial cleaned dataset was used for the main statistical analyses, PCA, LDA, and eight-dimensional data-quality assessment. The extended dataset was separately validated.

---

## 3. Exploratory Data Analysis

EDA was performed to understand the distribution and relationships of the collected variables.

### Descriptive Statistics

The following measures were calculated:

- Mean
- Median
- Standard deviation
- Minimum and maximum
- Frequency distributions
- Percentages

### Selected Results

| Variable | Mean | Standard Deviation |
|---|---:|---:|
| Sleep duration | 5.87 hours | 1.51 |
| Entertainment screen time | 3.78 hours | 1.86 |
| Water intake | 2.79 litres | 1.02 |
| Composite stress score | 15.72 | 4.56 |
| Evening energy | 2.87 | 1.08 |
| Digestive discomfort | 2.35 | 1.12 |

The composite stress score was calculated by summing five 1–5 mental-wellbeing responses, producing a score between 5 and 25. It is an exploratory project-specific index, not a validated clinical scale.

---

## 4. Statistical Hypothesis Testing

Four statistical procedures were implemented at a significance level of 5% (\(\alpha = 0.05\)).

### 4.1 F-Test — Comparison of Variances

**Objective:** Compare entertainment screen-time variances between male and female respondents.

Formula:

\[
F=\frac{s_1^2}{s_2^2}
\]

**Reported results:**

- F-statistic: 1.783
- Degrees of freedom: (56, 42)
- p-value: approximately 0.052

**Interpretation:** The null hypothesis was not rejected at the 5% significance level. The result does not establish that the population variances are identical.

### 4.2 Independent Two-Sample t-Test

**Objective:** Compare mean entertainment screen time between male and female respondents.

The reported analysis used a pooled-variance t-test.

\[
t=\frac{\bar{x}_1-\bar{x}_2}
{s_p\sqrt{\frac{1}{n_1}+\frac{1}{n_2}}}
\]

**Reported results:**

- Male mean: 4.1754 hours
- Female mean: 3.2605 hours
- t-statistic: 2.606
- Degrees of freedom: 98
- p-value: approximately 0.011

**Interpretation:** The sample showed a statistically significant difference in mean entertainment screen time between the two gender groups.

### 4.3 One-Sample Z-Test

**Objective:** Compare average sleep duration against a reference value of 7 hours.

The project used a large-sample Z approximation:

\[
Z=\frac{\bar{x}-\mu_0}{s/\sqrt{n}}
\]

**Reported results:**

- Sample mean: 5.87 hours
- Reference mean: 7 hours
- Absolute test statistic: approximately 7.47
- p-value: less than 0.001

**Interpretation:** The reported sample mean was significantly below the 7-hour reference.

Because the population standard deviation was unknown, the calculation is described as a large-sample approximation rather than an exact population-standard-deviation Z-test.

### 4.4 Chi-Square Test of Independence

**Objective:** Examine the association between gender and meal regularity.

Formula:

\[
\chi^2=\sum\frac{(O-E)^2}{E}
\]

**Reported results:**

- Chi-square statistic: 9.95
- Degrees of freedom: 2
- p-value: approximately 0.007
- Cramér's V: 0.32

**Interpretation:** Gender and meal regularity were statistically associated in the collected sample. This does not establish causation.

---

## 5. Correlation Analysis

Pearson correlation was used to examine linear relationships among selected numerical variables.

\[
r=\frac{\operatorname{Cov}(X,Y)}{s_Xs_Y}
\]

### Selected Findings

| Variable Pair | Correlation |
|---|---:|
| Sleep duration and evening energy | +0.28 |
| Stress score and evening energy | −0.33 |
| Entertainment screen time and stress score | +0.18 |
| Water intake and evening energy | +0.20 |
| Stress score and digestive discomfort | +0.23 |

These correlations indicate weak or modest linear relationships.

Correlation does not establish causation.

---

## 6. Simple Linear Regression

**Objective:** Examine the relationship between sleep duration and evening physical energy.

The regression model was:

\[
\hat{Y}=b_0+b_1X
\]

The fitted equation was:

\[
\hat{Y}=1.697+0.1998X
\]

Where:

- \(X\) represents sleep duration in hours.
- \(\hat{Y}\) represents predicted evening-energy rating.
- \(b_0\) is the intercept.
- \(b_1\) is the slope.

### Results

| Metric | Value |
|---|---:|
| Correlation coefficient | 0.280 |
| Coefficient of determination (R²) | 0.078 |
| Slope | 0.1998 |
| p-value | 0.005 |

**Interpretation:** One additional hour of reported sleep was associated with approximately a 0.20-point increase in predicted evening-energy rating.

The model explained approximately 7.8% of the observed variation in evening energy.

This represents a weak positive association, not a causal relationship.

---

## 7. Data Quality Assessment

The initial cleaned dataset was assessed across eight dimensions:

| Dimension | Assessment |
|---|---|
| Completeness | 99.96% of cells populated |
| Validity | Tested numerical, rating and categorical rules passed |
| Consistency | Parsing and documented transformations checked |
| Uniqueness | No exact duplicate response records detected |
| Accuracy | Self-reported accuracy could not be independently verified |
| Timeliness | August 2026 collection period |
| Integrity | Basic structural checks passed |
| Relevance | Selected analytical variables covered the intended domains |

The extended dataset underwent additional validation for derived variables, dietary indicators, record identities and ambiguous activity measurements.

---

## 8. Principal Component Analysis

### Objective

Reduce the dimensionality of selected numerical wellness variables while preserving as much variance as possible.

### Features

PCA used ten numerical variables:

- Five mental-wellbeing ratings.
- Sleep duration.
- Entertainment screen time.
- Water intake.
- Evening physical energy.
- Digestive discomfort.

### Mathematical Method

**Step 1 — Standardization**

\[
z_{ij}=\frac{x_{ij}-\bar{x}_j}{s_j}
\]

**Step 2 — Covariance Matrix**

\[
C=\frac{Z^TZ}{n-1}
\]

**Step 3 — Eigenvalue Decomposition**

\[
Cv=\lambda v
\]

**Step 4 — Projection**

\[
T=ZW_k
\]

### Results

| Metric | Result |
|---|---:|
| Original features | 10 |
| Variance explained by PC1 | 30.911% |
| Variance explained by first 2 PCs | 44.561% |
| Variance explained by first 3 PCs | 55.930% |
| Components required for at least 90% variance | 8 |
| Variance retained by first 8 PCs | 92.730% |

The mathematical implementation was verified against NumPy and scikit-learn.

PCA was used for dimensionality reduction and exploration, not for predicting individual wellness outcomes.

---

## 9. Linear Discriminant Analysis

### Objective

Investigate whether selected lifestyle variables could distinguish two exploratory stress-frequency categories.

### Target Definition

The `stress_anxious` response was used to define:

- Class 0: Ratings 1–3.
- Class 1: Ratings 4–5.

These are project-defined categories, not clinical labels.

### Predictor Variables

- Sleep duration
- Entertainment screen time
- Water intake
- Evening energy
- Digestive discomfort

### Mathematical Method

LDA was implemented using class means and scatter matrices.

Within-class scatter:

\[
S_W=\sum_c\sum_{x\in c}(x-\mu_c)(x-\mu_c)^T
\]

Between-class scatter:

\[
S_B=\sum_cn_c(\mu_c-\mu)(\mu_c-\mu)^T
\]

The discriminant direction was calculated to maximize the ratio of between-class to within-class variation.

### Evaluation

The dataset was divided into 75 training and 25 testing observations.

Outlier boundaries, imputation values and standardization parameters were fitted using training data and applied to test data.

| Metric | Result |
|---|---:|
| Manual LDA accuracy | 68% |
| scikit-learn accuracy | 68% |
| Prediction agreement | 100% |
| Balanced accuracy | 53.31% |
| Higher-stress class recall | 12.5% |

Confusion matrix:

\[
\begin{bmatrix}
16 & 1\\
7 & 1
\end{bmatrix}
\]

Although overall accuracy was 68%, the model correctly identified only one of eight higher-stress-frequency test observations.

The LDA experiment therefore demonstrated the mathematical method but did not produce a reliable classification model.

---

## 10. Data Visualizations

The project used several visualizations to communicate distributions, group comparisons and associations.

| Visualization | Purpose |
|---|---|
| IQR boxplots | Identify potential outliers |
| Living-arrangement bar chart | Examine sample composition |
| Meal-regularity grouped bar chart | Compare dietary patterns by gender |
| Responses-per-day line chart | Examine survey collection timing |
| Stress-by-academic-year line chart | Compare average stress scores |
| Correlation heatmap | Display pairwise linear relationships |
| Screen-time boxplot | Compare distributions by gender |
| Stress-by-living-arrangement boxplot | Compare stress distributions |
| Regression scatter plot | Visualize sleep–energy association |
| PCA variance plots | Examine explained variance |
| PCA projection plot | Visualize principal-component scores |
| LDA projection histogram | Examine exploratory class separation |

These visualizations support interpretation but do not establish causal relationships.

---

## 11. Evaluation and Limitations

### Main Findings

- Average reported sleep duration was 5.87 hours.
- Male respondents reported higher mean entertainment screen time than female respondents.
- Gender and meal regularity showed a statistical association.
- Sleep duration had a weak positive relationship with evening energy.
- Stress score and evening energy showed a negative correlation.
- PCA demonstrated dimensionality reduction.
- LDA showed limited higher-stress-frequency classification performance.

### Limitations

- The sample contained only 100 self-selected respondents.
- Survey measurements were self-reported.
- The study was cross-sectional.
- Some physical-activity measurements had ambiguous units.
- Median imputation and midpoint conversion introduced assumptions.
- Some analyses treated ordinal ratings numerically.
- The exploratory LDA model was not suitable for individual screening.

The findings are limited to the collected sample and should not be interpreted as medical or causal conclusions.

---

## 12. Conclusion

The project combined exploratory data analysis, statistical hypothesis testing, correlation, regression, data-quality assessment, PCA and LDA to investigate associations among mental, physical and nutritional wellbeing.

The mathematical implementations and statistical evaluations demonstrated practical application of Data Science concepts.

The results identified several weak or modest associations within the collected sample while highlighting the importance of data quality, preprocessing decisions and cautious interpretation.

The project is intended for academic research and learning rather than clinical assessment or individual wellness prediction.
