- The bounded buffer problem (Producer Consumer Problem) is one of the classic problem of Process Synchronization.
- There is a buffer of n slots and each slot is capable of storing one unit of data.
- There are two processes running, namely, Producer and Consumer which are operating on the buffer.

![[Pasted image 20230301140408.png]]

- The producer tries to insert data into an empty slot of the buffer.
- The consumer tries to remove data from a filled slot of the buffer.
- The producer must not insert data when the buffer is full.
- The consumer must not remove data when the buffer is empty.
- The producer and consumer must not insert/remove data simultaneously.
