# Private
- In Python, the private access specifier is used to restrict access to class members (attributes and methods) from outside the class. By convention, private members are intended to be used only within the class and should not be directly accessed or modified from outside.
- However, Python does not have true private members like some other languages (e.g., C++ or Java). Instead, it relies on a naming convention to indicate private members.


### 1. Convention for Private Members:
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

### 2. Name Mangling
- When a member is prefixed with double underscores, Python changes its name internally to avoid accidental access.
- The private member __brand will be stored as _Car__brand internally.
```
car1 = Car("Tesla", 120)
print(car1._Car__brand)  # Access private attribute via name mangling (Not recommended)
```
💡 Rule: Name mangling makes private attributes harder to access but doesn't completely prevent it. Direct access is discouraged.


### 3. Private Members Cannot Be Accessed Directly:
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

# 4. Accessing Private Members via Methods:
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


