---
aliases:
  - "Part 3: Python Comprehensive Guide"
---
# File and Directory Operations (continued)

**Examples (continued)**:

```python
# Delete a directory and its contents
shutil.rmtree("directory_to_delete")

# Copy a file
shutil.copy("source.txt", "destination.txt")

# Copy a directory and its contents
shutil.copytree("source_dir", "destination_dir")

# Move a file or directory
shutil.move("source", "destination")

# Get absolute path
abs_path = os.path.abspath("relative/path")
print(abs_path)

# Normalize path
norm_path = os.path.normpath("path/with/../redundant/./parts")
print(norm_path)  # "path/redundant/parts"

# Walk through a directory tree
for root, dirs, files in os.walk("some_directory"):
    print(f"Root: {root}")
    print(f"Directories: {dirs}")
    print(f"Files: {files}")
```

## Error Handling

### Try-Except Blocks

**What they are**: Try-except blocks are used to catch and handle exceptions that may occur during program execution.

**How they work**: The code in the `try` block is executed, and if an exception occurs, the execution transfers to the appropriate `except` block.

**Examples**:

```python
# Basic try-except
try:
    x = 10 / 0  # This will raise a ZeroDivisionError
except ZeroDivisionError:
    print("Cannot divide by zero!")

# Multiple except blocks
try:
    number = int("abc")  # This will raise a ValueError
except ValueError:
    print("Invalid conversion to integer")
except ZeroDivisionError:
    print("Cannot divide by zero")

# Catching multiple exceptions in one block
try:
    # Some risky operation
    result = int("abc") / 0
except (ValueError, ZeroDivisionError) as e:
    print(f"An error occurred: {str(e)}")

# Catching any exception
try:
    # Some risky operation
    result = risky_function()
except Exception as e:
    print(f"An error occurred: {str(e)}")

# Getting exception information
try:
    x = 10 / 0
except Exception as e:
    print(f"Type: {type(e).__name__}")
    print(f"Message: {str(e)}")
    import traceback
    print(f"Traceback: {traceback.format_exc()}")

# Nested try-except blocks
try:
    try:
        x = 10 / 0
    except ValueError:
        print("This won't catch the error")
except ZeroDivisionError:
    print("This will catch the error")
```

### Finally Clause

**What it is**: The `finally` clause contains code that is always executed, whether an exception occurred or not.

**How it works**: The code in the `finally` block runs after the `try` and `except` blocks, regardless of whether an exception was raised or caught.

**Examples**:

```python
# Basic try-except-finally
try:
    file = open("example.txt", "r")
    content = file.read()
except FileNotFoundError:
    print("File not found!")
finally:
    # This will run regardless of whether an exception occurred
    print("Execution completed")
    # Close the file if it was opened
    if 'file' in locals() and not file.closed:
        file.close()

# Finally with return in try
def function_with_return():
    try:
        print("In try block")
        return "Return from try"
    finally:
        print("In finally block")  # This will execute before the return

result = function_with_return()
print(result)  # "Return from try"

# Finally with return in both try and finally
def function_with_multiple_returns():
    try:
        print("In try block")
        return "Return from try"
    finally:
        print("In finally block")
        return "Return from finally"  # This will override the try's return

result = function_with_multiple_returns()
print(result)  # "Return from finally"
```

### Else Clause

**What it is**: The `else` clause contains code that is executed if no exceptions were raised in the `try` block.

**How it works**: The code in the `else` block runs after the `try` block, but only if no exceptions were raised.

**Examples**:

```python
# Try-except-else
try:
    x = 10 / 2  # This won't raise an exception
except ZeroDivisionError:
    print("Cannot divide by zero!")
else:
    print(f"Division result: {x}")  # This will execute

# Else clause with file operations
try:
    with open("example.txt", "r") as file:
        content = file.read()
except FileNotFoundError:
    print("File not found!")
else:
    # This will only run if the file was found and read successfully
    print(f"File content length: {len(content)}")

# Complete try-except-else-finally
try:
    num = int(input("Enter a number: "))
except ValueError:
    print("Invalid input!")
else:
    print(f"You entered: {num}")
finally:
    print("Execution completed")
```

