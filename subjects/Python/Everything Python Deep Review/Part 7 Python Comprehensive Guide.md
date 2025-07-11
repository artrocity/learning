---
aliases:
  - "Part 3: Python Comprehensive Guide"
---
# Debugging (continued)

**Examples (continued)**:

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
    print(f"Error occurred: {e}")  # ZeroDivisionError

# Using assertions for debugging
def calculate_average(numbers):
    assert len(numbers) > 0, "List cannot be empty"
    total = sum(numbers)
    return total / len(numbers)

try:
    calculate_average([])
except AssertionError as e:
    print(f"Assertion failed: {e}")

# Using the built-in debugger (pdb)
import pdb

def complex_function(a, b):
    result = a * 2
    # Start the debugger
    # pdb.set_trace()  # Python 3.7+: breakpoint()
    result = result + b
    return result

# When this function is called, the debugger will pause at set_trace()
# complex_function(3, 4)
# Common pdb commands:
# n (next) - Execute the current line and move to the next one
# s (step) - Step into a function call
# c (continue) - Continue execution until the next breakpoint
# q (quit) - Quit the debugger
# p expression - Print the value of an expression
# l (list) - Show the current line in the context of the source code
# h (help) - Show help on debugger commands

# Debugging with logging
import logging

# Configure logging
logging.basicConfig(
    level=logging.DEBUG,
    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s',
    filename='debug.log'
)

def calculate_with_logging(a, b):
    logging.debug(f"calculate_with_logging called with a={a}, b={b}")
    
    if b == 0:
        logging.error("Division by zero attempted")
        raise ValueError("Cannot divide by zero")
    
    result = a / b
    logging.debug(f"Result calculated: {result}")
    return result

try:
    calculate_with_logging(10, 2)  # Works fine
    calculate_with_logging(10, 0)  # Raises error
except ValueError as e:
    logging.exception("Exception occurred")

# Using a context manager for timing code blocks
import time
from contextlib import contextmanager

@contextmanager
def timer(name):
    start_time = time.time()
    yield
    elapsed = time.time() - start_time
    print(f"{name} took {elapsed:.6f} seconds")

def slow_function():
    with timer("slow_function"):
        time.sleep(1)
        return "Done"

slow_function()

# Using traceback module
import traceback

def function_c():
    # Access an undefined variable to cause an error
    return undefined_variable

def function_b():
    return function_c()

def function_a():
    try:
        return function_b()
    except NameError:
        # Print the traceback
        traceback.print_exc()
        # Get the traceback as a string
        error_msg = traceback.format_exc()
        return f"An error occurred: {error_msg}"

print(function_a())

# Using sys.settrace for custom debugging
import sys

def trace_calls(frame, event, arg):
    if event != 'call':
        return
    co = frame.f_code
    func_name = co.co_name
    if func_name == 'write':
        # Ignore write() calls from print statements
        return
    func_line_no = frame.f_lineno
    func_filename = co.co_filename
    caller = frame.f_back
    caller_line_no = caller.f_lineno
    caller_filename = caller.f_code.co_filename
    print(f'Call to {func_name} on line {func_line_no} of {func_filename} from line {caller_line_no} of {caller_filename}')
    return

def traced_example():
    a = 1
    b = 2
    return a + b

# Enable tracing
sys.settrace(trace_calls)
traced_example()
# Disable tracing
sys.settrace(None)

# Using the warnings module
import warnings

def deprecated_function():
    warnings.warn("This function is deprecated", DeprecationWarning, stacklevel=2)
    return "Result"

# Configure warnings
warnings.filterwarnings("default")  # Show all warnings
# warnings.filterwarnings("ignore")  # Ignore all warnings
# warnings.filterwarnings("error")   # Convert warnings to errors

