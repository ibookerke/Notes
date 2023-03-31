
## TCP Overview
- point-to-point: 
	- one sender, one receiver 
- reliable, in-order byte stream:
	- no “message boundaries” 
- pipelined: 
	- TCP [[Congestion control]] and [[Flow control]] set window size
- full duplex data: 
	- bi-directional data flow in same connection 
	- MSS: maximum segment size 
- connection-oriented: 
	- handshaking (exchange of control msgs) inits sender, receiver state before data exchange 
- [[Flow control]]led: 
	- sender will not overwhelm receiver

![[Pasted image 20230326212502.png]]
![[Pasted image 20230326213729.png]]

## TCP round trip time, timeout
- How to set TCP timeout value?
	- It should be longer than RTT, but RTT varies
- how to estimate RTT?
	- SampleRTT: measured time from segment transmission until ACK receipt 
	- ignore retransmissions

![[Pasted image 20230326223157.png]]

- timeout interval: EstimatedRTT plus “safety margin” 
	- large variation in EstimatedRTT -> larger safety margin 
- ![[Pasted image 20230326223458.png]]

### TCP Reliable Data Transfer
TCP creates rdt service on top of IP’s unreliable service 
- pipelined segments 
- cumulative acks 
- single retransmission timer
retransmissions triggered by: 
- timeout events 
- duplicate acks

#### TCP sender events:
![[Pasted image 20230326225045.png]]
#### TCP sender
![[Pasted image 20230326225310.png]]

#### [[Fast Retransmit]]
Fast Retransmit is being used to provide a rdt

## TCP [[Flow control]] 
![[Pasted image 20230327131216.png]]
- Receiver “advertises” free buffer space by including rwnd value in TCP header of receiver-to-sender segments
	- RcvBuffer size set via socket options (typical default is 4096 bytes) 
	- many operating systems autoadjust RcvBuffer 
- sender limits amount of unacked (“in-flight”) data to receiver’s rwnd(Recieve window) value 
- guarantees receive buffer will not overflow

![[Pasted image 20230327131620.png]]

### Calculations
- Receiver computes rwnd = RcvBuffer - (LastByteRcvd - LastByteRead)
- Sender computes x = LastByteSent - LastByteAcked
- If x <= rwnd then sender can send

- One problem occurs when rwnd = 0 and receiver has no data to send to sender 
- To solve this problem, sender sends one data byte when rwnd = 0, if the sender receives corresponding ACK => rwnd != 0

## Connection Management
before exchanging data, sender/receiver “handshake” : 
- agree to establish connection (each knowing the other willing to establish connection) 
- agree on connection parameters
![[Pasted image 20230327134828.png]]

### TCP Closing connection
- Client, server each close their side of connection • send TCP segment with FIN bit = 1 
- respond to received FIN with ACK 
	- on receiving FIN, ACK can be combined with own FIN 
- simultaneous FIN exchanges can be handled

![[Pasted image 20230327142904.png]]
