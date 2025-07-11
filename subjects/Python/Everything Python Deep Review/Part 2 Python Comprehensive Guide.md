---
aliases:
  - "Part 2: Python Comprehensive Guide"
---
# Lambda Functions (continued)

**Examples (continued)**:

```python
# Lambda with multiple arguments
add = lambda x, y: x + y
print(add(3, 5))  # 8

# Lambda in sorting
students = [
    {"name": "Alice", "grade": 88},
    {"name": "Bob", "grade": 92},
    {"name": "Charlie", "grade": 85}
]
# Sort by grade
sorted_students = sorted(students, key=lambda student: student["grade"], reverse=True)
# sorted_students order: Bob, Alice, Charlie

# Lambda with map
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x**2, numbers))  # [1, 4, 9, 16, 25]

# Lambda with filter
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))  # [2, 4, 6, 8, 10]

# Lambda with reduce
from functools import reduce
product = reduce(lambda x, y: x * y, numbers)  # 3628800 (factorial of 10)
```

### Recursion

**What it is**: Recursion is when a function calls itself directly or indirectly.

**How it works**: A recursive function solves a problem by solving smaller instances of the same problem. Every recursive function needs a base case to avoid infinite recursion.

**Examples**:

```python
# Factorial calculation using recursion
def factorial(n):
    if n <= 1:  # Base case
        return 1
    else:  # Recursive case
        return n * factorial(n - 1)

print(factorial(5))  # 120 (5 * 4 * 3 * 2 * 1)

# Fibonacci sequence using recursion
def fibonacci(n):
    if n <= 1:  # Base cases
        return n
    else:  # Recursive case
        return fibonacci(n-1) + fibonacci(n-2)

for i in range(10):
    print(fibonacci(i), end=" ")  # 0 1 1 2 3 5 8 13 21 34

# Recursion with memoization to improve performance
def fibonacci_memo(n, memo={}):
    if n in memo:
        return memo[n]
    if n <= 1:
        return n
    memo[n] = fibonacci_memo(n-1, memo) + fibonacci_memo(n-2, memo)
    return memo[n]

# File system traversal with recursion
import os

def list_files(directory):
    for item in os.listdir(directory):
        path = os.path.join(directory, item)
        if os.path.isfile(path):
            print(f"File: {path}")
        elif os.path.isdir(path):
            print(f"Directory: {path}")
            list_files(path)  # Recursive call
```

## Classes and Object-Oriented Programming

### Class Definition

**What it is**: A class is a blueprint for creating objects that encapsulate data and behavior.

**How it works**: Classes are defined using the `class` keyword and can contain attributes (variables) and methods (functions).

**Examples**:

```python
# Simple class definition
class Dog:
    # Class attribute (shared by all instances)
    species = "Canis familiaris"
    
    # Initializer (constructor)
    def __init__(self, name, age):
        # Instance attributes (unique to each instance)
        self.name = name
        self.age = age
    
    # Instance method
    def description(self):
        return f"{self.name} is {self.age} years old"
    
    # Another instance method
    def speak(self, sound):
        return f"{self.name} says {sound}"

# Creating an instance of the class
my_dog = Dog("Rex", 3)

# Accessing attributes
print(my_dog.name)  # Rex
print(my_dog.species)  # Canis familiaris

# Calling methods
print(my_dog.description())  # Rex is 3 years old
print(my_dog.speak("Woof"))  # Rex says Woof

# Modifying attributes
my_dog.age = 4
print(my_dog.description())  # Rex is 4 years old
```

### Inheritance

**What it is**: Inheritance allows a class to acquire the properties and methods of another class.

**How it works**: A child class inherits attributes and methods from its parent class and can override or extend them.

**Examples**:

