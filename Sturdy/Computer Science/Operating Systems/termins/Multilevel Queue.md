## Basics
- It is a class of scheduling algorightms which is used when processes are easily classified into different groups.
- It partitions the ready state queue into several separate queues by the process properties such as size, priority and type

We classify process into 2 groups:
- ==Foreground==/Interactive 
	- direct interaction with the user
	- need to be quick and interactive
- ==Background==/Batch
	- may not be in direct interaction with user
	- doesn't have to be as fast as foreground

- Base on the needs they have different response-time requirements and different scheduling needs.
- Each queue has its own scheduling algorithm

## Choosing algos for queues

Lets choose the best algorithms for foregound and background queues 
- foreground queue can be scheduled using [[Round Robin]], since it has a good timesharing and evenly shares resources between processes
- background is used to be implemented using [[FCFS]] since the average responce time and average waiting time are not pioritized 


## Scheduling among queues
- There should also be a scheduling among the queues
- usually implemented as fixed-priority ==preemptive== scheduling
- i.e. foreground queue may have an absolute priority over the background

![[Pasted image 20230301114312.png]]

In this example Student processes will start executing if all the above queues are empty.