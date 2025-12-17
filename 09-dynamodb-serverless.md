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
