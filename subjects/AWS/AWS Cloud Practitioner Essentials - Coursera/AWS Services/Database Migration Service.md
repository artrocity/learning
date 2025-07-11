AWS Database Migration Service

- Helps customers migrate existing databases onto AWS in a secure manner
- During the migration the source database remains reliable and usable
- Downtime is minimized
- Source and target database don’t have to be of the same type
 
Homogeneous Data Migration

- 2 databases of the same type…MySQL to MySQL etc
 
Heterogenous Data Migration

- 2 Databases of differing types
- 2 step process
    
    - Convert Schemas using AWS Schema Conversion Tool
        
        - This converts the source schema and code to that of the target database
    - Use DMS to migrate data from the source database to the destination database