### Raising Exceptions

**What it is**: Raising exceptions allows you to explicitly trigger an exception when a certain condition is met.

**How it works**: The `raise` statement is used to raise an exception. You can raise built-in exceptions or custom exceptions.

**Examples**:

```python
# Raising a built-in exception
def validate_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative")
    if age > 120:
        raise ValueError("Age unrealistically high")
    return age

try:
    validate_age(-5)
except ValueError as e:
    print(e)  # "Age cannot be negative"

# Re-raising an exception
try:
    x = 10 / 0
except ZeroDivisionError:
    print("Caught an error, but re-raising it")
    raise  # Re-raises the last exception

# Raising an exception with a custom message
raise ValueError("This is a custom error message")

# Creating and raising a custom exception
class CustomError(Exception):
    def __init__(self, message, code):
        self.message = message
        self.code = code
        super().__init__(self.message)

# Raising the custom exception
try:
    raise CustomError("Something went wrong", 500)
except CustomError as e:
    print(f"Error message: {e.message}")
    print(f"Error code: {e.code}")
```

### Custom Exceptions

**What they are**: Custom exceptions are user-defined exception classes that extend the built-in Exception class or its subclasses.

**How they work**: By creating custom exception classes, you can provide more specific error types and additional context for errors in your application.

**Examples**:

```python
# Basic custom exception
class MyError(Exception):
    pass

try:
    raise MyError("This is a custom error")
except MyError as e:
    print(f"Caught custom error: {e}")

# Custom exception with additional attributes
class ValidationError(Exception):
    def __init__(self, message, field):
        self.message = message
        self.field = field
        super().__init__(f"{field}: {message}")

try:
    raise ValidationError("Cannot be empty", "username")
except ValidationError as e:
    print(f"Field: {e.field}")
    print(f"Message: {e.message}")

# Hierarchy of custom exceptions
class AppError(Exception):
    """Base class for all application errors"""
    pass

class DatabaseError(AppError):
    """Errors related to database operations"""
    pass

class NetworkError(AppError):
    """Errors related to network operations"""
    pass

class ConnectionError(NetworkError):
    """Errors related to network connections"""
    pass

# Using the hierarchy
try:
    raise ConnectionError("Failed to connect to server")
except ConnectionError as e:
    print("Connection error:", e)
except NetworkError as e:
    print("Network error:", e)
except AppError as e:
    print("Application error:", e)
except Exception as e:
    print("Unknown error:", e)
```

### Assert Statement

**What it is**: The `assert` statement is used to test if a condition is true, and if not, it raises an AssertionError with an optional message.

**How it works**: If the condition evaluates to False, an AssertionError is raised. Assertions can be disabled globally by running Python with the -O (optimize) flag.

**Examples**:

```python
# Basic assert
def calculate_square_root(num):
    assert num >= 0, "Number must be non-negative"
    return num ** 0.5

try:
    result = calculate_square_root(-1)
except AssertionError as e:
    print(e)  # "Number must be non-negative"

# Using assert for invariants
def divide(a, b):
    assert b != 0, "Divisor cannot be zero"
    return a / b

# Using assert for type checking
def process_list(items):
    assert isinstance(items, list), "Items must be a list"
    return [item.upper() for item in items if isinstance(item, str)]

# Using assert for postconditions
def get_positive_value():
    result = compute_value()
    assert result > 0, "Expected a positive result"
    return result

# Assertions in a class
class Rectangle:
    def __init__(self, width, height):
        assert width > 0, "Width must be positive"
        assert height > 0, "Height must be positive"
        self.width = width
        self.height = height
        
    def set_dimensions(self, width, height):
        assert width > 0, "Width must be positive"
        assert height > 0, "Height must be positive"
        self.width = width
        self.height = height
```

## Functional Programming

### First-Class Functions

**What they are**: In Python, functions are first-class objects, which means they can be passed as arguments, returned from other functions, and assigned to variables.

**How they work**: Functions in Python are objects and can be manipulated like any other object.

**Examples**:

