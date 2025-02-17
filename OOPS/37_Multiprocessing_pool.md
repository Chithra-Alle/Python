# Multiprocessing Pool

- The multiprocessing.Pool class in Python is used to parallelize function execution across multiple processes. 
- It helps distribute tasks among multiple CPU cores, improving performance for CPU-bound tasks.
- Look at the below image to know how multiprocessing pool works

  ![image](https://github.com/user-attachments/assets/9273c559-6dcf-419b-b637-84e47ee8056c)

#### Why use multiprocessing pool?
* Parallel Execution – Runs tasks concurrently using multiple CPU cores.
* Efficient Resource Management – Automatically manages worker processes.
* Load Balancing – Distributes tasks among processes.
* Simple Syntax – Provides an easy way to execute functions in parallel.

```
from multiprocessing import *
from time import *

def randfun(n):
    sum=0
    for x in range(10):
        sum+=n*x
    return sum

if __name__ == "__main__":
    t1=time()
    array=[1,2,3,4,5,6,7,8,9,10]
    p = Pool(processes=5)
    res=p.map(randfun,array)
    print(res)
    p.close()
    p.join()
    print("Pool took: ",time()-t1)

    t2=time()
    res=[]
    for x in array:
        res.append(randfun(x))

    print(res)
    print("serial processing took: ",time()-t2)
```
