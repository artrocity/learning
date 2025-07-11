---
aliases:
  - "Part 3: Python Comprehensive Guide"
---
# Class Decorators (continued)

**Examples (continued)**:

```python
# Singleton pattern using class decorator
def singleton(cls):
    instances = {}
    def get_instance(*args, **kwargs):
        if cls not in instances:
            instances[cls] = cls(*args, **kwargs)
        return instances[cls]
    return get_instance

@singleton
class Database:
    def __init__(self, url):
        self.url = url
        print(f"Connecting to database at {url}")

# Both variables reference the same instance
db1 = Database("localhost:5432")  # Prints: Connecting to database at localhost:5432
db2 = Database("localhost:5432")  # No output - reusing existing instance
print(db1 is db2)  # True

# Decorator that registers classes
registry = []

def register(cls):
    registry.append(cls)
    return cls

@register
class MyClass:
    pass

@register
class AnotherClass:
    pass

print(registry)  # [<class '__main__.MyClass'>, <class '__main__.AnotherClass'>]
```

### Decorator with functools.wraps

**What it is**: `functools.wraps` is a decorator that preserves the metadata of the original function when creating a decorator.

**How it works**: When you create a decorator, the wrapped function loses its original metadata (like name, docstring, and argument list). `functools.wraps` preserves this metadata.

**Examples**:

```python
import functools

# Decorator without wraps
def simple_decorator(func):
    def wrapper(*args, **kwargs):
        """Wrapper function"""
        print("Before function call")
        result = func(*args, **kwargs)
        print("After function call")
        return result
    return wrapper

@simple_decorator
def greet(name):
    """Greets a person by name."""
    return f"Hello, {name}!"

print(greet.__name__)  # "wrapper"
print(greet.__doc__)   # "Wrapper function"

# Decorator with wraps
def better_decorator(func):
    @functools.wraps(func)  # Preserves metadata
    def wrapper(*args, **kwargs):
        """Wrapper function"""
        print("Before function call")
        result = func(*args, **kwargs)
        print("After function call")
        return result
    return wrapper

@better_decorator
def greet_better(name):
    """Greets a person by name."""
    return f"Hello, {name}!"

print(greet_better.__name__)  # "greet_better"
print(greet_better.__doc__)   # "Greets a person by name."

# Practical decorator with wraps
def timer(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        import time
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        print(f"{func.__name__} ran in {end_time - start_time:.6f} seconds")
        return result
    return wrapper

@timer
def slow_function():
    """A slow function for testing."""
    import time
    time.sleep(1)
    return "Done!"

slow_function()  # slow_function ran in 1.001234 seconds
print(slow_function.__name__)  # "slow_function"
print(slow_function.__doc__)   # "A slow function for testing."
```

## Context Managers

### With Statement

**What it is**: The `with` statement is used for resource management, making it easier to handle setup and teardown operations.

**How it works**: It ensures that cleanup code is executed even if an exception is raised in the code block, similar to try-finally but more concise.

**Examples**:

```python
# Using 'with' for file operations
with open("example.txt", "w") as file:
    file.write("Hello, World!")
# File is automatically closed when the block exits

# Multiple context managers
with open("input.txt", "r") as infile, open("output.txt", "w") as outfile:
    content = infile.read()
    outfile.write(content.upper())

# Other built-in context managers
import threading
with threading.Lock():
    # Code in this block has exclusive access
    pass

# Context manager for changing directory
import os
from contextlib import contextmanager

@contextmanager
def working_directory(path):
    """Change the working directory to the given path and restore it when done."""
    current_dir = os.getcwd()
    try:
        os.chdir(path)
        yield
    finally:
        os.chdir(current_dir)

with working_directory("/tmp"):
    # Code here runs with /tmp as the current directory
    pass
# Working directory is restored
```

### Creating Context Managers

**What it is**: You can create your own context managers to handle resource management for custom operations.

**How it works**: There are two ways to create context managers: by defining a class with `__enter__` and `__exit__` methods, or by using the `contextlib.contextmanager` decorator.

**Examples**:

