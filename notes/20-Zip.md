# Python `zip()`

## What is `zip()`?

`zip()` is a built-in Python function that groups elements from two or more iterables by their corresponding positions.

```python
names = ["Movsum", "Ali", "Murad"]
ages = [27, 25, 30]

result = zip(names, ages)
```

Conceptually:

```text
Movsum  <-> 27
Ali     <-> 25
Murad   <-> 30
```

When converted to a list:

```python
print(list(result))
# [('Movsum', 27), ('Ali', 25), ('Murad', 30)]
```

The outer object is a list after conversion, and each grouped item is a tuple.

## More Than Two Iterables

`zip()` can group more than two iterables.

```python
names = ["Movsum", "Ali"]
ages = [27, 25]
jobs = ["SOC Analyst", "Developer"]

print(list(zip(names, ages, jobs)))
# [('Movsum', 27, 'SOC Analyst'), ('Ali', 25, 'Developer')]
```

## Different Lengths

With normal `zip()`, processing stops when the shortest iterable is exhausted.

```python
names = ["Movsum", "Ali", "Murad"]
ages = [27, 25]

print(list(zip(names, ages)))
# [('Movsum', 27), ('Ali', 25)]
```

`"Murad"` has no corresponding element in `ages`, so it is not included.

## Return Type

`zip()` does not directly return a list or tuple. It returns a `zip` object.

```python
names = ["Movsum", "Ali"]
ages = [27, 25]

result = zip(names, ages)
print(type(result))
# <class 'zip'>
```

## `zip` is an Iterator

A `zip` object behaves as an iterator. Its values are produced as they are requested, and the iterator moves forward as it is consumed.

```python
names = ["Movsum", "Ali"]
ages = [27, 25]

result = zip(names, ages)

print(list(result))
# [('Movsum', 27), ('Ali', 25)]

print(list(result))
# []
```

The second result is empty because the same `zip` iterator has already been consumed to the end.

The original `names` and `ages` lists are not deleted or modified. Only the iterator has been exhausted.

If the result needs to be reused, convert it to a list once and store that list:

```python
result = list(zip(names, ages))

print(result)
print(result)
```

Both prints contain the same data because `result` is now a list rather than the original `zip` iterator.

## Mental Model

Think of `zip()` like a zipper:

```text
A1   A2   A3
|    |    |
B1   B2   B3

      zip
       ↓

(A1, B1)
(A2, B2)
(A3, B3)
```

## Summary

```text
zip()
├── built-in function
├── accepts two or more iterables
├── groups corresponding elements
├── grouped elements are tuples
├── stops at the shortest iterable
├── returns a zip object
└── zip object is an iterator and can be exhausted
```
