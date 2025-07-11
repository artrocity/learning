---
aliases:
  - "Part 3: Python Comprehensive Guide"
---
# Dynamic Programming (continued)

**Examples (continued)**:

```python
# Coin Change Problem (number of ways to make change)
def count_ways(coins, amount):
    dp = [0] * (amount + 1)
    dp[0] = 1  # Base case: 1 way to make amount 0
    
    for coin in coins:
        for i in range(coin, amount + 1):
            dp[i] += dp[i - coin]
    
    return dp[amount]

# Longest Increasing Subsequence (LIS)
def longest_increasing_subsequence(nums):
    if not nums:
        return 0
    
    n = len(nums)
    dp = [1] * n  # Each number by itself is a subsequence of length 1
    
    for i in range(1, n):
        for j in range(i):
            if nums[i] > nums[j]:
                dp[i] = max(dp[i], dp[j] + 1)
    
    return max(dp)

# Matrix Chain Multiplication
def matrix_chain_multiplication(dimensions):
    n = len(dimensions) - 1  # Number of matrices
    
    # Create a table to store the minimum number of multiplications
    dp = [[0] * n for _ in range(n)]
    
    # Fill the table in a bottom-up manner
    for length in range(2, n + 1):
        for i in range(n - length + 1):
            j = i + length - 1
            dp[i][j] = float('infinity')
            for k in range(i, j):
                cost = dp[i][k] + dp[k+1][j] + dimensions[i] * dimensions[k+1] * dimensions[j+1]
                dp[i][j] = min(dp[i][j], cost)
    
    return dp[0][n-1]

# Edit Distance (Levenshtein Distance)
def edit_distance(s1, s2):
    m, n = len(s1), len(s2)
    
    # Create a table to store the minimum edit distance
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    
    # Fill the first row and column
    for i in range(m + 1):
        dp[i][0] = i
    for j in range(n + 1):
        dp[0][j] = j
    
    # Fill the table in a bottom-up manner
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if s1[i-1] == s2[j-1]:
                dp[i][j] = dp[i-1][j-1]
            else:
                dp[i][j] = 1 + min(dp[i-1][j],      # Delete
                                   dp[i][j-1],      # Insert
                                   dp[i-1][j-1])     # Substitute
    
    return dp[m][n]

# Longest Palindromic Subsequence
def longest_palindromic_subsequence(s):
    n = len(s)
    
    # Create a table to store the length of the LPS
    dp = [[0] * n for _ in range(n)]
    
    # All substrings of length 1 are palindromes
    for i in range(n):
        dp[i][i] = 1
    
    # Fill the table in a bottom-up manner
    for length in range(2, n + 1):
        for i in range(n - length + 1):
            j = i + length - 1
            if s[i] == s[j] and length == 2:
                dp[i][j] = 2
            elif s[i] == s[j]:
                dp[i][j] = dp[i+1][j-1] + 2
            else:
                dp[i][j] = max(dp[i+1][j], dp[i][j-1])
    
    return dp[0][n-1]

# Rod Cutting Problem
def rod_cutting(prices, n):
    # Create a table to store the maximum value for each length
    dp = [0] * (n + 1)
    
    # Fill the table in a bottom-up manner
    for i in range(1, n + 1):
        max_val = float('-infinity')
        for j in range(i):
            max_val = max(max_val, prices[j] + dp[i - j - 1])
        dp[i] = max_val
    
    return dp[n]

# Subset Sum Problem
def subset_sum(nums, target_sum):
    n = len(nums)
    
    # Create a table to store whether a sum is possible
    dp = [[False] * (target_sum + 1) for _ in range(n + 1)]
    
    # If the target sum is 0, an empty subset can achieve it
    for i in range(n + 1):
        dp[i][0] = True
    
    # Fill the table in a bottom-up manner
    for i in range(1, n + 1):
        for j in range(1, target_sum + 1):
            if nums[i-1] <= j:
                dp[i][j] = dp[i-1][j] or dp[i-1][j-nums[i-1]]
            else:
                dp[i][j] = dp[i-1][j]
    
    return dp[n][target_sum]

# Example usage
print(fibonacci_memo(10))  # 55
print(fibonacci_tabulation(10))  # 55

print(longest_common_subsequence("ABCBDAB", "BDCABA"))  # "BCBA"

weights = [2, 3, 4, 5]
values = [3, 4, 5, 6]
capacity = 8
max_value, selected_items = knapsack(weights, values, capacity)
print(f"Maximum value: {max_value}")  # 9
print(f"Selected items: {selected_items}")  # [3, 1]

coins = [1, 2, 5]
amount = 11
print(f"Minimum coins needed: {min_coins(coins, amount)}")  # 3
print(f"Number of ways to make change: {count_ways(coins, amount)}")  # 11

nums = [10, 22, 9, 33, 21, 50, 41, 60]
print(f"Length of longest increasing subsequence: {longest_increasing_subsequence(nums)}")  # 5
```

