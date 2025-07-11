Amazon Virtual Private Cloud

- Foundational network service that lets you create an isolated private network environment in the cloud
- A VPC is a fortress
    
    - The only way to enter the fortress is through an internet gateway
- Inside of the VPC
    
    - Subnets
        
        - The only technical reason to use subnets within a VPC is to control access to the IGW or Internet Gateway
        - Subnets can also control packet
    - Network Access Control List (ACL)
        
        - Checks packets to see if they have the necessary permissions to leave or enter the subnet
        - A Network ACL is essentially a Passport Control Officer
        - Stateless - checks every single packet that comes in or out
    - Security Groups
        
        - EC2 instances come with a default security group that does not allow any traffic into the instance at all
        - Security groups are essentially Doormen at a building, they’ll check a list to see if you're allowed to enter, they do not check identity on the way out
        - A security group is stateful - it has some sort of memory as to who is allowed in or out
- Key components
    
    - Subnets
        
        - Public and Private
    - Route Tables
        
        - Control traffic flow
    - Internet Gateway
        
        - Access to the internet
        - Allows traffic in or out of the VPC
    - GAT Gateway
        
        - Private resources can access the internet
    - Network ACLs and Security groups
- Core Features
    
    - Network Isolation
    - Security Controls
    - Connectivity Options
- Common Uses
    
    - Multi-Tier Web Apps
    - Creating Dev/Test Environments
    - Extending Corporate Networks to Cloud
    - Running regulated/complaint workloads
- Best Practices
    
    - Private subnet for backend resources
    - Implement least privilege
    - Plan IP addressing carefully
    - Use VPC endpoints for AWS Services
    - Flow logs for monitoring
 
A packet traveling from One subnet within a VPC to another subnet located within the same VPC

- EC2 on Subnet A sends the packet to an EC2 on Subnet B
- The security group does not check outbound traffic by default so it's let through.
- The packet approaches the Network Access Control List
    
    - The NACL checks the packet to ensure it has the necessary permissions to leave the subnet
- The packet then arrives at Subnet B and the NACL checks the packet to ensure it has the necessary permissions to access Subnet B
- The packet then arrives at the EC2 on Subnet B and the security group (stateful) remembers that the packet is on the list and allows the packet in.
- By default - all traffic is forbidden from entering an EC2 Instance via the security group