VPC

- Much like physical networks, VPCs have Routing Tables
- VPCs belong to Google Cloud "Projects"
- Routing tables are built in
- No need to provision or manage a router
- Forward traffic from one instance to another
- No external IP address required
- No Firewall required
- VPCs provide a globally distributed firewall
    
    - Can be used to restrict access to instances for both incoming and outgoing traffic
    - Firewall rules can be defined through network tags on compute engine instances
        
        - For instance you can tag all web servers with a network tab of "WEB"
        - Write a firewall rule that allows traffic on ports 80 and 443 to the WEB tag, no matter their IP address