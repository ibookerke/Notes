## Basic Concepts

CPU is always switching between running and waiting state

- Maximum CPU utilization obtained with multiprogramming 
- ==CPU-I'O Burst Cycle== – Process execution consists of a **cycle** of [[CPU Burst]] and [[IO Burst]] wait 
- ==CPU burst== followed by ==I/O burst== 
- CPU burst distribution is of main concern

![[Pasted image 20230228092609.png]]

Before process termination there will be a final [[CPU Burst]] where system requests for termination of the process

## CPU Scheduler 
==Short-term scheduler== selects from among the processes in ==ready queue==, and allocates the CPU to one of them 
- Queue may be ordered in various ways (e.g., a FIFO or a Priority Queue)  

## Preemptive & non-preemptive scheduling

### CPU Schedule
Whenever the CPU becomes idle, the operating system must select one of the processes in the ready queue to be executed. The selection process is carried out by the short-term scheduler (or CPU scheduler). The scheduler selects a process from the processes in memory that are ready to execute and allocates the CPU to that process. 

### Dispatcher
The dispatcher is the module that gives control of the CPU to the process selected by the short-term scheduler. The time it takes for the dispatcher to stop one process and start another running is known as the ==dispatch latency==. 

### CPU-scheduling decisions may take place under 4 circumstances
1. Switches from running to waiting state 
2. Switches from running to ready state (e.g. interrupt or smth)
3. Switches from waiting to ready (e.g. completion of I/O)
4. Terminates

There are no choices of scheduling for:
1. running -> waiting
4. terminating
processes, since we are just choosing a new process for execution from queue.
Such scheduling scheme is called ==non-preemptive==/cooperative
The process volunteerly gives up the CPU since their execution ended.

However there are some for 
2. running -> ready
3. wairing -> ready
Scheduling scheme for this circumstances are called ==preemptive==. So there are processes when CPU can be taken away from the processes even before it has completed its execution

## Scheduling criteria
The criterias the CPU takes into consideration while how to schedult procceses
-   CPU utilization – keep the CPU as busy as possible
-   Throughput - # of processes that complete their execution per time unit
-   Turnaround time - amount of time to execute a particular process
-   Waiting time - amount of time a process has been waiting in the ready queue(Sum of periods spent in wairing queue in the ready state)
-   Response time - amount of time it takes from when a request was submitted until the first response is produced(when process can start producing some output earlier and can continue computing new results while previous results are being output)

## Scheduling algorithms
- ### [[FCFS]]
- ### [[SJF]]


## Efficiency calculations

==turnaround time== = completion time - arrival time
==waiting time== = turnaround time - burst time 
==Response time== = Time at which the process gets the CPU for the first time - Arrival time