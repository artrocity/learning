EC2 Cheat Sheet  
[https://digitalcloud.training/amazon-ec2/](https://digitalcloud.training/amazon-ec2/)  
VPC Cheat Sheet  
[https://digitalcloud.training/amazon-vpc/](https://digitalcloud.training/amazon-vpc/)
 
EC2 CRAM

- EC2 - launch virtual server instances on AWS Cloud
- Each virtual server is known as an instance
- EC2 provides full control at the OS Layer
- Key pairs are used to secure connections to EC2 instances
- Storage is either
    
    - EBS - persistent
    - Instance Store - non-persistent
- AMIs provides info required to launch an instance, includes
    
    - Template for the root volume
    - Launch permissions
    - Block device mapping specifying the volumes to attach
    - AMIs are regional - can only launch an AMI from the region in which it's stored
        
        - You can copy AMIs to other regions via CLI
- Instance Meta Data
    
    - Data about your instance
    - 169.254.169.254/latest/meta-data
- User Data
    
    - Used to configure the launch of the instance, scripts, installations, etc.
    - 169.254.169.254/latest/user-data
- EC2 Benefits
    
    - Elastic computing
    - Complete Control
    - Flexible - OS, Hardware, etc
    - Reliable - high levels of availability
    - Secure - Fully integrated with VPC and security features
    - Cost - low cost
- IP Addresses
    
    - Public - lost when an instance is stopped, don’t get charged
    - Private IP - Retained when instance is stopped
    - Elastic IP address - Charged when not being used, Static IP
- Placement Groups
    
    - Cluster - tightly coupled, low latency, HPC
    - Spread - Strictly places on different hardware
    - Partitioned - spread across partitions, do not share underlying hardware, distributed and replicated workloads - Hadop, Cassandra, Kafka
- NAT Instance
    
    - EC2 instance, user managed, can use as bastion host
- NAT Gateway
    
    - Elastic, managed by AWS, Can't Access through SSH
- EC2 Lifecycle
    
    - Stopping EC2 instance
        
        - EBS backed instances only
        - No charge for stopped instances
        - EBS volumes remain attached
        - Data in RAM is lost
        - Instance is migrated to a different host when started
        - Private addreses retained, public addresses released
    - Hibernation
        
        - On-demand / reserved Linux
        - Contents of RAM saved
        - Must be enabled during launch
        - When started
            
            - Root volume and RAM content restored
    - Reboot
        
        - OS Reboot
        - DNS Name and IP address retained
        - Does not affect billing
    - Retire EC2 Instances
        
        - If underlying hardware fails
        - Reaches its scheduled termination
    - Terminated instances
        
        - Deleting the Instance
        - Cannot recover a terminated instance
        - EBS volumes are deleted
    - Recovering EC2 instances
        
        - CloudWatch can be used to monitor system status checks and recover instances
        - Applies if the instance becomes impaired
        - Recovered instance is identical to old instance
    - Nitro
        
        - Updated underlying platform for the next generation of EC2 instances
        - Breaks logical functions into specialized hardware with a Nitro hypervisor
        - Specialized hardware
        - Improves performance, security, and innovation
    - Nitro Enclaves
        
        - Isolated compute environments
        - Integrates with KMS
        - Good for sensitive data
    - EC2 Pricing
        
        - On-Demand
        - Spot - 90% reduction, can be terminated
        - Reserved - 1-3 year commitment, committing to a specific compute / instance type
        - Dedicated Instance - billed per instances
        - Dedicated Host - socket visibility, pay per host
        - Savings Plan - commit to a per hour usage for various compute service, 1-3 years