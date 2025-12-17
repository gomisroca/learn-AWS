# Amazon DynamoDB for Serverless Architectures

- Serverless, NoSQL database
- Flexible schema
- JSON or key-value
- Event-driven programming support
- Scales horizontally
- Integrates with other AWS services

## How Amazon DynamoDB Works

- Data is stored in tables, similar to rows in a relational database.
- Each item has attributes, similar to columns in a relational database.
- Each item must have a partition key and can have a sort key. Together they form the primary key.
- The rest of attributes are flexible from one item to another.
- Scaling and partitioning is automated.
- Supports number, string, binary, boolean and null, which can be nested.
- All data is automatically replicated across multiple availability zones.
- Eventual consistency is the default.
- Can specify the amount of request throughput needed.
- Basic item requests:
  - PutItem: insert/overwrite an item based on its primary key.
  - UpdateItem: update an item based on its primary key.
  - DeleteItem: delete an item based on its primary key.
  - GetItem: retrieve an item based on its primary key.
  - BatchWriteItem/BatchGetItem: batch write/read operations.
  - Scan: reads the entire table.
  - Query: can only be used in tables with primary+sort keys. Looks up items based on a query expression.
- With Secondary Indexes, we can direct Query and Scan to attributes that are not the primary key.
- LSI are secondary indexes local to a partition key.
- GSI are secondary indexes that span all partition keys in the base table.

## Operating Amazon DynamoDB

- Should build resilient client behavior:
  - Handle 400/500 errors gracefully.
  - Tune the built-in retry logic.
  - Handle errors in batch operations.
- Auto Scaling is enabled by default.
- Global tables are managed, multi-region tables. Select the regions and done.
- DynamoDB is integrated with IAM to prevent unauthorized access.
- DynamoDB Accelerator (DAX) is a caching service for DynamoDB.
- DynamoDB has on-demand backup and restore.

## Design Considerations

- The Partition Key determines the distribution of data across the partition.
- If we read/write to the same partition, it will become a "hot partition", while the others remain unused.
- Avoid this by choosing the partition key wisely, and distributing read/write load across partitions.
- Ideally, items should be small.
- Seconday indexes should be used sparingly and thoughtfully.
- Optimistic locking with a version number is a good way to avoid conflicts.
- One-to-many Tables instead of large number of attributes.
- Store frequently accessed small attributes in a separate table.
