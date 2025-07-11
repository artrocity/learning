DNS

- DNS
    
    - DNS Zone
        
        - Contains Records
        - A Record
            
            - Maps domain name to IP Address
        - CNAME
            
            - Maps domain name to another domain name
        - MX
            
            - Returns mails servers for a domain
        - TXT
            
            - Associates Text with a domain name
        - SRV
            
            - Maps a domain name to a protocol
        - NS
            
            - Specifies the authoritative DNS servers for a domain
        - SOA
            
            - Start of Authority record stores important info about the domain
    - Zone File
        
        - Contains IP addresses for web servers
    - If a DNS doesn't have the IP address it will recursively forward the request untl it is found
    - FQDN
        
        - [www.example.com](http://www.example.com).
        - Com
            
            - top level domain
        - Subdomain
            
            - Sub division of the domain name for organizing services
            - example
        - Hostname
            
            - www
 
Route53

- Features
    
    - Domain Registration
        
        - .net, .com, .org
    - Hosted Zone
        
        - Represents a set of records belonging to a domain
        - Example.com
    - Health Checks
        
        - Can preform health checks against EC2 instances and resources
    - Traffic Flow