# Data Analysis with Pandas

Pandas is an open-source Python library built on top of NumPy. It provides fast, flexible, and expressive data structures (such as the **DataFrame** and **Series**) designed to work with structured data (tabular, multidimensional, etc.) intuitively.

Before starting, remember that you must always **import** the library at the beginning of your script:

```python
import pandas as pd
```

## 🔬 Preprocessing and Initial Analysis
When you load a dataset for the first time, you need to understand its shape, size, and basic content before manipulating it. Pandas offers quick methods for this "initial look."

```python
# Assuming we have already loaded a DataFrame called 'df'

# 1. View the first and last rows
print(df.head())    # Shows the first 5 rows by default
print(df.tail(3))   # Shows the last 3 rows
print(df.sample(5)) # Shows 5 random rows

# 2. Understand structure and data types
print(df.shape)     # Returns a tuple (rows, columns), e.g., (1000, 15)
print(df.info())    # Technical summary: column names, data types, and non-null values

# 3. Quick descriptive statistics
print(df.describe()) # Calculates mean, std dev, min, max, and quartiles for numerical columns
```

## 📖 Advanced Reading and Processing Techniques
Often, raw data does not come in a perfect format. The `pd.read_csv()` function (and its equivalents for Excel, SQL, JSON) has powerful parameters to process data while you read it, saving you a lot of subsequent work.

```python
# Advanced reading of a CSV file
sales_df = pd.read_csv(
    "sales_2023.csv",
    sep=";",                     # If the file is semicolon-separated instead of comma-separated
    usecols=["Date", "Total"],   # Load only specific columns to save memory
    parse_dates=["Date"],        # Automatically convert the 'Date' column to datetime format
    index_col="Date"             # Use the 'Date' column as the DataFrame index
)

# Advanced processing: Applying custom functions to columns
# The .apply() method executes a function on every element of a series
sales_df['Total_with_VAT'] = sales_df['Total'].apply(lambda x: x * 1.16)
```

## Managing Missing and Duplicate Data
In the real world, data is messy. There are missing values (represented as NaN or nulls) and repeated records. Cleaning this up is 80% of a data analyst's job.

### Missing Data (NaN)

```python
# 1. Identify null values
print(df.isna().sum())  # Counts how many null values exist per column

# 2. Drop rows with null values (Useful if there are few)
clean_df = df.dropna()                 # Drops any row containing at least one NaN
clean_df = df.dropna(subset=["Total"]) # Drops the row only if data is missing in the "Total" column

# 3. Fill null values (Imputation)
# Fill with a fixed value (e.g., 0) or with the mean/median of the column
mean_sales = df['Total'].mean()
df['Total'] = df['Total'].fillna(mean_sales)
```

### Duplicate Data
```python
# 1. Identify if there are identical rows
print(df.duplicated().sum()) # Counts the total number of duplicate rows

# 2. Remove duplicates (Keeps the first occurrence by default)
df = df.drop_duplicates()
```

## 🎯 Filtering Data with Sophisticated Methods
Filtering in Pandas goes far beyond selecting a column. You can use boolean indexing and built-in methods for complex queries.

```python
# 1. Filtering by multiple conditions (Boolean Indexing)
# We use & (AND) and | (OR). Parentheses for each condition are mandatory!
filter_cond = (df['Age'] > 25) & (df['Department'] == 'Sales')
young_sales_employees = df[filter_cond]

# 2. The .isin() method (Useful for searching for multiple specific values)
target_countries = ["Mexico", "Colombia", "Spain"]
countries_df = df[df['Country'].isin(target_countries)]

# 3. The .query() method (Cleaner string-based syntax)
# Allows writing SQL-like queries, making the code very readable
filtered_df = df.query("Age > 25 and Department == 'Sales'")

# 4. Structural filtering with .loc and .iloc
# .loc: Filters by row and column LABELS (names)
# .iloc: Filters by row and column NUMERICAL INDICES (integer positions)

# Get all rows for VIP customers, but only show Name and Email columns
vip_data = df.loc[df['Category'] == 'VIP', ['Name', 'Email']]

# Get the first 10 rows and the first 3 columns (using positions)
first_records = df.iloc[:10, :3]
```


