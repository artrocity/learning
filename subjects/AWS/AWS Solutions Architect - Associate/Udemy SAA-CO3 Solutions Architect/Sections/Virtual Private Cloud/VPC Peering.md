AWS VPC Peering

- Allows the connection of 2 or more VPCs
- Enables private routing for IPv4 or IPv6
- CIDR blocks can't overlap
- VPCs can be in different accounts and regions
- VPC to VPC connection will communicate via private IP addreses
- Transitive peering doesn't work
    
    - If there are 4 VPCs in order to communicate with resources on all 4 VPCs, each VPC will need a direct VPC peering connection to the other one