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

- the moment I say start, the heirarchy changes.. now the created threads will be counted as seperate threads.so total threads will be 1 main threa + no.of created threads
```
import time
from threading import *
class Hello(Thread):
    def run(self):
        for _ in range(5):
            print("Hello")
            time.sleep(1)
    
class Hi(Thread):
    def run(self):
        for _ in range(5):
            print("Hi")
            time.sleep(1)
st=time.time() # not mandatoy, just to know how much time it is taking... use time module for better experience.

t1 = Hello()
t2 = Hi()
t1.start()#Threads class internally has a run class, so call it start, the Thread class will perform run operation. And make sure that the method inside the created classes above are defined as run instead of naming other names
t2.start()

t1.join()#to tell main thread that let other threads complete their work
t2.join()

print("Bye')# if you won't join threads, the main threads interepts between t1 and t2, and as printing "bye" is the work of main thread, whenever t1 and t2 are sleeping.. main thread executes its works. that is so awkward, so joining threads is compulsory.

print(active_count())# to know how many active threads are there
et=time.time()
res=st-et
print(res)
```


