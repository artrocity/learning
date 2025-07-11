AWS Elastic File System

- Managed File System
- Regional service
    
    - Stores data in and across multiple AZs (Availability zones)
- AWS takes care of the scalability, backups, etc
- Multiple instances can access the data in EFS at the same time
- Scales up and down as needed with zero user interaction
- How does EFS differ from EBS Elastic Block Storage
    
    - EFS can have multiple instances reading and writing simultaneously
    - Linux file system
    - Regional Resource
        
        - Any EC2 in the region can write to the EFS
    - Automatically scales in size
- Ideal when a large number of resources need to access the same data at the same time