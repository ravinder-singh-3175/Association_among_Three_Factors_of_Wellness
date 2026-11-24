# Association among 3 factors of wellness

### Fundamentals of Data Science | CSDS2002P

**A Data Science Study of Mental, Physical, and Nutritional Wellbeing Among University Students**

This project investigates associations among three interconnected dimensions of student wellness: **mental wellbeing, physical wellbeing, and nutritional wellbeing**.

Using primary survey data collected from university students, the project applies data cleaning, exploratory data analysis, statistical hypothesis testing, regression, data quality assessment, Principal Component Analysis (PCA), and Linear Discriminant Analysis (LDA).

The objective is to understand patterns and statistical relationships within the collected sample, rather than develop a clinical diagnostic or medical recommendation system.

---

## 1. Project Overview

University students frequently experience academic pressure, irregular sleep patterns, prolonged screen exposure, inconsistent dietary habits, and varying levels of physical activity.

This project examines how these factors are associated with self-reported stress, concentration, motivation, physical energy, and other indicators of wellbeing.

### Three Dimensions of Wellness

**Mental Wellbeing**
- Stress and anxiety frequency
- Racing thoughts and repetitive worry
- Concentration difficulties
- Low motivation and energy
- Irritability and mental exhaustion

**Physical Wellbeing**
- Sleep duration
- Walking activity and step counts
- Exercise frequency
- Consecutive sitting duration
- Evening physical energy
- Academic and entertainment screen time

**Nutritional Wellbeing**
- Daily water intake
- Meal regularity
- Dietary food categories
- Digestive discomfort

These dimensions are investigated using self-reported survey measurements. The study does not establish causal relationships.

---

## 2. Problem Statement

**How are mental, physical, and nutritional wellbeing factors associated among university students, and which lifestyle characteristics are related to higher reported stress and lower physical energy?**

The project uses statistical analysis to investigate these associations within the collected student sample.

---

## 3. Project Objectives

1. Collect and understand primary survey data related to student wellness.
2. Identify variable types, measurement scales, and data quality issues.
3. Clean and standardize mixed-format numerical and categorical responses.
4. Perform exploratory data analysis to identify patterns and distributions.
5. Apply descriptive statistics and statistical hypothesis testing.
6. Examine relationships using correlation and simple linear regression.
7. Assess data quality across eight dimensions.
8. Implement PCA and LDA using mathematical methods and verify their results.
9. Interpret findings while acknowledging sampling, measurement, and analytical limitations.

---

## 4. Dataset Description

The dataset was collected using a Google Form distributed among university students.

| Attribute | Description |
|---|---|
| Data source | Primary online survey |
| Target population | University students |
| Responses | 100 |
| Original variables | 22 |
| Collection period | 14–18 August 2026 |
| Data type | Cross-sectional, self-reported |
| Initial cleaned dataset | 100 rows × 25 columns |
| Extended cleaned dataset | 100 rows × 42 columns |

### Data Preparation

The initial preprocessing stage standardized sleep duration, entertainment screen time, and water intake.

The extended cleaning stage additionally processed academic screen time, sitting duration, physical activity responses, dietary selections, and free-text factors.

The extended dataset preserves original response fields alongside derived variables for traceability.

Ambiguous physical-activity measurements are retained separately rather than being assigned unsupported units.

---

## 5. Methodology

The project follows the **CRISP-DM (Cross-Industry Standard Process for Data Mining)** framework.

| Phase | Implementation |
|---|---|
| Business Understanding | Define the student wellness research problem |
| Data Understanding | Inspect survey variables, data types, and distributions |
| Data Preparation | Clean, standardize, validate, and derive features |
| Modelling | Apply statistical tests, regression, PCA, and LDA |
| Evaluation | Interpret findings and assess model limitations |
| Deployment / Delivery | Prepare reports, documentation, and reproducible project files |

---

## 6. Techniques Implemented

### Data Cleaning and Preprocessing

- Rule-based numerical parsing
- Unit normalization
- Range midpoint conversion
- IQR-based outlier treatment for selected initial numerical variables
- Median imputation
- Missing-value analysis
- Categorical validation
- Multi-hot encoding of seven dietary categories
- Activity measurement classification and uncertainty flags
- Free-text normalization

### Exploratory Data Analysis

- Frequency distributions
- Descriptive statistics
- Group comparisons
- Boxplots and bar charts
- Correlation heatmaps
- Scatter plots and time-based response visualizations

