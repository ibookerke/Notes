# Perfomance of rdt3.0
![[Pasted image 20230326202536.png]]
![[Pasted image 20230326202613.png]]
# Pipelined protocols
pipelining: sender allows multiple, “in-flight” , yetto-be-acknowledged pkts 
- range of sequence numbers must be increased 
- buffering at sender and/or receiver
![[Pasted image 20230326204307.png]]

## Pipeline protocols
- [[Go-back-N]]
	- ![[Pasted image 20230326204733.png]]
- [[Selective Repeat]]
	- ![[Pasted image 20230326205208.png]]

