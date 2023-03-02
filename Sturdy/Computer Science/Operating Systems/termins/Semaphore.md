- Semaphore proposed by Edsger Dijkstra, is a technique to manage concurrent processes by using a simple integer value, known as Semaphore.
- Semaphore is simply a nonnegative variable which is shared between threads.
-  This variable helps to solve the [[Critical Section Problem]] and to achieve process synchronization in the multiprocessing environment.
- A semaphore S in an integer variable that, apart from initialization, is accessed only through two standard atomic operations: wait( ) and signal( ).
- ==Wait==( ) is represented as ==P== (from the Dutch word proberen, which means “to test”)
	- check if S > 0, which means it is free to use, while cycle breaks and S process decrements S valum stating that he has reserved the [[Critical Section]] for its needs
- ==Signal==( ) is represented as ==V== (from the Dutch word verhogen, means “to increment)
	- Just letting others know that the [[Critical Section]] is free to use

![[Pasted image 20230301152906.png]]

1. Binary Semaphore
The value of a binary semaphore can range between only 0 and 1. On some systems, binary semaphores are known as [[MUTEX]] locks, as they are locks that provide mutual exclusion.
2. Counting Semaphore
Its value can range between an unrestricted domain. It is used to control access to a resource with multiple instances.

## Semaphores Disadvantages
1. Busy Waiting
	- While a process is in its [[Critical Section]], any other process that tries to enter its [[Critical Section]] must loop continuously in the entry code.
	- Busy waiting wastes CPU cycles that some other process might use productively.
	- When a process executes the wait( ) operation and finds the semaphore value is not positive, it must be added to the waiting/blocked queue
	- The process can use ==wakeup== operation when the critical-section is free to use

![[Pasted image 20230301153412.png]]
2. Deadlock and Starvation
- The implementation of a semaphore with a waiting queue may result in a situation where two or more processes are waiting indefinitely for an event that can be caused by one of the waiting processes.
![[Pasted image 20230301163035.png]]

3. Priority Inversion
- It is a scheduling problem where low priority process holds a lock needed by the higher priority process. It can be solved by using [[Priority Inheritance Protocol]]s.
- Let, there are three processes with priorities L(Low), M(Medium), and H(High).
- Process with priority L is holding a resource, which is further required by process with H priority. Whereas, process with priority M can preempt process with L priority.
- One possible solution is to have only two priorities. However, it is not an efficient solution.
- Priority inheritance protocols allows process with Lower Priority to inherit the Higher Priority for sometime. Hence, process with M priority cannot preempt the running process.

