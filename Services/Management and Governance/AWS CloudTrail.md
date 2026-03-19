## [AWS CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)
AWS CloudTrail is an AWS service that helps you enable operational and risk auditing, governance, and compliance
of your AWS account. Actions taken by a user, role, or an AWS service are recorded as events in CloudTrail.
Events include actions taken in the AWS Management Console, AWS Command Line Interface, and AWS SDKs and APIs.

### [CloudTrail Trail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-concepts.html#cloudtrail-concepts-trails)
A trail is a configuration that enables delivery of CloudTrail events to an S3 bucket, with optional delivery
to CloudWatch Logs and Amazon EventBridge. You can use a trail to choose the CloudTrail events you want delivered,
encrypt your CloudTrail event log files with an AWS KMS key, and set up Amazon SNS notifications for log file delivery.

### [CloudTrail Management Events](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-concepts.html)
Management events provide information about management operations that are performed on resources in your AWS account.
These are also known as control plane operations. These are captured and stored by default.

### [CloudTrail Data Events](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-concepts.html)
Data events provide information about the resource operations performed on or in a resource.
These are also known as data plane operations. Data events are often high-volume activities.

Data events are not logged by default when you create a trail or event data store.
To record CloudTrail data events, you must explicitly add each resource type for which you want to collect activity.

### [CloudTrail Network Activity Events](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-concepts.html)
CloudTrail network activity events enable VPC endpoint owners to record AWS API calls made using their VPC endpoints
from a private VPC to the AWS service. Network activity events provide visibility into the resource operations performed within a VPC.

Network activity events are not logged by default when you create a trail or event data store.
To record CloudTrail network activity events, you must explicitly set the event source for which you want to collect activity.

### [CloudTrail Insights Events](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-concepts.html)
CloudTrail Insights events capture unusual API call rate or error rate activity in your AWS account by analyzing CloudTrail
management activity. Insights events provide relevant information, such as the associated API, error code, incident time,
and statistics, that help you understand and act on unusual activity. Unlike other types of events captured in a CloudTrail
trail or event data store, Insights events are logged only when CloudTrail detects changes in your account's API usage or
error rate logging that differ significantly from the account's typical usage patterns.

### [CloudTrail Retention](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-concepts.html#cloudtrail-concepts-event-history)
CloudTrail Events are stored for 90 days. To keep events beyond this period, log them to an S3 bucket.