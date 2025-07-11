Cloud Load Balancer

- The job of a load balancer is to distribute user traffic across multiple instances of an application
- By Spreading the load, load balancing reduces the risk of applications experiencing performance issues
- Cloud load balancing is a fully distributed, software-defined, managed service for all traffic
- Load balancers don't run in VMs that the user has to manage
- You can put load balancers in front of all traffic
    
    - HTTP
    - HTTPS
    - TCP
    - SSL
    - UDP, etc.
- Google Cloud offers Load balancing solutions that can be classified based on the OSI model layer that they operate
 
Application Load Balancer

- Operate at the application layer
- Designed to handle HTTP and HTTPS traffic
- Ideal for web applications
- Operate as reverse proxies
    
    - Distribute incoming traffic across multiple backend user defined instances  
Network Load Balancers

- Operate at the transport layer
- Handles TCP, UDP, and Other IP protocols
- Can be classified in two subtypes
    
    - Proxy Network Load Balancers
        
        - Reverse Proxy
        - Advanced traffic management
        - Support backends located on prem and cloud environments
    - Passthrough Network Load Balancer
        
        - Do not modify or terminate connections
        - Forward traffic to backend while preserving original source IP address
        - Suited for applications that require direct server return or handle a wide range of IP Protocols