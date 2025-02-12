# Python Class Methods
-  A class method in Python is a method that is bound to the class rather than its instance.
-  It takes the class itself as its first argument, which is conventionally named cls.
-  This allows class methods to access or modify class-level attributes, which are shared by all instances of the class.
- To define a class method, we use the @classmethod decorator.

### Rules for Class Methods
1. Receives cls as the First Argument: Instead of the self parameter used in instance methods, class methods receive cls, which represents the class itself.
2. Can Modify Class Attributes: Class methods have access to and can modify class-level attributes (shared by all instances of the class).
3. Can Be Called on the Class or an Instance: Class methods can be called using both the class name and an instance of the class.
4. Cannot Access Instance Attributes: Class methods do not have access to self, so they cannot modify instance-level attributes.
5. Used for Factory Methods: Often used to create factory methods, which are alternative constructors to create instances of the class.

## Example 1: Basic Class Method
```
class Person:
    name = "Unknown"  # Class-level attribute

    @classmethod
    def change_name(cls, new_name):
        cls.name = new_name  # Modifies class-level attribute

# Calling class method using class name
print(Person.name)  # Output: Unknown
Person.change_name("John")  # Changing class-level attribute
print(Person.name)  # Output: John

```
🔹 Explanation:
- change_name is a class method that modifies the class-level attribute name.
- It’s called using Person.change_name(), and it affects all instances that share the name attribute.


## Example 2: Class Method with Instances
```
class Person:
    count = 0  # Class-level attribute to count instances

    def __init__(self, name):
        self.name = name  # Instance-level attribute
        Person.count += 1  # Access class-level attribute from instance

    @classmethod
    def total_count(cls):
        return cls.count  # Access class-level attribute

# Creating instances
p1 = Person("Alice")
p2 = Person("Bob")
print(Person.total_count())  # Output: 2 (Accessing class-level attribute)
```
🔹 Explanation:
- total_count() is a class method that returns the value of count, a class-level attribute that tracks how many instances of Person have been created.


## Example 3: Factory Method Using Class Method
```
class Car:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

    @classmethod
    def from_string(cls, car_str):
        brand, model = car_str.split("-")  # Create object from string
        return cls(brand, model)

# Using the factory method to create an object
car = Car.from_string("Toyota-Corolla")
print(car.brand)  # Output: Toyota
print(car.model)  # Output: Corolla
```
🔹 Explanation:
- from_string() is a factory method that converts a string to a Car object.
- The method is called using Car.from_string(), and it creates an instance of Car from the string.



## Example 4: Calling Class Methods on Instances and Classes
```
class Dog:
    species = "Canine"  # Class-level attribute

    @classmethod
    def describe(cls):
        return f"A {cls.species} is a domestic animal."

# Calling class method using class name
print(Dog.describe())  # Output: A Canine is a domestic animal.

# Calling class method using an instance
dog = Dog()
print(dog.describe())  # Output: A Canine is a domestic animal.
```
🔹 Explanation:
- describe() is a class method that works with class-level data (species).
- It can be called using either the class name (Dog.describe()) or an instance (dog.describe()).


## Conclusion
- Class methods are bound to the class and take cls as the first argument.
- They can modify class-level attributes but cannot access instance-specific data.
- Class methods are useful for working with class-level data or creating factory methods for object creation.


