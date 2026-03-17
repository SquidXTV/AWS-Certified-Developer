## [Amazon Elastic Container Service (ECS)](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html)
Amazon ECS is a fully managed container orchestration service to build, manage, and run containerized workloads.

### [ECS Clusters](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/clusters.html)
An Amazon ECS cluster is a logical grouping of tasks or services that provides the **infrastructure capacity** for your containerized applications.
When creating a cluster, you choose from the three primary infrastructure types, each optimized for different use cases and operational requirements.

- **Amazon ECS Managed Instances:** EC2 instances managed by AWS, only specify underlying instance type
- **Amazon ECS Fargate:** Serverless compute
- **Amazon EC2 Instances:** Full control, own managed EC2 instances
- **Amazon ECS Everywhere:** Own external instances such as on-premises servers or VMs

### [ECS Task Definitions](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definitions.html)
A task definition is a blueprint for your application with 0..n containers. A task is a simple running instance of that blueprint, while an ECS Service
manages a specified number of instances of that blueprint continuously, handling health checks, restarts, and optional load balancing.

#### Infrastructure Configuration
- Infrastructure Type / Launch Type / Capacity Option
- OS, Architecture, and Network Mode
- CPU, Memory
- Task Role, Task Execution Role
- Storage
- Monitoring

#### Container Configuration
- Name
- Image URI
- Port Mappings
- CPU, Memory, (GPU), Ulimits
- Environment Variables
- Logging
- Restart Policy, Healthcheck
- Startup Dependency, Timeouts
- Networking
- Entrypoint, Command, Working Directory


### [EC2 Instance Profile](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/managed-instances-instance-profile.html)
An instance profile is an IAM container that holds exactly one IAM role and allows Amazon EC2 Instances or Amazon ECS Managed Instances
to assume that role securely. The instance profile contains an instance role that the ECS agent assumes to register instances with
clusters and communicate with the ECS service.

### [ECS Task Role](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-iam-roles.html)
Your Amazon ECS tasks can have an IAM role associated with them. The permissions granted in the IAM role are vended to containers running in the task.
This role allows your application code (running in the container) to use other AWS services. The task role is required when your application accesses
other AWS services, such as Amazon S3.

### [Storage Options](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/using_data_volumes.html)
- **Elastic File System (EFS):** persistent shared network file storage
- **Elastic Block Store (EBS):** block storage
- **Docker Volumes**: docker-managed storage
- **Bind mounts**: mount directory or file from host instance file system to the container


### [ECS Load Balancing](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/service-load-balancing.html)
Your service can optionally be configured to use Elastic Load Balancing to distribute traffic evenly across the tasks in your service.

- Application Load Balancer (ALB)
- Network Load Balancer (NLB)
- Gateway Load Balancer (GLB)

### [ECS Service Auto Scaling](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/service-auto-scaling.html)
Automatic scaling is the ability to increase or decrease the desired number of tasks in your Amazon ECS service automatically.
Amazon ECS leverages the Application Auto Scaling service to provide this functionality.

### [ECS Cluster Auto Scaling](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/cluster-auto-scaling.html)
Amazon ECS can manage the scaling of Amazon EC2 instances that are registered to your cluster.
This is referred to as Amazon ECS cluster auto scaling.

### [ECS Rolling Updates](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/deployment-type-ecs.html)
When you create a service which uses the rolling update (ECS) deployment type, the Amazon ECS service scheduler replaces the currently running tasks
with new updated tasks. The number of tasks that Amazon ECS adds or removes from the service during a rolling update is controlled by the
`minimumHealthyPercent` and `maximumPercent` parameters.

### [ECS Task Placement](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-placement.html)
You can use task placement to configure Amazon ECS to place your tasks on container instances that meet certain criteria,
for example an Availability Zone or instance type.

#### Task Placement Process
1. Identify the container instances that satisfy the CPU, GPU, memory, and port requirements in the task definition.
2. Identify the container instances that satisfy the task placement constraints.
3. Identify the container instances that satisfy the task placement strategy. (Amazon ECS Managed Instances does not support task placement strategies. Amazon ECS will try its best to spread tasks across accessible Availability Zones.)
4. Select the instances for task placement.

#### [Task Placement Constraints](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-placement-constraints.html)
These are rules that must be met in order to place a task on a container instance. If the constraint is not met, the task is not placed and
remains in the `PENDING` state. For example, you can use a constraint to place tasks only on a particular instance type.

#### [Task Placement Strategy](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-placement-strategies.html)
For tasks that use the EC2 launch type, Amazon ECS must determine where to place the task based on the requirements specified in the task definition,
such as CPU and memory. Similarly, when you scale down the task count, Amazon ECS must determine which tasks to terminate. You can apply task placement
strategies and constraints to customize how Amazon ECS places and terminates tasks. 

- **Binpack:** Tasks are placed on container instances so as to leave the least amount of unused CPU or memory. This strategy minimizes the number of container instances in use.
- **Random:** Tasks are placed randomly.
- **Spread:** When the spread strategy is used and a scale-in action is taken, Amazon ECS selects tasks to terminate that maintain a balance across Availability Zones. Within an Availability Zone, tasks are selected at random.
