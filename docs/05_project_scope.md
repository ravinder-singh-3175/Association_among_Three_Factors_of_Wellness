# 05 — Project Scope

## Project Title

**Association among 3 factors of wellness**

## 1. Overview

This project investigates statistical associations among three dimensions of university student wellness:

1. Mental wellbeing
2. Physical wellbeing
3. Nutritional wellbeing

The study uses primary survey data and Data Science techniques to examine patterns, relationships, and differences among selected wellness and lifestyle variables.

The project is **exploratory, cross-sectional, and non-clinical**.

---

## 2. Scope of Data Collection

The study uses 100 self-reported responses collected from university students between 14 and 18 August 2026.

The original dataset contains 22 survey columns, including demographic, mental-wellness, physical-activity, nutritional, and lifestyle variables.

### Included Variables

**Mental Wellbeing**
- Stress and anxiety frequency
- Racing thoughts
- Concentration difficulties
- Low motivation
- Irritability and mental exhaustion

**Physical Wellbeing**
- Sleep duration
- Academic and entertainment screen time
- Walking activity and step count
- Exercise frequency
- Sitting duration
- Evening physical energy

**Nutritional Wellbeing**
- Water intake
- Meal regularity
- Dietary food categories
- Digestive discomfort

**Supporting Variables**
- Gender
- Academic year
- Living arrangement
- Survey submission timestamp

---

## 3. Scope of Data Preparation

The project includes two stages of data cleaning.

| Stage | Dataset | Work Completed |
|---|---|---|
| Initial cleaning | 100 × 25 | Standardization of sleep, entertainment screen time, and water intake |
| Extended cleaning | 100 × 42 | Additional lifestyle processing, activity classification, dietary encoding, and text normalization |

### Included Preprocessing Operations

- Data inspection and variable classification
- Missing-value identification
- Duplicate detection
- Rule-based numerical parsing
- Unit normalization
- Range midpoint conversion
- IQR-based outlier treatment for selected variables
- Median imputation
- Categorical validation
- Dietary multi-hot encoding
- Activity inference and uncertainty classification
- Free-text normalization
- Data-integrity and transformation checks

The original responses were retained for traceability.

Ambiguous activity measurements were documented rather than automatically assigned unsupported units.

---

## 4. Scope of Statistical Analysis

The project includes:

### Exploratory Data Analysis

- Frequency distributions
- Descriptive statistics
- Group comparisons
- Statistical visualizations

### Hypothesis Testing

- F-test for comparing entertainment screen-time variances by gender
- Independent two-sample t-test for comparing entertainment screen-time means by gender
- One-sample Z-test approximation comparing mean sleep duration with 7 hours
- Chi-square test examining gender and meal regularity

### Correlation and Regression

- Pearson correlation analysis
- Simple linear regression between sleep duration and evening physical energy

### Data Quality Assessment

Eight dimensions were assessed using the initial cleaned dataset:

1. Completeness
2. Validity
3. Consistency
4. Uniqueness
5. Accuracy
6. Timeliness
7. Integrity
8. Relevance

Additional validation was conducted during extended cleaning.

### Multivariate Analysis

**Principal Component Analysis (PCA)**

Applied to ten numerical features to investigate dimensionality reduction.

Eight principal components retained approximately 92.73% of total variance.

**Linear Discriminant Analysis (LDA)**

Implemented as an exploratory two-class classification experiment using selected lifestyle variables.

The model achieved 68% test accuracy but showed weak detection of the higher-stress-frequency class.

---

## 5. Scope of Implementation

The project was implemented using Python and supporting Data Science libraries.

The work includes:

- Data processing and feature engineering
- Statistical computations
- Mathematical PCA and LDA implementations
- Library-based verification
- Visualization
- Notebook-based documentation
- Academic reports
- GitHub version control

The project follows the CRISP-DM framework.

For this academic submission, the final delivery consists of analytical code, processed data, results, and documentation.

---

## 6. Out-of-Scope Components

The following are not part of the completed project:

- Clinical diagnosis of mental-health conditions
- Personalized medical or nutritional prescriptions
- Real-time student wellness monitoring
- Production web or mobile application development
- Wearable-device integration
- Automated clinical risk assessment
- Causal inference from the survey
- Longitudinal tracking of individual students
- Deployment of a production prediction service
- K-Means clustering or other unimplemented algorithms

These components should not be described as completed features.

---

## 7. Project Deliverables

The project deliverables include:

1. Original survey dataset and classification records.
2. Initial cleaned dataset and statistical-analysis code.
3. Extended cleaned dataset and cleaning audit.
4. Data Quality Assessment, PCA, and LDA notebook.
5. Extended data-cleaning notebook.
6. Statistical visualizations.
7. Final project report.
8. Technical project documentation.
9. Supporting technical reports.
10. GitHub repository containing approved project artifacts.

Row-level survey data should only be published where sharing is authorized and appropriate.

---

## 8. Limitations

### Sampling Limitations

The sample contains 100 self-selected respondents and may not represent the wider university student population.

### Measurement Limitations

Survey responses are self-reported and may contain recall errors, inaccurate estimates, or ambiguous measurement units.

### Data Processing Limitations

Range midpoint conversion, outlier treatment, and median imputation introduce assumptions.

Some physical-activity responses remain uncertain and are not directly comparable.

### Analytical Limitations

The study is cross-sectional and supports association rather than causation.

Some ordinal ratings were treated numerically for exploratory analysis.

The LDA classifier demonstrated limited predictive performance.

---

## 9. Future Scope

Potential future extensions include:

- Collecting a larger and more representative dataset.
- Improving survey design and input validation.
- Separating step counts, walking duration, and walking distance into distinct survey questions.
- Investigating additional associations among dietary and physical-activity variables.
- Exploring further multivariate techniques.
- Collecting longitudinal data.
- Improving model evaluation and preprocessing reproducibility.

These are future possibilities, not completed implementations.

---

## 10. Conclusion

The scope of **Association among 3 factors of wellness** is limited to investigating statistical relationships among mental, physical, and nutritional wellbeing using self-reported university student data.

The project demonstrates practical applications of data collection, preprocessing, exploratory analysis, statistical testing, regression, data quality assessment, PCA, and LDA.

Its findings describe patterns within the collected sample and should not be interpreted as causal or clinical conclusions.
