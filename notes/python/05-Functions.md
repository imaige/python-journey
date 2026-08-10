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

## 6. `pass`

`pass` is a placeholder statement that does nothing.

It is useful when a function must exist syntactically but its real implementation has not been written yet.

```python
def greet():
    pass
```

A function without an explicit `return` returns `None` automatically.

```python
def greet():
    pass


print(greet())
# None
```

## 7. Function Arguments Are Object References

When an object is passed to a function, the parameter receives a reference to that object.

The important difference is not whether a reference is passed. References are used in both cases.

The important difference is whether the object is mutable or immutable.

## 8. Passing Immutable Objects

Common immutable types include:

- `int`
- `float`
- `str`
- `bool`
- `tuple`

Example:

```python
def change_number(x):
    x = 100


a = 10
change_number(a)
print(a)
# 10
```

At first, both names refer to the same integer object:

```text
a ───► 10 ◄─── x
```

But integers are immutable. The object `10` cannot be changed into `100` in place.

When this runs:

```python
x = 100
```

`x` is simply rebound to another object:

```text
a ───► 10
x ───► 100
```

The original variable `a` still refers to `10`.

## 9. Passing Mutable Objects

Common mutable types include:

- `list`
- `dict`
- `set`

Example:

```python
def add_item(items):
    items.append(4)


numbers = [1, 2, 3]
add_item(numbers)
print(numbers)
# [1, 2, 3, 4]
```

At function entry:

```text
numbers ─────┐
             ▼
          [1, 2, 3]
             ▲
items ───────┘
```

`append()` mutates the same list object in place, so the change is visible through `numbers` outside the function.

```text
numbers ─────┐
             ▼
        [1, 2, 3, 4]
             ▲
items ───────┘
```

## 10. Mutation vs Reassignment

This distinction is essential.

Mutation changes the existing object:

```python
items.append(4)
```

Reassignment changes what a variable name refers to:

```python
items = [9, 9, 9]
```

A function can rebind its local parameter without changing the caller's variable.

```python
def replace(items):
    items = [9, 9, 9]


numbers = [1, 2, 3]
replace(numbers)
print(numbers)
# [1, 2, 3]
```

## 11. Protecting an External Mutable Object with `copy()`

If a function should work with a list without modifying the original object, a copy can be created inside the function.

```python
def add_item(items):
    items = items.copy()
    items.append(4)


numbers = [1, 2, 3]
add_item(numbers)
print(numbers)
# [1, 2, 3]
```

The flow is:

```text
Before copy:

numbers ─────┐
             ▼
          [1, 2, 3]
             ▲
items ───────┘

After items = items.copy():

numbers ─────► [1, 2, 3]
items ───────► [1, 2, 3]

After items.append(4):

numbers ─────► [1, 2, 3]
items ───────► [1, 2, 3, 4]
```

The original list is protected because the function mutates its own copy.

For nested mutable objects, remember that `list.copy()` is a shallow copy. If full independence is required at every nested level, `copy.deepcopy()` may be needed.

## 12. `id()` and Object Identity

`id()` can help show whether two names refer to the same object.

For a mutable object, in-place mutation normally keeps the same object identity:

```python
numbers = [1, 2, 3]
print(id(numbers))

numbers.append(4)
print(id(numbers))
```

The list contents change, but the list object itself remains the same object.

For an immutable value, reassignment usually points the variable to a different object instead of changing the existing one.

## 13. Positional Arguments

With positional arguments, Python assigns values to parameters according to their order.

```python
def person(name, age):
    print(name, age)


person("Movsum", 27)
```

Conceptually:

```text
1st argument → name
2nd argument → age
```

Changing the order changes which parameter receives each value.

```python
person(27, "Movsum")
```

Python does not infer the intended meaning. It follows the argument positions.

## 14. Keyword Arguments

Keyword arguments explicitly name the parameter receiving each value.

```python
person(name="Movsum", age=27)
```

Because the parameter names are provided, the order can be changed:

```python
person(age=27, name="Movsum")
```

Mental model:

```text
Positional argument → matched by position
Keyword argument    → matched by parameter name
```

## 15. Variable Positional Arguments with `*args`

Sometimes a function should accept a variable number of positional arguments.

