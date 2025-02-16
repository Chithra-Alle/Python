# MultiProcessing
- we are going to see the difference between multi processing and multi threading both of these are ways to achieve multitasking.
- when you are doing multiple tasks at the same time it is called multitasking for example this mom she is taking care of baby picking up the phone call and at the same time cooking food so she's doing all these multiple things at the same time.

![multitask](https://github.com/user-attachments/assets/a4f41886-86fd-4745-bcc1-48c159727426)

- a computer in similar fashion does multiple tasks for example on my computer I have PowerPoint running, I have browser running I might have calculated a couple of other programs running.
- so all these different programs are basically different processes and if you want to see those processes you can see it here in windows task manager if
1:02
you go to details tab all these entities
1:06
which are listed here they are all
1:09
different processes so for example for
1:12
Chrome I have all this processes and for
1:15
PowerPoint I have this guy here and
1:18
there is a PID PID means process ID so
1:22
they have that own different process IDs
1:25
so understanding processes is pretty
1:28
easy
1:29
basically there are different programs
1:31
running on your computer then what is
1:34
actually multiple threads okay so let me
1:39
go back to my presentation so multiple
1:42
threads basically lives within the same
1:46
process so in this diagram here this
1:49
outer block is a process which has its
1:52
own virtual memory or an address space
1:55
now it can create multiple threads
1:59
inside it now the difference between
2:02
process and third is that threads will
2:04
share this outer space now they will
2:07
have their own instruction sets they
2:09
will be doing each of these threads will
2:10
be doing
2:11
specific tasks and they will be
2:14
exhibiting their own core they have
2:16
their own stack memory own instruction
2:20
pointer but the only thing that they
2:23
share is that a space which means if you
2:25
have any global variables to define in
2:28
your program they can be accessed by
2:30
these threads and heap memory can be
2:33
accessed by this Thresh okay whereas if
2:36
you look at the processes this is
2:40
process one and process two they have
2:42
their own address paste okay and if they
2:46
ever want to communicate with each other
2:48
they can use inter process communication
2:52
techniques such as a file on the disk or
2:57
a shared memory or a message pipe okay
3:00
so from these two pictures you can at
3:03
least guess what is the key difference
3:05
between process and a thread so the key
3:09
difference is players are lightweight
3:12
vs. processes are hey wait okay that's
3:16
the key difference now if there is a
3:20
lightweight why do you even care to
3:21
create a new process well first of all
3:24
these processes are different programs
3:26
written by different companies so they
3:28
have to run separately as separate
3:31
process and another thing is if you have
3:35
any error or a memory leak in one
3:38
program or or one process it will not
3:41
impact another process versus if you
3:44
have that problem in a one thread then
3:48
since it is running under is in the
3:50
diagram if this thread has a memory leak
3:52
then it can potentially impact the
3:54
entire process and it can have harmful
3:57
effects on these threads and the parent
3:59
process all right so that was all about
4:02
multi processing and multi-threading
