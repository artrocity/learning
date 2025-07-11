AWS Direct Connect

- Dedicated direct private connection to AWS
- AWS Direct Connect Location
    
    - Physical Data Center
    - Contains AWS Server Cage / Rack
    - Contains Customer Server Cage / Rack
    - There is a cross-connect between the AWS DX partner and the customer
    - A DX port must be allocated in a direct connect location
    - The customer router in their data center is connected to the DC location via a router
- Benefits
    
    - Private connectivity between data center and your office
    - Consistent network experience
    - Increased speed and bandwidth
- Cons
    
    - DX Connections are not encrytped
- Gateways
    
    - Direct Connect Gateway
    - Transit Gateway
        
        - Network transit hub that interconnects VPCs and on-premises networks
        - VPCs are connected to the Transit Gateway
        - Corporate Office connects to TGW
        - TGWs can be attached to
            
            - VPNs
            - Direct Connect Gateways
            - 3rd Party Appliances
            - And TGWs in other regions