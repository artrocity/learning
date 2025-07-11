---
aliases:
  - "Part 3: Python Comprehensive Guide"
---
# Method Resolution Order (MRO) (continued)

**How it works (continued)**: Python uses the C3 linearization algorithm to determine the MRO, which ensures that a class always appears before its base classes and the relative order of base classes is preserved.

**Examples**:

```python
# Simple inheritance
class A:
    def method(self):
        return "A"

class B(A):
    def method(self):
        return "B"

class C(B):
    pass

# MRO for class C: C -> B -> A -> object
print(C.__mro__)  # (<class '__main__.C'>, <class '__main__.B'>, <class '__main__.A'>, <class 'object'>)
print(C().method())  # "B" (found in B before reaching A)

# Multiple inheritance
class A:
    def method(self):
        return "A"

class B:
    def method(self):
        return "B"

class C(A, B):
    pass

# MRO for class C: C -> A -> B -> object
print(C.__mro__)  # (<class '__main__.C'>, <class '__main__.A'>, <class '__main__.B'>, <class 'object'>)
print(C().method())  # "A" (found in A before reaching B)

# Diamond inheritance
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

# MRO for class D: D -> B -> C -> A -> object
print(D.__mro__)  # (<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>)
print(D().method())  # "B" (found in B before reaching C)

# Using super() with MRO
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

# MRO for class D: D -> B -> C -> A -> object
print(D.__mro__)  # (<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>)
print(D().method())  # "ABCD" (follows MRO)

# Complex inheritance
class A:
    def method(self):
        return "A"

class B(A):
    def method(self):
        return super().method() + "B"

class C(A):
    def method(self):
        return super().method() + "C"

class D(A):
    def method(self):
        return super().method() + "D"

class E(B, C):
    def method(self):
        return super().method() + "E"

class F(C, D):
    def method(self):
        return super().method() + "F"

class G(E, F):
    def method(self):
        return super().method() + "G"

# MRO for class G
print(G.__mro__)  # Will show the complex linearization
print(G().method())  # Will follow the MRO
```

### Monkey Patching

**What it is**: Monkey patching is the practice of modifying or extending the behavior of existing code at runtime without modifying its source code.

**How it works**: In Python, you can replace methods, attributes, or even entire classes at runtime, which can be useful for testing, debugging, or adding functionality to existing code.

**Examples**:

```python
# Monkey patching a function
def original_function():
    return "Original"

def replacement_function():
    return "Replacement"

# Replace the function
original_function = replacement_function
print(original_function())  # Replacement

# Monkey patching a method
class MyClass:
    def method(self):
        return "Original method"

def new_method(self):
    return "New method"

# Replace the method
MyClass.method = new_method
obj = MyClass()
print(obj.method())  # New method

# Monkey patching an instance
obj = MyClass()
original_method = obj.method

def instance_method(self):
    return "Instance-specific method"

obj.method = instance_method.__get__(obj, MyClass)
print(obj.method())  # Instance-specific method

# Creating a new instance without the patch
obj2 = MyClass()
print(obj2.method())  # New method (class-level patch still applies)

# Monkey patching built-in types (generally not recommended)
original_len = len
def custom_len(obj):
    print("Custom len called")
    return original_len(obj)

len = custom_len
print(len([1, 2, 3]))  # Custom len called, 3

# Restoring the original function
len = original_len
print(len([1, 2, 3]))  # 3

# Monkey patching a module
import datetime

# Save the original function
original_now = datetime.datetime.now

def mock_now():
    return datetime.datetime(2023, 1, 1, 12, 0, 0)

# Replace the function
datetime.datetime.now = mock_now
print(datetime.datetime.now())  # 2023-01-01 12:00:00

# Restore the original function
datetime.datetime.now = original_now
print(datetime.datetime.now())  # Current date and time

# Safer patching with context managers
from contextlib import contextmanager

@contextmanager
def patch_method(target_object, method_name, replacement):
    original = getattr(target_object, method_name)
    setattr(target_object, method_name, replacement)
    try:
        yield
    finally:
        setattr(target_object, method_name, original)

class Example:
    def method(self):
        return "Original"

def replacement(self):
    return "Patched"

example = Example()
print(example.method())  # Original

with patch_method(Example, "method", replacement):
    print(example.method())  # Patched

print(example.method())  # Original again
```

