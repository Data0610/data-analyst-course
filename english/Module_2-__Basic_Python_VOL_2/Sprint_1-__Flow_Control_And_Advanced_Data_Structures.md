# 🔄 Flow Control and Advanced Data Structures

Once you have mastered lists, the next step is to manipulate them dynamically and structure information more intelligently.

## 🔁 Iterating over tables and modifying values
In Python (without using external libraries), a “table” is commonly represented as a **list of lists**, where each sub-list is a row. 

To modify data, we iterate over each row using a `for` loop. Since lists are mutable, any changes you make inside the loop will affect the original table.

```python
# Sales table: [Product, Price, Quantity]
sales = [
    [“Shirt”, 20.0, 50],
    [“Pants”, 30.0, 30],
    [“Shoes”, 50.0, 10]
]

# Objective: Apply a 10% tax to the ‘Price’ column (index 1)
print(“--- Before ---”)
print(sales)

for row in sales:
    current_price = row[1]
    # Modify the value directly in the row
    row[1] = current_price * 1.10 

print(“\n--- After (Prices with tax) ---”)
print(sales) 
# Shows the updated prices: 22.0, 33.0, 55.0
```

## 🔍 Complex filters with conditional statements
We often need to extract specific information based on multiple criteria. To do this, we combine the for loop with if statements and logical operators (and, or, not).

```python
employees = [
    # [Name, Department, Salary, Years_of_Service]
    [“Ana”, “Sales”, 3000, 5],
    [“Luis”, “IT”, 4500, 2],
    [“Marta”, “Sales”, 3200, 1],
    [“Carlos”, “IT”, 2900, 6]
]

promotion_candidates = []

# Filter rule: IT department ‘OR’ (or) more than 4 years of seniority
# ‘AND’ (and) salary less than 4000.
for emp in employees:
    dept = emp[1]
    salary = emp[2]
    seniority = emp[3]
    
    if (dept == “IT” or seniority > 4) and salary < 4000:
        promotion_candidates.append(emp)

print(“Candidates for promotion:”, promotion_candidates)
# Result: Ana (Seniority) and Carlos (IT and low salary)
```

## 📖 Storing and organizing data with dictionaries
While lists use numerical indexes (0, 1, 2...), dictionaries allow us to organize data using keys (descriptive names) and values. They are ideal for representing real-world objects or database records.

Syntax: Curly brackets {} and the key:value structure are used.

```python
# A dictionary representing a single product
product = {
    “name”: “Gaming Laptop,”
    “price”: 1500,
    “available”: True,
    “colors”: [“Black,” “Red”]  # A value can be a list
}

# Access data by its key (much more readable than using indexes)
print(product[“name”])  # Displays: Gaming Laptop

# Modify values
product[“price”] = 1400

# Add new information
product[“warranty”] = “2 years”

print(product)
```


## ⚙️ Handling large amounts of data with Functions
When working with large amounts of data, writing the same code over and over again is inefficient and prone to errors. Functions allow you to encapsulate complex logic in a reusable block.

Advantages:

- Reusability: You write the code once, use it a thousand times.
- Organization: Break large problems down into small parts.
- Readability: Your main code becomes easier to read.

```python
# We define a function to process data
def calculate_average(list_of_numbers):
    if len(list_of_numbers) == 0:
        return 0
    total = sum(list_of_numbers)
    average = total / len(list_of_numbers)
    return average

# Massive data (simulated)
north_region_data = [10, 20, 30, 40, 50]
south_region_data = [5, 15, 25, 35, 45, 55, 65]

# We use the function to process different data sets
north_average = calculate_average (north_region_data)
south_average = calculate_average(south_region_data)

print(f“North Average: {north_average}”)
print(f“South Average: {south_average}”)
```