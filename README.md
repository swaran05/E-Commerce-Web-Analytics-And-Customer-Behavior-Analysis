# E-Commerce Web Analytics and Customer Behavior Analysis

**An end-to-end data analytics project using Python, Tableau, and statistical analysis to understand online shopping behavior and purchasing patterns.**

[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Data%20Analysis-Pandas-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Tableau](https://img.shields.io/badge/Visualization-Tableau-E97627?logo=tableau&logoColor=white)](https://www.tableau.com/)
[![Status](https://img.shields.io/badge/Project-Analytics%20%26%20EDA-success)]()

---

## Table of Contents

- [Project Overview](#project-overview)
- [Problem Statement](#problem-statement)
- [Project Objectives](#project-objectives)
- [Dataset Description](#dataset-description)
- [Technology Stack](#technology-stack)
- [Project Workflow](#project-workflow)
- [Data Preprocessing](#data-preprocessing)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Tableau Dashboard](#tableau-dashboard)
- [Statistical Analysis](#statistical-analysis)
- [Key Findings](#key-findings)
- [Business Implications](#business-implications)
- [Project Structure](#project-structure)
- [Installation and Setup](#installation-and-setup)
- [How to Run the Analysis](#how-to-run-the-analysis)
- [Limitations](#limitations)
- [Future Enhancements](#future-enhancements)
- [Conclusion](#conclusion)
- [Dataset Reference](#dataset-reference)
- [Author](#author)

---

## Project Overview

E-commerce websites generate valuable data about browsing activity, page engagement, visitor categories, and purchasing outcomes. Analyzing this information helps businesses understand how customers interact with their websites and identify patterns associated with successful purchases.

**E-Commerce Web Analytics and Customer Behavior Analysis** is a data analytics project that explores online shopping sessions using the Online Shoppers Purchasing Intention dataset.

The project combines Python-based data preprocessing, exploratory data analysis (EDA), interactive Tableau dashboards, and statistical hypothesis testing to investigate relationships between browsing behavior and revenue generation.

The analysis focuses on session-level data, including page views, recorded browsing durations, bounce rates, exit rates, visitor types, monthly traffic, and the revenue outcome of each session.

### Project at a Glance

| Component | Description |
|---|---|
| Project domain | E-Commerce and Web Analytics |
| Dataset | Online Shoppers Purchasing Intention |
| Original dataset | 12,330 sessions and 18 attributes |
| Cleaned dataset | 12,205 sessions after duplicate removal |
| Programming language | Python |
| Data manipulation | Pandas and NumPy |
| Visualization | Tableau |
| Statistical analysis | SciPy |
| Analysis methods | Correlation, chi-square, group comparison, and hypothesis testing |

## Problem Statement

Online shopping websites receive many visitors, but not every session results in a purchase. Understanding the differences between revenue-generating and non-revenue-generating sessions can help businesses evaluate website engagement and identify areas for further investigation.

The central problem addressed by this project is:

> How are online shopping session characteristics, visitor categories, and browsing engagement associated with purchasing outcomes?

The project investigates these questions using descriptive statistics, visual analytics, and statistical tests. It aims to convert raw session data into understandable findings rather than relying solely on traffic counts or visual trends.

## Project Objectives

The primary objectives are:

1. Inspect and preprocess the online shopping dataset.
2. Identify and remove duplicate records.
3. Create derived variables for total page views, recorded duration, and conversion.
4. Analyze traffic patterns across months.
5. Compare conversion rates across visitor categories and weekend status.
6. Visualize engagement patterns using Tableau.
7. Measure relationships between numerical engagement variables using correlation analysis.
8. Test associations between categorical variables using the chi-square test.
9. Compare revenue and non-revenue session distributions using the Mann–Whitney U test.
10. Interpret the findings and identify possible directions for future analysis.

## Dataset Description

The project uses the **Online Shoppers Purchasing Intention Dataset**, available from the UCI Machine Learning Repository.

- Original observations: 12,330 sessions
- Original attributes: 18
- Duplicate records removed: 125
- Cleaned observations: 12,205
- Missing values: None detected in the inspected original dataset

Each row represents a shopping session. The dataset is session-level data; it does not provide a complete, event-by-event sequence of clicks for every user.

### Important Features

| Feature | Description |
|---|---|
| `Administrative` | Number of administrative pages visited |
| `Administrative_Duration` | Recorded duration associated with administrative pages |
| `Informational` | Number of informational pages visited |
| `Informational_Duration` | Recorded duration associated with informational pages |
| `ProductRelated` | Number of product-related pages visited |
| `ProductRelated_Duration` | Recorded duration associated with product-related pages |
| `BounceRates` | Bounce-rate measure |
| `ExitRates` | Exit-rate measure |
| `PageValues` | Page-value metric associated with the purchasing process |
| `SpecialDay` | Measure of proximity to a special day |
| `Month` | Month associated with the session |
| `OperatingSystems` | Operating system category |
| `Browser` | Browser category |
| `Region` | Region category |
| `TrafficType` | Encoded traffic category |
| `VisitorType` | New, returning, or other visitor category |
| `Weekend` | Whether the session occurred on a weekend |
| `Revenue` | Whether the session generated revenue |

### Derived Features

The project creates additional variables to simplify analysis.

**1. TotalPages**

```python
df_clean["TotalPages"] = (
    df_clean["Administrative"]
    + df_clean["Informational"]
    + df_clean["ProductRelated"]
)
```

This combines the three page-count variables into a single session-level page-view measure.

**2. TotalDuration**

```python
df_clean["TotalDuration"] = (
    df_clean["Administrative_Duration"]
    + df_clean["Informational_Duration"]
    + df_clean["ProductRelated_Duration"]
)
```

This combines the recorded durations across the three page categories.

**3. Converted**

```python
df_clean["Converted"] = df_clean["Revenue"].astype(int)
```

This converts the Boolean revenue outcome into a numerical indicator:

- `True` becomes `1`
- `False` becomes `0`

**4. PagesPerSession**

A duplicate feature was initially created using `TotalPages`. Because it contains the same values, `TotalPages` is the preferred feature for analysis.

## Technology Stack

| Technology | Purpose |
|---|---|
| Python | Data preprocessing and analysis |
| Pandas | Data loading, cleaning, grouping, and manipulation |
| NumPy | Numerical operations |
| SciPy | Correlation and statistical hypothesis testing |
| Matplotlib | Data visualization |
| Seaborn | Correlation heatmaps and statistical visualization |
| Tableau Desktop / Tableau Public | Interactive dashboards |
| Jupyter Notebook / Google Colab | Developing and executing Python analysis |
| GitHub | Version control and project documentation |

## Project Workflow

The project follows a structured analytics workflow.

```text
Raw Dataset
    |
    v
Data Inspection
    |
    v
Data Cleaning
    |
    v
Feature Engineering
    |
    v
Exploratory Data Analysis
    |
    +-----------------------+
    |                       |
    v                       v
Tableau Dashboards     Statistical Analysis
    |                       |
    +-----------+-----------+
                |
                v
       Findings and Interpretation
                |
                v
       Future Enhancements
```

### Phase 1: Data Inspection

The dataset is loaded into a pandas DataFrame. Its dimensions, column names, data types, missing values, duplicate records, and descriptive statistics are inspected.

### Phase 2: Data Preprocessing

Duplicate records are removed, and the data is checked for consistency. Additional analytical variables are created for page views, duration, and conversion.

### Phase 3: Exploratory Data Analysis

Numerical and categorical variables are analyzed to understand session distributions, monthly traffic, visitor types, revenue outcomes, and engagement patterns.

### Phase 4: Tableau Visualization

The cleaned dataset is connected to Tableau to build KPI cards, bar charts, monthly comparisons, and scatter plots.

### Phase 5: Statistical Analysis

Correlation, chi-square, and Mann–Whitney U tests are used to investigate relationships and differences identified during exploratory analysis.

### Phase 6: Interpretation

The results are interpreted in terms of statistical evidence and possible business relevance, while recognizing that observational data does not establish causation.

## Data Preprocessing

The following preprocessing steps were performed:

1. Loaded the original CSV file using pandas.
2. Inspected the dataset dimensions and column names.
3. Checked data types and non-null counts.
4. Checked for missing values.
5. Identified 125 duplicate rows.
6. Removed duplicate records using `drop_duplicates()`.
7. Created `TotalPages`, `TotalDuration`, and `Converted`.
8. Exported the cleaned data to CSV for use in Tableau.

### Cleaning Summary

| Metric | Result |
|---|---:|
| Original rows | 12,330 |
| Duplicate rows removed | 125 |
| Cleaned rows | 12,205 |
| Missing values detected | 0 |
| Duplicate rows remaining | 0 |

The cleaned dataset is exported using:

```python
df_clean.to_csv("ecommerce_cleaned.csv", index=False)
```

## Exploratory Data Analysis

Exploratory data analysis helps summarize the dataset and identify patterns before performing statistical tests.

### 1. Session and Revenue Overview

The cleaned dataset contains:

- Total sessions: 12,205
- Revenue sessions: 1,908
- Non-revenue sessions: 10,297
- Overall session conversion rate: approximately 15.63%

The conversion rate is calculated as:

\[
\text{Conversion Rate} =
\frac{\text{Revenue Sessions}}{\text{Total Sessions}}
\times 100
\]

### 2. Monthly Traffic Analysis

The largest monthly session counts observed in the cleaned dataset were:

| Month | Sessions |
|---|---:|
| May | 3,329 |
| November | 2,982 |
| March | 1,860 |
| December | 1,706 |

May had the highest session volume among the listed months.

### 3. Visitor Type Analysis

The cleaned dataset contains:

| Visitor Type | Sessions |
|---|---:|
| Returning Visitor | 10,431 |
| New Visitor | 1,693 |
| Other | 81 |

The conversion rates calculated from the cleaned dataset were approximately:

| Visitor Type | Conversion Rate |
|---|---:|
| New Visitor | 24.91% |
| Other | 18.82% |
| Returning Visitor | 13.93% |

New visitors had the highest observed conversion rate among these categories. This is a descriptive result for the analyzed dataset and should not be interpreted as a causal relationship.

### 4. Weekend vs. Weekday

The analysis compares session conversion rates across weekend and weekday categories.

Previously calculated rates were approximately 17.45% for weekends and 15.08% for weekdays. These values should be recalculated from the cleaned dataset before final publication if the analysis is standardized to `df_clean`.

### 5. Engagement Analysis

The project examines relationships between:

- Total page views and recorded duration
- Product-related page views and product-related duration
- Bounce rates and exit rates
- Page values and engagement measures

These relationships provide an initial understanding of session engagement and form the basis for the statistical analysis.

## Tableau Dashboard

Tableau is used to present the analytical findings through visualizations and KPI cards.

### Dashboard Components

| Visualization | Purpose |
|---|---|
| Total Sessions KPI | Displays the total number of cleaned sessions |
| Revenue Sessions KPI | Displays the number of sessions generating revenue |
| Conversion Rate KPI | Shows the proportion of sessions generating revenue |
| Monthly Traffic | Compares session counts across months |
| Monthly Conversion Rate | Compares conversion rates across months |
| Visitor Type Analysis | Compares conversion rates by visitor category |
| Traffic Type Analysis | Compares sessions across encoded traffic categories |
| Weekend vs. Weekday | Examines differences in conversion rates |
| Engagement Analysis | Visualizes page views against recorded duration |
| Bounce vs. Exit Rate | Examines the relationship between the two metrics |
| Product Engagement | Compares product-page activity and recorded duration |

### Dashboard Goals

The dashboard is designed to:

- Provide a quick overview of session performance.
- Make monthly patterns easier to identify.
- Compare visitor categories.
- Explore engagement patterns.
- Support interactive filtering and further investigation.

**Note:** Traffic type values are encoded categories. They should not be assigned names such as Google or Facebook unless a verified mapping is available.

A Tableau workbook and published dashboard can be linked here once their repository paths or public URLs are confirmed.

## Statistical Analysis

Statistical analysis is used to evaluate the strength of relationships and test differences between groups.

The significance threshold used in the analysis is:

\[
\alpha = 0.05
\]

A p-value below 0.05 is treated as statistically significant under the assumptions of the relevant test.

### 1. Pearson Correlation

**Objective:** Measure the direction and strength of the linear relationship between numerical variables.

The principal analysis examined `TotalPages` and `TotalDuration`.

Reported results:

| Measure | Result |
|---|---:|
| Pearson correlation coefficient | 0.856760 |
| Reported p-value | Below 0.001 |
| Interpretation | Strong positive linear relationship |

**Interpretation:** Sessions with more page views tended to have longer recorded durations.

The correlation matrix also showed:

| Variable Pair | Correlation |
|---|---:|
| BounceRates and ExitRates | 0.902 |
| ProductRelated and ProductRelated_Duration | 0.860 |
| TotalPages and TotalDuration | 0.857 |
| TotalPages and ExitRates | -0.300 |
| PageValues and TotalDuration | 0.056 |

Correlations involving a total and one of its components must be interpreted carefully because part of the relationship is mathematical by construction.

### 2. Chi-Square Test of Independence

**Objective:** Test whether visitor type and revenue generation are associated.

Variables:

- `VisitorType`
- `Revenue`

Hypotheses:

- **Null hypothesis (H₀):** Visitor type and revenue are independent.
- **Alternative hypothesis (H₁):** Visitor type and revenue are associated.

The earlier test on the original dataset returned:

| Measure | Result |
|---|---:|
| Chi-square statistic | 135.252 |
| Degrees of freedom | 2 |
| p-value | 4.27 × 10⁻³⁰ |

The result indicates a statistically significant association between visitor type and revenue in the original dataset.

For a final report, this test should be rerun on the cleaned dataset so the statistical results are consistent with the cleaned-data analysis.

### 3. Group Comparison

Revenue and non-revenue sessions were compared using their mean values.

| Variable | Non-Revenue Mean | Revenue Mean |
|---|---:|---:|
| TotalPages | 31.65 | 52.39 |
| TotalDuration | 1,188.22 | 2,053.30 |
| ProductRelated | 29.05 | 48.21 |
| ProductRelated_Duration | 1,082.98 | 1,876.21 |
| BounceRates | 0.0232 | 0.0051 |
| ExitRates | 0.0455 | 0.0196 |
| PageValues | 2.00 | 27.26 |

Revenue-generating sessions had higher average page counts, recorded duration, product-related activity, and PageValues. They also had lower average bounce and exit rates.

### 4. Mann–Whitney U Test

**Objective:** Compare the distributions of engagement variables between revenue and non-revenue sessions.

Hypotheses for each variable:

- **H₀:** The two groups have the same distribution for the variable.
- **H₁:** The distributions differ.

The reported tests returned p-values below 0.001 for all seven variables:

| Variable | Reported p-value | Result at 0.05 |
|---|---:|---|
| TotalPages | 2.83 × 10⁻¹⁰⁸ | Significant |
| TotalDuration | 1.20 × 10⁻¹²⁶ | Significant |
| ProductRelated | 3.69 × 10⁻¹⁰² | Significant |
| ProductRelated_Duration | 4.18 × 10⁻¹²² | Significant |
| BounceRates | 1.06 × 10⁻⁵⁶ | Significant |
| ExitRates | 3.03 × 10⁻¹⁶⁹ | Significant |
| PageValues | Below numerical display precision | Significant |

The extremely small PageValues p-value was displayed by Python as `0.0`; it should be reported as below 0.001 rather than as an exact zero.

These tests provide evidence of differences between the two groups. The Mann–Whitney U test evaluates distributions or ranks; it is not automatically a test of mean differences.

Because multiple tests were conducted, a final statistical report should consider a multiple-testing adjustment such as the Holm procedure.

## Key Findings

The main findings from the current analysis are:

1. **Overall conversion:** Approximately 15.63% of cleaned sessions generated revenue.
2. **Monthly traffic:** May had the highest session count among the reported months.
3. **Visitor categories:** New visitors had a higher observed conversion rate than returning visitors.
4. **Engagement relationship:** TotalPages and TotalDuration had a strong positive correlation.
5. **Bounce and exit rates:** These variables had a very strong positive correlation.
6. **Revenue-group differences:** Revenue sessions had higher average page views, recorded duration, product-related activity, and PageValues.
7. **Statistical evidence:** Mann–Whitney U tests indicated statistically significant distributional differences for all seven examined engagement variables.

These findings describe the analyzed dataset. They should not be generalized automatically to every online store or interpreted as proof of causation.

## Business Implications

The findings can help formulate questions for further investigation by e-commerce businesses.

### 1. Investigate Engagement Patterns

Revenue-generating sessions showed higher average page-view counts and longer recorded durations. Businesses could investigate which content and navigation patterns are associated with useful customer engagement.

### 2. Compare Visitor Categories

New and returning visitors had different observed conversion rates. Further analysis could investigate traffic sources, product interests, and other characteristics that might help explain these differences.

### 3. Monitor Bounce and Exit Metrics

The strong relationship between bounce rates and exit rates suggests that monitoring both metrics together may help identify sessions or page categories requiring further investigation.

### 4. Analyze Page Value

PageValues differed substantially between revenue and non-revenue sessions. This variable could be examined further to understand its relationship with purchasing outcomes.

These are potential areas for investigation, not verified outcomes of marketing interventions.

## Project Structure

The following is a suggested structure for organizing the project repository. Adjust the paths to match the files actually present in the repository.

```text
E-Commerce-Web-Analytics-And-Customer-Behavior-Analysis/
│
├── README.md
│
├── dataset/
│   ├── online_shoppers_intention.csv
│   └── ecommerce_cleaned.csv
│
├── notebooks/
│   └── E_Commerce_Web_Analytics.ipynb
│
├── tableau/
│   ├── ecommerce_dashboard.twbx
│   └── screenshots/
│
├── reports/
│   ├── abstract.docx
│   └── project_report.pdf
│
└── requirements.txt
```

Not every file listed above is necessarily included yet. Use the actual repository contents when finalizing this section.

## Installation and Setup

### Prerequisites

- Python 3
- Jupyter Notebook or Google Colab
- Tableau Desktop or Tableau Public
- Git (optional, for cloning the repository)

### 1. Clone the repository

```bash
git clone https://github.com/swaran05/E-Commerce-Web-Analytics-And-Customer-Behavior-Analysis.git
cd E-Commerce-Web-Analytics-And-Customer-Behavior-Analysis
```

### 2. Install Python libraries

```bash
pip install pandas numpy scipy matplotlib seaborn jupyter
```

### 3. Prepare the dataset

Obtain the Online Shoppers Purchasing Intention dataset from the UCI Machine Learning Repository and place the CSV in the appropriate project directory.

Ensure that the filename in your notebook matches the actual location of the dataset.

### 4. Open the notebook

```bash
jupyter notebook
```

Open the project's analysis notebook and execute the cells in order.

Alternatively, upload the notebook and dataset to Google Colab and update the file path as needed.

### 5. Open the Tableau workbook

Open the saved Tableau workbook, verify that its data source points to the correct cleaned CSV, and refresh the data if necessary.

If a workbook is not included in the repository, the dashboard must first be saved and added to the project before this step can be reproduced by another person.

## How to Run the Analysis

The recommended execution order is:

1. Load the original dataset.
2. Inspect dimensions, data types, missing values, and duplicates.
3. Remove duplicate rows.
4. Create derived features.
5. Export the cleaned dataset.
6. Run exploratory data analysis.
7. Calculate correlation coefficients and p-values.
8. Perform the chi-square test using the cleaned data.
9. Compare revenue and non-revenue groups.
10. Perform the Mann–Whitney U tests.
11. Open or rebuild the Tableau dashboard using the cleaned CSV.
12. Interpret and document the results.

Use the same cleaned DataFrame throughout the final statistical analysis to avoid mixing results from the original and cleaned datasets.

## Limitations

This project has several limitations:

- The dataset represents shopping sessions rather than complete event-level user journeys.
- The analysis is observational and cannot establish causal relationships.
- Traffic types are encoded categories; source names cannot be inferred without a verified mapping.
- Pearson correlation measures linear relationships and may not capture nonlinear associations.
- Very small p-values do not automatically indicate large or commercially important effects.
- The dataset may not represent current behavior across all e-commerce platforms.
- Results should be checked on the cleaned dataset before final reporting.
- Statistical significance should be considered alongside effect size, data quality, and practical relevance.

## Future Enhancements

Possible extensions include:

### 1. Effect Size Analysis

Add effect-size measures to quantify the magnitude of group differences rather than reporting p-values alone.

### 2. Multiple-Testing Correction

Apply a correction such as Holm's procedure when conducting multiple hypothesis tests.

### 3. Visitor and Session Segmentation

Explore clustering techniques to group sessions based on page views, duration, bounce rate, exit rate, and PageValues.

### 4. Purchase Prediction

Experiment with classification models such as logistic regression, decision trees, or random forests to estimate the likelihood that a session will generate revenue.

Any predictive model should be evaluated using suitable metrics and a held-out test set.

### 5. Interactive Analytics Application

Build a Streamlit application to present selected metrics, statistical findings, and optional model predictions.

### 6. Dashboard Improvements

Add validated filters, clearer metric definitions, and a documented workflow for refreshing the Tableau data source.

These enhancements are proposed future work and are not presented as completed features.

## Conclusion

The E-Commerce Web Analytics and Customer Behavior Analysis project demonstrates an end-to-end workflow for exploring online shopping sessions using Python, Tableau, and statistical methods.

The project combines data cleaning, feature engineering, exploratory analysis, interactive visualization, and hypothesis testing to investigate how engagement measures and visitor categories are associated with purchasing outcomes.

The results show that revenue-generating sessions differ from non-revenue sessions across several engagement measures, while correlation and chi-square analysis reveal additional relationships within the dataset.

Overall, the project demonstrates how data analytics can transform raw session records into interpretable findings that support further investigation of e-commerce customer behavior.

## Dataset Reference

**Online Shoppers Purchasing Intention Dataset**

UCI Machine Learning Repository:

https://archive.ics.uci.edu/dataset/468/online+shoppers+purchasing+intention+dataset

Please review the dataset's citation and usage terms on the official source before redistribution.

## Author

**Swaran Chandra Gouthireddy**

Computer Science undergraduate focused on Data Science, Machine Learning, and Data Analytics.

- GitHub: [swaran05](https://github.com/swaran05)
- Project Repository: [E-Commerce Web Analytics and Customer Behavior Analysis](https://github.com/swaran05/E-Commerce-Web-Analytics-And-Customer-Behavior-Analysis)
- LinkedIn: [Swaran Chandra Reddy](https://www.linkedin.com/in/swaran-chandra-reddy-3443862a6/)

---

If you find this project useful, consider starring the repository. Feedback and suggestions for improving the analysis are welcome.
