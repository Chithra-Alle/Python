# Generators in Python
- Generators are a special type of iterable, like lists or tuples, but unlike lists, they do not store the entire sequence in memory.
-  Instead, they generate the values one by one as they are requested, which makes them much more memory-efficient, especially when working with large datasets or infinite sequences.

Generators in Python are created using two methods:
1. Generator Functions (using yield keyword)
2. Generator Expressions (using a syntax similar to list comprehensions)

### Key Characteristics of Generators:
- Memory Efficient: They generate values on-the-fly and do not store them in memory.
- Lazy Evaluation: The values are generated only when requested, which is known as lazy evaluation.
- Iterable: Like lists, generators can be iterated over using loops, and they can be passed to any function that requires an iterable.
- One-time Iteration: Once a generator’s values have been exhausted (i.e., it has yielded all values), it cannot be reset or reused.

### How Generators Work:
Generators are functions that use the yield statement to produce a series of values. Each time the generator function is called, it continues from where it last yielded a value, instead of starting from the beginning.

### Example 1: Generator Function
```
def count_up_to(n):
    count = 1
    while count <= n:
        yield count  # Yield is like return, but allows the function to resume
        count += 1

# Create a generator object
counter = count_up_to(5)

# Use a loop to iterate over the generator
for num in counter:
    print(num)
Output:
1
2
3
4
5
```
In this example:
- count_up_to is a generator function.
- Each time the yield statement is executed, it returns a value and pauses the function's execution. The function can be resumed from where it left off when the next value is requested.


### Example 2: Generator Expression
Generator expressions are similar to list comprehensions, but they return a generator instead of a list.
```
squares = (x*x for x in range(1, 6))  # Generator expression

for square in squares:
    print(square)
Output:

1
4
9
16
25
```
Here:
- The generator expression (x*x for x in range(1, 6)) creates a generator object.
- The values are computed one by one as they are needed, without storing them in memory.

### Rules for Using Generators:
**Use yield to create a generator:**
The yield keyword is used inside a function to make it a generator. When the function is called, it returns a generator object instead of executing the function completely.
**Generators are lazy iterators:**
They produce values only when iterated over, meaning they don’t compute the values all at once.
**Generators can't be re-used:**
Once all the values have been yielded, the generator is exhausted. If you try to iterate over it again, you will get no values.
**No need to call next() repeatedly in the loop:**
You can directly loop over a generator using a for loop, as Python internally calls next() for you until the generator is exhausted.
**Memory efficiency:**
Unlike lists, which hold all values in memory, generators produce one value at a time and use a constant amount of memory. This is particularly useful for large datasets or infinite sequences.


### Example: Generator for Fibonacci Sequence
```
def fibonacci(n):
    a, b = 0, 1
    while n > 0:
        yield a
        a, b = b, a + b
        n -= 1

fib = fibonacci(10)

for num in fib:
    print(num)
Output:

0
1
1
2
3
5
8
13
21
34
```
Here:
- The even_numbers generator yields even numbers indefinitely (infinite sequence), but you can stop it whenever you want by limiting the iteration.

### Advantages of Generators:
> Efficiency: They are memory efficient because they generate one item at a time and don’t store the whole sequence.
> Lazy Evaluation: They allow lazy evaluation, meaning values are computed only when needed, which can improve performance in some scenarios.
> Suitable for Infinite Sequences: You can use generators to create infinite sequences, such as streams of data.

### Disadvantages of Generators:
> One-time use: You can only iterate over a generator once. Once it’s exhausted, it cannot be reused unless recreated.
> Limited functionality: Since generators yield values one at a time, you can’t index or slice a generator like you can with lists.




