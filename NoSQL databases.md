## Advantages

- Insertion and retrievals are easier in NoSQL database as all data is present in 1 JSON document. In SQL, joins across tables can be expensive.

- Schema is easily changeable in NoSQL database.

- Built for scale. Horizontal partitioning is in-built in NoSQL database.

- Built for metrics and analysis.

## Disadvantages

- Not built for too many updates (Delete + Insert). Consistency is a problem. ACID is not guranteed.

- Read times are comparitively slower in NoSQL.

- Relations are not implicit in NoSQL.

- Joins are hard in NoSQL. SQL databases to some extent are built for joins.

## Cassandra architecture

- Multi-level sharding (2 layer cluster) is useful in case load is increasing on 1 node.

- Read queries are optimized and writes are more guranteed if replicas of data are made. Cassandra offers load balancing and redundancy/replication.

- A Quorum is the minimum number of votes that a distributed transaction has to obtain in order to be allowed to perform an operation in a distributed system.

- Distributed Consensus. Consensus is the task of getting all processes in a group to agree on some specific value based on the votes of each processes. Eg. If Replication factor - 3, Quorum - 2 and an update is done on nodes 5,1 and 2. 5 crashes but 1 and 2 are not yet updated so they both agree that no value is found (Quorum - 2, means if 2 of the nodes (2/3) accept a particular value then it is considered the truth) and an error is returned to the user. If Quorum is made 3 (3 nodes have to agree on a particular value) then the above query will fail as node 5 has failed.

- Cassandra pushes key-value data pairs in memory to new sorted string tables. Cassandra provides compaction feature where different sorted string tables (immutable) are merged to remove duplicate keys and optimize for space.