Route53 Cheat Sheet  
[https://digitalcloud.training/amazon-route-53/](https://digitalcloud.training/amazon-route-53/)
 
CloudFront Cheat Sheet  
[https://digitalcloud.training/amazon-cloudfront/](https://digitalcloud.training/amazon-cloudfront/)
 
Global Accelerator Cheat Sheet  
[https://digitalcloud.training/aws-global-accelerator/](https://digitalcloud.training/aws-global-accelerator/)
 
Exam Cram

- Route 53
    
    - DNS
    - Domain name registry
    - Health Checking of resources
    - Located alongside edge locations
    - Authoritative DNS server for registered domains and creates a public hosted zone
    - Transfer
        
        - Can transfer domains to Route53 if TLD is support
        - Transfer outside of AWS with AWS support
        - Can transfer to another account
        - Can have a domain name registered in one AWS account and hosted zone in another
    - Hosted Zone
        
        - Collection of records for a domain
        - Two types of zones
            
            - Public Hosted Zone
                
                - Determines how traffic is routed on the internet
            - Private Hosted Zone
                
                - Determines how traffic is routed in the VPC
                - Following must be enabled for PHZ
                    
                    - enableDnsHostname
                    - enableDnsSupport
    - Health Checks
        
        - Checks instances health by connecting to it
        - Endpoints can be a domain name or IP address
    - CNAME Vs Alias Records
        
        - |   |   |
            |---|---|
            |CNAME|Alias|
            |Charges for CNAME Queries|Doesn't charge to AWS resources|
            |Can't be the top record|Can create at top but can't route to CNAME|
            |Can point to any DNS record that is hosted ￼anywhere|Can only point to CloudFront, EBS, ELB, S3￼or to another record in the same hosted zone|
            
    - CloudFront
        
        - Define maximum TTL and Default TTL
        - TTL is defined at the behavioral level
        - Headers are used to control the cache
        - Signed URLs + Cookies
            
            - URLs
                
                - Single Files
                - Signed provide more control over access to content
            - Cookies
                
                - Multiple Objects
        - Lambda@Edge
            
            - Run Node and Python functions to customize content
            - Executes functions closer to the viewer