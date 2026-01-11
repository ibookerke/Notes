Multi-Paxos optimizes the traditional [[Paxos]] protocol by introducing a streamlined approach to leader election and proposal management, significantly reducing the overhead associated with reaching consensus on multiple decisions. This efficiency is crucial for distributed systems where numerous decisions must be agreed upon swiftly and reliably.



1. **Leader Election**: The process begins by selecting a leader among the nodes. This leader will be responsible for managing the consensus process across multiple proposals, which eliminates the need to elect a new leader for each decision, thus saving time and reducing communication overhead.
2. **Phase 1 (Prepare)**: Once elected, the leader performs the preparatory phase only once for a series of proposals. In this phase, the leader sends a prepare request to acceptor nodes, who respond with promises not to accept any future proposals with a lower sequence number than the one included by the leader. This step ensures that the leader has authority over the subsequent sequence of proposals.
3. **Phase 2 (Propose/Accept)**: With the authority established, the leader proposes values for multiple “slots.” Each slot represents a separate consensus decision. Unlike basic Paxos, the leader does not need to repeat the preparatory phase for each proposal, allowing for a more fluid and continuous decision-making process. But it does have to send a slot number in the propose message for serialization.
4. **Learning Phase**: As each proposal is accepted by a quorum of acceptors, the agreed-upon value for each slot is relayed back to all nodes. This synchronization allows all participants to update their state according to the latest consensus, ensuring system-wide consistency. For simplicity the leader is also an acceptor and it can send the value back to the client.
5. **Looping steps 3 and 4**: The leader serializes the execution of each proposal in the slots for all incoming client requests, ensuring that all decisions are processed in an orderly and linear fashion even if the requests come in parallely as long as we align the right slot to it.


*Quorum - set of individuals participating in a decision


