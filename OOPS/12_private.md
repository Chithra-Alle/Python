# Private
- In Python, the private access specifier is used to restrict access to class members (attributes and methods) from outside the class. By convention, private members are intended to be used only within the class and should not be directly accessed or modified from outside.
- However, Python does not have true private members like some other languages (e.g., C++ or Java). Instead, it relies on a naming convention to indicate private members.


## 1. Convention for Private Members:
- To make a member private in Python, prefix it with double underscores (__).
- This triggers name mangling, where Python internally changes the name of the attribute to make it harder to access directly outside the class.

```
class Car:
    def __init__(self, brand, speed):
        self.__brand = brand  # Private attribute
        self.__speed = speed  # Private attribute

    def __display_info(self):  # Private method
        return f"Car: {self.__brand}, Speed: {self.__speed} km/h"

    def public_method(self):
        return self.__display_info()  # Access private method from within the class

car1 = Car("Tesla", 120)
print(car1.public_method())  # Public method can access private method
```
💡 Rule: Private attributes and methods are prefixed with __ and are intended for internal use only.

## 2. Name Mangling
- When a member is prefixed with double underscores, Python changes its name internally to avoid accidental access.
- The private member __brand will be stored as _Car__brand internally.
```
car1 = Car("Tesla", 120)
print(car1._Car__brand)  # Access private attribute via name mangling (Not recommended)
```
💡 Rule: Name mangling makes private attributes harder to access but doesn't completely prevent it. Direct access is discouraged.


## 3. Private Members Cannot Be Accessed Directly:
- Private attributes and methods cannot be accessed directly from outside the class. Trying to do so results in an AttributeError.
```
car1 = Car("Tesla", 120)
print(car1.__brand)  # This will raise an AttributeError
```


Output
```
AttributeError: 'Car' object has no attribute '__brand'
```
💡 Rule: Private members are not directly accessible from outside the class.

## 4. Accessing Private Members via Methods:
- To provide controlled access to private attributes or methods, use getter and setter methods.
- This approach ensures data encapsulation, allowing validation or transformation before setting or getting values.
```python
class Car:
    def __init__(self, brand, speed):
        self.__brand = brand
        self.__speed = speed

    def get_brand(self):  # Getter method
        return self.__brand

    def set_brand(self, brand):  # Setter method
        self.__brand = brand

    def get_speed(self):
        return self.__speed

    def set_speed(self, speed):
        self.__speed = speed

car1 = Car("Tesla", 120)
print(car1.get_brand())  # Access private attribute via getter
car1.set_brand("BMW")  # Modify private attribute via setter
print(car1.get_brand())
```
💡 Rule: Use getter and setter methods to interact with private members instead of accessing them directly.


## 5.Private Methods
- Methods prefixed with double underscores are considered private and cannot be called directly from outside the class. They can only be accessed from within the class.
- Private methods are used for internal logic that should not be exposed externally.
  ```python
  class BankAccount:
    def __init__(self, balance):
        self.__balance = balance

    def __update_balance(self, amount):  # Private method
        self.__balance += amount

    def deposit(self, amount):
        self.__update_balance(amount)  # Access private method within a public method
        print(f"Deposited {amount}, New Balance: {self.__balance}")

account = BankAccount(1000)
account.deposit(500)  # Private method is used inside a public method ```
💡 Rule: Private methods handle internal functionality that should not be exposed.

## 6.  Private Variables Are Not Inherited in Subclasses
- While public variables are inherited by subclasses, private variables are not directly accessible in subclasses.
- To access them in subclasses, use getter and setter methods.

  ```python
 class Parent:
    def __init__(self, value):
        self.__value = value  # Private variable

    def get_value(self):
        return self.__value  # Getter method

class Child(Parent):
    def __init__(self, value):
        super().__init__(value)

child = Child(100)
print(child.get_value())  # Access private variable via getter method ```
💡 Rule: Private attributes cannot be accessed directly in subclasses but can be accessed through getter methods.

## 7. Use of Single Underscore _ (Protected vs Private):
- A single underscore (_) is used for protected attributes, which are intended to be used within the class and its subclasses, but they are still technically accessible outside the class.
- Double underscores (__) are used to indicate private attributes that are meant to be hidden.
```
class MyClass:
    def __init__(self):
        self._protected = "I am protected"  # Protected member
        self.__private = "I am private"    # Private member

obj = MyClass()
print(obj._protected)  # Accessible
print(obj.__private)   # Not accessible
```
💡 Rule: Use single underscore (_) for protected members (convention) and double underscore (__) for private members.
  

 
