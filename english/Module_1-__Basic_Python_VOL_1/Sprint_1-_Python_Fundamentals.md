## 🐍 Python Fundamentals
A quick guide to Python basics, ideal for beginners and data professionals.

## 📌 What is Python?
Python is one of the most popular programming languages in the world, widely used and highly valued, especially by data professionals. It stands out for its readability and versatility.

## 📝 Syntax
Syntax is the set of rules that define how Python code is written and interpreted. Clean and correct syntax is essential for the computer to understand which actions it should execute.

## 🖨️ The `print` Command
The `print()` function is used to display messages or results on the screen. It is one of the most basic and useful tools for interacting with your code.

```python
# Usage example:
print("Hello1, GitHub!")
```

## 📦 Variables
A variable is a container designed to store data values. It is created by assigning it a name and a specific value.

### Assignment Operator
To store data inside a variable, we use the assignment operator, which is the = symbol.
 
```python
# Creating a variable and assigning it a value
age = 25
```

## Descriptive Variable Names
It is a best practice to use variable names that clearly describe the value they store. This significantly improves code readability and maintenance.

```python
# ❌ Bad Example (not descriptive)
x = "María"

# ✅ Good Example (descriptive)
customer_name = "María"
```


## Variable Reassignment
Variables in Python are dynamic, which means you can reassign or change the value stored in a variable at any time by assigning it a new value.

```python
score = 10
print(score) # Displays: 10

score = 15   # Reassignment
print(score) # Displays: 15
```

## Case Sensitivity
Python is case sensitive. This means that it treats variable names that differ in their capitalization as completely different containers.

```python
My_Variable = 100
my_variable = 50

# These are two separate variables.
```

## Valid variable names
For Python to accept a variable name, you must follow these strict rules:

It must start with a letter (a-z, A-Z) or an underscore (_).

It cannot start with a number.

It can only contain letters, numbers, and underscores (A-z, 0-9, and _).

System reserved words (such as print, if, for) cannot be used.

```python
# ✅ Valid Names:
my_variable = 1
_secret_variable = 2
user_1 = “Juan”

# ❌ Invalid Names:
# 1_user = “Juan”  (Starts with a number)
# my-variable = 1     (Contains a hyphen)
```