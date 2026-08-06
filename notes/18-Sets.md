# Python Sets

## What is a Set?

A `set` is a mutable Python collection used to store unique elements.

```python
numbers = {10, 20, 30}
```

The important characteristics covered so far are:

- elements are unique
- duplicate values are not stored separately
- sets are not indexed like lists
- element order should not be relied on
- sets are mutable

## Collection Comparison

A quick comparison of the Python collection/data types covered so far:

| Type | Mutable | Ordered | Duplicate elements |
|---|---|---|---|
| `list` | Yes | Yes | Yes |
| `tuple` | No | Yes | Yes |
| `set` | Yes | No | No |
| `range` | No | Yes | No |
| `dict` | Yes | Yes* | Keys: No, Values: Yes |
| `str` | No | Yes | Yes |

`*` In modern Python, dictionaries preserve insertion order. Dictionary keys must be unique, while values may repeat.

A simple mental model:

```text
list   -> mutable, ordered, duplicates allowed
tuple  -> immutable, ordered, duplicates allowed
set    -> mutable, unordered for our learning model, unique elements
range  -> immutable sequence, ordered
 dict  -> mutable, insertion-ordered mapping, unique keys
str    -> immutable, ordered sequence of characters, duplicates allowed
```

## Set vs List

A list has meaningful element positions and supports indexing:

```python
numbers = [10, 20, 30]
print(numbers[0])
# 10
```

A set does not provide list-style indexing:

```python
numbers = {10, 20, 30}
print(numbers[0])
# TypeError
```

With a set, the important question is whether an element exists, not what numeric index it has.

## Unique Elements

Sets keep only unique elements.

```python
numbers = {10, 20, 20, 30, 30, 30}

print(numbers)
# {10, 20, 30}  # display order may vary

print(len(numbers))
# 3
```

Repeated values do not become separate set elements.

## Set Display Order

A set should not be treated as a sorted collection.

For example, Python may display a set of numbers in an order that is different from the order used when writing or combining them. The program should not rely on that display order.

If sorted output is needed:

```python
numbers = {100, 10, 50, 20, 250}
print(sorted(numbers))
# [10, 20, 50, 100, 250]
```

`sorted()` returns a list.

## Adding Elements with `add()`

`add()` adds one element to a set.

```python
numbers = {10, 20, 30}
numbers.add(40)

print(numbers)
# {10, 20, 30, 40}  # display order may vary
```

Adding a value that already exists does not create a duplicate:

```python
numbers.add(20)
```

The set still contains only one `20` element.

## Adding Multiple Elements with `update()`

`update()` takes elements from an iterable and adds them to the set.

```python
numbers = {10, 20, 30}
numbers.update([40, 50, 60])
```

The set now contains:

```text
10, 20, 30, 40, 50, 60
```

A useful mental model:

```text
add()    -> add one object
update() -> add elements from an iterable
```

## Removing Elements with `remove()`

```python
numbers = {10, 20, 30}
numbers.remove(20)
```

The set now contains `10` and `30`.

If the requested element does not exist:

```python
numbers.remove(100)
```

Python raises `KeyError`.

## Removing Elements with `discard()`

`discard()` also removes an element if it exists:

```python
numbers.discard(20)
```

The important difference from `remove()` is what happens when the value is missing:

```python
numbers.discard(100)
```

No exception is raised.

```text
remove(x)  -> remove x, but raise KeyError if x is missing
discard(x) -> remove x if present, otherwise do nothing
```

## `pop()`

`set.pop()` removes one arbitrary element and returns it.

```python
numbers = {10, 20, 30}
x = numbers.pop()
```

After this operation:

- `x` contains the element that was removed
- that element is no longer in `numbers`

Because a set does not have a reliable positional order, code should not assume which particular element `pop()` will remove.

`pop()` does not convert the returned value to `int` or another type. It returns the removed element itself.

## `union()`

`union()` combines the unique elements of sets.

```python
a = {10, 20, 30, 40}
b = {30, 40, 50, 60}

print(a.union(b))
```

The result contains:

```text
10, 20, 30, 40, 50, 60
```

A useful mental model:

```text
union -> all unique elements from both sides
```

## `intersection()`

`intersection()` returns elements that exist in both sets.

```python
a = {10, 20, 30, 40}
b = {30, 40, 50, 60}

print(a.intersection(b))
# {30, 40}
```

```text
intersection -> common elements
```

## `difference()`

`difference()` is directional.

```python
a = {10, 20, 30, 40}
b = {30, 40, 50, 60}

print(a.difference(b))
# {10, 20}

print(b.difference(a))
# {50, 60}
```

So in general:

```text
A difference B != B difference A
```

## `symmetric_difference()`

`symmetric_difference()` keeps elements that are present on only one side and removes the common elements.

```python
a = {10, 20, 30, 40}
b = {30, 40, 50, 60}

print(a.symmetric_difference(b))
# {10, 20, 50, 60}
```

A useful mental model:

```text
difference            -> difference from one selected side
symmetric_difference  -> non-common elements from both sides
```

For two sets, the `^` operator also represents symmetric difference:

```python
print(a ^ b)
```

## Reading a Method Signature

An editor may show a signature similar to:

```text
(method) symmetric_difference:
(__s: Iterable[str], /) -> set[str]
```

The parts covered so far mean:

- `(method)` -> this is a method
- `symmetric_difference` -> method name
- `__s` -> parameter name shown by the type information
- `:` -> introduces the type hint
- `Iterable[str]` -> an iterable whose elements are strings
- `/` -> parameters before it are positional-only
- `->` -> indicates the return type
- `set[str]` -> returns a set containing strings

Example of positional-only syntax:

```python
def hello(name, /):
    print(name)
```

This works:

```python
hello("Movsum")
```

But passing `name` as a keyword is not allowed for that positional-only parameter.

## Summary

```text
SET
├── unique elements
├── no list-style indexing
├── do not rely on element order
├── mutable
│
├── add()                  -> add one element
├── update()               -> add elements from an iterable
├── remove()               -> remove, KeyError if missing
├── discard()              -> remove if present, no error if missing
├── pop()                  -> remove and return an arbitrary element
│
├── union()                -> all unique elements
├── intersection()         -> common elements
├── difference()           -> elements unique to the selected side
└── symmetric_difference() -> non-common elements from both sides
```
