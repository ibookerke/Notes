### Shortest-Job-First (SJF)
- Associate with each process the length of its next CPU burst
	- Use these lengths to schedule the process with the shortest time
- SJF is optimal – gives ==minimum average waiting== time for a given set of processes
	- The difficulty is knowing the length of the next CPU request
![[Pasted image 20230228193715.png]]
There also a ==preemptive== implementation, when we are reassiging CPU during runtime on process arrival. 
![[Pasted image 20230228194137.png]]

turnaround time = completion time - arrival time
waiting time = turnaround time - burst time 
Response time = Time at which the process gets the CPU for the first time - Arrival time

P1: 17 - 0  = 17    17 - 8 = 9
P2: 5 - 1 = 4          4 - 4 = 0
P3: 26 - 2 = 24      24 - 9 = 15
P4: 10 - 3 = 7       7 - 5 = 2
AVG:      13               6.5

