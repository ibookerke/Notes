- sender can have up to N unack’ed packets in pipeline 
- rcvr sends individual ack for each packet 
- sender maintains timer for each unacked packet 
	- when timer expires, retransmit only that unacked packet
![[Pasted image 20230326204818.png]]

## Sender Algorithm
- data from above: 
	- if next available seq # in window, send pkt 
- timeout(n): 
	- resend pkt n, restart timer 
- ACK(n) in `sendbase,sendbase+N`: 
	- mark pkt n as received 
	- if n smallest unACKed pkt, advance window base to next unACKed seq#
## Receiver Algorithm
- pkt n in `rcvbase, rcvbase+N-1` 
	- send ACK(n) 
	- out-of-order: buffer 
	- in-order: deliver (also deliver buffered, in-order pkts), advance window to next notyet-received pkt 
- pkt n in `rcvbase-N,rcvbase-1` 
	- ACK(n) 
- otherwise: 
	- ignore



