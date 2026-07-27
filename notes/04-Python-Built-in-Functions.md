# 04 - Python Built-in Functions

## What are Built-in Functions?

Built-in functions are functions that Python provides by default.

We do not need to import them.

Examples:

- print()
- len()
- type()
- str()
- int()
- float()
- bool()
- input()
- dir()
- range()

---

## print()

Displays output on the screen.

```python
print("Hello")
```

Output

```
Hello
```

---

## type()

Returns the data type of an object.

```python
age = 27

print(type(age))
```

Output

```
<class 'int'>
```

---

## len()

Returns the number of characters or elements.

```python
print(len("Python"))
```

Output

```
6
```

```python
numbers = [10,20,30]

print(len(numbers))
```

Output

```
3
```

---

## str()

Converts data to string.

```python
age = 27

print(str(age))
```

Output

```
27
```

---

## int()

Converts data to integer.

```python
number = "15"

print(int(number))
```

Output

```
15
```

---

# Nested Functions

Python evaluates functions from the inside out.

Example

```python
print(len(str(12345)))
```

Evaluation

```
str(12345)
↓

"12345"

↓

len("12345")

↓

5

↓

print(5)
```

Output

```
5
```

Another example

```python
print(type(int("50")))
```

Evaluation

```
int("50")

↓

50

↓

type(50)

↓

<class 'int'>

↓

print(...)
```

---

# dir()

Shows available attributes and methods of an object.

Example

```python
print(dir(str))
```

or

```python
print(dir(__builtins__))
```

---

# __builtins__

Python automatically provides many functions.

Examples

- print()
- len()
- type()
- int()
- str()
- float()
- bool()
- input()
- range()

They are stored inside

```python
__builtins__
```

To display them

```python
print(dir(__builtins__))
```

---

# What I Learned

✅ Built-in functions

✅ Nested function execution

✅ Python evaluates functions from inside to outside

✅ dir()

✅ __builtins__

---

# Next Topic

Comparison Operators

==
!=
>
<
>=
<=