# Python Functions, Expressions, Statements and Imports

## 1. Functions with `def`

A function is a reusable block of code. In Python, a function is created with the `def` keyword.

```python
def greet():
    print("Hello")
```

The function runs only when it is called:

```python
greet()
```

## 2. Function Parameters

Parameters allow a function to receive data.

```python
def greet(name):
    print("Hello", name)


greet("Movsum")
```

In this example, `name` is a parameter and `"Movsum"` is an argument.

## 3. The `return` Statement

`return` sends a value back from a function.

```python
def add(a, b):
    return a + b


result = add(5, 7)
print(result)
```

Output:

```text
12
```

### `print()` vs `return`

`print()` displays a value on the screen:

```python
def add(a, b):
    print(a + b)
```

`return` gives the value back so it can be stored or used later:

```python
def add(a, b):
    return a + b


number = add(5, 7)
print(number * 2)
```

Output:

```text
24
```

When Python reaches `return`, the function stops.

```python
def example():
    return 10
    print("This line will not run")
```

## 4. Expressions — Выражения

An expression is code that produces a value.

Examples:

```python
5 + 3
```

```python
10 > 4
```

```python
len("Python")
```

```python
add(2, 3)
```

Each expression produces a result.

## 5. Statements — Инструкции

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

A simple way to remember the difference:

- Expression produces a value.
- Statement performs an action.

## 6. Imports

Python has ready-made modules. The `import` statement makes a module available in the current program.

```python
import math

print(math.sqrt(25))
```

Output:

```text
5.0
```

Another example:

```python
import random

number = random.randint(1, 10)
print(number)
```

### Importing a specific item

```python
from math import sqrt

print(sqrt(36))
```

### Importing with an alias

```python
import math as m

print(m.sqrt(49))
```

## 7. Combined Example

```python
import math


def calculate_circle_area(radius):
    area = math.pi * radius ** 2
    return area


result = calculate_circle_area(5)
print(result)
```

In this example:

- `import math` is an import statement.
- `calculate_circle_area` is a function.
- `radius` is a parameter.
- `math.pi * radius ** 2` is an expression.
- `return area` returns the calculated result.
- `result = calculate_circle_area(5)` stores the returned value.

## 8. What I Learned

- How to create a function with `def`
- How to call a function
- How parameters and arguments work
- The difference between `print()` and `return`
- What expressions are
- What statements are
- How `import` works
- How to use standard-library modules

## 9. Practice Tasks

### Task 1

Create a function called `multiply` that accepts two numbers and returns their product.

### Task 2

Create a function called `full_name` that accepts a first name and a last name and returns one complete string.

### Task 3

Import the `math` module and create a function that returns the square root of a number.

### Task 4

For each line below, decide whether it is mainly an expression or a statement:

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
len("AI Engineer")
```
