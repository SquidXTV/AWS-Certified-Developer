## [AWS Elastic Beanstalk](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/Welcome.html)
AWS Elastic Beanstalk is an easy-to-use service for deploying and scaling web applications developed with Java, .NET, PHP, Node.js, and more.
You simply upload your application code and Elastic Beanstalk automatically handles all the infrastructure details including capacity provisioning,
load balancing, auto scaling, and application health monitoring. 

### [Elastic Beanstalk Application](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts.html)
An Elastic Beanstalk application is a container for Elastic Beanstalk components, including environments, versions, and environment configurations.
Within an Elastic Beanstalk application, you manage all the resources relevant to running your code.

#### [Elastic Beanstalk Application Version](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts.html#concepts-version)
In Elastic Beanstalk, an application version refers to a specific, labeled iteration of deployable code for a web application.
An application version points to an Amazon Simple Storage Service (Amazon S3) object that contains the deployable code, such as a Java WAR file.


### [Elastic Beanstalk Environment](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts.html)
An environment is a collection of AWS resources running an application version. Each environment runs only one application version at a time,
however, you can run the same application version or different application versions in many environments simultaneously.
When you create an environment, Elastic Beanstalk provisions the resources needed in your AWS account to run the application version you specified.

#### [Web Server Environment](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts-webserver.html)
A Web Server Environment in Elastic Beanstalk is designed to handle HTTP requests from users and serve web applications directly to the internet.
It automatically provisions and manages AWS resources including EC2 instances, an Elastic Load Balancer to distribute incoming traffic,
an Auto Scaling group for scaling based on demand, security groups for network access control, and CloudWatch monitoring.

#### [Worker Environment](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts-worker.html)
A Worker Environment in Elastic Beanstalk is designed to handle background processing tasks by pulling messages from an Amazon SQS queue.
Elastic Beanstalk automatically provisions EC2 instances with a daemon process that continuously reads messages from the SQS queue and
sends them as HTTP POST requests to your application for processing, making it ideal for asynchronous tasks like image processing, email sending,
or data analysis.


### [Design Considerations](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/concepts.concepts.design.html)
- **Scalability:** It is recommended to design applications stateless and scalable
- **Security:** Shared responsibility, configure security of data in transit and the security of the underlying application
- **Persistent Storage:** Beanstalk applications run on EC2 instances without persistent storage, configure your applications to store data in persistent AWS services to prevent data loss
- **Fault Tolerance:** Design for automated recovery by spreading instances across multiple AZ's, configure auto scaling to maintain a minimum fleet size
- **Content Delivery:** Integrate Amazon CloudFront to reduce latency
- **Software Updates and Patching:** Take advantage of Beanstalk's managed platform updates
- **Connectivity:** Ensure proper configuration for traffic routing in load-balanced applications

### [Beanstalk Deployment Modes](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.deploy-existing-version.html)
- **All at once:** deploy new version to existing instances and restart application server, short downtime
- **Rolling:** update one batch of existing instances at a time, never complete downtime
- **Rolling with additional batch:** update one batch of instances at a time, keep capacity throughout deployment by having additional batch of new instances
- **Immutable:** deploy new version to new instances using a temporary Auto Scaling Group, move instances to existing Auto Scaling Group after all health checks pass, terminate old instances afterwards
- **Traffic splitting:** deploy new version to new instances using a temporary Auto Scaling Group, route a portion of the traffic to new version for a specific amount of time, switch all to new instances if health checks pass during that time
- **Blue/Green:** create second environment and reconfigure routing after successful deployment

### [Beanstalk Lifecycle Policy](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/applications-lifecycle.html)
Elastic Beanstalk Lifecycle Policy automatically manages application versions by deleting old versions based on either their age or total count to prevent hitting the
application version quota (1000). The policy is applied each time you create a new version, deleting up to 100 old versions while preserving currently deployed or used
environments. Additionally, you can configure whether to delete the source bundles from S3 when application versions are deleted or retain them for data preservation.

### [Elastic Beanstalk Extensions](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/ebextensions.html)
Elastic Beanstalk Extensions are configuration files placed in a `.ebextensions` folder within your application source bundle that allow you to customize and configure
your Elastic Beanstalk Environment beyond the default settings. These files use YAML or JSON format with a `.config` file extension and can modify configuration options,
install software, add AWS resources, and more. 

### [Elastic Beanstalk Cloning](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/using-features.managing.clone.html)
Elastic Beanstalk Cloning allows you to create a new environment from an existing environment. The cloning process copies all environment settings, configuration
options, and resource configurations, but does not transfer data from databases or security groups. Cloning an environment allows you to optionally modify
settings including the underlying platform version.