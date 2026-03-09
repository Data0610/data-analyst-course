# 🚦 Conditional Statements in Python

**Conditional statements** (or conditional declarations) allow your program to make decisions. They work by evaluating whether a specific condition is true (`True`) or false (`False`) and, based on that result, execute one block of code or another.

[Image of Python if else flowchart diagram]

In Python, conditional flow control is mainly handled with three keywords: `if`, `elif`, and `else`.

## 📌 1. The `if` statement
This is the most basic form of a conditional. It tells Python: *“If this condition is true, execute the following block of code. If it is false, skip it.”*

**Important note about syntax:** Python uses **indentation** (white space at the beginning of the line) to define which code belongs to the condition. Don't forget to put a colon (`:`) at the end of the condition.

```python
temperature = 30

# If the temperature is greater than 25, print is executed
if temperature > 25:
    print(“It's hot, don't forget to stay hydrated. 💧”)
    
# Code without indentation is always executed, regardless of the condition
print(“End of weather check.”)
```

## 🔀 2. The else statement (If not...)
It is used in combination with an if statement. It serves to catch any case in which the original if condition has been false.

```python
grade = 65
 
if grade >= 70:
    print(“Congratulations, you passed the exam! 🎉”)
else:
    print(“You didn't reach the minimum passing grade. Keep trying! 📚”)
```

## 🚥 3. The elif statement (Or else, if...)
Short for “else if.” It allows you to evaluate multiple different conditions, one after another, until you find one that is true. You can use as many elif statements as you need.

```python
age = 20

if age < 13:
    print(“You are a child.”)
elif age < 18:
    print(“You are a teenager.”)
elif age < 65:
    print(“You are an adult.”)
else:
    print(“You are a senior citizen.”)
```

In this example, Python evaluates the conditions in order. Since 20 is not less than 13, nor less than 18, but it is less than 65, it will print “You are an adult” and skip the rest.

## 🧩 4. Combining conditions with logical operators
You can evaluate more than one thing at the same time using the operators and, or, and not.

- **and**: Returns True if both conditions are true.
- **or**: Returns True if at least one condition is true.
- **not**: Reverses the result (from True to False and vice versa).

```python
has_ID = True
is_of_age = False

# Using AND
if has_ID and is_of_age:
    print(“You can enter the club.”)
else:
    print("Access denied. Requirements not met.")
    
# Using OR
day = “Saturday”
if day == “Saturday” or day == “Sunday”:
    print("It's the weekend! 🏖️")
```

## 5. Nested Conditionals
You can place an if statement inside another if statement. This is known as nesting, and it is useful for checking secondary conditions once a primary condition has been met.

```python
good_weather = True
have_money = True

if good_weather:
    print("We are going out.")
    # This if is only evaluated if good_weather is True
    if have_money:
        print("Let's go to a restaurant!")
    else:
        print("We'll go for a walk in the park (it's free).")
else:
    print("We're staying home to watch movies.")
```