```python
# Assigning a function to a variable
def square(x):
    return x ** 2

f = square
print(f(5))  # 25

# Passing a function as an argument
def apply_function(func, value):
    return func(value)

result = apply_function(square, 4)  # 16

# Returning a function from another function
def get_multiplier(factor):
    def multiplier(x):
        return x * factor
    return multiplier

double = get_multiplier(2)
triple = get_multiplier(3)

print(double(5))  # 10
print(triple(5))  # 15

# Storing functions in data structures
function_list = [lambda x: x**2, lambda x: x**3, lambda x: x**4]
for func in function_list:
    print(func(2))  # 4, 8, 16

function_dict = {
    'square': lambda x: x**2,
    'cube': lambda x: x**3
}
print(function_dict['square'](3))  # 9
```

### Map, Filter, and Reduce

**What they are**: Map, filter, and reduce are higher-order functions that operate on iterables.

- `map()` applies a function to all items in an iterable.
- `filter()` filters items from an iterable based on a function.
- `reduce()` (from the `functools` module) applies a function cumulatively to the items of an iterable.

**How they work**: These functions process iterables in a functional programming style, avoiding explicit loops.

**Examples**:

```python
# Map function
numbers = [1, 2, 3, 4, 5]
squared = map(lambda x: x**2, numbers)
print(list(squared))  # [1, 4, 9, 16, 25]

# Map with multiple iterables
first_list = [1, 2, 3]
second_list = [10, 20, 30]
sums = map(lambda x, y: x + y, first_list, second_list)
print(list(sums))  # [11, 22, 33]

# Filter function
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
even_numbers = filter(lambda x: x % 2 == 0, numbers)
print(list(even_numbers))  # [2, 4, 6, 8, 10]

# Filter with a named function
def is_positive(num):
    return num > 0

numbers = [-2, -1, 0, 1, 2]
positive_numbers = filter(is_positive, numbers)
print(list(positive_numbers))  # [1, 2]

# Reduce function
from functools import reduce
numbers = [1, 2, 3, 4, 5]
product = reduce(lambda x, y: x * y, numbers)
print(product)  # 120 (1*2*3*4*5)

# Reduce with an initial value
sum_with_initial = reduce(lambda x, y: x + y, numbers, 10)
print(sum_with_initial)  # 25 (10+1+2+3+4+5)

# Combining map, filter, and reduce
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
# Sum of squares of even numbers
result = reduce(
    lambda x, y: x + y,
    map(lambda x: x**2,
        filter(lambda x: x % 2 == 0, numbers))
)
print(result)  # 220 (4+16+36+64+100)
```

### List Comprehensions

**What they are**: List comprehensions provide a concise way to create lists based on existing lists or other iterables.

**How they work**: A list comprehension consists of brackets containing an expression followed by a for clause, then zero or more for or if clauses.

**Examples**:

```python
# Basic list comprehension
numbers = [1, 2, 3, 4, 5]
squares = [x**2 for x in numbers]
print(squares)  # [1, 4, 9, 16, 25]

# List comprehension with condition
even_squares = [x**2 for x in numbers if x % 2 == 0]
print(even_squares)  # [4, 16]

# Nested list comprehension
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flattened = [item for row in matrix for item in row]
print(flattened)  # [1, 2, 3, 4, 5, 6, 7, 8, 9]

# Transposing a matrix
transposed = [[row[i] for row in matrix] for i in range(3)]
print(transposed)  # [[1, 4, 7], [2, 5, 8], [3, 6, 9]]

# List comprehension with conditional expression (ternary)
numbers = [1, 2, 3, 4, 5]
parity = ["even" if x % 2 == 0 else "odd" for x in numbers]
print(parity)  # ['odd', 'even', 'odd', 'even', 'odd']

# Creating a dictionary with list comprehension
squares_dict = {x: x**2 for x in range(1, 6)}
print(squares_dict)  # {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

# Creating a set with list comprehension
squares_set = {x**2 for x in range(1, 6)}
print(squares_set)  # {1, 4, 9, 16, 25}

# List comprehension vs. map and filter
numbers = [1, 2, 3, 4, 5]
# These are equivalent:
squares1 = [x**2 for x in numbers]
squares2 = list(map(lambda x: x**2, numbers))

# These are equivalent:
even_numbers1 = [x for x in numbers if x % 2 == 0]
even_numbers2 = list(filter(lambda x: x % 2 == 0, numbers))
```

