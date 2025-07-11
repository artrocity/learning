---
aliases:
  - "Part 3: Python Comprehensive Guide"
---
# Random Data Generation (continued)

**Examples (continued)**:

```python
import random

# Setting a seed for reproducibility
random.seed(42)

# Random floating-point number between 0 and 1
rand_float = random.random()
print(rand_float)  # 0.6394267984578837

# Random integer in a range (inclusive)
rand_int = random.randint(1, 10)
print(rand_int)  # 10

# Random element from a sequence
fruits = ["apple", "banana", "cherry", "date"]
random_fruit = random.choice(fruits)
print(random_fruit)  # "date"

# Random sample from a sequence (without replacement)
random_sample = random.sample(fruits, 2)
print(random_sample)  # ['cherry', 'banana']

# Shuffle a list in-place
cards = ["A", "K", "Q", "J", "10"]
random.shuffle(cards)
print(cards)  # ['Q', 'K', '10', 'A', 'J']

# Random floating-point number in a range
rand_uniform = random.uniform(1.5, 3.5)
print(rand_uniform)  # 2.5096361108532466

# Random selection from a weighted distribution
choices = random.choices(
    population=["win", "lose", "draw"],
    weights=[0.3, 0.6, 0.1],
    k=10
)
print(choices)  # ['lose', 'lose', 'lose', 'win', 'lose', 'win', 'lose', 'win', 'lose', 'lose']

# Gaussian (normal) distribution
rand_gauss = random.gauss(mu=0, sigma=1)
print(rand_gauss)  # -0.8394519156545516

# Random bytes
rand_bytes = random.randbytes(4)
print(rand_bytes)  # b'\x11\x1b\x82\xf4'

# Random bit generation
rand_bits = [random.getrandbits(1) for _ in range(10)]
print(rand_bits)  # [0, 1, 0, 0, 1, 0, 0, 0, 1, 1]

# For cryptographic applications, use secrets module instead
import secrets
token = secrets.token_hex(16)
print(token)  # '58e5a96eec8c3581952624c7e9e1c11a'
```

## Concurrency and Parallelism

### Threading

**What it is**: Threading is a technique for concurrent execution of code through threads, which are lighter weight than processes and share the same memory space.

**How it works**: Python's `threading` module provides a simple way to create and manage threads. Due to the Global Interpreter Lock (GIL), threads are most useful for I/O-bound tasks in Python.

**Examples**:

```python
import threading
import time

# Basic thread creation
def worker(name):
    print(f"Worker {name} starting")
    time.sleep(1)
    print(f"Worker {name} finished")

# Create and start threads
threads = []
for i in range(5):
    t = threading.Thread(target=worker, args=(i,))
    threads.append(t)
    t.start()

# Wait for all threads to complete
for t in threads:
    t.join()

print("All workers completed")

# Thread with a class
class WorkerThread(threading.Thread):
    def __init__(self, name):
        super().__init__()
        self.name = name
    
    def run(self):
        print(f"Worker {self.name} starting")
        time.sleep(1)
        print(f"Worker {self.name} finished")

# Create and start threads using the class
threads = []
for i in range(5):
    t = WorkerThread(i)
    threads.append(t)
    t.start()

# Wait for all threads to complete
for t in threads:
    t.join()

print("All class-based workers completed")

# Thread synchronization with Lock
counter = 0
counter_lock = threading.Lock()

def increment_counter():
    global counter
    for _ in range(100000):
        with counter_lock:  # Using lock as a context manager
            counter += 1

threads = []
for _ in range(5):
    t = threading.Thread(target=increment_counter)
    threads.append(t)
    t.start()

for t in threads:
    t.join()

print(f"Counter: {counter}")  # Should be 500000

# Thread synchronization with RLock (reentrant lock)
rlock = threading.RLock()

def outer_function():
    with rlock:
        print("Outer function acquired lock")
        inner_function()

def inner_function():
    with rlock:  # Same thread can acquire the lock again
        print("Inner function also acquired lock")

threading.Thread(target=outer_function).start()

# Using Event for thread communication
event = threading.Event()

def waiter():
    print("Waiter: Waiting for event")
    event.wait()  # Block until event is set
    print("Waiter: Event received, proceeding")

def setter():
    print("Setter: Sleeping before setting event")
    time.sleep(2)
    print("Setter: Setting event")
    event.set()  # Set the event, unblocking all waiters

waiter_thread = threading.Thread(target=waiter)
setter_thread = threading.Thread(target=setter)

waiter_thread.start()
setter_thread.start()

# Using Condition for producer-consumer pattern
queue = []
MAX_SIZE = 10
condition = threading.Condition()

def producer():
    global queue
    for i in range(20):
        with condition:
            while len(queue) >= MAX_SIZE:
                print("Producer: Queue full, waiting")
                condition.wait()
            queue.append(i)
            print(f"Producer: Added {i} to queue")
            condition.notify()  # Notify a waiting consumer
        time.sleep(0.1)

def consumer():
    global queue
    while True:
        with condition:
            while len(queue) == 0:
                print("Consumer: Queue empty, waiting")
                condition.wait()
            item = queue.pop(0)
            print(f"Consumer: Got {item} from queue")
            condition.notify()  # Notify a waiting producer
        time.sleep(0.2)

producer_thread = threading.Thread(target=producer)
consumer_thread = threading.Thread(target=consumer, daemon=True)  # Daemon thread
producer_thread.start()
consumer_thread.start()
producer_thread.join()  # Only wait for producer to finish

# Thread pool with concurrent.futures
from concurrent.futures import ThreadPoolExecutor
import urllib.request

def fetch_url(url):
    try:
        with urllib.request.urlopen(url) as response:
            return url, response.read().decode('utf-8')[:100]  # First 100 chars
    except Exception as e:
        return url, str(e)

urls = [
    'http://python.org',
    'http://www.google.com',
    'http://www.github.com'
]

with ThreadPoolExecutor(max_workers=3) as executor:
    results = executor.map(fetch_url, urls)
    for url, content in results:
        print(f"URL: {url}\nContent: {content}\n")
```

