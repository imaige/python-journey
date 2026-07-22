# Python OOP Fundamentals

## Overview

This document summarizes the Object-Oriented Programming concepts I learned in Python.

OOP stands for:

```text
Object-Oriented Programming
```

The main idea is to represent real or logical entities using classes and objects.

---

## 1. Class

A class is a blueprint or template.

It describes:

- what data an object can have
- what actions an object can perform

Example:

```python
class Human:
    pass
```

`Human` is a class.

It represents the general concept of a human, but it is not a specific person yet.

---

## 2. Object

An object is a specific instance created from a class.

Example:

```python
movsum = Human()
ali = Human()
```

Here:

- `Human` is the class
- `movsum` is an object
- `ali` is another object

Both objects belong to the same class, but they are independent from each other.

---

## 3. Attribute

An attribute is information stored inside an object.

For a human, attributes can include:

- name
- age
- height
- weight
- nationality
- hair color

Example:

```python
movsum.name = "Movsum"
movsum.age = 27
```

Attributes answer the question:

> What does this object have?

---

## 4. Method

A method is a function defined inside a class.

It describes an action that an object can perform.

For a human, methods can include:

- walk
- speak
- jump

Example:

```python
class Human:

    def speak(self):
        print("Hello")
```

Methods answer the question:

> What can this object do?

---

## 5. `self`

`self` refers to the object that is currently using the method.

Example:

```python
class Human:

    def introduce(self):
        print(self.name)
```

```python
movsum = Human()
movsum.name = "Movsum"

ali = Human()
ali.name = "Ali"
```

When this runs:

```python
movsum.introduce()
```

`self` refers to `movsum`.

When this runs:

```python
ali.introduce()
```

`self` refers to `ali`.

The same method works with different objects because `self` identifies the object that called it.

A useful way to remember it:

```text
self.name = this object's name
self.age = this object's age
```

---

## 6. `__init__`

`__init__` is a special method that runs automatically when an object is created.

It is commonly used to assign initial attributes.

Example:

```python
class Human:

    def __init__(self, name, age):
        self.name = name
        self.age = age
```

Creating an object:

```python
movsum = Human("Movsum", 27)
```

This produces:

```text
movsum.name = "Movsum"
movsum.age = 27
```

Python effectively passes the newly created object as `self`.

Conceptually:

```python
Human.__init__(movsum, "Movsum", 27)
```

---

## 7. Independent Objects

Objects created from the same class have independent attributes.

Example:

```python
class Human:

    def __init__(self):
        self.name = "Unknown"


p1 = Human()
p2 = Human()

p1.name = "Movsum"

print(p1.name)
print(p2.name)
```

Output:

```text
Movsum
Unknown
```

Changing `p1` does not change `p2`, because they are different objects.

---

## 8. Changing an Attribute with a Method

A method can update the object that calls it.

Example:

```python
class Dog:

    def __init__(self, name):
        self.name = name

    def rename(self, new_name):
        self.name = new_name
```

```python
dog = Dog("Max")
dog.rename("Rocky")

print(dog.name)
```

Output:

```text
Rocky
```

Inside `rename`, `self` refers to `dog`.

---

## 9. Using Another Object as a Method Argument

A method can receive another object as an argument.

Example:

```python
class Cat:

    def __init__(self, name):
        self.name = name

    def copy_name(self, other):
        self.name = other.name
```

```python
cat1 = Cat("Leo")
cat2 = Cat("Milo")

cat1.copy_name(cat2)

print(cat1.name)
print(cat2.name)
```

Output:

```text
Milo
Milo
```

In this call:

```python
cat1.copy_name(cat2)
```

- `self` is `cat1`
- `other` is `cat2`

This line:

```python
self.name = other.name
```

means:

```python
cat1.name = cat2.name
```

`cat2` is not changed. Its name is only read and copied to `cat1`.

---

## 10. What Happens Without `__init__`

This class accepts no custom arguments:

```python
class Human:
    pass
```

This works:

```python
movsum = Human()
```

This does not work:

```python
movsum = Human("Movsum")
```

It produces a `TypeError` because the class has no custom initializer that accepts the provided value.

Also, this would fail:

```python
print(movsum.name)
```

unless the `name` attribute was assigned somewhere first.

---

## Complete Example

```python
class Human:

    def __init__(self, name, age):
        self.name = name
        self.age = age

    def introduce(self):
        print(f"My name is {self.name} and I am {self.age} years old.")

    def change_name(self, new_name):
        self.name = new_name


movsum = Human("Movsum", 27)
ali = Human("Ali", 25)

movsum.introduce()
ali.introduce()

movsum.change_name("Murad")

movsum.introduce()
ali.introduce()
```

This example demonstrates:

- class
- objects
- attributes
- methods
- `self`
- `__init__`
- independent object state
- changing attributes through methods

---

## What I Understand Now

I can explain:

- what a class is
- what an object is
- the difference between class and object
- what an attribute is
- what a method is
- what `self` refers to
- what `__init__` does
- why different objects have independent data
- how methods can change object attributes
- how one object can be passed to another object's method

## Next OOP Topics

- inheritance
- encapsulation
- polymorphism
- abstraction
- class attributes
- instance attributes
- class methods
- static methods
