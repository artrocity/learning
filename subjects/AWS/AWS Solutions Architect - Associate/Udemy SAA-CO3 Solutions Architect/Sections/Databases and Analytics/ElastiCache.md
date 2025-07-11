AWS ElastiCache

- In-memory database
- Used to cache data from other databases
- Fully managed implementation of Redis and Memcached
- High-performance low latency
- Can be put in front of RDS/DynamoDB
- ElastiCache Nodes run on EC2 instances so you must choose an instance type
- Data is written to RDS and then Loaded to ElastiCache
- If read is given for that
- Use Cases
    
    - Static, frequently accessed data
    - Tolerant of stale data
    - Slow or expensive to get compared to cache retrieval
    - Push-button scalability for memory, write, and read
    - Storing session state data
 
AWS ElastiCache Scaling

- Memcached
    
    - Add nodes to a cluster
    - Scale vertically - change a node type
        
        - Changing the underlying EC2 instance
        - Must create a new node type
    - Each node is a partition of data
    - Its not replicated
- Redis
    
    - Cluster Mode Disabled
        
        - Add replica or change node type
        - Only one shard
        - Across or in one AZ
    - Cluster Mode Enabled
        
        - Online resharding to add or remove shards; vertical scaling to change node type
        - Offline resharding to add or remove shards
        - Shards can be within or across AZs
        - Each Shard contains a Primary nodes and replicas