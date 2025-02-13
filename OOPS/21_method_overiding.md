# Method Overriding in Python
- Method overriding in Python allows a child class to provide a specific implementation of a method that is already defined in its parent class. This is useful when you want to modify or extend the behavior of the inherited method.

### How Method Overriding Works?
1. The child class defines a method with the same name as the one in the parent class.
2. When the method is called on a child class object, the child class's version overrides the parent class’s version.
3. You can still call the parent class method using super().

*Example 1: Basic Method Overriding*
```
class Animal:
    def sound(self):
        print("Animals make sounds")

class Dog(Animal):
    def sound(self):  # Overriding the method
        print("Dog barks")

d = Dog()
d.sound()  # Output: Dog barks
```
- 🔹 Explanation:
- Dog class overrides the sound() method from Animal.
- Instead of "Animals make sounds", it prints "Dog barks".


*Example 2: Using super() to Call Parent Method*
```
class Animal:
    def sound(self):
        print("Animals make sounds")

class Cat(Animal):
    def sound(self):
        super().sound()  # Calls parent class method
        print("Cat meows")

c = Cat()
c.sound()
Output:
Animals make sounds
Cat meows
```
- 🔹 Explanation:
- super().sound() calls the sound() method of Animal first.
- Then the overridden method in Cat is executed.

*Example 3: Overriding __init__ Method*
```
class Person:
    def __init__(self, name):
        self.name = name

class Student(Person):
    def __init__(self, name, grade):
        super().__init__(name)  # Calls Parent's __init__
        self.grade = grade

s = Student("Alice", "A")
print(s.name, s.grade)  # Output: Alice A
```
- 🔹 Explanation:
- The Student class overrides __init__ of Person.
- super().__init__(name) ensures that name is initialized properly.

*Example 4: Method Overriding in Multiple Inheritance*
```
class Parent1:
    def show(self):
        print("Parent1 show method")

class Parent2:
    def show(self):
        print("Parent2 show method")

class Child(Parent1, Parent2):
    def show(self):
        super().show()  # Calls Parent1's show() (follows MRO)
        print("Child show method")

c = Child()
c.show()
Output:
Parent1 show method
Child show method
```
- 🔹 Explanation:
- super().show() calls Parent1.show() (due to Method Resolution Order (MRO)).
- Then, Child.show() prints "Child show method".
### Key Takeaways
✔ Method overriding happens when a child class defines a method with the same name as the parent class.
✔ super() allows calling the parent method inside the child method.
✔ Used in constructor (__init__) overriding to extend initialization.
✔ In multiple inheritance, super() follows the Method Resolution Order (MRO).

