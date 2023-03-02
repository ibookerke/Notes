
- A priority number (integer) is associated with each proces
- The CPU is allocated to the process with the highest priority (smallest integer → highest priority)
- Can be both preemptive and nonpreemptive
- [[SJF]] is priority scheduling where priority is the inverse of predicted next CPU burst time
- Problem: ==Starvation== – low priority processes may never execute or execute very late 
- Solution: ==Aging== – as time progresses increase the priority of the process

![[Pasted image 20230228202908.png]]
