# What are Decorators in Python?
- A decorator is a special function that modifies another function without changing its actual code.
- It adds extra functionality to a function in a simple way.
- Think of a decorator like a wrapper around a gift 🎁.
- The gift (function) stays the same, but the wrapper (decorator) adds extra decoration (functionality).

### ✅ Basic Example Without Decorator
Normally, we call a function like this:
```python
def greet():
    return "Hello!"

print(greet())  # Output: Hello!
```
Now, let's say we want to add extra behavior—like making the text uppercase without modifying the original function. We can do this using a decorator.

### 🚀 How to Create a Decorator?
1. A decorator is just a function that takes another function as input.
2. It adds extra functionality.
3. It returns a modified version of the function.

### ✅ Example of a Simple Decorator
```python
def uppercase_decorator(func):
    def wrapper():
        original_result = func()  # Call the original function
        modified_result = original_result.upper()  # Convert output to uppercase
        return modified_result
    return wrapper  # Return the modified function

@uppercase_decorator  # Apply the decorator
def greet():
    return "hello, chithra!"

print(greet())  # Output: HELLO, CHITHRA!
```

### ✅ Using Decorators with Arguments
```python
def repeat_decorator(func):
    def wrapper(name):
        return func(name) + " " + func(name)  # Repeat the output
    return wrapper

@repeat_decorator
def greet(name):
    return f"Hello, {name}!"

print(greet("Chithra"))  # Output: Hello, Chithra! Hello, Chithra!
```

### ✅ Manually Assigning the Decorator
```python
def greet():
    return "hello, chithra!"

greet = uppercase_decorator(greet)  # Manually wrapping the function

print(greet())  # Output: HELLO, CHITHRA!
```


### ✅ Applying a Decorator to Two Functions
```python
def uppercase_decorator(func):
    def wrapper():
        return func().upper()
    return wrapper

@uppercase_decorator  # Decorates greet()
def greet():
    return "hello, chithra!"

@uppercase_decorator  # Decorates welcome()
def welcome():
    return "welcome to python!"

print(greet())   # Output: HELLO, CHITHRA!
print(welcome()) # Output: WELCOME TO PYTHON!
```

### ✅ Applying Multiple Decorators to One Function
```python
def exclaim_decorator(func):
    def wrapper():
        return func() + "!!!"
    return wrapper

@uppercase_decorator  # First decorator
@exclaim_decorator    # Second decorator
def greet():
    return "hello, chithra!"

print(greet())  # Output: HELLO, CHITHRA!!!
```
