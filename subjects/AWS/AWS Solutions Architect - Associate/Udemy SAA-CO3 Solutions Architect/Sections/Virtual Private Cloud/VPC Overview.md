AWS VPC Overview

- A VPC is a logically isolated portion of the AWS cloud within a region
    
    - You can create multiple VPCs within a region (Up to 5)
    - VPCs are located with a region, they can't span across regions
    - VPC spans across all AZs within a regionvgfcxdzAasdfgg qaawdssddrdssetyghhhujikkolllp-pppppppp
    - CIDR Block
        
        - Classless Interdomain Routing
        - Defines the range of IP addresses that will be available for resources within the VPC
        - Each subnet has a block of IP address from the CIDR block
- Subnet
    
    - Segment of a VPC where you can place groups of isolated resources
    - Within an availability zone, you can create a subnet
    - Subnets are created within an AZ, and can't span across multiple AZs
- NAT
    
    - Network Address Table
    - NAT instance
        
        - Enables Internet access for EC2 instances in private subnets (managed by you)
    - NAT Gateway
        
        - Enables Internet access for EC2 instances in private subnets (managed by AWS)
- Internet Gateway
    
    - Attached to a VPC and used to connect to the internet
        
        - Only 1 per VPC
- VPC Router
    
    - We interact with the VPC by configuring Routing Tables
- Security
    
    - Security Group
        
        - Instance Level Firewall
    - Network ACL
        
        - Subnet level Firewall
- Peering Connection
    
    - Direct Connection between two VPCs
- VPC Endpoints
    
    - Private Connection to public AWS services
- VPN Gateways
    
    - An encrypted tunnel over the internet
    - Virtual Private Gateway
        
        - Amazon VPC side of a VPN connection
    - Customer Gateway Customer side of a VPN Connection
- Direct Connect
    
    - High speed private connection from the customer to AWS