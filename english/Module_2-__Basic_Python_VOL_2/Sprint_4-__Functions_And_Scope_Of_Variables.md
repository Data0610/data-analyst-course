# 🛠️ Functions and Variable Scope
As your programs grow, writing the same code over and over becomes unsustainable. This is where functions come in, allowing you to package blocks of code to reuse them and optimize your processes.

## 🏗️ Creating Your Own Functions
A function is a block of code with a name that performs a specific task. To create (or "define") a function in Python, we use the def keyword, followed by the function name, parentheses `()`, and a colon `:`.

You can pass information to the function inside the parentheses; these are called parameters or arguments.

```python
# Defining the function
def greet_user(name):
    print(f"Hello, {name}! Welcome to the system.")

# Calling the function (executing it)
greet_user("Ana")    # Output: Hello, Ana! Welcome to the system.
greet_user("Carlos") # Output: Hello, Carlos! Welcome to the system.
```

## 📤 Using the return Keyword
It is very important to understand the difference between printing a value (print) and returning a value (return).

- `print()` simply displays something on the screen for a human to read.
- `return` makes the function send a real data point back to the program, so you can save it in a variable or use it in another calculation. When Python reads a return, the function ends immediately.

```python
def calculate_rectangle_area(base, height):
    area = base * height
    return area # Returns the calculated value

# We store the result of the function in a variable
result = calculate_rectangle_area(5, 10)

# Now we can use that result for other things
cost_per_meter = 15
total_cost = result * cost_per_meter

print(f"The area is {result} and the total cost will be ${total_cost}")
```

## 🌍 Global vs. Local Variables
In Python, the place where you create a variable determines where you can use it. This is called scope.

- `Global Variable`: Created outside of any function. It can be read and used by any part of your code, including inside functions.

- `Local Variable`: Created inside a function. It only exists while that function is running. Once the function finishes, the local variable disappears. The rest of the program does not know it exists.

```python
# GLOBAL Variable (created in the main body of the code)
global_tax = 0.16 

def calculate_final_price(price):
    # LOCAL Variable (created inside the function)
    local_discount = 20 
    
    # The function can use both the local AND the global variable
    price_with_discount = price - local_discount
    final_price = price_with_discount * (1 + global_tax)
    return final_price

print(calculate_final_price(100))

# ❌ THIS WILL CAUSE AN ERROR:
# print(local_discount) 
# NameError: name 'local_discount' is not defined (Because it only exists inside the function)
```

## ⚡ Optimizing Code for Large Amounts of Data
When working with data analysis (lists with thousands or millions of records), using functions is key for optimization and performance:

- `Avoid repetition`: Instead of writing the same mathematical formula in different parts of your code, you call a single function. If there is an error in the formula, you only have to fix it in one place.

- `Batch processing (List Comprehensions)`: You can apply a function to all elements of a large list very efficiently by combining it with advanced Python techniques.

```python
# We have a huge list of raw prices
raw_prices = [10.5, 20.0, 15.75, 40.2, 5.99] # Imagine there are thousands

# We define a cleaning/transformation function
def apply_inflation(price):
    new_price = price * 1.05
    return round(new_price, 2)

# We optimize processing by applying the function to the entire list compactly
updated_prices = [apply_inflation(p) for p in raw_prices]

print(updated_prices) 
# Output: [11.02, 21.0, 16.54, 42.21, 6.29]
```