```python
# Class-based context manager
class FileManager:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode
        self.file = None
    
    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        if self.file:
            self.file.close()
        # Return True to suppress exceptions, False (or None) to propagate them
        return False

# Using the class-based context manager
with FileManager("example.txt", "w") as file:
    file.write("Hello, World!")

# Generator-based context manager using contextlib
from contextlib import contextmanager

@contextmanager
def file_manager(filename, mode):
    try:
        file = open(filename, mode)
        yield file
    finally:
        file.close()

# Using the generator-based context manager
with file_manager("example.txt", "w") as file:
    file.write("Hello, World!")

# Timing context manager
import time

@contextmanager
def timer():
    start_time = time.time()
    try:
        yield
    finally:
        end_time = time.time()
        print(f"Execution took {end_time - start_time:.6f} seconds")

# Using the timing context manager
with timer():
    # Some time-consuming operations
    time.sleep(1)  # Prints: Execution took 1.001234 seconds

# Context manager for handling temporary state changes
@contextmanager
def temporary_attribute(obj, attr, value):
    original = getattr(obj, attr)
    setattr(obj, attr, value)
    try:
        yield
    finally:
        setattr(obj, attr, original)

class Person:
    def __init__(self, name):
        self.name = name

person = Person("Alice")
print(person.name)  # Alice
with temporary_attribute(person, "name", "Temporary"):
    print(person.name)  # Temporary
print(person.name)  # Alice

# Nested context managers
@contextmanager
def indent(level=1):
    old_indent = globals().get('_indent', 0)
    globals()['_indent'] = old_indent + level
    try:
        yield
    finally:
        globals()['_indent'] = old_indent

def print_indented(text):
    print(' ' * (globals().get('_indent', 0) * 4) + text)

print_indented("Top level")
with indent():
    print_indented("First level")
    with indent():
        print_indented("Second level")
    print_indented("Back to first level")
print_indented("Back to top level")
```

## Regular Expressions

### Basic Patterns

**What they are**: Regular expressions (regex) are sequences of characters that define a search pattern, mainly for string matching.

**How they work**: Python's `re` module provides functions for working with regular expressions. Basic patterns include literals (characters that match themselves) and metacharacters (characters with special meanings).

**Examples**:

```python
import re

# Simple pattern matching
text = "The quick brown fox jumps over the lazy dog."
match = re.search("fox", text)
print(match.group())  # fox
print(match.start())  # 16
print(match.end())    # 19

# Checking if a pattern exists
if re.search("cat", text):
    print("Found a cat!")
else:
    print("No cats found.")  # No cats found.

# Finding all occurrences
text = "The fox and the fox jumped over the foxes."
matches = re.findall("fox", text)
print(matches)  # ['fox', 'fox', 'fox']

# Character classes
# [abc] matches any one of the characters a, b, or c
text = "The quick brown fox jumps over the lazy dog."
vowels = re.findall("[aeiou]", text)
print(vowels)  # ['e', 'u', 'i', 'o', 'o', 'u', 'o', 'e', 'e', 'a', 'o']

# Negated character classes
# [^abc] matches any character except a, b, or c
non_vowels = re.findall("[^aeiou ]", text)
print(non_vowels)  # ['T', 'h', 'q', 'c', 'k', 'b', 'r', 'w', 'n', 'f', 'x', 'j', 'm', 'p', 's', 'v', 'r', 't', 'h', 'l', 'z', 'y', 'd', 'g', '.']

# Character ranges
# [a-z] matches any lowercase letter
lowercase = re.findall("[a-z]", text)
print(len(lowercase))  # 35

# Metacharacters
# . (dot) matches any character except a newline
dots = re.findall(".", "abc123")
print(dots)  # ['a', 'b', 'c', '1', '2', '3']

# Escape metacharacters with backslash
# \. matches a literal dot
dots = re.findall(r"\.", "www.example.com")
print(dots)  # ['.', '.']

# \d matches any digit
digits = re.findall(r"\d", "abc123")
print(digits)  # ['1', '2', '3']

# \D matches any non-digit
non_digits = re.findall(r"\D", "abc123")
print(non_digits)  # ['a', 'b', 'c']

# \w matches any word character (alphanumeric + underscore)
word_chars = re.findall(r"\w", "hello_world123!")
print(word_chars)  # ['h', 'e', 'l', 'l', 'o', '_', 'w', 'o', 'r', 'l', 'd', '1', '2', '3']

# \W matches any non-word character
non_word_chars = re.findall(r"\W", "hello_world123!")
print(non_word_chars)  # ['!']

# \s matches any whitespace character
whitespace = re.findall(r"\s", "hello world\t\n")
print(len(whitespace))  # 3

# \S matches any non-whitespace character
non_whitespace = re.findall(r"\S", "hello world\t\n")
print(len(non_whitespace))  # 10
```