### Multiprocessing

**What it is**: Multiprocessing is a technique for parallel execution of code through processes, which have separate memory spaces.

**How it works**: Python's `multiprocessing` module provides an API similar to `threading`, but uses processes instead of threads, allowing true parallelism by bypassing the GIL.

**Examples**:

```python
import multiprocessing
import time
import os

# Basic process creation
def worker(name):
    print(f"Worker {name} starting, PID: {os.getpid()}")
    time.sleep(1)
    print(f"Worker {name} finished")

if __name__ == "__main__":  # Required for Windows
    # Create and start processes
    processes = []
    for i in range(5):
        p = multiprocessing.Process(target=worker, args=(i,))
        processes.append(p)
        p.start()
    
    # Wait for all processes to complete
    for p in processes:
        p.join()
    
    print("All workers completed")

# Process with a class
class WorkerProcess(multiprocessing.Process):
    def __init__(self, name):
        super().__init__()
        self.name = name
    
    def run(self):
        print(f"Worker {self.name} starting, PID: {os.getpid()}")
        time.sleep(1)
        print(f"Worker {self.name} finished")

if __name__ == "__main__":
    # Create and start processes using the class
    processes = []
    for i in range(5):
        p = WorkerProcess(i)
        processes.append(p)
        p.start()
    
    # Wait for all processes to complete
    for p in processes:
        p.join()
    
    print("All class-based workers completed")

# Sharing data between processes with a Queue
def producer(queue):
    for i in range(10):
        print(f"Producer: producing {i}")
        queue.put(i)
        time.sleep(0.1)
    queue.put(None)  # Sentinel value

def consumer(queue):
    while True:
        item = queue.get()
        if item is None:  # Sentinel value
            break
        print(f"Consumer: consuming {item}")
        time.sleep(0.2)

if __name__ == "__main__":
    queue = multiprocessing.Queue()
    prod_proc = multiprocessing.Process(target=producer, args=(queue,))
    cons_proc = multiprocessing.Process(target=consumer, args=(queue,))
    
    prod_proc.start()
    cons_proc.start()
    
    prod_proc.join()
    cons_proc.join()

# Sharing data with a Manager
def worker_shared_dict(d, key, value):
    d[key] = value

if __name__ == "__main__":
    with multiprocessing.Manager() as manager:
        shared_dict = manager.dict()
        processes = []
        
        for i in range(5):
            p = multiprocessing.Process(
                target=worker_shared_dict,
                args=(shared_dict, f"key{i}", i*i)
            )
            processes.append(p)
            p.start()
        
        for p in processes:
            p.join()
        
        print("Shared dictionary:", dict(shared_dict))

# Using Pool for map-reduce style processing
def calculate_square(n):
    return n * n

if __name__ == "__main__":
    with multiprocessing.Pool(processes=4) as pool:
        numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
        results = pool.map(calculate_square, numbers)
        print("Squares:", results)
        
        # Asynchronous version
        result_async = pool.map_async(calculate_square, numbers)
        print("Doing other work while calculating...")
        print("Results:", result_async.get())

# Process pool with concurrent.futures
from concurrent.futures import ProcessPoolExecutor
import math

def compute_factorial(n):
    return n, math.factorial(n)

if __name__ == "__main__":
    numbers = [5, 7, 10, 12, 15]
    with ProcessPoolExecutor(max_workers=3) as executor:
        results = executor.map(compute_factorial, numbers)
        for number, factorial in results:
            print(f"{number}! = {factorial}")
```

