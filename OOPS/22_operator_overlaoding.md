# Operator Overloading in Python
- Operator overloading allows us to define custom behavior for built-in operators (+, -, *, /, ==, etc.) when used with user-defined objects. Python achieves this using magic/dunder methods (like __add__, __sub__, etc.).

## Why Use Operator Overloading?
- 🔹 By default, Python operators work with built-in types, but not with objects.
- 🔹 With operator overloading, we can define how operators should behave for custom classes.

### Example 1: Overloading the + Operator
- Let's define a class to represent a point (x, y) and overload the + operator.
```
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):  # Overloading +
        return Point(self.x + other.x, self.y + other.y)

    def __str__(self):  # To print objects properly
        return f"({self.x}, {self.y})"

p1 = Point(2, 3)
p2 = Point(4, 5)

p3 = p1 + p2  # Calls p1.__add__(p2)
print(p3)  # Output: (6, 8)
```
- 🔹 Explanation:
- The __add__ method defines how + works for Point objects.
- p1 + p2 adds the x and y coordinates and returns a new Point object.
### Example 2: Overloading * Operator
```
class Product:
    def __init__(self, price):
        self.price = price

    def __mul__(self, quantity):  # Overloading *
        return self.price * quantity

item = Product(100)
total = item * 5  # Calls item.__mul__(5)
print(total)  # Output: 500
```
- 🔹 Explanation:
- __mul__ allows Product * quantity to return the total cost.
### Example 3: Overloading == Operator
```
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __eq__(self, other):  # Overloading ==
        return self.age == other.age

p1 = Person("Alice", 25)
p2 = Person("Bob", 25)
p3 = Person("Charlie", 30)

print(p1 == p2)  # True (same age)
print(p1 == p3)  # False
```
- 🔹 Explanation:
- __eq__ makes == compare ages instead of default object identity.
## *Common Operator Overloading Methods*
|Operator|	Method|
|:------:|:-----:|
|+|	__add__(self, other)|
|-|	__sub__(self, other)|
|*|	__mul__(self, other)|
|/|	__truediv__(self, other)|
|//|	__floordiv__(self, other)|
|%|	__mod__(self, other)|
|**|	__pow__(self, other)|
|==|	__eq__(self, other)|
|!=|	__ne__(self, other)|
|<|	__lt__(self, other)|
|<=|	__le__(self, other)|
|>|	__gt__(self, other)|
|>=|	__ge__(self, other)|
### Key Takeaways
- ✔ Operator overloading customizes the behavior of operators for objects.
- ✔ Use dunder/magic methods like __add__, __mul__, __eq__, etc.
- ✔ Helps make objects behave like built-in types, improving readability.
