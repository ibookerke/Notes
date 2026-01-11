
It is a method of dividing of big database tables into multiple smaller tables. 
We might need to apply this technique, when the table is too big to maintain like messenger's table of messages.

Partitioning - when we divide the table into multiple tables but they stay on one database instance.
Sharding - same as partitioning, but data is spread across multiple db instances.

## Vertical Partitioning 
We take a big table, break it by subsets of columns and store in different tables with same identifiers. The approach is very uncommon, and is being rarely used in real life.
Example:
We had a table with columns (id, name, status, description, photo) and we divide it into 2 tables:
- id, name, status
- id, description, photo


# Horizontal Partitioning

Here are some popular strategies:
- [[Range-Based Sharding]]
- [[Key-Based Sharding]]
- [[Directory-Based Sharding]]


### Challenges
There is no problem on inserting data to separate shards, however it could be complicated to select or aggregate data from separate shards. Try to avoid as much as you could to shard the table, on which regularly complex select queries are being applied. If you could live without sharding by purchasing a more expensive device - do it.

You always should do [[Replication]] of you shards, especially if you are using sharking, each shard should be replicated.


# Routing
Suppose we've sharded our database, and the client tries to fetch data for a certain record or perform a select query. There is a need to provide a way for a client to access any part of desired data in an according shard.

Here are some Routing solutions:
### Client-driven approach
So, the client, that tries to access some data knows on which shard the data is situated and addresses certain shard(s) by itself.
Pros:
- no redundant/excessive nodes
Cons:
- Additional logic in client code
- Need in notifying the client, when shard is down, or new shard is added

### Proxy approach
So, there should be a proxy node, that redirects the traffic to a desired shard
Pros:
- simple and fast solution
- application doesn't know about sharding
Cons:
- Additional network node
- functional loss (no joins or complex group by statements) !!!
- single point of failure 

### Coordinator approach
Just like proxy, but has a logic that allows performing complex aggregations like joins and group by's, or ordering by not indexed fields.

Pros:
- might cache requests
- application doesn't no about sharding
Cons:
- Additional network node
- infrastructural complexity(hard to develop and maintain)
- Single point of failure (might need [[Hot Standby]])
- High load may lead to degradation

There are some community approved solutions for this problem. 
For MySQL or PostgreSQL a popular solution is https://proxysql.com/


# [[Rebalancing]]
Sometimes, there is a need to move some data from one shard to another(one of the server is old and needs to be changed, or there is a need to move data to another host). 

Here are some strategies that are used to perform rebalancing:

### Read-only approach
This approach might be used only if it is allowed to make write operations to database unavailable for a certain time. 
So, the shard that is being copied rejects all write operations, allowing only read operations, while the other shard is copying data from it. It can only be applied it the service may tolerate db downtime for writing.

### Immutable data
In case the data that is being written are just logs or only new records and there is no update or delete statements, we might just write to the active node, while the new node will be copying the data from it.

### Logical Replication
We are just performing shard [[Replication]], when the sync is over, we are turning the old node off and update connections to a new node with replicated data.



# [[Resharding]]
Suppose a situation when the there is a need to add more nodes or remove some nodes, due to the higher or lower loads and database capacity changes.
Or it might be a situation when you understand, that the sharding strategy was not optimal and the data is spread unevenly across the shards.

Here comes the [[resharding]] to solve our architectural mistakes.
