Suppose we decided to use [[Key-Based Sharding]] approach and distributed the data across the multiple nodes by the certain hash value. However, in order to maintain an ability to add or remove shards we might consider a certain cycle:

![[Screenshot 2024-11-30 at 21.52.22.png]]

In this example, all the data with certain hash value are going to be stored on the closest shard on a clock. In case, if we need to add new shards, we might just add shards to a clock, and if we want to remove the shard, we might move the data to the next closest shard(in our example, when removing shard #2, data moved to the shard #3).

However, this approach is not optimal, since it causes and uneven data distribution. Suppose a situation, when the shard-2  went down due to the high load, then it moves all the data to shard-3, it also goes down due to the load, and it will eventually disable the whole system shard by shard.

This problem may be approached by introducing the virtual nodes (just like in [[Lecture 20 - VLANs, Virtualization ...]]).

![[Screenshot 2024-11-30 at 21.58.41.png]]
So, in the provided example there are some shards that are being pointed to certain virtual nodes. By introducing the Vnodes we may make processes like [[Resharding]] or [[Rebalancing]] easier