### Quantifiers and Anchors

**What they are**: Quantifiers specify how many instances of a character, group, or character class must be present. Anchors specify the position of the matches in the text.

**How they work**: Quantifiers follow the character or group they modify. Anchors don't match characters but match positions in the text.

**Examples**:

```python
import re

# Quantifiers
# * (zero or more)
matches = re.findall("ab*c", "ac abc abbc")
print(matches)  # ['ac', 'abc', 'abbc']

# + (one or more)
matches = re.findall("ab+c", "ac abc abbc")
print(matches)  # ['abc', 'abbc']

# ? (zero or one)
matches = re.findall("ab?c", "ac abc abbc")
print(matches)  # ['ac', 'abc']

# {n} (exactly n times)
matches = re.findall("ab{2}c", "ac abc abbc abbbc")
print(matches)  # ['abbc']

# {n,} (at least n times)
matches = re.findall("ab{2,}c", "ac abc abbc abbbc")
print(matches)  # ['abbc', 'abbbc']

# {n,m} (between n and m times)
matches = re.findall("ab{1,2}c", "ac abc abbc abbbc")
print(matches)  # ['abc', 'abbc']

# Greedy vs non-greedy (lazy) quantifiers
# Greedy (default) - match as much as possible
greedy = re.findall("<.*>", "<p>Paragraph</p>")
print(greedy)  # ['<p>Paragraph</p>']

# Non-greedy (lazy) - match as little as possible
lazy = re.findall("<.*?>", "<p>Paragraph</p>")
print(lazy)  # ['<p>', '</p>']

# Anchors
# ^ (start of string or line)
starts_with_the = re.findall(r"^The", "The quick brown fox\nThe lazy dog")
print(starts_with_the)  # ['The']
# With MULTILINE flag
starts_with_the = re.findall(r"^The", "The quick brown fox\nThe lazy dog", re.MULTILINE)
print(starts_with_the)  # ['The', 'The']

# $ (end of string or line)
ends_with_fox = re.findall(r"fox$", "The quick brown fox\nThe lazy dog")
print(ends_with_fox)  # []
# With MULTILINE flag
ends_with_fox = re.findall(r"fox$", "The quick brown fox\nThe lazy dog", re.MULTILINE)
print(ends_with_fox)  # ['fox']

# \b (word boundary)
word_dog = re.findall(r"\bdog\b", "dog doggy doghouse")
print(word_dog)  # ['dog']

# \B (non-word boundary)
non_word_dog = re.findall(r"\Bdog\B", "hotdogs")
print(non_word_dog)  # []
```

### Groups and Capturing

**What they are**: Groups allow you to treat multiple characters as a single unit, and capturing groups remember the matched text for later use.

**How they work**: Parentheses `()` create capturing groups. You can reference these groups in replacement patterns or extract them from match objects.

**Examples**:

