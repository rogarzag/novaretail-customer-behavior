# NovaRetail+ Customer Behavior and Revenue Drivers

## Overview

This project explores which customer behavior factors are most strongly associated with the annual revenue generated for **NovaRetail+**, an e-commerce platform in Latin America.

The analysis focuses on exploratory relationships rather than causal claims and applies different correlation methods according to variable type.

## Business Question

**Which customer behavior factors are most strongly associated with the annual revenue generated?**

## Dataset

The analysis uses a customer-level dataset with:

- **15,000 records**
- **12 variables**
- Customer demographics and estimated income
- Monthly visits and purchases
- Targeted advertising spend
- Satisfaction
- Premium membership and churn status
- Device type and region
- Annual revenue generated per customer

The notebook expects the dataset at:

```text
data/novaretail_comportamiento_clientes_2024.csv
```

> The CSV is included in the `data/` folder so the notebook can be reproduced using the relative path above.

## Methods

- Data inspection and type validation
- Descriptive statistics
- Correlation heatmap
- Pairplot and regression scatterplots
- **Pearson correlation** for linear numerical relationships
- **Spearman correlation** as a robustness check for dispersed relationships and potential extreme values
- **Point-biserial correlation** for numerical–binary relationships
- **Cramér's V** for categorical associations

## Key Findings

### 1. Purchase frequency is the strongest revenue-related behavior

`compras_mes` and `ingreso_anual` show a **very strong positive Pearson correlation of 0.967**.

Customers who make more monthly purchases tend to generate substantially more annual revenue. However, the analysis does **not** establish that more purchases necessarily imply greater profitability because costs, margins, discounts, and returns are not available.

### 2. Premium customers generate more revenue per customer

Premium membership has only a **very weak positive point-biserial association** with annual revenue (`r = 0.093`), but the segment analysis shows:

| Segment | Average annual revenue | Share of total revenue |
| --- | ---: | ---: |
| Non-premium | 35.30 | 83.04% |
| Premium | 44.58 | 16.96% |

Premium customers represent about **13.9% of the customer base** but contribute **16.96% of total revenue**, indicating higher average revenue per customer.

### 3. Customer activity is more strongly related to advertising than to revenue

Key associations include:

- `visitas_mes` vs `gasto_publicidad_dirigida`: **Pearson 0.579**
- `visitas_mes` vs `compras_mes`: **Pearson 0.354 | Spearman 0.333**
- `visitas_mes` vs `ingreso_anual`: **Pearson 0.337 | Spearman 0.321**
- `gasto_publicidad_dirigida` vs `ingreso_anual`: **Pearson 0.20**

This suggests that monthly activity is moderately associated with targeted advertising spend, but only weakly associated with purchases and revenue.

## Limitations

- Correlation does not establish causation.
- Potential extreme values were observed but not formally evaluated with an outlier method.
- Revenue cannot be interpreted as profitability without cost and margin data.
- Most relationships were analyzed across the full customer base and may differ by segment.
- The dataset does not contain the intermediate stages needed for a complete conversion funnel.

## Next Steps

- Compare the main relationships between premium and non-premium customers.
- Segment further by age range, region, and device type.
- Add funnel stages between visits and purchases.
- Incorporate ticket size, costs, margins, discounts, and returns.
- Formally evaluate outliers and test the robustness of the correlation results.

## Repository Structure

```text
novaretail-customer-behavior/
├── README.md
├── novaretail_customer_behavior_analysis.ipynb
├── requirements.txt
├── .gitignore
└── data/
    ├── README.md
    └── novaretail_comportamiento_clientes_2024.csv
```

## Reproducibility

The dataset used in the analysis is included in the `data/` directory. Dependencies are listed in `requirements.txt`, and the notebook can be executed from top to bottom in Jupyter Notebook.

## Tools

Python, pandas, NumPy, Seaborn, Matplotlib, SciPy, Jupyter Notebook.
