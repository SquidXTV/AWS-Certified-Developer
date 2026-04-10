## [AWS CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html)
CodeDeploy is a deployment service that automates application deployments to Amazon EC2 instances,
on-premises instances, serverless Lambda functions, or Amazon ECS services.

### [CodeDeploy Application](https://docs.aws.amazon.com/codedeploy/latest/userguide/primary-components.html#primary-components-application)
An application is a name that uniquely identifies the application you want to deploy. CodeDeploy uses this name,
which functions as a container, to ensure the correct combination of revision, deployment configuration,
and deployment group are referenced during a deployment.

### [CodeDeploy Compute Platform](https://docs.aws.amazon.com/codedeploy/latest/userguide/primary-components.html#primary-components-compute-platform)
A compute platform is a platform on which CodeDeploy deploys an application. There are three compute platforms:
- EC2/On-Premises
- AWS Lambda
- Amazon ECS

### [CodeDeploy Agent](https://docs.aws.amazon.com/codedeploy/latest/userguide/codedeploy-agent.html)
The AWS CodeDeploy agent is a software package that, when installed and configured on an instance, makes it possible for that instance to
be used in CodeDeploy deployments.

### [CodeDeploy Redeploy & Rollbacks](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployments-rollback-and-redeploy.html)
CodeDeploy rolls back deployments by redeploying a previously deployed revision of an application as a new deployment.
These rolled-back deployments are technically new deployments, with new deployment IDs, rather than restored versions of a previous deployment.
