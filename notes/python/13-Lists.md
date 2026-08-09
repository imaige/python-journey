# Python Lists

## What is a list?

A `list` is an ordered and mutable Python data type used to store multiple elements in a single object.

A list can contain values of the same or different types.

```python
items = [10, "Movsum", True, 3.5]
```

`list` is also a Python class. When a list is created, a list object is created.

```python
numbers = [10, 20, 30, 40]

print(type(numbers))
# <class 'list'>
```

## Creating lists

A list can be created with square brackets:

```python
numbers = [10, 20, 30]
```

It can also be created with the `list()` class:

```python
numbers = list()

print(numbers)
# []
```

## Ordered elements and indexes

Every list element has an index.

Python indexing starts from `0`.

```python
numbers = [10, 20, 30, 40]
```

```text
Value:  10  20  30  40
Index:   0   1   2   3
```

Accessing an element:

```python
print(numbers[2])
# 30
```

## Negative indexing

Python can also count elements from the end of the list.

```text
Value:   10  20  30  40
Index:   -4  -3  -2  -1
```

```python
print(numbers[-1])
# 40
```

`-1` always refers to the last element.

## Updating list elements

Lists are mutable, which means their elements can be changed after creation.

```python
numbers = [10, 20, 30]

numbers[1] = 50

print(numbers)
# [10, 50, 30]
```

## Mutable objects

A mutable object can be modified without creating a completely new object.

A list is mutable:

```python
numbers = [10, 20, 30]
numbers[0] = 99

print(numbers)
# [99, 20, 30]
```

## References

When one variable is assigned to another list variable, Python does not automatically create a second independent list.

```python
numbers = [10, 20, 30]
a = numbers
```

Both variables reference the same list object.

```python
a[0] = 99

print(numbers)
# [99, 20, 30]
```

The important idea is:

```text
a = numbers
```

copies the reference to the list object, not the list itself.

Conceptually:

```text
numbers ──┐
          ├──> [10, 20, 30]
a ────────┘
```

After changing `a[0]`:

```text
numbers ──┐
          ├──> [99, 20, 30]
a ────────┘
```

## What I learned

- A list stores multiple elements in one object
- A list may contain different data types
- `list` is a Python class
- List indexes start from `0`
- Negative indexes count from the end
- List elements can be updated
- Lists are mutable
- `a = numbers` does not create an independent copy
- Two variables can reference the same list object

## Practice

### Exercise 1

Create this list:

```python
numbers = [10, 20, 30, 40, 50]
```

Print:

- the first element
- the third element
- the last element using a negative index

### Exercise 2

Change `20` to `200`:

```python
numbers = [10, 20, 30]
```

Expected result:

```python
[10, 200, 30]
```

### Exercise 3

Predict the output before running the code:

```python
numbers = [1, 2, 3]
other = numbers
other[1] = 99

print(numbers)
print(other)
```
