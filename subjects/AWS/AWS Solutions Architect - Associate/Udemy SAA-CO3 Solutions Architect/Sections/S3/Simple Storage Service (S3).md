**AWS Simple Storage Service**

- AWS's object based service system
- Has a bucket, which is a container for objects
- An object is a file you upload
    
    - PDF, Word, MP4, JPG
    - Object consists of
        
        - Key
        - Version ID
        - Value (Data)
        - Metadata
        - Sub-resources
        - Access control information
- Object Storage
    
    - Data is stored in buckets
    - Flat namespace (No hierarchy)
    - Hierarchy can be mimicked with Prefixes
    - Accessed via REST API and can't be mounted
- You can store millions of objects in a bucket
- Accessing items in a bucket
    
    - S3 bucket endpoint URL
    - [https://bucket.s3.aws-region.amazonaws.com/key](https://bucket.s3.aws-region.amazonaws.com/key)
    - This is a rest API using the HTTP protocol
- Naming Convention
    
    - Bucket has to be unique across AWS
 
**AWS S3 Storage Classes**

- Durability
    
    - Protection against data loss and corruption
    - S3 Offers 11 9s of durability (99.999999999%)
- Availability
    
    - Measurement in time of when the data is accessible
    - Expressed as a percent of time per year
        
        - 99.99%
- S3 Standard
- S3 Standard-IA
- S3 Intelligent Tiering
- S3 One-Zone IA
- S3 Glacier Instant Retrieval
- S3 Glacier Flexible Retrieval
- S3 Glacier Deep Archivef