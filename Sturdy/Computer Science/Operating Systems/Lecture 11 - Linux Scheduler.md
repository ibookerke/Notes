## Tips
### Linux priorities
- ==nice== - used at user space(==from -20 to +19==)
- `nice -n <value> <program_name>` (to run a new process with a given priority)
	- e.g., `nice -n -5 libreoffice`
- `renice <value> <pid>` (to change the priority of a running process)
	- e.g. `renice -5  765265`

### Scheduling policies in Linux
- `chrt -m` (SCHED_OTHER = default one) -  **sets or retrieves the real-time scheduling attributes of an existing PID, or runs command with the given attribute**

![[Pasted image 20230301123543.png]]

### Scheduling Statistics
`cat /proc/<pid>/schedstat`
- Time spent on the CPU 
- Time spent waiting on the “queue” 
- Number of timeslices run

## The Linux Scheduler
- [[Completely Fair Scheduler (CFS)]]
	- Linux 2.6.23 – now (since 2007) 
	- Replaced the O(1) scheduler
- Goal: each task to make proportional progress on the CPU
	- No starvation

### Ideal Scheduling from [[Round Robin]] Concept
![[Pasted image 20230301123936.png]]

