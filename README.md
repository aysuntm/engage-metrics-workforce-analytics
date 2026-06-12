# EngageMetrics Workforce Analytics: Employee Satisfaction Study

This repository contains an end-to-end data analytics pipeline investigating patterns associated with employee satisfaction using a workforce employee profile dataset. The project applies data cleaning, exploratory data analysis (EDA), and statistical testing to examine relationships among overtime workload, work mode, departmental differences, compensation, and employee satisfaction. The analysis combines visual exploration with quantitative validation to assess whether observed workforce patterns reflect meaningful organizational trends or localized sample variation.

## 🚀 Key Strategic Findings from EDA
* **Overtime Threshold Exploration:** Visual analysis suggested a potential shift in employee satisfaction around **6 hours of weekly overtime** with lower satisfaction appearing more frequently beyond this point across several employee groups. This threshold was explored further through statistical testing to determine whether the pattern reflected a meaningful association or normal sample variation.
* **HR Compensation & Workload Profile:** Department-level distributional analysis identified HR as a potentially vulnerable subgroup, exhibiting the **lowest median salary (~$65k)** alongside one of the broadest weekly workload distributions, with hours extending to **54 hours per week**. However, conclusions should be interpreted cautiously due to the department’s relatively small sample size.
* **Marketing Workload Dynamics:** Marketing employees showed the **highest average compensation and strongest remote-work representation**, yet satisfaction remained moderate. The department also exhibited the **highest median overtime (~7.2 hours/week)**, suggesting possible operational strain despite compensation advantages.
* **Finance Satisfaction Ceiling:** The Finance department displayed a relatively compressed satisfaction profile, with **75% of employees reporting satisfaction scores of 6.0 or lower**, indicating a potentially stable but constrained satisfaction baseline that may warrant further organizational investigation.75% of the Finance cohort scores a 6.0 or lower in satisfaction, signaling a flat baseline that could be optimized through targeted interventions like remote optionality or compensation adjustments.

## 🛠️ Statistical Analysis

After data cleaning and exploratory analysis, statistical testing was conducted to evaluate whether observed patterns represented meaningful organizational relationships or localized sample variation.

1. **Categorical Independence Testing (Chi-Square):**
   * **Work Mode vs. High Overtime:** A second Chi-Square Test evaluated whether work mode (remote, hybrid, or on-site) influenced the likelihood of crossing the exploratory high-overtime threshold. Results found no statistically significant relationship, indicating that overtime patterns appeared broadly independent of work arrangement in this dataset.
   
   * **Overtime Threshold vs. Satisfaction:** Because satisfaction scores were **ordinal (1–10)** and overtime workload groups exhibited **unequal sample sizes and non-normal distributions**, a **Kruskal–Wallis test** was used to compare satisfaction distributions across overtime workload categories. Results did not reveal statistically significant differences in satisfaction across overtime groups, suggesting that the visual decline in satisfaction beyond the exploratory 6-hour overtime threshold may reflect sample variability rather than a robust underlying relationship. To further assess whether overtime and satisfaction were associated, a **Spearman rank correlation test** was performed using raw overtime values. The correlation analysis similarly found no statistically significant monotonic relationship, reinforcing the conclusion that overtime was not meaningfully associated with employee satisfaction in this sample.

2. **Departmental Satisfaction Testing (ANOVA + Kruskal–Wallis):**
   * **Departmental Satisfaction Differences:** **One-Way ANOVA** was used to compare mean satisfaction scores across departments after validating assumptions using **Levene’s test for variance homogeneity and Shapiro–Wilk normality checks**. Because several department groups showed non-normal distributions and small subgroup sizes, a **nonparametric Kruskal–Wallis test** was also performed as a robustness check.
   * Results from both parametric and nonparametric testing found no statistically significant differences in employee satisfaction across departments, suggesting that observed variation between HR, Finance, Engineering, and Marketing may be attributable to sample variability rather than systematic organizational effects.

## 🛠️ Limitations & Future Work

While exploratory analysis revealed visible departmental patterns in overtime and satisfaction, formal statistical testing did not identify statistically significant differences in employee satisfaction across departments or overtime groups within this sample. Interpretation is limited by small subgroup sizes—particularly for HR and Marketing—after removing observations with missing salary data.

Future work would prioritize recovering missing salary information to improve subgroup representation and statistical power before re-running the analysis pipeline. Additional investigation into relationships between salary, overtime workload, and employee satisfaction may also provide further insight once dataset completeness improves.

## 📁 Repository Structure
The project is built using a highly modular, "docs-as-code" workflow split into distinct steps:

* `data/`
  * `processed_employee_profiles.csv`: Cleaned and validated dataset used for downstream analysis.
* `notebooks/`
  * `01_data_cleaning.ipynb`: Ingestion pipeline that filters anomalies, handles missing fields, and addresses data integrity (including the removal of standard median imputation artifacts to protect salary distributions).
  * `02_eda_and_visualization.ipynb`: Exploratory visual analysis using Matplotlib and Seaborn to investigate salary, overtime, satisfaction, and department-level workforce patterns.
  * `03_statistical_analysis.ipynb`: Statistical validation of exploratory findings, including expected cell-count inspection for Chi-Square assumptions, Levene’s and Shapiro–Wilk tests, Chi-Square Tests of Independence, One-Way ANOVA, and Kruskal–Wallis testing for robustness under non-normal group distributions.

## 🛠️ Tech Stack & Dependencies
* **Language:** Python 3
* **Libraries:** Pandas, NumPy, SciPy, Matplotlib, Seaborn
* **Version Control:** Git & GitHub

## ⚙️ How to Run the Project
1. Clone the repository:
   ```bash
   git clone [https://github.com/aysuntm/EngageMetrics-Workforce-Analytics.git](https://github.com/aysuntm/EngageMetrics-Workforce-Analytics.git)
2. Install the required dependencies:
    ```bash
    pip install -r requirements.txt
3. Run the Jupyter Notebooks sequentially in your local environment or VS Code workspace
(01_data_cleaning.ipynb -> 02_eda_and_visualization.ipynb -> 03_statistical_analysis.ipynb).