```python
# Parent class
class Animal:
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        raise NotImplementedError("Subclass must implement abstract method")
    
    def eat(self):
        return f"{self.name} is eating"

# Child class
class Dog(Animal):
    def speak(self):
        return f"{self.name} says Woof!"
    
    def fetch(self):
        return f"{self.name} is fetching a ball"

# Another child class
class Cat(Animal):
    def speak(self):
        return f"{self.name} says Meow!"
    
    def groom(self):
        return f"{self.name} is grooming"

# Create instances
my_dog = Dog("Rex")
my_cat = Cat("Fluffy")

# Inherited method
print(my_dog.eat())  # Rex is eating

# Overridden method
print(my_dog.speak())  # Rex says Woof!
print(my_cat.speak())  # Fluffy says Meow!

# Child-specific methods
print(my_dog.fetch())  # Rex is fetching a ball
print(my_cat.groom())  # Fluffy is grooming

# Checking inheritance
print(isinstance(my_dog, Dog))    # True
print(isinstance(my_dog, Animal))  # True
print(issubclass(Dog, Animal))    # True
```

### Multiple Inheritance

**What it is**: Multiple inheritance allows a class to inherit from more than one parent class.

**How it works**: The child class inherits attributes and methods from all parent classes. Python uses the Method Resolution Order (MRO) to determine which method to call when the same method exists in multiple parent classes.

**Examples**:

```python
# First parent class
class Animal:
    def __init__(self, name):
        self.name = name
    
    def eat(self):
        return f"{self.name} is eating"

# Second parent class
class Flyable:
    def fly(self):
        return f"{self.name} is flying"

# Child class with multiple inheritance
class Bird(Animal, Flyable):
    def speak(self):
        return f"{self.name} says Tweet!"

# Create an instance
my_bird = Bird("Tweety")

# Methods from Animal
print(my_bird.eat())  # Tweety is eating

# Methods from Flyable
print(my_bird.fly())  # Tweety is flying

# Method Resolution Order (MRO)
print(Bird.__mro__)  # (<class 'Bird'>, <class 'Animal'>, <class 'Flyable'>, <class 'object'>)

# Diamond inheritance problem
class A:
    def method(self):
        return "A"

class B(A):
    def method(self):
        return "B"

class C(A):
    def method(self):
        return "C"

class D(B, C):
    pass

# MRO resolves the diamond problem
d = D()
print(d.method())  # "B" (follows MRO)
print(D.__mro__)  # (<class 'D'>, <class 'B'>, <class 'C'>, <class 'A'>, <class 'object'>)
```

### Method Overriding

**What it is**: Method overriding is the ability of a subclass to provide a specific implementation of a method that is already defined in its parent class.

**How it works**: When a method is called on an instance of the subclass, the subclass's implementation takes precedence over the parent class's implementation.

**Examples**:

```python
# Parent class
class Shape:
    def __init__(self, color):
        self.color = color
    
    def area(self):
        # Base implementation
        return 0
    
    def describe(self):
        return f"A {self.color} shape with area: {self.area()}"

# Child class overriding the area method
class Circle(Shape):
    def __init__(self, color, radius):
        super().__init__(color)
        self.radius = radius
    
    def area(self):
        # Override with specific implementation
        return 3.14159 * self.radius ** 2

# Another child class
class Rectangle(Shape):
    def __init__(self, color, width, height):
        super().__init__(color)
        self.width = width
        self.height = height
    
    def area(self):
        # Override with specific implementation
        return self.width * self.height

# Create instances
circle = Circle("red", 5)
rectangle = Rectangle("blue", 4, 6)

# Call overridden methods
print(circle.area())  # 78.53975
print(rectangle.area())  # 24

# Call parent method that uses overridden method
print(circle.describe())  # A red shape with area: 78.53975
print(rectangle.describe())  # A blue shape with area: 24
```

### Super Function

**What it is**: The `super()` function is used to call methods from a parent class.

**How it works**: It returns a temporary object of the superclass, allowing you to call its methods.

**Examples**:

```python
# Parent class
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def introduce(self):
        return f"My name is {self.name} and I am {self.age} years old."

# Child class using super()
class Student(Person):
    def __init__(self, name, age, grade):
        # Call the parent's __init__ method
        super().__init__(name, age)
        self.grade = grade
    
    def introduce(self):
        # Call the parent's introduce method and extend it
        basic_intro = super().introduce()
        return f"{basic_intro} I'm in grade {self.grade}."

# Create an instance
student = Student("Alice", 15, 10)

# Call the overridden method
print(student.introduce())  
# My name is Alice and I am 15 years old. I'm in grade 10.

# Multiple inheritance with super()
class A:
    def method(self):
        return "A"

class B(A):
    def method(self):
        return super().method() + "B"

class C(A):
    def method(self):
        return super().method() + "C"

class D(B, C):
    def method(self):
        return super().method() + "D"

# Super follows MRO
d = D()
print(d.method())  # "ABCD"
print(D.__mro__)  # (<class 'D'>, <class 'B'>, <class 'C'>, <class 'A'>, <class 'object'>)
```

