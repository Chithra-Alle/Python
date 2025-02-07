# Exception Handling
Exception handling is the process of responding to unwanted or unexpected events when a computer program runs. Exception handling deals with these events to avoid the program or system crashing, and without this process, exceptions would disrupt the normal operation of a program.
# Exceptions in Python
Python has many built-in exceptions that are raised when your program encounters an error (something in the program goes wrong).

When these exceptions occur, the Python interpreter stops the current process and passes it to the calling process until it is handled. If not handled, the program will crash.

# Python try...except
try….. except blocks are used in python to handle errors and exceptions. The code in try block runs when there is no error. If the try block catches the error, then the except block is executed. 

 ## Syntax:
 ```python
 try:
      #statements which could generate 
      #exception
except:
      #Soloution of generated exception
```
## Example:
```python
try:
    num = int(input("Enter an integer: "))
except ValueError:
    print("Number entered is not an integer.")
 ```

## Output:
```
Enter an integer: 6.022
Number entered is not an integer.
```



# Finally Clause
The finally code block is also a part of exception handling. When we handle exception using the try and except block, we can include a finally block at the end. The finally block is always executed, so it is generally used for doing the concluding tasks like closing file resources or closing database connection or may be ending the program execution with a delightful message.
# Syntax:
```
try:
   #statements which could generate 
   #exception
except:
   #solution of generated exception
finally:
    #block of code which is going to 
    #execute in any situation
    
   
```
The finally block is executed irrespective of the outcome of try……except…..else blocks\
One of the important use cases of finally block is in a function which returns a value.
# Example:
```python
try:
    num = int(input("Enter an integer: "))
except ValueError:
    print("Number entered is not an integer.")
else:
    print("Integer Accepted.")
finally:
    print("This block is always executed.")
 ```

## Output 1:
```
Enter an integer: 19
Integer Accepted.
This block is always executed.
```
## Output 2:
```
Enter an integer: 3.142
Number entered is not an integer.
This block is always executed.
```

# Defining Custom Exceptions
In Python, you can create and raise your own errors using the raise keyword. This is useful when you want to stop the program if something specific goes wrong.
### 🔹 Basic Example
```
age = int(input("Enter your age: "))
if age < 18:
    raise ValueError("You must be 18 or older!")
```
💡 Explanation:
If the user enters an age less than 18, Python stops and shows the error message.
raise ValueError("message") forces an error when a condition is met.

### 🔹 Creating a Custom Error Class
You can create your own error type by making a new class that inherits from Exception.
```
class TooYoungError(Exception):
    pass  # Just a custom error with no extra behavior

age = 15
if age < 18:
    raise TooYoungError("You are too young to proceed!")
```
💡 Why?
This lets you define specific error types to make debugging easier.

### 🔹 Custom Error with More Details
You can add extra behavior to your custom error by defining an __init__ method.
```
class AgeError(Exception):
    def __init__(self, age, message="Age must be 18 or older!"):
        self.age = age
        self.message = message
        super().__init__(f"{message} (You entered: {age})")

age = 16
if age < 18:
    raise AgeError(age)
```




