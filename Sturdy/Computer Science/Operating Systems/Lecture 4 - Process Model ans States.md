## Process concept
==**Program**== - a file in storage medium that can be executed
==**Process**== - a program in execution; process execution must progress in sequential fashion

Multiple parts
- The program code, also called ==text section== 
- Current activity including ==program counter==, processor registers 
- ==Stack== containing temporary data 
	- Function parameters, return addresses, local variables 
- ==Data section== containing global variables 
- ==Heap== containing memory dynamically allocated during run time

### Heap vs Stack
- Stack has an ordered and structurized data
- Heap is sotring data in a pile

//TODO 
Escape Analysis during allocation

![[Pasted image 20230227130419.png]]

Program - passive(stored as ==executable file==)
Process - active

A program becomes a process when the executable file loaded into memory
One program can be several processes


## Process States
As a process executes, it changes **state**
### States:
- ==new==: The process is being created 
- ==running==: Instructions are being executed 
- ==waiting==: The process is waiting for some event to occur 
- ==ready==: The process is waiting to be assigned to a processor 
- ==terminated==: The process has finished execution
![[Pasted image 20230227131642.png]]

## Process Control Block([[PCB]])

Information associated with each process (also called task control block) 
- Process state – running, waiting, etc 
- [[Program Counter]] – location of instruction to next execute 
- CPU registers – contents of all process-centric [[Register]]s 
- CPU scheduling information- priorities, scheduling queue pointers 
- Memory-management information – memory allocated to the process 
- Accounting information – CPU used, clock time elapsed since start, time limits 
- I/O status information – I/O devices allocated to process, list of open files

## Context Switch
![[Pasted image 20230227132533.png]]

- When CPU switches to another process, the system must save the state of the old process and load the saved state for the new process via a context switch
- ==Context== of a process represented in the [[PCB]]
- Context-switch time is overhead; the system does no useful work while switching
	- The more complex the OS and the PCB -> the longer the context switch
- Time dependent on hardware support
	- Some hardware provides multiple sets of registers per CPU -> multiple contexts loaded at once

## Process Scheduling
- Maximize CPU usage, quickly switch processes for time-sharing 
- Process scheduler selects among available processes for next execution on the CPU(s) 
- Maintains scheduling queues of processes 
	- Job queue – set of all processes in the system 
	 - Ready queue – set of all processes residing in main memory, ready and waiting to execute 
	 - Device queues – set of processes waiting for an I/O device 
	 - Processes migrate among the various queues


## Operations on Processes

System must provide mechanisms for:
- process creation
- process termination

### Process Creation
- Parent process creates children processes, which, in turn create other processes, forming a tree of processes
- Generally, process identified and managed via a process identifier (==pid==) 
- Resource sharing options 
	- Parent and children share all resources 
	- Children share subset of parent’s resources 
	- Parent and child share no resources 
- Execution options 
	- Parent and children execute concurrently 
	- Parent waits until children terminate

There are two ways of creating child process
- Address space 
	- Child duplicate of parent: `dubplicates the parent's code and `[[Program Counter]]` and execute it` 
	- Child has a program loaded into it:  `use another program and executes it, however it is still child of parent process`
- UNIX examples 
	- fork() system call creates new process 
	- exec() system call used after a fork() to replace the process’ memory space with a new program

![[Pasted image 20230227135614.png]]

![[Pasted image 20230227141835.png]]

### Process Termination
- Process executes last statement and then asks the operating system to delete it using the exit() system call.
	- Returns status data from child to parent (via wait()) 
	- Process’ resources are deallocated by the operating system 
- Parent may terminate the execution of children processes using the abort() system call. Some reasons for doing so: 
	- Child has exceeded allocated resources 
	- Task assigned to child is no longer required 
	- The parent is exiting and the operating systems does not allow a child to continue if its parent terminates

Some operating systems do not allow a child to exist if its parent has terminated. If a process terminates, then all its children must also be terminated. 
- ==cascading termination==. All children, grandchildren, etc. are terminated. 
- The termination is initiated by the operating system. 

The parent process may wait for termination of a child process by using the wait() system call. The call returns status information and the pid of the terminated process 
```
pid = wait(&status);
```
- If no parent is waiting (did not invoke wait()), the child process is a ==[[Zombie]]== 
- If the parent terminated without invoking wait(), the child process is an ==[[Orphan]]==


## Code examples

### wait()
```
#include <stdio.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>

int main(){ 
	int p = fork(); 
	if (p == 0) { 
		printf("Hello from child\n"); 
		sleep(2); 
	} else { 
		printf("Hello from parent\n"); 
		wait(NULL); 
		printf("Child has terminated\n"); 
	} 
	printf("Bye\n");
	 
	return 0; 
}
```

### exec() and wait()

```
#include <stdio.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>

int main(){
	char *argv[3] = {"Command", "-l", NULL};
	int status = 1;
	int p = fork();
	
	if ( p == 0 ) {
		execvp( "ls", argv );
	}
	
	wait( &status );
	printf( "Finished executing the parent process\n");
	
	return 0;
}
```

