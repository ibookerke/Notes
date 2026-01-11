A way to organize data distribution by shards.
Basically, it is a lot like [[Consistent Hashing]], but the hash function accepts as a parameters not only identifier of the record, but also a number of shard. This action is repeated for all the shards and the shard with maximum resultant value of hash function will be chosen to store this information.

![[Screenshot 2024-12-02 at 22.10.45.png]]

So, basically, if we'll have 1000 shards, we will perform hashing 1000 times in order to decide where to store a record. However, the implementation for the randevous hashing might include some tree-based architectures, where there are lower number of hash functions are called 