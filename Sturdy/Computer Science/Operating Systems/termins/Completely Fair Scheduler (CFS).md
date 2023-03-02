The Completely Fair Scheduler is a process scheduler that was merged into the 2.6.23 release of the Linux kernel and is the default scheduler of the tasks of the SCHED_NORMAL class

## Main Idea
- To have a simple list of tasks 
	- Ordered by how much time they ran 
	- Least time to most time  
- Always pick the “neediest” task to run 
	- Until it is no longer neediest 
	- Then re-insert old task in the timeline 
	- Schedule the new neediest

![[Pasted image 20230301124325.png]]
![[Pasted image 20230301124336.png]]
### Lists are costly

- Idea: to use a tree 
	- use [[Red-black Tree]]
- log(n) time for: 
	- Picking next task (i.e., search for left-most task) 
	- Putting the task back when it is done (i.e., insertion)

### Node Value Calculation

- Global virtual clock: ticks at a fraction of real time 
	- Fraction is number of total tasks 
- Each task counts how many clock ticks it has had 
- Example: 10 tasks 
	- Global vclock ticks once every 10 real ticks 
	- Each task scheduled for one real tick; advances local clock by one tick 
- Task’s ticks ([[Vruntime]]) -> value in [[Red-black Tree]]  
	- Shortest [[Vruntime]] gets serviced first 
- No more runqueues 
	- Just a single tree-structured timeline

![[Pasted image 20230301130805.png]]
#### New Tasks
 - What about a new task? 
	- If task ticks start at zero, doesn’t it get to unfairly run for a long time? 
- Strategies: 
	- Could initialize to current time (start at right) 
	- Could get half of parent’s deficit


### Priorities
- In CFS, priorities weigh the length of a task’s “tick” 
- [[Vruntime]] = q(quantum) • (a weight based on nice value) 
- Result: Higher-priority tasks run longer, lowpriority tasks make some progress

### Scheduling Latency
- Equivalent to time slice across all processes 
	- To set/get type: `sysctl kernel.sched_latency_ns` 
- Each process gets equal proportion of slice 
	- Timeslice(task) = latency/N_tasks
	- To set/get: `sysctl kernel.sched_min_granularity_ns`
	- Too many tasks? Timeslice = N_tasks * min_granularity 
- ==Priority== through proportional sharing 
	- Task gets share of CPU proportional to relative priority 
	- Timeslice(task) = `Timeslice(t) * prio(t) / Sum_all_t’(prio(t’))`

