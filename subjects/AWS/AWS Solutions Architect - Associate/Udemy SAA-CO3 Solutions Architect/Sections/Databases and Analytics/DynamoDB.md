AWS DynamoDB

- Fully managed NoSQL Database
- Key/value store and Document store
- Serverless
- Push button scaling
- DynamoDB is made up of
    
    - Tables
    - Items
        
        - Items are rows in a table
    - Attributes
        
        - Individual pieces of data within an item ( a cell of data)
        - Attributes Types
            
            - Scalar Types: String, Numbers, Boolean, Null
            - Complex Types: List, Map
            - Set Types: String Set, Number Set, Binary Set
- TTL - Time to Live
    
    - Lets you define when items in a table expire so that they can automatically be deleted from the database
    - No Extra costs
    - Doesn't use WCU / RCU
    - Helps reduce overall storage size
- Composite Key
    
    - When you have a partition key and a sort key
- Features
    
    - Serverless
    - Highly Available
    - NoSQL Name/Value Structure
    - Horizontal Scaling
    - DynamoDB Streams
    - DynamoDB Accelerator
    - Transaction Options
    - Backups
    - Global Tables
 
DynamoDB Streams

- Running record of changes
- When enabled, DynamoDB keeps track of every modification to your data
- Each changes creates a stream record
- Stream records record:
    
    - Key attributes of the modified item
    - New version - after change
    - Old version - before change
    - Both the old and new versions
 
DynamoDB Accelerator (DAX)

- Used to improve performance of tables
- Managed, highly available, in-memory cache
- Reduces latency from milliseconds to microseconds
- Read-through and write-through requests
- No modification of existing logic - can be added to existing API Calls