### [Amazon Elastic Compute Cloud (EC2)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)
Amazon Elastic Compute Cloud (Amazon EC2) is an Infrastructure as a Service (IaaS) offering that provides on‑demand,
scalable computing capacity in the AWS Cloud.

#### EC2 Instance Configuration Option
- **Operating System:** Linux, Windows or MacOS
- **vCPU**
- **Memory**
- **Storage:** Network-attached EBS, EFS storage, Hardware EC2 Instance Storage
- **Networking:** Network Card, IP address
- **Security Group**
- **User Data**

#### [EC2 Instance Store](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html)
An instance store provides ephemeral, temporary block-level storage for your EC2 instance. This storage is provided by disks that are
physically attached to the host computer. Instance store is ideal for temporary storage of information that changes frequently,
such as buffers, caches, scratch data, and other temporary content. An instance store consists of one or more instance store
volumes exposed as block devices. The size of an instance store as well as the number of devices available varies by instance type and instance size.

#### [EC2 Instance Metadata](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html#instancedata-data-categories)
Instance metadata is data about your instance that you can use to configure or manage the running instance. 

- **Instance Metadata Properties:** properties of the EC2 instance such as instance id, hostname, mac, etc.
- **Dynamic Data:** metadata that is generated when the instance is launched
- **User Data:** script that runs on the first startup of the instance, used to install software, configuration, etc. 

#### [EC2 Security Groups](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html)
A security group acts as a virtual firewall for your EC2 instances to control incoming and outgoing traffic.
Inbound rules control the incoming traffic to your instance, and outbound rules control the outgoing traffic from your instance.
You can associate each instance with multiple security groups, and you can associate each security group with multiple instances.
Security groups are stateful, if you send a request from your instance, the response traffic for that request is allowed to flow
in regardless of inbound security group rules. Also, responses to allowed inbound traffic are allowed to flow out, regardless of outbound rules.

#### [EC2 Instance Profile](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html)
An EC2 instance profile is a special IAM role container that you attach to an EC2 instance so the instance can obtain temporary AWS credentials
via the instance metadata service, without hard-coding access keys. It allows applications running on the instance to automatically assume
the role and access permitted AWS resources securely.

#### [EC2 Instance Types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html)
When you launch an instance, the instance type that you specify determines the hardware of the host computer used for your instance.
Each instance type offers different compute, memory, and storage capabilities, and is grouped in an instance family based on these capabilities.

Amazon EC2 dedicates some resources of the host computer, such as CPU, memory, and instance storage, to a particular instance.
Amazon EC2 shares other resources of the host computer, such as the network and the disk subsystem, among instances.
If each instance on a host computer tries to use as much of one of these shared resources as possible, each receives an equal share of that resource.
However, when a resource is underused, an instance can consume a higher share of that resource while it's available.

##### [EC2 Instance Type Series](https://docs.aws.amazon.com/ec2/latest/instancetypes/instance-type-names.html)
- **C** - Compute optimized
- **I** - Storage optimized
- **M** - General purpose
- **R** - Memory optimized
- **T** - Burstable Performance


#### [EC2 Purchasing Options](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-purchasing-options.html)
- **On-Demand:** Pay, by the second, for the instances that you launch
- **Savings Plan:** Reduce your Amazon EC2 costs by making a commitment to a consistent amount of usage, in USD per hour, for a term of 1 or 3 years
- **Reserved:** Reduce your Amazon EC2 costs by making a commitment to a consistent instance configuration, including instance type and Region, for a term of 1 or 3 years
- **Spot:** Request unused EC2 instances, which can reduce your Amazon EC2 costs significantly
- **Dedicated Hosts:** Pay for a physical host that is fully dedicated to running your instances, and bring your existing per-socket, per-core, or per-VM software licenses to reduce costs
- **Dedicated Instances:** Pay, by the hour, for instances that run on single-tenant hardware
- **Capacity Reservations:** Reserve capacity for your EC2 instances in a specific Availability Zone

#### [EC2 Instance Connect](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-connect-methods.html)
Amazon EC2 Instance Connect provides a secure way to connect to your Linux instances over Secure Shell (SSH).
With EC2 Instance Connect, you use AWS Identity and Access Management (IAM) policies and principals to control SSH access to your instances,
removing the need to share and manage SSH keys.

#### [Amazon Machine Image (AMI)](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html)
An Amazon Machine Image (AMI) is an image that provides the software that is required to set up and boot an Amazon EC2 instance.
You can create an AMI from your Amazon EC2 instances and then use it to launch instances with the same configuration.


