# [Amazon Elastic Compute Cloud (EC2)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)

Amazon Elastic Compute Cloud (Amazon EC2) is an Infrastructure as a Service (IaaS) offering that provides on‑demand,
scalable computing capacity in the AWS Cloud.

## EC2 Instance Configuration Option

- **Operating System:** Linux, Windows or MacOS
- **vCPU**
- **Memory**
- **Storage:** Network-attached EBS, EFS storage, Hardware EC2 Instance Storage
- **Networking:** Network Card, IP address
- **Security Group**
- **User Data**


## [EC2 Instance Store](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html)

An instance store provides ephemeral, temporary block-level storage for your EC2 instance. This storage is provided by disks that are
physically attached to the host computer. Instance store is ideal for temporary storage of information that changes frequently,
such as buffers, caches, scratch data, and other temporary content. An instance store consists of one or more instance store
volumes exposed as block devices. The size of an instance store as well as the number of devices available varies by instance type and instance size.


## [EC2 Instance Metadata](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html#instancedata-data-categories)

Instance metadata is data about your instance that you can use to configure or manage the running instance. 

- **Instance Metadata Properties:** properties of the EC2 instance such as instance id, hostname, mac, etc.
- **Dynamic Data:** metadata that is generated when the instance is launched
- **User Data:** script that runs on the first startup of the instance, used to install software, configuration, etc. 


## [EC2 Security Groups](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html)

A security group acts as a virtual firewall for your EC2 instances to control incoming and outgoing traffic.
Inbound rules control the incoming traffic to your instance, and outbound rules control the outgoing traffic from your instance.
You can associate each instance with multiple security groups, and you can associate each security group with multiple instances.
Security groups are stateful, if you send a request from your instance, the response traffic for that request is allowed to flow
in regardless of inbound security group rules. Also, responses to allowed inbound traffic are allowed to flow out, regardless of outbound rules.


## [EC2 Instance Profile](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html)

An EC2 instance profile is a special IAM role container that you attach to an EC2 instance so the instance can obtain temporary AWS credentials
via the instance metadata service, without hard-coding access keys. It allows applications running on the instance to automatically assume
the role and access permitted AWS resources securely.


## [EC2 Instance Types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html)

When you launch an instance, the instance type that you specify determines the hardware of the host computer used for your instance.
Each instance type offers different compute, memory, and storage capabilities, and is grouped in an instance family based on these capabilities.

Amazon EC2 dedicates some resources of the host computer, such as CPU, memory, and instance storage, to a particular instance.
Amazon EC2 shares other resources of the host computer, such as the network and the disk subsystem, among instances.
If each instance on a host computer tries to use as much of one of these shared resources as possible, each receives an equal share of that resource.
However, when a resource is underused, an instance can consume a higher share of that resource while it's available.

### [EC2 Instance Type Series](https://docs.aws.amazon.com/ec2/latest/instancetypes/instance-type-names.html)

- **C** - Compute optimized
- **I** - Storage optimized
- **M** - General purpose
- **R** - Memory optimized
- **T** - Burstable Performance



## [EC2 Purchasing Options](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-purchasing-options.html)

- **On-Demand:** Pay, by the second, for the instances that you launch
- **Savings Plan:** Reduce your Amazon EC2 costs by making a commitment to a consistent amount of usage, in USD per hour, for a term of 1 or 3 years
- **Reserved:** Reduce your Amazon EC2 costs by making a commitment to a consistent instance configuration, including instance type and Region, for a term of 1 or 3 years
- **Spot:** Request unused EC2 instances, which can reduce your Amazon EC2 costs significantly
- **Dedicated Hosts:** Pay for a physical host that is fully dedicated to running your instances, and bring your existing per-socket, per-core, or per-VM software licenses to reduce costs
- **Dedicated Instances:** Pay, by the hour, for instances that run on single-tenant hardware
- **Capacity Reservations:** Reserve capacity for your EC2 instances in a specific Availability Zone


## [EC2 Instance Connect](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-connect-methods.html)

