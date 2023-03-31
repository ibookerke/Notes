- sender can have up to N unacked packets in pipeline 
- receiver only sends cumulative ack 
	- doesn’t ack packet if there’s a gap 
- sender has timer for oldest unacked packet 
	- when timer expires, retransmit all unacked packets

![[Pasted image 20230326204557.png]]

## Sender:
![[Pasted image 20230326204623.png]]
## Receiver
![[Pasted image 20230326204641.png]]
