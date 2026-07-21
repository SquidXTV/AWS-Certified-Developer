# [AWS CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html)

CodeDeploy is a deployment service that automates application deployments to Amazon EC2 instances,
on-premises instances, serverless Lambda functions, or Amazon ECS services.

## [CodeDeploy Application](https://docs.aws.amazon.com/codedeploy/latest/userguide/primary-components.html#primary-components-application)

An application is a name that uniquely identifies the application you want to deploy. CodeDeploy uses this name,
which functions as a container, to ensure the correct combination of revision, deployment configuration,
and deployment group are referenced during a deployment.


## [CodeDeploy Compute Platform](https://docs.aws.amazon.com/codedeploy/latest/userguide/primary-components.html#primary-components-compute-platform)

A compute platform is a platform on which CodeDeploy deploys an application. There are three compute platforms:
- EC2/On-Premises (with CodeDeploy Agent)
- Amazon ECS
- AWS Lambda


## [CodeDeploy Deployment Types](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployments.html)

### [CodeDeploy In-place Deployment](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html#welcome-deployment-overview-in-place)

In-place deployment in CodeDeploy updates the existing instances (EC2/On-Premises only) in a deployment group by stopping the old application
version and installing the new one on the same hosts.


### [CodeDeploy Blue/Green Deployment](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html#welcome-deployment-overview-blue-green)

A blue/green deployment provisions the new application version alongside the old version before rerouting.



## [CodeDeploy Predefined Deployment Configurations](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-configurations.html)

### [CodeDeploy Predefined Deployment Configurations on an EC2/On-Premises Platform](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-configurations.html#deployment-configuration-server)

- **AllAtOnce:** Attempts to deploy an application to as many instances as possible at once. Succeeds if at least one deployment is successful.
- **HalfAtAtime:** Deploys up to half of the instances at a time. Overall deployment succeeds if at least half of the instances deployed successful.
- **OneAtATime:** Deploys only one instance at a time. Only succeeds if all but the last instance deployed successful.


### [CodeDeploy Predefined Deployment Configurations on an ECS Platform](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-configurations.html#deployment-configuration-ecs)

- ECSAllAtOnce
- ECSLinear10PercentEvery1Minutes
- ECSLinear10PercentEvery3Minutes
- ECSCanary10Percent5Minutes
- ECSCanary10Percent15Minutes


### [CodeDeploy Predefined Deployment Configurations on an AWS Lambda Platform](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-configurations.html#deployment-configuration-lambda)

- LambdaAllAtOnce
- LambdaLinear10PercentEvery1Minute
- LambdaLinear10PercentEvery2Minute
- LambdaLinear10PercentEvery3Minute
- LambdaLinear10PercentEvery10Minute
- LambdaCanary10Percent5Minutes
- LambdaCanary10Percent10Minutes
- LambdaCanary10Percent15Minutes
- LambdaCanary10Percent30Minutes



## [CodeDeploy Hooks](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file-structure-hooks.html#reference-appspec-file-structure-hooks-list-ecs)

Hooks let you customize what happens at each stage (lifecycle events) during the deployment process.

### [CodeDeploy Hooks for an EC2/On-Premises Deployment](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file-structure-hooks.html#appspec-hooks-server)

- ApplicationStop
- DownloadBundle
- BeforeInstall
- Install
- AfterInstall
- ApplicationStart
- ValidateService
- BeforeBlockTraffic
- BlockTraffic
- AfterBlockTraffic
- BeforeAllowTraffic
- AllowTraffic
- AfterAllowTraffic


### [CodeDeploy Hooks for an ECS Deployment](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file-structure-hooks.html#appspec-hooks-ecs)

- BeforeInstall
- Install
- AfterInstall
- AllowTestTraffic
- AfterAllowTestTraffic
- BeforeAllowTraffic
- AllowTraffic
- AfterAllowTraffic


### [CodeDeploy Hooks for an AWS Lambda Deployment](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file-structure-hooks.html#appspec-hooks-lambda)

- BeforeAllowTraffic
- AllowTraffic
- AfterAllowTraffic



## [CodeDeploy Agent](https://docs.aws.amazon.com/codedeploy/latest/userguide/codedeploy-agent.html)

The AWS CodeDeploy agent is a software package that, when installed and configured on an instance, makes it possible for that instance to
be used in CodeDeploy deployments.


## [CodeDeploy Redeploy & Rollbacks](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployments-rollback-and-redeploy.html)

CodeDeploy rolls back deployments by redeploying a previously deployed revision of an application as a new deployment.
These rolled-back deployments are technically new deployments, with new deployment IDs, rather than restored versions of a previous deployment.
