
# AWS DynamoDB – Complete Notes (KK FUNDA Style)

---

## 1. What is DynamoDB?

Amazon DynamoDB

DynamoDB is a **fully managed NoSQL database service** provided by AWS.

### Simple Explanation :

* It is a **key-value + document database**
* No need to manage servers (serverless)
* Automatically scales (no manual DB scaling)

### Real-Time Example:

* Flipkart / Amazon product catalog
* User session storage
* Cart data in eCommerce apps

---

## 2. Key Features

* Fully managed (AWS handles infra)
* Serverless (no EC2 required)
* High availability (multi-AZ)
* Auto scaling
* Low latency (milliseconds response)

---

## 3. DynamoDB vs RDS (Important Interview Question)

| Feature     | DynamoDB      | RDS       |
| ----------- | ------------- | --------- |
| Type        | NoSQL         | SQL       |
| Schema      | Flexible      | Fixed     |
| Scaling     | Auto          | Manual    |
| Joins       | Not supported | Supported |
| Performance | Ultra fast    | Moderate  |

### Teaching Tip:

👉 Use DynamoDB when:

* High traffic apps
* Real-time performance needed

---

## 4. Core Components

### 4.1 Table

* Similar to table in SQL

### 4.2 Item

* Row (data record)

### 4.3 Attribute

* Column (fields)

---

## 5. Primary Key (VERY IMPORTANT)

### Types:

### 1. Partition Key

* Unique identifier

Example:

```
UserID = 101
```

### 2. Composite Key (Partition + Sort Key)

```
UserID (Partition Key)
OrderID (Sort Key)
```

### Real-Time Example:

* One user → multiple orders

---

## 6. Secondary Indexes

### 1. GSI (Global Secondary Index)

* Different partition key
* Query flexibility

### 2. LSI (Local Secondary Index)

* Same partition key
* Different sort key

---

## 7. Capacity Modes

### 1. On-Demand

* Pay per request
* Best for unpredictable traffic

### 2. Provisioned

* Fixed read/write capacity
* Cost optimization

---

## 8. Read/Write Units

### Read Capacity Unit (RCU)

* 1 strongly consistent read/sec

### Write Capacity Unit (WCU)

* 1 write/sec

---

## 9. Consistency Models

### Strongly Consistent

* Always latest data

### Eventually Consistent

* Slight delay
* Faster and cheaper

---

## 10. Creating DynamoDB Table (Step-by-Step)

### Step 1: Login to

AWS Management Console

### Step 2:

Go to → DynamoDB → Create Table

### Step 3:

Enter:

* Table Name: `Users`
* Partition Key: `UserID`

### Step 4:

Choose:

* On-demand (recommended for beginners)

### Step 5:

Click Create

---

## 11. Insert Data (Console Method)

1. Open Table
2. Click → Explore Items
3. Click → Create Item
4. Add JSON:

```
{
  "UserID": "101",
  "Name": "Prasanth",
  "City": "Bangalore"
}
```

---

## 12. Query vs Scan

### Query

* Fast
* Uses primary key

### Scan

* Slow
* Reads entire table

### Interview Tip:

👉 Always prefer Query over Scan

---

## 13. DynamoDB CLI Commands

### Create Table

```
aws dynamodb create-table \
--table-name Users \
--attribute-definitions AttributeName=UserID,AttributeType=S \
--key-schema AttributeName=UserID,KeyType=HASH \
--billing-mode PAY_PER_REQUEST
```

---

### Insert Item

```
aws dynamodb put-item \
--table-name Users \
--item '{"UserID": {"S": "101"}, "Name": {"S": "Prasanth"}}'
```

---

### Get Item

```
aws dynamodb get-item \
--table-name Users \
--key '{"UserID": {"S": "101"}}'
```

---

## 14. DynamoDB Streams

* Capture changes in table
* Used with Lambda

### Example:

* Trigger Lambda when new user added

---

## 15. Backup & Restore

* On-demand backup
* Point-in-time recovery (PITR)

---

## 16. Security

* IAM roles and policies
* Encryption at rest (KMS)
* VPC endpoints

---

## 17. Real-Time Architecture Use Case

### E-commerce Cart System

```
User → Add to Cart → DynamoDB
                 ↓
            Fast retrieval
```

### Why DynamoDB?

* High speed
* Scalable
* No DB admin needed

---

## 18. Advantages

* Serverless
* Highly scalable
* Millisecond latency

---

## 19. Disadvantages

* No joins
* Complex queries difficult
* Cost can increase

---

## 20. Interview Questions (Top)

1. What is DynamoDB?
2. Difference between Query and Scan?
3. What is Partition Key?
4. What is GSI?
5. How scaling works?
6. Strong vs Eventual consistency?

---

## 21. Common Mistakes (Real Project)

* Using Scan instead of Query
* Wrong partition key design
* Not using indexes
* Over provisioning capacity

---

## 22. Best Practices

* Choose good partition key
* Avoid hot partitions
* Use GSI for flexibility
* Monitor with CloudWatch

---

## 23. Monitoring

Use:
Amazon CloudWatch

Metrics:

* Read/Write usage
* Throttling
* Latency

---

## 24. Integration Services

* Lambda
* API Gateway
* S3
* Kinesis

---

## 25. Simple Diagram Explanation (for Students)

```
Client → API → DynamoDB
              ↓
        Fast Storage
```

---

