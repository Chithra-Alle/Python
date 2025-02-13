# Command Line Arguments

## What are Commadn Line Arguments?
- Command line arguments are values or parameters that you can pass to a program when you run it from the command line (or terminal).
- These arguments help control how the program runs, such as specifying files to process, setting options, or passing in configuration values.
- For example, if you want to run a program that processes an image file, you can pass the file name as a command line argument to tell the program which image to work on.

## How to Use Command Line Arguments in Python:
1. Running a Program with Arguments:
- When you run a Python script, you can provide values after the script name. For example:
```
python my_script.py arg1 arg2 arg3
```

2. Accessing Argumetns in Python:
- In python you can acces these arguments using the sys module.
- The list sys.argv holds all the arguments passed to the script.
```
   example.py
import sys
# Print the command line arguments
print("Command line arguments:", sys.argv)
```


## Why use command line arguments
- Control the Program's Behavior: You can use them to change the behavior of your program. For example, you might want to specify an input file or enable a special mode.
- They allow you to use your program in different situations without modifying the code each time.
### Example of Practical Use:
If you're writing a program that processes files, you might want to specify the file to process as a command line argument.

```
# file_processor.py
import sys

# Check if the user passed the filename as an argument
if len(sys.argv) < 2:
    print("Please provide a filename as a command line argument.")
else:
    filename = sys.argv[1]
    print(f"Processing file: {filename}")
```

Run Script like:
```
python file_processor.py data.txt
```

# argparse a way to handle command line arguments
**What is argparse?**
- argparse is a Python library that provides a more structured and user-friendly way to handle command line arguments.
- Instead of manually handling arguments with sys.argv, argparse helps you define the arguments clearly, provide descriptions, set default values, and even display helpful error messages if the user provides incorrect inputs.

**Why Use argparse?**
- User-friendly: It automatically generates help and usage messages.
- Flexible: You can specify types, default values, and make arguments optional or required.
- Error handling: It helps in handling errors when the wrong arguments are passed.


**How to Use argparse?**
### Step 1: Import argparse
- You need to first import the argparse module:
```
import argparse
```
### Step 2: Create an ArgumentParser object
- The ArgumentParser class is the starting point. It allows you to define what arguments your program will accept.
```
parser = argparse.ArgumentParser(description="A simple program that accepts arguments.")
```
### Step 3: Define the Arguments
- Use the add_argument() method to define what arguments you expect. Each argument will be identified by a name and can have options like default values, types, or whether it is required.
```
parser.add_argument('filename', type=str, help="The file to process")
parser.add_argument('-v', '--verbose', action='store_true', help="Enable verbose mode")
```
1. "-" means optional argument, used for single character
2. "--" is also optional arguement, used for multiple character
3. without both of them is positional argument, the use must provide it

### Step 4: Parse the Arguments
- After defining the arguments, you need to parse them using parse_args().
```
args = parser.parse_args()
```
- This will read the arguments passed from the command line and store them in the args object.

###  Step 5: Access the Arguments
- Now you can use args to access the values passed by the user.
```
print(f"Filename: {args.filename}")
if args.verbose:
    print("Verbose mode is enabled")
```
### Step 6: Running the Program
- Run the script from the command line like this:
```
python script_name.py input.txt -v
```
### Example code
```
import argparse

# Create the parser
parser = argparse.ArgumentParser(description="A program to process command line arguments.")

# Define command line arguments
parser.add_argument('filename', type=str, help="The input filename to process")
parser.add_argument('-v', '--verbose', action='store_true', help="Enable verbose mode")

# Parse the arguments
args = parser.parse_args()

# Use the arguments
print(f"Processing file: {args.filename}")
if args.verbose:
    print("Verbose mode enabled")
```
### Output
```
Processing file: input.txt
Verbose mode enabled
```

### More Options with argparse:
1. Default Values: You can specify default values for arguments.
```
parser.add_argument('--output', type=str, default="output.txt", help="Output file")
If the user doesn't provide an --output argument, the program will use "output.txt" by default.
```
2. Type Checking: You can specify the type of the argument, like int, float, str, etc.
```
parser.add_argument('--count', type=int, help="Number of items to process")
This ensures that the count argument must be an integer.
```
3. Optional Arguments with a Flag: Flags allow you to make arguments optional and can be specified with short (-v) or long (--verbose) options.
```
parser.add_argument('--verbose', action='store_true', help="Enable verbose output")
```


### Example with Multiple Arguments:
```
import argparse

# Create the parser
parser = argparse.ArgumentParser(description="Program to process files and numbers.")

# Define arguments
parser.add_argument('input', type=str, help="Input file")
parser.add_argument('--output', type=str, default="result.txt", help="Output file (default: result.txt)")
parser.add_argument('--count', type=int, help="Number of items to process")
parser.add_argument('-v', '--verbose', action='store_true', help="Enable verbose mode")

# Parse the arguments
args = parser.parse_args()

# Print parsed values
print(f"Input file: {args.input}")
print(f"Output file: {args.output}")
if args.count:
    print(f"Processing {args.count} items")
if args.verbose:
    print("Verbose mode enabled")
```
You can run this script like:
```
python script.py input.txt --output result.txt --count 5 -v
```


  
