## Round Robin
- Each process gets a small unit of CPU time (==time quantum q==), usually 10-100 milliseconds. After this time has elapsed, the process is preempted and added to the end of the ready queue. 
- If there are n processes in the ready queue and the time quantum is q, then each process gets 1/n of the CPU time in chunks of at most q time units at once. No process waits more than (n-1)q time units. 
- **Timer interrupts** at every quantum to schedule next process 
- Performance 
	- q large -> FIFO
	- q small -> q must be large with respect to context switch, otherwise overhead is too high

![[Pasted image 20230228204551.png]]
![[Pasted image 20230228205311.png]]