### Class Methods and Static Methods

**What they are**:

- Class methods are methods that are bound to the class rather than its instances.
- Static methods are methods that don't have access to either the instance (self) or the class (cls).

**How they work**:

- Class methods are defined using the `@classmethod` decorator and receive the class as their first parameter (typically named `cls`).
- Static methods are defined using the `@staticmethod` decorator and don't receive any special first parameter.

**Examples**:

```python
class Person:
    # Class attribute
    person_count = 0
    
    def __init__(self, name, age):
        self.name = name
        self.age = age
        Person.person_count += 1
    
    # Instance method - has access to instance through self
    def introduce(self):
        return f"Hi, I'm {self.name} and I'm {self.age} years old."
    
    # Class method - has access to class through cls
    @classmethod
    def get_person_count(cls):
        return f"There are {cls.person_count} people."
    
    # Another class method - can create instance
    @classmethod
    def from_birth_year(cls, name, birth_year):
        import datetime
        age = datetime.datetime.now().year - birth_year
        return cls(name, age)
    
    # Static method - no access to instance or class
    @staticmethod
    def is_adult(age):
        return age >= 18

# Creating instances
person1 = Person("Alice", 25)
person2 = Person("Bob", 17)

# Calling instance method
print(person1.introduce())  # Hi, I'm Alice and I'm 25 years old.

# Calling class method via class or instance
print(Person.get_person_count())  # There are 2 people.
print(person1.get_person_count())  # There are 2 people.

# Creating instance using alternative constructor
person3 = Person.from_birth_year("Charlie", 1990)
print(person3.age)  # Current year - 1990

# Calling static method via class or instance
print(Person.is_adult(20))  # True
print(person1.is_adult(15))  # False
```

### Properties

**What they are**: Properties provide a way to define getter, setter, and deleter methods for class attributes.

**How they work**: The `@property` decorator is used to define a method that will be called when the attribute is accessed. Additional decorators can be used to define setter and deleter methods.

**Examples**:

```python
class Temperature:
    def __init__(self, celsius=0):
        self._celsius = celsius
    
    # Getter method
    @property
    def celsius(self):
        return self._celsius
    
    # Setter method
    @celsius.setter
    def celsius(self, value):
        if value < -273.15:
            raise ValueError("Temperature below absolute zero is not possible")
        self._celsius = value
    
    # Property with getter only (calculated attribute)
    @property
    def fahrenheit(self):
        return self._celsius * 9/5 + 32
    
    # Setter for the calculated attribute
    @fahrenheit.setter
    def fahrenheit(self, value):
        self.celsius = (value - 32) * 5/9
    
    # Deleter method
    @celsius.deleter
    def celsius(self):
        print("Resetting temperature to absolute zero")
        self._celsius = -273.15

# Creating an instance
temp = Temperature(25)

# Using properties
print(temp.celsius)  # 25
print(temp.fahrenheit)  # 77.0

# Setting values via properties
temp.celsius = 30
print(temp.fahrenheit)  # 86.0

temp.fahrenheit = 68
print(temp.celsius)  # 20.0

# Try setting an invalid value
try:
    temp.celsius = -300
except ValueError as e:
    print(str(e))  # Temperature below absolute zero is not possible

# Using the deleter
del temp.celsius
print(temp.celsius)  # -273.15
```

### Dunder Methods

**What they are**: Dunder (double underscore) methods are special methods in Python classes that allow instances to interact with built-in functions and operators.

**How they work**: Python calls these methods automatically in certain circumstances. For example, `__init__` is called when an object is created, and `__str__` is called by the `str()` function.

**Examples**:

```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    # String representation for developers
    def __repr__(self):
        return f"Vector({self.x}, {self.y})"
    
    # String representation for end users
    def __str__(self):
        return f"({self.x}, {self.y})"
    
    # Addition: v1 + v2
    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)
    
    # Subtraction: v1 - v2
    def __sub__(self, other):
        return Vector(self.x - other.x, self.y - other.y)
    
    # Equality: v1 == v2
    def __eq__(self, other):
        return self.x == other.x and self.y == other.y
    
    # Length: len(v)
    def __len__(self):
        return int((self.x**2 + self.y**2)**0.5)
    
    # Make the object callable: v()
    def __call__(self, scale):
        return Vector(self.x * scale, self.y * scale)
    
    # Container behavior: x in v
    def __contains__(self, item):
        return item == self.x or item == self.y

# Create vectors
v1 = Vector(3, 4)
v2 = Vector(1, 2)

# String representation
print(repr(v1))  # Vector(3, 4)
print(str(v1))   # (3, 4)

# Operator overloading
v3 = v1 + v2
print(v3)  # (4, 6)

v4 = v1 - v2
print(v4)  # (2, 2)

# Equality
print(v3 == Vector(4, 6))  # True

# Length
print(len(v1))  # 5 (sqrt(3^2 + 4^2) = 5)

# Callable object
v5 = v1(2)  # Equivalent to: v1.__call__(2)
print(v5)  # (6, 8)

# Container behavior
print(3 in v1)  # True
print(5 in v1)  # False
```

### Abstract Base Classes

**What they are**: Abstract Base Classes (ABCs) are classes that cannot be instantiated and may contain abstract methods that must be implemented by subclasses.

**How they work**: ABC is a module in Python that provides the infrastructure for defining ABCs. Abstract methods are defined using the `@abstractmethod` decorator.

**Examples**:

```python
from abc import ABC, abstractmethod

# Abstract base class
class Shape(ABC):
    def __init__(self, color):
        self.color = color
    
    @abstractmethod
    def area(self):
        """Calculate the area of the shape."""
        pass
    
    @abstractmethod
    def perimeter(self):
        """Calculate the perimeter of the shape."""
        pass
    
    # Concrete method that uses abstract methods
    def describe(self):
        return f"A {self.color} shape with area {self.area()} and perimeter {self.perimeter()}"

# Concrete subclass
class Circle(Shape):
    def __init__(self, color, radius):
        super().__init__(color)
        self.radius = radius
    
    def area(self):
        return 3.14159 * self.radius**2
    
    def perimeter(self):
        return 2 * 3.14159 * self.radius

# Another concrete subclass
class Rectangle(Shape):
    def __init__(self, color, width, height):
        super().__init__(color)
        self.width = width
        self.height = height
    
    def area(self):
        return self.width * self.height
    
    def perimeter(self):
        return 2 * (self.width + self.height)

# Cannot instantiate the abstract class
try:
    shape = Shape("red")  # This will raise TypeError
except TypeError as e:
    print(str(e))  # Can't instantiate abstract class Shape with abstract methods area, perimeter

# Can instantiate concrete subclasses
circle = Circle("blue", 5)
rectangle = Rectangle("green", 4, 6)

print(circle.area())  # 78.53975
print(rectangle.perimeter())  # 20
print(circle.describe())  # A blue shape with area 78.53975 and perimeter 31.4159
```

## Modules and Packages

### Importing Modules

**What it is**: Importing modules allows you to access code defined in other Python files.

**How it works**: The `import` statement is used to import modules, and the `from` keyword can be used to import specific attributes or functions from a module.

**Examples**:

```python
# Basic import
import math
print(math.sqrt(16))  # 4.0

# Import with alias
import math as m
print(m.sqrt(16))  # 4.0

# Import specific attributes
from math import sqrt, pi
print(sqrt(16))  # 4.0
print(pi)        # 3.141592653589793

# Import all attributes (not recommended)
from math import *
print(cos(0))  # 1.0

# Import with specific and general alternative
import math
from math import sqrt

# These are equivalent
print(math.sqrt(16))  # 4.0
print(sqrt(16))       # 4.0

# Importing from packages
import os.path
print(os.path.join('folder', 'file.txt'))  # folder/file.txt

from os import path
print(path.join('folder', 'file.txt'))  # folder/file.txt
```

