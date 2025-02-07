
# Python Sets

| Feature | Set | Frozen Set|
|:-------:|:---:|:---------:|
|Mutable | yes | No|
|can add/remove elements?| yes | No|
|can contain lsits?|no|no|

sets in Python are mutable because you can add or remove elements after creating them. However, the elements inside a set must be immutable (i.e., numbers, strings, tuples, etc.)

## 1️⃣ Mutability of Sets (✅ Can be Modified)
```python
my_set = {1, 2, 3}
my_set.add(4)  # Adding an element
my_set.remove(2)  # Removing an element
print(my_set)  # Output: {1, 3, 4}

```
✅ Modifiable: We can add or remove elements.

## 2️⃣ Set Elements Must Be Immutable (❌ No Lists, Yes Tuples)
```python
my_set = {1, 2, (3, 4)}  # Tuples are allowed
print(my_set)  # Output: {1, 2, (3, 4)}

# ❌ This will cause an error:
# my_set = {1, 2, [3, 4]}  # ❌ Lists are mutable and cannot be inside a set

```
❌ Lists cannot be inside sets because they are mutable.


## 3️⃣ Frozen Sets (Immutable Version of Sets)
If you want an immutable set, use frozenset():
```python
f_set = frozenset({1, 2, 3})
# f_set.add(4)  # ❌ Error: 'frozenset' object has no attribute 'add'
```
✅ Frozen sets cannot be modified after creation.





✅ You cannot modify individual elements in a set, but
✅ You can add or remove elements using .add(), .remove(), .update(), etc.
```python
info = {"Carla", 19, False, 5.9}
info.add("New Item")  # ✅ Allowed
info.remove(19)  # ✅ Allowed
print(info)
```


❌ But this is not allowed:
```python
info[0] = "Changed Item"  # ❌ Error: 'set' object does not support indexing
```

## 4 How to Create an Empty Set?
```python
empty_set = {}
print(type(empty_set))  # ❌ Output: <class 'dict'> (NOT a set!)
```
This creates an empty dictionary, not a set!



```python
empty_set = set()
print(type(empty_set))  # ✅ Output: <class 'set'>
```
✅ To create an empty set, use above code




