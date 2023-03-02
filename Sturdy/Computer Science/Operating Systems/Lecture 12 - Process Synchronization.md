## Background 
A cooperating process is the one that can affect or be affected by other processes executing in the system.
![[Pasted image 20230301135104.png]]
- Concurrent access to shared data may result in ==Data Inconsistency==!
- There is a need in techniques that ensures the ==orderly execution== of cooperating processes that share logical address space, so that ==data consistency is maintained==.


### Producer and Consumer problem
- A producer process produces information that is consumed by a consumer process.
	- For example, a compiler may produce assembly code, which is consumed by assembler.
	- The assembler, in turn, may produce object modules, which are consumed by the loader.
- One Possible solution to Producer Consumer Problem is to use ==Shared Memory==.
- To run Producer-Consumer processes to run concurrently, there should be a ==Buffer of Items== that can be filled by producer and emptied by consumer.
- This buffer can be placed in a region of memory that is shared between the Producer and Consumer Processes at the same time.

![[Pasted image 20230301140408.png]]

#### There are 2 types of Buffers
- Unbound buffer - There is no practical limit in the size of the buffer. The consumer may have to wait for the new items, but the producer can always produce.
- Bounded buffer - There is a fixed buffer size. The consumer must wait if the buffer is empty. The producer must wait if the buffer is full

#### Counter
- initially it is zero
- increments when producer adds smth to buffer
- decrements when consumer removes smth from buffer

#### Example
- Let's assume counter value is 5
- The producer execute `counter++` while consumer execute `counter--`
- The only correct value should be 5, but without proper synchronization we may face the problem below:
![[Pasted image 20230301141330.png]]

A situation like this, where several processes access and manipulate the same data concurrently and the outcome of the execution depends on the particular order in which the access takes place, is called as ==race condition==.

That's why we need process synchronization

There exist multiple synchronization techniques that are designed to solve [[Critical Section Problem]] 

