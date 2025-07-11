**AWS Relational Database Service**

- Managed relational database service
- Runs on EC2 instances or serverless
    
    - If EC2 you must choose the DB instance type.
- Used for online transaction processing
- Create DB Instance
    
    - Instance can contain multiple user-created databases
- Uses AWS EBS for volumes storage
- Backups can be taken using EBS snapshots
- Offers a choice of Database Engines
    
    - Aurora
    - MySQL
    - PostgreSQL
    - Oracle - BYOL
    - Microsoft SQL / SQL Server
    - MariaDB
- Scaling
    
    - RDS Vertical Scaling
        
        - When you need more write performance
        - Scales up via increasing the instance types
        - Database will have to restart for changes to take effect
    - Scaling Out
        
        - Creates read replicas in order to scale out
        - Read replicas can be in same or different AZ
        - Asynchronous replication
    - Multi-AZ
        
        - Synchronous replication
        - Standbys are located in a different AZ
        - Multi-AZ enable automatic disaster recovery
      
    
 
**RDS Backup, Recovery, and Maintenance**

- Backups
    
    - Backups are snapshots from 0-35 days
    - Snapshots do not expire
- Recovery
    
    - When restoring snapshot will create a new database
- Maintenance Windows
    
    - OS and DB patching can require taking the database offline
 
**RDS Security**

- RDSs are ran within a VPC
- Databases can be publicly available
- Security groups are used to permit or block traffic
- For EC2 instances to RDS, APP SG 3306 traffic is required
- Encryption
    
    - RDS encryption AES 256 is for at rest
    - You can only enable encryption at the time of creation, not after
    - AES 256 is strong encryption with minimal performance impact
    - AWS KMS is used for encryption keys
- Exam Tips
    
    - You can't have:
        
        - An encrypted read replica of an unencrypted DB instance
        - An unencrypted read replica of an encrypted DB Instance
        - The same KMS key is used if in the same region as the primary
        - If the read replica is in a different region, the key is different
        - You can't restore an unencrypted backup or snapshot to an encrypted database
    - Restoring to an encrypted database from unencrypted
        
        - You can make a snapshot of an unencrypted, encrypt the snapshot
        - Restore the snapshot to a new instance with a new endpoint
 
**RDS Proxy**

- Fully managed DB proxy
- Highly available
- Increase scalability, fault tolerance, and security for connections to DB
- Can be used to insert before the RDS instance to connect to the proxy which is in a connection pool
    
    - Reduced stress
    - Shares used connections
    - Increased efficiency
    - Control Authentication Methods