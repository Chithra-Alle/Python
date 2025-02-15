# Lookahead Assertion((?=...)) in Regex
A lookahead assertion in regex allows you to check if a pattern exists ahead in the string without consuming characters. This means the regex engine does not move forward after checking the pattern inside (?=...).

### Why Use Lookahead?
- When matching patterns without a lookahead, regex consumes characters as it moves forward. This prevents overlapping matches.
- With lookahead ((?=...)), we can check for a match at every position, allowing us to capture overlapping substrings.

🔹 Basic Syntax
(?=pattern)
- This checks if pattern exists ahead in the string but does not consume characters.
- The regex engine stays at the same position after checking the pattern.

🔹 Example 1: Overlapping Matches
**Problem without lookahead**
You want to match every three-letter substring in "abcdef", but the normal regex skips overlapping parts.
```
import re

s = "abcdef"
pattern = re.compile(r"[a-z]{3}")  # Matches exactly 3 letters
matches = pattern.findall(s)

print(matches)
Output
['abc','def']
```

**Solution using lookahead for overlapping matches**
```
import re

s = "abcdef"
pattern = re.compile(r"(?=([a-z]{3}))")  # Lookahead allows overlap
matches = [match[0] for match in pattern.findall(s)]

print(matches)
output
['abc', 'bcd', 'cde', 'def']
```
👉 How it works?
- (?=([a-z]{3})) checks for 3-letter sequences at every position.
- The regex engine does not move forward after checking, allowing it to capture overlapping matches.


🔹 Example 2: Checking for a Pattern Without Consuming It
Imagine you want to find all "a" characters, only if they are followed by "b", without capturing "b".
```
import re

s = "aabacabc"
pattern = re.compile(r"a(?=b)")  # 'a' should be followed by 'b'
matches = pattern.findall(s)

print(matches)
output
['a', 'a']
```
👉 Why? It finds "a" at positions where "b" follows but does not consume "b".



🔹 Example 3: Validating a Password (Must Contain a Number)
Let's say we need a regex that ensures a password contains at least one digit, but we don't want to capture the whole password.
```
import re

password = "hello123"
pattern = re.compile(r"^(?=.*\d).{6,}$")  # At least one digit, 6+ characters

if pattern.match(password):
    print("Valid password")
else:
    print("Invalid password")
```
👉 How it works?
- (?=.*\d) ensures at least one digit (\d) exists somewhere.
- .{6,}$ ensures at least 6 characters in total.





# Negative Lookahead((?!....) in Regex
A Negative Lookahead is used when you want to exclude a specific pattern ahead in the string without consuming characters. It checks if a pattern does not exist after a certain position.


🔹 Basic Syntax
(?!pattern)
- This ensures that pattern does NOT exist at that position.
- The regex engine stays at the same position and continues matching.

🔹 Example 1: Exclude a Word
- Problem: Match "cat" but NOT if followed by "dog"
- You want to match "cat" only if it is NOT followed by "dog".
```
import re

s = "cat dog catfish cat"
pattern = re.compile(r"cat(?!\s*dog)")  # "cat" should NOT be followed by "dog"
matches = pattern.findall(s)

print(matches)
output
['catfish', 'cat']

```

🔹 Example 2: Exclude Certain File Extensions
- Problem: Match all filenames except .exe files
```
import re

files = ["report.doc", "image.png", "virus.exe", "notes.txt"]
pattern = re.compile(r"\b\w+\.(?!exe)\w+")  # Match any filename NOT ending in ".exe"

matches = [f for f in files if pattern.search(f)]
print(matches)
output
['report.doc', 'image.png', 'notes.txt']
```

🔹 Example 3: Validate a Password (No Spaces Allowed)
- A password should NOT contain spaces, but it must have at least 6 characters.
```
import re

password = "hello 123"
pattern = re.compile(r"^(?!.*\s).{6,}$")  # No spaces allowed

if pattern.match(password):
    print("Valid password")
else:
    print("Invalid password")
```

🔹 Example 4: Find Words That Do Not End With "ing"
- You want to find words except those ending in "ing".
```
import re

text = "playing reading coding sleeping walk talk"
pattern = re.compile(r"\b\w+\b(?!ing)")  # Match words NOT ending with "ing"

matches = pattern.findall(text)
print(matches)
```




# Word Boundary \b
In regex, \b represents a word boundary. It ensures that the match happens at the start or end of a word, rather than in the middle of another word.
🔹 What is a Word Boundary?
#### A word boundary (\b) occurs:
- Between a word character ([a-zA-Z0-9_]) and a non-word character ([^a-zA-Z0-9_]).
- At the start or end of a string, if the first or last character is a word character.
- 👉 This helps to match whole words instead of substrings inside larger words.


🔹 Example 1: Match Whole Words
```
import re

text = "cat category catalog"
pattern = re.compile(r"\bcat\b")  # Match "cat" as a separate word

matches = pattern.findall(text)
print(matches)
output
['cat']
```
👉 Why?
- "cat" matches because it is a separate word.
- "category" and "catalog" do NOT match because "cat" is inside them.
