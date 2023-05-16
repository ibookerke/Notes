
Network core - mesh of interconnected routers 

Using [[Packet Switching]] hosts break application-layer messages into packets

Network Core functions
![[Pasted image 20230203132928.png]]


## [[Packet Switching]]

- Evaluated by [[Packet Transmission Delay]]
- Store and forward - entire packet must  arrive at router before it can be transmitted on next link

![[Pasted image 20230203133721.png]]

### Queueing in Packet switching

When the packtes arrives to access networks faster than they could be handled they are stored as a queue in access network

Packet queuing and loss: - if arrival rate (in bps) to link exceeds transmission rate (bps) of link for some period of time:
- packets will queue, waiting to be transmitted on output link
- packets can be ![[Pasted image 20230203133721.png]]dropped (lost) if memory (buffer) in router fills up

## Cirquit switching
end-end resources allocated to, reserved for “call” between source and destination
- in diagram, each link has four circuits.
	- call gets 2nd circuit in top link and 1st circuit in right link.
- dedicated resources: no sharing
- circuit-like (guaranteed) performance
- circuit segment idle if not used by call (no sharing)
- commonly used in traditional telephone networks

![[Pasted image 20230203134427.png]]

Circuite switching may have 2 types of implementation
[[Frequency Division Multiplexing (FDM)]] and [[Time Division Multiplexing (TDM)]]

## [[Packet Switching]] vs Cirquit Switching

For instance for 1Gb/s link cirquit switching network will cover only 10 active users using 100 mb/s, while with packet switching the probability of 35 users simultaneusoly be active as same time is .0004

Packet Switching - on demand allocation
Cirquirt switching - reserved resources


## Internet structure: a "Network of Networks"

How to connect millions of [[ISP]]s together? 
1) Create multiple global competitive ISPs
2) Connect them with [[Internet exchange point(IXP)]]
3) Make regional ISPs that connect to global
4) and content provider networks  (e.g., Google, Microsoft,  Akamai) may run their own network, to bring services, content close to end users
![[Pasted image 20230203140119.png]]

![[Pasted image 20230203140148.png]]