## Performance and Optimization

### Time and Space Complexity

**What they are**: Time complexity measures how an algorithm's runtime grows relative to the size of the input, while space complexity measures how much memory an algorithm uses relative to the input size.

**How they work**: Complexities are usually expressed using Big O notation, which describes the upper bound of the growth rate.

**Examples**:

```python
# O(1) - Constant time complexity
def constant_time(arr):
    return arr[0] if arr else None

# O(log n) - Logarithmic time complexity
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

# O(n) - Linear time complexity
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1

# O(n log n) - Linearithmic time complexity
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    
    return merge(left, right)

def merge(left, right):
    result = []
    i = j = 0
    
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    
    result.extend(left[i:])
    result.extend(right[j:])
    return result

# O(n^2) - Quadratic time complexity
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
    return arr

# O(2^n) - Exponential time complexity
def fibonacci_recursive(n):
    if n <= 1:
        return n
    return fibonacci_recursive(n-1) + fibonacci_recursive(n-2)

# Space complexity examples

# O(1) - Constant space complexity
def sum_array(arr):
    total = 0
    for num in arr:
        total += num
    return total

# O(n) - Linear space complexity
def duplicate_array(arr):
    return arr.copy()

# O(n^2) - Quadratic space complexity
def create_matrix(n):
    return [[0] * n for _ in range(n)]

# Time complexity analysis
import time

def measure_time(func, *args):
    start_time = time.time()
    result = func(*args)
    end_time = time.time()
    print(f"{func.__name__} took {end_time - start_time:.6f} seconds")
    return result

# Example measurement
numbers = list(range(10000))
sorted_numbers = sorted(numbers)
measure_time(linear_search, sorted_numbers, 9999)  # O(n)
measure_time(binary_search, sorted_numbers, 9999)  # O(log n)
```

### Code Profiling

**What it is**: Code profiling is the process of analyzing the performance of your code to identify bottlenecks and areas for optimization.

**How it works**: Python provides built-in profiling modules like `cProfile` and `profile`, as well as third-party tools like `line_profiler` and `memory_profiler`.

**Examples**:

```python
# Using cProfile
import cProfile

def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

# Profile the function
cProfile.run('fibonacci(30)')

# Profile a specific function call
def profile_function():
    fibonacci(30)

cProfile.run('profile_function()')

# Save profiling results to a file
cProfile.run('fibonacci(30)', 'fibonacci_profile')

# Analyze saved profiling results
import pstats
p = pstats.Stats('fibonacci_profile')
p.strip_dirs().sort_stats('cumulative').print_stats(10)  # Show top 10 functions

# Using the timeit module for benchmarking
import timeit

# Measure the execution time of a small code snippet
execution_time = timeit.timeit('"-".join(str(n) for n in range(100))', number=10000)
print(f"Execution time: {execution_time} seconds")

# Compare different implementations
list_creation_time = timeit.timeit('[i for i in range(1000)]', number=1000)
print(f"List comprehension: {list_creation_time} seconds")

generator_creation_time = timeit.timeit('list(i for i in range(1000))', number=1000)
print(f"Generator expression: {generator_creation_time} seconds")

# Using a timer context manager
import time
import contextlib

@contextlib.contextmanager
def timer(name):
    start_time = time.time()
    yield
    end_time = time.time()
    print(f"{name} took {end_time - start_time:.6f} seconds")

with timer("Fibonacci calculation"):
    fibonacci(30)

# Using line_profiler for line-by-line profiling
# First, install line_profiler: pip install line_profiler
# Then, use the @profile decorator and run with kernprof
"""
@profile
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

# Run with: kernprof -l script.py
# View results with: python -m line_profiler script.py.lprof
"""

# Using memory_profiler for memory usage profiling
# First, install memory_profiler: pip install memory_profiler
# Then, use the @profile decorator
"""
@profile
def create_large_list():
    return [i for i in range(1000000)]

# Run with: python -m memory_profiler script.py
"""
```

