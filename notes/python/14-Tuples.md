# Python Tuples

## What is a Tuple?

A tuple is an ordered Python data type that is similar to a list, but it is immutable.

```python
car = ("Hyundai", "Grandeur", 2017)
```

Like a list, tuple elements can be accessed by index.

```python
print(car[1])
# Grandeur

print(car[-1])
# 2017
```

## Tuple vs List

A list is mutable:

```python
numbers = [10, 20, 30]
numbers[1] = 50

print(numbers)
# [10, 50, 30]
```

A tuple is immutable:

```python
numbers = (10, 20, 30)
numbers[1] = 50
# TypeError
```

After a tuple is created, its elements cannot be replaced using index assignment.

## References

Assignment does not create a new tuple object:

```python
a = (10, 20, 30)
b = a

print(id(a) == id(b))
# True
```

`a` and `b` reference the same tuple object.

## Single-Element Tuples

Parentheses alone do not make an object a tuple.

```python
a = (10)
print(type(a))
# <class 'int'>
```

To create a tuple containing one element, a comma is required:

```python
b = (10,)
print(type(b))
# <class 'tuple'>
```

The same rule applies to strings:

```python
x = ("Movsum")
print(type(x))
# <class 'str'>

y = ("Movsum",)
print(type(y))
# <class 'tuple'>
```

A tuple can even be written without parentheses when the comma makes the tuple structure clear:

```python
c = 100,
print(type(c))
# <class 'tuple'>
```

A useful rule is:

```text
(10)        -> int
(10,)       -> tuple
("Python")  -> str
("Python",) -> tuple
```

The comma is the important part when creating a single-element tuple.

## Mutable Objects Inside a Tuple

A tuple itself is immutable, but it can contain mutable objects such as lists.

```python
data = ([10, 20], "Python")
```

The tuple element cannot be replaced:

```python
data[0] = [50, 60]
# TypeError
```

However, the list object stored inside the tuple can still be modified:

```python
data[0].append(30)

print(data)
# ([10, 20, 30], 'Python')
```

This works because the tuple still references the same list object. The tuple element itself was not replaced. Only the contents of the mutable list were changed.

Conceptually:

```text
tuple element replacement       -> not allowed
change inside a mutable object  -> allowed
```

## Key Takeaways

- Tuple is an ordered data type.
- Tuple elements can be accessed with positive and negative indexes.
- Tuples are immutable.
- `a = tuple_object` creates another reference to the same tuple object.
- A one-element tuple requires a comma, for example `(10,)`.
- Parentheses alone do not create a tuple.
- A tuple may contain mutable objects.
- A mutable object inside a tuple can change even though the tuple itself is immutable.
