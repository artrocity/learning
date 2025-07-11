AWS Aurora

- AWS created database in the RDS family
- Valid for MySQL and Postgres
- 5x faster than MySQL and 3x faster than Postgres
- Aurora features a distributed fault-tolerant, self-healing storage system that auto-scales up to 128TB per instance
- Aurora Replicas can be located in different Availability Zones but must be within the same region
- Aurora Replicas
    
    - Replicas can read from the database
    - Primary writes to the database
    - Can use auto-scalers to create read replicas
 
AWS Aurora Fault Tolerance

- Fault tolerance across 3 AZs
- Single logical Volume
- Replicas scale-out read requests
- Primary's write to all 3 replicas
- Replicas are independent endpoints
- Can promote a replica to a primary
- Can use Auto Scaling to add replicas
 
AWS Aurora Serverless

- Use Cases
    
    - Infrequently used apps
    - Multi-tenant applications
    - Variable workloads
    - New applications
    - Development and test databases