### Creating Modules

**What it is**: A module is a file containing Python definitions and statements that can be imported and used in other Python files.

**How it works**: Any Python file can be imported as a module. When a module is imported, its code is executed once.

**Example Module (mymodule.py)**:

```python
# mymodule.py

# Define variables
PI = 3.14159
E = 2.71828

# Define functions
def square(x):
    return x ** 2

def cube(x):
    return x ** 3

# Define a class
class Circle:
    def __init__(self, radius):
        self.radius = radius
    
    def area(self):
        return PI * self.radius ** 2

# Code that runs on import
print("mymodule imported")

# Code that runs only when executed directly
if __name__ == "__main__":
    print("mymodule executed directly")
    print(f"Square of 5: {square(5)}")
```

**Using the Module**:

```python
# Import the entire module
import mymodule
print(mymodule.PI)  # 3.14159
print(mymodule.square(4))  # 16
circle = mymodule.Circle(5)
print(circle.area())  # 78.53975

# Import specific items
from mymodule import PI, square, Circle
print(PI)  # 3.14159
print(square(4))  # 16
circle = Circle(5)
print(circle.area())  # 78.53975
```

### Creating Packages

**What they are**: Packages are a way of organizing related modules into a directory hierarchy.

**How they work**: A package is a directory that contains Python files (modules) and a special `__init__.py` file that indicates the directory is a Python package.

**Example Package Structure**:

```
mypackage/
    __init__.py
    module1.py
    module2.py
    subpackage/
        __init__.py
        module3.py
```

**Example Package Files**:

**mypackage/__init__.py**:

```python
# This file can be empty or can define what gets imported with "from mypackage import *"
__all__ = ['module1', 'module2']

# It can also contain initialization code that runs when the package is imported
print("mypackage initialized")

# It can define variables, functions, or classes that are available directly from the package
version = "1.0.0"

def get_version():
    return version
```

**mypackage/module1.py**:

```python
def function1():
    return "Function 1 from module1"

class Class1:
    def method1(self):
        return "Method 1 from Class1 in module1"
```

**mypackage/module2.py**:

```python
def function2():
    return "Function 2 from module2"

class Class2:
    def method2(self):
        return "Method 2 from Class2 in module2"
```

**mypackage/subpackage/__init__.py**:

```python
print("subpackage initialized")
```

**mypackage/subpackage/module3.py**:

```python
def function3():
    return "Function 3 from module3 in subpackage"
```

**Using the Package**:

```python
# Import from package
import mypackage
print(mypackage.version)  # 1.0.0
print(mypackage.get_version())  # 1.0.0

# Import module from package
import mypackage.module1
print(mypackage.module1.function1())  # Function 1 from module1

# Import from subpackage
import mypackage.subpackage.module3
print(mypackage.subpackage.module3.function3())  # Function 3 from module3 in subpackage

# Direct import of functions or classes
from mypackage.module1 import function1, Class1
print(function1())  # Function 1 from module1
obj = Class1()
print(obj.method1())  # Method 1 from Class1 in module1

# Using relative imports (within package modules)
# In mypackage/subpackage/module3.py, you could do:
# from .. import module1
# from ..module2 import function2
```

## File Handling

### Opening and Closing Files

**What it is**: File handling in Python allows reading from and writing to files on the file system.

**How it works**: The `open()` function is used to open files, and the `close()` method is used to close them. In modern Python, the `with` statement is preferred as it automatically closes the file.

**Examples**:

```python
# Basic open/close pattern (not recommended)
file = open("example.txt", "r")  # Open for reading
content = file.read()
file.close()  # Don't forget to close!

# Preferred: using the with statement (context manager)
with open("example.txt", "r") as file:
    content = file.read()
# File is automatically closed when the block exits

# Opening modes:
# "r" - Read (default)
# "w" - Write (truncates the file)
# "a" - Append
# "x" - Create a new file, fail if it exists
# "b" - Binary mode
# "t" - Text mode (default)
# "+" - Read and write mode

# Text files (default)
with open("text_file.txt", "w") as file:
    file.write("Hello, World!")

# Binary files
with open("binary_file.bin", "wb") as file:
    file.write(b"\x00\x01\x02\x03")

# Specifying encoding for text files
with open("unicode_file.txt", "w", encoding="utf-8") as file:
    file.write("Hello, 世界!")
```

