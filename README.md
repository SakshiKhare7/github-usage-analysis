# GitHub Usage Analysis

This project analyzes GitHub usage data focusing on two primary services: "Shared Storage" and "Actions". The analysis includes visualizations to understand the usage patterns over time.

## Data Overview

The dataset used in this analysis contains the following columns:

- **Date**: The date of the recorded usage.
- **Product**: The type of product/service used ("Shared Storage" or "Actions").
- **SKU**: Stock Keeping Unit, represents the unique identifier for the product.
- **Quantity**: The amount of the product used.
- **Unit Type**: The unit of measurement for the product (e.g., gb-day, minute).
- **Price Per Unit ($)**: The cost per unit of the product.
- **Multiplier**: A multiplier applied to the quantity.
- **Owner**: The owner of the repository.
- **Repository Slug**: The identifier for the repository.
- **Username**: The username associated with the usage.
- **Actions Workflow**: The workflow file used in GitHub Actions.
- **Notes**: Additional notes regarding the usage.

Here is a snippet of the dataset:

| Date       | Product        | SKU            | Quantity | Unit Type | Price Per Unit ($) | Multiplier | Owner          | Repository Slug    | Username         | Actions Workflow                   | Notes                         |
|------------|----------------|----------------|----------|-----------|--------------------|------------|----------------|--------------------|------------------|------------------------------------|-------------------------------|
| 2023-12-05 | Shared Storage | Shared Storage | 0.0      | gb-day    | 0.008              | 1.0        |  SakshiKhare7 | API-Benchmarking   |                  |                                    |                               |
| 2023-12-06 | Shared Storage | Shared Storage | 0.0      | gb-day    | 0.008              | 1.0        |  SakshiKhare7 | API-Benchmarking   |                  |                                    |                               |
| 2023-12-07 | Actions        | Compute - UBUNTU| 1        | minute    | 0.008              | 1.0        |  SakshiKhare7 | open-sauced-goals  | SakshiKhare7  | .github/workflows/goals-caching.yml|                               |
| 2023-12-07 | Shared Storage | Shared Storage | 0.0      | gb-day    | 0.008              | 1.0        |  SakshiKhare7 | API-Benchmarking   |                  |                                    |                               |
| 2023-12-08 | Shared Storage | Shared Storage | 0.0      | gb-day    | 0.008              | 1.0        |  SakshiKhare7 | API-Benchmarking   |                  |                                    |                               |
| 2023-12-09 | Actions        | Compute - UBUNTU| 1        | minute    | 0.008              | 1.0        |  SakshiKhare7 | Leetcode-Submissions|  SakshiKhare7  | .github/workflows/sync_leetcode.yml|                               |
| 2023-12-09 | Shared Storage | Shared Storage | 0.0      | gb-day    | 0.008              | 1.0        | SakshiKhare7 | API-Benchmarking   |                  |                                    |                               |
| 2023-12-10 | Shared Storage | Shared Storage | 0.0      | gb-day    | 0.008              | 1.0        | SakshiKhare7 | API-Benchmarking   |                  |                                    |                               |
| 2023-12-11 | Actions        | Compute - UBUNTU| 1        | minute    | 0.008              | 1.0        | SakshiKhare7 | open-sauced-goals  |  SakshiKhare7   |                                    |                               |

## Analysis and Visualizations

### 1. Pie Chart: Proportion of Shared Storage and Actions Usage

This pie chart visualizes the proportion of usage between "Shared Storage" and "Actions".

```python
import pandas as pd
import matplotlib.pyplot as plt

# Group by 'Product' and sum the 'Quantity'
grouped_df = df.groupby('Product').sum()

# Plot a pie chart
plt.figure(figsize=(8, 8))
plt.pie(grouped_df['Quantity'], labels=grouped_df.index, autopct='%1.1f%%', startangle=90, colors=['skyblue', 'lightcoral'])
plt.title('Proportion of Shared Storage and Actions Usage')
plt.axis('equal')
plt.show()
```

### 2. Bar Graph: Quantity vs. Product

This bar graph shows the quantity of each product used.

```python
plt.figure(figsize=(10, 6))
plt.bar(grouped_df.index, grouped_df['Quantity'], color=['skyblue', 'lightcoral'])
plt.xlabel('Product')
plt.ylabel('Quantity')
plt.title('Quantity vs. Product')
plt.show()
```

### 3. Line Graph: Price Per Unit ($) vs. Date

This line graph shows the price per unit over the specified dates.

```python
# Convert 'Date' column to datetime type
df['Date'] = pd.to_datetime(df['Date'])

# Plotting
plt.figure(figsize=(10, 6))
plt.plot(df['Date'], df['Price Per Unit ($)'], marker='o', linestyle='-', color='b')
plt.xlabel('Date')
plt.ylabel('Price Per Unit ($)')
plt.title('Price Per Unit ($) vs. Date')
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

## Conclusion

This analysis provides insights into the usage patterns of GitHub services over a period of time. The visualizations help in understanding the distribution and trends of usage for "Shared Storage" and "Actions".

## Future Work

- **Detailed Usage Analysis**: Extend the analysis to include more detailed metrics and insights.
- **Cost Analysis**: Analyze the cost implications of the usage patterns.
- **Anomaly Detection**: Identify any anomalies or unusual patterns in the usage data.


