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
Example 3: Built-in Higher-Order Functions (map, filter, reduce)
Python has built-in higher-order functions that take other functions as arguments.

### map() - Applies a function to each item in a list
```python
numbers = [1, 2, 3, 4]
squared = list(map(lambda x: x ** 2, numbers))  # Squares each number
print(squared)  # Output: [1, 4, 9, 16]
```
### filter() - Filters elements based on a condition
```python
numbers = [1, 2, 3, 4, 5, 6]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))  # Keeps only even numbers
print(even_numbers)  # Output: [2, 4, 6]
```
### reduce() - Combines all elements into a single value
```python
from functools import reduce

numbers = [1, 2, 3, 4]
sum_numbers = reduce(lambda x, y: x + y, numbers)  # Adds all numbers
print(sum_numbers)  # Output: 10
```
Why Use Higher-Order Functions?
- ✅ Makes code more reusable
- ✅ Reduces repetition
- ✅ Improves readability
