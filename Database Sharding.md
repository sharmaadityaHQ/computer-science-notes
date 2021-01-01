## MongoDB Introduction

- A record in MongoDB is a document (data structure composed of key-value pairs). MongoDB documents are similar to JSON objects.

- Values of fields can include other documents, arrays or arrays of documents.

- MongoDB stores documents in collections. Collections are analogous to tables in relational databases.

## Advantages of using documents

- Documents (objects) correspond to native data types in many languages.

- Embedded documents and arrays reduce need for expensive joins.

## Key Features

- MongoDB provides high performance. Embedded data models reduce I/O activity on database system. Indexes support faster queries.

- Indexes are special data structures that store a small portion of the collection’s data set in an easy to traverse form. The index stores the value of a specific field or set of fields, ordered by the value of the field.

- Without indexes MongoDB must perform a collection scan, i.e. scan every document in a collection to select those documents that match the query statement. If an appropriate index exists for a query, MongoDB can use the index to limit the number of documents it must inspect.

- MongoDB has high availability. The replication facility called replica set is a group of MongoDB servers that maintain the same data set providing redundancy and increasing data availability.

- MongoDB provides horizontal scalability as a core functionality via sharding.

## Sharding

- Sharding is a method for distributing data across multiple machines. Database systems with large data sets or high throughput applications can challenge the capacity of a single server.

- Sharding is horizontal partitioning of data according to a shard key. MongoDB uses the shard key to distribute the collection’s documents across shards. The shard key consists of a field or multiple fields in the documents. This shard key determines which database the entry to be persisted is sent to.

- Sharding a database is a common scalability strategy. It makes databases more performant and reliable.

## Problems in Sharding

- Joins across shards. Queries will go to different shards, pull the data and join it across the network which is an expensive process.

- Fixed number of shards. To overcome this problem we take a shard which has too much data and then dynamically break it into smaller pieces. This is called hierarchical sharding.

## Sharding best practices

- Create index on a shard. This index can be on a different attribute than the shard key.

- Master-slave architecture in case a shard fails. Multiple slaves copy the master. Write requests go to the master and slaves continuously read from the master. Read requests can now be distributed among slaves and write requests always go to the master. In case the master fails the slaves choose 1 master amongst themselves resulting in good single point of failure tolerance.