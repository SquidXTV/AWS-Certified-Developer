## [Amazon CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)
Amazon CloudWatch monitors your Amazon Web Services (AWS) resources and the applications you run on AWS in real time,
and offers many tools to give you system-wide observability of your application performance, operational health,
and resource utilization.

### [CloudWatch Namespaces](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_concepts.html#Namespace)
A namespace is a container for CloudWatch metrics. Metrics in different namespaces are isolated from each other.

### [CloudWatch Metrics](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_concepts.html#Metric)
A metric represents a time-ordered set of data points published to CloudWatch. It is a variable to monitor and the data points
represent the values of that variable over time. 

#### [CloudWatch Metrics Time Stamps](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_concepts.html#Metric)
Each metric data point must be associated with a time stamp. The time stamp can be up to two weeks in the past and up to
two hours into the future. If you do not provide a time stamp, CloudWatch creates a time stamp for you based on the time
the data point was received. 

#### [CloudWatch Metrics Retention](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_concepts.html#Metric)
- Data points with a period of less than 60 seconds are available for 3 hours. These data points are high-resolution custom metrics.
- Data points with a period of 60 seconds (1 minute) are available for 15 days
- Data points with a period of 300 seconds (5 minutes) are available for 63 days
- Data points with a period of 3600 seconds (1 hour) are available for 455 days (15 months)

Data points that are initially published with a shorter period are aggregated together for long-term storage.
For example, if you collect data using a period of 1 minute, the data remains available for 15 days with 1-minute resolution.
After 15 days this data is still available, but is aggregated and is retrievable only with a resolution of 5 minutes.
After 63 days, the data is further aggregated and is available with a resolution of 1 hour.

#### [CloudWatch Custom Metrics](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/publishingMetrics.html)
CloudWatch allows you to publish your own metrics using the AWS CLI or using the `PutMetricData` API.


### [CloudWatch Dimensions](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_concepts.html#Dimension)
A dimension is a name/value pair that is part of the identity of a metric. You can assign up to 30 dimensions to a metric.
CloudWatch treats each unique combination of dimensions as a separate metric, even if the metrics have the same metric name.
You can only retrieve statistics using combinations of dimensions that you specifically published.
When you retrieve statistics, specify the same values for the namespace, metric name, and dimension parameters that were
used when the metrics were created.

### [CloudWatch Dashboards](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch_Dashboards.html)
CloudWatch Dashboards offer a unified view of your resources and applications with visualizations of your metrics and logs in
a single location.

### [CloudWatch Basic vs Detailed Monitoring](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch-metrics-basic-detailed.html)
CloudWatch provides both basic and detailed monitoring. Basic Monitoring is free, enabled by default and offered by most AWS services.
Detailed monitoring is offered by only some services at additional charges to gain more fine-grained and more frequent metrics.

### [CloudWatch Logs](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html)
You can use Amazon CloudWatch Logs to monitor, store, and access your log files. It enables you to centralize the
logs from all of your systems, applications, and AWS services that you use, in a single, highly scalable service.

#### [CloudWatch Log Streams](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/CloudWatchLogsConcepts.html)
A log stream is a sequence of log events that share the same source. More specifically, a log stream is generally intended
to represent the sequence of events coming from the application instance or resource being monitored.

#### [CloudWatch Log Groups](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/CloudWatchLogsConcepts.html)
Log groups define groups of log streams that share the same retention, monitoring, and access control settings.
Each log stream has to belong to one log group.

#### [CloudWatch Logs Insights](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/AnalyzingLogData.html)
With CloudWatch Logs Insights, you can interactively search and analyze your log data in Amazon CloudWatch Logs.
You can perform queries to help you more efficiently and effectively respond to operational issues.
It supports a purpose-built Logs Insights Query Language, OpenSearch Service Piped Processing Language and OpenSearch
Service Structured Query Language.

#### [CloudWatch Logs Export to S3](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/S3Export.html)
CloudWatch Logs can be exported to S3 buckets using the `CreateExportTask` API. Log data can take up to 12 hours to
become available for export.

#### [CloudWatch Logs Subscriptions](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/Subscriptions.html)
You can use subscriptions to get access to a real-time feed of log events from CloudWatch Logs and have it delivered
to other services such as an Amazon Kinesis stream, an Amazon Data Firehose stream, or AWS Lambda for custom processing,
analysis, or loading to other systems.

A subscription filter defines the filter pattern to use for filtering which log events get delivered to your AWS resource,
as well as information about where to send matching log events to.

#### [CloudWatch Logs Metric Filters](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/MonitoringLogData.html)
You can search and filter the log data coming into CloudWatch Logs by creating one or more metric filters.
Metric filters define the terms and patterns to look for in log data as it is sent to CloudWatch Logs. 

#### [CloudWatch Logs Security](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/security.html)
CloudWatch Logs are encrypted by default and supports AWS KMS for managed keys.


### [CloudWatch Alarms](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch_Alarms.html)
You can create alarms that watch metrics and send notifications or automatically make changes to the resources
you are monitoring when a threshold is breached.

#### [CloudWatch Alarm Actions and Targets](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/alarm-actions.html)
- SNS Notifications
- EC2 actions
- Auto Scaling actions
- Lambda Function invocation

#### [CloudWatch Composite Alarms](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/alarm-combining.html)
With CloudWatch, you can combine several alarms into one composite alarm to create a summarized, aggregated health indicator
over a whole application or group of resources. Composite alarms are alarms that determine their state by monitoring the states
of other alarms. You define rules to combine the status of those monitored alarms using Boolean logic.


### [CloudWatch Synthetic Monitoring](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/CloudWatch_Synthetics_Canaries.html)
You can use Amazon CloudWatch Synthetics to create canaries, configurable scripts that run on a schedule, to monitor your endpoints
and APIs. Canaries follow the same routes and perform the same actions as a customer, which makes it possible for you to continually
verify your customer experience even when you don't have any customer traffic on your applications. By using canaries, you can
discover issues before your customers do.

### [CloudWatch Agent](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/Install-CloudWatch-Agent.html)
CloudWatch agent is a software component that collects metrics, logs, and traces from your Amazon EC2 instances,
on-premises servers, and containerized applications. It enables you to monitor your infrastructure and applications
more comprehensively than the basic monitoring provided by default. 