# Heart Disease Analysis & Risk Factor Prediction

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626.svg?style=for-the-badge&logo=Jupyter&logoColor=white)

An end-to-end data analysis project focused on identifying significant risk factors for heart disease from a complex clinical dataset. The project involves intensive data cleaning, exploratory data analysis, and statistical analysis, with the final insights presented in a fully interactive Power BI dashboard.

---

### 📊 **Final Power BI Dashboard**
![Heart Disease Dashboard](https://github.com/LakshitaPagaria/Heart-Disease-Analysis-Risk-Factor-Prediction/blob/main/Dashboard%20Image.png)

---

## 📋 Table of Contents
1.  [📖 Project Overview](#1--project-overview)
2.  [🎯 Business Problem](#2--business-problem)
3.  [💾 Data Source](#3--data-source)
4.  [🛠️ Tech Stack & Libraries](#4--tech-stack--libraries)
5.  [⚙️ Project Workflow & Methodology](#5--project-workflow--methodology)
6.  [📊 Key Findings: Risk Factor Analysis](#6--key-findings-risk-factor-analysis)
7.  [💡 Actionable Recommendations](#7--actionable-recommendations)
8.  [🚀 Getting Started](#8--getting-started)
9.  [📂 File Structure](#9--file-structure)
10. [📞 Contact](#10--contact)

---

## 1. 📖 Project Overview

This project provides a comprehensive analysis of the UCI Heart Disease dataset, which aggregates clinical data from four different hospitals. The primary goal is to transform this raw, multi-source data into actionable insights. The workflow covers the entire data analysis lifecycle: from intensive data cleaning and preprocessing to exploratory data analysis (EDA) and statistical risk factor identification. The final deliverable is a dynamic Power BI dashboard designed to help healthcare professionals understand and explore the key drivers of heart disease.

---

## 2. 🎯 Business Problem

Cardiovascular diseases are a leading cause of mortality worldwide. For healthcare organizations, the ability to identify high-risk patient profiles is critical for deploying preventive strategies, optimizing resource allocation, and improving patient outcomes. This project addresses this need by analyzing clinical data to determine the most significant predictors of heart disease, thereby providing a foundation for data-informed clinical decision-making.

---

## 3. 💾 Data Source

The dataset used is a comprehensive collection of patient records from the **UCI Machine Learning Repository**, combining data from four medical centers: Cleveland, Hungary, Switzerland, and the V.A. Long Beach.

-   **Raw Dataset:** `heart_disease_uci.csv`
-   **Cleaned Dataset:** `cleaned_heart_disease.csv`

The raw dataset contains 920 records and 16 columns, including various clinical attributes and a target variable indicating the presence of heart disease.

---

## 4. 🛠️ Tech Stack & Libraries

-   **Programming Language:** `Python`
-   **Core Libraries:** `Pandas`, `NumPy`, `Matplotlib`, `Seaborn`, `Scipy`
-   **BI & Visualization:** `Microsoft Power BI`
-   **Development Environment:** `Jupyter Notebook`

---

## 5. ⚙️ Project Workflow & Methodology

The analysis was conducted in a systematic, multi-stage process, detailed below:

### Step 1: Data Acquisition & Initial Inspection
-   The raw dataset (`heart_disease_uci.csv`) was loaded into a Pandas DataFrame.
-   Initial data understanding was performed using `.head()`, `.shape`, `.columns`, `.info()`, and `.describe(include='all')` to assess the data's structure, identify missing values, and understand the initial data types.

### Step 2: Data Cleaning & Preprocessing
This was the most critical phase, involving several steps to handle the raw data's inconsistencies:
-   **Duplicate Removal:** Checked for and removed any duplicate rows using `.drop_duplicates()`.
-   **Column Standardization:** All column names were converted to lowercase and stripped of leading/trailing spaces for consistency.
-   **Missing Value Imputation:**
    -   Identified columns with significant missing data (`trestbps`, `chol`, `slope`, `ca`, `thal`, etc.).
    -   Handled missing values (`?`, `NaN`, blanks) using median imputation for key numerical features (`ca`, `thalch`, `oldpeak`) and mode imputation for categorical features (`thal`, `cp`, `slope`).
    -   Rows with null values in critical columns (`trestbps`, `chol`) were dropped to ensure data integrity.
-   **Data Type Correction:** Corrected data types for several columns from `object` to `numeric` using `pd.to_numeric` after cleaning.
-   **Feature Engineering & Encoding:**
    -   Categorical text data was mapped to numerical formats (e.g., `sex`: 'Male'/'Female' to `1`/`0`; `fbs` and `exang`: 'True'/'False' to `1`/`0`).
    -   The multi-class target variable `num` (ranging from 0-4) was binarized into a `target` column where `0` represents 'No Heart Disease' and `1` represents 'Presence of Heart Disease'.

### Step 3: Exploratory Data Analysis (EDA)
-   **Univariate Analysis:** Visualized the distribution of the target variable (Disease Frequency) and key numerical features (`age`, `trestbps`, `chol`, etc.) using histograms and count plots.
-   **Bivariate Analysis:** Analyzed the relationship between categorical features and the heart disease outcome using `sns.countplot` with a `hue` for the target variable.
-   **Correlation Analysis:** A heatmap was generated using `sns.heatmap` to visualize the correlation matrix of all numerical features, helping to identify linear relationships and potential multicollinearity.

### Step 4: Statistical Risk Factor Analysis
-   A dual approach was used to quantify the importance of each feature:
    -   **Numerical Features:** Pearson correlation coefficient was calculated between each numerical feature and the binary `target` variable.
    -   **Categorical Features:** The Chi-Square test of independence (`scipy.stats.chi2_contingency`) was conducted to determine the statistical significance of the association between each categorical feature and the `target`.
-   The results were compiled and ranked to create a definitive list of the most impactful risk factors.

### Step 5: Data Export for Business Intelligence
-   The fully cleaned, processed, and engineered DataFrame was saved as `cleaned_heart_disease.csv`, making it ready for ingestion into Power BI.

---

## 6. 📊 Key Findings: Risk Factor Analysis

The statistical analysis provided a clear hierarchy of heart disease predictors. The table below ranks the features based on their association strength (Correlation for numeric, Chi-Square p-value for categorical).

| Feature   | Association Type   |   Association Value | Strength   |
|:----------|:-------------------|--------------------:|:-----------|
| exang     | Correlation        |         0.491     | Strong     |
| oldpeak   | Correlation        |         0.416     | Strong     |
| thalch    | Correlation        |        -0.396     | Moderate   |
| sex       | Correlation        |         0.299     | Moderate   |
| age       | Correlation        |         0.288     | Moderate   |
| ca        | Correlation        |         0.210     | Moderate   |
| trestbps  | Correlation        |         0.149     | Weak       |
| chol      | Correlation        |        -0.137     | Weak       |
| fbs       | Correlation        |         0.120     | Weak       |
| cp        | Chi2 p-value       |         0.000     | Strong     |
| dataset   | Chi2 p-value       |         0.000     | Strong     |
| thal      | Chi2 p-value       |         0.000     | Strong     |
| slope     | Chi2 p-value       |         0.000     | Strong     |
| restecg   | Chi2 p-value       |         0.002     | Strong     |

---

## 7. 💡 Actionable Recommendations

Based on the findings, the following actions are recommended for healthcare providers:

1.  **Prioritize High-Risk Markers:** Patients presenting with **exercise-induced angina**, **asymptomatic chest pain**, and abnormal **thalassemia** results should be prioritized for further cardiovascular screening.
2.  **Enhance Diagnostic Protocols:** Incorporate `oldpeak` and `ST slope` measurements from stress tests as primary indicators in risk assessment models.
3.  **Targeted Screening Programs:** Implement targeted screening initiatives for the male population, particularly as they enter the 50+ age bracket, where the prevalence of heart disease increases sharply.

---

## 8. 🚀 How to Use

### Prerequisites
-   Python 3.8+
-   Jupyter Notebook or JupyterLab
-   Microsoft Power BI Desktop

### Installation & Setup
1.  **Clone the repository:**
    ```sh
    git clone [https://github.com/your-username/heart-disease-analysis.git](https://github.com/your-username/heart-disease-analysis.git)
    ```
2.  **Navigate to the project directory:**
    ```sh
    cd heart-disease-analysis
    ```
3.  **Install dependencies:**
    ```sh
    pip install pandas numpy matplotlib seaborn scipy
    ```
4.  **Run the Analysis:**
    -   Launch Jupyter Notebook.
    -   Open and run all cells in `heart_disease_analysis.ipynb`. This will generate the `cleaned_heart_disease.csv`.

5.  **View the Dashboard:**
    -   Open the project's `.pbix` file in Power BI Desktop.
    -   If prompted, update the data source to point to the newly generated `cleaned_heart_disease.csv`.

---

## 9. 📂 File Structure

├── heart_disease_analysis.ipynb      # Main Jupyter Notebook with all the analysis
├── heart_disease_uci.csv             # Raw input data
├── cleaned_heart_disease.csv         # Processed data for Power BI
├── Heart Disease Dashboard.pbix      # Power BI dashboard file (placeholder)
└── README.md                         # Project documentation


---

## 10. 📞 Contact

**Your Name**

-   **Email:** `lakshitapagaria@gmail.com`
-   **LinkedIn:** `https://www.linkedin.com/in/lakshita-pagaria/`
