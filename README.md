# Frude-risk-analysis
# Fraud Risk Analysis Dashboard | Power BI

## 📌 Project Overview

The Fraud Risk Analysis Dashboard analysis 1,296,675 rows, is an interactive Power BI solution designed to monitor and analyze fraudulent financial transactions. The dashboard provides key fraud indicators, fraud trends, transaction behavior, demographic analysis, and geographic risk distribution to help organizations detect suspicious activities and make informed decisions.
<img width="948" height="541" alt="Screenshot 2026-10-30 094323" src="https://github.com/user-attachments/assets/d9de0d99-ab42-48f8-8161-7a3b6cf7d63f" />



## 🎯 Business Objectives

- Monitor fraud transaction volume and value.
- Measure fraud occurrence rates.
- Analyze fraud patterns across categories and demographics.
- Identify high-risk states and transaction segments.
- Compare fraud and non-fraud financial impact.
- Support fraud prevention and risk management initiatives.

---

## 📊 Dashboard KPIs

### Total Transactions
Measures the overall transaction volume processed.

```DAX
Total Transactions =
COUNTROWS('Fraud_Data')
```

### Total Fraud Cases
Measures total fraudulent transactions.

```DAX
Total Fraud Cases =
CALCULATE(
    COUNTROWS('Fraud_Data'),
    'Fraud_Data'[is_fraud] = 1
)
```

### Fraud Rate %

Percentage of transactions classified as fraud.

```DAX
Fraud Rate % =
DIVIDE(
    [Total Fraud Cases],
    [Total Transactions],
    0
)
```

### Average Transaction Amount

```DAX
Average Transaction Amount =
AVERAGE('Fraud_Data'[amt])
```

### Average Fraud Amount

```DAX
Avg Fraud Amount =
CALCULATE(
    AVERAGE('Fraud_Data'[amt]),
    'Fraud_Data'[is_fraud] = 1
)
```

### Total Fraud Amount

```DAX
Fraud Amount =
CALCULATE(
    SUM('Fraud_Data'[amt]),
    'Fraud_Data'[is_fraud] = 1
)
```

### Non-Fraud Amount

```DAX
Non Fraud Amount =
CALCULATE(
    SUM('Fraud_Data'[amt]),
    'Fraud_Data'[is_fraud] = 0
)
```

---

## 📈 Visual Analysis

### Fraud Rate (%) vs Non-Fraud Amount Trend

Analyzes how fraud occurrence changes relative to legitimate transaction value over time.

**Metrics Used**

```DAX
Monthly Fraud Rate =
CALCULATE(
    [Fraud Rate %]
)
```

```DAX
Monthly Non Fraud Amount =
[Non Fraud Amount]
```

---

### Fraud Rate (%) by Gender

Measures fraud distribution across customer demographics.

```DAX
Fraud Rate by Gender =
DIVIDE(
    [Total Fraud Cases],
    [Total Transactions]
)
```

---

### Fraud Amount by Category

Analyzes which transaction categories contribute the highest fraud losses.

```DAX
Fraud Amount by Category =
CALCULATE(
    SUM('Fraud_Data'[amt]),
    'Fraud_Data'[is_fraud] = 1
)
```

Categories include:

- Shopping
- Grocery POS
- Grocery Net
- Entertainment
- Food Dining
- Gas Transport
- Home
- Miscellaneous

---

### Total Fraud Cases by State

Ranks states according to detected fraud cases.

```DAX
Fraud Cases by State =
CALCULATE(
    COUNTROWS('Fraud_Data'),
    'Fraud_Data'[is_fraud] = 1
)
```

---

## 🚨 Risk Classification

Fraud transactions can be categorized using a risk level column.

```DAX
Risk Category =
SWITCH(
    TRUE(),
    'Fraud_Data'[amt] < 250, "Low",
    'Fraud_Data'[amt] < 1000, "Medium",
    "High"
)
```

---

## 📋 Dashboard Insights

### Key Findings

- Fraud rate reached approximately 57.89% of identified transactions.
- More than 8K fraud cases were recorded.
- Fraud amount exceeded 3.9M in transaction losses.
- Shopping and retail categories contributed significantly to fraud volume.
- Certain states demonstrated substantially higher fraud concentrations.
- Average fraud transactions were higher than normal transaction patterns.

### Business Impact

- Improves fraud detection efficiency.
- Supports proactive risk mitigation.
- Enhances transaction monitoring.
- Identifies high-risk geographies and categories.
- Reduces financial loss through data-driven decisions.

---

## 🛠 Tools & Technologies

- Microsoft Power BI
- DAX (Data Analysis Expressions)
- Power Query
- Data Modeling
- Data Visualization
- Financial Risk Analytics

---

## 📂 Project Structure

```
Fraud-Risk-Analysis-Dashboard
│
├── Dataset
│   └── fraud_data.csv  <img width="1322" height="577" alt="Screenshot 2026-11-02 121144" src="https://github.com/user-attachments/assets/38886857-4932-4460-8fd3-ef8787475706" />

│
├── PowerBI
│   └── Fraud_Risk_Analysis.pbix
│
├── Images
│   ├── Dashboard.png<img width="948" height="541" alt="Screenshot 2026-10-30 094323" src="https://github.com/user-attachments/assets/8d58450f-5b05-4873-8573-542049a3a581" />

│   └── Overview.png
│
└── README.md
```
<img width="1322" height="577" alt="Screenshot 2026-11-02 121144" src="https://github.com/user-attachments/assets/cae5023f-f39a-43b9-aee2-6ca0ab37a596" />



## 📸 Dashboard Features

✔ KPI Monitoring

✔ Fraud Trend Analysis

✔ Geographic Fraud Distribution

✔ Category Risk Assessment

✔ Gender-Based Fraud Analysis

✔ Interactive Filtering

✔ Executive-Level Reporting





## Conclusion

The Fraud Risk Analysis Dashboard delivers a comprehensive view of fraud performance, transaction behavior, and financial risk. Through interactive Power BI visualizations and DAX-driven analytics, decision-makers can quickly identify fraud trends, assess exposure, and implement targeted risk management strategies.
