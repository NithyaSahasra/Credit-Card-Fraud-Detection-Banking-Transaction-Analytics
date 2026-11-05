# 💳 Credit Card Fraud Detection

## Objective
Develop a model to identify fraudulent credit card transactions in real-time. To detect fraudulent credit card transactions using data analysis and visualization techniques. The project covers data collection, cleaning, exploratory data analysis (EDA), and building interactive Power BI dashboards.

---

## Task 1: Dataset Used

* **Dataset Name:** Credit Card Fraud Detection
* **Source:** Kaggle
* **Link:** [Kaggle Dataset](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
* **Format:** `.csv`

### Description

* **Rows:** 284,807
* **Columns:** 31
* **Target Column:** `class` (0 = Normal, 1 = Fraud)
* **Features:** `V1` to `V28` (PCA components), `time`, `amount`
* **Goal:** Identify transaction patterns and detect fraudulent activities.

---

##  Task 2: Data Collection and Preparation

**Tools Used:** PostgreSQL, Python (Pandas), Power BI

### ✅ 1. Dataset Identification and Collection

* Downloaded from Kaggle
* Format: `creditcard.csv`
* ✅ **Deliverable:** `.csv` file confirmed

### ✅ 2. Data Import into SQL Database

* Tool: **PostgreSQL**
* Table: `cc_data`
* Schema created using appropriate data types (`FLOAT`, `INT`)
* Data imported using `SQLAlchemy` in Python
* No normalization needed (flat table)

✅ **Deliverable:** Data stored and accessible via PostgreSQL

### ✅ 3. Initial SQL Data Profiling

* Queried to find:

  * Total Records: `284,807`
  * Null Values: `0`
  * Duplicate Rows: `1,854`
  * Data Types: All numerical
* ✅ **Deliverable:** Profiling complete with scripts and findings

### ✅ 4. Data Cleaning and Transformation

* **In SQL:**

  * Checked for nulls, duplicates, formatting issues

* **In Python (Pandas):**

  * Loaded using `read_sql_query`
  * Dropped duplicates from class `0` only
  * Kept all fraud class records
  * Converted and renamed where needed

✅ **Deliverable:** Cleaned DataFrame with `283,745` records exported as `cleaned_dataset.csv`

### ✅ 5. Data Validation

* Row count in SQL matched Python
* Verified class distribution, stats, and consistency

✅ **Deliverable:** Clean dataset ready for Power BI analysis

---

## 📊 Task 3: EDA and Visualization

**Tools Used:** Python (Seaborn, Matplotlib), Power BI

### 🔹 1. Summary Statistics

* Used `.describe()` and `value_counts()`
* Mean amount: ₹88.35
* Fraud Rate: **0.173%**

### 🔹 2. Univariate Analysis

* Countplots of class distribution
* Histograms for `amount`, `time`
* Noticed skewed transaction frequency toward smaller amounts

### 🔹 3. Bivariate/Multivariate Analysis

* Boxplots for `amount` and `time` vs `class`
* Correlation plot shows features like `V11`, `V4`, `V14`, `V10` strongly linked to fraud

### 🔹 4. Outlier & Anomaly Detection

* Outliers identified via boxplots in selected features
* **Decision:** Keep outliers—they might be actual fraud cases

### 🔹 5. Power BI Dashboard

* Imported `cleaned_dataset.csv`
* Built dashboard with:

  * **KPIs:** Total Transactions, Fraud %, Avg. Amount
  * **Visuals:** Bar charts, histograms, filters by amount/time/class
  * **Final Clean Data Stats:**

    * Records: 283,745
    * Normal: 283,253
    * Fraud: 492
    * Fraud Rate: 0.1734%

✅ **Deliverables:**

* creditcard_project(`.ipynb`)
* Power BI file (`.pbix`)
* Summary: Clean, imbalanced dataset with high fraud-risk anomaly zones

---

## ✅ Task 4: Conclusion and Recommendations

###  Key Insights Summary

* Dataset is **heavily imbalanced**
* Fraudulent transactions tend to occur in small amounts and within narrow time frames
* Strong correlations found in certain PCA components

### Business Implications

* Even small-value frauds can accumulate into significant losses
* Real-time systems should prioritize transactions matching fraud profiles

### Recommendations

1. **Deploy anomaly detection models** using top correlated features
2. **Monitor small transactions more closely**
3. **Use real-time dashboards** in Power BI to trigger fraud alerts
4. **Update dataset regularly** and retrain models

### Next Steps

* Build **predictive ML model** 
* Automate **Power BI data refresh**
* Integrate with **live transaction feeds**

✅ **Deliverable:**

* `Power BI snapshots`
  
![dashboard](https://github.com/user-attachments/assets/43d96f8c-fa23-42a1-9e7f-7b3669c2ee47)


---

## Files in This Repository

| File Name              | Description                              |
| ---------------------- | ---------------------------------------- |
| `creditcard.csv`       | Original dataset from Kaggle             |
| `cleaned_dataset.csv`  | Cleaned dataset used for visualization   |
| `CC_Project.sql`  | Original Dataset import into Postgresql   |
| `creditcard_project.ipynb`   | Exploratory data analysis in Jupyter     |
| `CreditCardFraudDetection_Dashboard.pbix` | Power BI interactive dashboard           |
| `README.md`            | GitHub project documentation (this file) |