result = deprecated_function()
```

## Algorithms and Data Structures

### Sorting Algorithms

**What they are**: Sorting algorithms are methods for reorganizing a list of items into a specific order, such as numerical or lexicographical.

**How they work**: Different sorting algorithms use different strategies to reorder elements, and they vary in terms of time complexity, space complexity, and stability.

**Examples**:

```python
# Bubble Sort
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        # Flag to optimize if array is already sorted
        swapped = False
        
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]
                swapped = True
        
        # If no swapping occurred in this pass, array is sorted
        if not swapped:
            break
    
    return arr

# Selection Sort
def selection_sort(arr):
    n = len(arr)
    for i in range(n):
        min_idx = i
        for j in range(i+1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        
        # Swap the found minimum element with the element at index i
        arr[i], arr[min_idx] = arr[min_idx], arr[i]
    
    return arr

# Insertion Sort
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i-1
        while j >= 0 and key < arr[j]:
            arr[j+1] = arr[j]
            j -= 1
        arr[j+1] = key
    
    return arr

# Merge Sort
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

# Quick Sort
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    
    return quick_sort(left) + middle + quick_sort(right)

# Heap Sort
def heapify(arr, n, i):
    largest = i
    left = 2 * i + 1
    right = 2 * i + 2
    
    if left < n and arr[left] > arr[largest]:
        largest = left
    
    if right < n and arr[right] > arr[largest]:
        largest = right
    
    if largest != i:
        arr[i], arr[largest] = arr[largest], arr[i]
        heapify(arr, n, largest)

def heap_sort(arr):
    n = len(arr)
    
    # Build max heap
    for i in range(n // 2 - 1, -1, -1):
        heapify(arr, n, i)
    
    # Extract elements one by one
    for i in range(n-1, 0, -1):
        arr[0], arr[i] = arr[i], arr[0]
        heapify(arr, i, 0)
    
    return arr

# Counting Sort (for integers within a specific range)
def counting_sort(arr, max_val=None):
    if not arr:
        return arr
    
    if max_val is None:
        max_val = max(arr)
    
    counts = [0] * (max_val + 1)
    
    for num in arr:
        counts[num] += 1
    
    sorted_arr = []
    for i in range(len(counts)):
        sorted_arr.extend([i] * counts[i])
    
    return sorted_arr

# Radix Sort (for integers)
def radix_sort(arr):
    if not arr:
        return arr
    
    # Find the maximum number to know number of digits
    max_num = max(abs(num) for num in arr)
    
    # Handle negative numbers
    neg = [num for num in arr if num < 0]
    pos = [num for num in arr if num >= 0]
    
    # Sort positive numbers
    exp = 1
    while max_num // exp > 0:
        pos = counting_sort_by_digit(pos, exp)
        exp *= 10
    
    # Sort negative numbers
    neg = [-num for num in neg]  # Make them positive for sorting
    exp = 1
    while max_num // exp > 0:
        neg = counting_sort_by_digit(neg, exp)
        exp *= 10
    neg = [-num for num in neg]  # Make them negative again
    neg.reverse()  # Reverse to maintain correct order
    
    return neg + pos

def counting_sort_by_digit(arr, exp):
    n = len(arr)
    output = [0] * n
    count = [0] * 10
    
    for i in range(n):
        digit = (arr[i] // exp) % 10
        count[digit] += 1
    
    for i in range(1, 10):
        count[i] += count[i-1]
    
    i = n - 1
    while i >= 0:
        digit = (arr[i] // exp) % 10
        output[count[digit] - 1] = arr[i]
        count[digit] -= 1
        i -= 1
    
    return output

# Using Python's built-in sort
numbers = [5, 2, 8, 1, 9, 3]
sorted_numbers = sorted(numbers)  # Creates a new sorted list
print(sorted_numbers)  # [1, 2, 3, 5, 8, 9]

numbers.sort()  # Sorts the list in-place
print(numbers)  # [1, 2, 3, 5, 8, 9]

# Sorting with a key function
words = ["apple", "Banana", "Cherry", "date", "Fig"]
sorted_words = sorted(words)  # Case-sensitive sort
print(sorted_words)  # ['Banana', 'Cherry', 'Fig', 'apple', 'date']

case_insensitive = sorted(words, key=str.lower)  # Case-insensitive sort
print(case_insensitive)  # ['apple', 'Banana', 'Cherry', 'date', 'Fig']

# Sorting objects by attribute
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def __repr__(self):
        return f"Person('{self.name}', {self.age})"

people = [
    Person("Alice", 30),
    Person("Bob", 25),
    Person("Charlie", 35)
]

# Sort by age
sorted_by_age = sorted(people, key=lambda person: person.age)
print(sorted_by_age)  # [Person('Bob', 25), Person('Alice', 30), Person('Charlie', 35)]

# Sort by name
sorted_by_name = sorted(people, key=lambda person: person.name)
print(sorted_by_name)  # [Person('Alice', 30), Person('Bob', 25), Person('Charlie', 35)]

# Reverse sort
reverse_sorted = sorted(numbers, reverse=True)
print(reverse_sorted)  # [9, 8, 5, 3, 2, 1]
```

### Searching Algorithms

**What they are**: Searching algorithms are methods for finding an item with specified properties within a collection of items.

**How they work**: Different searching algorithms use different strategies to locate items, and they vary in terms of time complexity and prerequisites for the input data.

**Examples**:

```python
# Linear Search
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i  # Return the index of the target
    return -1  # Target not found

# Binary Search (requires sorted array)
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    
    while left <= right:
        mid = (left + right) // 2
        
        if arr[mid] == target:
            return mid  # Target found
        elif arr[mid] < target:
            left = mid + 1  # Search the right half
        else:
            right = mid - 1  # Search the left half
    
    return -1  # Target not found

# Recursive Binary Search
def recursive_binary_search(arr, target, left=None, right=None):
    if left is None:
        left = 0
    if right is None:
        right = len(arr) - 1
    
    if left > right:
        return -1  # Target not found
    
    mid = (left + right) // 2
    
    if arr[mid] == target:
        return mid  # Target found
    elif arr[mid] < target:
        return recursive_binary_search(arr, target, mid + 1, right)  # Search the right half
    else:
        return recursive_binary_search(arr, target, left, mid - 1)  # Search the left half

# Jump Search (requires sorted array)
def jump_search(arr, target):
    n = len(arr)
    step = int(n ** 0.5)  # Optimal jump size
    
    prev = 0
    while arr[min(step, n) - 1] < target:
        prev = step
        step += int(n ** 0.5)
        if prev >= n:
            return -1  # Target not found
    
    # Linear search in the block
    while arr[prev] < target:
        prev += 1
        if prev == min(step, n):
            return -1  # Target not found
    
    if arr[prev] == target:
        return prev  # Target found
    
    return -1  # Target not found

# Interpolation Search (requires sorted array)
def interpolation_search(arr, target):
    low, high = 0, len(arr) - 1
    
    while low <= high and target >= arr[low] and target <= arr[high]:
        if low == high:
            if arr[low] == target:
                return low
            return -1
        
        # Formula for position based on value distribution
        pos = low + int(((float(high - low) / (arr[high] - arr[low])) * (target - arr[low])))
        
        if arr[pos] == target:
            return pos
        elif arr[pos] < target:
            low = pos + 1
        else:
            high = pos - 1
    
    return -1  # Target not found

# Exponential Search (requires sorted array)
def exponential_search(arr, target):
    n = len(arr)
    
    # If target is the first element
    if arr[0] == target:
        return 0
    
    # Find range for binary search
    i = 1
    while i < n and arr[i] <= target:
        i = i * 2
    
    # Call binary search for the found range
    return binary_search(arr, target, i // 2, min(i, n - 1))

# Using Python's built-in methods
numbers = [1, 2, 3, 5, 8, 9]
index = numbers.index(5)  # Returns the index of 5 (3)
print(index)

# Using 'in' operator for membership testing
if 5 in numbers:
    print("5 is in the list")

# Find in unsorted list
unsorted = [5, 2, 8, 1, 9, 3]
index = unsorted.index(8)  # Returns the index of 8 (2)
print(index)

# Search in a dictionary
person = {"name": "Alice", "age": 30, "city": "New York"}
if "name" in person:
    print(person["name"])  # Alice

# Using the bisect module for binary search in sorted arrays
import bisect

sorted_numbers = [1, 2, 3, 5, 8, 9]

# Find insertion point
insertion_point = bisect.bisect_left(sorted_numbers, 5)
print(insertion_point)  # 3

# Check if element exists
def binary_search_bisect(arr, target):
    idx = bisect.bisect_left(arr, target)
    return idx < len(arr) and arr[idx] == target

print(binary_search_bisect(sorted_numbers, 5))  # True
print(binary_search_bisect(sorted_numbers, 4))  # False
```

### Graph Algorithms

**What they are**: Graph algorithms are methods for processing and analyzing graph structures, which consist of nodes (vertices) and connections (edges) between them.

**How they work**: These algorithms address problems like finding paths, connectivity, and network flow in graphs.

**Examples**:

```python
# Graph representation using adjacency list
class Graph:
    def __init__(self):
        self.graph = {}
    
    def add_edge(self, u, v, directed=False):
        if u not in self.graph:
            self.graph[u] = []
        if v not in self.graph:
            self.graph[v] = []
        
        self.graph[u].append(v)
        if not directed:
            self.graph[v].append(u)
    
    def print_graph(self):
        for vertex in self.graph:
            print(f"{vertex} -> {' '.join(map(str, self.graph[vertex]))}")

# Breadth-First Search (BFS)
from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])
    visited.add(start)
    
    while queue:
        vertex = queue.popleft()
        print(vertex, end=" ")
        
        for neighbor in graph.graph.get(vertex, []):
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)

# Depth-First Search (DFS)
def dfs(graph, start, visited=None):
    if visited is None:
        visited = set()
    
    visited.add(start)
    print(start, end=" ")
    
    for neighbor in graph.graph.get(start, []):
        if neighbor not in visited:
            dfs(graph, neighbor, visited)

# Dijkstra's Algorithm for Shortest Path
import heapq

def dijkstra(graph, start):
    # Initialize distances with infinity for all vertices except start
    distances = {vertex: float('infinity') for vertex in graph.graph}
    distances[start] = 0
    
    # Priority queue to get the vertex with the smallest distance
    priority_queue = [(0, start)]
    
    while priority_queue:
        current_distance, current_vertex = heapq.heappop(priority_queue)
        
        # Check if we already found a better path
        if current_distance > distances[current_vertex]:
            continue
        
        # Check neighbors
        for neighbor in graph.graph.get(current_vertex, []):
            distance = current_distance + 1  # Assuming all edges have weight 1
            
            # If we found a better path, update the distance
            if distance < distances[neighbor]:
                distances[neighbor] = distance
                heapq.heappush(priority_queue, (distance, neighbor))
    
    return distances

# Bellman-Ford Algorithm for Shortest Path (handles negative weights)
def bellman_ford(graph, start):
    # Initialize distances with infinity for all vertices except start
    distances = {vertex: float('infinity') for vertex in graph.graph}
    distances[start] = 0
    
    # Relax all edges |V| - 1 times
    for _ in range(len(graph.graph) - 1):
        for u in graph.graph:
            for v in graph.graph[u]:
                if distances[u] + 1 < distances[v]:  # Assuming all edges have weight 1
                    distances[v] = distances[u] + 1
    
    # Check for negative weight cycles
    for u in graph.graph:
        for v in graph.graph[u]:
            if distances[u] + 1 < distances[v]:  # Assuming all edges have weight 1
                print("Graph contains a negative weight cycle")
                return None
    
    return distances

# Kruskal's Algorithm for Minimum Spanning Tree
class DisjointSet:
    def __init__(self, vertices):
        self.parent = {v: v for v in vertices}
        self.rank = {v: 0 for v in vertices}
    
    def find(self, item):
        if self.parent[item] != item:
            self.parent[item] = self.find(self.parent[item])  # Path compression
        return self.parent[item]
    
    def union(self, x, y):
        root_x = self.find(x)
        root_y = self.find(y)
        
        if root_x == root_y:
            return
        
        # Union by rank
        if self.rank[root_x] < self.rank[root_y]:
            self.parent[root_x] = root_y
        elif self.rank[root_x] > self.rank[root_y]:
            self.parent[root_y] = root_x
        else:
            self.parent[root_y] = root_x
            self.rank[root_x] += 1

def kruskal(graph):
    edges = []
    for u in graph.graph:
        for v in graph.graph[u]:
            edges.append((u, v, 1))  # Assuming all edges have weight 1
    
    # Remove duplicate edges for undirected graph
    unique_edges = set()
    for u, v, w in edges:
        edge = tuple(sorted([u, v]) + [w])
        unique_edges.add(edge)
    
    edges = list(unique_edges)
    edges.sort(key=lambda x: x[2])  # Sort by weight
    
    vertices = list(graph.graph.keys())
    disjoint_set = DisjointSet(vertices)
    
    minimum_spanning_tree = []
    for u, v, w in edges:
        if disjoint_set.find(u) != disjoint_set.find(v):
            minimum_spanning_tree.append((u, v, w))
            disjoint_set.union(u, v)
    
    return minimum_spanning_tree

# Prim's Algorithm for Minimum Spanning Tree
def prim(graph):
    # Start with an arbitrary vertex
    start = next(iter(graph.graph))
    
    # Initialize sets
    included = {start}
    vertices = set(graph.graph.keys())
    
    minimum_spanning_tree = []
    
    while included != vertices:
        min_edge = None
        min_weight = float('infinity')
        
        for u in included:
            for v in graph.graph[u]:
                if v not in included:
                    weight = 1  # Assuming all edges have weight 1
                    if weight < min_weight:
                        min_weight = weight
                        min_edge = (u, v, weight)
        
        if min_edge:
            u, v, w = min_edge
            minimum_spanning_tree.append(min_edge)
            included.add(v)
    
    return minimum_spanning_tree

# Topological Sorting
def topological_sort(graph):
    visited = set()
    stack = []
    
    def dfs_util(vertex):
        visited.add(vertex)
        
        for neighbor in graph.graph.get(vertex, []):
            if neighbor not in visited:
                dfs_util(neighbor)
        
        stack.append(vertex)
    
    for vertex in graph.graph:
        if vertex not in visited:
            dfs_util(vertex)
    
    return stack[::-1]  # Reverse the stack to get the topological order

# Floyd-Warshall Algorithm for All-Pairs Shortest Paths
def floyd_warshall(graph):
    # Initialize distances
    vertices = list(graph.graph.keys())
    n = len(vertices)
    vertex_to_index = {vertices[i]: i for i in range(n)}
    
    # Initialize distance matrix with infinity
    dist = [[float('infinity') for _ in range(n)] for _ in range(n)]
    
    # Set distance to self as 0
    for i in range(n):
        dist[i][i] = 0
    
    # Set distance for direct edges
    for u in graph.graph:
        for v in graph.graph[u]:
            i, j = vertex_to_index[u], vertex_to_index[v]
            dist[i][j] = 1  # Assuming all edges have weight 1
    
    # Calculate shortest paths
    for k in range(n):
        for i in range(n):
            for j in range(n):
                if dist[i][j] > dist[i][k] + dist[k][j]:
                    dist[i][j] = dist[i][k] + dist[k][j]
    
    # Convert back to vertex representation
    result = {}
    for i in range(n):
        result[vertices[i]] = {}
        for j in range(n):
            result[vertices[i]][vertices[j]] = dist[i][j]
    
    return result

# Example usage
g = Graph()
g.add_edge(0, 1)
g.add_edge(0, 2)
g.add_edge(1, 2)
g.add_edge(2, 0)
g.add_edge(2, 3)
g.add_edge(3, 3)

print("Graph representation:")
g.print_graph()

print("\nBFS starting from vertex 2:")
bfs(g, 2)

print("\nDFS starting from vertex 2:")
dfs(g, 2)

print("\nShortest paths from vertex 2 (Dijkstra):")
print(dijkstra(g, 2))
```

### Dynamic Programming

**What it is**: Dynamic Programming is a problem-solving technique that solves complex problems by breaking them down into simpler subproblems and storing their solutions to avoid redundant calculations.

**How it works**: It uses a table (memoization) to store solutions to subproblems, which are then reused when solving larger problems.

**Examples**:

```python
# Fibonacci sequence with dynamic programming (top-down approach with memoization)
def fibonacci_memo(n, memo={}):
    if n in memo:
        return memo[n]
    if n <= 1:
        return n
    
    memo[n] = fibonacci_memo(n-1, memo) + fibonacci_memo(n-2, memo)
    return memo[n]

# Fibonacci sequence with dynamic programming (bottom-up approach with tabulation)
def fibonacci_tabulation(n):
    if n <= 1:
        return n
    
    dp = [0] * (n + 1)
    dp[1] = 1
    
    for i in range(2, n + 1):
        dp[i] = dp[i-1] + dp[i-2]
    
    return dp[n]

# Longest Common Subsequence (LCS)
def longest_common_subsequence(s1, s2):
    m, n = len(s1), len(s2)
    
    # Create a table to store the length of LCS
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    
    # Fill the table in a bottom-up manner
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if s1[i-1] == s2[j-1]:
                dp[i][j] = dp[i-1][j-1] + 1
            else:
                dp[i][j] = max(dp[i-1][j], dp[i][j-1])
    
    # Reconstruct the LCS
    lcs = []
    i, j = m, n
    while i > 0 and j > 0:
        if s1[i-1] == s2[j-1]:
            lcs.append(s1[i-1])
            i -= 1
            j -= 1
        elif dp[i-1][j] > dp[i][j-1]:
            i -= 1
        else:
            j -= 1
    
    return ''.join(reversed(lcs))

# 0-1 Knapsack Problem
def knapsack(weights, values, capacity):
    n = len(weights)
    
    # Create a table to store the maximum value for each capacity
    dp = [[0] * (capacity + 1) for _ in range(n + 1)]
    
    # Fill the table in a bottom-up manner
    for i in range(1, n + 1):
        for w in range(1, capacity + 1):
            if weights[i-1] <= w:
                dp[i][w] = max(values[i-1] + dp[i-1][w-weights[i-1]], dp[i-1][w])
            else:
                dp[i][w] = dp[i-1][w]
    
    # Find the selected items
    selected = []
    i, w = n, capacity
    while i > 0 and w > 0:
        if dp[i][w] != dp[i-1][w]:
            selected.append(i-1)
            w -= weights[i-1]
        i -= 1
    
    return dp[n][capacity], selected

# Coin Change Problem (minimum number of coins)
def min_coins(coins, amount):
    # Initialize dp array with a value larger than any possible solution
    dp = [float('infinity')] * (amount + 1)
    dp[0] = 0  # Base case: 0 coins needed for amount 0
    
    for coin in coins:
        for i in range(coin, amount + 1):
            dp[i] = min(dp[i], dp[i - coin] + 1)
    
    return dp[amount] if dp[amount] != float('infinity') else -1

# Coin Change Problem (number of ways to make change)
def count_ways(coins, amount):
    dp = [0] * (amount + 1)
    dp[0] = 1  # Base case: 1 way to make amount 0
    
    for coin in coins:
        for i in range(coin, amount +
```