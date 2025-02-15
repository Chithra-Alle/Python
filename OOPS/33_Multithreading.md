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
![Threads hierarchy]([image.png](https://in.images.search.yahoo.com/images/view;_ylt=AwrKBJSjmLBnY8kLcYu9HAx.;_ylu=c2VjA3NyBHNsawNpbWcEb2lkA2FmNjM3ZGI3MjRiNTQ1Njk5YTY4YWQyNDMzMTg5YTZiBGdwb3MDMgRpdANiaW5n?back=https%3A%2F%2Fin.images.search.yahoo.com%2Fsearch%2Fimages%3Fp%3Dmain%2Bthreads%2Bin%2Bpython%26ei%3DUTF-8%26type%3DE210IN714G0%26fr%3Dmcafee%26fr2%3Dp%253As%252Cv%253Ai%252Cm%253Asb-top%26tab%3Dorganic%26ri%3D2&w=1024&h=683&imgurl=www.askpython.com%2Fwp-content%2Fuploads%2F2020%2F07%2Fillustration-of-main-thread-and-child-threads-1024x683.png&rurl=https%3A%2F%2Fwww.askpython.com%2Fpython-modules%2Fmultithreading-in-python&size=41KB&p=main+threads+in+python&oid=af637db724b545699a68ad2433189a6b&fr2=p%3As%2Cv%3Ai%2Cm%3Asb-top&fr=mcafee&tt=Multithreading+in+Python%3A+An+Easy+Reference+-+AskPython&b=0&ni=57&no=2&ts=&tab=organic&sigr=LHmWbZFLZpoW&sigb=VqghtgECQd9j&sigi=pe9XOD00g6Im&sigt=tAIWTrjq2ZJN&.crumb=Y8glGlhdMa4&fr=mcafee&fr2=p%3As%2Cv%3Ai%2Cm%3Asb-top&type=E210IN714G0)) 
