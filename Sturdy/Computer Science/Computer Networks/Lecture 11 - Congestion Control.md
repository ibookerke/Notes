
# Congestion Control
- When packets are lost – packet retransmissions solve this. 
- But packet retransmissions does not solve the cause of packet loss. 
- Packets could be lost due to receiver buffer overflow -> [[Flow control]] service of TCP solves. 
- Packets can also be lost on the way between sender and receiver, at routers’ buffers.

## Problem Definition
informally “too many sources sending too much data too fast for network to handle”
#### Manifestations
- lost packets (buffer overflow at routers) 
- long delays (queueing in router buffers)

# Causes/costs of congestion
## Scenario 1
![[Pasted image 20230327144831.png]]
There is large queueing delays since the packet arrival rate nears the link capacity
<hr>

## Scenario 2
### A
![[Pasted image 20230327151148.png]]
- Perfect knowledge
- almost no loss
<hr>

### B
![[Pasted image 20230327151521.png]]
- Known loss
- Here comes the first congestion cose - ==Retransmissions==
- We can observe the gap emergence between the sending and receiving rates
<hr>

### C
![[Pasted image 20230327151733.png]]
- Here comes the most realistic scenario when the retransmissions cause ==Diplicates==
- The difference between the sending and reciving rates grows

## Scenario 3
![[Pasted image 20230327152452.png]]
Another Congestion cost: ==when packet dropped, any upstream transmission capacity used for that packet was wasted!==
<hr>


# TCP Congestion Problem Solution
Controls the sender rate based on the congestion level in the network 
- No congestion -> increase rate 
- Congestion -> decrease rate

CWND - Congestion Window

## Additive Increase/Multiplicative Decrease
- approach:sender increases transmission rate (window size), probing for usable bandwidth, until loss occurs 
	- additive increase: increase cwnd by ==1 MSS== every RTT until loss detected 
	- multiplicative decrease: cut cwnd in half after loss
![[Pasted image 20230327153201.png]]

![[Pasted image 20230327155001.png]]

# TCP Congestion Control Algorithm
## 3 Components:
- **Slow Start**
- **Congestion Avoidance**
- **Fast Recovery**

### Slow Start
- when connection begins, increase rate exponentially until first loss event: 
	- initially cwnd = 1 MSS 
	- double cwnd every RTT 
	- done by incrementing cwnd for every ACK received 
- **summary**: initial rate is slow but ramps up exponentially fast
![[Pasted image 20230327155310.png]]
### Congestion Avoidance
The slow start algorithm is used when cwnd < ssthresh, otherwise, the congestion avoidance algorithm is used – increment cwnd by 1 MSS

### Detecting and Reacting to Loss
- loss indicated by timeout
	- cwnd set to 1 MSS; 
	- window then grows exponentially (as in slow start) to threshold, then grows linearly
- loss indicated by 3 duplicate ACKs:  
	- dup ACKs indicate network capable of delivering some segments 
- Reacting techniques(Variations of [[Fast Retransmit]]):
	- TCP RENO
		- cwnd is cut in half window, adds 3 MSS then grows linearly
	- TCP Tahoe 
		- always sets cwnd to 1 (timeout or 3 duplicate acks)
![[Pasted image 20230327161300.png]]
![[Pasted image 20230327161328.png]]

# TCP Throughput

![[Pasted image 20230327161827.png]]


# TCP Fairness
==fairness goal==: 
- if K TCP sessions share same bottleneck link of bandwidth R, each should have average rate of R/K

## Fairness and UDP 
- multimedia apps often do not use TCP 
	- do not want rate throttled by congestion control 
- instead use UDP: 
	- send audio/video at constant rate, tolerate packet loss

## Fairness, parallel TCP connections
- application can open multiple parallel connections between two hosts 
- web browsers do this 
- e.g., link of rate R with 9 existing connections: 
	- new app asks for 1 TCP, gets rate R/10 
	- new app asks for 11 TCPs, gets R/2