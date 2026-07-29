# Python Functions

## 1. What Is a Function?

A function is a reusable block of code that performs a specific task.

In Python, a function is created with the `def` keyword.

```python
def greet():
    print("Hello")
```

A function runs only when it is called:

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

In this example:

- `name` is a parameter
- `"Movsum"` is an argument

## 3. Returning a Value with `return`

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

## 4. `print()` vs `return`

`print()` only displays a value on the screen.

```python
def add(a, b):
    print(a + b)
```

`return` gives the value back so it can be stored and used later.

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

## 5. `return` Stops the Function

When Python reaches `return`, the function stops.

```python
def example():
    return 10
    print("This line will not run")
```

The `print()` line does not run because it comes after `return`.

## 6. Function Example

```python
def calculate_total(price, quantity):
    total = price * quantity
    return total


result = calculate_total(15, 3)
print(result)
```

In this example:

- `calculate_total` is the function name
- `price` and `quantity` are parameters
- `15` and `3` are arguments
- `price * quantity` calculates the value
- `return total` sends the result back

## What I Learned

- How to create a function with `def`
- How to call a function
- How parameters and arguments work
- How `return` sends a value back
- The difference between `print()` and `return`
- Why code after `return` does not run

## Practice Tasks

1. Create a function called `multiply` that accepts two numbers and returns their product.
2. Create a function called `full_name` that accepts a first name and last name and returns one complete string.
3. Create a function called `is_adult` that receives an age and returns the result of `age >= 18`.
4. Store a returned value in a variable and use it in another calculation.