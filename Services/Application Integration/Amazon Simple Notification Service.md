## [Amazon Simple Notification Service (SNS)](https://docs.aws.amazon.com/sns/latest/dg/welcome.html)
Amazon Simple Notification Service (SNS) is a fully managed service that provides message delivery from publishers (producers)
to subscribers (consumers).

### [SNS Topic](https://docs.aws.amazon.com/sns/latest/dg/sns-create-topic.html)
A SNS Topic is a logical access point that acts as a communication channel. A topic lets you group multiple endpoints.

### [SNS FIFO Topic](https://docs.aws.amazon.com/sns/latest/dg/sns-fifo-topics.html)
An SNS FIFO Topic provides strict message ordering and exactly-once message delivery using message group ids and
deduplication.

### [SNS Message Filtering](https://docs.aws.amazon.com/sns/latest/dg/sns-message-filtering.html)
By default, an Amazon SNS topic subscriber receives every message that's published to the topic.
To receive only a subset of the messages, a subscriber must assign a filter policy to the topic subscription.

A filter policy is a JSON object containing properties that define which messages the subscriber receives.
Amazon SNS supports policies that act on the message attributes or on the message body, according to the
filter policy scope that you set for the subscription. Filter policies for the message body assume that
the message payload is a well-formed JSON object.

### [SNS Subscription](https://docs.aws.amazon.com/sns/latest/dg/sns-create-subscribe-endpoint-to-topic.html)
To receive messages published to a topic, you must subscribe an endpoint to the topic. When you subscribe an endpoint to a topic, the
endpoint begins to receive messages published to the associated topic.

### [Fanout to SQS queues](https://docs.aws.amazon.com/sns/latest/dg/sns-sqs-as-subscriber.html)
Fanout to SQS queues allows a message to be delivered to multiple subscribed SQS queues.

### [SNS Security](https://docs.aws.amazon.com/sns/latest/dg/security.html)
SNS supports both in-flight encryption using HTTPS API and at-rest encryption using KMS keys.
Access is given through either IAM policies or SNS policies.