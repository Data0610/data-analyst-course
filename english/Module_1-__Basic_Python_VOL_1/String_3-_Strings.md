# 🧵 Strings in Python

Text handling is one of the most common tasks in programming. In Python, text is represented by a data type called a **string**.

## 🔤 Basic characteristics of strings
* **Definition:** A string is a sequence of characters. They are created by enclosing the text in single quotes (`‘Text’`) or double quotes (`“Text”`). Both work exactly the same.
* **Immutability:** Strings in Python are **immutable**. This means that once you create a string, you cannot modify its internal characters individually (although you can always assign completely new text to the variable).

```python
greeting_1 = ‘Hello World’
greeting_2 = “Hello World”
# Both are valid and equivalent
```

## 📏 Calculating the length of strings
To find out exactly how many characters a string contains (counting letters, spaces, numbers, and symbols), we use the built-in function len() (from length).

```python
message = “Hello, GitHub”
length = len(message)
print(length) # Displays: 12 (The space and comma also count)
```

## 🏃‍♂️ Using escape characters
Sometimes you need to include special characters within a string, such as internal quotation marks or line breaks. To avoid confusing Python, we use the backslash \ as an escape character.

- \' or \" : Allows you to insert quotation marks within the text.
- \n : Creates a line break (Enter).
- \t : Creates a tab (indentation).

```python
# Using quotation marks within a string
quote = “He said: \”Python is great\“”

# Using line breaks and tabs
formatted_text = “Shopping list:\n\t- Apples\n\t- Bread”
print (formatted_text)
```

## 📜 Creating multi-line strings
If you have a very long text that spans several paragraphs, using \n can be tedious. Python allows you to create multi-line strings by enclosing the text between three single quotes (‘’') or three double quotes (“”").

```python
poem = “”"This is a text
that spans several lines
without the need to use
escape characters.“”"
print(poem)
```

## ✨ Formatting strings effectively
The most modern, readable, and efficient way to combine variables with text in Python is with f-strings (formatted strings). Just put an f before the quotation marks and place the variables between curly brackets {}.

```python
name = “Ana”
age = 28
# Using f-strings
introduction = f“Hello, my name is {name} and I am {age} years old.”
print(introduction) # Displays: Hello, my name is Ana and I am 28 years old.
```

## 🔍 Using indexes to access elements
You can access any individual character within a string using its index (its numerical position).

In Python, counting starts from zero (0).

You can also use negative indexes to count from the end backwards (where -1 is the last character).
```python
word = “PYTHON”

# Positive indexes (from left to right)
print(word[0])  # Displays: ‘P’ (First character)
print(word[3])  # Displays: ‘H’ (Fourth character)

# Negative indexes (from right to left)
print(word[-1]) # Displays: ‘N’ (Last character)
print(word[-2]) # Displays: ‘O’ (Penultimate character)
```

## Processing strings with specialized methods
Strings in Python come with built-in “powers” called methods, which allow you to easily transform and analyze them. Here are some of the most common ones:

```python
text = “Python is INcredible”

# .lower() - Converts everything to lowercase
print(text.lower())      # “  python is amazing  ”

# .upper() - Converts everything to uppercase
print(text.upper())      # “  PYTHON IS AMAZING  ”

# .strip() - Removes whitespace at the beginning and end
clean_text = text.strip()
print(clean_text)       # “Python is AMAZING”

# .replace() - Replaces part of the text with another
print(clean_text.replace(“AMAZING”, ‘easy’)) # “Python is easy”

# .split() - Splits the text into a list of words (separates by spaces by default)
words = clean_text.split()
print(words)           # [‘Python’, ‘is’, ‘INcredible’]
```