### Performance Optimization Techniques

**What they are**: Techniques to make Python code run faster or use less memory.

**How they work**: These techniques include choosing appropriate data structures, avoiding unnecessary computations, and leveraging Python's optimized functions.

**Examples**:

```python
# 1. Use appropriate data structures

# Inefficient: list for membership test
def contains_inefficient(value, collection):
    return value in collection  # O(n) for lists

# Efficient: set for membership test
def contains_efficient(value, collection_set):
    return value in collection_set  # O(1) for sets

# 2. Avoid unnecessary computations

# Inefficient: compute in loop
def sum_squares_inefficient(n):
    total = 0
    for i in range(n):
        total += i ** 2
    return total

# Efficient: move computations out of loops
def sum_squares_efficient(n):
    return sum(i ** 2 for i in range(n))

# 3. Use list comprehensions instead of loops for building lists

# Inefficient: building list with append
def build_squares_inefficient(n):
    squares = []
    for i in range(n):
        squares.append(i ** 2)
    return squares

# Efficient: using list comprehension
def build_squares_efficient(n):
    return [i ** 2 for i in range(n)]

# 4. Use generator expressions for iteration

# Inefficient: creating a full list in memory
def process_inefficient(n):
    for i in [x ** 2 for x in range(n)]:
        print(i)

# Efficient: using generator expression
def process_efficient(n):
    for i in (x ** 2 for x in range(n)):
        print(i)

# 5. Use built-in functions and libraries

# Inefficient: manual implementation
def sum_manual(arr):
    total = 0
    for num in arr:
        total += num
    return total

# Efficient: using built-in function
def sum_builtin(arr):
    return sum(arr)

# 6. Use local variables over globals

global_var = 10

def use_global_inefficient():
    total = 0
    for i in range(1000000):
        total += global_var
    return total

def use_local_efficient():
    total = 0
    local_var = 10
    for i in range(1000000):
        total += local_var
    return total

# 7. Use join() for string concatenation

# Inefficient: string concatenation with +
def concatenate_inefficient(strings):
    result = ""
    for s in strings:
        result += s
    return result

# Efficient: using join()
def concatenate_efficient(strings):
    return "".join(strings)

# 8. Use defaultdict instead of checking for key existence

from collections import defaultdict

# Inefficient: checking if key exists
def count_words_inefficient(words):
    counts = {}
    for word in words:
        if word not in counts:
            counts[word] = 0
        counts[word] += 1
    return counts

# Efficient: using defaultdict
def count_words_efficient(words):
    counts = defaultdict(int)
    for word in words:
        counts[word] += 1
    return counts

# 9. Use functools.lru_cache for memoization

from functools import lru_cache

# Inefficient: no memoization
def fibonacci_inefficient(n):
    if n <= 1:
        return n
    return fibonacci_inefficient(n-1) + fibonacci_inefficient(n-2)

# Efficient: using lru_cache
@lru_cache(maxsize=None)
def fibonacci_efficient(n):
    if n <= 1:
        return n
    return fibonacci_efficient(n-1) + fibonacci_efficient(n-2)

# 10. Use NumPy for numerical computations

import numpy as np

# Inefficient: using plain Python
def matrix_multiply_inefficient(a, b):
    c = [[0 for _ in range(len(b[0]))] for _ in range(len(a))]
    for i in range(len(a)):
        for j in range(len(b[0])):
            for k in range(len(b)):
                c[i][j] += a[i][k] * b[k][j]
    return c

# Efficient: using NumPy
def matrix_multiply_efficient(a, b):
    return np.matmul(np.array(a), np.array(b))

# 11. Avoid creating unnecessary temporary objects

# Inefficient: creates temporary list
def sum_of_squares_inefficient(n):
    return sum([i ** 2 for i in range(n)])

# Efficient: uses generator expression
def sum_of_squares_efficient(n):
    return sum(i ** 2 for i in range(n))

# 12. Use map() or comprehensions instead of for loops

# Inefficient: using a for loop
def square_all_inefficient(numbers):
    result = []
    for n in numbers:
        result.append(n ** 2)
    return result

# Efficient: using map()
def square_all_efficient_map(numbers):
    return list(map(lambda x: x ** 2, numbers))

# Efficient: using list comprehension
def square_all_efficient_comprehension(numbers):
    return [n ** 2 for n in numbers]

# 13. Use islice for working with a portion of an iterable

from itertools import islice

# Inefficient: creates a full list in memory
def process_first_n_inefficient(iterable, n):
    return list(iterable)[:n]

# Efficient: uses islice
def process_first_n_efficient(iterable, n):
    return list(islice(iterable, n))

# 14. Use Counter for counting occurrences

from collections import Counter

# Inefficient: manual counting
def most_common_inefficient(items):
    counts = {}
    for item in items:
        if item not in counts:
            counts[item] = 0
        counts[item] += 1
    return max(counts.items(), key=lambda x: x[1])

# Efficient: using Counter
def most_common_efficient(items):
    counts = Counter(items)
    return counts.most_common(1)[0]

# 15. Use sets for removing duplicates

# Inefficient: manual removal
def unique_inefficient(items):
    result = []
    for item in items:
        if item not in result:
            result.append(item)
    return result

# Efficient: using set
def unique_efficient(items):
    return list(set(items))
```

