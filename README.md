# Data

This folder contains the dataset used in the analysis:

```text
novaretail_comportamiento_clientes_2024.csv
```

The notebook loads it using a relative path:

```python
pd.read_csv('data/novaretail_comportamiento_clientes_2024.csv')
```

The dataset contains 15,000 customer-level records and 12 variables covering demographics, monthly activity, targeted advertising, premium membership, churn status, device type, region, and annual revenue generated per customer.
