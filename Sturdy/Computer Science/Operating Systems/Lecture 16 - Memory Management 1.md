# Background
- Program must be brought (from disk) into memory and placed within a process for it to be run
- Main memory and registers are the only items CPU can access directly 
- Memory unit only sees a stream of addresses + read requests, or address + data and write requests 
- Register access in one CPU clock (or less) 
- Main memory can take many cycles, causing a ==stall== 
- ==Cache== sits between main memory and CPU registers 
- Protection of memory required to ensure correct operation\

# Address binding of Instructions and Data to Memory

Address binding of instructions and data to memory addresses can happen at three different stages:

- **Compile time**: If memory location known a priori, absolute code can be generated; must recompile code if starting location changes 
- **Load time**: Must generate relocatable code if memory location is not known at compile time 
- **Execution time**: Binding delayed until run time if the process can be moved during its execution from one memory segment to another 
	- Needs hardware support for address maps (e.g., base and limit registers)

![[Pasted image 20230429205453.png]]

- A pair of base and limit registers define the logical address space 
	- e.g., the Intel 8088 (Introduced on July 1, 1979) 
- CPU must check every memory access generated in user mode to be sure it is between base and limit for that user 
- Applicable in Contiguous allocation
![[Pasted image 20230429205630.png]]

![[Pasted image 20230429205655.png]]
