## `if __name__ == "__main__"` in Python
The if __name__ == "__main__" idiom is a common practice in Python that helps you control what code should run when a script is executed directly, and what should run when the script is imported into another script.



##Why do we use if __name__ == "__main__"?
- In Python, every script has a special built-in variable called __name__.
- When you run a script directly, the value of __name__ is set to "__main__".
- However, if you import that script into another script, __name__ is set to the name of the script/module.
- This behavior allows you to write code that:
- Runs when you run the script directly (e.g., for testing or as a standalone program)
- Doesn't run when the script is imported into another script as a module, but still allows the functions and variables to be accessed.


###Simple Example:
- Let's say you have a Python file called example.py, and you want to control the flow of execution depending on how it's being used.

```python
# example.py
def greet():
    print("Hello from the greet function!")

def main():
    print("This is the main function.")
    greet()

if __name__ == "__main__":
    main()

```
### What Happens When You Run It Directly?
- If you run example.py directly (by using python example.py in your terminal),
- Python will execute the code inside the main() function because __name__ will be equal to "__main__".
```python
This is the main function.
Hello from the greet function!

```
### What Happens When You Import It into Another Script?
- If you import example.py into another script (say, another_script.py), 
- the main() function will not be called automatically. 
- Instead, you can call the greet() function or any other function defined in example.py.

Here’s how it works:
```python
# another_script.py
import example

example.greet()  # This will run the greet function from example.py

```
```
Hello from the greet function!
```

- Notice that the message from main() wasn't printed because the main() function only runs when example.py is executed directly (due to the if __name__ == "__main__": condition).
## Summary:
- The if __name__ == "__main__": block is used to control whether certain code in a script should run when the script is executed directly or when it is imported as a module in another script.
- It's not necessary to use it in every script, but it's a good practice when you want to separate the code meant for execution and the code meant for importing.

