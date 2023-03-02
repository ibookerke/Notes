
Packet Switches - forward packets (chunks of data) obtained by [[Packet Switching]].

Transmission rate - [[Bandwidth]]

[[ISP]] - Internet Service Provider
[[RFC]] - Request for Comments
[[IETF]] - Internet Engineering Task Force


## Protocols

Protocols define the format, order of messages sent and received among network entities, and actions taken on message transmission, receipt 

## Network edges

Network edge:
- hosts: clients and servers
- servers often in data centers

## Access Networks
Access networks, physical media:
- wired, wireless communication links
	- cable-based access uses [[Multiplexing]] 
	- [[Frequency Division Multiplexing (FDM)]] : different channels transmitted in different frequency bands

Network core:
- interconnected routers
- network of networks

![[Pasted image 20230203054618.png]]

HFC - hubrid fiber coax
- Up to 40 Mbps – 1.2 Gbps downstream transmission rate, 30-100 Mbps upstream transmission rate
- Network of cable, fiber attaches homes to ISP router
	- homes share access network to cable headend

[[DSL]] - digital subcriber line. DSLAM distributes voice and data to according networks
![[Pasted image 20230203055135.png]]

### Wireless access networks

Wireless local area networks (WLANs)
- typically within or around building (~100 ft)
- 802.11b/g/n (WiFi): 11, 54, 450 Mbps transmission rate
Wide-area cellular access networks
- provided by mobile, cellular network operator (10’s km)
- 10’s Mbps
- 4G cellular networks (5G coming)

### Enterprise Networs
Ethernet: wired access at 100Mbps, 1Gbps, 10Gbps
WiFi: wireless access points at 11, 54, 450 Mbps

## Sending Packets
Host - sends packets 

Host sending function:
- takes application message
- breaks into smaller chunks, known as packets, of length <span style="color:red;">L</span> bits
- transmits packet into access network at transmission rate <span style="color:red;">R</span>
- **link transmission rate**, aka **link capacity**, aka link [[Bandwidth]]

Given the length of packets and transmittion rate the [[Packet Transmission Delay]] could be evaluated

## Links

### Physical Media
- **bit** : 
	- propagates between  
	- transmitter/receiver pairs 
- **physical link**
	- what lies between transmitter & receiver
- guided media
	- signals propagate in solid media: copper, fiber, coax
- unguided media:
	- signals propagate freely, e.g., radio
- [[Twisted Pair]] (TP)


**Wireless radio**
- signal carried in various “bands” in electromagnetic spectrum
- no physical “wire”
- broadcast, “half-duplex” (sender to receiver)
- propagation environment effects:
- reflection
- obstruction by objects
- Interference/noise

**Radio link types:**
- Wireless LAN (WiFi)
	- 10-100’s Mbps; 10’s of meters
- wide-area (e.g., 4G cellular)
	- 10’s Mbps over ~10 Km
- Bluetooth: cable replacement
	- short distances, limited rates
- terrestrial  microwave
	- point-to-point; 45 Mbps channels
- satellite
	- up to 45 Mbps per channel
- 270 msec end-end delay

