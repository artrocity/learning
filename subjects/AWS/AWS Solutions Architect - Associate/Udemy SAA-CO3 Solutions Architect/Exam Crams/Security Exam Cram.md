Cheat Sheets:  
[https://digitalcloud.training/aws-iam/](https://digitalcloud.training/aws-iam/)  
[https://digitalcloud.training/amazon-cognito/](https://digitalcloud.training/amazon-cognito/)  
[https://digitalcloud.training/aws-directory-services/](https://digitalcloud.training/aws-directory-services/)  
[https://digitalcloud.training/aws-kms/](https://digitalcloud.training/aws-kms/)  
[https://digitalcloud.training/aws-cloudhsm/](https://digitalcloud.training/aws-cloudhsm/)  
[https://digitalcloud.training/aws-waf-shield/](https://digitalcloud.training/aws-waf-shield/)
 
Security

- Managed Microsoft AD
    
    - Fully managed AWS Service
    - Best choice more than 500 users
    - Can perform schema extensions
    - Can setup trust relationships
        
        - On prem users and groups can access resources in either domain using SSO
        - Requires VPN or Direct Connection
    - Can be used as a standalone AD in the AWS cloud
- AD Connector
    
    - Redirects directory requests to your on-prem active directory
    - Best choice when you want to use an existing Active directory with AWS services
    - AD Connector has 2 sizes
        
        - Small - Organizations up to 500 users
        - Large - Organizations up to 5000 users
    - Join EC2 instances to your on-premises AD through AD connector
- Simple AD
    
    - Inexpensive AD service
    - Standalone, fully-managed AWS service
    - Good for less than 500 users
- Identity Providers and Federation
    
    - IdP you can managed user identities outside of AWS and give these identities permissions to use AWS resources in your account
    - With IAM identity provider there's no need to create custom sign-in code or manage your own user's identities
    - External users sign in through a well-known IdP such as Amazon, Google, Facebook, Apple
    - IAM supports IdPs that are compatible with OpenID Connect or SAML 2.0
- IAM Identity Center
    
    - Previously AWS SSO
    - Centrally manage access to multipole AWS accounts and business apps
    - Easily manage SSO access
    - Includes built-in integrations to many business apps
    - Create and manage user identities in the IAM identity center
    - Connect to existing ADs or Azure
- Cognito
    
    - Add user sign up or sign in access control to web and mobile apps
    - User Pool is a directory for managing sign in and sign up
    - Users can be stored in a user pool
    - Supports SAML and OIDC IdPs
    - Cognito acts as an Identity broker between the IdP and AWS
    - Identity pools are used to obtain temp credentials for AWS services using STS
    - IAM Role is assumed, providing access to the AWS services
- KSM
    
    - Fully managed service for creating and managing cryptographic keys
    - Can control key usage across AWS services in applications
    - KMS allows you to centrally manage and store your keys
    - Supports symmetric and asymmetric encryption
    - KMS keys are the primary resource in AWS KMS
    - KMS keys are created in AWS KMS and contain the key material used to encrypt and decrypt data
    - Only encrypt up to 4kb in size
    - KMS keys can generate data encryption keys
    - Data encryption keys can be used for encrypting large amounts of data
    - You can import your own key material
    - KMS does not store, manage, or track your data keys
- CloudHSM
    
    - Cloud based hardware security module
    - Runs in VPC
    - Generate and use your own encryption keys
    - Managed, automatically scaling service
    - Uses FIPS 140-2 Level 3
    - AWS has no access to your keys
    - Use cases
        
        - Protect Private Keys
        - Store Master Key for Oracle
        - Offload SSL/TLS processing from your servers
- ACM
    
    - AWS certificate manager
    - Create and store SSL/TLS certificates
    - Single, Multi, and wildcrd domains
    - Public certs are signed by AWS public CAs
- WAF
    
    - Web app firewall
    - Lets you create rules to filter common exploits, SQL injections and XSS
    - Web ACLs
        
        - Use web access controls lists to protect a set of AWS resources
        - Rules - statement that defines insepction criteria
        - Rule grous - store rules
        - IP sets - range of IP addresses
        - Rule Action - what do do when criteria meetrs rule
            
            - Count
            - Block
            - Allow
        - Match Statement
            
            - Geographic
            - IP Set Match
            - SQLi Attack
            - String match
            - XSS attack
- Shield
    
    - DDoS Protection service
    - Helps minimize downtime and latency
    - Tiers
        
        - Standard - Free - integrated with CloudFront by default
        - Advance - $3,000