### Asyncio

**What it is**: Asyncio is a library for writing concurrent code using the `async`/`await` syntax.

**How it works**: It's a single-threaded, single-process design that uses cooperative multitasking with coroutines. It's ideal for I/O-bound and high-level structured network code.

**Examples**:

```python
import asyncio
import time

# Basic coroutine
async def say_hello():
    print("Hello")
    await asyncio.sleep(1)
    print("World")

# Run the coroutine
asyncio.run(say_hello())

# Multiple coroutines
async def print_after(message, delay):
    await asyncio.sleep(delay)
    print(message)

async def main():
    # Schedule tasks to run concurrently
    task1 = asyncio.create_task(print_after("First", 2))
    task2 = asyncio.create_task(print_after("Second", 1))
    task3 = asyncio.create_task(print_after("Third", 3))
    
    # Wait for all tasks to complete
    await asyncio.gather(task1, task2, task3)

asyncio.run(main())  # Second, First, Third (in order of completion)

# Waiting for multiple coroutines
async def main():
    # gather - run multiple coroutines concurrently and collect their results
    results = await asyncio.gather(
        print_after("One", 1),
        print_after("Two", 2),
        print_after("Three", 3)
    )
    print("All tasks completed")

asyncio.run(main())

# Timeouts
async def eternity():
    await asyncio.sleep(3600)  # Sleep for an hour
    print("Completed!")

async def main():
    try:
        # Wait for at most 1 second
        await asyncio.wait_for(eternity(), timeout=1.0)
    except asyncio.TimeoutError:
        print("Timeout!")

asyncio.run(main())  # Timeout!

# Handling coroutine cancellation
async def cancellable_task():
    try:
        while True:
            print("Working...")
            await asyncio.sleep(0.5)
    except asyncio.CancelledError:
        print("Task was cancelled")
        raise  # Re-raise to propagate cancellation

async def main():
    task = asyncio.create_task(cancellable_task())
    await asyncio.sleep(2)  # Let it run for 2 seconds
    task.cancel()  # Cancel the task
    try:
        await task  # Wait for the task to be cancelled
    except asyncio.CancelledError:
        print("Main: task is cancelled")

asyncio.run(main())

# Producer-consumer pattern with asyncio
async def producer(queue):
    for i in range(10):
        print(f"Producing {i}")
        await queue.put(i)
        await asyncio.sleep(0.1)
    await queue.put(None)  # Sentinel value

async def consumer(queue):
    while True:
        item = await queue.get()
        if item is None:  # Sentinel value
            break
        print(f"Consuming {item}")
        queue.task_done()
        await asyncio.sleep(0.2)

async def main():
    queue = asyncio.Queue()
    producer_task = asyncio.create_task(producer(queue))
    consumer_task = asyncio.create_task(consumer(queue))
    await asyncio.gather(producer_task, consumer_task)

asyncio.run(main())

# Running blocking code with executors
import concurrent.futures

def blocking_io():
    time.sleep(1)  # This would block the event loop if not in an executor
    return "Result from blocking I/O"

async def main():
    print("Starting")
    
    # Use a thread pool executor for I/O-bound blocking code
    with concurrent.futures.ThreadPoolExecutor() as executor:
        result = await asyncio.get_event_loop().run_in_executor(
            executor, blocking_io
        )
        print(result)
    
    # Use a process pool executor for CPU-bound blocking code
    with concurrent.futures.ProcessPoolExecutor() as executor:
        result = await asyncio.get_event_loop().run_in_executor(
            executor, blocking_io
        )
        print(result)
    
    print("Finished")

asyncio.run(main())

# Working with streams (TCP echo server and client)
async def handle_echo(reader, writer):
    data = await reader.read(100)
    message = data.decode()
    addr = writer.get_extra_info('peername')
    
    print(f"Received {message} from {addr}")
    
    print(f"Send: {message}")
    writer.write(data)
    await writer.drain()
    
    print("Close the connection")
    writer.close()
    await writer.wait_closed()

async def main():
    server = await asyncio.start_server(
        handle_echo, '127.0.0.1', 8888
    )
    
    addr = server.sockets[0].getsockname()
    print(f'Serving on {addr}')
    
    async with server:
        await server.serve_forever()

# asyncio.run(main())  # Uncomment to run the server

# TCP client
async def tcp_echo_client():
    reader, writer = await asyncio.open_connection(
        '127.0.0.1', 8888)
    
    message = 'Hello World!'
    print(f'Send: {message}')
    writer.write(message.encode())
    await writer.drain()
    
    data = await reader.read(100)
    print(f'Received: {data.decode()}')
    
    print('Close the connection')
    writer.close()
    await writer.wait_closed()

# asyncio.run(tcp_echo_client())  # Uncomment to run the client
```

