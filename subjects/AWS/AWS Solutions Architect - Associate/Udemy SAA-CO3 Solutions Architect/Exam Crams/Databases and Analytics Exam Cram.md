Cheat Sheet  
[https://digitalcloud.training/amazon-rds/](https://digitalcloud.training/amazon-rds/)  
[https://digitalcloud.training/amazon-aurora/](https://digitalcloud.training/amazon-aurora/)  
[https://digitalcloud.training/amazon-dynamodb/](https://digitalcloud.training/amazon-dynamodb/)  
[https://digitalcloud.training/amazon-elasticache/](https://digitalcloud.training/amazon-elasticache/)  
[https://digitalcloud.training/amazon-redshift/](https://digitalcloud.training/amazon-redshift/)  
[https://digitalcloud.training/amazon-emr/](https://digitalcloud.training/amazon-emr/)  
[https://digitalcloud.training/amazon-kinesis/](https://digitalcloud.training/amazon-kinesis/)  
[https://digitalcloud.training/amazon-athena/](https://digitalcloud.training/amazon-athena/)  
[https://digitalcloud.training/aws-glue/](https://digitalcloud.training/aws-glue/)
 
Databases & Analytics

- |   |   |
    |---|---|
    |Data Store|Use Cases|
    |Database on EC2|Need full control￼Third party database engine not available on RDS|
    |RDS|Relational Database￼Oracle, PostgreSQL, MariaDB, MySQL, Microsoft SQL Server￼Data is structured|
    |DynamoDB|NoSQL Database￼In-memory performance￼High I/O Needs￼Dynamic Scaling|
    |RedShift|Data warehouse for large volumes of aggregated data|
    |ElastiCache|Fast temporary storage for small amounts of data￼In-memory database|
    |EMR|Analytics workloads using Hadoop Framework|
    
- RDS
    
    - Uses EC2 / Serverless
    - Relational SQL
    - OLTP - Online Transaction Processing
    - Encryption
        
        - Encryption available at rest if enabled during creation
        - KSM is used to managed encryption keys
    - Scaling
        
        - Scales up - increasing performance
        - Scales out - read replicas
    - Snapshots
        
        - Do not expire
        - Backups entire DB instance
        - For single AZ DB instance brief suspension of I/O
        - For multi-AZ SQL Server I/O is suspended on primary
        - Others snapshot is taking from the standby
- Aurora
    
    - AWS database offering in the RDS family
    - 5x faster than MySQL
    - 3x faster than PostgreSQL
    - MySQL / PostgreSQL compatible
    - Serverless, Distributed, fault-tolerant, self-healing storage system
    - Auto-scales to 128 TB per database instance
    - Serverless Use Cases
        
        - Infrequently used applications
        - New Applications
        - Variable Workloads
        - Unpredictable workloads
        - Development and Test DBs
        - Multi-Tenant Applications
- ElastiCache
    
    - Fully Managed implementations of Redis and Memcached
    - Key / Value Store
    - In-memory DB offering high performance and low latency
    - Can be placed in front of databases such as RDS and DynamoDB
    - Nodes run on EC2 instances
    - |   |   |   |   |
        |---|---|---|---|
        |Feature|Memcached|Redis (Cluster Disabled)|Redis (Cluster Enabled)|
        |Data Persistence|No|Yes|Yes|
        |Data Types|Simple|Complex|Complex|
        |Data Partitioning|Yes|No|Yes|
        |Encryption|No|Yes|Yes|
        |High Availability|No|Yes|Yes|
        |Multi-AZ|Yes - place nodes in￼multiple AZs|Yes with auto-failover|Yes, with auto-failover|
        |Scaling|Up - Node type￼Out - Add Nodes|Up - Node type￼Out - Add replicas|Up - Node type￼Out - Add Shards|
        |Multithreaded|Yes|No|No|
        |Backup and Restore|No|Yes, automatic and manual ￼snapshot|Yes, automatic and manual ￼snapshot|
        
    - Use Cases:
        
        - Static frequently accessed data
        - Apps that are tolerant of stale data
        - If data is slow and expensive to get compared to cache retrieval
        - Require push-buttons scalability
        - Store session state data
- DynamoDB
    
    - Fully managed NoSQL database service
    - Key Value document store
    - Serverless
    - Push button scaling
    - Replicated across 3 AZs
    - Two Read modules
        
        - Eventually consistent
        - Strongly consistent
    - Pricing
        
        - On demand capacity
        - Provisioned Capacity
    - TTL
        
        - Define when items in a DB expire so they can be automatically deleted from DB
        - No extra costs
        - Doesn’t use WCU / RCU
    - DynamoDB Streams
        
        - Captures time-ordered sequence of item-level modifications and stores in a 24 hour log
        - Can save the following:
            
            - Keys only
            - New-image - entire item
            - Old image
            - New and old image
    - DynamoDB Accelerator (DAX)
        
        - In-memory cache for DynamoDB
        - Improves performance from milliseconds to microseconds
        - Used to improve read and write performance
        - DAX is updated only if DynamoDB updated successfully
- |   |   |
    |---|---|
    |ElastiCache|DAX|
    |More management overhead|Optimized for DynamoDB|
    |Modify application code to implement|No modification needed|
    |Supports more databases|DynamoDB|
    
- RedShift
    
    - SQL based data warehouse for analytical operations
    - Analyze data using BI tools and SQL
    - Uses EC2 instances
    - Keeps 3 copies of your data
    - Use cases
        
        - Complex queries on structured and semi structured
        - Managed Data warehouse
        - Spectrum for direct access to S3 objects
- EMR
    
    - Managed cluster platform for running big data frameworks like Hadoop and Spark
    - Used for processing data for analytics and business intelligence
    - Preforms ETL functions
- Kinesis Data Streams
    
    - Enables real-time processing of streaming big data
    - Used for rapidly moving data off producers and then processing data
    - Producers send data to Kinesis - Data stored in shard for 24 hours by default to 7 days
    - Streams
        
        - Stream Stores data for later processing by applications
        - Firehose delivers data directly to AWS services
        - Client Library (KCL) helps consume and process data from Data Stream
        - Each shard is processed by one KCL worker
        - One worker can process any number of shards
    - Firehose
        
        - Delivers data directly to AWS services
        - Producers send data to firehose
        - No shards, scaling is elastic
        - Enables near real time analytics with BI Tools
        - 60 seconds latency
        - Destinations
            
            - RedShift
            - ElastiSearch
            - S3
            - Splunk
            - Datadog
            - MongoDB
            - New Relic
            - HTTP endpoint
    - Kinesis Data Analytics
        
        - Real time SQL processing for data stream
        - Analytics for data coming in from Data streams or Firehose
        - Destinations can be data stream, fire hose, or lambda
        - Quickly create and run SQL against streaming services
        - Can ingest data from Streams and Firehose
- Athena
    
    - Queries data in S3 using SQL
    - Data can be in CSV, TSV, JSON, Parquet and ORC formats
    - Uses AWS Glue (Catalog Service) to store information and schemas about the database and tables
    - Optimizing Athena for performance
        
        - Partition Data
        - Bucket your data
        - Use compression
        - Optimize file sizes
        - Optimize columnar data store generation
        - Optimize ORDER BY and GROUP BY
        - Use approximate functions
        - Only include columns you need
- AWS Glue
    
    - Managed ETL service
    - Used for preparing data for analytics
    - Runs ETL jobs on scale-out Apache Spark Environment
    - Discovers and stores metadata in Catalog
    - Works with Data Lakes (S3) data warehouses (RedShift), and data stores (RDS, EC2)