[[Test and Set Lock]]s pattern of implementing the [[MUTEX]]

It is also may be implemented using [[Semaphore]]s


## Classic Problems of Process Synchronization
- ### [[Bounded Buffer Problem]]
	- In order to solve this problem we will be using [[Semaphore]]s
		1. m([[MUTEX]]): A binary semaphore which is used to acquire and release lock.
		2. empty: A counting semaphore contains the empty slots of the buffer. Since initially all the slots are empty; therefore, the value of empty = total number of slots in buffer.
		3. full: A counting semaphore contains the filled slots of the buffer. Since initially no slot is filled; therefore, the value of full = 0.
		
		![[Pasted image 20230301165112.png]]
- ### Reader-Writers Problem
	- Here, we can use two [[Semaphore]]s and an integer variable, as follows:
		1. mutex: A semaphore (initialized to 1) which is used to ensure mutual exclusion when readcount is updated (i.e., when reader enters/exits the critical-section).
		2. wrt: A semaphore (initialized to 1)  common to both (i.e., reader and writer) processes.
		3. readcount: An integer variable (initialized to 0) that keeps the record of processes reading the database at a given time
		
		![[Pasted image 20230301170644.png]]
- ### The Dinning Philosophers Problem
	 ![[Pasted image 20230301170853.png]]
	 - Possible solution for the problem:
		 - One possible solution is to represent each fork/chopstick with a [[Semaphore]].
		 - A philosopher can grab a fork/chopstick by executing a wait( ) operation on that semaphore.
		 - He can release the forks/chopsticks by using a signal( ) operation on the appropriate semaphore.
		 - Thus, the shared data are
		 - Where all the elements of chopsticks are initialized to 1.
		![[Pasted image 20230301171708.png]]


Although this solution guarantees that no two neighbors are eating simultaneously. However, it can still create a deadlock. 

Suppose that all philosophers are hungry at the same time, and each grabs their left fork/chopstick. All the elements of fork/chopstick will be equal to zero.

When each philosopher tries to grab his right fork/chopstick, he will be delayed forever.

Remedies to avoid deadlock:
- allow at most 4 phylosophers to sit at a table
- Allow a philosopher to pickup his forks/chopsticks only if both of the forks/chopsticks are available. (To do this, philosopher must pick up forks/chopsticks in the critical-section.)
- Use an asymmetric approach; i.e., an odd philosopher picks up his left fork/chopstick and then his right fork/chopstick. Whereas, an even philosopher picks up his right fork/chopstick first and then his left fork/chopstick.

Another way of avoiding the problems with deadlocks and stuff is using [[Monitors]]

