Versioning

- Means of keeping multiple variants of an object in the same bucket - similar to git
- Use versioning to preserve retrieve, and restore every version of every object stored in your AWS S3 Bucket
- Versioning-enabled buckets allow you to recover objects from accidental deletion or overwrite
 
S3 Replication

- Must have versioning enabled
- CRR
    
    - Cross-region replication
    - Any data that is uploaded to bucket a, it automatically replicates it to the bucket in the other region
- SRR
    
    - Same-region replication
    - Replicates buckets from one bucket to another within the same region

￼Lifecycle Management

- Two actions
    
    - Transition Actions
        
        - Define when objects transition to another storage class
    - Expiration Actions
        
        - Define when objects expire (deleted by S3)
- Possible Transition
    
    - Standard
    - Standard - IA
    - Intelligent - Tiering
    - One Zone - IA
    - Glacier
    - Glacier Deep Archive