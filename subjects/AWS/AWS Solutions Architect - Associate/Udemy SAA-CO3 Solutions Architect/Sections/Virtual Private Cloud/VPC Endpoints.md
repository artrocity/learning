VPC Endpoints

- Normally an instance in a private subnet would need to be routed through an internet gateway and then to a specific AWS service.
- With VPC endpoints, you can stay within your private subnet and reach out and communicate with AWS services
- Types of endpoints
    
    - Interface Endpoint
        
        - This is accomplished via VPC Endpoints creating a Elastic Network Interface in the subnet which has a private IP address and can reach out and touch the desired AWS service.
    - Gateway Endpoint
        
        - A route table entry is required with the prefix list for S3 and the gateway ID
        - Services
            
            - S3
            - DynamoDB
        - VPC Endpoint Policies
- IAM policies can be applied to the VPC endpoint as well as the resource