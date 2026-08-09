# Python Type Conversion

## What is Type Conversion?

Type conversion means converting a value from one data type to another.

Python provides built-in classes such as:

```python
int()
float()
str()
bool()
complex()
list()
```

These can create new objects or convert compatible values.

## String to Integer

```python
number = int("100")

print(number)        # 100
print(type(number))  # <class 'int'>
```

The original value is a string, but `int()` returns an integer object.

## Integer to String

```python
age = 27
text = str(age)

print(text)        # 27
print(type(text))  # <class 'str'>
```

This is useful when combining numbers with text.

```python
age = 27
print("My age is " + str(age))
```

Without `str(age)`, Python raises a `TypeError` because a string and an integer cannot be concatenated directly.

## Integer and Float Conversion

```python
print(float(10))  # 10.0
print(int(10.9))  # 10
```

`int()` removes the decimal part. It does not round the number.

## Input Always Returns a String

```python
age = input("Enter your age: ")
print(type(age))  # <class 'str'>
```

Even when the user enters `27`, the result is still a string.

To use it as a number:

```python
age = int(input("Enter your age: "))
print(type(age))  # <class 'int'>
```

## Boolean Conversion

```python
bool(0)     # False
bool(1)     # True
bool("")    # False
bool(" ")   # True
```

## Invalid Conversion

Not every value can be converted.

```python
int("Movsum")
```

This raises a `ValueError` because `"Movsum"` does not represent an integer.

## Classes and Conversion

`int`, `str`, `bool`, and `list` are classes.

```python
number = int()
text = str()
items = list()
```

Results:

```text
number = 0
text = ""
items = []
```

The same object-creation principle applies to a custom class:

```python
class Car:
    pass

car = Car()
```

## What I Learned

- What type conversion means
- Converting between `str`, `int`, `float`, `bool`, and `complex`
- Why `input()` always returns a string
- Why strings and integers cannot be concatenated directly
- The difference between `TypeError` and `ValueError` in basic conversion examples
- Built-in types are classes that create objects

## Practice

Predict the type and value:

```python
a = int("25")
b = str(100)
c = float(7)
d = bool("")
e = int(9.8)
```
