# Addressing and ARP

## [[MAC address]] 
Each adapter on [[LAN]] has unique LAN address

![[Pasted image 20230330225116.png]]

[[MAC address]] allocation administered by IEEE
- manufacturer buys portion of MAC address space (to assure uniqueness)
- analogy:
	- MAC address: like Social Security Number
	- IP address: like postal address
- MAC flat address ➜ portability
	- can move LAN card from one LAN to another
- IP hierarchical address not portable
	- address depends on IP subnet to which node is attached

## [[ARP]] 
![[Pasted image 20230330231024.png]]

# [[Ethernet]]

## Physical Topology
- bus: popular through mid 90s 
	- all nodes in same collision domain (can collide with each other) 
- star: prevails today
	- active switch in center 
	- each “spoke” runs a (separate) Ethernet protocol (nodes do not collide with each other)
 
![[Pasted image 20230330232521.png]]

<hr>

## Frame Structure
Sending adapter encapsulates IP datagram (or other network layer protocol packet) in ==Ethernet frame==
![[Pasted image 20230330232644.png]]
### preamble:
- 7 bytes with pattern 10101010 followed by one byte with pattern 10101011
- used to synchronize receiver, sender clock rates

### Dest. address & source address
6 byte source, destination [[MAC address]]es
- if adapter receives frame with matching destination address, or with broadcast address (e.g. ARP packet), it passes data in frame to network layer protocol 
- otherwise, adapter discards frame

### Type
indicates higher layer protocol (mostly IP but others possible, e.g., Novell IPX, AppleTalk)

### [[CRC]]
- cyclic redundancy check at receiver
- error detected: frame is dropped

<hr>

## Ethernet Unreliable & Connectionless
- ==connectionless== - no handshaking between sending and receiving [[NIC]]s
- ==unreliable== - receiving [[NIC]] doesn't send acks or nacks to sending [[NIC]]
	- data in dropped frames recovered only if initial sender uses higher layer rdt (e.g., TCP), otherwise dropped data lost
- Ethernet’s MAC protocol: unslotted [[CSMA-CD]] (check [[Lecture 18 - Link Layer MAC]]) with binary backoff

## 802.3 Ethernet standards: link & physical layers
many different Ethernet standarts
- common MAC protocol and frame format
- different speeds: 2 Mbps, 10 Mbps, 100 Mbps, 1Gbps, 10 Gbps, 40 Gbps
- different physical layer media: fiber, cable

# Switches
## Ethernet switch
- link-layer device: takes an active role
	- store, forward Ethernet frames 
	- examine incoming frame’s MAC address, selectively forward frame to one-or-more outgoing links when frame is to be forwarded on segment, uses [[CSMA-CD]] to access segment
- transparent
	- hosts are unaware of presence of switches
- plug-and-play, self-learning
	- switches do not need to be configured

## Multiple Simultaneous Transmissions
- hosts have dedicated, direct connection to switch 
- switches buffer packets 
- Ethernet protocol used on each incoming link, but no collisions; full duplex • each link is its own collision domain 
- switching: A-to-A’ and B-to-B’ can transmit simultaneously, without collisions
![[Pasted image 20230331004651.png]]
Each switch has a switch table, each 6 entry:
- MAC address of host, interface to reach host, time stamp) 
- looks like a routing table!

## Self-learning
- switch learns which hosts can be reached through which interfaces 
	- when frame received, switch “learns” location of sender: incoming LAN segment
	- records sender/location pair in switch table
![[Pasted image 20230331005041.png]]

## Frame Filtering/Forwarding
when frame received at switch:
1) record incoming link, [[MAC address]] of sending host 
2) index switch table using MAC destination address
3) 
```Go
if entry found for destination {
	if destination on segment from which frame arrived {
		Drop frame     
	} else{
		forward frame on interface indicated by entry
	}      
} else flood /* forward on all interfaces except arriving interface */

```

## Interconnecting switches
self-learning switches can be connected together:
![[Pasted image 20230331010225.png]]

