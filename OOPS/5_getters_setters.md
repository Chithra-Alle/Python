# Getters and Setters
In Python, getters and setters are methods used to access and modify the attributes of a class. They provide a way to interact with private or protected attributes while keeping control over how the values are accessed or changed.

## Getters
- A getter method is used to retrieve the value of an attribute.
- It allows access to an attribute in a controlled manner.
- A getter method is typically prefixed with get_ (though it is not a strict rule) and is used to return the value of a private or protected attribute.

## Setter
- A setter method is used to set or modify the value of an attribute.
- It allows controlled modification of an attribute by adding logic to check or modify the value before it gets assigned.
- A setter method is typically prefixed with set_ (though this is also not a strict rule).

###  Why Use Getters and Setters?
1. Encapsulation: In object-oriented programming, it's a good practice to encapsulate attributes so they are not directly accessed or modified. Instead, getters and setters control how attributes are accessed and modified, adding a layer of safety or validation.
2. Data Validation: Setters can add logic to validate data before setting the value, such as ensuring a number is positive or that a string is of a certain length.
3. Read-Only Attributes: Getters allow reading of an attribute, but setters can be omitted to make the attribute read-only.

#### Example without Getters and Setters:
```python
class Person:
    def __init__(self, name, age):
        self.name = name  # Public attribute
        self.age = age    # Public attribute

p = Person("John", 25)
print(p.name)  # Direct access
p.age = -10    # Directly changing value, no control
```
#### Example with Getters and Setters:
```python
class Person:
    def __init__(self, name, age):
        self._name = name  # Private attribute (by convention)
        self._age = age    # Private attribute (by convention)

    # Getter for name
    def get_name(self):
        return self._name

    # Setter for name
    def set_name(self, name):
        self._name = name

    # Getter for age
    def get_age(self):
        return self._age

    # Setter for age
    def set_age(self, age):
        if age > 0:  # Validation check
            self._age = age
        else:
            print("Age must be positive!")

# Usage
p = Person("John", 25)
print(p.get_name())  # Access using getter
p.set_age(30)        # Modify using setter
p.set_age(-10)       # Invalid age, setter will prevent it
```
   
