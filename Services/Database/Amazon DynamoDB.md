## [Amazon DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Introduction.html)
Amazon DynamoDB is a serverless, fully managed, distributed NoSQL database. 

### [DynamoDB Tables, Items and Attributes](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html#HowItWorks.CoreComponents.TablesItemsAttributes)
DynamoDB stores data in tables. A table is a collection of items.
Each table contains zero or more items. An item is a group of attributes that is uniquely identifiable among all of the other items.
Each item is composed of one or more attributes. An attribute is a fundamental data element, something that does not need to be broken down any further.

### [DynamoDB Primary Key](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html#HowItWorks.CoreComponents.PrimaryKey)
- **Partition Key:** A simple unique primary key, composed of one attribute known as the partition key
- **Partition Key & Sort Key:** Referred to as a composite primary key, this type of key is composed of two attributes. The first attribute is the partition key, and the second attribute is the sort key

### [DynamoDB Attribute Data Types](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.NamingRulesDataTypes.html#HowItWorks.DataTypes)
- **Scalar Types:** number, string, binary, boolean, null
- **Document Types:** list, maps
- **Set Types:** string set, number set, binary set

### [DynamoDB Read Consistency](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.ReadConsistency.html)
- **Eventually Consistent Read:** default read consistency model, the responses may not reflect the results of a recently completed write
- **Strongly Consistent Read:** responses return the most up-to-date data, reflecting the updates from all prior write operations that were successful

### [DynamoDB Throughput Capacity](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/capacity-mode.html)
- **On-demand:** serverless throughput that automatically scales with demand
- **Provisioned:** fixed throughput specified as reads/writes per second

### [DynamoDB Read/Write Capacity Units (RCU/WCU)](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/provisioned-capacity-mode.html#read-write-capacity-units)
For provisioned mode tables, you specify throughput requirements in terms of capacity units. These units represent the amount of data your application needs to read or write per second.
Capacity Units are rounded up to the nearest whole number.
- A write capacity unit (WCU) represents one write per second for an item up to 1 KB.
- A read capacity unit (RCU) represents one strongly consistent read per second for an item up to 4 KB, or two eventually read operations per second

### [DynamoDB Read/Write Operations](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/read-write-operations.html)
- **PutItem:** creates or replaces an item based on the primary key
- **UpdateItem:** modifies an existing item's attributes
- **GetItem:** read an item based on the primary key
- **Query:** read multiple items that have the same partition key value
- **Scan:** reads all items in a table
- **DeleteItem:** deletes an item based on the primary key
- **DeleteTable:** deletes a whole table and all of its items
- **BatchWriteItem:** put or delete up to 25 items in one or more table, failed write operations get returned as a list of `UnprocessedItems`
- **BatchGetItem:** return up to 100 items from one or more tables, failed read operations get returned as a list of `UnprocessedKeys`

### [DynamoDB Transactions](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/transactions.html)
Amazon DynamoDB transactions simplify the developer experience of making coordinated, all-or-nothing changes to multiple items both within and across tables.
Transactions provide atomicity, consistency, isolation, and durability (ACID) in DynamoDB, helping you to maintain data correctness in your applications.

### [DynamoDB PartiQL](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/ql-reference.html)
Amazon DynamoDB supports PartiQL, a SQL-compatible query language, to select, insert, update, and delete data in Amazon DynamoDB.

### [DynamoDB Conditional Writes](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/WorkingWithItems.html#WorkingWithItems.ConditionalUpdate)
DynamoDB optionally supports conditional writes for write operations like `PutItem`. A conditional write succeeds only if the item attributes meet one or more
expected conditions. Otherwise, it returns an error. Conditional writes check their conditions against the most recently updated version of the item.
Note that if the item did not previously exist or if the most recent successful operation against that item was a delete, then the conditional write
will find no previous item.

### [DynamoDB Condition/Filter Expressions, operators and functions](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Expressions.OperatorsAndFunctions.html)
- =, <>, <, <=, >, >=
- ... BETWEEN ... AND ...
- .. IN (..., ...)
- ... AND ...
- ... OR ...
- NOT ...
- (...)
- attribute_exists (path)
- attribute_not_exists (path)
- attribute_type (path, type)
- begins_with (path, prefix)
- contains (path, operand)
- size (path)

### [DynamoDB Time to Live (TTL)])(https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/TTL.html)
Time To Live (TTL) for DynamoDB is a cost-effective method for deleting items that are no longer relevant. TTL allows you to define a per-item expiration timestamp
that indicates when an item is no longer needed. DynamoDB automatically deletes expired items within a few days of their expiration time, without consuming write throughput. 

### [DynamoDB Secondary Indexes](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/SecondaryIndexes.html)
Amazon DynamoDB provides fast access to items in a table by specifying primary key values. However, many applications might benefit from
having one or more secondary (or alternate) keys available, to allow efficient access to data with attributes other than the primary key.
To address this, you can create one or more secondary indexes on a table and issue Query or Scan requests against these indexes.
A projection is the set of attributes that is copied from a table into a secondary index.
The possible projection can be `KEYS_ONLY`, `INCLUDE` and `ALL` attributes.

#### [DynamoDB Local Secondary Indexes (LSI)](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/LSI.html)
To give your application a choice of sort keys, you can create one or more local secondary indexes on an Amazon DynamoDB table and issue
Query or Scan requests against these indexes. Local secondary indexes on a table are created when the table is created. When you delete a
table, any local secondary indexes on that table are also deleted. The attribute that you choose must be a scalar `String`, `Number`, or `Binary`. 

#### [DynamoDB Global Secondary Indexes (GSI)](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/GSI.html)
Global Secondary Indexes allow for an alternative primary key from the base table. The attribute that you choose must be a scalar `String`, `Number`, or `Binary`. 


### [DynamoDB Accelerator (DAX)](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DAX.html)
DAX is a DynamoDB-compatible caching service that enables you to benefit from fast in-memory performance for demanding applications.
The item cache has a Time to Live (TTL) setting, which is 5 minutes by default. DAX assigns a timestamp to every item that it writes to the item cache.
An item expires if it has remained in the cache for longer than the TTL setting. If you issue a GetItem request on an expired item,
this is considered a cache miss, and DAX sends the GetItem request to DynamoDB. DAX allows up to 11 nodes per cluster including the primary node plus
a maximum of 10 read replicas.

### [DynamoDB Streams](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Streams.html)
DynamoDB Streams captures a time-ordered sequence of item-level modifications in any DynamoDB table and stores this information in a log for up to 24 hours.
The possible stream view types are `KEYS_ONLY`, `NEW_IMAGE`, `OLD_IMAGE`, and `NEW_AND_OLD_IMAGES`.

### [DynamoDB Standard-Infrequent Access](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.TableClasses.html)
The DynamoDB Standard-Infrequent Access (DynamoDB Standard-IA) table class is optimized for tables where storage is the dominant cost.
You can select the most cost-effective table class for your table based on its storage and throughput usage patterns.
The choice of a table class is not permanent.
