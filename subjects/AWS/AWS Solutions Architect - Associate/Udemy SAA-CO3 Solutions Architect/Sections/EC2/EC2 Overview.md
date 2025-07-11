Elastic Compute Cloud (EC2)

- A virtualized server hosted on an AWS Host Server
- When you create an EC2 instance, you are getting a portion of a physical server (Called a host) in an AWS data center.
- The AWS Host runs a special software called a hypervisor (Zen/Nitro) that divides the physical server's resources into multiple virtual machines.
- Key EC2 Components
    
    - AMI - Amazon Machine Images.
        
        - Template for your EC2 instance. Contains OS, pre-installed software, configuration settings, etc.
    - Instance Types
        
        - These define the hardware capabilities of your virtual server. They are organized into families
            
            - T-series: General Purpose
            - C-Series: Compute Optimized
            - R-series: Memory Optimized
            - I-series: Storage optimized
            - G-Series - GPU instance
    - Storage Types
        
        - Instance Store: Temporary storage that's physically attached to the host
        - EBS (Elastic Block Store): Persistent storage that can be attached and detached
        - EFS (Elastic File System): Scalable file storage that can be accessed by multiple instances
    - Security - EC2 instances are protected through multiple layers
        
        - Security Groups: Act as virtual firewalls controlling inbound and outbound traffic (Stateful)
        - Key Pairs: Used for secure SSH access to Linux instances
        - Network ACLs: Network-level security for your VPC
        - IAM Roles: Control what AWS services the instance can access
    - Networking: EC2 instances run within a VPC (Virtual Private Cloud), which provide:
        
        - IP Addresses
            
            - |   |   |
                |---|---|
                |Public IP Address|Lost when instance is stopped￼Used in Public Subnets￼No Charge￼Associated with a private IP address on the instance￼Can't be moved between instances|
                |Private IP Address|Retained when instance is stopped￼Used in public and private subnets|
                |Elastic IP Address|Static Public Address￼You are charged if not used￼Associated with a private IP address on the instance￼Can be moved between instances and elastic network adapters|
                
        - Public and Private Subnets
        - Internet connectivity through Internet Gateways
        - Private networking between instances
        - Network isolation and security
    - Pricing Models - EC2 offers several ways to pay for instances
        
        - On-Demand: Pay by the second or hour (depending on host OS) with no commitment
        - Reserved Instances: Lower hourly rate with 1-3 year commitment
        - Spot instances: Bid on unused EC2 capacity for up to 90% discounts
        - Dedicated Hosts: Physical servers dedicated to your use
    - Common Use Cases
        
        - Web Servers
        - Application Servers
        - Development/Test Environments
        - Batch Processing
        - Gaming Servers