```python
import re

# Basic grouping
match = re.search(r"(ab)+", "ababab")
print(match.group())  # ababab
print(match.group(0))  # ababab (same as group())
print(match.group(1))  # ab (the captured group)

# Multiple groups
match = re.search(r"(\d+)-(\d+)", "Order: 123-456")
print(match.group())   # 123-456
print(match.group(1))  # 123
print(match.group(2))  # 456
print(match.groups())  # ('123', '456')

# Named groups
match = re.search(r"(?P<year>\d{4})-(?P<month>\d{2})-(?P<day>\d{2})", "Date: 2023-05-15")
print(match.group("year"))   # 2023
print(match.group("month"))  # 05
print(match.group("day"))    # 15
print(match.groupdict())     # {'year': '2023', 'month': '05', 'day': '15'}

# Non-capturing groups (?:...)
match = re.search(r"(\d+)(?:-(\d+))?", "Order: 123")
print(match.groups())  # ('123', None)
match = re.search(r"(\d+)(?:-(\d+))?", "Order: 123-456")
print(match.groups())  # ('123', '456')

# Backreferences in pattern
# \1 refers to the first capturing group
duplicated_word = re.search(r"\b(\w+)\s+\1\b", "The the cat")
print(duplicated_word.group())  # The the
print(duplicated_word.group(1))  # The

# Using groups in replacement
text = "John Smith"
swapped = re.sub(r"(\w+)\s+(\w+)", r"\2, \1", text)
print(swapped)  # Smith, John

# Named backreferences in replacement
date = "2023-05-15"
formatted = re.sub(r"(?P<year>\d{4})-(?P<month>\d{2})-(?P<day>\d{2})", r"\g<month>/\g<day>/\g<year>", date)
print(formatted)  # 05/15/2023
```

### Regex Functions

**What they are**: The `re` module in Python provides functions for working with regular expressions.

**How they work**: Functions like `search()`, `match()`, `findall()`, `finditer()`, `sub()`, and `split()` perform different operations using regular expressions.

**Examples**:

```python
import re

text = "The quick brown fox jumps over the lazy dog."

# re.search() - Find the first match
match = re.search(r"(\w+) fox", text)
if match:
    print(match.group())  # brown fox
    print(match.group(1))  # brown

# re.match() - Match at the beginning of the string only
match = re.match(r"The", text)
print(match.group())  # The
match = re.match(r"quick", text)
print(match)  # None - not at the beginning

# re.fullmatch() - Match the entire string
match = re.fullmatch(r"The quick brown fox jumps over the lazy dog\.", text)
print(match.group())  # The quick brown fox jumps over the lazy dog.

# re.findall() - Find all non-overlapping matches
matches = re.findall(r"\b\w{4}\b", text)
print(matches)  # ['quick', 'over', 'lazy']

# re.finditer() - Return an iterator over matches
for match in re.finditer(r"\b\w{4}\b", text):
    print(f"Match: {match.group()} at position {match.start()}-{match.end()}")

# re.sub() - Substitute matches with replacement text
replaced = re.sub(r"fox", "cat", text)
print(replaced)  # The quick brown cat jumps over the lazy dog.

# re.sub() with a function
def capitalize(match):
    return match.group().upper()

replaced = re.sub(r"\b\w{4}\b", capitalize, text)
print(replaced)  # The QUICK brown fox jumps OVER the LAZY dog.

# re.split() - Split string by pattern
parts = re.split(r"\s+", "Hello  world   Python")
print(parts)  # ['Hello', 'world', 'Python']

# re.split() with capturing groups
parts = re.split(r"(\s+)", "Hello  world   Python")
print(parts)  # ['Hello', '  ', 'world', '   ', 'Python']

# Compile a regex pattern for repeated use
pattern = re.compile(r"\b\w{4}\b")
matches = pattern.findall(text)
print(matches)  # ['quick', 'over', 'lazy']

# Using flags
# re.IGNORECASE or re.I - Case-insensitive matching
matches = re.findall(r"the", text, re.IGNORECASE)
print(matches)  # ['The', 'the']

# re.MULTILINE or re.M - ^ and $ match at line boundaries
multiline_text = "First line\nSecond line"
matches = re.findall(r"^.*$", multiline_text, re.MULTILINE)
print(matches)  # ['First line', 'Second line']

# re.DOTALL or re.S - Dot matches newline
dotall_matches = re.findall(r"First.*Second", multiline_text, re.DOTALL)
print(dotall_matches)  # ['First line\nSecond']

# re.VERBOSE or re.X - Allow verbose regex with comments
pattern = re.compile(r"""
    \b      # Word boundary
    \w{4}   # Exactly 4 word characters
    \b      # Word boundary
""", re.VERBOSE)
matches = pattern.findall(text)
print(matches)  # ['quick', 'over', 'lazy']
```

## Working with Data

### JSON Handling

