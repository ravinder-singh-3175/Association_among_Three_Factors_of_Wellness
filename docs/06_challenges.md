# 06 — Project Challenges and Solutions

## Project Title

**Association among 3 factors of wellness**

## 1. Introduction

During the development of this project, several challenges were encountered in data collection, preprocessing, statistical analysis, feature engineering, and model evaluation.

These challenges arose primarily because the dataset contained self-reported survey responses with inconsistent numerical formats, ambiguous measurement units, categorical variables, and free-text answers.

This document records the major challenges, the methods used to address them, and the limitations that remain.

---

## 2. Data Collection Challenges

### Challenge 1 — Limited Sample Size

The survey collected 100 responses from university students.

**Problem:** The sample may not adequately represent the broader university student population.

**Approach:** The study was treated as exploratory and cross-sectional. Findings were interpreted as associations within the collected sample.

**Limitation:** Results cannot automatically be generalized to all university students.

### Challenge 2 — Self-Reported Measurements

Students reported their own sleep duration, screen time, physical activity, nutrition habits, and mental-wellbeing experiences.

**Problem:** Responses may contain recall errors, estimation errors, or subjective interpretations.

**Approach:** Data validity and consistency checks were performed where possible.

**Limitation:** Actual response accuracy could not be independently verified.

---

## 3. Data Cleaning Challenges

### Challenge 3 — Inconsistent Numerical Formats

Several survey questions allowed students to enter numerical information as free text.

Examples included:

- `7 hr`
- `8-9hrs`
- `4 hours 30 mins`
- `2-3 litres`

**Problem:** These values could not be used directly for numerical analysis.

**Solution:** Rule-based parsing was implemented using Python and regular expressions.

Numerical values were extracted, units were standardized, and ranges were converted into midpoint estimates.

For a range with endpoints \(a\) and \(b\):

\[
x_{\text{mid}}=\frac{a+b}{2}
\]

**Limitation:** Midpoint conversion loses information about the original range.

### Challenge 4 — Missing and Unusable Responses

Some respondents entered values such as:

- `No idea`
- `Don't know`
- `Not specific time`
- Unrelated text

**Problem:** Such responses could not always be interpreted as valid numerical measurements.

**Solution:** Unusable values were represented as missing values (`NaN`).

Median imputation was applied to selected variables during initial cleaning.

During extended cleaning, uncertain academic screen-time and sitting-duration values were preserved as missing rather than automatically imputed.

### Challenge 5 — Outlier Detection and Treatment

Some numerical responses were unusually distant from the majority of observations.

**Problem:** Extreme values could influence descriptive statistics and subsequent analysis.

**Solution:** The initial cleaning stage applied the Interquartile Range (IQR) method.

\[
IQR=Q_3-Q_1
\]

\[
\text{Lower Fence}=Q_1-1.5(IQR)
\]

\[
\text{Upper Fence}=Q_3+1.5(IQR)
\]

The method flagged:

- One sleep-duration value of 1 hour.
- Three water-intake values of 6, 6, and 8 litres.

These values were replaced with missing values and subsequently median-imputed.

**Limitation:** Statistical outliers are not necessarily incorrect measurements.

During extended cleaning, unusual values were generally retained or flagged rather than automatically replaced.

---

## 4. Physical Activity Challenges

### Challenge 6 — Mixed Measurement Units

The physical-activity question accepted responses in different units.

Examples:

- `10000 steps`
- `30 minutes`
- `5 km`
- `8000`
- `60`

**Problem:** Step counts, walking duration, and walking distance represent different measurements and cannot be combined directly into one numerical variable.

**Solution:** Three separate derived columns were created:

- `daily_steps`
- `walking_minutes`
- `walking_km`

Responses with explicit units were processed separately from those with missing or ambiguous units.

### Challenge 7 — Ambiguous Activity Responses

Many respondents entered numbers without specifying whether they represented steps or minutes.

**Problem:** Automatically assigning units could introduce incorrect measurements.

**Solution:** Additional fields were created:

- `activity_inferred_value`
- `activity_inferred_unit`
- `activity_status`

