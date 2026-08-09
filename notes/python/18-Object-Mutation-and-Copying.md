# Python Object Mutation and Copying

## Overview

This document summarizes how object references, mutation, shallow copies, and deep copies behave in Python.

The key idea is that assigning one variable to another usually copies a reference to the same object. Copying an object requires creating a new object, and the behavior differs between shallow and deep copies.

## Assignment Does Not Copy the Object

```python
a = [1, 2, 3]
b = a

b.append(4)

print(a)
print(b)
```

Output:

```text
[1, 2, 3, 4]
[1, 2, 3, 4]
```

`b = a` does not create a new list. Both variables refer to the same list object.

Conceptually:

```text
a ──► [1, 2, 3]
       ▲
b ─────┘
```

Changing the object through either variable is visible through the other variable because there is only one list object.

## Mutable Objects

A mutable object can be changed after it is created.

Examples include:

```text
list
dict
set
```

When two variables refer to the same mutable object, a mutation through one variable affects the shared object.

Example:

```python
a = [10, 20]
b = a

b[0] = 99

print(a)
# [99, 20]
```

## Creating a Shallow Copy

For a list, `.copy()` creates a new outer list.

```python
a = [1, 2, 3]
b = a.copy()

b.append(4)

print(a)
print(b)
```

Output:

```text
[1, 2, 3]
[1, 2, 3, 4]
```

Now `a` and `b` are different outer list objects.

```text
a ──► [1, 2, 3]

b ──► [1, 2, 3, 4]
```

The same shallow-copy idea can also be expressed with the `copy` module:

```python
import copy

b = copy.copy(a)
```

## Shallow Copy with Nested Mutable Objects

A shallow copy creates a new outer container, but the references stored inside it are copied as references.

```python
a = [[1, 2], [3, 4]]
b = a.copy()
```

Conceptually:

```text
a ──► outer list A
       ├──► inner list X: [1, 2]
       └──► inner list Y: [3, 4]

b ──► outer list B
       ├──► inner list X: [1, 2]
       └──► inner list Y: [3, 4]
```

The outer lists are different:

```python
print(a is b)
# False
```

But the first nested list is the same object:

```python
print(a[0] is b[0])
# True
```

Therefore:

```python
b[0].append(99)

print(a)
print(b)
```

Output:

```text
[[1, 2, 99], [3, 4]]
[[1, 2, 99], [3, 4]]
```

The nested list is shared, so mutating it is visible through both outer lists.

## Why Immutable Values Are Usually Not a Problem

A shallow copy also copies references to immutable objects such as integers and strings.

Example:

```python
a = [1, 2, 3]
b = a.copy()
```

The integer objects may be referenced by both lists, but integers cannot be mutated in place. Replacing an element in `b` changes only the element reference stored in `b`.

```python
b[0] = 99

print(a)
# [1, 2, 3]

print(b)
# [99, 2, 3]
```

## Deep Copy

A deep copy recursively creates independent copies of nested objects.

```python
import copy

a = [[1, 2], [3, 4]]
b = copy.deepcopy(a)
```

Conceptually:

```text
a ──► outer list A
       ├──► inner list X
       └──► inner list Y

b ──► outer list B
       ├──► inner list X2
       └──► inner list Y2
```

The nested mutable objects are now independent.

```python
b[0].append(99)

print(a)
print(b)
```

Output:

```text
[[1, 2], [3, 4]]
[[1, 2, 99], [3, 4]]
```

## Shallow Copy vs Deep Copy

```text
assignment
b = a
→ no new container is created
→ both variables refer to the same object

shallow copy
b = a.copy()
→ new outer container is created
→ nested objects are still referenced from both containers

deep copy
b = copy.deepcopy(a)
→ new outer container is created
→ nested objects are recursively copied as well
```

## Practical Mental Model

Think of a nested list as a box containing smaller boxes.

```text
Assignment
→ another label is attached to the same box

Shallow copy
→ a new outer box is created
→ the same smaller boxes are placed by reference inside it

Deep copy
→ a new outer box is created
→ the smaller boxes are copied too
```

## Important Checks with `is`

The `is` operator can help confirm whether two variables refer to the exact same object.

```python
a = [[1, 2]]
b = a.copy()

print(a is b)
# False

print(a[0] is b[0])
# True
```

With a deep copy:

```python
import copy

b = copy.deepcopy(a)

print(a is b)
# False

print(a[0] is b[0])
# False
```

## Summary

```text
mutable object
→ can be changed after creation

reference assignment
→ variables can point to the same object

shallow copy
→ copies the outer container
→ keeps references to nested objects

deep copy
→ recursively copies nested objects

list.copy()
→ shallow copy

copy.copy()
→ shallow copy

copy.deepcopy()
→ deep copy
```
