# Python Booleans

## What is a Boolean?

A Boolean represents one of two logical values:

```python
True
False
```

The Boolean type is called `bool`.

```python
print(type(True))   # <class 'bool'>
print(type(False))  # <class 'bool'>
```

## Truthy and Falsy Values

Python can convert other values to `True` or `False` with `bool()`.

Falsy values include:

```python
bool(0)              # False
bool(0.0)            # False
bool(complex(0, 0))  # False
bool("")             # False
bool([])             # False
bool({})              # False
bool(None)            # False
```

Most other values are truthy:

```python
bool(1)         # True
bool(-5)        # True
bool("Movsum")  # True
bool(" ")       # True
bool([1])       # True
```

## Empty String vs Space

These are different:

```python
bool("")   # False
bool(" ")  # True
```

`""` is empty, but `" "` contains one space character.

## Important Idea

`bool()` does not only check numbers. It checks whether a value is considered empty, zero, or absent.

## What I Learned

- `True` and `False`
- The `bool` type
- Truthy and falsy values
- Why zero values are falsy
- Why an empty string is falsy
- Why a string containing a space is truthy
- `bool()` with integers, floats, complex numbers, strings, lists, dictionaries, and `None`

## Practice

Predict the result:

```python
print(bool(0))
print(bool(10))
print(bool(""))
print(bool(" "))
print(bool([]))
print(bool([0]))
print(bool(complex(0, 0)))
```
