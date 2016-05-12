# Computer-Systems
Consists of projects for CS5600 - Computer Systems



### [mini-DMTCP](https://github.com/dixitk13/computer-systems/blob/master/mini-DMTCP/myrestart.c) [ [-](http://www.ccs.neu.edu/home/kapil/courses/cs5600/hw1.html) ]

This is an implementation of mini-DMTCP version. DMTCP is Distributed MultiThreaded Checkpointing which checkpoints a single-host or distributed computation in user-space  with no modifications to user code or to the O/S.

This checkpoints the hello.c which increments counter, is killed with the help of a makefile which then saves its state and registers in myckpt file. Then its brought back to life with the help of myrestart.c.
Output:

```
./hello.out
counter: 1 PID: 4192
counter: 2 PID: 4192
counter: 3 PID: 4192
counter: 4 PID: 4192
counter: 5 PID: 4192
counter: 6 PID: 4192
make: *** [check] Killed
hello.out killed (pid 4192)
./myrestart.out myckpt
counter: 7 PID: 4196
counter: 8 PID: 4196
counter: 9 PID: 4196
counter: 10 PID: 4196
````

### [Master-Worker System ](https://github.com/dixitk13/computer-systems/blob/master/master-worker-system/master.c)[ [-](http://www.ccs.neu.edu/home/kapil/courses/cs5600/hw2.html) ]
A Multi-process solution to compute exponential function using a master-worker architecture.

The master spawns n child worker processes, each of which computes x^n/n!. The Master will communicate with each worker via a separate pipe. The write-end of the pipe is made standard-out of the worker. Uses the following system calls
- SEQUENTIAL(not a system call) : Sequentially reads from workers
-  select : Uses select system call to read from file-descripters
-  poll : Uses poll system call to read from file-descripters
-  epoll : Uses epoll system call to read from file-descripters

The makefile has targets for multiple tests.


### [Malloc Library](https://github.com/dixitk13/computer-systems/blob/master/buddy-algorithm-malloc/malloc.c)[ [-](http://www.ccs.neu.edu/home/kapil/courses/cs5600/hw3.html) ]
A Malloc library that provides the following dynamic memory allocation

```
- void *malloc(size_t size)
- void free(void *ptr)
- void *calloc(size_t nmemb, size_t size)
- void *realloc(void *ptr, size_t size)
```

- The implementation uses [buddy allocation](https://en.wikipedia.org/wiki/Buddy_memory_allocation) for coalescing free memory within a bucket.  
- Uses sbrk to ask kernel for more memory
- Implements [Malloc Hooks](http://www.gnu.org/software/libc/manual/html_node/Hooks-for-Malloc.html)
- Includes a test threads program which is called by default make target in the makefile

### [Master-Boss ThreadPool System ](https://github.com/dixitk13/computer-systems/blob/master/boss-worker/boss-slave.c)[ [-](http://www.ccs.neu.edu/home/kapil/courses/cs5600/hw5.html) ]
A Multi-threaded boss-worker example. In this the boss add works in the worker Q and the worker picks up those and starts processing and puts the item in the master queue. After processing the master collects and displays the answer of the exponential function. Its similar to the master-worker architecture except that it uses a threadpool this time.

The makefile has targets testing.


created using : [Dillinger](http://dillinger.io/)