### Slots

**What they are**: The `__slots__` attribute is a class variable that can be used to define a fixed set of attributes for a class, saving memory and preventing the creation of new attributes.

**How they work**: When you define `__slots__` in a class, Python creates a more efficient data structure to store the instance attributes, instead of using a dictionary.

**Examples**:

```python
# Class without slots
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

# Class with slots
class PersonWithSlots:
    __slots__ = ['name', 'age']  # Define allowed attributes
    
    def __init__(self, name, age):
        self.name = name
        self.age = age

# Using the classes
person = Person("John", 30)
person_with_slots = PersonWithSlots("Alice", 25)

# Both work the same for defined attributes
print(person.name)  # John
print(person_with_slots.name)  # Alice

# Regular class allows adding new attributes
person.email = "john@example.com"  # This works
print(person.email)  # john@example.com

# Slots class prevents adding new attributes
try:
    person_with_slots.email = "alice@example.com"  # This will raise an AttributeError
except AttributeError as e:
    print(e)  # 'PersonWithSlots' object has no attribute 'email'

# Memory comparison
import sys
print(f"Memory usage without slots: {sys.getsizeof(person.__dict__)} bytes")
# No __dict__ for slots class
print(f"Memory usage with slots: "
      f"{sum(sys.getsizeof(getattr(person_with_slots, slot)) for slot in PersonWithSlots.__slots__)} bytes")

# __slots__ and inheritance
class Parent:
    __slots__ = ['a', 'b']

class Child(Parent):
    __slots__ = ['c', 'd']
    # Child's slots are ['a', 'b', 'c', 'd']

child = Child()
child.a = 1
child.c = 3
print(child.a, child.c)  # 1 3

# Class with both __slots__ and __dict__
class Flexible:
    __slots__ = ['a', 'b', '__dict__']
    
    def __init__(self, a, b):
        self.a = a
        self.b = b

flex = Flexible(1, 2)
flex.c = 3  # This works because we included __dict__ in __slots__
print(flex.a, flex.b, flex.c)  # 1 2 3

# Using __slots__ with properties
class Temperature:
    __slots__ = ['_celsius']
    
    def __init__(self, celsius):
        self._celsius = celsius
    
    @property
    def celsius(self):
        return self._celsius
    
    @celsius.setter
    def celsius(self, value):
        if value < -273.15:
            raise ValueError("Temperature below absolute zero")
        self._celsius = value
    
    @property
    def fahrenheit(self):
        return self._celsius * 9/5 + 32
    
    @fahrenheit.setter
    def fahrenheit(self, value):
        self.celsius = (value - 32) * 5/9

temp = Temperature(25)
print(temp.celsius)  # 25
print(temp.fahrenheit)  # 77.0
temp.celsius = 30
print(temp.fahrenheit)  # 86.0
```

### Type Hints

**What they are**: Type hints are annotations added to Python code to indicate the expected types of variables, function parameters, and return values.

**How they work**: Type hints don't affect runtime behavior by default but can be used by third-party tools like mypy for static type checking and by IDEs for better code completion and error detection.

**Examples**:

