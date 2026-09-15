# [Amazon ElastiCache](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/WhatIs.html)

Amazon ElastiCache is a web service that makes it easy to set up, manage, and scale a distributed
in-memory data store or cache environment in the cloud.

## [ElastiCache Engine](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.html)

- Redis
- Memcached
- Valkey


## [ElastiCache Deployment Options](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/WhatIs.deployment.html)

- **Serverless Caching:** automatically scale and store data redundantly across three AZs
- **Node-based Clusters:** choose configuration for underlying nodes in a cluster


## [ElastiCache Nodes](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/WhatIs.Components.html#WhatIs.Components.Nodes)

A node is a fixed-size chunk of secure, network-attached RAM. Each node runs an instance of the engine and version that was chosen when you created your cluster.
If necessary, you can scale the nodes in a cluster up or down to a different instance type.

Every node within a cluster is the same instance type and runs the same cache engine. Each cache node has its own Domain Name Service (DNS) name and port. 


## [ElastiCache Shards](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/WhatIs.Components.html#WhatIs.Components.Shards)

A Valkey or Redis OSS shard is a grouping of one to six related nodes. A Valkey or Redis OSS cluster with cluster mode enabled always has at least one shard.
Sharding is a method of database partitioning that separates large databases into smaller, faster, and more easily managed parts called data shards.

A multiple node shard implements replication by having one read/write primary node and 1–5 replica nodes.
Replica nodes use asynchronous replication mechanisms to keep synchronized with the primary node.
Applications can read from any node in the cluster but can write only to primary nodes
Nodes in a shard can be spread across multiple AZs.
 
 
## [ElastiCache Clusters](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/WhatIs.Components.html#WhatIs.Components.Clusters)

A cluster is a logical grouping of one or more nodes. Data is partitioned across the nodes in a Memcached cluster, and across the shards in a Valkey or
Redis OSS cluster that has cluster mode enabled. All nodes in a cluster must reside in the same region.


## [ElastiCache Endpoints](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/WhatIs.Components.html#WhatIs.Components.Endpoints)

An endpoint is the unique address your application uses to connect to an ElastiCache node or cluster.

### ElastiCache Single Node Endpoints

The endpoint for a single node Valkey or Redis OSS cluster is used to connect to the cluster for both reads and writes.


### ElastiCache Multi Node Endpoints

A multiple node Valkey or Redis OSS cluster with cluster mode disabled has two types of endpoints. The primary endpoint always
connects to the primary node in the cluster, even if the specific node in the primary role changes. Use the primary endpoint
for all writes to the cluster. Use the Reader Endpoint to evenly split incoming connections to the endpoint between all read replicas.



## [ElastiCache Caching Strategies](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/Strategies.html)

### [ElastiCache Lazy Loading](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/Strategies.html#Strategies.LazyLoading)

Amazon ElastiCache is an in-memory key-value store that sits between your application and the database that it accesses.
Whenever your application requests data, it first makes the request to the ElastiCache cache. If the data exists in the
cache and is current, ElastiCache returns the data to your application. If the data doesn't exist in the cache or has expired,
your application requests the data from your data store. Your data store then returns the data to your application.
Your application next writes the data received from the store to the cache. This way, it can be more quickly retrieved
the next time it's requested.


### [ElastiCache Write-through](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/Strategies.html#Strategies.WriteThrough)

The write-through strategy adds data or updates data in the cache whenever data is written to the database.
Data in the cache is never stale. Because the data in the cache is updated every time it's written to the database,
the data in the cache is always current.


### [ElastiCache Time-to-Live (TTL)](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/Strategies.html#Strategies.WithTTL)

Lazy loading allows for stale data but doesn't fail with empty nodes. Write-through ensures that data is always fresh,
but can fail with empty nodes and can populate the cache with superfluous data. By adding a time to live (TTL) value
to each write, you can have the advantages of each strategy. At the same time, you can and largely avoid cluttering
up the cache with extra data.



## [ElastiCache Encryption](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/encryption.html)

ElastiCache support in-transit and at-rest encryption of your data.