### Statistical Hypothesis Testing

Four statistical procedures were implemented:

| Test | Purpose |
|---|---|
| F-test | Compare entertainment screen-time variances by gender |
| Independent two-sample t-test | Compare mean entertainment screen time by gender |
| One-sample Z-test | Compare mean sleep duration with a 7-hour reference |
| Chi-square test of independence | Examine association between gender and meal regularity |

### Regression Analysis

Simple linear regression was used to examine the association between sleep duration and evening physical energy.

### Data Quality Assessment

Eight dimensions were assessed:

1. Completeness
2. Validity
3. Consistency
4. Uniqueness
5. Accuracy
6. Timeliness
7. Integrity
8. Relevance

The assessment was performed on the initial cleaned dataset. The extended dataset was separately subjected to additional structural and transformation checks.

### Principal Component Analysis (PCA)

PCA was implemented using mathematical calculations involving standardization, covariance matrices, eigenvalues, eigenvectors, and projection.

The results were verified against scikit-learn.

### Linear Discriminant Analysis (LDA)

LDA was implemented using class means, within-class scatter, between-class scatter, and linear discriminant calculations.

An exploratory two-class stress-frequency grouping was used. The implementation was compared with scikit-learn and evaluated using held-out test data.

---

## 7. Key Results

| Analysis | Result |
|---|---|
| Average sleep duration | 5.87 hours |
| Average entertainment screen time | 3.78 hours |
| Average water intake | 2.79 litres |
| Sleep–evening energy correlation | r = 0.28 |
| Stress–evening energy correlation | r = −0.33 |
| Simple linear regression R² | 0.078 |
| Initial cleaned dataset completeness | 99.96% |
| PCA variance retained using 8 components | 92.73% |
| LDA test accuracy | 68% |
| LDA balanced accuracy | 53.31% |

**Interpretation:** The observed associations are generally weak or modest. PCA successfully demonstrated dimensionality reduction, while LDA showed limited ability to distinguish the higher-stress-frequency class.

These results are exploratory and should not be interpreted as evidence of causation or clinical prediction.

---

## 8. Technologies Used

- Python
- pandas
- NumPy
- Matplotlib
- SciPy
- scikit-learn
- openpyxl
- Jupyter Notebook
- Visual Studio Code
- Microsoft Excel
- Git and GitHub
- LaTeX / Overleaf for technical reporting

---

## 9. Project Documentation

The repository is organized to maintain the original survey information, preprocessing work, statistical analysis, technical reports, and academic project documentation.

Key project artifacts include:

- Original survey dataset and variable classification
- Initial data-cleaning and statistical-analysis notebook
- Data Quality Assessment, PCA, and LDA notebook
- Extended data-cleaning notebook
- Extended cleaned dataset and audit
- Final project report
- Technical documentation
- Supporting reports for extended cleaning and multivariate analysis

Some artifacts may be retained locally or shared separately where survey-data privacy requires restricted access.

---

## 10. Limitations

- The dataset contains 100 self-selected respondents.
- Survey responses are self-reported and may contain measurement or recall errors.
- The dataset represents a cross-sectional snapshot.
- Ambiguous activity measurements cannot always be assigned reliable units.
- Midpoint conversion and median imputation introduce assumptions.
- Likert-scale responses are ordinal, although some analyses use numerical approximations.
- Statistical associations do not establish causation.
- The LDA classifier is exploratory and is not suitable for individual mental-health screening.

---

## 11. Future Scope

Potential future improvements include:

- Collecting a larger and more representative sample.
- Improving survey questions through validated numerical inputs and clearly specified units.
- Examining additional relationships among dietary habits, physical activity, and mental wellbeing.
- Exploring additional multivariate statistical techniques.
- Improving the reliability and reproducibility of preprocessing.
- Conducting longitudinal studies to investigate changes in student wellness over time.

These are proposed improvements and are not presented as completed implementations.

---

## 12. Project Team

**Jasika Garg**  
**Ravinder Singh**

B.Tech Computer Science and Engineering — Data Science  
School of Computer Science  
UPES, Dehradun

**Course:** Fundamentals of Data Science (CSDS2002P)  
**Faculty:** Dr. Virender Kadyan  
**Academic Year:** 2026

---

## 13. Academic Disclaimer

This project was developed for academic research and learning purposes.

It is a non-clinical study based on self-reported survey data. The findings must not be used to diagnose mental-health conditions, assess individual medical risk, or make personalized clinical recommendations.