```python
# Basic type hints
def greet(name: str) -> str:
    return f"Hello, {name}!"

result: str = greet("World")
print(result)  # Hello, World!

# Type hints for variables
age: int = 30
pi: float = 3.14159
active: bool = True
name: str = "Alice"

# Type hints for collections
from typing import List, Dict, Tuple, Set, Optional, Union, Any

# List
numbers: List[int] = [1, 2, 3]
names: List[str] = ["Alice", "Bob", "Charlie"]

# Dict
person: Dict[str, str] = {"name": "Alice", "city": "New York"}
counts: Dict[str, int] = {"apples": 10, "oranges": 5}

# Tuple
point: Tuple[int, int] = (10, 20)
rgb: Tuple[int, int, int] = (255, 0, 0)

# Set
unique_numbers: Set[int] = {1, 2, 3}

# Optional (either the specified type or None)
def find_user(user_id: int) -> Optional[Dict[str, Any]]:
    if user_id == 42:
        return {"name": "Alice", "age": 30}
    return None

# Union (one of several types)
def process_input(data: Union[str, bytes]) -> str:
    if isinstance(data, bytes):
        return data.decode('utf-8')
    return data

# Type aliases
Vector = List[float]

def scale(vector: Vector, factor: float) -> Vector:
    return [x * factor for x in vector]

# Type hints for classes
class Person:
    def __init__(self, name: str, age: int) -> None:
        self.name = name
        self.age = age
    
    def greet(self) -> str:
        return f"Hello, my name is {self.name}"

# Type hints for callable objects
from typing import Callable

def apply_operation(x: int, y: int, operation: Callable[[int, int], int]) -> int:
    return operation(x, y)

def add(a: int, b: int) -> int:
    return a + b

result = apply_operation(5, 3, add)
print(result)  # 8

# Type hints for generators
from typing import Generator, Iterator, Iterable

def count_up_to(n: int) -> Generator[int, None, None]:
    i = 0
    while i < n:
        yield i
        i += 1

for num in count_up_to(5):
    print(num)  # 0, 1, 2, 3, 4

# Type hints for context managers
from typing import ContextManager
from contextlib import contextmanager

@contextmanager
def file_opener(filename: str) -> Generator[str, None, None]:
    file = open(filename, 'r')
    try:
        yield file.read()
    finally:
        file.close()

# Type hints with TypeVar (generic types)
from typing import TypeVar, Sequence

T = TypeVar('T')  # Declare a type variable

def first(seq: Sequence[T]) -> T:
    return seq[0]

first_int = first([1, 2, 3])  # Type: int
first_str = first(["a", "b", "c"])  # Type: str

# Type hints with Protocol (structural typing)
from typing import Protocol

class Drawable(Protocol):
    def draw(self) -> None:
        ...

def render(drawable: Drawable) -> None:
    drawable.draw()

class Circle:
    def draw(self) -> None:
        print("Drawing a circle")

class Square:
    def draw(self) -> None:
        print("Drawing a square")

render(Circle())  # Drawing a circle
render(Square())  # Drawing a square

# Type checking with mypy
"""
To check types with mypy, install it and run:
pip install mypy
mypy your_file.py
"""
```

### Abstract Base Classes (ABCs)

**What they are**: Abstract Base Classes (ABCs) provide a way to define interfaces in Python, specifying methods that must be implemented by subclasses.

**How they work**: The `abc` module provides the tools for defining ABCs. You can mark methods as abstract using the `@abstractmethod` decorator, forcing subclasses to implement them.

**Examples**:

