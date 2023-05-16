Deadlock - situation where two or more processes are waiting indefinitely for an event that can be caused by one of the waiting processes


# System Model

- A system consists of a finite number of resources to be distributed among a number of competing processes.
- Let there are m number of Resources  as (R1, R2, . . ., Rm), (e.g., CPU cycles, memory space, I/O devices).
- Also, each resource type has Wi instances.
- If a system has two CPUs, then the resource type CPU has two instances. Similarly, the resource type printer may have five instances.

- A process must ==request== a resource before using it and must ==release== the resource after using it.
- Also, a process may request as many resources as it requires to carry out its designated task.
- However, the number of resources requested may not exceed the total number of resources available in the system. (e.g., demand = 3 printers and available = 2 printers)

## Utilizing resources

Each process utilizes a resource as follows:
- Request - The process requests the resource
- Use - Process uses resource
- Release - process releases resource


Deadlocks may also involve different resource types. For example, consider a system with one printer and one DVD drive. Suppose that process Pi is holding the DVD and process Pj is holding the printer. If Pi requests the printer and Pj requests the DVD drive, a deadlock occurs.


# Necessary conditions for Deadlocks
- **Mutual Exclusion**
	- At least one resource must be held in a non-sharable mode; that is, only one process at a time can use the resource. If another process requests that resource, the requesting process must be delayed until the resource has been released
- **Hold and Wait**
	- A process must be holding at least one resource and waiting to acquire additional resources that are currently being held by other processes.
- **No Preemption**
	- Resources cannot be preempted; that is, a resource can be released only voluntarily by the process holding it, after that process has completed its task.
- **Circular Wait**
	- A set {P0, P1, ..., Pn} of waiting processes must exist such that P0 is waiting for a resource held by P1, P1 is waiting for a resource held by P2, ..., Pn−1 is waiting for a resource held by Pn, and Pn is waiting for a resource held by P0

# Resource Allocation Graph
Deadlock can be presented with the help of ==Resource-Allocation Graph==. A graph can be represented as; 
$$G = (V, E)$$where, 
V shows vertices and 
E shows edges.

## Edges
- **Request Edge**: Pi → Rj shows that process Pi has requested an instance of resource type Rj and is currently waiting for that resource.
- **Assignment Edge**: Rj → Pi shows that an instance of resource type Rj has been allocated to process Pi. 
- **Claim Edge** : Pi → Rj indicates that process Pi may request resource Rj at some time in the future.
	- represented by dashed line
	- Claim edge converts to request edge when a process requests a resource.
	- Request edge converted to an assignment edge when the  resource is allocated to the process.
	- When a resource is released by a process, assignment edge reconverts to a claim edge.
![[Pasted image 20230429201828.png]]

Claim edge example:
![[Pasted image 20230429203953.png]]


## Graph with and without deadlocks
![[Pasted image 20230429202043.png]]
left one has deadlock
right one doesn't

## Basic Facts
- If Graph (G) contains no cycles then there will not be deadlock
- If Graph (G) contains cycles then:
	- if only one instance per resource type, then deadlock is must.
	- If several instances per resource type, then there is a possibility of deadlock.





# Deadlock Handling
There are 3 ways:
- We can use a protocol to prevent or avoid deadlocks, ensuring that the system will never enter a deadlocked state.
- We can allow the system to enter a deadlocked state, detect it, and recover.
- We can ignore the problem altogether and pretend that deadlocks never occur in the system.

The third solution is the one used by most operating systems, including Linux and Windows. It is then up to the application developer to write programs that handle deadlocks.

==Prevention in better than cure==

## Deadlock prevention
A set of methods to ensure that at least one of the necessary conditions must not hold. These methods prevent deadlocks by constraining how requests for resources can be made

- **Mutual Exclusion** 
	- not required for sharable resources (e.g., read-only files); must hold for non-sharable resources.
- **Hold and wait**
	- must guarantee that whenever a process requests a resource, it does not hold any other resources. 
	- Require process to request and be allocated all its resources before it begins execution.
	- Allow process to request resources only when the process has no resources allocated to it.
	- face such issues as low resource utilization and starvation possibility
- **No Preemption** 
	- If a process that is holding some resources requests another resource that cannot be immediately allocated to it, then all resources currently being held are released. 
	- Preempted resources are added to the list of resources for which the process is waiting.
	- Process will be restarted only when it can regain its old resources, as well as the new ones that it is requesting.
	- This protocol is often applied to resources whose state can be easily saved and restored later, such as CPU registers and memory space. It cannot generally be applied to such resources as mutex locks and semaphores.
- **Circular Wait**
	- It impose a total ordering of all resource types, and require that each process requests resources in an increasing order of enumeration.
 

## Deadlock Avoidance
Requires that the operating system be given additional information in advance concerning which resources a process will request and use during its lifetime. 
With this additional knowledge, the operating system can decide for each request whether or not the process should wait.

- It requires that the system has some additional a priori information available.
- Simplest and most useful model requires that each process declare the maximum number of resources of each type that it may need.
- The deadlock-avoidance algorithm dynamically examines the resource-allocation state to ensure that there can never be a circular-wait condition
- Resource-allocation state is defined by the number of available and allocated resources, and the maximum demands of the processes.

### Deadlock state
If system is in Safe State, No Deadlock.
If a system is in Unsafe State, Possibility of Deadlock.

==How to choose algorithm to avoid deadlock==
If there is a single instance of a resource, the resource allocation graph algorithm is used.
However, if there are multiple instance of a resource, then banker’s algorithm can be used.

### Banker's Algorithm