### Caching and Memoization

**What they are**: Caching and memoization are techniques to store the results of expensive function calls and reuse them when the same inputs occur again.

**How they work**: The function's results are stored in a cache (usually a dictionary), and when the function is called again with the same inputs, the cached result is returned instead of recalculating.

**Examples**:

```python
# Manual memoization
def fibonacci_with_memo(n, memo={}):
    if n in memo:
        return memo[n]
    if n <= 1:
        return n
    memo[n] = fibonacci_with_memo(n-1, memo) + fibonacci_with_memo(n-2, memo)
    return memo[n]

# Using functools.lru_cache
import functools

@functools.lru_cache(maxsize=None)
def fibonacci_lru(n):
    if n <= 1:
        return n
    return fibonacci_lru(n-1) + fibonacci_lru(n-2)

# Using functools.cached_property (Python 3.8+)
class Circle:
    def __init__(self, radius):
        self.radius = radius
    
    @functools.cached_property
    def area(self):
        import math
        return math.pi * self.radius ** 2

# Creating a decorator for memoization
def memoize(func):
    cache = {}
    
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        # Create a key from the function arguments
        key = str(args) + str(kwargs)
        
        if key not in cache:
            cache[key] = func(*args, **kwargs)
        
        return cache[key]
    
    return wrapper

@memoize
def expensive_function(a, b):
    print(f"Computing {a} + {b}")
    return a + b

# Using @functools.cache (Python 3.9+)
@functools.cache
def factorial(n):
    return n * factorial(n-1) if n else 1

# Memoization with timeout (for time-sensitive caching)
import time

def memoize_with_timeout(timeout_seconds):
    def decorator(func):
        cache = {}
        
        @functools.wraps(func)
        def wrapper(*args, **kwargs):
            key = str(args) + str(kwargs)
            current_time = time.time()
            
            if key in cache:
                result, timestamp = cache[key]
                if current_time - timestamp < timeout_seconds:
                    return result
            
            result = func(*args, **kwargs)
            cache[key] = (result, current_time)
            return result
        
        return wrapper
    
    return decorator

@memoize_with_timeout(10)  # Cache results for 10 seconds
def get_weather(city):
    print(f"Fetching weather for {city}")
    # Simulating an API call
    return f"Sunny, 25°C in {city}"

# Example usage
print(fibonacci_with_memo(30))  # Fast due to memoization
print(fibonacci_lru(30))        # Fast due to LRU cache

circle = Circle(5)
print(circle.area)  # Calculated and cached
print(circle.area)  # Retrieved from cache

print(expensive_function(2, 3))  # Computing 2 + 3
print(expensive_function(2, 3))  # Uses cached result

print(factorial(10))  # Computed and cached
print(factorial(10))  # Retrieved from cache

print(get_weather("New York"))  # Fetching weather for New York
print(get_weather("New York"))  # Uses cached result (within timeout)
```

### Parallelization and Optimization

**What they are**: Techniques to make Python code faster by utilizing multiple processors or optimizing computation-intensive tasks.

**How they work**: Parallelization involves running multiple tasks simultaneously, while optimization involves improving the efficiency of individual tasks.

