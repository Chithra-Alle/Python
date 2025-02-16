- We have seen the porblem causing in Multiprocessing due to no shared data among process in our previous file.
- so to efficeiently solve this problem, we are going to use Array and Value in Multiprocessing
- Look at the below code and syntax to know about how data will be shared among process using Arra

# Sharing Data between Processes using Array
```
from multiprocessing import *
from time import *

def square(nums,ar):
    for indx,n in enumerate(nums):
        print(n)
        ar[indx]=n
        sleep(1)
if __name__ == "__main__":
    nums =[1,2,3,4]
    array_space=Array('i',4)# i is the datatype, 4 is the size of the array
    p = Process(target=square,args=(nums,array_space))
    p.start()
    p.join()
    print(array_space[:])
```
# Sharing Data between Processes using Value
```
from multiprocessing import *
from time import *

def square(nums,v):
    v.value=5.6
    for n in nums:
        print(n)
        sleep(1)
if __name__=="__main__":
    nums=[1,2,3,4]
    v=Value('d',3.4)
    print("value is : "+v)
    p=Process(target=square,args=(nums,v))
    p.start()
    p.join()
    print("Bye")
```

# Sharing Data between Processes using Queue
```
from multiprocessing import *
from time import *

def hel(nums,q):
    for n in nums:
        print(n)
        q.put(n)
        sleep(1)
if __name__=="__main__":
    nums=[1,2,3,4]
    q=Queue()
    p = Process(target=hel,args=(nums,q))
    p.start()
    p.join()

    while q.empty() is False:
        print(q.get())
    print("Bye")           
```
# Difference between Queue module and Multiprocessing Queue
| Multiprocessing Queue | Queue Module|
|:--------:|:-------:|
|import multiprocessing|import queue|
|q=multiprocessing.Queue()|q=queue.Queue()|
|Lives in shared memory|Lives in in-process memory|
|Used in share data between processe|Used in share data between threads|
