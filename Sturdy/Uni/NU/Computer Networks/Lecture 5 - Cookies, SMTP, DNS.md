# Cookies
1) cookie header line of HTTP response message 
2) cookie header line in next HTTP request message 
3) cookie file kept on user ’s host, managed by user’ s browser 
4) back-end database at Web site

![[Pasted image 20230214055406.png]]

May be used for storing
- authorization 
- shopping carts 
- recommendations 
- user session state (Web e-mail)

# Electronic Mail
3 components
- User agents
	- composing, editing, reading mail messages
- Mail agents
	- mailbox - contains incoming messages for user
	- message queue - queue of outgoing (to be sent) mail messages
- [[SMTP]] 
	- uses TCP
	- uses port 25

# [[DNS]]
- hostname to ip
- host aliasing(canonical, alias names)
- mail server aliasing
- load distribution(replicated Web servers: many IP addresses correspond to one name)

![[Pasted image 20230214063645.png]]

## DNS server types:

### Root name servers
- contacted by local name server that cannot resolve name
- get mapping
- return mapping to local name server
- 13 logical root name servers worldwide

### [[TLD]]
- responsible for com, org, net, edu, aero, jobs, museums, and all top-level country domains, e.g.: uk, fr, ca, jp

### Authoritative DNS servers
- organization’s own DNS server(s), providing authoritative hostname to IP mappings for organization’s named hosts
- can be maintained by organization or service provider

### Local DNS name servers
- does not strictly belong to hierarchy
- each [[ISP]] (residential ISP, company, university) has one
- when host makes DNS query, query is sent to its local DNS server
	- has local cache of recent name-to-address translation pairs (but may be out of date!)
	- acts as proxy, forwards query into hierarchy

## DNS name resolution types
### Iterated query 
- contacted server replies with name of server to contact 
- "If I don't know maybe he knows"
![[Pasted image 20230214071007.png]]

### Recursive query
- puts burden of name resolution on contacted name server
![[Pasted image 20230214071019.png]]

## DNS Caching
Once (any) name server learns mapping, it caches mapping
- cache entries timeout (disappear) after some time([[TTL]])
- [[TLD]] servers typically cached in local name servers(thus root name servers not often visited)
Cached entries may be out-of-date
- if name host changes IP address, may not be known Internet-wide until all [[TTL]]s expire
- So the update/notify mechanisms proposed IETF standard

### DNS records storing
#### Format
storing Resource Records(RR)
RR format(name, value , type, ttl)
#### Types
- type=A 
	- name is hostname
	- value is IP address
- type=NS
	- name is domain (e.g., foo.com)
	- value is hostname of authoritative name server for this domain
- type=CNAME
	- name is alias name for some “canonical” (the real) name
	- www.ibm.com is really servereast.backup2.ibm.com
	- value is canonical name
- type=MX
	- value is name of mailserver associated with name

### DNS protocol messages
![[Pasted image 20230214072334.png]]
![[Pasted image 20230214073408.png]]