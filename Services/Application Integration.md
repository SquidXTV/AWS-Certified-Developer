### [AWS AppSync](https://docs.aws.amazon.com/appsync/latest/devguide/what-is-appsync.html)

### [Amazon EventBridge](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-what-is.html)

### [Amazon Simple Notification Service (SNS)](https://docs.aws.amazon.com/sns/latest/dg/welcome.html)

### [Amazon Simple Queue Service (SQS)](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html)
Amazon Simple Queue Service offers a fully managed message queuing service that enables you to decouple and scale distributed software
systems. In SQS, **producers** are applications or services that send messages to queues, while **consumers** are applications that receive
and process messages from those queues.

#### [SQS Standard Queue](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-queue-types.html)
The SQS Standard Queue supports a very high, nearly unlimited number of API calls per second and guarantees at-least-once delivery
of messages. In some cases, a message may be delivered more than once due to retries or network delays. It also provides best-effort
ordering, where SQS attempts to deliver messages in the order they were sent, but it does not guarantee this.

#### [SQS FIFO Queue](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-fifo-queues.html)
The SQS FIFO Queues provide exactly-once processing and strict message ordering, ensuring messages are delivered in the exact order
they were sent and preventing duplicates from being introduced into the queue. Duplicate messages are based on either content-based
deduplication using a SHA-256 hash from the message body or by explicitly providing a unique message deduplication id.

#### [SQS Message Visibility Timeout](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html)
When you receive a message from an Amazon SQS queue, it remains in the queue but becomes temporarily invisible to other consumers.
This invisibility is controlled by the visibility timeout, which ensures that other consumers cannot process the same message
while you are working on it. After that you explicitly delete messages after successful processing.

#### [SQS Delay Queues](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-delay-queues.html)
Delay queues let you postpone the delivery of new messages to consumers for a number of seconds, for example,
when your consumer application needs additional time to process messages. If you create a delay queue, any messages
that you send to the queue remain invisible to consumers for the duration of the delay period.

#### [SQS Dead Letter Queues](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-dead-letter-queues.html)
Amazon SQS supports dead-letter queues (DLQs), which source queues can target for messages that are not processed successfully.
Use a redrive policy to specify the maxReceiveCount. The maxReceiveCount is the number of times a consumer can receive a message
from a source queue before it is moved to a dead-letter queue.

#### [SQS Short and Long Polling](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-short-and-long-polling.html)
- **Short Polling:** the poll request queries a subset of servers to find available messages and sends an immediate response, even if no messages are found
- **Long Polling:** the poll request queries all servers for messages, sending a response once at least one message is available.
  An empty response is sent only if the pooling wait time expires

#### [SQS Message Quotas](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/quotas-messages.html)
- **Message Retention:** by default, a message is retained for 4 days, minimum is 60 seconds and maximum is 14 days
- **Message Timer:** the default delay for a message is 0 seconds, the maximum is 15 minutes
- **Message Visibility Timeout:** the default visibility timeout for a message is 30 seconds, the minimum is 0 seconds and the maximum is 12 hours
- **Message Size:** the minimum message size is 1 byte, the maximum is 1048 Kb

#### [SQS Extended Client](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-managing-large-messages.html)
The SQS Extended Client allows you to send messages larger than 1048 Kb by storing the payload in an Amazon S3 bucket and send a reference
to the stored object in the SQS queue.

#### [SQS Security](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/security.html)
SQS supports both in-flight encryption using HTTPS API and at-rest encryption using KMS keys.
Access is given through either IAM policies at the user or SQS policies applied to the queue.


### [AWS Step Functions](https://docs.aws.amazon.com/step-functions/latest/dg/welcome.html)