Cloud Storage

- Object based storage service
    
    - Objects can be moved from bucket to bucket
    - Objects are immutable
- Buckets
    
    - Buckets store objects
    - Buckets can not be nested
    - Naming conventions
- Best used for:
    
    - Website content
    - Images, media, and backups
    - Storing data for archiving and disaster recovery
    - Distributing large data objects to users via direct download
    - Files in a file system
    - Collection of buckets that you place objects into
    - 4 storage classes
        
        - Standard
            
            - Data that is frequently used
        - Nearline
            
            - Storage that is low-cost, highly durable
            - Used for storing infrequently accessed data such as
                
                - Data backups
                - Data archiving, etc.
            - Best for 30 day minimum storage before accessing
        - Coldline
            
            - Very low cost
            - Best for 90 day minimum storage before accessing
        - Archive
            
            - Lowest-cost for data storage
            - Used for archiving
            - 365 day minimum for accessing data
    - Each storage type has 3 location types
        
        - Multi-region
            
            - 2 or more geographical places in a large area such as the U.S
        - Dual Region
            
            - Specific pair of regions such as Finland and the Netherlands
        - Region
            
            - Specific geographic place, such as London
- Key features
    
    - Scalable to exabytes
    - Time to first byte in milliseconds
    - Very high availability across all storage classes
    - Single API across storage classes
 
Access Control

- IAM can be used to control which individual user or service account can see the buckets, list, or modify the bucket
    
    - IAM is sufficient in most cases
    - Roles are inherited from project to bucket to object
- Access Control methods - These can be used together
    
    - IAM
    - Access Control Lists
        
        - If finer-tuned control is needed, Access Control Lists are available
        - 100 maximum per bucket
        - Contain
            
            - Scope
                
                - Who this applies to
            - Permission
                
                - Owner, Writer, Reader, etc.
    - Signed URLS
        
        - Provide a cryptographic key that gives time-limited access
        - "Valet Key"
            
            - Ticket issued
            - Timed limited
            - Operations limited to ticket parameters (Get, Put, Delete, Post)
    - Signed Policy Document
        
        - Further refines the control by determining what kind of file can be uploaded by someone with a signed URL
 
Cloud Storage Features

- Customer-supplied encryption key
    
    - Use your own key instead of google managed keys
- Object lifecycle management (OLMP)
    
    - Automatically delete or archive objects
    - Changes to OLMP takes 24 hours to apply
    - Object inspection occurs asynchronously in batches
    - Ability to assign an Object Lifecycle Management policy configuration to a bucket
    - Examples
        
        - Downgrade storage class for objects older than a year
        - Delete objects within a specified data range
        - Keep only the 3 most recent versions of an object
    - Ob
- Object versioning
    
    - Maintain multiple versions of objects
    - Maintain a history of modifications of objects
    - List archived versions of an object
    - Restore an object to an older state
    - Delete a version
- Directory synchronization
    
    - Sync a VM directory with a bucket
- Object change notifications
- Autoclass
- Objects are immutable
- Object Retention Lock
    
    - Retention config governs how long the object must be kept
    - Assists with regulatory compliance
- Data import services
    
    - Transfer Appliance
        
        - Rack, capture, and then ship data to Google Cloud data center
    - Storage Transfer Service
        
        - Import data online
    - Offline Media Import
        
        - 3rd party provider uploads data from a physical media device
- Soft Delete
    
    - Provides default bucket-level protection from
        
        - Accidental Deletion
        - Malicious Deletion
    - Retains overwritten or changed data
    - Enabled by default with a 7 day retention duration
 
Choosing a storage class￼

![Choosing a storage class Structured or unstructured data? unstructured structured Consider a structured database service Read < 1 per year? Yes Consider Archive Storage Read 1 per 90 days ? Yes Consider Coldline Storage Read 1 per 30 days ? Yes Consider Nearline Storage No Standard Storage Choose location and type by balancing latency, availability, and bandwidth costs for data consumers GOO* C ](Exported%20image%2020250301230911-0.png)