Possible Architerctures:
- Client-server Architercture
- peer-to-peer(P2P)

## Client-server architecture
### Server 
- always on host
- permanent IP address

### Clients
- may be intermittently connected
- may have dynamic IP addresses



## Addressing processes
### Sockets
- Process sends/receives messages to/from its [[Socket]]

Processes in order to exchange messages must have and identifier
**Identidier/endpoint** consist of IP address and port number


### Transport services
- data integrity - 100% reliable data transfer
- timing - require low delay to be “effective”
- throughput - require minimum amount of throughput to be “effective”
- security - encryption ...

### App features
- reliable transport - 100% reliable data transfer
- flow contol - sender won't overhelm/shock receiver
- congestion control - throttle sender when network overloaded
- connection-oriented - setup required between client and server processes

### TCP vs UDP
TCP:
- reliable
- flow control
- congestion control
- connection-oriented
- no timing, throughtput guarantee, security

UDP:
- unreliable data transfer
- no reliability/flow control/congestion control/throughput guarantee/security/connestion setup

## HTTP 
- web page consists of objects
- object can be HTML file, JPEG image, Java applet, audio file,… 
- web page consists of base HTML-file which includes several referenced objects 
- each object is addressable by a URL, e.g

- uses tcp
- stateless - server maintains no information about past client requests

### Persistence

#### non-persistent HTTP
- At most one object sent over TCP connection • connection then closed 
- Downloading multiple objects required multiple connections
- Respone time = 2 [[RTT]] + file transmission time
<hr>
- OS overhead for each TCP connection
- Browsers often open parallel TCP connection to fetch referenced objects


#### persistent HTTP
- multiple objects can be send over single TCP connection 
- server leaves connection open after sending response
- subsequent HTTP messages between same client/server sent over open connection
- client sends requests as soon as it encounters a referenced object
- as little as one [[RTT]] for all the referenced objects

### HTTP Request message
- sp - separator = '/'
- cr - carriage return = '/r'
- lf - line feed = '/n'
![[Pasted image 20230214054215.png]]

### Method types
#### HTTP 1/0
- GET
- POST
- HEAD - same as GET request but without response body(actually just to get headers)

#### HTTP 1/1
- GET, POST, HEAD, DELETE
- PUT - create/update actions

