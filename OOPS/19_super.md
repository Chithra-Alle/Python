#  *super* Keyword
The super keyword in Python is used to call a method from a parent (super) class inside a child (sub) class. It is commonly used in inheritance to extend or override the behavior of parent class methods.

### Rules for using super
- Access Parent Class Methods:
*super() allows calling a method from the parent class inside the child class.*
- Works with Multiple Inheritance:
*In multiple inheritance, super() follows the Method Resolution Order (MRO) to call the next class in the hierarchy.*
- No Need for Explicit Parent Class Name:
*Unlike calling Parent.method(self), super() makes the code more flexible by automatically referring to the correct superclass.*
- Does Not Require self:
*Unlike normal method calls, super().method() does not require passing self explicitly.*


### Example 1: Using super() in Single Inheritance
```
class Parent:
    def greet(self):
        print("Hello from Parent!")

class Child(Parent):
    def greet(self):
        super().greet()  # Call Parent's greet method
        print("Hello from Child!")

c = Child()
c.greet()
```
Output
```
Hello from Parent!
Hello from Child!
```


### Example 2: Using super() in __init__ Method
```
class Animal:
    def __init__(self, name):
        self.name = name
        print(f"Animal {self.name} created")

class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name)  # Calls Animal's __init__
        self.breed = breed
        print(f"Dog of breed {self.breed} created")

d = Dog("Bruno", "Labrador")
```
output
```
Animal Bruno created
Dog of breed Labrador created
```


### Example 3: super() in Multiple Inheritance
```
class A:
    def show(self):
        print("Class A")

class B(A):
    def show(self):
        super().show()  # Calls A's show method
        print("Class B")

class C(B):
    def show(self):
        super().show()  # Calls B's show method
        print("Class C")

c = C()
c.show()
#output
Class A
Class B
Class C
```

### Example 4: super() in Diamond Problem (MRO)
```
class A:
    def show(self):
        print("Class A")

class B(A):
    def show(self):
        print("Class B")
        super().show()

class C(A):
    def show(self):
        print("Class C")
        super().show()

class D(B, C):  # Multiple Inheritance
    def show(self):
        print("Class D")
        super().show()

d = D()
d.show()
#output
Class D
Class B
Class C
Class A
```





