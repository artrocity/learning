Cheat sheet:  
[https://digitalcloud.training/amazon-ebs/](https://digitalcloud.training/amazon-ebs/)  
[https://digitalcloud.training/amazon-efs/](https://digitalcloud.training/amazon-efs/)
 
Exam Cram:

- AWS EBS
    
    - EBS volume data persists independently of an EC2 instance
    - Doesn't need to be physically attached to instances
    - Multiple EBS volumes can be attached to an instance
    - You can use multi-attach to attach a volume to multiple instances but with constraints
    - EBS volumes must be in the same AZ as the instances they are attached to
    - Root EBS volumes are deleted on termination by default
    - Extra non-boot volumes are not deleted by default
    - Snapshots
        
        - Capture a point in time state of an instance
        - Cost effective and easy to backup
        - Can be used to migrate a system to a new AZ or region
        - Can be used to convert an unencrypted volume to an encrypted volume
        - Stored on S3
        - Volumes are AZ specific, Snapshots are region specific
    - RAID with EBS
        
        - Redundant Array of Independent Tasks
        - AWS doesn’t provide
        - RAID 0 and 1 are optional on EBS
            
            - 0 - Striping data across disks
            - 1 - mirroring data across disks
        - RAID 5 + 6 are not recommended
    - Encryption with EBS
        
        - Can encrypt both boot and data volumes
        - Following is encrypted
            
            - Data at rest
            - Data moving between volume and instance
            - Snapshots and volumes created from snapshots
        - Encryption is supported by all EBS types
        - All instance families support encryption
- AWS Data Lifecycle Manager
    
    - DLM automates the creation, retention, and deletion of EBS snapshots and EBS-backed AMI
    - Helps with
        
        - Protect data by enforcing backup schedules
        - Create standardize AMIs
        - Retain backups as required for auditing or compliance
        - Reduce storage costs by deleting outdated backups
        - Create disaster recovery backup policies that backup data to isolated accounts
- Instance Store
    
    - High-performance, local disks that are physically attached to the host
    - Ephemeral, data is lost when powered-off
    - Ideal for temporary storage, buffers, caches, etc.
    - Created from AMI templates stored on S3
    - Can't be detached/reattached
- AMI
    
    - Amazon Machine Images
    - Provide information required to launch image
    - Includes
        
        - 1+ snapshots
        - Template for root volume of instance
        - Launch permissions that control which AWS accounts can use AMI
        - Block device mapping that specifies volumes to attach when launched
    - 3 categories
        
        - Community - Free images
        - AWS Marketplace - Paid images and includes software
        - My AMIs - Self created AMIs
- EFS
    
    - Elastic File System
    - Fully managed file system
    - Elastic storage capacity - pay for what you use
    - Multi-AZ meta data and data storage
    - Can configure mount-points in one or more AZs
    - Can be mounted on on-premises systems if using direct connect or VPN, if not use AWS data sync
    - EFS is elastic and grows and shrinks as you add and remove data
    - EFS Access Control
        
        - Can scale up to petabytes
        - Data is stored across multiple AZ's within a region
        - IAM can control EFS
        - POSIX Permissions allow you to restrict access from hosts by user and group
        - EFS Security Groups acts as a firewall
    - EFS Encryption
        
        - Must be enabled at file system creation time
        - Uses TLS
        - Keys are managed by AWS KMS
        - Can encrypt in transit and at rest
- DataSync
    
    - Used to transfer data into EFS
    - Securely copy files over the internet
    - Copies all data regarding the file
- AWS FSx
    
    - 3rd party file system
    - FSx Windows File Server
        
        - Full support for SMB, NTFS, and AD
        - Supports ACLs, shadow copies
        - Replicates data within an AZ
        - Multi AZ support
    - FSx for Lustre
        
        - Native S3 support
        - Fast file system optimized for:
            
            - Machine Learning
            - High performance computing
            - Video processing
            - Financial Modeling
            - Electronic Design Automation
- Storage Gateway - File Gateway
    
    - Provides a virtual on-premises file server
    - Store and retrieve files as S3 Objects
    - Use with on-premises applications
    - Offers SMB or NFS
- Storage Gateway - Volume Gateway
    
    - Block Storage- iSCI protocol
    - Supports block-based volumes
    - Stored Volume Node
        
        - Entire dataset is stored on-site
    - Cached Volume Node
        
        - Entire dataset is stored on S3 and a cache on site
- Storage Gateway - Tape Gateway
    
    - Used for backups
    - Up to 1500 tapes for 1 PB
    - Encrypted using SSL
    - Stored data is S3 managed SSE-E3