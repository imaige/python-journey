# Python Data Types

## Overview

This document summarizes the basic Python data types and functions I learned.

A data type describes what kind of value a variable stores and what operations can be performed on that value.

The main data types covered in this document are:

- integer
- float
- string
- boolean
- list
- dictionary

---

## 1. Integer

An integer is a whole number without a decimal point.

Examples:

```python
age = 27
year = 2026
temperature = -5
```

The Python type name for an integer is:

```text
int
```

Checking the type:

```python
age = 27

print(type(age))
```

Output:

```text
<class 'int'>
```

Integers can be used in mathematical operations.

Example:

```python
number1 = 10
number2 = 5

print(number1 + number2)
print(number1 * number2)
```

Output:

```text
15
50
```

---

## 2. Float

A float is a number that contains a decimal point.

Examples:

```python
weight = 82.5
price = 19.99
temperature = 36.6
```

The Python type name for a decimal number is:

```text
float
```

Checking the type:

```python
price = 19.99

print(type(price))
```

Output:

```text
<class 'float'>
```

Floats are commonly used for values such as:

- prices
- weight
- height
- percentages
- measurements
- AI model parameters

Example:

```python
temperature = 0.7
```

Here, `temperature` is a float.

---

## 3. String

A string represents text.

Strings are written inside quotation marks.

Examples:

```python
name = "Movsum"
job = "SOC Analyst"
city = "Baku"
```

The Python type name for text is:

```text
str
```

Checking the type:

```python
name = "Movsum"

print(type(name))
```

Output:

```text
<class 'str'>
```

---

## 4. String Concatenation

The `+` operator joins strings together.

Example:

```python
value1 = "10"
value2 = "5"

print(value1 + value2)
```

Output:

```text
105
```

Python does not perform addition here.

It joins the two strings:

```text
"10" + "5" = "105"
```

This operation is called:

```text
concatenation
```

---

## 5. String Repetition

A string can be repeated by multiplying it by an integer.

Example:

```python
value = "10"

print(value * 3)
```

Output:

```text
101010
```

This means:

```text
"10" + "10" + "10"
```

A string cannot be multiplied by another string.

This does not work:

```python
print("10" * "5")
```

It produces a `TypeError` because Python cannot use a string as the repetition count.

---

## 6. Type Conversion

Type conversion means changing a value from one data type to another.

The `int()` function converts a compatible value into an integer.

Example:

```python
number = int("10")

print(number)
print(type(number))
```

Output:

```text
10
<class 'int'>
```

The `str()` function converts a value into a string.

Example:

```python
number = 5
text = str(number)

print(text)
print(type(text))
```

Output:

```text
5
<class 'str'>
```

Type conversion is useful when values have different data types.

Example:

```python
number1 = "10"
number2 = 5

result = int(number1) + number2

print(result)
```

Output:

```text
15
```

---

## 7. Boolean

A boolean represents one of two logical values:

```text
True
False
```

The Python type name is:

```text
bool
```

Examples:

```python
is_admin = True
is_logged_in = False
is_malicious = True
```

Checking the type:

```python
is_admin = True

print(type(is_admin))
```

Output:

```text
<class 'bool'>
```

Boolean values are commonly used to represent answers such as:

- yes or no
- enabled or disabled
- logged in or logged out
- malicious or safe
- true or false

Python also connects boolean values with binary logic:

```text
1 = True
0 = False
```

Example:

```python
print(bool(1))
print(bool(0))
```

Output:

```text
True
False
```

---

## 8. List

A list stores multiple values in a specific order.

Example:

```python
numbers = [10, 20, 30, 40, 50]
```

A list can also store different data types.

Example:

```python
user_data = ["Movsum", 27, True, 82.5]
```

This is valid Python.

The values inside a list are called elements.

---

## 9. List Index

Each element in a list has a position called an index.

Python indexing starts from `0`.

Example:

