# Python Dictionaries

## What is a Dictionary?

A dictionary (`dict`) is a Python data type that stores information as `key: value` pairs.

```python
car = {
    "brand": "Hyundai",
    "model": "Grandeur",
    "year": 2017
}
```

Here:

- `"brand"` is a key and `"Hyundai"` is its value.
- `"model"` is a key and `"Grandeur"` is its value.
- `"year"` is a key and `2017` is its value.

Unlike a list, where values are normally accessed by numeric index, dictionary values are accessed by their keys.

```python
print(car["model"])
# Grandeur
```

Modern Python dictionaries preserve insertion order, but keys are still the main way to access dictionary values.

## Accessing Values

A value can be accessed with square brackets:

```python
print(car["brand"])
```

It can also be accessed with the `get()` method:

```python
print(car.get("brand"))
```

Both return:

```text
Hyundai
```

### Missing Keys: `[]` vs `get()`

If a key does not exist, square-bracket access raises `KeyError`:

```python
print(car["color"])
# KeyError
```

`get()` is safer when a key may not exist:

```python
print(car.get("color"))
# None
```

A custom default value can also be provided:

```python
print(car.get("color", "No information"))
# No information
```

## Updating Values

Dictionaries are mutable, so their contents can be changed after creation.

```python
car["year"] = 2020
```

Now:

```python
{
    "brand": "Hyundai",
    "model": "Grandeur",
    "year": 2020
}
```

The type of the value also matters. For example:

```python
car["year"] = "2020"
```

works, but now the value is a string instead of an integer.

## Adding New Key-Value Pairs

Assigning to a key that does not yet exist adds a new pair:

```python
car["color"] = "Blue"
```

## Removing Data

### `del`

`del` removes a key-value pair:

```python
del car["year"]
```

### `pop()`

`pop()` removes the pair and returns the removed value:

```python
removed = car.pop("model")
print(removed)
# Grandeur
```

A useful mental model is:

```text
del   -> remove
pop() -> remove + return the value
```

## `len()` with Dictionaries

`len()` returns the number of key-value pairs in a dictionary.

```python
car = {
    "brand": "Hyundai",
    "model": "Grandeur",
    "year": 2017
}

print(len(car))
# 3
```

Since each dictionary entry has one key, this is also the number of keys.

## Using Variables as Values

Variables can be used as dictionary values:

```python
brand = "Hyundai"
model = "Grandeur"
year = 2017

car = {
    "brand": brand,
    "model": model,
    "year": year
}
```

In:

```python
"brand": brand
```

- the left `"brand"` is a string used as the dictionary key;
- the right `brand` is a variable whose value is `"Hyundai"`.

## References

Like lists, dictionaries are mutable objects.

```python
car = {
    "brand": "Hyundai",
    "year": 2017
}

car2 = car
car2["year"] = 2020

print(car)
```

Result:

```python
{'brand': 'Hyundai', 'year': 2020}
```

`car2 = car` does not create a second dictionary. Both variables reference the same dictionary object.

Conceptually:

```text
car  ----\
          -> same dictionary object
car2 ----/
```

Therefore, changing the object through `car2` is visible through `car` as well.

## Copying a Dictionary

Use `copy()` when a separate dictionary object is needed:

```python
person = {
    "name": "Movsum",
    "age": 27
}

person2 = person.copy()
person2["age"] = 30
person2["job"] = "AI Engineer"
```

Now:

```python
print(person)
# {'name': 'Movsum', 'age': 27}

print(person2)
# {'name': 'Movsum', 'age': 30, 'job': 'AI Engineer'}
```

For this simple dictionary, `person` and `person2` are separate dictionary objects, so their `id()` values are different.

## Creating a Dictionary with `dict()`

`dict()` can build a dictionary from two-element pairs.

```python
data = [
    ["name", "Movsum"],
    ["age", 27],
    ["job", "SOC Analyst"]
]

person = dict(data)
```

Result:

```python
{
    "name": "Movsum",
    "age": 27,
    "job": "SOC Analyst"
}
```

For each pair, Python interprets:

```text
first element  -> key
second element -> value
```

For example:

```python
["name", "Movsum"]
```

becomes:

```python
"name": "Movsum"
```

## Trailing Commas

A comma separates dictionary entries:

```python
person = {
    "name": "Movsum",
    "age": 27,
    "job": "SOC Analyst"
}
```

The comma after the final entry is optional:

```python
person = {
    "name": "Movsum",
    "age": 27,
}
```

This is also valid Python. A trailing comma does not add another value.

## Key Takeaways

- `dict` stores data as `key: value` pairs.
- Values are normally accessed using keys instead of numeric list indexes.
- `dictionary[key]` raises `KeyError` if the key is missing.
- `dictionary.get(key)` returns `None` by default when the key is missing.
- Dictionaries are mutable.
- `del` removes a pair.
- `pop()` removes a pair and returns its value.
- `len(dictionary)` gives the number of key-value pairs.
- `a = dictionary` creates another reference to the same object.
- `dictionary.copy()` creates a separate dictionary object for the simple cases covered so far.
- `dict()` can create a dictionary from two-element pairs.
