## [Amazon Aurora](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/CHAP_AuroraOverview.html)
Amazon Aurora is a fully managed relational database engine that's compatible with MySQL and PostgreSQL.
With some workloads, Aurora can deliver up to five times the throughput of MySQL and up to three times
the throughput of PostgreSQL without requiring changes to most of your existing applications.
Aurora is part of the managed database service Amazon Relational Database Service.

### [Aurora Storage](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Overview.StorageReliability.html)
Aurora data is stored in the cluster volume, which is a single, virtual volume that uses solid state drives.
A cluster volume consists of copies of the data across three Availability Zones in a single AWS Region.
Because the data is automatically replicated across Availability Zones, your data is highly durable with less possibility of data loss.
This replication also ensures that your database is more available during a failover. It does so because the data copies already exist
in the other Availability Zones and continue to serve data requests to the DB instances in your DB cluster.
The amount of replication is independent of the number of DB instances in your cluster.
Aurora cluster volumes automatically grow as the amount of data in your database increases up to 256 TiB in 10 GB increments.

### [Aurora Replication](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Replication.html)
An Aurora DB cluster can contain up to 15 Aurora Replicas. The Aurora Replicas can be distributed across the Availability Zones
that a DB cluster spans within an AWS Region.
Aurora Replicas have two main purposes. You can issue queries to them to scale the read operations for your application.
You typically do so by connecting to the reader endpoint of the cluster. That way, Aurora can spread the load for read-only
connections across as many Aurora Replicas as you have in the cluster. Aurora Replicas also help to increase availability.
If the writer instance in a cluster becomes unavailable, Aurora automatically promotes one of the reader instances to take
its place as the new writer.

### [Aurora Endpoints](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/Aurora.Overview.Endpoints.html)
Using endpoints, you can map each connection to the appropriate instance or group of instances based on your use case.
The cluster or writer endpoint points to the primary database instance and lets you perform write operations. The reader
endpoint is a load balancing connection pool for all Aurora Replicas and allows you to perform queries across them.