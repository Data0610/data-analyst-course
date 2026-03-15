# 🚀 Efficient Data Analysis with Pandas
Pandas is not only for cleaning data; it stands out for its tremendous efficiency when ingesting and exploring large volumes of information. Below, we will look at the key functionalities for loading and getting to know your datasets in depth.

## 📄 Reading CSV Files with Different Formats
The CSV (Comma-Separated Values) format is the gold standard for sharing data. However, in practice, CSV files come with different separators, different encodings, or irregular structures. The `pd.read_csv()` function is designed to handle all of these scenarios.

```python
import pandas as pd

# 1. Read a standard CSV (comma-separated)
df_standard = pd.read_csv("data.csv")

# 2. Read a semicolon-separated CSV (very common in Excel in Spanish-speaking regions)
df_semicolon = pd.read_csv("european_data.csv", sep=";")

# 3. Read a CSV specifying the encoding (useful to avoid errors with accents and special characters)
df_utf8 = pd.read_csv("spanish_data.csv", encoding="utf-8")

# 4. Read a CSV ignoring "junk" rows at the top and specifying it has no header
df_unformatted = pd.read_csv("dirty_data.csv", skiprows=3, header=None)
```

## Reading Data from Different Excel Sheets
Excel files (.xlsx) often contain multiple tabs or worksheets. Pandas allows you to access any of them, or even all of them at once, using the `pd.read_excel()` function.

```python
# Read the first sheet by default
df_excel = pd.read_excel("financial_report.xlsx")

# Read a specific sheet by its exact name
df_sales = pd.read_excel("financial_report.xlsx", sheet_name="Sales_Q1")

# Read a specific sheet by its position (index 1 is the second sheet)
df_expenses = pd.read_excel("financial_report.xlsx", sheet_name=1)

# Read ALL sheets at once (This returns a dictionary of DataFrames)
all_sheets = pd.read_excel("financial_report.xlsx", sheet_name=None)
```

## 🔍 Visualizing General Structure and Properties
Once the data is loaded, you need to inspect it. Pandas offers built-in tools to get an instant "X-ray" of your DataFrame without having to print thousands of rows on your screen. 

```python
# Show the dimensions of the dataset (returns a tuple: rows, columns)
print(df_sales.shape)

# View the data types of each column (int64 for integers, float64 for decimals, object for text)
print(df_sales.dtypes)

# Get a complete technical summary
# This is the most useful function for a first look! It shows columns, non-null values, and memory usage.
df_sales.info()
```

## 📈 Obtaining Basic Summary Statistics
For columns containing numbers (numerical features), it is vital to quickly understand their mathematical distribution. The .describe() method instantly calculates the most important descriptive statistics of your dataset.

```python
# Generate descriptive statistics for all numerical columns
statistical_summary = df_sales.describe()
print(statistical_summary)

"""
The .describe() method will automatically return the following for each column:
- count: Total number of data points (excluding null/empty values)
- mean: The average or arithmetic mean
- std: Standard deviation (how spread out the data is relative to the average)
- min / max: The minimum and maximum values recorded
- 25%, 50%, 75%: The quartiles (Note: 50% is exactly the median)
"""
```
