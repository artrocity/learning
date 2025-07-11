Applications

- Applications are made of multiple components
- Components communicate with each other to
    
    - Transmit data
    - Fulfill Requests
    - Keep the application running
   

Monolithic Applications

- Application with tightly coupled components
- With a monolithic approach, if one component fails, multiple components can fail, if not the entire application
   

Microservices

- Applications components are loosely coupled
- If a single component fails, other components continue to work because they are communicating with each other
 
Serverless

- Cant see or access the underlying infrastructure
- All management of the instance is taken care of for the user
 
Subnet

- A subnet is a section of a VPC in which you can group resources based on security or operational needs.
- Subnets can be private or public
    
    - Public Subnet
        
        - Contain resources that need to be accessed by the public
    - Private Subnet
        
        - Contain resources that should only be accessible through your private network, such as databases
 
Packet

- Unit of data sent over the internet or a network
 
AWS Container

- Docker Container
    
    - Widely used platform
    - Uses operating system virtualization to deliver software in containers
- Container is a package for your code
- Containers run on top of EC2 instances
 
AWS Outposts

- AWS Outposts are AWS managed mini data centers installed directly into your data center

￼Network Access Control List (NACL, Network ACL)

- NACL is a virtual firewall that controls inbound and outbound traffic at the subnet level
- NACLs perform stateless packet filtering
    
    - This means they remember nothing and check each packet as it leaves or enters the subnet
 
Security Group

- A security group is a virtual firewall that controls the inbound and outbound traffic for an Amazon EC2 Instance
- Security groups are stateful, meaning they remember who has access to the Instance
 
Block level storage

- Block level storage is a type of data storage that manages data in fixed-size chunks called blocks (Typically 512 bytes or 4kb)
- When a file is updated only the piece that changes is updated within the block
- Common Examples
    
    - Hard Drives and SSDs
    - Cloud block storage - AWS EBS
    - Storage Area Network Volumes
- Key Characteristics
    
    - Raw storage without a file system
    - Direct access to blocks
    - Low-level control
    - High performance for databases and VMs
    - OS sees it as a regular hard drive