# EngageMetrics Workforce Analytics: Employee Satisfaction Study

This repository contains an end-to-end data analytics pipeline investigating the structural and operational drivers of employee satisfaction. Utilizing a dataset of employee profiles, the project applies data cleaning, exploratory data analysis (EDA), and statistical testing to identify operational risk areas and deliver actionable insights for organizational leadership.

## 🚀 Key Strategic Findings from EDA
* **The Overtime Burnout Horizon:** Organizational data identifies **6 hours of weekly overtime** as a critical burnout threshold. Beyond this boundary, employee satisfaction drops across almost all demographics.
* **The HR Underpayment & Workload Risk:** While average salary metrics look stable on paper, distributional analysis isolates the HR department as a severe retention risk. HR exhibits the lowest median salary (~$65k) paired with the widest distribution of weekly working hours (stretching up to 54 hours per week).
* **The Marketing Overtime Paradox:** Marketing teams enjoy the highest average compensation and the greatest remote work flexibility, yet satisfaction remains capped. This is driven by acute operational volatility, with Marketing pulling the highest median overtime (7.2 hours/week) despite lower absolute weekly volume.
* **Finance Distributional Ceiling:** 75% of the Finance cohort scores a 6.0 or lower in satisfaction, signaling a flat baseline that could be optimized through targeted interventions like remote optionality or compensation adjustments.

## 🛠️ Phase 3 Roadmap: Statistical Analysis

With the data cleaned and validated and departmental trends mapped, the project transitions from visual hypotheses to quantitative verification. The next phase will execute statistical testing to determine if the initial findings reflect systemic corporate dynamics or localized variance:

1. **Categorical Independence Testing (Chi-Square):**
   * **Overtime Threshold vs. Satisfaction:** To prove whether crossing the 6-hour weekly overtime cliff is a genuine statistical driver for low satisfaction scores.

   * **Work Mode vs. High Overtime:** Investigating if working remotely or in a hybrid structure inherently impacts the probability of crossing the 6-hour overwork boundary, or if overwork is independent of location.

2. **Variance Testing (ANOVA):**
   * **Departmental Satisfaction Distributions:** Implementing an analysis of variance across department cohorts to confirm if the severe drop in HR's satisfaction score (and the 6.0 satisfaction ceiling discovered in Finance) meets the threshold of statistical significance.

## 📁 Repository Structure
The project is built using a highly modular, "docs-as-code" workflow split into distinct steps:

* `data/`
  * `processed_employee_profiles.csv`: The sanitized, validated dataset used for analysis.
* `notebooks/`
  * `01_data_cleaning.ipynb`: Ingestion pipeline that filters anomalies, handles missing fields, and addresses data integrity (including the removal of standard median imputation artifacts to protect salary distributions).
  * `02_eda_and_visualization.ipynb`: Advanced graphical exploration utilizing Seaborn and Matplotlib to map organizational trends and isolate macro-to-micro departmental behaviors.
  * **(WIP)** `03_statistical_analysis.ipynb`: Quantitative validation phase running Chi-Square Tests of Independence (Work Mode vs. Overtime; Overtime vs. Satisfaction) and ANOVA variance testing to prove statistical significance.

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
