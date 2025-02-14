# Raw Text
- A raw text is a string which is prefixed with r, that tells python not to handle back slashes in any special way.
> print(r'\tChithra') will print like <br>
>   Chithra<br>
> print('\tChithra') will print as
> \tChithra


### Commonly Used Metacharacters
> . → Matches any single character except a newline<br>
> ^ → Matches the beginning of a string<br>
> ^ → Negotes the pattern mentioned after it<br>
> $ → Matches the end of a string<br>
> [] → Matches any character inside brackets<br>
> \d → Matches any digit (0-9)<br>
> \D → Matches any non-digit<br>
> \b → Matches a word boundary<br>
> \B → Matches not a word boundary<br>
> \w → Matches any word character (a-z,A-Z,1-9)<br>
> \W → Matches any non-word character(\n, . ,   , " ")<br>
> \s → Matches any whitespace (spaces, tabs, newlines)<br>
> \S → Matches any non-whitespace<br>
> "*" → Matches 0 or more repetitions of the previous character<br>
> "+" → Matches 1 or more repetitions<br>
> ? → Matches 0 or 1 repetitions<br>
> {n,m} → Matches between n and m occurrences<br>


Example
```
import re
str ='''
I am chithra.
chithraalle.gmail.com
and i Need to be cool yes.
I . so leave it'''
pattern = re.compile(r"chithraalle\.gmail\.com")
matches = pattern.finditer(str)
for match in matches:
    print(match)
# Output
re.Match object; span=(15, 36), match='chithraalle.gmail.com'>
```
here,
  - the . will be considered as special character, in order to tell python that consider . as a dot we need to add \ infront of it.


Example
```
import re
str ='''
I am chithra.
94415
chithraalle.gmail.com
and i Need to be cool yes.
I . so leave it'''
pattern = re.compile(r"\d+")
matches = pattern.finditer(str)
for match in matches:
    print(match)
output
<re.Match object; span=(15, 20), match='94415'>
```
here,
  - \d+ counts continuous digits as one value
  - but note that \d will count every digit as a value
  - similarly \D+ will count continuous non digit as one value
  - and \D will count every non digit as a value

## METHODS in REGULAR EXPRESSIONS

1. findall()
- returns a list of all matches
Example
```
import re
text = "The rain in Spain falls mainly in the plain."
pattern = re.compile(r"in")  
matches = pattern.findall(text)  # Finds all occurrences of "in"
print(matches)  # Output: ['in', 'in', 'in', 'in']
```
Why use this? It extracts all matches from a string.


2. finditer()
- return an iterator with match objects
Example
```
text = "apple, banana, mango"
pattern = re.compile(r"\b\w{5}\b")  # Finds words with exactly 5 letters
matches = pattern.finditer(text)  
for match in matches:
    print(match.group(), match.start(), match.end())
```
output
```
apple 0 5
mango 15 20
```
Why use this? It provides additional details like position.


3. sub()
- replaces occurences of a pattern
Example
```
text = "I love apples and apples are tasty."
pattern = re.compile(r"apples")
new_text = pattern.sub("bananas", text)
print(new_text)  # Output: I love bananas and bananas are tasty.
```
Why use this? To replace text dynamically.


4. match()
- checks if the pattern matches only at the start of the string
Example
```
text = "Python is great"
pattern = re.compile(r"Python")
match = pattern.match(text)
print(match.group()) if match else print("No match")  # Output: Python
```
Why use this? To check if a string starts with a pattern.


5. search()
- finds the first occurence anywhere in the string
Example
```
text = "Learning Python is fun"
pattern = re.compile(r"Python")
match = pattern.search(text)
print(match.group()) if match else print("No match")  # Output: Python
```
Why use this? To find the first occurrence of a pattern.


6. re.IGNORECASE (or re.I)
- makes the search case-insensitive
Example
```
text = "HELLO, Hello, hello!"
pattern = re.compile(r"hello", re.IGNORECASE)
matches = pattern.findall(text)
print(matches)  # Output: ['HELLO', 'Hello', 'hello']
```
Why use this? To match text regardless of case.


7. split()
- splits a stsring using a pattern
Example
```
text = "apple,banana;grape orange"
pattern = re.compile(r"[ ,;]")
words = pattern.split(text)
print(words)  # Output: ['apple', 'banana', 'grape', 'orange']
```

8. fullmatch()
- checks if the entire string matches
Example
```
pattern = re.compile(r"\d{4}")
match = pattern.fullmatch("1234")
print("Valid" if match else "Invalid")  # Output: Valid
```

9. compile()
improves efficiency when reusing the same pattern
Example
```
pattern = re.compile(r"\d+")
print(pattern.findall("There are 3 apples and 5 bananas."))  # Output: ['3', '5']
```
