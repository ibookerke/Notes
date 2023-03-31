# Random access protocols

- When node has packet to send 
	- transmit at full channel data rate R. 
	- no a priori coordination among nodes 
- two or more transmitting nodes ➜ “collision” , 
- random access MAC protocol specifies: 
	- how to detect collisions 
	- how to recover from collisions (e.g., via delayed retransmissions) 
- examples of random access MAC protocols: 
	- slotted ALOHA 
	- ALOHA 
	- CSMA,
	- CSMA/CD, 
	- CSMA/CA

## Slotted ALOHA
### Assumptions
- all frames same size – L bits 
- time divided into equal size slots – L/R seconds (time to transmit 1 frame) 
- [[Link Layer Nodes]] start to transmit only at the beginning of slots
- nodes are synchronized 
- if 2 or more nodes transmit in slot, all nodes detect collision before the slot ends

### Operation
- When node obtains fresh frame, transmits in next slot 
	- if no collision: node can send new frame in next slot 
	- if collision: node retransmits frame in each subsequent slot with prob. p until success, where 0 < p < 1

![[Pasted image 20230330202420.png]]

### Pros:
- single active node can continuously transmit at full rate of channel 
- highly decentralized: only slots in nodes need to be in sync 
- simple
### Pros:
- collisions, wasting slots 
- idle slots 
- nodes may be able to detect collision in less than time to transmit packet 
- clock synchronization

### Efficiency
Long-run fraction of successful slots (many nodes, all with many frames to send)
at best: channel used for useful transmissions 37% of time!


## Pure (Unslotted) ALOHA
![[Pasted image 20230330203538.png]]
- unslotted Aloha: simpler, no synchronization
- when frame first arrives
	- transmit immediately
- collision probability increases:
	- frame sent at t0 collides with other frames sent in [t0 -1,t0+1]
![[Pasted image 20230330203559.png]]
### Efficiency
![[Pasted image 20230330203627.png]]

# CSMA (carrier sense multiple access)
## Assumption
- Listen before transmit
- if channel sensed idle: transmit entire frame
- if channel sensed busy, defer transmission
- human analogy: don’t interrupt others!

## Collisions
collisions can still occur:
- propagation delay means two nodes may not hear each other’s transmission
if Colision
- entire packet transmission time waste
	- distance & propagation delay play role in in determining collision probability

# [[CSMA-CD]]

### Algorithm
1) [[NIC]] receives datagram from network layer, creates frame 
2) If [[NIC]] senses channel idle, starts frame transmission. If [[NIC]] senses channel busy, waits until channel idle, then transmits. 
3) If [[NIC]] transmits entire frame without detecting another transmission, [[NIC]] is done with frame !
4) If [[NIC]] detects another transmission while transmitting, aborts the transmission. 
5) After aborting, [[NIC]] enters binary (exponential) backoff:
	1) after mth collision, [[NIC]] chooses K at random from {0,1,2, …, 2m-1}. NIC waits K·512 bit times, returns to Step 2 
	2) longer backoff interval with more collision

![[Pasted image 20230330204924.png]]

# “Taking turns” MAC protocols

## Assumption
- channel partitioning MAC protocols:
	- share channel efficiently and fairly at high load 
	- inefficient at low load: delay in channel access, 1/N bandwidth allocated even if only 1 active node!
- random access MAC protocols 
	- efficient at low load: single node can fully utilize channel 
	- high load: collision overhead

“taking turns” protocols look for best of both worlds!


## Polling
- master node “invites” slave nodes to transmit in turn
- typically used with “dumb” slave devices
- concerns:
	- polling overhead 
	- latency 
	- single point of failure (master)

![[Pasted image 20230330205538.png]]

* The polling protocol requires one of the nodes to be designated as a Master node (Primary station). 
* The master node polls each of the nodes in a [[Round Robin]] fashion. 
* In particular, the master node first sends a message to node 1, saying that it (node 1) can transmit up to some maximum number of frames. 
* After node 1 transmits some frames, the master node tells node 2 it (node 2) can transmit up to the maximum number of frames. 
* The master node can determine when a node has finished sending its frames by observing the lack of a signal on the channel.
- The procedure continues in this manner, with the master node polling each of the nodes in a cyclic manner.
- The polling protocol eliminates the collision.
- This allows polling to achieve a much higher efficiency. 
- The first drawback is that the protocol introduces a polling delay—the amount of time required to notify a node that it can transmit. 
- The second drawback, which is potentially more serious, is that if the master node fails, the entire channel becomes inoperative. 

## Token Passing
- Control token passed from one node to next sequentially. 
	- token message 
	- concerns: 
		- token overhead 
		- latency 
		- single point of failure (token)


* A station is authorized to send data when it receives a special frame called a token. 
* Here there is no master node. 
* A small, special-purpose frame known as a token is exchanged among the nodes in some fixed order. 
* When a node receives a token, it holds onto the token only if it has some frames to transmit; otherwise, it immediately forwards the token to the next node. 
* If a node does have frames to transmit when it receives the token, it sends up to a maximum number of frames and then forwards the token to the next node. 
* Token passing is decentralized and highly efficient. But it has problems as well. 

![[Pasted image 20230330211639.png]]

# Cable Access Network
![[Pasted image 20230330211749.png]]
- multiple 40Mbps downstream (broadcast) channels 
	- single CMTS transmits into channels 
- multiple 30 Mbps upstream channels 
	- multiple access: all users contend for certain upstream channel time slots (others assigned)

![[Pasted image 20230330212013.png]]

[[DOCSIS]]: data over cable service interface spec 
- [[Frequency Division Multiplexing (FDM)]] over upstream, downstream frequency channels 
- [[Time Division Multiplexing (TDM)]] upstream: some slots assigned, some have contention 
	- downstream MAP frame: assigns upstream slots
	- request for upstream slots (and data) transmitted random access (binary backoff) in selected slots