**Examples**:

```python
# Using concurrent.futures for parallelization
import concurrent.futures
import time

def cpu_bound_task(n):
    """A CPU-bound task that computes the sum of squares."""
    return sum(i * i for i in range(n))

def run_sequential(numbers):
    start = time.time()
    results = [cpu_bound_task(n) for n in numbers]
    end = time.time()
    print(f"Sequential execution took {end - start:.2f} seconds")
    return results

def run_parallel_process_pool(numbers):
    start = time.time()
    with concurrent.futures.ProcessPoolExecutor() as executor:
        results = list(executor.map(cpu_bound_task, numbers))
    end = time.time()
    print(f"Parallel execution with ProcessPoolExecutor took {end - start:.2f} seconds")
    return results

# Example usage
numbers = [10000000] * 8  # 8 tasks with 10 million iterations each
sequential_results = run_sequential(numbers)
parallel_results = run_parallel_process_pool(numbers)

# Using NumPy for vectorized operations
import numpy as np

def sum_squares_pure_python(n):
    return sum(i * i for i in range(n))

def sum_squares_numpy(n):
    return np.sum(np.arange(n) ** 2)

# Benchmark
start = time.time()
result_python = sum_squares_pure_python(10000000)
end_python = time.time()
print(f"Pure Python: {end_python - start:.2f} seconds")

start = time.time()
result_numpy = sum_squares_numpy(10000000)
end_numpy = time.time()
print(f"NumPy: {end_numpy - start:.2f} seconds")

# Using Numba for JIT compilation
from numba import jit

@jit(nopython=True)
def sum_squares_numba(n):
    total = 0
    for i in range(n):
        total += i * i
    return total

start = time.time()
result_numba = sum_squares_numba(10000000)
end_numba = time.time()
print(f"Numba: {end_numba - start:.2f} seconds")

# Using multiprocessing directly
import multiprocessing

def worker(n):
    return cpu_bound_task(n)

def run_multiprocessing(numbers):
    start = time.time()
    with multiprocessing.Pool() as pool:
        results = pool.map(worker, numbers)
    end = time.time()
    print(f"Multiprocessing took {end - start:.2f} seconds")
    return results

multiprocessing_results = run_multiprocessing(numbers)

# Using Cython for C-level performance
"""
# In file: sum_squares.pyx
def sum_squares_cython(int n):
    cdef long long total = 0
    cdef int i
    for i in range(n):
        total += i * i
    return total
"""

# Cython setup: python setup.py build_ext --inplace
"""
# In file: setup.py
from setuptools import setup
from Cython.Build import cythonize

setup(
    ext_modules=cythonize("sum_squares.pyx")
)
"""

# Using Python's built-in optimizations
import operator
from functools import reduce

def product_inefficient(numbers):
    result = 1
    for n in numbers:
        result *= n
    return result

def product_reduce(numbers):
    return reduce(operator.mul, numbers, 1)

# Using specialized libraries for specific tasks
import pandas as pd

def process_data_pure_python(data):
    result = {}
    for row in data:
        category = row["category"]
        if category not in result:
            result[category] = 0
        result[category] += row["amount"]
    return result

def process_data_pandas(data):
    df = pd.DataFrame(data)
    return df.groupby("category")["amount"].sum().to_dict()

# Example data
data = [
    {"category": "A", "amount": 10},
    {"category": "B", "amount": 20},
    {"category": "A", "amount": 30},
    {"category": "C", "amount": 40},
    {"category": "B", "amount": 50}
]

start = time.time()
result_python = process_data_pure_python(data)
end_python = time.time()
print(f"Pure Python: {end_python - start:.6f} seconds")

start = time.time()
result_pandas = process_data_pandas(data)
end_pandas = time.time()
print(f"Pandas: {end_pandas - start:.6f} seconds")
```

## Conclusion

This comprehensive guide has covered Python from beginner to intermediate levels, providing detailed explanations and practical examples for a wide range of topics. Whether you're just starting with Python or looking to deepen your understanding of specific concepts, this resource offers a solid foundation for your software engineering journey with Python.

Remember that mastering Python, like any programming language, requires practice and application. Try to implement the concepts you've learned in your own projects, and continue exploring the vast ecosystem of Python libraries and frameworks that can help you solve real-world problems efficiently.

Happy coding!