# *Magic Dunder*
- Magic methods, also known as dunder (double underscore) methods, are special methods in Python that start and end with double underscores (__).
- These methods automatically get called when performing certain operations on objects.

## Common Magic Methods and Their Uses
1. Object Initialization (__init__)
Used for initializing an object when an instance is created.
```
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

p = Person("Alice", 25)  # __init__ is called automatically
print(p.name, p.age)  # Output: Alice 25
```

2. String Representation (__str__ and __repr__)
- __str__: Returns a human-readable string of the object.
- __repr__: Returns an unambiguous string (useful for debugging).
```
class Person:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return f"Person: {self.name}"  # For users

    def __repr__(self):
        return f"Person('{self.name}')"  # For debugging

p = Person("Bob")
print(str(p))   # Output: Person: Bob
print(repr(p))  # Output: Person('Bob')
```
3. Arithmetic Operations (__add__, __sub__, etc.)
Used to define behavior for arithmetic operators.
```
class Number:
    def __init__(self, value):
        self.value = value

    def __add__(self, other):
        return Number(self.value + other.value)

n1 = Number(10)
n2 = Number(5)
n3 = n1 + n2  # Calls __add__
print(n3.value)  # Output: 15
```
4. Comparison Methods (__eq__, __lt__, __gt__, etc.)
Define comparison behavior (==, <, >).
```
class Student:
    def __init__(self, marks):
        self.marks = marks

    def __eq__(self, other):
        return self.marks == other.marks  # Checks equality

s1 = Student(85)
s2 = Student(85)
print(s1 == s2)  # Output: True
```
5. Length and Indexing (__len__, __getitem__)
- __len__: Returns the length of an object.
- __getitem__: Allows indexing like a list.
```
class Container:
    def __init__(self, items):
        self.items = items

    def __len__(self):
        return len(self.items)

    def __getitem__(self, index):
        return self.items[index]

c = Container([10, 20, 30])
print(len(c))   # Output: 3
print(c[1])     # Output: 20
```
6. Object Representation (__call__)
Makes an object callable like a function.
```
class Multiply:
    def __init__(self, factor):
        self.factor = factor

    def __call__(self, num):
        return num * self.factor

double = Multiply(2)
print(double(5))  # Output: 10
```
