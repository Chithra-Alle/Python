# Protected
- In Python, protected members are indicated by a single underscore (_) before the attribute or method name. This is just a naming convention, meaning that it is not strictly enforced but is intended to signal that the member should only be used within the class and its subclasses.
- Unlike private members (__), which are truly hidden using name mangling, protected members are accessible from outside the class, but they should be treated as internal details.

##  1. Convention for Protected Members
- Protected members start with a single underscore (_).
- They can be accessed outside the class, but it is discouraged.
- They are intended for use within the class and its subclasses.

```
class Person:
    def __init__(self, name, age):
        self._name = name  # Protected attribute
        self._age = age    # Protected attribute

    def _display_info(self):  # Protected method
        return f"Name: {self._name}, Age: {self._age}"

p = Person("Alice", 25)
print(p._name)  # Accessible but not recommended
print(p._display_info())  # Accessible but intended for internal use
```
💡 Rule: Protected members can be accessed directly but should be treated as internal variables.

## 2. Protected Members Can Be Accessed in Subclasses
- Protected members are inherited and can be accessed inside child classes.
- This makes them useful for attributes or methods that should be shared between a parent and child class but not exposed to the outside world.
```
class Parent:
    def __init__(self):
        self._value = 100  # Protected attribute

class Child(Parent):
    def show_value(self):
        return f"Value from Parent: {self._value}"  # Accessing protected member in subclass

c = Child()
print(c.show_value())  # Accessing protected attribute from subclass
```
💡 Rule: Protected members can be inherited and used in subclasses.

## 3. Protected Members Can Be Modified Outside the Class (But Shouldn’t Be)
- Even though protected members should be used only within the class and its subclasses, Python does not restrict modification.
- This means you can modify a protected attribute from outside, but it is against best practices.
```
class Car:
    def __init__(self, brand, speed):
        self._brand = brand  # Protected attribute
        self._speed = speed  # Protected attribute

car1 = Car("Toyota", 120)
car1._speed = 150  # Modifying a protected attribute (not recommended)
print(car1._speed)
```
💡 Rule: Protected members can be modified, but this should be avoided in general.

## 4. Accessing Protected Methods in a Subclass
- Protected methods (methods prefixed with _) are also inherited and can be called inside child classes.
```
class Animal:
    def _sound(self):  # Protected method
        return "Some generic sound"

class Dog(Animal):
    def make_sound(self):
        return self._sound()  # Calling protected method from parent class

dog = Dog()
print(dog.make_sound())  # Works because protected methods are accessible in subclasses
```
💡 Rule: Protected methods are accessible inside subclasses.

## 5. Difference Between Private (__) and Protected (_)
| Feature |	Private (__)	| Protected (_) |
|:-------:|:--------------:|:------------:|
| Prefix |	Double underscore (__)	| Single underscore (_) |
|Accessibility|	Not accessible directly outside the class|	Can be accessed outside the class but discouraged|
|Inheritance|	Not inherited (needs getters/setters)|	Inherited and accessible in subclasses|
|Modification|	Cannot be modified directly outside the class|	Can be modified (not recommended)|
|Use Case	|Strict encapsulation (completely hidden)|	Controlled inheritance (for subclass use)|

## 6. Best Practices for Using Protected Members
- ✅ Use protected members when you want a variable or method to be accessible in subclasses but not directly exposed to other parts of the program.
- ✅ Do not access or modify protected members outside the class unless absolutely necessary.
- ✅ If you need to enforce strict encapsulation, use private (__) members instead.
- ✅ Use getter and setter methods for controlled access.