```python
from abc import ABC, abstractmethod

# Basic abstract class
class Shape(ABC):
    @abstractmethod
    def area(self) -> float:
        """Calculate the area of the shape."""
        pass
    
    @abstractmethod
    def perimeter(self) -> float:
        """Calculate the perimeter of the shape."""
        pass
    
    def describe(self) -> str:
        """Return a description of the shape."""
        return f"A shape with area {self.area()} and perimeter {self.perimeter()}"

# Cannot instantiate abstract class
try:
    shape = Shape()  # This will raise TypeError
except TypeError as e:
    print(e)  # Can't instantiate abstract class Shape with abstract methods area, perimeter

# Concrete implementation
class Circle(Shape):
    def __init__(self, radius: float):
        self.radius = radius
    
    def area(self) -> float:
        import math
        return math.pi * self.radius ** 2
    
    def perimeter(self) -> float:
        import math
        return 2 * math.pi * self.radius

# Another concrete implementation
class Rectangle(Shape):
    def __init__(self, width: float, height: float):
        self.width = width
        self.height = height
    
    def area(self) -> float:
        return self.width * self.height
    
    def perimeter(self) -> float:
        return 2 * (self.width + self.height)

# Using the concrete implementations
circle = Circle(5)
print(circle.area())  # ~78.54
print(circle.describe())  # A shape with area ~78.54 and perimeter ~31.42

rectangle = Rectangle(4, 6)
print(rectangle.area())  # 24
print(rectangle.describe())  # A shape with area 24 and perimeter 20

# Abstract property
class AbstractWithProperty(ABC):
    @property
    @abstractmethod
    def readonly_property(self) -> str:
        pass
    
    @property
    @abstractmethod
    def readwrite_property(self) -> int:
        pass
    
    @readwrite_property.setter
    @abstractmethod
    def readwrite_property(self, value: int) -> None:
        pass

class ConcreteWithProperty(AbstractWithProperty):
    def __init__(self):
        self._value = 0
    
    @property
    def readonly_property(self) -> str:
        return "Read only"
    
    @property
    def readwrite_property(self) -> int:
        return self._value
    
    @readwrite_property.setter
    def readwrite_property(self, value: int) -> None:
        self._value = value

obj = ConcreteWithProperty()
print(obj.readonly_property)  # Read only
obj.readwrite_property = 42
print(obj.readwrite_property)  # 42

# Abstract class methods and static methods
class AbstractWithClassMethods(ABC):
    @classmethod
    @abstractmethod
    def from_string(cls, string: str):
        pass
    
    @staticmethod
    @abstractmethod
    def utility_method(value: int) -> int:
        pass

class ConcreteWithClassMethods(AbstractWithClassMethods):
    def __init__(self, value: int):
        self.value = value
    
    @classmethod
    def from_string(cls, string: str):
        return cls(int(string))
    
    @staticmethod
    def utility_method(value: int) -> int:
        return value * 2

obj = ConcreteWithClassMethods.from_string("42")
print(obj.value)  # 42
print(ConcreteWithClassMethods.utility_method(21))  # 42

# Using ABC for duck typing
from collections.abc import Iterable, Sequence, Mapping

def process_items(items: Iterable):
    for item in items:
        print(item)

process_items([1, 2, 3])  # Works with list
process_items((4, 5, 6))  # Works with tuple
process_items({"a", "b", "c"})  # Works with set

def get_first_item(items: Sequence):
    return items[0]

print(get_first_item([1, 2, 3]))  # 1
print(get_first_item((4, 5, 6)))  # 4
# print(get_first_item({"a", "b", "c"}))  # TypeError: 'set' object is not subscriptable

def get_value(mapping: Mapping, key: str):
    return mapping.get(key, "Not found")

print(get_value({"name": "Alice"}, "name"))  # Alice
print(get_value({"name": "Alice"}, "age"))   # Not found
```

## Python Development Tools

### Virtual Environments

**What they are**: Virtual environments are isolated Python environments that allow you to install packages without affecting the global Python installation.

**How they work**: They create a directory containing a copy of the Python interpreter and a separate site-packages directory for installing packages.

**Examples**:

```bash
# Creating a virtual environment using venv
python -m venv myenv

# Activating the virtual environment
# On Windows:
myenv\Scripts\activate
# On Unix or MacOS:
source myenv/bin/activate

# Deactivating the virtual environment
deactivate

# Installing packages in the virtual environment
pip install requests

# Listing installed packages
pip list

# Generating a requirements.txt file
pip freeze > requirements.txt

# Installing packages from requirements.txt
pip install -r requirements.txt

# Creating a virtual environment with specific Python version (using virtualenv)
# First, install virtualenv: pip install virtualenv
virtualenv -p python3.8 myenv38

# Creating a virtual environment with conda
# First, install conda: https://docs.conda.io/en/latest/miniconda.html
conda create --name myenv python=3.9
conda activate myenv
conda deactivate
```

### Pip and Package Management

**What it is**: Pip is the package installer for Python, used to install and manage packages from the Python Package Index (PyPI) and other sources.

**How it works**: Pip downloads packages from package repositories, resolves dependencies, and installs them to the current Python environment.

**Examples**:

