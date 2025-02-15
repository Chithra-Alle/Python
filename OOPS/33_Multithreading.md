# Threads
- A thread is a lightweight, independent unit of execution within a process. 
- Python threads allow programs to perform multiple tasks simultaneously, improving efficiency when dealing with I/O-bound operations.

basic example without threads:
```
import time
class Hello():
    def run(self):
        for _ in range(5):
            print("Hello")
    
class Hi():
    def run(self):
        for _ in range(5):
            print("Hi")
st=time.time()
t1 = Hello()
t2 = Hi()
t1.run()
t2.run()
et=time.time()
res=st-et
res

output

Hello
Hello
Hello
Hello
Hello
Hi
Hi
Hi
Hi
Hi
-0.003000020980834961
```


##### example with threads
- initially every execution has a main thread
- but when we create threads, those threads will come under this main thread, look at the image for clarification



![Main thread hierarchy](https://tse3.mm.bing.net/th?id=OIP.wnh96dy-FwT1E36_QbTTKgHaE8&pid=Api&P=0&h=180)
