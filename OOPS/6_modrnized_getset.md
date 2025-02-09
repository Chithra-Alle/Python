# Python Property Decorators:
Python provides a more elegant and Pythonic way to define getters and setters using the @property decorator. This allows you to use getter and setter functionality without calling methods explicitly.

#### Example with @property and @<property_name>.setter:
```python
class Person:
    def __init__(self, name, age):
        self._name = name  # Private attribute
        self._age = age    # Private attribute

    # Getter for name using property
    @property
    def name(self):
        return self._name

    # Setter for name using property
    @name.setter
    def name(self, name):
        self._name = name

    # Getter for age using property
    @property
    def age(self):
        return self._age

    # Setter for age using property
    @age.setter
    def age(self, age):
        if age > 0:  # Validation
            self._age = age
        else:
            print("Age must be positive!")

# Usage
p = Person("John", 25)
print(p.name)  # Access using getter (no method call syntax)
p.name = "Alice"  # Modify using setter (no method call syntax)
p.age = -10       # Invalid age, setter will prevent it
```
