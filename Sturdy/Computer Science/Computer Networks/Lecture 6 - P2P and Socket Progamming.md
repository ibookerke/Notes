# P2P 

## P2P Architecture
- no always on server
- arbitrary end systems directly communicate
- peers are intermittently connected and change IP addresses

### File distribution time in client-server architecture
![[Pasted image 20230214150424.png]]

### File distribution time in P2P architecture
![[Pasted image 20230214150540.png]]

Client-server vs P2P
![[Pasted image 20230214150821.png]]

## P2P file distribution 

### BitTorrent 
- File is being divided into 256Kb chunks
- peers in torrent send/receive file chunks

![[Pasted image 20230214151041.png]]

#### Requesting chunks
- at any time different peers have different subsets of chunks
- periodically client asks each peer for list of chunks they have
- Client requests missing chunks from peers(rarest first)

#### Sending chunks(tit-for-tat)
- Client sends chunks to those 4 peers currently sending her chunks at highest rate
	- re-evaluate top 4 every 10 seconds
- every 30 seconds randonly selecting another peer, starts sending chunks 


# Socket Programming

[[Socket]] - door between application process and end-end-transport protocol

2 socket types for two transport services
- UDP: unrelibale datagram
- TCP: reliable, byte stram-oriented

## Example:
1) client reads a line of characters (data) from its keyboard and sends data to server
2) server receives the data and converts characters to uppercase
3) server sends modified data to client
4) client receives modified data and displays line on its screen

### UDP implementation
- no “connection” between client & server
- no handshaking before sending data
- sender explicitly attaches IP destination address and port # to each packet
- receiver extracts sender IP address and port# from received packet
- transmitted data may be lost or received out-of-order
- provides unreliable transfer of groups of bytes (“datagrams”) between client and server
![[Pasted image 20230214153520.png]]

### TCP Implementation
- Client must contact server
	- server process must first be running
	- server must have created [[Socket]] that listens to client's requests 
- Client contacts servery by
	- Creating TCP socket, specifying IP address, port number of server process
	- when client creates socket: client TCP establishes connection to server TCP
	- when contacted by client, server TCP creates new socket for server process to communicate with that particular client
		- allows server to talk with multiple clients
		- source port numbers used to distinguish clients
- application viewpoint
	- TCP provides reliable, in-order byte-stream transfer (“pipe”) between client and server

![[Pasted image 20230214154953.png]]

