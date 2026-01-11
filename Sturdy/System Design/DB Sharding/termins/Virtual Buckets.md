The concept is very similar to virtual nodes explained in [[Consistent Hashing]]. For this solution, we are just setting a certain amount of virtual buckets and assign each one to a certain shard. In case we want to move some data from one shard to another - we are just copying the VBucket's data and to another shard and reassign it. 

![[Screenshot 2024-12-02 at 22.14.30.png]]

Such approach doesn't imply changing the amount of VBuckets, so the the amount of Vbuckets should be significant from the beginning(usually its something like 1024/2048 vBucks)