### Generator Expressions

**What they are**: Generator expressions are similar to list comprehensions but create generators instead of lists.

**How they work**: They use the same syntax as list comprehensions but with parentheses instead of brackets, and they generate values on-the-fly, making them more memory-efficient for large datasets.

**Examples**:

```python
# Basic generator expression
numbers = [1, 2, 3, 4, 5]
squares_gen = (x**2 for x in numbers)
print(squares_gen)  # <generator object <genexpr> at 0x...>

# Consuming a generator
for square in squares_gen:
    print(square)  # 1, 4, 9, 16, 25

# Converting a generator to a list
numbers = [1, 2, 3, 4, 5]
squares_gen = (x**2 for x in numbers)
squares_list = list(squares_gen)
print(squares_list)  # [1, 4, 9, 16, 25]

# Memory efficiency
# This would be memory-intensive for large n:
# squares_list = [x**2 for x in range(1000000)]

# This is memory-efficient:
squares_gen = (x**2 for x in range(1000000))
# Only generates values as needed

# Generator expressions with conditions
even_squares_gen = (x**2 for x in range(10) if x % 2 == 0)
print(list(even_squares_gen))  # [0, 4, 16, 36, 64]

# Using generator expressions in function calls
sum_of_squares = sum(x**2 for x in range(10))
print(sum_of_squares)  # 285

max_square = max(x**2 for x in range(10))
print(max_square)  # 81

# Chaining generator expressions
gen1 = (x for x in range(5))
gen2 = (x * 2 for x in gen1)
print(list(gen2))  # [0, 2, 4, 6, 8]
```

### Closures

**What they are**: A closure is a function that remembers values from the enclosing lexical scope even when the program flow is no longer in that scope.

**How they work**: When a nested function references variables from its enclosing function, those variables are "captured" in the closure, allowing the nested function to access them even after the enclosing function has finished execution.

**Examples**:

```python
# Basic closure
def make_counter():
    count = 0
    
    def increment():
        nonlocal count
        count += 1
        return count
    
    return increment

counter = make_counter()
print(counter())  # 1
print(counter())  # 2
print(counter())  # 3

# Another counter from the same factory
counter2 = make_counter()
print(counter2())  # 1 (independent of first counter)

# Closure with parameters
def multiplier(factor):
    def multiply(number):
        return number * factor
    return multiply

double = multiplier(2)
triple = multiplier(3)

print(double(5))  # 10
print(triple(5))  # 15

# Closure to maintain state
def create_account(initial_balance):
    balance = initial_balance
    
    def deposit(amount):
        nonlocal balance
        balance += amount
        return balance
    
    def withdraw(amount):
        nonlocal balance
        if amount > balance:
            return "Insufficient funds"
        balance -= amount
        return balance
    
    def get_balance():
        return balance
    
    # Return a dictionary of operations
    return {
        "deposit": deposit,
        "withdraw": withdraw,
        "balance": get_balance
    }

account = create_account(100)
print(account["balance"]())  # 100
print(account["deposit"](50))  # 150
print(account["withdraw"](30))  # 120
print(account["withdraw"](200))  # "Insufficient funds"
```

## Iterators and Generators

### Iterators

**What they are**: Iterators are objects that implement the iterator protocol, which consists of the methods `__iter__()` and `__next__()`.

**How they work**: An iterator is used to iterate over a sequence of values, and it keeps track of its state. The `__next__()` method returns the next value in the sequence, and the `__iter__()` method returns the iterator itself.

**Examples**:

```python
# Basic iterator usage
my_list = [1, 2, 3, 4, 5]
iterator = iter(my_list)  # Get an iterator

print(next(iterator))  # 1
print(next(iterator))  # 2
print(next(iterator))  # 3
print(next(iterator))  # 4
print(next(iterator))  # 5
# print(next(iterator))  # StopIteration exception

# Using a for loop (which uses iterators behind the scenes)
for item in my_list:
    print(item)

# Custom iterator class
class Countdown:
    def __init__(self, start):
        self.start = start
    
    def __iter__(self):
        # Return an iterator object
        return CountdownIterator(self.start)

class CountdownIterator:
    def __init__(self, start):
        self.current = start
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.current <= 0:
            raise StopIteration
        self.current -= 1
        return self.current + 1

# Using the custom iterator
countdown = Countdown(5)
for num in countdown:
    print(num)  # 5, 4, 3, 2, 1

# Class that is its own iterator
class Countdown:
    def __init__(self, start):
        self.start = start
    
    def __iter__(self):
        # Return self as an iterator
        return self
    
    def __next__(self):
        if self.start <= 0:
            raise StopIteration
        self.start -= 1
        return self.start + 1

# Using the class that is its own iterator
countdown = Countdown(3)
print(next(countdown))  # 3
print(next(countdown))  # 2
print(next(countdown))  # 1
# print(next(countdown))  # StopIteration exception
```

### Generators

**What they are**: Generators are a special type of iterator that are created using functions with the `yield` statement.

**How they work**: When a generator function is called, it returns a generator object without executing the function body. The function is executed each time `next()` is called on the generator, and it executes until it encounters a `yield` statement, which returns a value and suspends the function's state.

**Examples**:

```python
# Basic generator function
def count_up_to(n):
    i = 1
    while i <= n:
        yield i
        i += 1

# Using the generator
counter = count_up_to(5)
print(next(counter))  # 1
print(next(counter))  # 2
print(next(counter))  # 3
print(next(counter))  # 4
print(next(counter))  # 5
# print(next(counter))  # StopIteration exception

# Using the generator in a for loop
for num in count_up_to(5):
    print(num)  # 1, 2, 3, 4, 5

# Generator with multiple yields
def fibonacci(n):
    a, b = 0, 1
    count = 0
    while count < n:
        yield a
        a, b = b, a + b
        count += 1

for num in fibonacci(10):
    print(num)  # 0, 1, 1, 2, 3, 5, 8, 13, 21, 34

# Infinite generator
def infinite_counter():
    i = 0
    while True:
        yield i
        i += 1

counter = infinite_counter()
for _ in range(5):
    print(next(counter))  # 0, 1, 2, 3, 4

# Generator that yields from another iterable
def flatten(nested_list):
    for item in nested_list:
        if isinstance(item, list):
            # Yield from another generator
            yield from flatten(item)
        else:
            yield item

nested = [1, [2, [3, 4], 5], 6]
for num in flatten(nested):
    print(num)  # 1, 2, 3, 4, 5, 6

# Generator expression (similar to list comprehension)
squares = (x**2 for x in range(5))
for square in squares:
    print(square)  # 0, 1, 4, 9, 16
```

### Yield Statement

**What it is**: The `yield` statement is used in generator functions to produce a value and temporarily suspend the function's execution.

**How it works**: When a generator function yields a value, it remembers its execution state, and when `next()` is called again, it resumes from where it left off.

**Examples**:

```python
# Basic yield usage
def simple_generator():
    yield 1
    yield 2
    yield 3

gen = simple_generator()
print(next(gen))  # 1
print(next(gen))  # 2
print(next(gen))  # 3
# print(next(gen))  # StopIteration exception

# Yield with a loop
def count_up_to(n):
    i = 1
    while i <= n:
        yield i
        i += 1

# Two-way communication with yield
def echo_generator():
    while True:
        received = yield
        yield f"Echo: {received}"

echo = echo_generator()
next(echo)  # Prime the generator
print(echo.send("Hello"))  # Echo: Hello
next(echo)  # Prepare for next send
print(echo.send("World"))  # Echo: World

# Using yield to create a coroutine
def grep(pattern):
    print(f"Looking for {pattern}")
    while True:
        line = yield
        if pattern in line:
            print(line)

search = grep("python")
next(search)  # Prime the coroutine
search.send("python is great")  # Prints: python is great
search.send("no match here")    # No output
search.send("python rules")     # Prints: python rules

# yield from
def subgenerator():
    yield 1
    yield 2
    yield 3

def main_generator():
    yield "Start"
    yield from subgenerator()
    yield "End"

for item in main_generator():
    print(item)  # Start, 1, 2, 3, End
```