The inference process classified responses into probable steps, probable minutes, unknown, and ambiguous categories.

### Activity Classification Results

| Classification | Responses |
|---|---:|
| Confirmed steps | 22 |
| Confirmed walking minutes | 21 |
| Confirmed distance | 1 |
| Probable steps | 30 |
| Probable minutes | 16 |
| Unknown | 8 |
| Ambiguous | 2 |
| **Total** | **100** |

Here, *confirmed* indicates that the parser recognized an explicit measurement unit, not that the respondent's actual activity was independently verified.

### Challenge 8 — Special Cases and Parsing Errors

One response, `10thoudand steps`, was initially interpreted incorrectly as 10 steps.

**Solution:** The identified spelling error was corrected to 10,000 steps.

Two responses containing `10k+` were flagged as lower-bound measurements rather than treated as exact step counts.

**Remaining limitation:** Some activity responses contain uncertain units, approximate ranges, or unusual values. These were retained with their limitations documented.

---

## 5. Dietary Data Challenges

### Challenge 9 — Multi-Select Categorical Responses

The dietary question allowed students to select multiple food categories.

**Problem:** A single response could contain several categories, making direct numerical analysis difficult.

**Initial issue:** Splitting responses at every comma incorrectly divided category descriptions containing commas inside parentheses.

For example:

`High-Protein items (Eggs, Meat, Paneer, Pulses)`

**Solution:** The original dietary categories were identified and encoded using seven binary indicator columns.

### Dietary Categories

| Category | Students |
|---|---:|
| Carbohydrate-rich foods | 60 |
| Dietary supplements | 18 |
| High-protein foods | 32 |
| Balanced home/mess meals | 73 |
| Fast food/junk food | 44 |
| Fruits/vegetables | 33 |
| Sugary/caffeinated drinks | 29 |

**Encoding method:** Multi-hot encoding.

Each feature contains:

- `1` — Category selected.
- `0` — Category not selected.

Multiple features can have a value of 1 for the same respondent.

The corrected seven-category encoding was verified to contain only binary values.

---

## 6. Free-Text Processing Challenges

### Challenge 10 — Unstructured Emotional-Wellbeing Responses

The survey included an open-ended question asking students to describe factors affecting their emotional wellbeing.

**Problem:** Responses contained varied wording, capitalization, and spacing.

**Solution:** Basic text normalization was performed using:

- Lowercase conversion.
- Leading and trailing whitespace removal.
- Repeated whitespace normalization.

The original text was preserved.

**Limitation:** Text normalization does not perform sentiment analysis or automatically extract reliable psychological categories.

---

## 7. Statistical Analysis Challenges

### Challenge 11 — Selecting Appropriate Statistical Tests

Different research questions involved different types of variables.

**Problem:** Applying an inappropriate statistical test could produce misleading conclusions.

**Approach:** Four procedures were selected according to their research objectives:

| Test | Application |
|---|---|
| F-test | Comparison of entertainment screen-time variances by gender |
| Independent two-sample t-test | Comparison of mean entertainment screen time by gender |
| One-sample Z-test approximation | Comparison of mean sleep duration with 7 hours |
| Chi-square test | Association between gender and meal regularity |

The reported tests were interpreted at a 5% significance level.

**Limitation:** Statistical conclusions depend on assumptions such as independence, distributional suitability, and measurement properties.

### Challenge 12 — Correlation Versus Causation

The analysis identified associations among selected wellness variables.

**Problem:** Correlations may be incorrectly interpreted as causal relationships.

**Approach:** Findings were described as statistical associations.

For example, the correlation between sleep duration and evening energy was approximately \(r=0.28\).

**Limitation:** The cross-sectional survey design does not establish whether one variable causes changes in another.

---

## 8. Data Quality Assessment Challenges

### Challenge 13 — Defining and Measuring Data Quality

Data quality cannot be determined solely by counting missing values.

**Solution:** Eight dimensions were assessed:

1. Completeness
2. Validity
3. Consistency
4. Uniqueness
5. Accuracy
6. Timeliness
7. Integrity
8. Relevance

