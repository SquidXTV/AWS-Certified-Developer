## [AWS CloudFormation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/Welcome.html)
CloudFormation is a Infrastructure as Code (IaC) service that helps you model and set up your AWS resources. You create
a template that describes all the AWS resources that you want and CloudFormation takes care of provisioning and configuring those
for you.

### [CloudFormation Template](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-guide.html)
An AWS CloudFormation template defines the AWS resources you want to create, update, or delete as part of a stack.
You can create templates using the AWS Infrastructure Composer, plain JSON or YAML files, or the IaC generator.
Templates are either stored in an Amazon S3 bucket or referenced from a Git repository.

- **AWSTemplateFormatVersion:** set the template format version that the template conforms to
- **Description:** description of the template
- **Parameters:** input custom values each time running the template
- **Mapping:** hardcoded key-value pairs for mapping values
- **Resources:** required section to declare AWS resources that you want to create as part of your stack
- **Outputs:** declare output values that can be imported into other stacks
- **Conditions:** define conditions to apply to resources

### [Intrinsic Functions](https://docs.aws.amazon.com/AWSCloudFormation/latest/TemplateReference/intrinsic-function-reference.html)
- **Fn::Ref:** returns the value of a specified parameter, resource, or another intrinsic function
- **Fn::FindInMap:** returns the value of a key-value pair from mapping section
- **Fn::ImportValue:** returns the value of an output exported by another stack
- **Fn::GetAtt:** returns the value of an attribute from a resource
- **Fn::And/Or/Equals/Not/If/:** returns true or false based on the condition
- **Fn::Base64:** returns the Base64 representation of the input

### [CloudFormation Capabilities](https://docs.aws.amazon.com/AWSCloudFormation/latest/APIReference/API_CreateStack.html)
In some cases you must explicitly acknowledge that your template contains certain capabilities in order for CloudFormation to create the stack.
- **CAPABILITY_IAM / CAPABILITY_NAMED_IAM:** allow the creation and management of IAM resources
- **CAPABILITY_AUTO_EXPAND:** allow macros to transform the template

### [CloudFormation Stack](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacks.html)
A stack is a collection of AWS resources that you can manage as a single unit. In other words, you can create, update,
and delete a collection of resources by creating, updating, and deleting stacks.

**Creating** a stack involves deploying a CloudFormation Template that specifies the resources and their configuration.
**Deleting** a stack deletes the resources associated with it.

**Updating** a stack involves making changes to the template or parameters. CloudFormation compares the changes with the
current state of your stack and updates only the changed resources. It might interrupt running or replace updated resources.
Updates can either be reviewed and deployed by Change sets, that summarize the changes of a stack in a preview, or through
direct updates that immediately deploys changes.

CloudFormation operations work as all or nothing. It ensures all stack resources are created or deleted as appropriate.
Because CloudFormation treats the stack resources as a single unit, they must all be created or deleted successfully for
the stack to be created or deleted. If a resource can't be created, CloudFormation rolls the stack back and automatically
deletes any resources that were created. If a resource can't be deleted, any remaining resources are retained until
the stack can be successfully deleted.

### [CloudFormation Stack Failure Options](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stack-failure-options.html)
- Roll back all resources to last known stable state on failure
- Preserve successfully provisioned resources and roll back failed resources to last known stable state

### [CloudFormation Stack Deletion Policy](https://docs.aws.amazon.com/AWSCloudFormation/latest/TemplateReference/aws-attribute-deletionpolicy.html)
- **Delete:** delete resource and its content during stack deletion
- **Retain:** keep the resource and its content when the stack is deleted
- **RetainExceptOnCreate:** keep the resource and its content when the stack is deleted except if it was newly created and rolled back
- **Snapshot:** creates a snapshot of the resource before deleting if supported

### [CloudFormation Stack Policy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/protect-stack-resources.html)
When you create a stack, all update actions are allowed on all resources. By default, anyone with stack update permissions
can update all of the resources in the stack. During an update, some resources might require an interruption or be completely
replaced, resulting in new physical IDs or completely new storage. You can prevent stack resources from being unintentionally
updated or deleted during a stack update by using a stack policy. A stack policy is a JSON document that defines the update actions
that can be performed on designated resources.

### [CloudFormation Stack Termination Protection](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-protect-stacks.html)
You can prevent a stack from being accidentally deleted by enabling termination protection on the stack.
If a user attempts to delete a stack with termination protection enabled, the deletion fails and the stack, including its status,
remains unchanged. You can enable termination protection on a stack when you create it. Termination protection on stacks is disabled
by default.

### [CloudFormation Stack Service Role](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-servicerole.html)
A service role is an IAM role that allows CloudFormation to make calls to resources in a stack on your behalf. 
You can specify an IAM role that allows CloudFormation to create, update, or delete your stack resources.
By default, CloudFormation uses a temporary session that it generates from your user credentials for stack operations.
If you specify a service role, CloudFormation uses that role's credentials.

### [CloudFormation StackSets](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacksets-concepts.html#stacksets-concepts-stackset)
A StackSet serves as a container for multiple stacks that are deployed across specified AWS accounts and Regions.
Each stack is based on the same CloudFormation template, but you can customize individual stacks using parameters.
