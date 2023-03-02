### First-Come, First-Served(FCFS)
- The process that requests the CPU first is allocated the CPU first.
- Implementation - FIFO queue
- When process enters ready queue its [[PCB]] is linked to tail of queue
- it is ==nonpreemptive==
- such thing as [[Convoy Effect]] may occur
![[Pasted image 20230228191350.png]]