### Global Interpreter Lock (GIL)

**What it is**: The Global Interpreter Lock (GIL) is a mutex that protects access to Python objects, preventing multiple threads from executing Python bytecode at once.

**How it works**: The GIL ensures that only one thread can execute Python code at a time, regardless of how many CPU cores are available. It's released during I/O operations.

**Examples**:

```python
import threading
import time
import multiprocessing

# CPU-bound task (limited by GIL)
def cpu_bound_task(n):
    """Compute the sum of squares of numbers from 0 to n-1."""
    total = 0
    for i in range(n):
        total += i * i
    return total

# Single-threaded execution
def single_threaded(n_tasks, numbers):
    start = time.time()
    results = []
    for _ in range(n_tasks):
        for n in numbers:
            results.append(cpu_bound_task(n))
    end = time.time()
    return end - start

# Multi-threaded execution
def multi_threaded(n_threads, n_tasks, numbers):
    start = time.time()
    
    def worker():
        for n in numbers:
            cpu_bound_task(n)
    
    threads = []
    for _ in range(n_threads):
        t = threading.Thread(target=worker)
        threads.append(t)
        t.start()
    
    for t in threads:
        t.join()
    
    end = time.time()
    return end - start

# Multi-process execution
def multi_process(n_processes, n_tasks, numbers):
    start = time.time()
    
    def worker():
        for n in numbers:
            cpu_bound_task(n)
    
    processes = []
    for _ in range(n_processes):
        p = multiprocessing.Process(target=worker)
        processes.append(p)
        p.start()
    
    for p in processes:
        p.join()
    
    end = time.time()
    return end - start

if __name__ == "__main__":
    n_tasks = 2
    numbers = [10000000, 20000000]
    n_workers = 2
    
    single_time = single_threaded(n_tasks, numbers)
    print(f"Single-threaded time: {single_time:.2f} seconds")
    
    multi_thread_time = multi_threaded(n_workers, n_tasks, numbers)
    print(f"Multi-threaded time: {multi_thread_time:.2f} seconds")
    
    multi_process_time = multi_process(n_workers, n_tasks, numbers)
    print(f"Multi-process time: {multi_process_time:.2f} seconds")
    
    print(f"Threading speedup: {single_time / multi_thread_time:.2f}x")
    print(f"Multiprocessing speedup: {single_time / multi_process_time:.2f}x")
    
    # Results will show that multi-threading doesn't provide much speedup for CPU-bound tasks
    # due to the GIL, while multiprocessing does provide a speedup proportional to the number of CPU cores.
    
    # I/O-bound task (not limited by GIL)
    def io_bound_task():
        """Simulate an I/O-bound task."""
        time.sleep(1)  # GIL is released during I/O operations
    
    def io_single_threaded(n_tasks):
        start = time.time()
        for _ in range(n_tasks):
            io_bound_task()
        end = time.time()
        return end - start
    
    def io_multi_threaded(n_tasks):
        start = time.time()
        
        threads = []
        for _ in range(n_tasks):
            t = threading.Thread(target=io_bound_task)
            threads.append(t)
            t.start()
        
        for t in threads:
            t.join()
        
        end = time.time()
        return end - start
    
    n_io_tasks = 5
    
    io_single_time = io_single_threaded(n_io_tasks)
    print(f"I/O Single-threaded time: {io_single_time:.2f} seconds")
    
    io_multi_thread_time = io_multi_threaded(n_io_tasks)
    print(f"I/O Multi-threaded time: {io_multi_thread_time:.2f} seconds")
    
    print(f"I/O Threading speedup: {io_single_time / io_multi_thread_time:.2f}x")
    
    # Results will show that multi-threading provides significant speedup for I/O-bound tasks
    # because the GIL is released during I/O operations.
```

