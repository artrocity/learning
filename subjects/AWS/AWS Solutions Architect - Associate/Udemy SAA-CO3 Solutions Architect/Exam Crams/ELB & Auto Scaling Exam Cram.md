Cheat Sheet: [https://digitalcloud.training/auto-scaling-and-elastic-load-balancing/](https://digitalcloud.training/auto-scaling-and-elastic-load-balancing/)
 
Auto Scaling

- Auto Scaling launches and terminates instances dynamically
- Scaling is horizontal
- Provides elasticity and scalability
- Responds to EC2 status checks and CloudWatch Metrics
- Can Scale based on demand or a schedule
- Scaling policies define how to respond to changes in demand
- Auto scaling groups define collections of EC2 instances that are scaled and managed together
- Health Checks
    
    - EC2 - EC2 Health Checks
    - ELB - ELB Health checks and EC2
    - Grace Period
        
        - How long to wait before checking the health status again
        - Auto scaling does not act on health checks until grace period expires
- Monitoring
    
    - Group metrics (ASG)
        
        - Data Points about scaling group
        - 1 minute granularity
        - No charge, must be enabled
    - Basic Monitoring (Instances)
        
        - 5 minute granularity
        - No Charge
    - Detailed Monitoring (Instances)
        
        - 1 minute granularity
        - Charges Apply
- Cooldowns - Used with simple scaling - default 300 seconds
- Termination Policy - controls which EC2 to eliminate first
- Termination Protection - Prevents Auto Scaling from terminating protected instances
- Standby State - used to put an instance in the InService state into the Standby state, update, or troubleshoot the instance
- Lifecycle Hooks - used to perform custom actions by pausing instances as the ASG launches them
    
    - Use Case:
        
        - Run scripts to download and install software
        - Pause Instance to update

￼Elastic Load Balancer

- Distribute incoming application traffic across multiple targets including:
    
    - EC2 Instances
    - Containers
    - IP addresses
    - Lambda Functions
- Provides fault tolerance
- Distributes incoming traffic in a single or multi-AZ environment
- Only 1 subnet per AZ can be enabled for each ELB
- Ensure at least a /27 subnet and make sure there are at least 8 IP addresses available for the ELB to scale
- Can be internet or internal facing
    
    - Internet
        
        - ELB nodes have public Ips
        - Routes traffic to the private IP addresses of the EC2 instances
        - Need one public subnet in each AZ where the ELB is defined
    - Internal only ELB
        
        - ELBs have private Ips
        - Routes traffic to the private IP address of the EC2 instance
 
USE CASES

- Application Load Balancer
    
    - Web Applications, Layer 7 (HTTP/HTTPS)
    - Microservices
    - Lambda Targets
- Network Load Balancer
    
    - TCP / UDP
    - Ultra-low latency
    - Static IP addresses
    - VPC Endpoint services
- Gateway Load Balancer
    
    - Layer 3
    - Listens for all IP packets across all ports
    - Use with virtual appliances such as
        
        - Firewalls
        - Intrusion Detection System
        - Intrusion Prevention System
        - Deep Packet inspection