## Decorators

### Function Decorators

**What they are**: Decorators are a way to modify or extend the behavior of functions or methods without modifying their source code.

**How they work**: A decorator is a callable that takes a function as an argument and returns a replacement function that typically extends the original's behavior.

**Examples**:

```python
# Basic decorator
def my_decorator(func):
    def wrapper():
        print("Before function call")
        func()
        print("After function call")
    return wrapper

# Using decorator syntax
@my_decorator
def say_hello():
    print("Hello!")

say_hello()
# Output:
# Before function call
# Hello!
# After function call

# Decorator for functions with arguments
def log_args(func):
    def wrapper(*args, **kwargs):
        print(f"Function {func.__name__} called with args: {args}, kwargs: {kwargs}")
        result = func(*args, **kwargs)
        print(f"Function {func.__name__} returned: {result}")
        return result
    return wrapper

@log_args
def add(a, b):
    return a + b

result = add(3, 5)
# Output:
# Function add called with args: (3, 5), kwargs: {}
# Function add returned: 8

# Decorator with arguments
def repeat(n):
    def decorator(func):
        def wrapper(*args, **kwargs):
            results = []
            for _ in range(n):
                results.append(func(*args, **kwargs))
            return results
        return wrapper
    return decorator

@repeat(3)
def greet(name):
    return f"Hello, {name}!"

print(greet("Alice"))
# Output: ['Hello, Alice!', 'Hello, Alice!', 'Hello, Alice!']

# Stacking decorators
def bold(func):
    def wrapper(*args, **kwargs):
        return f"<b>{func(*args, **kwargs)}</b>"
    return wrapper

def italic(func):
    def wrapper(*args, **kwargs):
        return f"<i>{func(*args, **kwargs)}</i>"
    return wrapper

@bold
@italic
def format_text(text):
    return text

print(format_text("Hello, World!"))
# Output: <b><i>Hello, World!</i></b>

# Class-based decorator
class CountCalls:
    def __init__(self, func):
        self.func = func
        self.count = 0
    
    def __call__(self, *args, **kwargs):
        self.count += 1
        print(f"Call {self.count} of {self.func.__name__}")
        return self.func(*args, **kwargs)

@CountCalls
def say_hi():
    print("Hi!")

say_hi()  # Call 1 of say_hi
say_hi()  # Call 2 of say_hi
```

### Class Decorators

**What they are**: Class decorators are similar to function decorators but are applied to class definitions instead of functions.

**How they work**: A class decorator is a callable that takes a class as an argument and returns a replacement class that typically extends or modifies the original.

**Examples**:

```python
# Basic class decorator
def add_greeting(cls):
    cls.greeting = "Hello!"
    return cls

@add_greeting
class Person:
    def __init__(self, name):
        self.name = name

person = Person("Alice")
print(person.greeting)  # Hello!

# Decorator that adds methods to a class
def add_methods(cls):
    def say_hello(self):
        return f"Hello, I'm {self.name}"
    
    def say_goodbye(self):
        return f"Goodbye from {self.name}"
    
    cls.say_hello = say_hello
    cls.say_goodbye = say_goodbye
    return cls

@add_methods
class Person:
    def __init__(self, name):
        self.name = name

person = Person("Bob")
print(person.say_hello())    # Hello, I'm Bob
print(person.say_goodbye())  # Goodbye from Bob

# Decorator that wraps all methods
def log_all_methods(cls):
    for name, method in cls.__dict__.items():
        if callable(method) and name != "__init__":
            setattr(cls, name, log_method(method))
    return cls

def log_method(method):
    def wrapper(self, *args, **kwargs):
        print(f"Calling {method.__name__}")
        result = method(self, *args, **kwargs)
        print(f"{method.__name__} returned {result}")
        return result
    return wrapper

@log_all_methods
class Calculator:
    def add(self, a, b):
        return a + b
    
    def subtract(self, a, b):
        return a - b

calc = Calculator()
calc.add(5, 3)  # Logs: Calling add, add returned 8
calc.subtract(10, 4)  # Logs: Calling subtract, subtract returned 6

# Singleton
```