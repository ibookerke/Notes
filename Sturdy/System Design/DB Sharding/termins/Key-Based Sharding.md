Basically, where are preparing a certain hash function, then we are using it to hash the record identifier. The result is being divided by the number of shards and the resultant modulus is a shard number that will be used to store this record. 

![[Screenshot 2024-11-28 at 18.11.24.png]]


So, let's look at this approach more precisely, if we perform a simple strategy when we just hash the record identifier and use the modulus of diving result by number of shards, there will be problem with adding and removing shards:

![[Screenshot 2024-11-30 at 21.32.44.png]]

So, in order to implement a long-lasting architecture with proper consider implication of the [[Resharding]] popular strategies