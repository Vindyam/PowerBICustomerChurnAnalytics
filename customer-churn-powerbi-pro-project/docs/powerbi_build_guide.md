# Power BI Build Guide

## 1) Import Data
Open Power BI Desktop and load:
`data/customer_churn_data.csv`

## 2) Recommended Calculated Columns
### Churn Status
```DAX
Churn Status = IF('customer_churn_data'[Churn] = "Yes", "Churned", "Retained")
```

### Tenure Band
```DAX
Tenure Band =
SWITCH(
    TRUE(),
    'customer_churn_data'[Tenure] <= 6, "0-6",
    'customer_churn_data'[Tenure] <= 12, "7-12",
    'customer_churn_data'[Tenure] <= 24, "13-24",
    'customer_churn_data'[Tenure] <= 36, "25-36",
    'customer_churn_data'[Tenure] <= 48, "37-48",
    'customer_churn_data'[Tenure] <= 60, "49-60",
    "60+"
)
```

## 3) Add Measures
Copy the measures from `measures/dax_measures.txt`.

## 4) Create Pages
- Executive Overview
- Customer Segmentation
- Revenue & Risk Analysis
- Drivers of Churn

## 5) Add Slicers
Recommended slicers:
- Gender
- ContractType
- InternetService
- None
- Tenure Band

## 6) Export Screenshots
After building the dashboard, export PNG screenshots and replace the mock images in `screenshots/`.