```python
def show_numbers(*args):
    print(args)


show_numbers(10, 20, 30)
# (10, 20, 30)
```

`*args` collects the extra positional arguments into a tuple.

```text
10, 20, 30
     ↓
   *args
     ↓
(10, 20, 30)
```

The name `args` is conventional, not mandatory. The `*` behavior is what matters.

```python
def show_numbers(*numbers):
    print(numbers)
```

A normal parameter can appear before `*args`:

```python
def person(name, *args):
    print(name)
    print(args)


person("Movsum", 27, "Baku", "SOC")
```

Result:

```text
name = "Movsum"
args = (27, "Baku", "SOC")
```

## 16. Variable Keyword Arguments with `**kwargs`

A function can also accept a variable number of keyword arguments.

```python
def person(**kwargs):
    print(kwargs)


person(name="Movsum", age=27, city="Baku")
```

Result:

```python
{
    "name": "Movsum",
    "age": 27,
    "city": "Baku"
}
```

`**kwargs` collects keyword arguments into a dictionary.

```text
name="Movsum"
age=27
city="Baku"
      ↓
   **kwargs
      ↓
{
  "name": "Movsum",
  "age": 27,
  "city": "Baku"
}
```

The name `kwargs` is conventional. The `**` behavior is what matters.

## 17. Using Normal Parameters, `*args`, and `**kwargs` Together

These patterns can be combined in one function.

```python
def info(name, *args, **kwargs):
    print(name)
    print(args)
    print(kwargs)


info(
    "Movsum",
    10,
    20,
    city="Baku",
    job="SOC"
)
```

Result:

```text
name = "Movsum"
args = (10, 20)
kwargs = {
    "city": "Baku",
    "job": "SOC"
}
```

The mental model is:

```text
normal parameter
→ receives its normal argument

*args
→ collects remaining positional arguments
→ tuple

**kwargs
→ collects remaining keyword arguments
→ dict
```

## 18. `*args` vs `**kwargs`

```text
*args
→ variable number of positional arguments
→ collected into a tuple

**kwargs
→ variable number of keyword arguments
→ collected into a dictionary
```

They are useful when a function needs to accept a flexible number of arguments.

## 19. Function Example

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

## Mental Model

```text
Function argument
      ↓
parameter receives a reference to the object
      ↓
Is the object mutable?

Immutable:
reassignment creates/references another object
original object is not changed

Mutable:
in-place mutation changes the shared object
caller can see the change

Need to protect the original mutable object?
make a copy before mutating it
```

Argument patterns:

```text
Positional argument → matched by order
Keyword argument    → matched by name
*args               → extra positional arguments → tuple
**kwargs             → extra keyword arguments → dict
```

## What I Learned

- How to create and call functions with `def`
- How parameters and arguments work
- How `return` sends a value back
- The difference between `print()` and `return`
- Why code after `return` does not run
- What `pass` does
- Why a function without `return` returns `None`
- That function parameters receive object references
- How immutable objects behave when passed to functions
- How mutable objects behave when passed to functions
- The difference between mutation and reassignment
- Why mutating a shared list inside a function affects the external object
- How `copy()` can protect an external mutable object
- How `id()` relates to object identity
- How positional arguments are matched by order
- How keyword arguments are matched by parameter name
- How `*args` collects variable positional arguments into a tuple
- How `**kwargs` collects variable keyword arguments into a dictionary
- How normal parameters, `*args`, and `**kwargs` can work together

## Practice Tasks

1. Create a function called `multiply` that accepts two numbers and returns their product.
2. Create a function called `full_name` that accepts a first name and last name and returns one complete string.
3. Create a function called `is_adult` that receives an age and returns the result of `age >= 18`.
4. Store a returned value in a variable and use it in another calculation.
5. Pass an integer to a function, reassign the parameter, and explain why the external variable does not change.
6. Pass a list to a function, mutate it with `append()`, and explain why the external list changes.
7. Repeat the previous task after copying the list inside the function and explain why the original stays unchanged.
8. Create a function with `*args` and verify that the collected value is a tuple.
9. Create a function with `**kwargs` and verify that the collected value is a dictionary.
10. Create a function with a normal parameter, `*args`, and `**kwargs`, then explain which arguments go to each part.