## Advanced Python Concepts

### Metaclasses

**What they are**: Metaclasses are classes that define how other classes should be created.

**How they work**: A metaclass is a class of a class - it defines how a class behaves. By customizing metaclasses, you can modify the behavior of class creation.

**Examples**:

```python
# Basic metaclass usage
class Meta(type):
    def __new__(cls, name, bases, attrs):
        print(f"Creating class: {name}")
        attrs['added_by_meta'] = 42  # Add a new attribute to the class
        return super().__new__(cls, name, bases, attrs)

class MyClass(metaclass=Meta):
    def __init__(self, value):
        self.value = value

obj = MyClass(10)
print(obj.added_by_meta)  # 42

# Singleton pattern using metaclass
class SingletonMeta(type):
    _instances = {}
    
    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            cls._instances[cls] = super().__call__(*args, **kwargs)
        return cls._instances[cls]

class Singleton(metaclass=SingletonMeta):
    def __init__(self, value):
        self.value = value

s1 = Singleton(1)
s2 = Singleton(2)
print(s1 is s2)  # True
print(s1.value)  # 1 (not 2, because s2 reuses the instance created by s1)

# Registry pattern using metaclass
class PluginMeta(type):
    plugins = {}
    
    def __new__(cls, name, bases, attrs):
        new_cls = super().__new__(cls, name, bases, attrs)
        
        # Don't register the base class
        if name != 'Plugin':
            cls.plugins[name] = new_cls
        
        return new_cls

class Plugin(metaclass=PluginMeta):
    def process(self, data):
        raise NotImplementedError

class TextPlugin(Plugin):
    def process(self, data):
        return f"Text processing: {data.upper()}"

class NumberPlugin(Plugin):
    def process(self, data):
        return f"Number processing: {data * 2}"

# Access registered plugins
print(PluginMeta.plugins)  # {'TextPlugin': <class '__main__.TextPlugin'>, 'NumberPlugin': <class '__main__.NumberPlugin'>}
text_plugin = PluginMeta.plugins['TextPlugin']()
print(text_plugin.process("hello"))  # Text processing: HELLO

# Attribute validation using metaclass
class ValidatorMeta(type):
    def __new__(cls, name, bases, attrs):
        for key, value in attrs.items():
            if key.startswith('_'):  # Skip private attributes
                continue
            
            if hasattr(value, '__call__'):  # Skip methods
                continue
            
            attrs[key] = property(
                fget=lambda self, attr_name=key: getattr(self, f"_{attr_name}"),
                fset=lambda self, value, attr_name=key: setattr(
                    self,
                    f"_{attr_name}",
                    value if value > 0 else 0
                )
            )
        
        return super().__new__(cls, name, bases, attrs)

class PositiveNumbers(metaclass=ValidatorMeta):
    x = 10
    y = -5  # Will be set to 0 through the property setter

obj = PositiveNumbers()
print(obj.x)  # 10
print(obj.y)  # 0

obj.x = -10
print(obj.x)  # 0
```

### Descriptors

**What they are**: Descriptors are objects that define how attribute access on other objects should behave (get, set, delete).

**How they work**: A descriptor is any object that implements at least one of the methods `__get__`, `__set__`, or `__delete__`. These methods are called when the attribute is accessed on an instance.

**Examples**:

