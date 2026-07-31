# Magic Methods and OOP Basics

## Classes and Objects

A **class** is a blueprint used to create objects.

```python
class Car:
    pass
```

`Car` is the class. `pass` means that the class body is currently empty.

```python
car = Car()
```

`car` is an object, also called an instance, created from the `Car` class.

Python's built-in types are also classes:

```python
number = int()   # int object with value 0
text = str()     # str object with value ""
items = list()   # list object with value []
car = Car()      # Car object
```

## Magic Methods

Magic methods, also called dunder methods, have double underscores before and after their names. Python calls them automatically in specific situations.

Examples:

```python
10 + 5
10.__add__(5)
```

```python
"Python" * 3
"Python".__mul__(3)
```

Both multiplication examples produce:

```text
PythonPythonPython
```

Common magic methods:

- `__add__()` controls the `+` operator.
- `__mul__()` controls the `*` operator.
- `__len__()` is used by `len()`.
- `__str__()` provides a readable string representation.
- `__init__()` initializes a newly created object.

## Defining Operator Behavior

A custom class does not automatically know how its objects should be added.

```python
class Car:
    pass

car1 = Car()
car2 = Car()

# car1 + car2 raises TypeError
```

We can define the behavior of `+` with `__add__()`:

```python
class Car:
    def __add__(self, other):
        return "Two cars were combined."

car1 = Car()
car2 = Car()

print(car1 + car2)
```

When Python evaluates `car1 + car2`, it effectively calls:

```python
car1.__add__(car2)
```

In this call:

- `self` refers to `car1`.
- `other` refers to `car2`.

## The `__init__()` Method

`__init__()` runs automatically immediately after a new object is created.

```python
class Car:
    def __init__(self, brand, year):
        self.brand = brand
        self.year = year
```

Now objects can receive data when they are created:

```python
car = Car("Hyundai", 2017)
```

During this call:

```text
self  -> the new Car object
brand -> "Hyundai"
year  -> 2017
```

These lines save the incoming values inside the object:

```python
self.brand = brand
self.year = year
```

The left side is an object attribute. The right side is a parameter containing incoming data.

After initialization, the object contains:

```text
Car object
brand = Hyundai
year = 2017
```

The values can be accessed later:

```python
print(car.brand)
print(car.year)
```

## Understanding `self`

`self` refers to the object that is currently using the method.

```python
class Human:
    def __init__(self, name):
        self.name = name

    def say_hello(self):
        print(f"Hello, I am {self.name}.")

person = Human("Movsum")
person.say_hello()
```

When this is written:

```python
person.say_hello()
```

Python effectively performs:

```python
Human.say_hello(person)
```

Therefore, the object does not need to be passed manually inside the parentheses. Python passes it as `self` automatically.

## Attributes and Methods

An **attribute** stores information about an object:

```python
self.name
self.brand
self.year
```

A **method** defines an action the object can perform:

```python
def say_hello(self):
    ...
```

```python
def start_engine(self):
    ...
```

## f-Strings

An f-string allows Python expressions to be inserted into a string using `{}`.

```python
name = "Movsum"
print(f"Hello, {name}")
```

Output:

```text
Hello, Movsum
```

Expressions can also be evaluated:

```python
print(f"{10 + 5}")
```

Output:

```text
15
```

Example inside a class:

```python
class Car:
    def __init__(self, brand):
        self.brand = brand

    def start_engine(self):
        print(f"{self.brand} engine started.")

car = Car("Hyundai")
car.start_engine()
```

Output:

```text
Hyundai engine started.
```

## What I Learned

- A class is a blueprint.
- An object is an instance created from a class.
- Built-in types such as `int`, `str`, and `list` are also classes.
- Magic methods are called automatically by Python.
- `__add__()` controls custom `+` behavior.
- `__mul__()` controls custom `*` behavior.
- `__init__()` initializes a new object.
- `self` refers to the current object.
- Parameters provide temporary incoming data.
- Attributes store data inside an object.
- Methods define object behavior.
- f-strings insert values and expressions into text.

## Practice

1. Create a `Car` class with `brand`, `model`, and `year` attributes.
2. Create two different `Car` objects.
3. Add an `info()` method that prints all attributes using an f-string.
4. Add a `start_engine()` method.
5. Create a class with `__add__()` and choose what the `+` operator should return.