**What it is**: JSON (JavaScript Object Notation) is a lightweight data interchange format that is easy for humans to read and write, and easy for machines to parse and generate.

**How it works**: Python's `json` module provides functions for encoding and decoding JSON data.

**Examples**:

```python
import json

# Converting Python objects to JSON strings
# Python dict to JSON string
person = {
    "name": "John",
    "age": 30,
    "city": "New York",
    "languages": ["Python", "JavaScript", "C++"],
    "is_employed": True,
    "spouse": None
}
json_string = json.dumps(person)
print(json_string)
# {"name": "John", "age": 30, "city": "New York", "languages": ["Python", "JavaScript", "C++"], "is_employed": true, "spouse": null}

# Pretty-printing JSON
pretty_json = json.dumps(person, indent=4, sort_keys=True)
print(pretty_json)
# {
#     "age": 30,
#     "city": "New York",
#     "is_employed": true,
#     "languages": [
#         "Python",
#         "JavaScript",
#         "C++"
#     ],
#     "name": "John",
#     "spouse": null
# }

# Converting JSON strings to Python objects
# JSON string to Python dict
json_data = '{"name": "Alice", "age": 25, "city": "London"}'
python_obj = json.loads(json_data)
print(python_obj["name"])  # Alice
print(python_obj["age"])   # 25

# Reading JSON from a file
with open("data.json", "w") as f:
    json.dump(person, f, indent=4)

with open("data.json", "r") as f:
    loaded_data = json.load(f)
    print(loaded_data["city"])  # New York

# Handling custom objects
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

# Custom encoder
def encode_person(obj):
    if isinstance(obj, Person):
        return {"name": obj.name, "age": obj.age, "__type__": "Person"}
    raise TypeError(f"Object of type {type(obj)} is not JSON serializable")

person = Person("John", 30)
json_string = json.dumps(person, default=encode_person)
print(json_string)  # {"name": "John", "age": 30, "__type__": "Person"}

# Custom decoder
def decode_person(obj):
    if "__type__" in obj and obj["__type__"] == "Person":
        return Person(obj["name"], obj["age"])
    return obj

json_data = '{"name": "Alice", "age": 25, "__type__": "Person"}'
person = json.loads(json_data, object_hook=decode_person)
print(type(person))  # <class '__main__.Person'>
print(person.name)   # Alice
```

### CSV Handling

**What it is**: CSV (Comma-Separated Values) is a simple file format used to store tabular data.

**How it works**: Python's `csv` module provides functionality for reading from and writing to CSV files.

**Examples**:

```python
import csv

# Writing to a CSV file
data = [
    ["Name", "Age", "City"],
    ["John", 30, "New York"],
    ["Alice", 25, "London"],
    ["Bob", 35, "Paris"]
]

with open("people.csv", "w", newline="") as file:
    writer = csv.writer(file)
    writer.writerows(data)

# Reading from a CSV file
with open("people.csv", "r", newline="") as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)
# ['Name', 'Age', 'City']
# ['John', '30', 'New York']
# ['Alice', '25', 'London']
# ['Bob', '35', 'Paris']

# Using DictReader to read CSV as dictionaries
with open("people.csv", "r", newline="") as file:
    reader = csv.DictReader(file)
    for row in reader:
        print(f"{row['Name']} is {row['Age']} years old and lives in {row['City']}")
# John is 30 years old and lives in New York
# Alice is 25 years old and lives in London
# Bob is 35 years old and lives in Paris

# Using DictWriter to write dictionaries to CSV
data = [
    {"Name": "Charlie", "Age": 40, "City": "Berlin"},
    {"Name": "David", "Age": 22, "City": "Tokyo"},
    {"Name": "Eve", "Age": 28, "City": "Sydney"}
]

with open("more_people.csv", "w", newline="") as file:
    fieldnames = ["Name", "Age", "City"]
    writer = csv.DictWriter(file, fieldnames=fieldnames)
    writer.writeheader()
    writer.writerows(data)

# Handling different delimiters
with open("data.tsv", "w", newline="") as file:
    writer = csv.writer(file, delimiter="\t")
    writer.writerows(data)

with open("data.tsv", "r", newline="") as file:
    reader = csv.reader(file, delimiter="\t")
    for row in reader:
        print(row)

# Handling quotes and special characters
data = [
    ["Name", "Description"],
    ["Product A", "Contains, a comma"],
    ["Product B", "Has \"quotes\" in it"],
    ["Product C", "Has a\nnewline"]
]

with open("products.csv", "w", newline="") as file:
    writer = csv.writer(file, quoting=csv.QUOTE_NONNUMERIC)
    writer.writerows(data)

with open("products.csv", "r", newline="") as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)
```

