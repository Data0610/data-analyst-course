# Data Cleaning and Grouping with Pandas
Before you can extract valuable insights or train Machine Learning models, your data must be clean, organized, and structured. In this section, we will cover the essential data preparation and transformation techniques using Pandas.

## 🏷️ Efficiently Renaming Columns
Often, column names in raw datasets are long, contain spaces, or have strange characters. Pandas offers very efficient ways to standardize them.

```python
# 1. Rename specific columns using a dictionary
df = df.rename(columns={
    "Nombre del Cliente": "customer",
    "Ventas Totales ($)": "sales"
})

# 2. Bulk rename ALL columns (very efficient)
# Example: Convert everything to lowercase and replace spaces with underscores
df.columns = df.columns.str.lower().str.replace(' ', '_')
```

## 🕳️ Handling Missing Values (NaN)
Missing data is a daily reality in data science. Depending on the context, you can choose to remove them or "impute" them (fill them with other values).

```python
# 1. Remove rows containing ANY null value
clean_df = df.dropna()

# 2. Fill with a constant value (e.g., 0 or "Unknown")
filled_df = df.fillna(0)

# 3. Statistical strategy: Fill with the mean or median of that specific column
mean_age = df['age'].mean()
df['age'] = df['age'].fillna(mean_age)

# 4. Sequential strategy: Fill with the previous value (useful in time series)
time_df = df.fillna(method='ffill') # Forward fill
```

## 👯 Identifying and Removing Duplicate Entries
Repeated records can bias your analysis (for example, counting a single sale twice).

```python
# See how many total duplicate records exist
print("Duplicates:", df.duplicated().sum())

# Remove rows that are exact copies across all columns
df = df.drop_duplicates()

# Remove duplicates based ONLY on one column (e.g., transaction ID)
# keep='last' keeps the last occurrence; by default it keeps the first
df = df.drop_duplicates(subset=['transaction_id'], keep='last')
```

## Understanding and Applying Grouping Techniques
Grouping allows us to segment our data by categories to calculate metrics (sums, averages, counts) for each segment separately.

### The 3 Stages of Grouping (Split-Apply-Combine)
The grouping process in Pandas follows the famous Split-Apply-Combine logic:

- **Split**: The original dataset is divided into small groups based on the values of one or more keys (e.g., splitting data by "Country").
- **Apply**: A function is applied to each group independently (e.g., calculating the sum of "Sales").
- **Combine**: The results from each group are merged into a new data structure (a new summarized DataFrame).

### Performing Grouping in Pandas (groupby)
```python 
# Group by 'department' and calculate the average salary for each
salary_by_dept = df.groupby('department')['salary'].mean()

# Multiple grouping: Group by 'department' and 'position', counting how many employees there are
employee_count = df.groupby(['department', 'position'])['employee_id'].count()

# Advanced grouping with multiple metrics using .agg()
sales_summary = df.groupby('region').agg({
    'sales': 'sum',       # Total sum of sales per region
    'discount': 'mean',   # Average discount given
    'customer': 'nunique' # Count of UNIQUE customers
})
print(sales_summary)
```

## 🕵️ Sorting Data to Identify Outliers
A quick and simple way to find anomalies (outliers) in your data without using complex mathematics is simply to sort your values and check the extremes.

```python
# Sort from highest to lowest (descending) to see the top values
# Useful for finding, for example, unusually large purchases
high_values = df.sort_values(by='purchase_amount', ascending=False)
print("Top 5 highest values:\n", high_values.head())

# Sort from lowest to highest (ascending) to see the lowest values
# Useful for finding erroneous negative values or prices at 0
low_values = df.sort_values(by='purchase_amount', ascending=True)
print("\nTop 5 lowest values:\n", low_values.head())
```