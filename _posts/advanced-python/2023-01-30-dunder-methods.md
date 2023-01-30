---
layout: post
title:  "Going Beyond the Basics: Mastering Dunder Methods in Python for Custom Object Operations"
date:   2023-01-30 19:25:37 +0000
categories: python dunder methods
---

# Dunder methods

Dunder methods, short for "double underscore methods," are special methods in Python that allow developers to define custom behavior for built-in operations. These methods are also known as "magic methods" and are denoted by their double underscore prefix and suffix (e.g. `__add__`).

One of the most common uses for dunder methods is to define custom behavior for mathematical operations such as addition, subtraction, and multiplication. For example, we can define a custom class `MyNumber` that behaves like a number:

```python
class MyNumber:
    def __init__(self, value):
        self.value = value

    def __add__(self, other):
        return MyNumber(self.value + other.value)

    def __sub__(self, other):
        return MyNumber(self.value - other.value)

    def __mul__(self, other):
        return MyNumber(self.value * other.value)

    def __truediv__(self, other):
        return MyNumber(self.value / other.value)

    def __repr__(self):
        return str(self.value)

a = MyNumber(5)
b = MyNumber(10)
c = a + b  # c = MyNumber(15)
print(c)
```

Another use case for dunder methods is to define custom behavior for comparison operators such as `==`, `>`, and `<`. For example, we can define a custom class `MyString` that behaves like a string:

```python
class MyString:
    def __init__(self, value):
        self.value = value

    def __eq__(self, other):
        return self.value.lower() == other.value.lower()

    def __ne__(self, other):
        return self.value.lower() != other.value.lower()

    def __lt__(self, other):
        return self.value.lower() < other.value.lower()

    def __le__(self, other):
        return self.value.lower() <= other.value.lower()

    def __gt__(self, other):
        return self.value.lower() > other.value.lower()

    def __ge__(self, other):
        return self.value.lower() >= other.value.lower()

    def __repr__(self):
        return self.value

a = MyString("Hello")
b = MyString("WORLD")
print(a == b)  # True
```

Another use case for dunder methods is to define custom behavior for built-in functions such as `len()`, `str()`, and `iter()`. For example, we can define a custom class `MyList` that behaves like a list:

```python
class MyList:
    def __init__(self, value):
        self.value = value

    def __len__(self):
        return len(self.value)

    def __str__(self):
        return str(self.value)

    def __iter__(self):
        return iter(self.value)

    def __getitem__(self, index):
        return self.value[index]

a = MyList([1, 2, 3])
print(len(a))  # 3
```

It is recommended to use dunder methods when you want to define custom behavior for certain operations on objects, such as defining how two objects of a certain class should be added together. For example, if you have a class for representing a 2D point, you might want to define the behavior of addition for two point objects to return a new point object that represents the sum of their x and y coordinates.

There are also a number of dunder methods that are commonly used in Python, such as **init** (initialization), **str** (string representation), **len** (length), and **getitem** (indexing).

Some caveats to look out for when using dunder methods include:

* Overriding dunder methods can lead to unexpected behavior if not done carefully. For example, if you override the **add** method to add two objects in a certain way, but then use the built-in sum function on a list of those objects, the built-in function will not use your custom implementation.
* Not all dunder methods need to be implemented for a class. For example, if you don't need to define a custom behavior for the "less than" operator, you don't have to implement the **lt** method.
* Some dunder methods are called by the Python interpreter automatically (e.g. **init**, **del**) and some are not (e.g. **add**, **str**), you should be aware of the difference and how to use them.
* Some dunder methods have specific signature and return type, so you should be aware of that and make sure to implement them correctly.

Overall, dunder methods are a powerful feature of Python that allows you to define custom behavior for certain operations on objects, but it's important to use them with care and be aware of their caveats.
