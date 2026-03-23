## [Amazon Relational Database Service (RDS)](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)
Amazon Relational Database Service is managed a web service that makes it easier to set up, operate, and scale a relational database in the AWS Cloud.

### [RDS Database Engines](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html#Welcome.Concepts.DBInstance)
- PostgreSQL
- MariaDB
- Microsoft SQL Server
- MySQL
- Oracle Database
- IBM DB2

### [RDS Instance Storage](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Storage.html)
DB instances for Amazon RDS uses Amazon Elastic Block Store volumes for database and log storage.
RDS is able to automatically detect if you are running out of database storage and scales it automatically.

#### [RDS Instance Storage Types](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Storage.html#Concepts.Storage)
- **Provisioned IOPS SSD:** I/O-intensive workloads, low I/O latency and consistent I/O throughput
- **General Purpose SSD:** cost-effective storage for general workloads on medium-sized DB instances
- **Magnetic:** legacy magnetic storage

#### [RDS Instance Storage Scaling](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_PIOPS.ModifyingExisting.ScalingUp.html)
You can scale up the storage of an existing DB instance by increasing the allocated storage for the primary volume.
When you increase the allocated storage, you must increase it by at least 10 percent. Storage optimization can take several hours.
You can't make further storage modifications for either six hours or until storage optimization has completed on the instance, whichever is longer.


### [RDS Read Replica](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ReadRepl.html)
A read replica is a read-only copy of a DB instance. You can reduce the load on your primary DB instance by routing queries
from your applications to the read replica. In this way, you can elastically scale out beyond the capacity constraints of a
single DB instance for read-heavy database workloads. Read Replicas can be within the same AZ, in a different AZ or in different
region from the primary database instance. When you make updates to the primary DB instance, Amazon RDS copies them asynchronously
to the read replica. Read Replicas within the same region don't pay additional fees for networking traffic.

#### [RDS Read Replica Promotion](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ReadRepl.Promote.html)
You can promote a read replica into a standalone DB instance. If a source DB instance has several read replicas,
promoting one of the read replicas to a DB instance has no effect on the other replicas.


### [RDS Multi-AZ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.MultiAZ.html)
In a Multi-AZ DB instance deployment, Amazon RDS automatically provisions and maintains a synchronous standby replica in a different Availability Zone.
The primary DB instance is synchronously replicated across Availability Zones to a standby replica to provide data redundancy and
minimize latency spikes during system backups.

### [RDS Proxy](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/rds-proxy.html)
By using Amazon RDS Proxy, you can allow your applications to pool and share database connections to improve their ability to scale.
RDS Proxy makes applications more resilient to database failures by automatically connecting to a standby DB instance while preserving application connections.

### [RDS Security](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.html)

#### [RDS Data Encryption](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.Encryption.html)
Amazon RDS can encrypt your Amazon RDS DB instances. Data that is encrypted at rest includes the underlying storage for DB instances,
its logs, automated backups, read replicas, and snapshots.

#### [RDS Access Management](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.IAM.html)
Access Management for RDS resources is controlled using AWS IAM. Network Access is managed using Security Groups.
