# Higher order functions
- A higher-order function is a function that takes another function as an argument or returns a function.
- This allows for more flexible and reusable code.

Example 1: Passing a Function as an Argument
Functions can be passed just like variables
```python
def greet(name):
    return f"Hello, {name}!"

def process_greeting(func, name):
    return func(name)  # Calling the passed function

print(process_greeting(greet, "Chithra"))  # Output: Hello, Chithra!
```

Example 2: Returning a Function
A function can return another function.
```python
def multiply_by(n):
    def multiply(x):
        return x * n  # Uses 'n' from the outer function
    return multiply  # Returns the inner function

double = multiply_by(2)  # Creates a function that multiplies by 2
print(double(5))  # Output: 10
```

