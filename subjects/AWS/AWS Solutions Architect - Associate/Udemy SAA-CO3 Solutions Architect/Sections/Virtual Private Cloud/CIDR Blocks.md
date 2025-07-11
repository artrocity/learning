CIDR Blocks

- A method for allocating IP addresses and routing traffic
    
    - Similar to organizing a large office building into different sections and rooms
- A CIDR block is written with two parts
    
    - IP Address
        
        - Consists of 32 bits
        - Each number can range from 0-255
    - A suffix number after a forward slash
    - Example
        
        - 192.168.1.0/24
- The suffix tells us how many bits are fixed in the network portion of the address
    
    - /24 - means the first 24 bits are fixed
        
        - This will leave us with 8 bits for host addresses
        - This will leave us with 256 possible addresses
        - The range would be 192.168.1.0 - 192.168.1.255
- CIDR Blocks are responsible for organizing and separating different parts of your networks
- Example
    
    - Large CIDR block for your entire network
    - Smaller blocks for different departments
    - Even smaller blocks for services
- Rules
    
    - CIDR Blocks must be between /16 and /28
    - CIDR block must not overlap with any other CIDR block associated with your VPC
    - Can't increase or decrease the size of an existing CIDR block
    - AWS reserves 5 IP addresses of each subnet for it's own use
        
        - The first 4 and last IP address are not available for use