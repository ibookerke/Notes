- Another hardware solution to the [[Critical Section Problem]].
- There is a shared lock variable, which can test and set at the same time.
- Before entering into critical section, a process inquires about the lock. (==Test==)
- If it is locked, it keeps on waiting till it becomes free.
- If it is not locked, it takes the lock and execute the [[Critical Section]]. (==Set==)

![[Pasted image 20230301152414.png]]

Usually being implemented using [[Semaphore]]
