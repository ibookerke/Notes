## OpenMP
- An API for Writing Multithreaded Applications
- Non-POSIX library
- Developed and maintained by a non-profit consortium 
- C/C++/Fortran 
- Cross platform (Linux, Windows, MacOS etc.)

- Makes use of `#pragma` directive 
	- Says to the C pre-processor to provide additional information to the compiler
- `#include <omp.h>` is required
- -fopenmp option with gcc
- We can specify how many threads will be generated
	- omp_set_num_threads(4);


## Using Pthreads and fork()

- A copy of the entire address space using a single thread (the one that invoked fork() ) is created
- May lead to [[Deadlock]]s!
- Use it with caution!
- When progress in waiting in while loop it is called a ==Spinlock==

## Threads at kernel space
- Thread creation is done through clone() system call -> wrapped in [[glibc]] as a function 
- clone() allows a child task to share the address space of the parent task (process) 
- Linux refers to threads as tasks rather than threads 
- `#include <sched.h>` is required

## clone()
```
  int clone(
    int (*fn)(void *),
    void *stack,
    int flags,
    void *arg
  )
```

- The stack argument specifies the location of the stack used by the child process
- Returns the thread id or -1 if something goes wrong

### Example
![[Pasted image 20230228092251.png]]

