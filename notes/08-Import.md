# Python Imports and Modules

## 1. What Is `import`?

Python includes ready-made modules. A module contains code, functions, variables, and other tools that can be reused.

The `import` statement makes a module available in the current program.

```python
import math
```

After importing the module, its tools can be used with the module name.

```python
import math

print(math.sqrt(25))
```

Output:

```text
5.0
```

## 2. Using a Module

The syntax is:

```python
module_name.item_name
```

Example:

```python
import math

print(math.pi)
print(math.sqrt(36))
```

## 3. Importing a Specific Item

A specific function or value can be imported from a module.

```python
from math import sqrt

print(sqrt(36))
```

Because `sqrt` was imported directly, `math.sqrt()` is not required in this example.

## 4. Importing with an Alias

A module can be given a shorter name with `as`.

```python
import math as m

print(m.sqrt(49))
```

Here, `m` is an alias for the `math` module.

## 5. The `random` Module

The `random` module can generate random values.

```python
import random

number = random.randint(1, 10)
print(number)
```

`randint(1, 10)` returns a random integer from 1 through 10.

## 6. Combined Example with a Function

```python
import math


def calculate_circle_area(radius):
    area = math.pi * radius ** 2
    return area


result = calculate_circle_area(5)
print(result)
```

In this example:

- `import math` loads the module
- `math.pi` gets the value of pi from the module
- `radius ** 2` is an expression
- `return area` sends the calculated value back

## 7. Important Notes

- Imports are usually written at the top of the file
- Use clear module names
- Import only what the program needs
- Python's standard library contains many built-in modules
- External packages may need to be installed before they can be imported

## What I Learned

- What a module is
- What the `import` statement does
- How to use `module.item`
- How `from module import item` works
- How to create an alias with `as`
- How functions and imported modules can be used together

## Practice Tasks

1. Import `math` and display the square root of `81`.
2. Import `sqrt` directly from `math` and use it without writing `math.sqrt()`.
3. Import `random` and generate a number from 1 to 100.
4. Create a function that receives a number and returns its square root using `math`.
5. Import `math` with the alias `m` and display `m.pi`.