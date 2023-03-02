How can packet loss occur 
- packets queue in router buffers, waiting for turn for transmission
- queue length grows when arrival rate to link (temporarily) exceeds output link capacity
- packet loss occurs when memory to hold queued packets fills up

## Packet Delay
![[Pasted image 20230203141100.png]]

### 4 sources:
d_proc - nodal processing
- check bit errors
- determine output link
- typically < microsecs
d_queue - queueing delay
- time waiting at output link for transmission
- depends on congestion level of router
d_trans - transmission delay [[Packet Transmission Delay]]
- L: packet length (bits)
- R: link transmission rate (bps)
- d_trans = L/R
d_prop: propagation delay:
- d: length of physical link
- s: propagation speed (~2x108 m/sec)
- d_prop = d/s


## [[Queueing delay]]

Real internet delay
**Traceroute** program: provides delay measurement from source to router along end-end Internet path towards destination.  For all i:
- sends three packets that will reach router i on path towards destination (with time-to-live field value of i)
- router i will return packets to sender
- sender measures time interval between transmission and reply
![[Pasted image 20230203151255.png]]

## Packet loss
- queue (aka buffer) preceding link in buffer has finite capacity
- packet arriving to full queue dropped (aka lost)
- lost packet may be retransmitted by previous node, by source end system, or not at all


## Throughput (пропускная способность)
It is a rate (bits/time unit) at which bits are being sent from sender to receiver
- **instantaneous**: rate at given point in time
- **average**: rate over longer period of time

# Protocol Layers & Service models

Layered internet protocol stack
![[Pasted image 20230203153723.png]]

- Application
	-  exchanges ==messages== to implement some application service using services of transport layer
- Transport
	- Transport-layer protocol transfers M (e.g., reliably) from one process to another
	- transport-layer protocol encapsulates application-layer message, M, with transport layer-layer header Ht to create a transport-layer ==segment==
- Network
	- Network-layer protocol transfers transport-layer segment [Ht | M] from one host to another, with transport-layer header Hn
	- encapsulates transport layer to create ==datagram==
- Link
	- protocol transfers datagram [ Hn | [Ht | M] ] from host to neighboring host
	- encapsulates network datagram [ Hn | [Ht | M] ], with link-layer header Hl  to create a link-layer ==frame==


![[Pasted image 20230203154312.png]]