The initial cleaned dataset had approximately 99.96% populated cells.

However, this result did not establish that all responses were accurate or that every collected variable was fully standardized.

**Limitation:** Some dimensions, particularly the accuracy of self-reported measurements, could not be independently verified.

---

## 9. PCA Implementation Challenges

### Challenge 14 — Different Measurement Scales

The selected PCA features included variables measured on different numerical scales.

**Problem:** Features with larger numerical variance could disproportionately influence the principal components.

**Solution:** The ten selected features were standardized before PCA.

The mathematical implementation included covariance calculation, eigenvalue decomposition, explained variance, and projection.

**Result:** Eight principal components retained approximately 92.73% of total variance.

The results were verified against NumPy and scikit-learn.

**Limitation:** Retaining variance does not guarantee improved predictive performance or clinical interpretability.

---

## 10. LDA Implementation Challenges

### Challenge 15 — Defining Classes and Avoiding Data Leakage

LDA requires predefined class labels.

**Problem:** The survey did not contain independently validated clinical stress categories.

**Solution:** Two exploratory stress-frequency classes were created using the `stress_anxious` response:

- Class 0: Ratings 1–3.
- Class 1: Ratings 4–5.

The target-defining variable was excluded from the predictor features.

Preprocessing parameters were fitted using training data and applied to the test set.

### Challenge 16 — Imbalanced Classification Performance

The LDA model achieved:

| Metric | Result |
|---|---:|
| Test accuracy | 68% |
| Balanced accuracy | 53.31% |
| Higher-stress recall | 12.5% |
| Manual vs scikit-learn agreement | 100% |

**Problem:** Overall accuracy concealed weak detection of the higher-stress-frequency class.

Only one of eight higher-stress test observations was correctly classified.

**Conclusion:** LDA was successfully demonstrated as a mathematical and computational method, but its predictive performance was insufficient for individual screening.

---

## 11. Documentation and Reproducibility Challenges

### Challenge 17 — Managing Multiple Dataset Versions

The project evolved through several stages.

| Dataset | Dimensions |
|---|---|
| Original survey | 100 × 22 |
| Initial cleaned dataset | 100 × 25 |
| Extended cleaned dataset | 100 × 42 |

**Problem:** Multiple versions could create confusion about which data were used for different analyses.

**Solution:** Dataset versions were documented separately, and original response columns were retained for traceability.

The initial cleaned dataset was used for the principal statistical analyses, PCA, LDA, and eight-dimensional data-quality assessment.

The extended dataset was subjected to additional validation.

### Challenge 18 — Reproducibility and Project Organization

**Problem:** The project involved multiple notebooks, datasets, reports, and supporting files.

**Approach:**

- Organized project documentation.
- Preserved original datasets.
- Used GitHub for version control.
- Maintained separate notebooks for different analytical tasks.
- Compared mathematical implementations with library results.
- Documented assumptions, results, and limitations.

---

## 12. Lessons Learned

The project demonstrated several important principles:

1. Data cleaning requires understanding the meaning of values, not just converting text into numbers.
2. Missing values, invalid responses, and outliers are different problems.
3. Preserving raw data supports traceability and reproducibility.
4. Multi-select categorical responses require appropriate encoding.
5. Ambiguous measurements should not be silently converted into exact values.
6. Statistical methods must match the variables and research questions.
7. Mathematical implementations help verify understanding of algorithms.
8. Model accuracy alone is not sufficient for evaluating classification performance.
9. Correlation does not establish causation.
10. Documentation and validation are essential parts of a Data Science workflow.

---

## 13. Conclusion

The project encountered challenges involving inconsistent survey responses, mixed measurement units, outliers, categorical encoding, statistical assumptions, and multivariate analysis.

These challenges were addressed through rule-based preprocessing, targeted outlier treatment, feature engineering, data-quality checks, mathematical implementations, and careful interpretation.

Some limitations remain, particularly those related to self-reported measurements, sample representativeness, ambiguous activity units, and LDA classification performance.

The completed work demonstrates how practical Data Science methods can be applied to investigate associations among mental, physical, and nutritional wellbeing in a university student sample.
