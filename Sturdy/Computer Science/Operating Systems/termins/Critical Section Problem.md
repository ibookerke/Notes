### Critical Section Problem
- Each process has a [[Critical Section]]
- When a process is executing in its [[Critical Section]], no other process is allowed to execute in its critical section.
- In other words, no two processes are executing in their critical section at the same time.
- The critical section problem is to design a protocol that the processes can use to cooperate.

#### Implementation
- Each process must request permission to enter its [[Critical Section]]
- There is [[Entry Section]]
- [[Critical Section]] may be followed by Exit section
- The remainding code is the remainder section

#### Soluction to critical problem section
1. [[MUTEX]]
2. Progress 
	- If no process is executing in its critical section and there exist some processes that wish to enter their critical section, then only those processes which are not executing in their remainder section can participate in deciding which will enter its critical section next and this selection cannot be postponed indefinitely.
1. Bounded Waiting
	- A bound must exist on the number of times that other processes are allowed to enter their critical sections after a process has made a request to enter its critical section and before that request is granted.

