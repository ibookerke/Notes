## fork()
Fork is a system call used for creating a new process 
- The new process is called child process, 
- Children processes run ==concurrently== with the parent process. 
- After a new child process is created, both processes will execute the next instruction following the fork() system call. 
- A child process uses the same [[Program Counter]], same CPU [[Register]]s, same open files that are used in the parent process

It takes no parameters and returns an integer value. Below are different values returned by fork(). 
- **Negative Value**: creation of a child process was unsuccessful. 
- **Zero**: Returned to the newly created child process. 
- **Positive value**: Returned to parent or caller. The value contains the process ID of the newly created child process.

![[Pasted image 20230227144756.png]]


