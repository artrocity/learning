EC2 Auto Scaling

- Automatically launch and terminates instances
- Maintain the availability and scale capacity
- Works with EC2, ECS, and EKS
- Integrates with:
    
    - CloudWatch - monitoring and scaling
    - ELB - distributing connections
    - EC2 Spot instances - Cost optimization
    - VPC - deploying instances across AZs
- Types of Scaling
    
    - Automatic
        
        - Integrates with CloudWatch.
        - EC2 instances send their utilization metrics to cloud watch
        - Once Metric reports are > 80%, it can launch new instances/nodes
        - Can replace failed nodes
    - Scaling is out
    - Provides elasticity and scalability
    - Can scale on demand or a schedule
- Launch Template
    
    - Used to be Launch Configurations
    - Specifies the EC2 Instance Configuration
    - Contains
        
        - AMI and Instance Type
        - EBS Volumes
        - Security Groups
        - Key Pair
        - IAM instance profile
        - User Data
        - Shutdown Behavior
        - Termination Protection
        - Capacity Reservation
        - Tenancy
        - Purchasing Options
            
            - When it scales, spot or on-demand instances
- Health Checks
    
    - EC2 - status checks
    - ELB - Uses ELB Health Checks in addition to EC2 status checks