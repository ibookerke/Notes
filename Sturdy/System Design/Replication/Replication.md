# Intro
Database replication - having multiple database instances available. 

The database replication may be used for securing service availability, by implementing [[Hot Standby]] or for the speeding up read operations.

Basically the replication means - creating another instances of databases. There are, multiple approaches of organization of how to implement it.
# Architectures:
- [[Master-master replication]]
- [[Peer-to-Peer Replication]]
- [[Read-Replica Architecture]]
- [[Cascade Replication]]
- [[Synchronous Replication]]
- [[Asynchronous Replication]]

# Choosing new master
There are multiple implementations, however, in order to avoid overhead with synchronization, it is a popular approach to have one master for write operations and multiple replicas, that replicate updates of the master. However, there is a problem, in case the master node is down, there is a need in choosing new master. 

Usually the new master is being chosen based on a following parameters:
- lowest latency
- highest priority(preconfigured)
- data-freshness

There might be some zooKeeper that will be choosing from replicas based on a aforementioned properties or it might even choose randomly.

However, there are some algorithms designed for choosing the most appropriate master. 

## Consensus Algorithms
- [[Raft]] - all nodes vote for a new master -> new master rules
- [[Paxos]] - all nodes vote on each proposal(request)
- [[Multi-Paxos]] - the leader is chosen and all nodes are voting on a sequence of proposals(requests)
- [[Byzantine Fault Tolerance(FBT)]] - Concept describing the cases when one of the nodes may propagate incorrect information to peers. Any distributes system needs to address this problem



