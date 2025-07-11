Cheat Sheet:

- VPC
    
    - [https://digitalcloud.training/amazon-vpc/](https://digitalcloud.training/amazon-vpc/)
- Direct Connect
    
    - [https://digitalcloud.training/aws-direct-connect/](https://digitalcloud.training/aws-direct-connect/)￼

Exam Cram

- VPC
    
    - Logically isolated segment of AWS for your network
    - Region Wide, 5 per region
    - VPCs spans all of the AZs in the region
    - A default VPC is created with a subnet in each AZ
    - Subnets
        
        - Private
        - Public
            
            - Auto assign public IPv4 must be to yes
            - Subnet route table will have an attached IGW
    - Logs
        
        - VPC Flow logs capture information about the IP traffic going to and from network interfaces
        - Flow Log data is stored using AWS CloudWatch Logs or S3
    - CIDR Block
        
        - Range of IPv4 addresses that you select
        - /16 - /28
        - VPC's CIRD Blocks can't overlap
        - Can't increase or decrease size of existing CIDR block
        - 5 IP Addresses (First four and last) are reserved for AWS use
    - Components of a VPC
        
        - Subnet
            
            - Segments of a VPC used to group resources
        - IGW
            
            - Public Connection to the internet
        - NAT Gateway
            
            - Highly Available Managed Network Address Translation service for your resources in a private cloud to access the internet
        - Router - Interconnects subnets and direct traffic between IGWs, VGW, NAT gateways, and subnets
        - Peering Connection
            
            - Enables you to connect two or more VPCs together
        - Endpoints
            
            - Allow private IP addresses to connect to AWS services without leaving the subnet
        - Virtual Private Gateway
            
            - AWS side of the VPN connection
        - Customer Gateway
            
            - Client side of the VPN connection
    - Virtual Firewalls
        
        - |   |   |
            |---|---|
            |Security Group|Network ACL|
            |Allow Rules Only|Allow and Deny Rules|
            |Stateful|Stateless|
            |Evaluates all rules|Processes Rules in order|
            |Applies to an instance only if associated ￼with a security group|Automatically applies to all instances￼in the subnet|
            
    - Methods of connecting to a VPC
        
        - |   |   |   |   |   |   |
            |---|---|---|---|---|---|
            |Method of Connection|What|When|Pros|Cons|How|
            |AWS Managed VPN|AWS Managed IPSec over your current internet connection|Secure tunneled connection to a VPC|Supports Static Routes or BGP peering|Depends on your internet connection|Create a Virtual Private Gateway on AWS, Customer Gateway on the on-premises side|
            |Direct Connect (DX)|Dedicated network connection|Requires a large network link to AWS|Predictable network performance|Timely and Costly, Requires additional telecom and hosting provider|Work with existing data provider, Create Virtual Interfaces|
            |DX + VPN|IPSec VPN connection over DX|Need added security of encrypted tunnels|More secure|More Complex|Work with existing data provider|
            |VPN CloudHub|Connect locations in a hub and spoke manner|Link remote offices for backup or primary access to AWS|Reuses existing internet connections|Depends on your internet connection|Assign multiple customer gateways to a Virtual Private Gateway|
            |Software VPN|You provide your own VPN endpoint and software|Must manage both ends of the VPN connection|Ultimate flexibility|You must design it|Install VPN software on an EC2 instance|
            |Transit VPC|Common strategy for geographically dispersed VPCs|Locations and VPC-deployed assets across multiple regions need to talk with each other|Ultimate flexibility|You must design|Providers like Cisco, Juniper, Riverbed have offerings|
            |VPC Peering|AWS provided VPC connectivity|Multiple VPCs needed to communicate with each other|Uses AWS backbone|Transitive peering not supported|VPC peering request made, accepter accepts request|