### [AWS Elastic Beanstalk](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/Welcome.html)
AWS Elastic Beanstalk is an easy-to-use service for deploying and scaling web applications developed with Java, .NET, PHP, Node.js, and more.
You simply upload your application code and Elastic Beanstalk automatically handles all the infrastructure details including capacity provisioning,
load balancing, auto scaling, and application health monitoring. 

#### [Elastic Beanstalk Application](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts.html)
An Elastic Beanstalk application is a container for Elastic Beanstalk components, including environments, versions, and environment configurations.
Within an Elastic Beanstalk application, you manage all the resources relevant to running your code.

##### [Elastic Beanstalk Application Version](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts.html#concepts-version)
In Elastic Beanstalk, an application version refers to a specific, labeled iteration of deployable code for a web application.
An application version points to an Amazon Simple Storage Service (Amazon S3) object that contains the deployable code, such as a Java WAR file.


#### [Elastic Beanstalk Environment](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts.html)
An environment is a collection of AWS resources running an application version. Each environment runs only one application version at a time,
however, you can run the same application version or different application versions in many environments simultaneously.
When you create an environment, Elastic Beanstalk provisions the resources needed in your AWS account to run the application version you specified.

##### [Web Server Environment](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts-webserver.html)
A Web Server Environment in Elastic Beanstalk is designed to handle HTTP requests from users and serve web applications directly to the internet.
It automatically provisions and manages AWS resources including EC2 instances, an Elastic Load Balancer to distribute incoming traffic,
an Auto Scaling group for scaling based on demand, security groups for network access control, and CloudWatch monitoring.

##### [Worker Environment](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts-worker.html)
A Worker Environment in Elastic Beanstalk is designed to handle background processing tasks by pulling messages from an Amazon SQS queue.
Elastic Beanstalk automatically provisions EC2 instances with a daemon process that continuously reads messages from the SQS queue and
sends them as HTTP POST requests to your application for processing, making it ideal for asynchronous tasks like image processing, email sending,
or data analysis.


#### [Design Considerations](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts.concepts.design.html)
- **Scalability:** It is recommended to design applications stateless and scalable
- **Security:** Shared responsibility, configure security of data in transit and the security of the underlying application
- **Persistent Storage:** Beanstalk applications run on EC2 instances without persistent storage, configure your applications to store data in persistent AWS services to prevent data loss
- **Fault Tolerance:** Design for automated recovery by spreading instances across multiple AZ's, configure auto scaling to maintain a minimum fleet size
- **Content Delivery:** Integrate Amazon CloudFront to reduce latency
- **Software Updates and Patching:** Take advantage of Beanstalk's managed platform updates
- **Connectivity:** Ensure proper configuration for traffic routing in load-balanced applications

#### [Beanstalk Deployment Modes](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.deploy-existing-version.html)
- **All at once:** deploy new version to existing instances and restart application server, short downtime
- **Rolling:** update one batch of existing instances at a time, never complete downtime
- **Rolling with additional batch:** update one batch of instances at a time, keep capacity throughout deployment by having additional batch of new instances
- **Immutable:** deploy new version to new instances using a temporary Auto Scaling Group, move instances to existing Auto Scaling Group after all health checks pass, terminate old instances afterwards
- **Traffic splitting:** deploy new version to new instances using a temporary Auto Scaling Group, route a portion of the traffic to new version for a specific amount of time, switch all to new instances if health checks pass during that time
- **Blue/Green:** create second environment and reconfigure routing after successful deployment

#### [Beanstalk Lifecycle Policy](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/applications-lifecycle.html)
Elastic Beanstalk Lifecycle Policy automatically manages application versions by deleting old versions based on either their age or total count to prevent hitting the
application version quota (1000). The policy is applied each time you create a new version, deleting up to 100 old versions while preserving currently deployed or used
environments. Additionally, you can configure whether to delete the source bundles from S3 when application versions are deleted or retain them for data preservation.

#### [Elastic Beanstalk Extensions](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/ebextensions.html)
Elastic Beanstalk Extensions are configuration files placed in a `.ebextensions` folder within your application source bundle that allow you to customize and configure
your Elastic Beanstalk Environment beyond the default settings. These files use YAML or JSON format with a `.config` file extension and can modify configuration options,
install software, add AWS resources, and more. 

#### [Elastic Beanstalk Cloning](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.managing.clone.html)
Elastic Beanstalk Cloning allows you to create a new environment from an existing environment. The cloning process copies all environment settings, configuration
options, and resource configurations, but does not transfer data from databases or security groups. Cloning an environment allows you to optionally modify
settings including the underlying platform version.


### [AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)