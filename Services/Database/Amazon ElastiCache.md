## [Amazon ElastiCache](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/WhatIs.html)
Amazon ElastiCache is a web service that makes it easy to set up, manage, and scale a distributed
in-memory data store or cache environment in the cloud.

### [ElastiCache Engine](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.html)
- Redis
- Memcached
- Valkey

### [ElastiCache Deployment Options](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/WhatIs.deployment.html)
- **Serverless Caching:** automatically scale and store data redundantly across three AZs
- **Node-based Clusters:** choose configuration for underlying nodes in a cluster

### [ElastiCache Caching Strategies](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/Strategies.html)

#### [ElastiCache Lazy Loading](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/Strategies.html#Strategies.LazyLoading)
Amazon ElastiCache is an in-memory key-value store that sits between your application and the database that it accesses.
Whenever your application requests data, it first makes the request to the ElastiCache cache. If the data exists in the
cache and is current, ElastiCache returns the data to your application. If the data doesn't exist in the cache or has expired,
your application requests the data from your data store. Your data store then returns the data to your application.
Your application next writes the data received from the store to the cache. This way, it can be more quickly retrieved
the next time it's requested.

#### [ElastiCache Write-through](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/Strategies.html#Strategies.WriteThrough)
The write-through strategy adds data or updates data in the cache whenever data is written to the database.
Data in the cache is never stale. Because the data in the cache is updated every time it's written to the database,
the data in the cache is always current.

#### [ElastiCache Time-to-Live (TTL)](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/Strategies.html#Strategies.WithTTL)
Lazy loading allows for stale data but doesn't fail with empty nodes. Write-through ensures that data is always fresh,
but can fail with empty nodes and can populate the cache with superfluous data. By adding a time to live (TTL) value
to each write, you can have the advantages of each strategy. At the same time, you can and largely avoid cluttering
up the cache with extra data.

### [ElastiCache Encryption](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/encryption.html)
ElastiCache support in-transit and at-rest encryption of your data.
