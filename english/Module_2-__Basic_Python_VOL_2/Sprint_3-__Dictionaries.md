# 📖 Python Dictionaries

When working with structured data, dictionaries are one of the most powerful and efficient tools Python offers. Below, we will explore what they are, how they compare to lists, and how to manipulate them.

## 🧠 What are Dictionaries?
A Python dictionary is a data structure that stores information in key-value pairs.
Imagine a real-world dictionary: you look up a word (the key) to find its definition (the value). In Python, keys must be unique, and values can be any data type (numbers, strings, lists, and even other dictionaries).

They are defined using curly braces `{}` and by separating the key from the value with a colon `:`.

```python
# Example of a dictionary representing a user
user = {
    "name": "Carlos",
    "age": 28,
    "profession": "Data Analyst",
    "is_active": True
}
```

## ⚖️ Dictionaries vs. Lists
Although both are used to store collections of data, they serve different purposes:

| Feature| Lists [] | Dictionaries {} |
|----------|----------|----------|
| Organization    | Ordered collection of elements. | Collection of key-value pairs. |
| Access    | "Accessed via numerical indices (0, 1, 2...)."  | Accessed via descriptive keys (names).  |
| Ideal Use    | "Storing sequences of similar data (e.g., a list of temperatures)."   | "Representing entities or objects with attributes (e.g., customer data)."   |

```python
# In a list, you must remember what each position represents:
user_list = ["Carlos", 28, "Analyst"]
print(user_list[1]) # You have to know that index 1 is the age

# In a dictionary, access is explicit and clear:
print(user["age"]) # It is obvious which data point you are retrieving
```

## 🔍 Retrieving Values from Dictionaries
There are two main ways to extract information from a dictionary:

- Using square brackets []: This is direct, but if the key does not exist, your program will throw an error (KeyError) and stop.

- Using the .get() method: This is the safer way. If the key does not exist, it returns None (or a default value of your choice) instead of crashing the program.

```python
team = {
    "name": "Cubs",
    "city": "Chicago",
    "championships": 3
}

# 1. Using square brackets
print(team["city"]) # Output: Chicago

# 2. Using .get()
print(team.get("championships")) # Output: 3

# If we look for something that doesn't exist with .get()
print(team.get("stadium", "Stadium not registered")) # Output: Stadium not registered
```

## ➕➖ Adding and Removing Elements
Dictionaries are mutable, meaning you can modify them at any time after they have been created.

### Adding or Modifying
To add a new key-value pair, simply assign a value to a new key. If the key already exists, its value will be updated (overwritten).

```python
profile = {"user": "Ana", "points": 150}

# Add a new element
profile["level"] = "Advanced"

# Update (modify) an existing element
profile["points"] = 200

print(profile) 
# Output: {'user': 'Ana', 'points': 200, 'level': 'Advanced'}
```

### Removing
You can delete elements using the `del` keyword or the `.pop()` method (which also returns the deleted value).

```python
inventory = {"apples": 10, "oranges": 5, "pears": 8}

# Remove with 'del'
del inventory["oranges"]

# Remove with '.pop()' and store the value
pears_count = inventory.pop("pears")

print(inventory)    # Output: {'apples': 10}
print(pears_count)  # Output: 8
```

## 🛠️ Working with Results (Iteration Methods)
When you need to process all the data in a dictionary, you can use for loops along with three very useful methods:

- `.keys()`: Returns only the keys.
- `.values()`: Returns only the values.
- `.items()`: Returns both (keys and values) at the same time.

```python
grades = {
    "Math": 9.5,
    "History": 8.0,
    "Science": 9.0
}

# 1. Iterate over keys (this is the default behavior)
print("Subjects:")
for subject in grades.keys():
    print(f"- {subject}")

# 2. Iterate over values (e.g., to calculate an average)
total = sum(grades.values())
average = total / len(grades)
print(f"\nOverall Average: {average}")

# 3. Iterate over keys and values at once (.items())
print("\nReport Card:")
for subject, score in grades.items():
    print(f"{subject}: {score}")
```