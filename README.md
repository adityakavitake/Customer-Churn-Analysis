# Customer Churn Analysis 📊

## 📌 Project Overview

This project focuses on **Customer Churn Analysis** using Python, Pandas, SQL, and data visualization techniques.

The objective is to analyze customer subscription data, identify customers who have churned, understand factors associated with churn, and generate useful business insights that can help improve customer retention.

The project combines data from three SQLite database tables:

* **Customer** – customer demographic information
* **Subscription** – subscription, plan, charges, CLTV, and churn information
* **Support** – customer complaints, escalations, and CSAT scores

The datasets are cleaned, transformed, merged, analyzed, and exported for further use.

---

## 🎯 Objectives

The main objectives of this project are:

* Analyze customer subscription behavior
* Identify churned and retained customers
* Calculate overall churn and retention rates
* Analyze churn by subscription plan
* Calculate Average Revenue Per User (ARPU)
* Calculate average customer tenure
* Estimate revenue at risk from churn
* Analyze customer support escalations
* Study the relationship between escalations and churn
* Categorize customers into low, medium, and high churn-risk groups
* Create visualizations to understand customer behavior

---

## 🛠️ Technologies Used

* **Python**
* **Pandas** – Data manipulation and analysis
* **NumPy** – Numerical operations
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization
* **SQLite** – Database management
* **Jupyter Notebook** – Development environment

---

### 1. Customer Table

Contains customer-related information such as:

* Customer ID
* Customer Name
* Country
* State
* Gender
* Date of Birth

The notebook performs data cleaning such as renaming columns, removing unnecessary columns, converting dates, handling missing country values, and standardizing gender values.

### 2. Subscription Table

Contains subscription-related information:

* Customer ID
* Subscription Start Date
* Subscription Type
* Renewal Date
* Plan Type
* Contract Type
* Cancellation Date
* Cancellation Reason
* Monthly Charges
* CLTV
* Churn Score

A `churn_flag` is created using the cancellation date:

* `1` → Customer churned
* `0` → Customer retained

### 3. Support Table

Contains customer-support information:

* Customer ID
* Complaint Date
* Escalations
* CSAT Score

Unnecessary columns were removed and complaint dates were converted into datetime format.

---

## 🔄 Project Workflow

```text
SQLite Database
       ↓
Import Tables
       ↓
Data Cleaning
       ↓
Data Type Conversion
       ↓
Missing Value Handling
       ↓
Data Standardization
       ↓
Feature Engineering
       ↓
Merge Customer + Subscription + Support Data
       ↓
KPI Calculation
       ↓
Churn Analysis
       ↓
Data Visualization
       ↓
Export Processed Dataset
```

The three tables are merged using `customerid` to create the final analytical dataset.

---

## 🧹 Data Cleaning

The following preprocessing operations were performed:

* Removed unnecessary columns such as `interests`, `pincode`, `col_1`, and `comment`

* Renamed `name` to `customer_name`

* Converted date columns to datetime format

* Handled missing country values using state-to-country mapping

* Standardized categorical information

* Created a customer complaint count

* Removed duplicate support records while retaining the latest complaint record

---

## 📈 Key Metrics

The analysis produced the following key metrics:

| Metric                          |        Result |
| ------------------------------- | ------------: |
| Total Customers                 |            21 |
| Churn Rate                      |    **28.57%** |
| Retention Rate                  |    **71.43%** |
| ARPU                            |     **18.85** |
| Average Tenure                  | **1529 days** |
| Revenue at Risk                 |     **73.94** |
| Escalation Rate                 |    **19.05%** |
| Average Complaints per User     |      **0.43** |
| Escalation vs Churn Correlation |      **0.77** |

The churn and retention calculations are based on the generated `churn_flag`.

The notebook calculates an ARPU of 18.85, average tenure of approximately 1,529 days, and revenue at risk of 73.94 from churned customers.

---

## 📊 Churn by Plan Type

The analysis shows different churn rates across subscription plans:

| Plan Type | Churn Rate |
| --------- | ---------: |
| Basic     | **60.00%** |
| Premium   | **14.29%** |
| Standard  | **22.22%** |

The **Basic plan has the highest observed churn rate**, while Premium has the lowest in this dataset.

---

## 🚨 Churn Risk Classification

Customers are classified into three risk categories based on their existing `churn_score`:

| Churn Score | Risk Level |
| ----------- | ---------- |
| `< 50`      | Low        |
| `50–69`     | Medium     |
| `>= 70`     | High       |

A new `churn_risk` feature is created using these thresholds.

---

## 🔎 Customer Support & Churn

Customer support behavior was also analyzed.

The project converts escalation values into numerical form and calculates the correlation between support escalations and churn.

The observed correlation is:

**0.77**

This indicates a strong positive association between escalations and churn within this dataset. However, correlation alone does not establish that escalations cause churn.

---

## 📊 Data Visualization

The project uses:

* Matplotlib
* Seaborn

for exploring customer churn patterns and relationships between different variables.

The visualization dataset includes features such as:

* Plan Type
* Contract Type
* Churn Score
* Churn Flag
* Churn Risk
* Escalations

---

## 💡 Key Insights

Based on the analysis:

1. The overall churn rate is **28.57%**.
2. The retention rate is **71.43%**.
3. The Basic plan has the highest observed churn rate at **60%**.
4. Premium customers show the lowest observed churn rate at **14.29%**.
5. Customer support escalations have a **0.77 correlation** with churn in this dataset.
6. The analysis identifies high-risk customers using the existing churn score.
7. Churned customers represent a measurable amount of monthly revenue at risk.
8. Customer support and subscription characteristics can be useful dimensions for further churn investigation.

---

## 📁 Project Structure

```text
Customer-Churn-Analysis/
│
├── churn_analysis.ipynb
├── customer_churn.db
├── exported_churn_data.csv
└── README.md
```

> **Note:** The notebook exports the processed dataset as `exported_churn_data.csv`.

---

## ▶️ How to Run the Project

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/customer-churn-analysis.git
```

### 2. Open the project folder

```bash
cd customer-churn-analysis
```

### 3. Install required libraries

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

SQLite support is provided through Python's `sqlite3` module.

### 4. Start Jupyter Notebook

```bash
jupyter notebook
```

### 5. Open

```text
churn_analysis.ipynb
```

### 6. Run the notebook

Run the cells sequentially to:

* Load the SQLite database
* Clean the data
* Merge the tables
* Generate churn features
* Calculate KPIs
* Perform churn analysis
* Generate visualizations
* Export the processed dataset

---

## 📌 Future Improvements

The project can be extended by:

* Building a machine-learning churn prediction model
* Comparing Logistic Regression, Decision Tree, Random Forest, and XGBoost
* Performing feature importance analysis
* Creating an interactive Power BI/Tableau dashboard
* Adding more customer behavioral data
* Improving categorical encoding
* Handling class imbalance
* Creating automated churn-risk predictions
* Adding more detailed customer segmentation

---

## 👨‍💻 Author

**Aditya Dayanand Kavitake**

Computer Engineering | Data Science & Analytics

---


