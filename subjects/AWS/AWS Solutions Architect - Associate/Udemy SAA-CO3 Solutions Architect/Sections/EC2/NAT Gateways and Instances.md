Network Address Translation

- Think of a Network Address Translation like a secure mail room in our office building.
- Just like employees can send mail out through the mail room but outsiders can't directly come in directly
- NAT Gateways are always deployed in public subnets
- NAT Instances have the string "amzn-ami-vpc-nat" in the name
    
    - Must disable source/destination checks
- The NAT gateway ID must be specified in the private subnet route table
- Private IP addresses can send internet traffic (Mail) out through the NAT, but can't receive unsolicited inbound connections
- NAT Gateways must be placed in a public subnet as it requires internet access
- Process - When an EC2 instance in a private subnet wants to access the internet (to download updates)
    
    - The instance initiates a request. It wants to access example.com. The EC2 instance has a private IP address of 10.0.2.15. here is what the packet would look like
        
        - Source IP: 10.0.2.15
        - Destination IP: example.com's IP
    - Route Table Consultation - The instance checks it's route table which will have an entry like
        
        - Local Traffic -> Stays in VPC
        - Everything Else -> Goes to NAT Gateway
    - NAT Gateway Processing the packet
        
        - Records connection in it's translation table
        - Replaces the source, private IP, with it's own public IP
        - Forwards the modified packet to the internet
    - Return Traffic Handling
        
        - Traffic comes back to the NAT Gateway's Public IP
        - NAT checks it's translation table
        - Converts destination address back to the private IP
        - Forwards the response back to the originating instance
 
An EC2 instance's network interface doesn't have a public external IP address physically assigned to it via the eth0, eth1, etc. What happens is the Internet Gateway associates a Public IP address to the network interface via a 1:1 NAT
   

|   |   |
|---|---|
|NAT Instance|NAT Gateway|
|Managed by you|Managed by AWS|
|Scale Up|Elastic scaling to 45Gbps|
|No High availability|Provides automatic high availability with an AZ|
|Need to assign a security group (EC2 instance)|No security group needed|
|Can be used as a bastion host|Cannot access through SSH|
|Use an Elastic IP address or a public IP address|Choose Elastic IP address at creation|
|Can implement port forwarding|Does not support port forwarding|