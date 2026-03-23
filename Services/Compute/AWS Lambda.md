## [AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)
AWS Lambda is a compute service that runs code as functions without the need to manage servers.
Your functions runs, scaling up and down automatically, with pay-per-use and compute time pricing.

### [Lambda Deployment](https://docs.aws.amazon.com/lambda/latest/dg/lambda-functions.html)

#### [Lambda File Archive](https://docs.aws.amazon.com/lambda/latest/dg/configuration-function-zip.html)
AWS Lambda .zip file deployment packages are compressed archives containing your function code and dependencies,
with a maximum size limit of 3 MB when unzipped. You can upload .zip files directly through the Lambda console
for packages under 50 MB, or store them in Amazon S3 for larger packages, and Lambda will extract and run your code
from the archive in the execution environment.

#### [Lambda Container Images](https://docs.aws.amazon.com/lambda/latest/dg/images-create.html)
AWS Lambda supports Container Images as an alternative deployment package to .zip files, allowing you to package your function code and dependencies
in a Docker container image up to 10 GB in size and store it in Amazon ECR. You can use AWS-provided base images for popular runtimes or bring your own
base image, as long as it implements the Lambda Runtime API.

#### [Lambda in CloudFormation Template](https://docs.aws.amazon.com/lambda/latest/dg/configuration-function-zip.html#configuration-function-cloudformation)
In CloudFormation templates, you can define Lambda functions inline by using the `ZipFile` property within the `Code` section for simple Node.js
or Python functions, allowing you to write the function code directly in the template. Alternatively, you can reference a deployment package stored
in S3 by specifying the `S3Bucket` and `S3Key` properties in the Code section, which is required for larger functions or other runtimes that don't
support inline code.

#### [Lambda Versions](https://docs.aws.amazon.com/lambda/latest/dg/configuration-versions.html)
You can use versions to manage the deployment of your functions. Lambda creates a new version of your function each time that you publish the function.
The new version is a copy of the unpublished version of the function. The unpublished version is named `$LATEST`.
Importantly, any time you deploy your function code, you overwrite the current code in `$LATEST`. To save the current iteration of `$LATEST`,
create a new function version. After you publish a function version, its code, runtime, architecture, memory, layers, and most other configuration
settings are immutable.

#### [Lambda Aliases](https://docs.aws.amazon.com/lambda/latest/dg/configuration-aliases.html)
You can create aliases for your Lambda function. A Lambda alias is a pointer to a function version that you can update.
The function's users can access the function version using the alias Amazon Resource Name (ARN). When you deploy a new version,
you can update the alias to use the new version, or split traffic between two versions.
You can use a weighted alias to split traffic between two different versions of the same function.
With this approach, you can test new versions of your functions with a small percentage of traffic and quickly roll back if necessary.


### [Lambda Invocation](https://docs.aws.amazon.com/lambda/latest/dg/lambda-invocation.html)

#### [Lambda Synchronous Invocation](https://docs.aws.amazon.com/lambda/latest/dg/invocation-sync.html)
When you invoke a function synchronously, Lambda runs the function and waits for a response.
When the function completes, Lambda returns the response from the function's code with additional data,
such as the version of the function that was invoked.

#### [Lambda Asynchronous Invocation](https://docs.aws.amazon.com/lambda/latest/dg/invocation-async.html)
When you invoke a function asynchronously, you don't wait for a response from the function code.
You hand off the event to Lambda and Lambda handles the rest. You can configure how Lambda handles errors,
and can send invocation records to a downstream resource such as Amazon Simple Queue Service or Amazon EventBridge
to chain together components of your application.

For asynchronous invocation, Lambda places the event in a queue and returns a success response without additional information.
A separate process reads events from the queue and sends them to your function.

Lambda manages your function's asynchronous event queue and attempts to retry on errors. If the function returns an error,
by default Lambda attempts to run it two more times, with a one-minute wait between the first two attempts, and two minutes
between the second and third attempts. Function errors include errors returned by the function's code and errors returned by
the function's runtime, such as timeouts.

Lambda can send records of finished asynchronous invocations to either SQS, SNS, S3, Lambda, or EventBridge.
The invocation record contains details about the request and response in JSON format.
You can configure separate destinations for events that are processed successfully, and events that fail all processing attempts.

#### [Lambda Event Source Mapping](https://docs.aws.amazon.com/lambda/latest/dg/invocation-eventsourcemapping.html)
An event source mapping is a Lambda resource that reads items from stream and queue-based services and invokes a function with
batches of records. Within an event source mapping, resources called event pollers actively poll for new messages and invoke functions.

By default, an event source mapping batches records together into a single payload that Lambda sends to your function.
To fine-tune batching behavior, you can configure a batching window (MaximumBatchingWindowInSeconds) and a batch size (BatchSize).
A batching window is the maximum amount of time to gather records into a single payload. A batch size is the maximum number of records in a single batch.

By default, if your function returns an error, the event source mapping reprocesses the entire batch until the function succeeds,
or the items in the batch expire. To ensure in-order processing, the event source mapping pauses processing for the affected shard
until the error is resolved.

