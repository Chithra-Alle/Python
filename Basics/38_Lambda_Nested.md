# Lambda Functions in Python
In Python, a lambda function is a small anonymous function without a name. It is defined using the lambda keyword and has the following syntax:

```python
lambda arguments: expression
```
Lambda functions are often used in situations where a small function is required for a short period of time. They are commonly used as arguments to higher-order functions, such as map, filter, and reduce.

Here is an example of how to use a lambda function:

```python
# Function to double the input
def double(x):
  return x * 2

# Lambda function to double the input
lambda x: x * 2
```
The above lambda function has the same functionality as the double function defined earlier. However, the lambda function is anonymous, as it does not have a name.

Lambda functions can have multiple arguments, just like regular functions. Here is an example of a lambda function with multiple arguments:

```python
# Function to calculate the product of two numbers
def multiply(x, y):
    return x * y

# Lambda function to calculate the product of two numbers
lambda x, y: x * y
```
Lambda functions can also include multiple statements, but they are limited to a single expression. For example:

```python
# Lambda function to calculate the product of two numbers,
# with additional print statement
lambda x, y: print(f'{x} * {y} = {x * y}')
```
In the above example, the lambda function includes a print statement, but it is still limited to a single expression.

### Lambda Functins
- What is a Lambda Function? A lambda function in Python is an anonymous function that is defined using the lambda keyword.
- It can take multiple arguments but has only one expression.
- Syntax: lambda arguments: expression

Rules for Lambda Functions in Python

1️⃣ Must Have Only One Expression

  1. A lambda function cannot have multiple expressions or statements.
  2. It evaluates a single expression and returns the result automatically.
2️⃣ No Assignments Inside Lambda

1. You cannot use the = operator inside a lambda function.
2. If you need a variable assignment, use a normal function instead.
3️⃣ Can Take Any Number of Arguments

1. A lambda function can accept multiple arguments, but it can only evaluate one expression.
4️⃣ Cannot Have return

1. You cannot use return (implicit return is always used).

# Nested Functions
- A nested function is a function that is defined inside another function.
-  The inner function is local to the outer function, meaning it cannot be accessed directly from outside.

- Nested functions in Python are powerful tools for encapsulation, scope control, and reusability. 
- They help organize code by keeping helper functions private, accessing outer variables through closures, and modifying them using nonlocal.

```python
# Example 
def authenticate(username, password):
    def check_credentials():
        stored_username = "admin"
        stored_password = "password123"
        return username == stored_username and password == stored_password
    
    return check_credentials

login_attempt = authenticate("admin", "password123")
if login_attempt():
    print("Login Successful!")  # Output: Login Successful!
else:
    print("Invalid Credentials")
```

```python
# example
def smart_home(device):
    def control(action):
        if device == "AC":
            return f"AC turned {'ON' if action == 'on' else 'OFF'}"
        elif device == "tempcontrol":
            return f"Temperature set to {action}°C"
        else:
            return "Device not recognized"
    
    return control

ac_control = smart_home("AC")
temp_control = smart_home("tempcontrol")

print(ac_control("on"))      # Output: AC turned ON
print(temp_control(22))    # Output: Temperature set to 22°C
```
```python
# example
def sentiment_analyzer():
    def analyze(text):
        positive_words = ["good", "excellent", "amazing", "happy"]
        negative_words = ["bad", "terrible", "sad", "angry"]
        
        if any(word in text.lower() for word in positive_words):
            return "Positive Sentiment 😊"
        elif any(word in text.lower() for word in negative_words):
            return "Negative Sentiment 😞"
        else:
            return "Neutral Sentiment 😐"
    
    return analyze
```





Lambda functions are often used in conjunction with higher-order functions, such as map, filter, and reduce which we will look into later.
