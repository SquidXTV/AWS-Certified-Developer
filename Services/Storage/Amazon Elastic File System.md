# [Amazon Elastic File System (EFS)](https://docs.aws.amazon.com/efs/latest/ug/whatisefs.html)

Amazon Elastic File System (Amazon EFS) provides serverless, fully elastic file storage so that you can share file data
without provisioning or managing storage capacity and performance. Amazon EFS is built to scale on demand to petabytes
without disrupting applications, growing and shrinking automatically as you add and remove files.

## [EFS File System Types](https://docs.aws.amazon.com/efs/latest/ug/features.html#availability-durability)

- **Regional:** Regional file systems store data redundantly across multiple geographically separated Availability Zones within the same AWS Region.
- **One Zone:** One Zone file systems store data within a single Availability Zone.  In the unlikely case of the loss or damage to all or part of the Availability Zone, however, data that is stored in these types of file systems might be lost.


## [EFS Storage Class](https://docs.aws.amazon.com/efs/latest/ug/features.html#availability-durability)

- **EFS Standard:** The EFS Standard storage class uses solid state drive (SSD) storage to deliver the lowest levels of latency for frequently accessed files. New file system data is first written to the EFS Standard storage class and then can be tiered to the EFS Infrequent Access and EFS Archive storage classes by using lifecycle management.
- **EFS Infrequent Access (IA):**  A cost-optimized storage class for data that is accessed only a few times each quarter.
- **EFS Archive:** A cost-optimized storage class for data that is accessed a few times each year or less.


## [EFS Storage Lifecycle](https://docs.aws.amazon.com/efs/latest/ug/lifecycle-management-efs.html)

You can manage your file systems so that they have cost-effective storage throughout their lifecycle.
Use lifecycle management to automatically transition data between storage classes according to the lifecycle configuration for the file system.
The lifecycle configuration comprises of three lifecycle policies that you set for the file system.


## [EFS Replication](https://docs.aws.amazon.com/efs/latest/ug/features.html#availability-durability)

You can create a replica of your Amazon EFS file system in the AWS Region of your preference using replication.
Replication automatically and transparently replicates the data and metadata on your EFS file system to a new destination
EFS file system that is created in an AWS Region that you choose. EFS automatically keeps the source and destination file systems synchronized.
Replication is continual and designed to provide a recovery point objective (RPO) and a recovery time objective (RTO) of minutes.