Amazon EC2 Instance Connect provides a secure way to connect to your Linux instances over Secure Shell (SSH).
With EC2 Instance Connect, you use AWS Identity and Access Management (IAM) policies and principals to control SSH access to your instances,
removing the need to share and manage SSH keys.


## [Amazon Machine Image (AMI)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html)

An Amazon Machine Image (AMI) is an image that provides the software that is required to set up and boot an Amazon EC2 instance.
You can create an AMI from your Amazon EC2 instances and then use it to launch instances with the same configuration.


## [EC2 Auto Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html)

Amazon EC2 Auto Scaling helps you ensure that you have the correct number of Amazon EC2 instances available to handle the load for your application.
It automatically monitors the health and availability of your instances using EC2 health checks and replaces terminated or impaired instances to maintain your desired capacity. 

### [EC2 Auto Scaling Launch Templates](https://docs.aws.amazon.com/autoscaling/ec2/userguide/launch-templates.html)

A launch template is similar to a launch configuration, in that it specifies instance configuration information.
It includes the ID of the Amazon Machine Image (AMI), the instance type, a key pair, security groups, and other parameters used to launch EC2 instances.


### [EC2 Auto Scaling Groups](https://docs.aws.amazon.com/autoscaling/ec2/userguide/auto-scaling-groups.html)

An Auto Scaling group contains a collection of EC2 instances that are treated as a logical grouping for the purposes of automatic scaling and management.
An Auto Scaling group also lets you use Amazon EC2 Auto Scaling features such as health check replacements and scaling policies.
If an instance becomes unhealthy, the group terminates the unhealthy instance and launches another instance to replace it.

The size of an Auto Scaling group depends on the number of instances that you set as the desired capacity.
You can adjust its size to meet demand, either manually or by using automatic scaling. 

You can use scaling policies to increase or decrease the number of instances in your group dynamically to meet changing conditions.
When the scaling policy is in effect, the Auto Scaling group adjusts the desired capacity of the group,
between the minimum and maximum capacity values that you specify, and launches or terminates the instances as needed.


### [EC2 Auto Scaling Methods](https://docs.aws.amazon.com/autoscaling/ec2/userguide/scaling-overview.html)

- Maintain a fixed number of instances
- Scale manually by updating the desired capacity
- Scale based on a schedule
- Scale dynamically based on demand using CloudWatch metrics

#### [Manual Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/ec2-auto-scaling-scaling-manually.html)

You can manually adjust the number of EC2 instances in your Auto Scaling group at any time using `aws autoscaling set-desired`.
This process of changing the instance count manually is referred to as manual scaling. Manual scaling is an alternative to auto scaling,
especially if you want to make one-time capacity changes.


#### [Scheduled Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/ec2-auto-scaling-scheduled-scaling.html)

With scheduled scaling, you can set up automatic scaling for your application based on predictable load changes.
You create scheduled actions that increase or decrease your group's desired capacity at specific times.


#### [Dynamic Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scale-based-on-demand.html)

Dynamic scaling scales the capacity of your Auto Scaling group as traffic changes occur.

##### [Target Tracking Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scaling-target-tracking.html)

A target tracking scaling policy automatically scales the capacity of your Auto Scaling group based on a target metric value.
With target tracking, you select a metric and a target value to represent the ideal average utilization or throughput level for your application.
Amazon EC2 Auto Scaling creates and manages the CloudWatch alarms that invoke scaling events when the metric deviates from the target.


##### [Step Scaling and Simple Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-scaling-simple-step.html)

Step scaling and simple scaling policies scale the capacity of your Auto Scaling group in predefined increments based on CloudWatch alarms.
You can define separate scaling policies to handle scaling out and scaling in when an alarm threshold is breached.



#### [Predictive Scaling](https://docs.aws.amazon.com/autoscaling/ec2/userguide/ec2-auto-scaling-predictive-scaling.html)

Predictive scaling works by analyzing historical load data to detect daily or weekly patterns in traffic flows.
It uses this information to forecast future capacity needs so Amazon EC2 Auto Scaling can proactively increase
the capacity of your Auto Scaling group to match the anticipated load.
