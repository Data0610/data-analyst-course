# 🧮 Arithmetic Operators in Python

In Python, performing mathematical calculations is a very intuitive process. Next, we will explore what arithmetic operators are, their syntax, and how to use them in your programs.

## ❓ What is an arithmetic operator?
An **arithmetic operator** is a standard mathematical symbol that tells Python to perform a specific mathematical operation (such as addition, subtraction, multiplication, or division) between two values or pieces of data. 

## 📝 Syntax of operators in Python
Python defines and uses the following symbols for arithmetic operations:

* **Addition (`+`)**: Adds two values.
* **Subtraction (`-`)**: Subtracts the value on the right from the value on the left.
* **Multiplication (`*`)**: Multiplies two values.
* **Division (`/`)**: Divides the value on the left by the value on the right. (The result is always a decimal number or *float*).
* **Integer division (`//`)**: Performs the division but returns only the integer part, discarding the decimals.
* **Modulo (`%`)**: Returns the “remainder” or residue of a division.
* **Exponentiation (`**`)**: Raises the first value to the power of the second.
## 🚀 Ejecutar operaciones aritméticas básicas
Puedes usar Python directamente como una calculadora. En estos ejemplos, utilizamos la función `print()` para que el resultado de la operación se muestre en la pantalla.

```python
# Addition
print(5 + 3)      # Shows: 8

# Subtraction
print(10 - 2)     # Shows: 8

# Multiplication
print(4 * 2)      # Shows: 8

# Division
print(16 / 2)     # Shows: 8.0 

# Integer division
print(17 // 2)    # Shows: 8 (since 2 fits 8 times in 17)

# Modulus (Remainder)
print(17 % 3)     # Shows: 2 (since 17 = 3 * 5 + 2)

# Exponentiation
print(2 ** 3)     # Shows: 8 (2 cubed)
```

## 📦 Performing arithmetic operations with variables
In real projects, it is more common to store numbers in variables and perform operations using the names of those variables, rather than writing the numbers directly.

```python
# 1. We assign numerical values to the variables
price = 50
discount = 10
quantity = 3

# 2. We perform operations using the variables
final_price = price - discount
total_cost = final_price * quantity

# 3. We display the results
print(“The discounted price is:”, final_price)  # Shows: 40
print(“The total cost for 3 items is:”, total_cost)  # Shows: 120

# You can also update the value of a variable using its own current value:
score = 100
score = score + 50  # We add 50 to the original 100
print(“Updated score:”, score)  # Shows: 150
```