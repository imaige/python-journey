# Python Expressions vs Statements

## Terminology

In Russian-language courses:

- Expression = **выражение**
- Statement = **инструкция**

These concepts are related, but they are not the same.

## 1. Expressions

An expression is code that produces a value.

Examples:

```python
5 + 3
```

This produces:

```text
8
```

```python
10 > 4
```

This produces:

```text
True
```

```python
len("Python")
```

This produces:

```text
6
```

A function call can also be an expression when it returns a value:

```python
def add(a, b):
    return a + b


add(2, 3)
```

The expression produces `5`.

## 2. Statements

A statement is an instruction that tells Python to perform an action.

Examples:

```python
name = "Movsum"
```

```python
print(name)
```

```python
import math
```

```python
def greet():
    print("Hello")
```

## 3. Main Difference

A simple way to remember the difference:

- An expression produces a value
- A statement performs an action

## 4. Expressions Inside Statements

A statement can contain an expression.

```python
result = 5 + 3
```

Here:

- `5 + 3` is an expression because it produces `8`
- `result = 5 + 3` is an assignment statement because it stores the value

Another example:

```python
print(len("Python"))
```

Python evaluates it from the inside out:

1. `"Python"` is passed to `len()`
2. `len("Python")` produces `6`
3. `print(6)` displays the result

## 5. More Examples

```python
age = 27
```

Mainly a statement.

```python
age >= 18
```

An expression that produces `True` or `False`.

```python
full_name = first_name + " " + last_name
```

- `first_name + " " + last_name` is an expression
- The complete line is an assignment statement

## What I Learned

- An expression produces a value
- A statement tells Python to perform an action
- Expressions can exist inside statements
- Function calls may be expressions when they return values
- Nested expressions are evaluated from the inside out

## Practice Tasks

For each line, identify the expression and the complete statement where applicable:

```python
5 * 10
```

```python
age = 27
```

```python
print(age)
```

```python
name_length = len("AI Engineer")
```

```python
is_logged_in = user_name == "Movsum"
```