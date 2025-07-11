Projects

- Organizer of resources in Google Cloud
- Associates objects with services and billings
- Contains networks in Google cloud that can be shared/peered
    
    - Up to 5 VPC networks, but can request up to 15
    - Each VPC network is a global resource
    - VPC networks do not have their own IP addresses but are a collection of:
        
        - Individual IP addresses
        - Subnets (IP Range)
        - Routes
        - Firewall rules
        - Regional Resources
    - VPC Explained
        
        - VPC = City Layout
        - Subnets = Different Neighborhoods
        - IP Addresses = Individual House
        - Firewall rules = Traffic Rules and Barriers
    - Do not contain IP address ranges but are simply a construct of all of the individual IP addresses and services within that network
- Every project is provided with a default VPC network with preset subnet and firewall rules
- There are 3 types of VPC networks
    
    - Default
        
        - Every project provided with a default
        - One subnet per region
        - Default firewall Rules
    - Auto Mode
        
        - Default Network
        - One subnet per region
        - Regional IP allocation
        - Fixed /20 subnetwork per region
            
            - Expandable to /16
        - Can be changed to custom mode networks
    - Custom Mode
        
        - No default subnets created
        - Full control of IP ranges
        - Regional IP allocation
        - Expandable to IP ranges the user specifies
        - Can not be reverted back to Auto Mode
- Compute Engine VM Communication
    
    - VMs on the same network can communicate with each other over internal IP addresses even if they're in different regions
    - VMs on different networks must communicate on external IP addresses even if they're in the same region
- Reserved subnet addresses
    
    - 0.0 = Network
    - 0.1 = 0.1 Gateway
    - .254, .255 = Broadcast addresses