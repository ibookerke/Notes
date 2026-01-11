Byzantine fault tolerance (BFT)—In the context of distributed systems, BFT is the ability of a distributed computer network to function as desired and correctly reach a sufficient consensus despite malicious components (nodes) of the system failing or propagating incorrect information to other peers.

## What is Byzantine Fault Tolerance?

Byzantine Fault Tolerance is a computer system's ability to continue operating even if some of its nodes fail or act maliciously.

The term comes from a hypothetical called the Byzantine Generals Problem. This logical dilemma, as you'd expect, is about a group of Byzantine generals. Each general has an army and a location surrounding a fortress, and they must decide as a group to attack or retreat.

If they all make the same decision, they're successful. But, if there's a miscommunication or treachery causing some generals to attack while the others retreat, then the battle is lost. These types of problems are known as Byzantine faults.

With any computer system that has multiple nodes, each node could be considered a general. The system's Byzantine Fault Tolerance refers to whether it can keep working even when some nodes go down or intentionally try to deceive it.

# Implementation
[Blockchain technology](https://www.fool.com/investing/stock-market/market-sectors/financials/blockchain-stocks/) is how cryptocurrencies validate, process, and record transactions. For a transaction to go through, a group of nodes must agree that it's valid. Each blockchain network has a consensus algorithm, which are the specific rules its nodes follow to reach an agreement on transactions.

So, here is the list of some algorithms addressing this problem:
- [[Proof of work(POW)]]
- [[Proof of stake]]
- 