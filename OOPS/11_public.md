# Public Access Specifier in Python
All the variables and methods (member functions) in python are by default public. Any instance variable in a class followed by the ‘self’ keyword ie. self.var_name are public accessed.
## Example:
```python
class Student:
    # constructor is defined
    def __init__(self, age, name):
        self.age = age               # public variable
        self.name = name             # public variable

obj = Student(21,"Harry")
print(obj.age)
print(obj.name)
```
## Output:
```
21
Harry
```

## Summary of Rules for Public Access Specifier
- ✅ Public members can be accessed and modified anywhere.
- ✅ Public methods can be inherited and called outside the class.
- ✅ Use getter and setter methods to manage public attributes safely.
- ✅ Public members do not enforce encapsulation, which may lead to unintended changes.
- ✅ Always follow naming conventions for better readability and maintainability.
