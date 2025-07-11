￼Network Technologies

- VPCs
    
    - Think of a VPC as your own private section within AWS Cloud, similar to having an office building within a sky scraper. The sky scraper is amazon and the office building (floor) is your VPC
    - Just as you would divide your office building into different departments with different security levels, you would divide your VPC into subnets
- CIDR
    
    - CIDR (Classless Inter-Domain Routing) blocks are like postal codes for your network
    - When you create a VPC, you assign it a CIDR block - 10.0.0.0/16 - The /16 means the first 16 bits of the address are fixed, leaving you with 16 bits (65k addresses) to work with
- Public Subnets
    
    - Public subnets are like the reception area and public conference room of an office building. Public subnets are public facing and they:
        
        - Have a route to the Internet Gateway
        - Can receive traffic directly from the internet
        - Typically host public-facing resources like web servers
        - Need their route table to have a route to the IGW for internet access
        - Usually contain resources like load balancers, web servers, etc.
- Private Subnets
    
    - Private subnets are similar to secure back offices where secure work happens. They:
        
        - Have no direct route to the internet
        - Can access the internet through a NAT gateway in a public subnet
        - Typically host databases, application servers, and other resources
        - Are more secure because they're not directly accessible from the internet
- Route Tables
    
    - Route Tables are similar to the building's directory and security instructions
    - They determine where network traffic can go
- Bastion Host
    
    - A Bastion Host, or Jump Box is a specially configured EC2 instance that sits in a public subnet and acts as the sole entry point for SSH/RDP access to your private instances
    - To access an instance on a private subnet using a bastion host
        
        - SSH into the bastion host using its public IP address
        - From the bastion host, SSH into the private instance using it's private IP address
        - All traffic is logged and monitored through this single entry point
- Example
    
    - Let's say we're building a web application
    - We configure a VPC with a CIDR of 10.0.0.0/16 - this gives us approximately 65k addresses
    - We configure a Public Subnet - 10.0.1.0/24. This will contain our
        
        - Load balancer
        - Has a route to the IGW
        - Can receive customer traffic
    - We then configure a Private Subnet 10.0.2.0/24
        
        - Contains your application servers and database
        - Routes internet-bound traffic through NAT gateway
        - Protected from direct internet access
- Best Practices
    
    - Always spread subnets across multiple AZs for high availability
    - Use the principle of least privilege - only make public what needs to be public
    - Size your CIDR blocks appropriately for future growth
    - Keep separate route tables for public and private subnets
    - Remember to update both route tables and Network ACLs for new rules