#### [Lambda Function URL](https://docs.aws.amazon.com/lambda/latest/dg/urls-configuration.html)
A function URL is a dedicated HTTP(S) endpoint for your Lambda function. When you create a function URL, Lambda automatically generates a unique URL endpoint for you.
Once you create a function URL, its URL endpoint never changes. The URL endpoints are in the format of `https://<url-id>.lambda-url.<region>.on.aws`.
Lambda function URLs use resource-based policies for security and access control. Function URLs also support cross-origin resource sharing configuration options.

The `AuthType` parameter determines how Lambda authenticates and authorizes requests to your function url. It is either `AWS_IAM` to secure functions using
AWS IAM or `NONE` to not perform any authentication before invoking the function.

#### [Lambda Invocation through ALB](https://docs.aws.amazon.com/lambda/latest/dg/services-alb.html)
You can use a Lambda function to process requests from an Application Load Balancer. Elastic Load Balancing supports Lambda
functions as a target for an Application Load Balancer. Use load balancer rules to route HTTP requests to a function,
based on path or header values. Process the request and return an HTTP response from your Lambda function.
Elastic Load Balancing invokes your Lambda function synchronously with an event that contains the request body and metadata.

#### [Lambda Invocation through EventBridge Scheduler](https://docs.aws.amazon.com/lambda/latest/dg/with-eventbridge-scheduler.html)
Amazon EventBridge Scheduler is a serverless scheduler that allows you to create, run, and manage tasks from one central, managed service.
With EventBridge Scheduler, you can create schedules using cron and rate expressions for recurring patterns, or configure one-time invocations.
When you set up EventBridge Scheduler with Lambda, EventBridge Scheduler invokes your Lambda function asynchronously.

#### [Lambda Invocation through S3 Event Notifications](https://docs.aws.amazon.com/lambda/latest/dg/with-s3.html)
You can use Lambda to process event notifications from Amazon Simple Storage Service. Amazon S3 can send an event to a Lambda function
when an object is created or deleted. You configure notification settings on a bucket, and grant Amazon S3 permission to invoke a function
on the function's resource-based permissions policy.
Amazon S3 invokes your function asynchronously with an event that contains details about the object.


### [Lambda Event Object](https://docs.aws.amazon.com/lambda/latest/dg/java-handler.html#java-handler-input)
The AWS Lambda event object is a JSON-formatted document wrapped in an object that contains the data your function needs to process,
passed as the first parameter to your handler function. The structure and content of the event object varies depending on the event.

### [Lambda Context Object](https://docs.aws.amazon.com/lambda/latest/dg/java-context.html)
The AWS Lambda context object is passed as the second parameter to your handler function and provides methods and properties containing
information about the invocation, function, and execution environment.
- Request Id
- Function Name
- Function Version
- Invoked Function ARN
- Memory Limit in MB
- Log Group Name
- Log Stream Name

### [Lambda Execution Role](https://docs.aws.amazon.com/lambda/latest/dg/lambda-intro-execution-role.html)
A Lambda function's execution role is an IAM role that grants the function permission to access AWS services and resources.

### [Lambda Resource-Based Policies](https://docs.aws.amazon.com/lambda/latest/dg/access-control-resource-based.html)
You can use resource-based policies to grant access to the function to other AWS accounts, organizations, or services.

### [Lambda Monitoring](https://docs.aws.amazon.com/lambda/latest/dg/lambda-monitoring.html)
When your AWS Lambda function finishes processing an event, Lambda automatically sends metrics about the invocation to Amazon CloudWatch.
As long as your function's execution role has the necessary permissions, Lambda captures logs for all requests handled by your function
and sends them to Amazon CloudWatch Logs, which is the default destination.
You can use AWS X-Ray to visualize the components of your application, identify performance bottlenecks, and troubleshoot requests that resulted in an error.
Your Lambda functions send trace data to X-Ray, and X-Ray processes the data to generate a service map and searchable trace summaries.

### [Lambda Edge Functions](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/edge-functions.html)
With Amazon CloudFront, you can write your own code to customize how your CloudFront distributions process HTTP requests and responses.
The code runs close to your viewers (users) to minimize latency, and you don’t have to manage servers or other infrastructure.
You can write code to manipulate the requests and responses that flow through CloudFront, perform basic authentication and authorization,
generate HTTP responses at the edge, and more.

CloudFront Functions are lightweight functions written in JavaScript for high-scale, latency-sensitive CDN customization. They are usually used
to transform or verify incoming requests.
Lambda@Edge offers powerful and flexible computing for complex functions and full application logic closer to your viewers.

### [Lambda Configuration](https://docs.aws.amazon.com/lambda/latest/dg/lambda-functions.html)

#### [Lambda Memory](https://docs.aws.amazon.com/lambda/latest/dg/configuration-memory.html)
Lambda allocates CPU power in proportion to the amount of memory configured. Memory is the amount of memory available to your Lambda function at runtime.
You can increase or decrease the memory and CPU power allocated to your function using the Memory setting.
You can configure memory between 128 MB and 10,240 MB in 1-MB increments. At 1,769 MB, a function has the equivalent of one vCPU.

