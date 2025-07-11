Notes

- Database Types
    
    - Relational
        
        - Organized by tables rows and columns
        - Rigid Schema
        - Rules enforced within the database
        - Typically scaled vertically
        - Supports complex queries and joins
        - RDS, Oracle, MySQL, PostgreSQL
    - Non-Relational
        
        - Varied data storage models
        - Flexible schema (NoSQL)
        - Rules can be defined in application code
        - Scales horizontally
        - Unstructured, simple language
        - DynamoDB, MongoDB, Redis, Neo4j
    - Graph Databases
        
        - Nodes to represent entities
        - Edges to represent relationships
        - Amazon Neptune
- Database Optimization
    
    - Operational
        
        - Online transactions
        - Receive data from applications
        - Production DB that process transactions
        - Shot transactions, simple queries
    - Analytical
        
        - Online Analytics Processing
        - Data warehouse - used for analytics
        - Long transactions, complex queries
        - BigQuery, RedShift, Teradata
- Use Cases
- |   |   |
    |---|---|
    |Data Store|Use Case|
    |Database on EC2|Need full control over instance and database￼Third-party database engine|
    |RDS|Need relational database  <br>Want it to be "serverless" or management conducted for you|
    |DynamoDB|NoSQL￼In-memory performance￼High I/O needs￼Dynamic scaling|
    |RedShift|Data warehouse for large volumes of aggregated data|
    |ElastiCache|Fast temporary storage for small amounts of data￼In-memory database|