### Reading from Files

**What it is**: Reading from files allows you to access the content of a file.

**How it works**: Python provides several methods for reading file content: `read()`, `readline()`, and `readlines()`.

**Examples**:

```python
# Reading the entire file at once
with open("example.txt", "r") as file:
    content = file.read()
    print(content)

# Reading a specific number of characters
with open("example.txt", "r") as file:
    chunk = file.read(10)  # Read first 10 characters
    print(chunk)

# Reading one line at a time
with open("example.txt", "r") as file:
    line = file.readline()
    print(line)

# Reading all lines into a list
with open("example.txt", "r") as file:
    lines = file.readlines()
    for line in lines:
        print(line.strip())  # strip() removes newline characters

# Iterating through the file line by line (memory efficient)
with open("example.txt", "r") as file:
    for line in file:
        print(line.strip())

# Reading binary data
with open("image.jpg", "rb") as file:
    header = file.read(10)  # Read first 10 bytes
    print(header)
```

### Writing to Files

**What it is**: Writing to files allows you to save data to the file system.

**How it works**: Python provides methods for writing to files: `write()` and `writelines()`.

**Examples**:

```python
# Writing a string to a file (overwrites existing content)
with open("output.txt", "w") as file:
    file.write("Hello, World!\n")
    file.write("This is a new line.")

# Appending to a file
with open("log.txt", "a") as file:
    file.write("New log entry\n")

# Writing multiple lines at once
lines = ["Line 1\n", "Line 2\n", "Line 3\n"]
with open("lines.txt", "w") as file:
    file.writelines(lines)

# Writing formatted data
with open("formatted.txt", "w") as file:
    for i in range(5):
        file.write(f"Number: {i}\n")

# Writing binary data
with open("binary.bin", "wb") as file:
    file.write(b"\x00\x01\x02\x03")

# Writing JSON data
import json
data = {"name": "John", "age": 30}
with open("data.json", "w") as file:
    json.dump(data, file, indent=4)

# Writing CSV data
import csv
data = [["Name", "Age"], ["John", 30], ["Alice", 25]]
with open("data.csv", "w", newline="") as file:
    writer = csv.writer(file)
    writer.writerows(data)
```

### File and Directory Operations

**What they are**: Operations to manipulate files and directories on the file system.

**How they work**: Python's `os` and `shutil` modules provide functions for file and directory operations.

**Examples**:

```python
import os
import shutil

# Check if a file or directory exists
if os.path.exists("file.txt"):
    print("File exists")

# Get file information
if os.path.isfile("file.txt"):
    print("It's a file")
    size = os.path.getsize("file.txt")
    print(f"Size: {size} bytes")
    mod_time = os.path.getmtime("file.txt")
    print(f"Last modified: {mod_time}")

# Create a directory
os.mkdir("new_directory")  # Creates a single directory
os.makedirs("path/to/nested/directory", exist_ok=True)  # Creates nested directories

# List directory contents
files = os.listdir(".")  # List current directory
print(files)

# Get current working directory
cwd = os.getcwd()
print(f"Current directory: {cwd}")

# Change working directory
os.chdir("new_directory")

# Join paths (platform-independent)
path = os.path.join("directory", "subdirectory", "file.txt")
print(path)

# Get parts of a path
dirname = os.path.dirname(path)
basename = os.path.basename(path)
filename, extension = os.path.splitext(basename)
print(f"Directory: {dirname}, Base: {basename}, Filename: {filename}, Extension: {extension}")

# Rename a file
os.rename("old_name.txt", "new_name.txt")

# Delete a file
os.remove("file_to_delete.txt")

# Delete an empty directory
os.rmdir("empty_directory")

# Delete a directory and its contents
shutil.rmtree("directory_to_
```