
## Threads
- A lightweight process within a process (in the same process address space) 
- ==Process creation== is heavy-weight while thread creation is light-weight 
- Multiple tasks can be implemented by separate multiple threads 
- Can simplify code, increase efficiency 
- **Kernels** are generally **multi-threaded** 
- Most modern applications are multi-threaded

![[Pasted image 20230227155317.png]]
![[Pasted image 20230227155749.png]]

### Pros 
- Less memory to maintain Thread State (mostly extra stack space) 
- Less performance overhead 
- Automatic data sharing (same address space)
### Cons
- Shared memory can be a source of data races 
- Less robust compared to processes: 
	- Memory corruption on one thread corrupts the entire program 
	- A crash in one thread may crash the entire program
<hr>

## Multicore Programming

- ==Multicore== or ==multiprocessor== systems putting pressure on programmers, challenges include: 
	- Dividing activities 
	- Balance 
	- Data splitting 
	- Data dependency 
	- Testing and debugging
- ==Parallelism== implies a system can perform more than one task simultaneously 
- ==Concurrency== supports more than one task making progress 
	- Single processor/core, scheduler providing concurrency
<hr>

## Concurrency and Parallelism
- Many programs need to perform mostly independent tasks that do not need to be serialized 
	- Web server: page requests 
	- Text editor: auto-save, spell checking, text entry 
	- Web client: tabbed browsing 
- Parallel Programming 
	- Make multiple runtime copies of the same task 
	- Underlying system runs each task on a separate CPU 
	- For performance 
	- Makes sense only on a multiprocessor machine 
- Concurrent Programming 
	- Divide program into multiple, generally different, tasks 
	- Underlying system provides illusion of concurrent progress 
	- For responsiveness (i.e. spell check does not delay text entry) 
	- Can make sense even on a single processor machine 
- The need for parallelism has become more acute with multicore CPUs
<hr>

## Amdah's Law
Identifies ==performance gains== from ==adding additional cores== to an application that has both serial and parallel components
![[Pasted image 20230227164223.png]]

That is, if application is 75% parallel / 25% serial, moving from 1 to 2 cores results in speedup of 1.6 times
$$ speedUp <= 1/(S+((1-S)/N)) = 1/(0.25 + 0.75/2) = 1.6 $$
Serial portion of an application has disproportionate effect on the performance gained by adding additional cores
<hr>

## User-level and Kernel-level Threads
### User-level Threads
#### Pros
- Fast (no system calls are required to create them, no switch between user/kernel space) 
- Can be implemented in an OS which does not support threads
#### Cons
- Scheduling is required 
- Requires non-blocking system calls (if one thread invokes a system call, all threads need to wait)

![[Pasted image 20230227164753.png]]
<hr>
### Kernel-level Threads
#### Pros
- The OS can give more resources to a process that has more threads
- Good for applications with many I/O requests 
#### Cons
- Slow, additional system overhead

![[Pasted image 20230227164951.png]]
<hr>

## Multithreading Models

### Many-to-One
- Many user-level threads mapped to single kernel thread 
- One thread blocking causes all to block 
- Multiple threads may not run in parallel on multicore system because only one may be in kernel at a time 
- Few systems currently use this model 
- Examples: 
	- Solaris Green Threads 
	- GNU Portable Threads
![[Pasted image 20230227165613.png]]
<hr>

### One-to-One
- Each user-level thread maps to kernel thread 
- Creating a user-level thread creates a kernel thread 
- More concurrency than many-to-one 
- Number of threads per process sometimes restricted due to overhead 
- Examples 
	- Windows 
	- Linux 
	- Solaris 9 and later
![[Pasted image 20230227165651.png]]
<hr>

### Many-to-Many
- Allows many user level threads to be mapped to many kernel threads 
- Allows the operating system to create a sufficient number of kernel threads 
	- Solaris prior to version 9 
	- Windows with the ThreadFiber package
![[Pasted image 20230227165744.png]]

