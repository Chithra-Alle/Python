* In multiprocessing, locks (also known as mutexes – mutual exclusions) are used to prevent multiple processes from accessing a shared resource simultaneously. Without locks, concurrent processes might try to modify shared data at the same time, leading to race conditions, data corruption, or inconsistent results.
* Locks ensure that only one process can access the shared resource at a time, enforcing synchronization and preventing conflicts.

###### Real Life Example
Imagine multiple people trying to withdraw money from the same bank account at an ATM. If two people access the account at the same time and try to withdraw ₹10,000 each when only ₹15,000 is available, both might succeed if the system doesn't lock access to the account while one transaction is in progress. This could lead to an incorrect negative balance.

Let us now code and observe what happens if we won't use locks in processes which access shared resources.
```
from multiprocessing import *
from time import *

def deposit(balance):
    for _ in range(100):
        balance.value+=1
        sleep(0.01)

def withdraw(balance):
    for _ in range(100):
        balance.value-=1
        sleep(0.01)

if __name__=="__main__":
    balance=Value('i',200)
    p1 = Process(target=deposit,args=(balance,))
    p2 = Process(target=withdraw,args=(balance,))
    p1.start()
    p2.start()
    p1.join()
    p2.join()
    print(balance.value)
    print("Bye")
```
> Try Running this multiple times, you can observe inconsistent result.
> What happening here is, the two processes trying to access the shared resource at a time, while before a process complete it's task, the other process interepts.
> So, to solve this issue we need locks, please look at the below code for better understanding

```
from multiprocessing import *
from time import *

def deposit(balance,lk):
    for _ in range(100):
        lk.acquire()
        balance.value+=1
        lk.release()
        sleep(0.01)

def withdraw(balance,lk):
    for _ in range(100):
        lk.acquire()
        balance.value-=1
        lk.release()
        sleep(0.01)

if __name__=="__main__":
    balance=Value('i',200)
    lk =Lock()
    p1 = Process(target=deposit,args=(balance,lk))
    p2 = Process(target=withdraw,args=(balance,lk))
    p1.start()
    p2.start()
    p1.join()
    p2.join()
    print(balance.value)
    print("Bye")

    ```
