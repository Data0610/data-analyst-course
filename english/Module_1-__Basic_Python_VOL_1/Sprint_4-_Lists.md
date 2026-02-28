# 📋 Lists in Python

A **list** is a data structure that allows you to store an ordered collection of items in a single variable. Unlike strings, lists are **mutable**, which means you can modify them after you have created them.

## ➕ Creating lists and adding data to them
To create a list, simply enclose the elements in square brackets `[]` and separate them with commas. Lists can contain different types of data (numbers, strings, and even other lists).

```python
# Create an empty list
my_list = []

# Create a list with data
fruits = [“apple”, ‘banana’, “cherry”]
ages = [25, 30, 18, 42]
mix = [“text”, 45, True, 3.14]

# Add an element to the end of the list with .append()
fruits.append(“orange”)
print(fruits)  # Displays: [‘apple’, ‘banana’, ‘cherry’, ‘orange’]

# Insert an element at a specific position with .insert()
# (The first number is the index, the second is the value)
fruits.insert(1, “kiwi”)
print(fruits)  # Displays: [‘apple’, ‘kiwi’, ‘banana’, ‘cherry’, ‘orange’]
```

## ✂️ Sorting, Slicing, and Basic Modifications
Slicing
Slicing allows you to extract a portion or “sub-list” using the syntax [start:end]. Remember that the start index is included, but the end index is not included.

```python
letters = [“A”, “B”, “C”, ‘D’, “E”]

# Extract from index 1 to 3 (not including 4)
print(letters[1:4])  # Output: [‘B’, ‘C’, ‘D’]

# Extract from the beginning to index 2
print(letters[:3])   # Shows: [‘A’, ‘B’, ‘C’]

# Extract from index 2 to the end
print(letters[2:])   # Shows: [‘C’, ‘D’, ‘E’]
```

## Sorting
You can easily sort the elements of a list. If they are numbers, they will be sorted from smallest to largest; if they are strings, they will be sorted alphabetically.

```python
numbers = [4, 1, 8, 3]

# .sort() permanently modifies the original list
numbers.sort()
print(numbers)  # Output: [1, 3, 4, 8]

# To sort in reverse order (descending)
numbers.sort(reverse=True)
print(numbers)  # Output: [8, 4, 3, 1]
```
## Other modifications (Delete data)

```python
colors = [“red”, “blue”, ‘green’, “blue”]

# .remove() deletes the first occurrence of a specific value
colors.remove(“blue”)
print(colors)  # Displays: [‘red’, ‘green’, ‘blue’]

# .pop() removes and returns the element at the specified index (or the last one if not specified)
last_color = colors.pop()
print(colors)       # Output: [‘red’, ‘green’]
print(last_color)  # Output: ‘blue’
```

## Working with nested lists
A nested list is simply a list within another list. This is very useful for representing matrices, tables, or data grids.

```python
# Create a list of lists (3x3 matrix)
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# Access the first inner list
print(matrix[0])  # Displays: [1, 2, 3]

# Access a specific element (row 1, column 2)
# First we select the inner list, then the element within it
number_six = matrix[1][2]
print(number_six)  # Output: 6
```

## 🧹 Use list methods to preprocess strings
Lists and strings work very well together. It is common to convert a string into a list to clean or process it, and then rejoin it.

The key methods here are .split() (from string to list) and .join() (from list to string).


```python
# 1. We have a messy string or one from a CSV file
raw_data = “apple, pear,   grape , orange”

# 2. We split the string into a list using the comma as a delimiter
fruit_list = raw_data.split(“,”)
print(fruit_list)  # Shows: [‘apple’, ‘ pear’, ‘   grape ’, ‘ orange’]

# 3. We clean the white spaces from each element (simulating preprocessing)
# (Here we use a ‘list comprehension’, an advanced but very common technique)
clean_list = [fruit.strip() for fruit in fruit_list]
print(clean_list)  # Output: [‘apple’, ‘pear’, ‘grape’, ‘orange’]

# 4. We rejoin the list into a single string, separated by hyphens
new_string = “ - ”.join(clean_list)
print(new_string)  # Shows: apple - pear - grape - orange
```