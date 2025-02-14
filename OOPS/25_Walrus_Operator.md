# Walrus Operator
The walrus operator (:=), introduced in Python 3.8, is used for assignment expressions. It allows you to assign a value to a variable as part of an expression, rather than a separate statement. This can make code more concise and readable.

### Rules for using the walrus operator
1. **Assigns and Returns a Value:** It assigns a value to a variable and returns that value simultaneously.
2. **Used Inside Expressions:** Unlike =, which is a statement, := can be used inside expressions like if, while, list comprehensions, etc.
3. **Cannot Be Used at the Top Level:** The walrus operator cannot be used as a standalone assignment statement like x := 10. You must use it within an expression.
4. **Useful for Avoiding Redundant Calculations:** It helps in avoiding repeated calculations by storing the result in a variable inside an expression.

## Examples of the Walrus Operator
1. Using in while Loops
- without the walrus operator
```
number = input("Enter a number (or 'exit' to stop): ")
while number != "exit":
    print(f"You entered: {number}")
    number = input("Enter a number (or 'exit' to stop): ")
```
- with the walrus operator
```
while (number := input("Enter a number (or 'exit' to stop): ")) != "exit":
    print(f"You entered: {number}")
```


2. Using the if statement
- wihtout the walrus operator
```
value = len("Hello World")
if value > 5:
    print(f"String length is {value}")
```
- with walrus operator
```
if (value := len("Hello World")) > 5:
    print(f"String length is {value}")
```


3. Using list comprehention
- without the walrus operator
```
numbers = [10, 20, 30, 40, 50]
filtered = []
for num in numbers:
    squared = num ** 2
    if squared > 800:
        filtered.append(squared)
print(filtered)
```

-with walrus operator
```
numbers = [10, 20, 30, 40, 50]
filtered = [squared for num in numbers if (squared := num ** 2) > 800]
print(filtered)
```



