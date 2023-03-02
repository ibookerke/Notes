### Acquire() and Release() Lock
- A simplest hardware solution to the Synchronization Problem.
- There is a shared lock variable, which can take either of two values, 0 or 1.
- Before entering into critical section, a process inquires about the lock.
- If it is locked, it keeps on waiting till it becomes free.
- If it is not locked, it takes the lock and execute the critical section.
- Lock = 0 shows vacant and Lock = 1 shows busy
![[Pasted image 20230301151306.png]]
