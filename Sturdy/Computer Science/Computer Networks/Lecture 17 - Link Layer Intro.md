# Terminology
- [[Link Layer Nodes]]
- [[Link Layer Links]]
- frame - layer-2 packet, encapsulates datagram

# Definition
Data-link layer has responsibility of transferring datagram from one node to physically adjacent node over a link

- datagram transferred by different link protocols over different links: 
	- e.g., WiFi on first link, Ethernet on next link 
- each link protocol provides different services 
	- e.g., may or may not provide reliable data transfer over link


## Transportation analogy: 
- trip from Princeton to Lausanne 
	- limo: Princeton to JFK 
	- plane: JFK to Geneva 
	- train: Geneva to Lausanne 
- tourist = ==datagram== 
- transportation segment = [[Link Layer Links]] 
- transportation mode = link layer protocol 
- travel agent = routing algorithm

# Link Layer Services
==Framing==: Encapsulate datagram into frame, adding header, trailer 

==Link access==: Channel access if shared medium 

==Reliable delivery between adjacent nodes==
	- We learned how to do this already (chapter 3)! 
	- Seldom used on low bit-error link (fiber, some twisted pair) 
	- Wireless links: high error rates

==Error detection and correction==: 
- Errors caused by signal attenuation, noise. 
- Receiver detects presence of errors: 
	- signals sender for retransmission or drops frame 
- Receiver identifies and corrects bit error(s) without resorting to retransmission

## Implementation
- Link layer implemented in “adapter” (aka network interface card [[NIC]]) or on a chip
- Attached into host’s system buses (looks like other IO devices.
- Combination of hardware, software, firmware
![[Pasted image 20230330151027.png]]
![[Pasted image 20230330151120.png]]

# Error Detection
==EDC== = Error Detection and Correction bits (redundancy)
==D== = Data protected by error checking, may include header fields

- Error detection not 100% reliable! 
	- protocol may miss some errors, but rarely 
	- larger EDC field yields better detection and correction
![[Pasted image 20230330151829.png]]

## Parity Checking
### Single Bit Parity
![[Pasted image 20230330152247.png]]

### Internet [[Checksum]]
### [[CRC]]

# Multiple access links, protocols

## Links
Two types of [[Link Layer Links]]
==Point-to-point== 
- PPP for dial-up access
- point-to-point link between Ethernet switch, host

==Broadcast== (shared wire or medium)
- old-fashioned Ethernet 
- upstream HFC 
- 802.11 wireless LAN
![[Pasted image 20230330164333.png]]

### Single shared broadcast channel 
- two or more simultaneous transmissions by nodes: [[Interference]] 
- collision if node receives two or more signals at the same time

## Multiple Access Protocol(MAC)
- distributed algorithm that determines how nodes share channel, i.e., determine when node can transmit
- communication about channel sharing must use channel itself!
	- no out-of-band channel for coordination

### An ideal multiple access protocol
- Given: broadcast channel of rate R bps
- desiderata
	1) when one node wants to transmit, it can send at rate R. 
	2) when M nodes want to transmit, each can send at average rate R/M 
	3) fully decentralized: 
		- no special node to coordinate transmissions 
		- no synchronization of clocks, slots
	4) simple

### Taxonomy
three broad classes:
- ==channel partitioning==
	- divide channel into smaller “pieces” (time slots, frequency, code) 
	- allocate piece to node for exclusive use
- ==random access==
	- channel not divided, allow collisions 
	- “ recover ” from collisions
- ==taking turns==
	- nodes take turns, but nodes with more to send can take longer turns

## Channel partitioning MAC protocols
- [[FDMA]]
- [[TDMA]]

