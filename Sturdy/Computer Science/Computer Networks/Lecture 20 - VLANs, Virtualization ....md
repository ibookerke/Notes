# Vlans
## Motivation
![[Pasted image 20230331011840.png]]

Switch(es) supporting [[VLAN]]s capabilities can be configured to define multiple virtual LANS over single physical LAN infrastructure.

![[Pasted image 20230331012017.png]]

## Port-based VLAN
- ==traffic isolation==:
	- frames to/from ports 1-8 can only reach ports 1-8 
	- can also define VLAN based on [[MAC address]]es of endpoints, rather than switch port
- ==dynamic membership==:
	- ports can be dynamically assigned among VLANs
- ==forwarding between VLANS==:
	- done via routing (just as with separate switches) 
	- in practice vendors sell combined switches plus routers

## Spanning Multiple Switches
==trunk port==: 
- carries frames between VLANS defined over multiple physical switches
	- frames forwarded within VLAN between switches can’t be vanilla 802.1 frames (must carry VLAN ID info) 
	- 802.1q protocol adds/removed additional header fields for frames forwarded between trunk ports
![[Pasted image 20230331012702.png]]

## 802.1Q VLAN frame format
![[Pasted image 20230331012757.png]]

# Multiprotocol label switching ([[MPLS]])
- Initial goal: high-speed IP forwarding using fixed length label (instead of IP address) 
	- fast lookup using fixed length identifier (rather than shortest prefix matching) 
	- borrowing ideas from Virtual Circuit (VC) approach 
	- but IP datagram still keeps IP address!

![[Pasted image 20230331013121.png]]

## MPLS capable routers
- a.k.a. label-switched router 
- forward packets to outgoing interface based only on label value (don’t inspect IP address)
	- MPLS forwarding table distinct from IP forwarding tables 
- flexibility: MPLS forwarding decisions can differ from those of IP 
	- use destination and source addresses to route flows to same destination differently (traffic engineering) 
	- re-route flows quickly if link fails: pre-computed backup paths (useful for VoIP)

![[Pasted image 20230331013916.png]]

## MPLS forwarding tables
![[Pasted image 20230331014639.png]]

# Data center Networking
