## [Amazon Kinesis](https://docs.aws.amazon.com/kinesis/)
Amazon Kinesis makes it easy to collect, process, and analyze video and data streams in real time. 

### [Amazon Kinesis Data Streams](https://docs.aws.amazon.com/streams/latest/dev/introduction.html)
Amazon Kinesis Data Streams allow you to collect and process large streams of data records.
A data stream is a set of shards. Each shard has a sequence of data records and each data record has a
sequence number that is assigned by Kinesis Data Streams.

#### [Kinesis Data Record](https://docs.aws.amazon.com/streams/latest/dev/key-concepts.html)
A data record is the unit of data stored in a data stream. Data records are composed of a sequence number,
a partition key, and a data blob, which is an immutable sequence of bytes. Kinesis Data Streams does not
inspect, interpret, or change the data in the blob in any way.

#### [Kinesis Shard](https://docs.aws.amazon.com/streams/latest/dev/key-concepts.html)
A shard is a uniquely identified sequence of data records in a stream. A stream is composed of one or more shards,
each of which provides a fixed unit of capacity.

#### [Kinesis Producer](https://docs.aws.amazon.com/streams/latest/dev/key-concepts.html)
A producer puts records into Amazon Kinesis Data Streams.

#### [Kinesis Consumer](https://docs.aws.amazon.com/streams/latest/dev/key-concepts.html)
A consumer gets records from Amazon Kinesis Data Streams and processes them.

#### [Kinesis Security](https://docs.aws.amazon.com/streams/latest/dev/security.html)
Kinesis supports both in-flight encryption using HTTPS API and at-rest encryption using KMS.

#### [Kinesis Capacity Modes](https://docs.aws.amazon.com/streams/latest/dev/how-do-i-size-a-stream.html)
- **Provisioned Mode:** specify number of shards, increase and decrease the number of shards as needed
- **On-demand Mode:** no capacity planning and automatically scale


### [Amazon Data Firehose](https://docs.aws.amazon.com/firehose/latest/dev/what-is-this-service.html)
Amazon Data Firehose is a fully managed service for delivering real-time streaming data to destinations such as S3, Redshift,
and any custom HTTP endpoint.

#### [Data Firehose Stream](https://docs.aws.amazon.com/firehose/latest/dev/what-is-this-service.html)
A Data Firehose Stream is a data pipeline that defines how your streaming data flows from sources/producers to destinations/consumers.

#### [Data Firehose Record](https://docs.aws.amazon.com/firehose/latest/dev/what-is-this-service.html)
A record is the data of interest that your producer sends to a Firehose stream.

#### [Data Firehose Producers](https://docs.aws.amazon.com/firehose/latest/dev/what-is-this-service.html)
Producers send records to Firehose streams. Alternatively, you can also configure your Firehose stream to automatically
gather data from an existing source such as Kinesis Data Stream.

#### [Data Firehose Destinations](https://docs.aws.amazon.com/firehose/latest/dev/basic-deliver.html)
When you send data to your Firehose stream, it's automatically delivered to your chosen destination.
Destinations can be Services such as S3, Redshift and OpenSearch, or alternatively 3rd party tools und plain HTTP endpoints.

#### [Data Firehose Transformation](https://docs.aws.amazon.com/firehose/latest/dev/data-transformation.html)
Amazon Data Firehose can invoke your Lambda function to transform incoming source data and deliver the transformed data
to destinations.