```python
numbers = [10, 20, 30, 40, 50]
```

The indexes are:

```text
Index:  0   1   2   3   4
Value: 10  20  30  40  50
```

Accessing elements:

```python
print(numbers[0])
print(numbers[2])
print(numbers[4])
```

Output:

```text
10
30
50
```

Trying to access an index that does not exist produces an error.

Example:

```python
print(numbers[5])
```

Output:

```text
IndexError: list index out of range
```

This happens because the valid indexes are from `0` to `4`.

---

## 10. Negative Index

Negative indexes access list elements from the end.

Example:

```python
numbers = [10, 20, 30, 40, 50]
```

The negative indexes are:

```text
Index: -5  -4  -3  -2  -1
Value: 10  20  30  40  50
```

Example:

```python
print(numbers[-1])
print(numbers[-2])
```

Output:

```text
50
40
```

A useful way to remember it:

```text
-1 = last element
-2 = second-to-last element
```

---

## 11. Dictionary

A dictionary stores data using key-value pairs.

Example:

```python
user = {
    "name": "Movsum",
    "age": 27,
    "job": "SOC Analyst"
}
```

In this dictionary:

```text
"name" is a key
"Movsum" is its value
```

```text
"age" is a key
27 is its value
```

```text
"job" is a key
"SOC Analyst" is its value
```

A dictionary is useful when each value needs a clear name.

---

## 12. Accessing Dictionary Values

Dictionary values are accessed using their keys.

Example:

```python
user = {
    "name": "Movsum",
    "age": 27,
    "job": "SOC Analyst"
}

print(user["name"])
print(user["age"])
print(user["job"])
```

Output:

```text
Movsum
27
SOC Analyst
```

A dictionary is easier to understand than a list when the data has specific meanings.

For example:

```python
user = ["Movsum", 27, "SOC Analyst"]
```

To understand `user[1]`, the programmer must remember what index `1` represents.

With a dictionary:

```python
user["age"]
```

The meaning is immediately clear.

---

## 13. `type()`

The `type()` function shows the data type of a value or variable.

Examples:

```python
age = 27
weight = 82.5
name = "Movsum"
is_admin = True

print(type(age))
print(type(weight))
print(type(name))
print(type(is_admin))
```

Output:

```text
<class 'int'>
<class 'float'>
<class 'str'>
<class 'bool'>
```

---

## 14. `input()`

The `input()` function receives information from the user.

Example:

```python
name = input("Enter your name: ")
```

An important rule:

```text
input() always returns a string
```

Example:

```python
age = input("Enter your age: ")

print(type(age))
```

Even if the user enters:

```text
27
```

the type will still be:

```text
<class 'str'>
```

To use the input as an integer, it must be converted.

Example:

```python
age = int(input("Enter your age: "))

print(type(age))
```

Output:

```text
<class 'int'>
```

---

## Complete Example

```python
name = input("Enter your name: ")
age = int(input("Enter your age: "))
weight = 82.5
is_student = False

skills = ["Python", "Git", "Linux"]

user = {
    "name": name,
    "age": age,
    "weight": weight,
    "is_student": is_student,
    "skills": skills
}

print(user["name"])
print(user["age"])
print(user["skills"][-1])
```

This example demonstrates:

- string
- integer
- float
- boolean
- list
- dictionary
- user input
- type conversion
- list indexing
- dictionary keys

---

## What I Understand Now

I can explain:

- what an integer is
- what a float is
- what a string is
- what a boolean is
- what a list is
- what a dictionary is
- why list indexing starts from zero
- how negative indexes work
- how to access dictionary values using keys
- what string concatenation means
- how string repetition works
- what type conversion is
- how to use `int()` and `str()`
- what the `type()` function does
- why `input()` always returns a string
- why an invalid list index produces an `IndexError`

## Next Python Topics

- comparison operators
- `if`
- `elif`
- `else`
- list methods
- dictionary methods