# Introspection
- Introspection in Python refers to the ability of a program to examine the type or properties of an object at runtime.
- It allows you to inspect the object’s attributes, methods, and structure during the execution of the code, which can be helpful for debugging, dynamic programming, or understanding the behavior of objects.

### What Can You Inspect?
1. The type of an object.
2. The attributes (variables) and methods (functions) of an object.
3. The inheritance structure of classes.
4. The modules and functions available in your program.

### Why Use Introspection?
1. It helps you dynamically interact with objects and classes.
2. It is useful in debugging to understand the state of an object.
3. It can be helpful in dynamic programming, where the behavior or structure of an object needs to be inspected and modified at runtime.

### *Common Techniques for Introspection in Python*
1. type()
You can use type() to find the type of an object.
```
x = 10
print(type(x))  # Output: <class 'int'>
```

2. dir()
dir() is used to list all the **attributes and methods** of an object.
```
class Person:
    def __init__(self, name):
        self.name = name

    def greet(self):
        print("Hello", self.name)

p = Person("Alice")
print(dir(p))  # Output: ['__class__', '__delattr__', '__dict__', '__doc__', '__eq__', ..., 'greet', 'name']
```

3. id()
id() returns the unique identifier (memory address) of an object.
```
a = 10
print(id(a))  # Output: (memory address of `a`)
```

4 hasattr()
hasattr() checks if an object has a specific attribute or method.
```
class Person:
    def __init__(self, name):
        self.name = name

p = Person("Bob")
print(hasattr(p, 'name'))  # Output: True
print(hasattr(p, 'age'))   # Output: False
```


5. getattr()
getattr() retrieves the value of an attribute if it exists.
```
print(getattr(p, 'name'))  # Output: Bob
```

6. setattr()
setattr() is used to set or modify an attribute dynamically.
```
setattr(p, 'age', 25)
print(p.age)  # Output: 25
```

7. delattr()
delattr() deletes an attribute from an object.
```
delattr(p, 'age')
print(hasattr(p, 'age'))  # Output: False
```

8. callable()
callable() checks if an object can be called (i.e., if it's a function or method).
```
print(callable(p.greet))  # Output: True
print(callable(p.name))   # Output: False
```

9. _dict__ Attribute
The __dict__ attribute is a dictionary that contains the attributes and their values of an object. It provides a more detailed look at an object's attributes compared to dir(), as it includes only instance attributes (not methods).
```
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

# Creating an instance of Person
p = Person("Bob", 25)

# Using __dict__ to view instance attributes
print(p.__dict__)
```

10. help() Function
The help() function provides detailed documentation about any Python object (module, class, method, function, etc.). It gives you information about the object's purpose, usage, and the available methods or attributes.
```
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        print(f"Hello, {self.name}!")

# Using help() on the Person class
help(Person)
```

