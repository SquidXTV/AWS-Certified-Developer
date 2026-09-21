# [Amazon Elastic Block Store (EBS)](https://docs.aws.amazon.com/ebs/latest/userguide/what-is-ebs.html)

Amazon Elastic Block Store provides scalable, high-performance block storage resources that can be used with Amazon Elastic Compute Cloud instances.

## [EBS Volumes](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-volumes.html)

An Amazon EBS volume is a durable, block-level storage device that you can attach to your instances.
After you attach a volume to an instance, you can use it as you would use a physical hard drive.
EBS volumes are flexible. For current-generation volumes attached to current-generation instance types,
you can dynamically increase size, modify the provisioned IOPS capacity, and change volume type on live production volumes.

You can use EBS volumes as primary storage for data that requires frequent updates, such as the system drive for an instance or storage for a database application.
You can also use them for throughput-intensive applications that perform continuous disk scans. EBS volumes persist independently from the running life of an EC2 instance.

You can attach multiple EBS volumes to a single instance. The volume and instance must be in the same Availability Zone.
Depending on the volume and instance types, you can use Multi-Attach to mount a volume to multiple instances at the same time.

### [EBS Volume Types](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-volume-types.html)

#### [SSD Volumes](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-volume-types.html#vol-type-ssd)

SSD-backed volumes are optimized for transactional workloads involving frequent read/write operations with small I/O size,
where the dominant performance attribute is IOPS.

- gp3: 1GiB - 64TiB at max 80000 IOPS
- gp2: 1GiB - 16TiB at max 16000 IOPS
- io2: 4GiB - 64TiB at max 256000 IOPS
- io1: 4GiB - 16 TiB at max 64000 IOPS


#### [HDD Volumes](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-volume-types.html#vol-type-hdd)

HDD-backed volumes are optimized for large streaming workloads where the dominant performance attribute is throughput.

- st1: 125GiB - 16TiB at max 500 IOPS
- sc1: 125GiB - 16TiB at max 250 IOPS



### [EBS Volume Lifecycle](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-volume-lifecycle.html)

The lifecycle of an Amazon EBS volume starts with the creation process. You can create a volume from an Amazon EBS snapshot or you can create an empty volume.
Before you can use your volume, you must attach it to one or more Amazon EC2 instances that are in the same Availability Zone as the volume.
You can attach multiple volumes to an instance. If needed, you can detach a volume from one instance and then attach it to another instance.
If your storage requirements change, you can modify the size or performance of the volume at any time. You can create point-in-time backups
of your volumes by creating Amazon EBS snapshots. If you no longer need a volume, you can delete it to stop incurring the related storage costs.



## [EBS Snapshots](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-snapshots.html)

You can back up the data on your Amazon EBS volumes by making point-in-time copies, known as Amazon EBS snapshots.
A snapshot is an incremental backup, which means that we save only the blocks on the volume that have changed since the most recent snapshot.
This minimizes the time required to create the snapshot and saves on storage costs by not duplicating data.

Snapshots are stored in Amazon S3, in S3 buckets that you can't access directly.
Snapshot data is automatically replicated across all Availability Zones in the Region. This provides high availability and durability for snapshot data,
and enables you to restore volumes in any Availability Zones in that Region.


## [EBS Encryption](https://docs.aws.amazon.com/ebs/latest/userguide/ebs-encryption.html)

Use Amazon EBS encryption as a straight-forward encryption solution for your Amazon EBS resources associated with your Amazon EC2 instances.
With Amazon EBS encryption, you aren't required to build, maintain, and secure your own key management infrastructure.
Amazon EBS encryption uses AWS KMS keys when creating encrypted volumes and snapshots.

You encrypt EBS volumes by enabling encryption, either using encryption by default or by enabling encryption when you create a volume that you want to encrypt.
You can't directly encrypt existing unencrypted volumes or snapshots. To encrypt an unencrypted volume, create a snapshot of that volume,
and then use the snapshot to create a new encrypted volume. To encrypt an unencrypted snapshot, create an encrypted copy of that snapshot.
