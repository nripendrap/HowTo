DynamoDB

What is DynamoDb?
DynamoDB is a low latency NoSQL database.

Data Models
Supports both document and key-value data models. Supported document formats are JSON, HTML, and XML.

Consistency Models
- Eventually consistent
- Strongly consistent
- DynamoDB transactions - ACID

DynamoDB Features
Consists of tables, items, and attributes

2 Types of Primary Key
- Partition key
- Composite key (partition key + sort key)


DynamoDB Access Control
Fine-Grained Access control with IAM
IAM condition parameter dynamodb:LeadingKeys allows users to access only the items where the partition key value matches their User_ID

Secondary Indexes
Enable fast queries on specific data columns.
Give you a different view of your data on alternative partition / sort keys.
It is important to understand the differences.

Local Secondary Index
Same partition key and different sort key to your table.
Must be created when you create your table.

Global Secondary Index
Different partition key and different sort key to your table.
Can be created any time.