#### [Lambda Environment Variables](https://docs.aws.amazon.com/lambda/latest/dg/configuration-envvars.html)
An environment variable is a pair of strings that is stored in a function's version-specific configuration.
The Lambda runtime makes environment variables available to your code and sets additional environment variables
that contain information about the function and invocation request.

#### [Lambda Timeout](https://docs.aws.amazon.com/lambda/latest/dg/configuration-timeout.html)
Lambda runs your code for a set amount of time before timing out. Timeout is the maximum amount of time in seconds that a Lambda function can run.
The default value for this setting is 3 seconds, but you can adjust this in increments of 1 second up to a maximum value of 900 seconds.

#### [Lambda Execution Context](https://docs.aws.amazon.com/lambda/latest/dg/lambda-runtime-environment.html)
Lambda invokes your function in an execution environment, which provides a secure and isolated runtime environment.
The execution environment manages the resources required to run your function.

When Lambda receives a request to run a function via the Lambda API, the service first prepares an execution environment.
During this initialization phase, the service downloads your code, starts the environment, and runs any initialization code outside of the main handler.
After the invocation completes, the execution environment is frozen. To improve resource management and performance, Lambda retains
the execution environment for a period of time. During this time, if another request arrives for the same function, Lambda can reuse the environment.
This second request typically finishes more quickly, since the execution environment is already fully set up.

#### [Lambda Ephemeral Storage](https://docs.aws.amazon.com/lambda/latest/dg/configuration-ephemeral-storage.html)
Lambda provides ephemeral storage for functions in the `/tmp` directory. This storage is temporary and unique to each execution environment.
You can control the amount of ephemeral storage allocated to your function using the Ephemeral storage setting.
You can configure ephemeral storage between 512 MB and 10,240 MB, in 1-MB increments. All data stored in `/tmp` is encrypted at rest with a key managed by AWS.

#### [Lambda File System Mounting](https://docs.aws.amazon.com/lambda/latest/dg/configuration-filesystem.html)
You can configure a function to mount an Amazon Elastic File System file system to a local directory.
With Amazon EFS, your function code can access and modify shared resources safely and at high concurrency.

#### [Lambda VPC](https://docs.aws.amazon.com/lambda/latest/dg/configuration-vpc.html)
You can give your Lambda function access to resources hosted in an Amazon VPC by attaching your function to the VPC through
the private subnets that contain the resources.

To attach a Lambda function to an Amazon VPC in your AWS account, Lambda needs permissions to create and manage the network
interfaces it uses to give your function access to the resources in the VPC. You can give your function the permissions it
needs by attaching the AWS managed policy `AWSLambdaVPCAccessExecutionRole` to your function's execution role.

Configure NAT Gateway and Internet Gateways to provide internet access to VPC-connected Lambda functions.
VPC endpoints can be used to privately access AWS services from within a Lambda function.


### [Lambda Layers](https://docs.aws.amazon.com/lambda/latest/dg/chapter-layers.html)
A Lambda layer is a .zip file archive that contains supplementary code or data. Layers usually contain library dependencies,
a custom runtime, or configuration files.

This allows you to reduce the size of your deployment package, separate core function logic from dependencies and share dependencies across
multiple functions. When you add a layer to a function, Lambda extracts the layer contents into the `/opt` directory in your function’s execution environment.

### [Lambda Concurrency](https://docs.aws.amazon.com/lambda/latest/dg/lambda-concurrency.html)
Concurrency is the number of in-flight requests that your AWS Lambda function is handling at the same time.
For each concurrent request, Lambda provisions a separate instance of your execution environment.
As your functions receive more requests, Lambda automatically handles scaling the number of execution environments
until you reach your account's concurrency limit. By default, Lambda provides your account with a total concurrency
limit of 1,000 concurrent executions across all functions in an AWS Region.

Each invocation over the concurrency limit will trigger a throttle. Synchronous invocations return a throttle error with status code 429,
whereas asynchronous invocations retry automatically and eventually go to the dead letter queue.

#### [Lambda Reserved Concurrency](https://docs.aws.amazon.com/lambda/latest/dg/configuration-concurrency.html)
Reserved concurrency is useful for ensuring that your most critical functions always have enough concurrency to handle incoming requests.
Additionally, reserved concurrency can be used for limiting concurrency to prevent overwhelming downstream resources, like database connections.
Reserved concurrency acts as both a lower and upper bound - it reserves the specified capacity exclusively for your function while also preventing
it from scaling beyond that limit.

#### [Lambda Provisioned Concurrency](https://docs.aws.amazon.com/lambda/latest/dg/provisioned-concurrency.html)
This is the number of pre-initialized execution environments allocated to your function. These execution environments are ready to respond
immediately to incoming function requests. Provisioned concurrency is useful for reducing cold start latencies for functions and designed
to make functions available with double-digit millisecond response times.
