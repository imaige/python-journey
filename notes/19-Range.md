# Python Range

## What is `range`?

`range` is a built-in Python class used to represent a sequence of integers without writing every number manually.

```python
numbers = range(5)
```

Conceptually, this represents:

```text
0, 1, 2, 3, 4
```

## Main Characteristics

- `range` is a class
- `range` objects are ordered
- indexing is supported
- `range` is immutable
- the `stop` value is not included

## `range(stop)`

When only one argument is provided, Python uses `0` as the start and `1` as the step.

```python
numbers = range(5)
print(list(numbers))
# [0, 1, 2, 3, 4]
```

Mental model:

```text
range(5)
start = 0
stop  = 5
step  = 1
```

## `range(start, stop)`

```python
numbers = range(2, 7)
print(list(numbers))
# [2, 3, 4, 5, 6]
```

`2` is included, but `7` is not.

## `range(start, stop, step)`

The third argument controls the step size.

```python
numbers = range(1, 10, 2)
print(list(numbers))
# [1, 3, 5, 7, 9]
```

General form:

```python
range(start, stop, step)
```

## Negative Step

A negative step can be used to move backwards.

```python
numbers = range(10, 0, -2)
print(list(numbers))
# [10, 8, 6, 4, 2]
```

The stop value `0` is still not included.

## Indexing

Although `range` is immutable, it is an ordered sequence and supports indexing.

```python
numbers = range(10, 20)

print(numbers[0])
# 10

print(numbers[2])
# 12
```

Immutable does not mean that indexing is unavailable. It means the existing range object cannot be modified in place.

## Immutability

This does not work:

```python
numbers = range(5)
numbers[0] = 100
```

Python raises an error because a `range` object is immutable.

## Summary

```text
range
├── built-in class
├── represents an integer sequence
├── ordered
├── supports indexing
├── immutable
├── stop is excluded
└── supports positive and negative steps
```

Core syntax:

```python
range(start, stop, step)
```
