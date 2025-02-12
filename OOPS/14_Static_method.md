# Static Methods in Python
A static method in Python is a method inside a class that does not depend on instance-specific data. It behaves like a regular function but is defined within a class and does not require access to instance (self) or class (cls) attributes.

To define a static method, we use the @staticmethod decorator.

### Rules for Static Methods
1. No Access to Instance (self): Static methods do not receive the self parameter and cannot modify instance attributes.
2. No Access to Class (cls): Unlike class methods, static methods do not receive the cls parameter and cannot modify class-level attributes.
3. Can be Called on Class or Instance: You can call a static method using both the class name and an instance.
4. Useful for Utility Functions: Static methods are used when the method logically belongs to the class but does not require any instance-specific data.

### Example 1: Basic Static Method
```python
class MathUtils:
    @staticmethod
    def add(a, b):
        return a + b

# Calling the static method using class name
print(MathUtils.add(5, 3))  # Output: 8

# Calling the static method using an instance
obj = MathUtils()
print(obj.add(10, 20))  # Output: 30
```
🔹 Explanation: The add method does not use self or cls, so it is defined as a static method.

### Example 2: Static Method vs Instance Method
```python
class Demo:
    def instance_method(self):
        return "This is an instance method"

    @staticmethod
    def static_method():
        return "This is a static method"

obj = Demo()

# Calling instance method (requires an instance)
print(obj.instance_method())  

# Calling static method (can be called with class name or instance)
print(Demo.static_method())  
print(obj.static_method())  
```
🔹 Explanation:

instance_method requires self, so it must be called using an instance.
static_method does not need self and can be called using either the class or instance.

### Example 3: When to Use Static Methods?
When creating utility methods that are logically related to the class but do not need access to instance or class attributes.
```python
class Validator:
    @staticmethod
    def is_even(number):
        return number % 2 == 0

print(Validator.is_even(10))  # Output: True
print(Validator.is_even(15))  # Output: False
```
🔹 Explanation: is_even checks if a number is even. It does not require instance or class attributes, so it's a static method.


### Conclusion
- Use @staticmethod when the method is related to the class but does not interact with instance or class variables.
- Static methods improve code organization and reusability.
- They are mostly used for utility functions within a class.

