
# Intro
**rdt** - Reliable data transfer 
**udt** - Unreliable data transfer

Characteristics of unreliable channel will determine complexity of reliable data transfer protocol

![[Pasted image 20230226114547.png]]

In order to achieve reliability we'll:
 - incrementally develop sender, receiver sides of rdt protocol
 - consider only [[Unidirectional Data Tranfer]]
	 - but control info will flow on both directions
- use [[Finite State Machine(FSM)]] to specify sender, receiver
![[Pasted image 20230226115010.png]]

# Channel Reliability

## rdt1.0
rdt1.0 - reliable transfer over reliable channel
#### Underlying channel perfectly reliable if: 
- no [[Bit errors]] 
- no loss of packets
- Separate FSMs for sender, receiver: 
	- sender sends data into underlying channel 
	- receiver reads data from underlying channel 
![[Pasted image 20230226115328.png]]

#### Underlying channels may flip bits
So [[Checksum]] to detect [[Bit errors]]

## Recovering from Errors
There are some ways of notifying the sender that errors occured, using:
-  [[ACK]]s: receiver explicitly tells sender that pkt received OK 
-  [[NAK]]s: receiver explicitly tells sender that pkt had errors 
- sender retransmits pkt on receipt of [[NAK]] 


## rdt2.0
rdt2.0 - transfer over unreliable channel

rdt2.0(beyond rdt1.0) has:
- error detection
- feedback: control msgs ([[ACK]], [[NAK]]) from receiver to sender

#### Protocols based on such retransmissions are called [[ARQ]] protocols.

rdt2.0 [[Finite State Machine(FSM)]] specifications:
![[Pasted image 20230226120636.png]]

### If [[ACK]]/[[NAK]] corrutped:
#### Sender:
- sender doens't know what happened at receiver
- can't just restransmit possible duplicate
- sender adds sequence number to each pkt
- if sender doesn't get [[ACK]] or gets [[NAK]] start retransmitting packets
#### Receiver
- discards(doesn't deliver up) duplicate packets


#### ==stop and wait== 
Sender sends one packet, then waits for receiver response

## rdt2.1
#### Sender
- seq # added to pkt 
- two seq. #’s (0,1) will suffice(since after sending packet we are stopping and waiting). 
- must check if received ACK/NAK corrupted 
- twice as many states 
	- state must “remember” whether “expected” pkt should have seq # of 0 or 1
![[Pasted image 20230226160447.png]]

#### Receiver
- must check if received packet is duplicate 
	- state indicates whether 0 or 1 is expected pkt seq # 
- ==receiver can not know if its last ACK/NAK received OK at sender== 
![[Pasted image 20230226160502.png]]

## rdt2.2 [[NAK]]-free protocol

- same functionality as rdt2.1, using [[ACK]]s only 
- instead of [[NAK]], receiver sends [[ACK]] for last pkt received OK 
	- receiver must explicitly include seq # of pkt being ACKed
- duplicate ACK at sender results in same action as NAK: retransmit current pkt

![[Pasted image 20230226160756.png]]

## rdt3.0: channels with errrors and loss

### New assumption
Underlying channel can also lose packets (data, [[ACK]]s) 
- checksum, seq. #, ACKs, retransmissions will be of help … but not enough

### Approach
- sender waits “reasonable” amount of time for [[ACK]]
- retransmits if no ACK received in this time
- if pkt (or ACK) just delayed (not lost):
	- retransmission will be duplicate, but seq. #’s already handles this 
	- receiver must specify seq # of pkt being ACKed
- requires ==**countdown timer**==

![[Pasted image 20230226161715.png]]
![[Pasted image 20230226161726.png]]

### Calculating perfomance
![[Pasted image 20230226161838.png]]

## Pipelined protocols
pipelining: sender allows multiple, “in-flight” , yetto-be-acknowledged pkts 
- range of sequence numbers must be increased 
- buffering at sender and/or receive

3-packet pipelining increases utilization by a factor of 3!