### Datetime Handling

**What it is**: The `datetime` module provides classes for manipulating dates and times in an easy and object-oriented way.

**How it works**: The module offers classes like `datetime`, `date`, `time`, and `timedelta` for representing and manipulating date and time values.

**Examples**:

```python
import datetime

# Current date and time
now = datetime.datetime.now()
print(now)  # 2023-05-17 15:30:45.123456

# Creating date and time objects
date = datetime.date(2023, 5, 17)
time = datetime.time(15, 30, 45)
dt = datetime.datetime(2023, 5, 17, 15, 30, 45)

print(date)  # 2023-05-17
print(time)  # 15:30:45
print(dt)    # 2023-05-17 15:30:45

# Current date
today = datetime.date.today()
print(today)  # 2023-05-17

# Date from timestamp
timestamp = 1621267200  # Seconds since epoch (Jan 1, 1970)
date_from_timestamp = datetime.date.fromtimestamp(timestamp)
print(date_from_timestamp)  # 2021-05-17

# Date attributes
print(today.year)    # 2023
print(today.month)   # 5
print(today.day)     # 17
print(today.weekday())  # 2 (Wednesday, 0 is Monday)

# Time attributes
print(time.hour)     # 15
print(time.minute)   # 30
print(time.second)   # 45
print(time.microsecond)  # 0

# Formatting dates and times
now = datetime.datetime.now()
formatted = now.strftime("%Y-%m-%d %H:%M:%S")
print(formatted)  # 2023-05-17 15:30:45

# Common format codes:
# %Y - Year with century (e.g., 2023)
# %m - Month as a zero-padded number (e.g., 05)
# %d - Day as a zero-padded number (e.g., 17)
# %H - Hour (24-hour clock) as a zero-padded number (e.g., 15)
# %I - Hour (12-hour clock) as a zero-padded number (e.g., 03)
# %M - Minute as a zero-padded number (e.g., 30)
# %S - Second as a zero-padded number (e.g., 45)
# %p - AM or PM (e.g., PM)
# %A - Full weekday name (e.g., Wednesday)
# %B - Full month name (e.g., May)

# Parsing strings to datetime
date_string = "2023-05-17 15:30:45"
parsed_date = datetime.datetime.strptime(date_string, "%Y-%m-%d %H:%M:%S")
print(parsed_date)  # 2023-05-17 15:30:45

# Date arithmetic with timedelta
today = datetime.date.today()
one_day = datetime.timedelta(days=1)
yesterday = today - one_day
tomorrow = today + one_day

print(yesterday)  # 2023-05-16
print(tomorrow)   # 2023-05-18

# Various timedelta examples
one_week = datetime.timedelta(weeks=1)
two_hours = datetime.timedelta(hours=2)
thirty_minutes = datetime.timedelta(minutes=30)
future_date = now + one_week + two_hours + thirty_minutes
print(future_date)  # 2023-05-24 18:00:45.123456

# Comparing dates
date1 = datetime.date(2023, 5, 17)
date2 = datetime.date(2023, 5, 18)

print(date1 < date2)   # True
print(date1 == date2)  # False
print(date1 > date2)   # False

# Date replacement
dt = datetime.datetime(2023, 5, 17, 15, 30, 45)
dt_modified = dt.replace(year=2024, hour=10)
print(dt_modified)  # 2024-05-17 10:30:45
```

### Random Data Generation

**What it is**: The `random` module provides functions for generating random numbers and making random selections.

**How it works**: The module implements pseudo-random number generators for various distributions.

**Examples**:

```python
import random

# Setting a seed for reproducibility
random.seed(42)

# Random floating-point number between 0 and 1
rand_float = random.random()
```