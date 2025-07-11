---
aliases:
  - "Part 1: Python Comprehensive Guide"
---
# Python Comprehensive Guide for Software Engineers

## Table of Contents

- [Basic Data Types](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#basic-data-types)
- [Collections and Data Structures](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#collections-and-data-structures)
- [Variables and Scope](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#variables-and-scope)
- [Control Flow](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#control-flow)
- [Functions](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#functions)
- [Classes and Object-Oriented Programming](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#classes-and-object-oriented-programming)
- [Modules and Packages](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#modules-and-packages)
- [File Handling](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#file-handling)
- [Error Handling](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#error-handling)
- [Functional Programming](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#functional-programming)
- [Iterators and Generators](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#iterators-and-generators)
- [Decorators](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#decorators)
- [Context Managers](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#context-managers)
- [Regular Expressions](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#regular-expressions)
- [Working with Data](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#working-with-data)
- [Concurrency and Parallelism](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#concurrency-and-parallelism)
- [Advanced Python Concepts](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#advanced-python-concepts)
- [Python Development Tools](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#python-development-tools)
- [Algorithms and Data Structures](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#algorithms-and-data-structures)
- [Performance and Optimization](https://claude.ai/chat/767dae45-bf20-48f2-98c5-14259004051c#performance-and-optimization)

## Basic Data Types

### Integers

**What they are**: Integers are zero, positive, or negative whole numbers without a fractional part and have unlimited precision.

**How they work**: Python integers have unlimited precision, meaning they can be as large as your system's memory allows without overflow.

**Examples**:

```python
# Simple integer assignment
x = 42

# Large integers work fine in Python
very_large = 10**100  # 1 followed by 100 zeros (a googol)

# Arithmetic operations
sum_result = 10 + 5  # 15
product = 7 * 6      # 42
power = 2**10        # 1024 (2 to the power of 10)

# Converting to integer
float_to_int = int(3.9)  # 3 (truncates decimal part)
str_to_int = int("42")   # 42
```

### Floating-Point Numbers

**What they are**: Floating-point numbers represent real numbers with a decimal point.

**How they work**: Python implements floating-point numbers using the IEEE 754 double-precision format, which means they have limited precision and can sometimes lead to rounding errors.

**Examples**:

```python
# Simple floating-point assignment
x = 3.14

# Scientific notation
scientific = 1.23e-4  # 0.000123

# Converting to float
int_to_float = float(42)    # 42.0
str_to_float = float("3.14")  # 3.14

# Be aware of floating-point precision issues
print(0.1 + 0.2)  # 0.30000000000000004 (not exactly 0.3)
```

### Strings

**What they are**: Strings are sequences of characters, used to represent text.

**How they work**: Strings in Python are immutable, meaning once created, they cannot be changed. Python 3 strings are Unicode by default.

**Examples**:

```python
# String creation
single_quotes = 'Hello'
double_quotes = "World"
triple_quotes = '''This string can
span multiple lines'''

# String concatenation
full_greeting = single_quotes + ", " + double_quotes + "!"  # "Hello, World!"

# String methods
upper_case = "hello".upper()  # "HELLO"
lower_case = "HELLO".lower()  # "hello"
stripped = "  hello  ".strip()  # "hello"

# String formatting
name = "Alice"
age = 30
f_string = f"{name} is {age} years old"  # "Alice is 30 years old"
formatted = "{} is {} years old".format(name, age)  # "Alice is 30 years old"

# String slicing
text = "Python"
first_char = text[0]  # "P"
substring = text[1:4]  # "yth"
reversed_text = text[::-1]  # "nohtyP"
```

### Booleans

**What they are**: Boolean values represent one of two states: True or False.

**How they work**: Booleans are used in logical operations and control flow. They are a subclass of integers where True is 1 and False is 0.

**Examples**:

```python
# Boolean values
is_valid = True
is_complete = False

# Boolean operations
and_result = True and False  # False
or_result = True or False    # True
not_result = not True        # False

# Comparison operators return booleans
equals = (5 == 5)            # True
not_equals = (5 != 10)       # True
greater_than = (10 > 5)      # True
less_than = (5 < 10)         # True
greater_equal = (10 >= 10)   # True
less_equal = (5 <= 10)       # True

# Truthy and falsy values
if 0:       # 0 is falsy
    print("This won't print")
if "hello": # Non-empty strings are truthy
    print("This will print")
```

### None

**What it is**: None is a special constant representing the absence of a value or a null value.

**How it works**: None is often used to represent the absence of a value, an empty return type, or to initialize variables that will later be assigned a more specific value.

**Examples**:

```python
# Initializing with None
result = None

# Checking for None (use identity operator 'is')
if result is None:
    print("No result yet")

# Functions with no return statement return None
def do_something():
    pass  # This function returns None

print(do_something())  # Outputs: None
```

## Collections and Data Structures

### Lists

**What they are**: Lists are ordered, changeable, and allow duplicate values.

**How they work**: Lists are mutable sequences, implemented as dynamic arrays that can hold items of different types.

**Examples**:

```python
# Creating lists
fruits = ["apple", "banana", "cherry"]
mixed = [1, "hello", True, 3.14]

# Accessing elements
first_fruit = fruits[0]  # "apple"
last_fruit = fruits[-1]  # "cherry"

# Modifying lists
fruits.append("orange")  # ["apple", "banana", "cherry", "orange"]
fruits.insert(1, "pear")  # ["apple", "pear", "banana", "cherry", "orange"]
fruits.remove("banana")  # ["apple", "pear", "cherry", "orange"]
popped = fruits.pop()    # "orange", fruits is now ["apple", "pear", "cherry"]

# Slicing
first_two = fruits[0:2]  # ["apple", "pear"]

# List comprehensions
squares = [x**2 for x in range(5)]  # [0, 1, 4, 9, 16]
even_numbers = [x for x in range(10) if x % 2 == 0]  # [0, 2, 4, 6, 8]

# Sorting
fruits.sort()  # Sorts in-place
sorted_copy = sorted(fruits)  # Returns a new sorted list
```

### Tuples

**What they are**: Tuples are ordered, unchangeable, and allow duplicate values.

**How they work**: Tuples are immutable sequences, similar to lists but cannot be modified after creation.

**Examples**:

```python
# Creating tuples
coordinates = (10, 20)
person = ("John", 25, "Developer")

# Accessing elements
x_coord = coordinates[0]  # 10
job = person[2]          # "Developer"

# Tuple packing and unpacking
a, b = coordinates       # a = 10, b = 20
name, age, occupation = person  # name = "John", age = 25, occupation = "Developer"

# Single-item tuple (note the comma)
single_item = (42,)

# Tuples are immutable
# This will raise an error: coordinates[0] = 15

# Tuples for swapping values
a, b = 10, 20
a, b = b, a  # a = 20, b = 10
```

### Sets

**What they are**: Sets are unordered, unchangeable (though you can add and remove items), and do not allow duplicate values.

**How they work**: Sets are implemented as hash tables without values, which makes them very efficient for membership testing and eliminating duplicates.

**Examples**:

```python
# Creating sets
fruits = {"apple", "banana", "cherry"}
numbers = {1, 2, 3, 4, 5}

# Cannot have duplicates
duplicate_set = {1, 1, 2, 2, 3}  # {1, 2, 3}

# Adding and removing items
fruits.add("orange")      # {"apple", "banana", "cherry", "orange"}
fruits.remove("banana")   # {"apple", "cherry", "orange"}
# If not sure if item exists, use discard
fruits.discard("pear")    # No error if "pear" doesn't exist

# Set operations
set1 = {1, 2, 3}
set2 = {3, 4, 5}
union_set = set1.union(set2)               # {1, 2, 3, 4, 5}
intersection_set = set1.intersection(set2)  # {3}
difference_set = set1.difference(set2)      # {1, 2}
symmetric_difference = set1.symmetric_difference(set2)  # {1, 2, 4, 5}

# Testing for membership
if "apple" in fruits:
    print("Apple is in the set")
```

### Dictionaries

**What they are**: Dictionaries are ordered (since Python 3.7), changeable, and do not allow duplicate keys.

**How they work**: Dictionaries are implemented as hash tables that map keys to values, providing fast lookup, insertion, and deletion.

**Examples**:

```python
# Creating dictionaries
person = {
    "name": "John",
    "age": 30,
    "job": "Developer"
}

# Accessing values
name = person["name"]  # "John"
# Safe access with get()
age = person.get("age", 0)  # 30 (returns 0 if key doesn't exist)

# Modifying dictionaries
person["email"] = "john@example.com"  # Add new key-value pair
person["age"] = 31                   # Update existing value
del person["job"]                    # Remove a key-value pair

# Dictionary methods
keys = person.keys()      # dict_keys(['name', 'age', 'email'])
values = person.values()  # dict_values(['John', 31, 'john@example.com'])
items = person.items()    # dict_items([('name', 'John'), ('age', 31), ('email', 'john@example.com')])

# Dictionary comprehensions
squares = {x: x**2 for x in range(5)}  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

# Merging dictionaries (Python 3.9+)
dict1 = {"a": 1, "b": 2}
dict2 = {"b": 3, "c": 4}
merged = dict1 | dict2  # {"a": 1, "b": 3, "c": 4}
```

### Frozen Set

**What it is**: A frozen set is an immutable version of a set.

**How it works**: Once created, you cannot add, remove, or change elements in a frozen set, making it hashable and usable as dictionary keys or elements of another set.

**Examples**:

```python
# Creating a frozen set
immutable_set = frozenset([1, 2, 3, 4])

# Attempting to modify it will raise an error
# This will fail: immutable_set.add(5)

# Using a frozen set as a dictionary key
feature_flags = {
    frozenset(["admin", "editor"]): True,
    frozenset(["user"]): False
}

# Frozen sets support the same operations as regular sets
set1 = frozenset([1, 2, 3])
set2 = frozenset([3, 4, 5])
union = set1.union(set2)  # frozenset({1, 2, 3, 4, 5})
```

### Deque

**What it is**: A deque (double-ended queue) is a generalization of a stack and a queue that supports efficient adding and removing elements from either end.

**How it works**: It's implemented in the collections module and is optimized for fast appends and pops from both ends.

**Examples**:

```python
from collections import deque

# Creating a deque
queue = deque(['a', 'b', 'c'])

# Adding elements
queue.append('d')        # deque(['a', 'b', 'c', 'd'])
queue.appendleft('z')    # deque(['z', 'a', 'b', 'c', 'd'])

# Removing elements
last = queue.pop()       # 'd', queue is now deque(['z', 'a', 'b', 'c'])
first = queue.popleft()  # 'z', queue is now deque(['a', 'b', 'c'])

# Rotating elements
queue.rotate(1)   # Rotate one step to the right: deque(['c', 'a', 'b'])
queue.rotate(-1)  # Rotate one step to the left: deque(['a', 'b', 'c'])

# Fixed-length deque
limited_queue = deque(maxlen=3)
for i in range(5):
    limited_queue.append(i)  # Final: deque([2, 3, 4], maxlen=3)
```

### DefaultDict

**What it is**: A defaultdict is a dictionary subclass that calls a factory function to supply missing values.

**How it works**: When a key that doesn't exist is accessed, instead of raising a KeyError, it calls the factory function to provide a default value and adds that key-value pair to the dictionary.

**Examples**:

```python
from collections import defaultdict

# Dictionary that defaults to an integer (0)
counts = defaultdict(int)
for word in ["apple", "banana", "apple", "cherry"]:
    counts[word] += 1  # No need to check if key exists
print(counts)  # defaultdict(<class 'int'>, {'apple': 2, 'banana': 1, 'cherry': 1})

# Dictionary with list as default
groups = defaultdict(list)
for name, group in [("Alice", "Admin"), ("Bob", "User"), ("Charlie", "Admin")]:
    groups[group].append(name)
print(groups)  # defaultdict(<class 'list'>, {'Admin': ['Alice', 'Charlie'], 'User': ['Bob']})

# Creating custom defaults
def default_factory():
    return "Not found"
d = defaultdict(default_factory)
d["key"] = "exists"
print(d["key"])      # "exists"
print(d["missing"])  # "Not found"
```

### Counter

**What it is**: A Counter is a dictionary subclass for counting hashable objects.

**How it works**: It's a collection where elements are stored as dictionary keys and their counts are stored as dictionary values.

**Examples**:

```python
from collections import Counter

# Count occurrences of elements
c = Counter(["apple", "banana", "apple", "cherry", "apple"])
print(c)  # Counter({'apple': 3, 'banana': 1, 'cherry': 1})

# Count characters in a string
char_count = Counter("hello world")
print(char_count)  # Counter({'l': 3, 'o': 2, ' ': 1, 'h': 1, 'e': 1, 'w': 1, 'r': 1, 'd': 1})

# Counter methods
print(c.most_common(2))  # [('apple', 3), ('banana', 1)]
print(list(c.elements()))  # ['apple', 'apple', 'apple', 'banana', 'cherry']

# Mathematical operations
c1 = Counter(a=3, b=1)
c2 = Counter(a=1, b=2)
print(c1 + c2)  # Counter({'a': 4, 'b': 3})
print(c1 - c2)  # Counter({'a': 2})
```

### Named Tuple

**What it is**: A named tuple is a factory function for creating tuple subclasses with named fields.

**How it works**: It creates an easy-to-create, lightweight object type, similar to a struct. Each instance of a class created with namedtuple() is a tuple, immutable, and identical in size to a tuple.

**Examples**:

```python
from collections import namedtuple

# Define a named tuple type
Person = namedtuple('Person', ['name', 'age', 'job'])

# Create an instance
john = Person('John', 30, 'Developer')

# Access fields by name or index
print(john.name)  # 'John'
print(john[0])    # 'John'

# Unpacking works as with regular tuples
name, age, job = john

# Named tuples are immutable
# This will raise an error: john.age = 31

# Convert to dictionary
john_dict = john._asdict()  # {'name': 'John', 'age': 30, 'job': 'Developer'}

# Create a new instance with one field replaced
john_promoted = john._replace(job='Senior Developer')
```

## Variables and Scope

### Variable Assignment

**What it is**: Variable assignment is the process of binding a name to an object in Python.

**How it works**: When you assign a value to a variable, Python creates an object for that value and makes the variable name point to it.

**Examples**:

```python
# Simple assignment
x = 10

# Multiple assignment
a, b = 1, 2

# Swapping values
a, b = b, a

# Augmented assignment
count = 0
count += 1  # Equivalent to: count = count + 1

# Chained assignment
x = y = z = 0  # All three variables refer to the same object

# Unpacking sequences
person = ("John", 30, "Developer")
name, age, job = person
```

### Variable Naming Rules

**What they are**: Rules and conventions for naming variables in Python.

**How they work**: Python has specific rules for valid identifiers, and the PEP 8 style guide provides conventions for naming.

**Examples**:

```python
# Valid variable names
name = "John"
age_in_years = 30
_private_var = "hidden"
camelCase = "not recommended but valid"
snake_case = "recommended"
CONSTANT_VALUE = 3.14159

# Invalid variable names
# 123abc = "can't start with a number"
# my-var = "hyphens are not allowed"
# class = "can't use Python keywords"

# Convention examples
# Class names use CamelCase
class Person:
    pass

# Function and variable names use snake_case
def calculate_total(item_price, tax_rate):
    total_cost = item_price * (1 + tax_rate)
    return total_cost

# Constants use ALL_CAPS
PI = 3.14159
MAX_CONNECTIONS = 100
```

### Local, Global, and Nonlocal Variables

**What they are**: Different variable scopes in Python.

**How they work**:

- Local variables are defined inside a function and can only be used inside that function.
- Global variables are defined at the module level and can be accessed throughout the module.
- Nonlocal variables are used in nested functions to refer to variables from the enclosing scope.

**Examples**:

```python
# Global variable
counter = 0

def update_counter():
    # Access global variable
    global counter
    counter += 1

def outer_function():
    # Variable in the enclosing scope
    x = "outer"
    
    def inner_function():
        # Access variable from outer scope
        nonlocal x
        x = "modified"
        
        # Local variable
        y = "local to inner"
        print(f"Inside inner: x = {x}, y = {y}")
    
    inner_function()
    print(f"After inner call: x = {x}")
    # This would raise an error: print(y)  # y is not defined here

# Demo
update_counter()
print(counter)  # 1

outer_function()
# Output:
# Inside inner: x = modified, y = local to inner
# After inner call: x = modified
```

### Private Variables

**What they are**: Python variables that are intended to be private to a class.

**How they work**: Python doesn't have true private variables, but it uses name mangling for variables prefixed with double underscores (__) and doesn't mangle names with a single underscore (_).

**Examples**:

```python
class Person:
    def __init__(self, name, age):
        self.name = name       # Public attribute
        self._age = age        # Convention for "private" (not enforced)
        self.__ssn = None      # Name mangled to _Person__ssn
    
    def set_ssn(self, ssn):
        # Validate SSN format
        if isinstance(ssn, str) and len(ssn) == 11:
            self.__ssn = ssn
    
    def get_details(self):
        return f"Name: {self.name}, Age: {self._age}"
    
# Usage
person = Person("John", 30)
print(person.name)        # "John" - public is accessible
print(person._age)        # 30 - "private" by convention but still accessible
# This would raise an AttributeError: print(person.__ssn)
# But this works (name mangling): print(person._Person__ssn)
```

## Control Flow

### If-Else Statements

**What they are**: Conditional statements that allow different code execution paths based on conditions.

**How they work**: The `if` statement tests a condition, and if it evaluates to True, the indented code block is executed. The `else` and `elif` (else if) clauses provide alternative execution paths.

**Examples**:

```python
# Simple if
age = 20
if age >= 18:
    print("You are an adult")

# If-else
if age >= 18:
    print("You are an adult")
else:
    print("You are a minor")

# If-elif-else chain
score = 85
if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
elif score >= 60:
    grade = "D"
else:
    grade = "F"
print(f"Grade: {grade}")  # Grade: B

# Conditional expressions (ternary operator)
status = "adult" if age >= 18 else "minor"

# Checking for empty sequences or collections
data = []
if not data:
    print("Data is empty")
```

### For Loops

**What they are**: For loops are used to iterate over a sequence (like a list, tuple, dictionary, set, or string) and execute code for each element.

**How they work**: The loop assigns each item in the sequence to the loop variable and executes the indented code block.

**Examples**:

```python
# Iterating over a list
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)

# Iterating over a string
for char in "Python":
    print(char)

# Iterating with index using enumerate
for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")

# Iterating over dictionary
person = {"name": "John", "age": 30, "job": "Developer"}
for key in person:
    print(f"{key}: {person[key]}")

# Iterating over key-value pairs
for key, value in person.items():
    print(f"{key}: {value}")

# Using range
for i in range(5):  # 0, 1, 2, 3, 4
    print(i)

for i in range(1, 6, 2):  # 1, 3, 5
    print(i)

# Break statement
for i in range(10):
    if i == 5:
        break
    print(i)  # 0, 1, 2, 3, 4

# Continue statement
for i in range(10):
    if i % 2 == 0:
        continue
    print(i)  # 1, 3, 5, 7, 9

# Else clause (executes when loop completes without break)
for i in range(5):
    print(i)
else:
    print("Loop completed normally")
```

### While Loops

**What they are**: While loops execute a block of code as long as a condition is true.

**How they work**: The condition is checked before each iteration. If it's true, the code block executes; if it's false, the loop terminates.

**Examples**:

```python
# Simple while loop
count = 0
while count < 5:
    print(count)
    count += 1  # Don't forget to update the condition!

# Break statement
count = 0
while True:  # Infinite loop
    print(count)
    count += 1
    if count >= 5:
        break

# Continue statement
count = 0
while count < 10:
    count += 1
    if count % 2 == 0:
        continue
    print(count)  # 1, 3, 5, 7, 9

# Else clause (executes when loop condition becomes false)
count = 0
while count < 5:
    print(count)
    count += 1
else:
    print("Loop condition is now false")

# Using while for input validation
# while True:
#     user_input = input("Enter a positive number: ")
#     if user_input.isdigit() and int(user_input) > 0:
#         break
#     print("Invalid input, please try again.")
```

### Break, Continue, and Pass Statements

**What they are**: Control flow statements for loops.

**How they work**:

- `break` exits the loop entirely.
- `continue` skips the current iteration and moves to the next one.
- `pass` does nothing and is used as a placeholder.

**Examples**:

```python
# Break example
for i in range(10):
    if i == 5:
        print("Breaking loop")
        break
    print(i)

# Continue example
for i in range(10):
    if i % 2 == 0:
        continue  # Skip even numbers
    print(i)  # 1, 3, 5, 7, 9

# Pass example
for i in range(5):
    if i == 2:
        # We'll handle this case later
        pass
    else:
        print(i)

# Pass as a placeholder in functions and classes
def function_not_implemented_yet():
    pass

class EmptyClass:
    pass
```

## Functions

### Function Definition and Calling

**What they are**: Functions are reusable blocks of code that perform a specific task.

**How they work**: Functions are defined using the `def` keyword, can accept parameters, and can return values.

**Examples**:

```python
# Simple function definition
def greet():
    print("Hello, World!")

# Calling the function
greet()  # Outputs: Hello, World!

# Function with parameters
def greet_person(name):
    print(f"Hello, {name}!")

greet_person("Alice")  # Outputs: Hello, Alice!

# Function with return value
def add(a, b):
    return a + b

result = add(3, 5)  # result = 8

# Function with default parameter values
def greet_with_message(name, message="Hello"):
    print(f"{message}, {name}!")

greet_with_message("Bob")           # Outputs: Hello, Bob!
greet_with_message("Bob", "Hi there")  # Outputs: Hi there, Bob!

# Function with multiple return values (actually returns a tuple)
def get_dimensions():
    return 1920, 1080

width, height = get_dimensions()  # width = 1920, height = 1080
```

### Function Parameters and Arguments

**What they are**: Parameters are defined in the function signature, while arguments are the values passed to the function when it's called.

**How they work**: Python supports several types of parameters and ways to pass arguments.

**Examples**:

```python
# Positional arguments (order matters)
def describe_pet(animal_type, pet_name):
    print(f"I have a {animal_type} named {pet_name}.")

describe_pet("hamster", "Harry")  # I have a hamster named Harry.

# Keyword arguments (order doesn't matter)
describe_pet(pet_name="Harry", animal_type="hamster")  # Same output

# Default parameter values
def describe_pet(pet_name, animal_type="dog"):
    print(f"I have a {animal_type} named {pet_name}.")

describe_pet("Willie")  # I have a dog named Willie.

# Variable number of positional arguments (*args)
def sum_all(*numbers):
    return sum(numbers)

print(sum_all(1, 2, 3, 4))  # 10

# Variable number of keyword arguments (**kwargs)
def build_profile(first, last, **user_info):
    profile = {"first_name": first, "last_name": last}
    profile.update(user_info)
    return profile

user = build_profile("Albert", "Einstein",
                    location="Princeton",
                    field="Physics")
# user = {'first_name': 'Albert', 'last_name': 'Einstein', 'location': 'Princeton', 'field': 'Physics'}

# Positional-only and keyword-only parameters (Python 3.8+)
def f(pos_only, /, pos_or_kwd, *, kwd_only):
    print(pos_only, pos_or_kwd, kwd_only)

f(1, 2, kwd_only=3)  # Valid
# f(pos_only=1, 2, kwd_only=3)  # Error: pos_only cannot be a keyword argument
# f(1, pos_or_kwd=2, 3)  # Error: kwd_only must be a keyword argument
```

### Return Statement

**What it is**: The `return` statement exits a function and optionally returns a value.

**How it works**: When encountered, the function immediately stops execution and returns control to the calling code, optionally providing a result.

**Examples**:

```python
# Function that returns a value
def square(number):
    return number ** 2

result = square(4)  # result = 16

# Multiple return values (as a tuple)
def get_min_max(numbers):
    return min(numbers), max(numbers)

min_val, max_val = get_min_max([1, 2, 3, 4, 5])  # min_val = 1, max_val = 5

# Early return for error cases
def divide(a, b):
    if b == 0:
        return "Error: Division by zero"
    return a / b

# Function with conditional returns
def get_grade(score):
    if score >= 90:
        return "A"
    elif score >= 80:
        return "B"
    elif score >= 70:
        return "C"
    else:
        return "F"

# Function with no return (implicitly returns None)
def greet(name):
    print(f"Hello, {name}!")

result = greet("Alice")  # result = None
```

### Lambda Functions

**What they are**: Lambda functions (or anonymous functions) are small, one-line functions without a name.

**How they work**: They are defined using the `lambda` keyword and can take any number of arguments but can only have one expression.

**Examples**:

```python
# Simple lambda function
square = lambda x: x**2
print(square(5))  # 25

# Lambda with multiple arguments
add = lambda x
```