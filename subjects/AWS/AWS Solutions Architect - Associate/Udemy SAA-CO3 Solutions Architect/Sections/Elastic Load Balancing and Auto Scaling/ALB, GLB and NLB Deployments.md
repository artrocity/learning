Load Balancers

- Application Load Balancer
    
    - Layer 7
    - Operates at the HTTP/HTTPS Protocol Level
    - Can route based on content
        
        - Reads each packet and routes based on the content
    - Ideal for web apps, RESTful APIs, Lambdas
    - Examples
        
        - HTTP/HTPPS
        - Microservices
        - Lambdas
- Network Load Balancer
    
    - Express highway for network traffic
    - Handles raw UDP/TCP
    - Provides static IP addresses
    - High performance
    - Great for gaming servers
    - Can terminate SSL at scale
    - Examples
        
        - TCP/UDP Applications
        - Ultra Low Latency
        - Static IP Addresses￼VPC Endpoints
- Gateway Load Balancer
    
    - Essentially a central security with inspection checkpoint
    - Designed for virtual network appliances
    - Centralizes network traffic inspection
    - Ideal for firewalls, ID
    - Provides single entry/exit point for inspection
    - Examples
        
        - 3rd party virtual network appliances
        - Centralized inspection and monitoring
        - Firewalls