# Function Caching in Python
- Function caching is a technique that stores the results of expensive function calls and reuses them when the same inputs occurs again.
- This helps improve performance by avoiding redundant computations.
- Python provides build-in support for function caching using the **functools.lru_cache decorator**

### Using functools.lru_cache for Caching
The Least Recently Used (LRU) Cache stores function results based on the arguments passed. If the same function is called with the same arguments again, the cached result is returned instead of recalculating.

### Example: Fibonacci with Caching
```
from functools import lru_cache
import time

@lru_cache(maxsize=None)  # Cache results indefinitely
def fibonacci(n):
    if n < 2:
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)

start_time = time.time()
print(fibonacci(40))  # Computes and caches results
print("Time taken:", time.time() - start_time)

start_time = time.time()
print(fibonacci(40))  # Returns cached result instantly
print("Time taken:", time.time() - start_time)
```

Explanation
> The @lru_cache decorator stores results of function calls.<br>
> If the function is called with the same input again, it returns the cached result instantly instead of recomputing.<br>
> maxsize=None means unlimited cache storage. You can specify a limit like maxsize=100 to restrict memory usage.


Benefits of Function Caching
✅ Speeds up repeated function calls (useful in recursive functions like Fibonacci).
✅ Reduces redundant computations (ideal for CPU-heavy operations).
✅ Improves performance in API calls, database queries, and data processing tasks.

When to Avoid Function Caching
❌ If function results frequently change (e.g., real-time data fetch).
❌ If arguments are mutable objects (e.g., lists, dictionaries).
❌ If memory usage is a concern (large caches can consume a lot of RAM).

To manually clear the cache, use:
```
fibonacci.cache_clear()
```

### Limitations of Function Caching
1. Memory Consumption
2. Not suitable for Mutable Arguments
3. Not suitable for Dynamic Data(eg: if you need weather report.. when first time you ask like "delhi weather" it stores the results.. but next when you ask again it gives the outdated data)
4. Cannot cache Functions with side effects
5. Cache staleness(should clear after using)