```bash
# Basic installation
pip install package_name

# Installing a specific version
pip install package_name==1.2.3

# Installing the latest version in a specific range
pip install "package_name>=1.2.0,<2.0.0"

# Upgrading a package
pip install --upgrade package_name

# Uninstalling a package
pip uninstall package_name

# Listing installed packages
pip list

# Showing information about a package
pip show package_name

# Searching for packages
pip search query  # Note: this is currently disabled on PyPI

# Installing from a requirements file
pip install -r requirements.txt

# Creating a requirements file
pip freeze > requirements.txt

# Installing from version control
pip install git+https://github.com/user/project.git
pip install git+https://github.com/user/project.git@branch_or_tag

# Installing from a local directory
pip install ./local_package_directory

# Installing from a wheel file
pip install package_name-1.2.3-py3-none-any.whl

# Installing in development mode
pip install -e ./local_package_directory

# Installing with extra dependencies
pip install package_name[extra1,extra2]

# Installing without dependencies
pip install --no-deps package_name

# Downloading a package without installing
pip download package_name -d ./download_directory

# Building a wheel
pip wheel package_name -w ./wheel_directory

# Using a different package index
pip install --index-url https://alternative-pypi.org/simple package_name

# Adding an additional package index
pip install --extra-index-url https://additional-pypi.org/simple package_name

# Installing behind a proxy
pip install --proxy http://proxy.example.com:8080 package_name
```

### Testing with unittest

**What it is**: unittest is a built-in testing framework for Python, inspired by JUnit, that provides a rich set of tools for writing and running tests.

**How it works**: It provides a base class, TestCase, which you extend to create test cases. Methods whose names start with "test" are automatically run as tests.

**Examples**:

```python
import unittest

# Function to test
def add(a, b):
    return a + b

# Test case class
class TestAddFunction(unittest.TestCase):
    def test_add_positive_numbers(self):
        result = add(1, 2)
        self.assertEqual(result, 3)
    
    def test_add_negative_numbers(self):
        result = add(-1, -2)
        self.assertEqual(result, -3)
    
    def test_add_mixed_numbers(self):
        result = add(-1, 2)
        self.assertEqual(result, 1)

# Class to test
class Calculator:
    def __init__(self, initial_value=0):
        self.value = initial_value
    
    def add(self, number):
        self.value += number
        return self.value
    
    def subtract(self, number):
        self.value -= number
        return self.value

# Test case for a class
class TestCalculator(unittest.TestCase):
    def setUp(self):
        # This runs before each test
        self.calc = Calculator()
    
    def tearDown(self):
        # This runs after each test
        pass
    
    def test_initial_value(self):
        self.assertEqual(self.calc.value, 0)
    
    def test_add(self):
        self.calc.add(5)
        self.assertEqual(self.calc.value, 5)
    
    def test_subtract(self):
        self.calc.subtract(3)
        self.assertEqual(self.calc.value, -3)
    
    def test_chain_operations(self):
        self.calc.add(5).subtract(3)
        self.assertEqual(self.calc.value, 2)
    
    def test_with_initial_value(self):
        calc = Calculator(10)
        self.assertEqual(calc.value, 10)

# Using assertions
class TestAssertions(unittest.TestCase):
    def test_assertions(self):
        # Test equality
        self.assertEqual(1 + 1, 2)
        self.assertNotEqual(1 + 1, 3)
        
        # Test truth values
        self.assertTrue(1 < 2)
        self.assertFalse(1 > 2)
        
        # Test None and identity
        x = None
        self.assertIsNone(x)
        y = 1
        self.assertIsNotNone(y)
        
        # Test membership
        self.assertIn(1, [1, 2, 3])
        self.assertNotIn(4, [1, 2, 3])
        
        # Test exceptions
        with self.assertRaises(ZeroDivisionError):
            1 / 0
        
        # Test approximate equality
        self.assertAlmostEqual(0.1 + 0.2, 0.3, places=1)
        
        # Test greater/less
        self.assertGreater(2, 1)
        self.assertLess(1, 2)
        self.assertGreaterEqual(2, 2)
        self.assertLessEqual(2, 2)
        
        # Test regex
        self.assertRegex("hello world", r"h.*d")
        
        # Test sequences and collections
        self.assertSequenceEqual([1, 2, 3], [1, 2, 3])
        self.assertListEqual([1, 2, 3], [1, 2, 3])
        self.assertDictEqual({"a": 1}, {"a": 1})
        self.assertSetEqual({1, 2, 3}, {3, 2, 1})

# Skipping tests
class TestSkipping(unittest.TestCase):
    @unittest.skip("Demonstrating skipping")
    def test_skipped(self):
        self.fail("Should not run")
    
    @unittest.skipIf(1 < 2, "Condition is true")
    def test_skip_if(self):
        self.fail("Should not run if condition is true")
    
    @unittest.skipUnless(False, "Condition is false")
    def test_skip_unless(self):
        self.fail("Should not run unless condition is true")
    
    @unittest.expectedFailure
    def test_expected_failure(self):
        self.assertEqual(1, 2)  # This test is expected to fail

# Running tests
if __name__ == "__main__":
    unittest.main()
```

