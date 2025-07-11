AWS Database Migration Service(DMS)

- What is it:
    
    - AWS DMS is a cloud service that makes it easy to migrate relational databases, data warehouses, NoSQL databases, and other types of data stores to AWS. It supports homogeneous migrations such as Oracle to Oracle as well as heterogeneous migrations between different platforms such as Oracle to Amazon Aurora.
- How it works
    
    - Replication instance setup
        
        - Create a replication instance on AWS that performs the migration tasks.
    - Source and Target configurations
        
        - Define the source database and target database endpoints, providing connection details and credentials
    - Migration Tasks
        
        - Create migration tasks that specify what tables and data to migrate, mapping rules, and transformation settings
    - Data Transfer Modes
        
        - Full Load: One-time migration of all data
        - Change Data Capture (CDC) Replicates ongoing changes after the initial load
        - Full Load and CDC: Combines both for zero downtime
    - Schema Conversions
        
        - For heterogenous migrations, AWS DMS can work with AWS Schema Conversion tool to convert database schema objects
    - Monitoring
        
        - Track the progress through the console
- Examples - Retail company wants to migrate their on-prem Oracle DB to Amazon Aurora PostgreSQL
    
    - Create a replication instance in their target VPC
    - Configure the source Oracle Database and target Aurora endpoints
    - Uses AWS SCT Schema Conversion tool to convert the schema
    - Sets up a full load and CDC task to maintain data consistency
    - Achieves migration with less than 10 minutes of application downtime