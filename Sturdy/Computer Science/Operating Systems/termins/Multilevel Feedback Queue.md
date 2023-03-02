it is an implementation of [[Multilevel Queue]]

- A process can move between the various queues
- Aging can be implemented this way 

![[Pasted image 20230301120358.png]]

- Multilevel-feedback-queue scheduler defined by the following parameters: 
	- number of queues 
	- scheduling algorithms for each queue 
	- method used to determine when to upgrade a process 
	- method used to determine when to demote a process 
	- method used to determine which queue a process will enter when that process needs service

### Benefits:
- if process use too much CPU it is moved on a layer with lower priority
- the scheme leaves I/O bound and interactive processes in the higher priority queues
- in addition if process wait too long in lower-priority queue it is being raised to higher by aging