### Testing with pytest

**What it is**: pytest is a popular third-party testing framework for Python that is simpler to use than unittest and provides powerful features like fixtures and parameterized tests.

**How it works**: pytest automatically discovers and runs test functions or methods prefixed with "test_" and provides a rich set of assertions and fixtures.

**Examples**:

```python
# First, install pytest: pip install pytest

# Basic test function
def test_addition():
    assert 1 + 1 == 2

# Test function with exception checking
def test_division_by_zero():
    import pytest
    with pytest.raises(ZeroDivisionError):
        1 / 0

# Functions to test
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

# Test functions for the above
def test_add():
    assert add(1, 2) == 3
    assert add(-1, -2) == -3
    assert add(-1, 2) == 1

def test_subtract():
    assert subtract(5, 2) == 3
    assert subtract(2, 5) == -3

# Class to test
class Calculator:
    def __init__(self, initial_value=0):
        self.value = initial_value
    
    def add(self, number):
        self.value += number
        return self
    
    def subtract(self, number):
        self.value -= number
        return self

# Using fixtures
import pytest

@pytest.fixture
def calculator():
    return Calculator(0)

def test_calculator_initial_value(calculator):
    assert calculator.value == 0

def test_calculator_add(calculator):
    calculator.add(5)
    assert calculator.value == 5

def test_calculator_subtract(calculator):
    calculator.subtract(3)
    assert calculator.value == -3

def test_calculator_chain(calculator):
    calculator.add(5).subtract(3)
    assert calculator.value == 2

# Parameterized tests
@pytest.mark.parametrize("a,b,expected", [
    (1, 2, 3),
    (-1, -2, -3),
    (-1, 2, 1),
    (0, 0, 0)
])
def test_add_parametrized(a, b, expected):
    assert add(a, b) == expected

# Fixture with teardown
@pytest.fixture
def managed_resource():
    print("Setting up resource")
    resource = {"data": "valuable"}
    yield resource
    print("Tearing down resource")
    resource.clear()

def test_with_managed_resource(managed_resource):
    assert managed_resource["data"] == "valuable"

# Built-in fixtures
def test_with_tmp_path(tmp_path):
    file_path = tmp_path / "test.txt"
    file_path.write_text("Hello, World!")
    assert file_path.read_text() == "Hello, World!"

# Skipping tests
@pytest.mark.skip(reason="Demonstrating skipping")
def test_skipped():
    assert False

@pytest.mark.skipif(1 < 2, reason="Condition is true")
def test_skip_if():
    assert False

# Marking tests for selection
@pytest.mark.slow
def test_slow_operation():
    import time
    time.sleep(1)
    assert True

# To run only slow tests: pytest -m slow
# To skip slow tests: pytest -m "not slow"

# Expected failures
@pytest.mark.xfail
def test_expected_to_fail():
    assert 1 == 2

# Fixtures with scopes
@pytest.fixture(scope="module")
def module_fixture():
    print("Setting up module fixture")
    yield "module data"
    print("Tearing down module fixture")

def test_with_module_fixture_1(module_fixture):
    assert module_fixture == "module data"

def test_with_module_fixture_2(module_fixture):
    assert module_fixture == "module data"

# Running tests from the command line:
# Basic: pytest
# Verbose: pytest -v
# Specific file: pytest test_file.py
# Specific test: pytest test_file.py::test_function
# Specific package: pytest path/to/package
```

### Debugging

**What it is**: Debugging is the process of finding and fixing errors (bugs) in code.

**How it works**: Python provides various tools and techniques for debugging, from simple print statements to advanced debuggers.

**Examples**:

```python
# Basic debugging with print statements
def buggy_function(a, b):
    print(f"a = {a}, b = {b}")  # Print input values
    result = a / b
    print(f"result = {result}")  # Print output value
    return result

try:
    buggy_function(5, 0)
except Exception as e:
    print(f"
```