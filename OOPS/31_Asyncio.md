# ASYNCIO
- before diving into the topic one should know when to use ASYNCIO.
- asyncio is a built-in Python library used for writing asynchronous programs. It allows running multiple tasks concurrently using a single thread, making it useful for I/O-bound tasks like network requests, file reading, and database queries.

Comparision chart:
###### ASYNCIO
> use for managing many waiting tasks

###### PROCESSES
> use for maximixing performance on CPU intensive tasks

###### THREADS
> use for parallel tasks taht share data with minimal CPU use

TO get Dive into the ASYNCIO, first we need to know 5 major concepts
1. EVENT LOOP
- An event loop is like a manager that keeps track of tasks and runs them when they are ready. It is used in asynchronous programming to handle tasks without stopping everything else.

2. Coroutines
-  A coroutine is a special type of funciton in python that can be paused and resumed without stopping the whole program. Coroutines allow you ot run multiple tasks at the same time without waiting for one to finish before starting another.
-  
