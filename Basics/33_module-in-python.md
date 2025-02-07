# OS Module in Python

The `os` module in Python provides a way to interact with the operating system. It allows you to perform various tasks like working with files, directories, and environment variables, as well as running system commands.

In simple terms, it helps you control and access parts of your computer's operating system through your Python code.

## Common Uses of the `os` Module

1. **File and Directory Operations**:
   - Create, delete, and check files or directories.
   - Rename files or change their permissions.

2. **Path Operations**:
   - Join, split, or get information about file paths.

3. **Environment Variables**:
   - Get or set environment variables, which are system-wide settings (like paths to programs or system configuration).

4. **System Commands**:
   - Run system or shell commands from within your Python script.

## Example Uses of the `os` Module

### 1. Get current working directory
```python
import os
print(os.getcwd())  # This will print the current working directory (folder)
```
### change directory
```
import os
os.chdir("/path/to/directory")  # Change the working directory to the given path
```
###  List all files and directories in a folder
``` import os
print(os.listdir())  # This will list all files and directories in the current folder
```
etc....
