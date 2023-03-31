# Transport Layer Services

- The goal is to provide logical communication between app processes running on different hosts
- Transport protocols run in end systems:
	- **send side** 
		- breaks app messages into segments
		- pass to network layer
	- **rcs side**
		- reasembles segments into messages
		- passes assembled messages to app layer
		
![[Pasted image 20230215164035.png]]


TCP and UDP are Transport layer protocol
TCP:
- reliable 
- in order 
- [[Congestion control]]
- [[Flow control]]
- connecton setup
UDP:
- unreliable
- unordered delievery
- [[No-frilles]] extension of [[Best-effort]] IP

# Multiplexing and Demultiplexing
![[Pasted image 20230215165935.png]]
![[Pasted image 20230215170432.png]]

## Connectionless Demultiplexing
#### Recall
- created socket has host-local port
- when creating datagram to send into UDP socket must specify
	- destination IP address
	- destination port
#### Realisation
- When host recieves UDP segments:
	- check destination port# in segment
	- directs UDP segment to socket with that port#
- IP datagrams with same dest. port#, but different source IP address and/or source port numbers will be directed to same socket at dest

## Connection-oriented demux
- Tcp socket identified by 4-tuple
	- source IP address
	- source port number
	- dest IP address
	- dest port number
- demux: receiver uses all four values to direct segment to appropriate socket
- server host may support many simultaneous TCP sockets:
	- each socket identified by its own 4-tuple
- web servers have different sockets for each connecting client
	- non-persistent HTTP will have different socket for each request

![[Pasted image 20230215175245.png]]
Example for threaded server
![[Pasted image 20230215175414.png]]


# Connectionless Transport UDP
- [[No-frilles]], “bare bones” Internet transport protocol
- [[Best-effort]] service, UDP segments may be:
	- lost
	- delivered out-of-order to app


#### UDP use:
- streaming multimedia apps (loss tolerant, rate sensitive)
- DNS
- [[SNMP]]

#### Reliable transfer over UDP
- add reliability at application layer 
- application-specific error recovery!