```python
# Basic descriptor
class Descriptor:
    def __get__(self, instance, owner):
        print(f"Getting from {instance} with {owner}")
        return instance._value if instance else None
    
    def __set__(self, instance, value):
        print(f"Setting {value} on {instance}")
        instance._value = value
    
    def __delete__(self, instance):
        print(f"Deleting from {instance}")
        del instance._value

class MyClass:
    attr = Descriptor()  # Class-level descriptor
    
    def __init__(self, value):
        self.attr = value  # Calls __set__

obj = MyClass(42)
print(obj.attr)  # Calls __get__, prints 42
obj.attr = 100   # Calls __set__
del obj.attr     # Calls __delete__

# Type validation descriptor
class TypeValidated:
    def __init__(self, name, expected_type):
        self.name = name
        self.expected_type = expected_type
    
    def __get__(self, instance, owner):
        if instance is None:
            return self
        return instance.__dict__.get(self.name, None)
    
    def __set__(self, instance, value):
        if not isinstance(value, self.expected_type):
            raise TypeError(f"Expected {self.expected_type}, got {type(value)}")
        instance.__dict__[self.name] = value

class Person:
    name = TypeValidated('name', str)
    age = TypeValidated('age', int)
    
    def __init__(self, name, age):
        self.name = name
        self.age = age

person = Person("John", 30)
print(person.name)  # John
print(person.age)   # 30

try:
    person.age = "thirty"  # Error: Expected <class 'int'>, got <class 'str'>
except TypeError as e:
    print(e)

# Lazy property descriptor
class LazyProperty:
    def __init__(self, function):
        self.function = function
        self.name = function.__name__
    
    def __get__(self, instance, owner):
        if instance is None:
            return self
        
        value = self.function(instance)
        instance.__dict__[self.name] = value  # Cache the result
        return value

class DataProcessor:
    def __init__(self, data):
        self.data = data
    
    @LazyProperty
    def processed_data(self):
        print("Processing data...")
        # Simulate expensive processing
        import time
        time.sleep(1)
        return [x * 2 for x in self.data]

processor = DataProcessor([1, 2, 3, 4, 5])
print("Processor created")

# First access - will process and cache
print(processor.processed_data)  # Prints "Processing data..." and [2, 4, 6, 8, 10]

# Subsequent access - uses cached value
print(processor.processed_data)  # Just prints [2, 4, 6, 8, 10] without "Processing data..."

# Property descriptor
class Property:
    def __init__(self, fget=None, fset=None, fdel=None, doc=None):
        self.fget = fget
        self.fset = fset
        self.fdel = fdel
        self.__doc__ = doc
    
    def __get__(self, instance, owner):
        if instance is None:
            return self
        if self.fget is None:
            raise AttributeError("unreadable attribute")
        return self.fget(instance)
    
    def __set__(self, instance, value):
        if self.fset is None:
            raise AttributeError("can't set attribute")
        self.fset(instance, value)
    
    def __delete__(self, instance):
        if self.fdel is None:
            raise AttributeError("can't delete attribute")
        self.fdel(instance)
    
    def getter(self, fget):
        return type(self)(fget, self.fset, self.fdel, self.__doc__)
    
    def setter(self, fset):
        return type(self)(self.fget, fset, self.fdel, self.__doc__)
    
    def deleter(self, fdel):
        return type(self)(self.fget, self.fset, fdel, self.__doc__)

# Using our custom Property descriptor
class Temperature:
    def __init__(self, celsius=0):
        self._celsius = celsius
    
    def get_celsius(self):
        return self._celsius
    
    def set_celsius(self, value):
        if value < -273.15:
            raise ValueError("Temperature below absolute zero")
        self._celsius = value
    
    def del_celsius(self):
        raise AttributeError("Cannot delete temperature")
    
    celsius = Property(get_celsius, set_celsius, del_celsius)

temp = Temperature(25)
print(temp.celsius)  # 25
temp.celsius = 30
print(temp.celsius)  # 30

try:
    temp.celsius = -300  # ValueError: Temperature below absolute zero
except ValueError as e:
    print(e)
```

### Method Resolution Order (MRO)

**What it is**: Method Resolution Order (MRO) is the order in which Python looks for methods and attributes in a hierarchy of classes.

**How it works**: Python uses the C3 linearization algorithm to determine the MRO, which ensures that a