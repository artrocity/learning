Cheat Sheet: [https://digitalcloud.training/aws-organizations/](https://digitalcloud.training/aws-organizations/)
 
Topics

- Organizations
    
    - Consolidate multiple accounts into a management account that you manage
    - Available in two features
        
        - Consolidated Billing, which includes
            
            - Linked Accounts - All linked accounts are independent
            - Paying account - Independent and can't access resources of other account
            - Single payment method for all accounts
            - Combined view of charges
            - Pricing benefits from aggregated usage
            - Limit of 20 linked accounts
        - All Features
    - Includes:
        
        - Root accounts
            
            -   
                
        - Organizational Units
    - Policies are applied to root accounts or OUs
    - Service Control Policies
        
        - Must have "All Features" applied in the Organization
        - Can be applied to accounts or OUs
        - Policies can be assigned at different points in the hierarchy
        - SCPs affect only IAM users and roles - NOT resource policies
        - SCPs affect the root account in member accounts
        - Do not affect any action performed by the management account
    - SCPs Strategies
        
        - Deny list strategy
            
            - Uses the FullAWSAccess SCP
            - Attached to every OU and account
            - Overrides the implicit deny
            - Explicitly allows all permissions to flow down from the root
            - Create additional SCPs to explicitly deny permissions
        - Allow list strategy
            
            - FullAWSAccess SCP is removed
            - No APIs are permitted anywhere unless you explicitly allow them
            - Create SCPs to allow permissions
            - SCPs must be attached to target accounts and every account above it
    - Migration
        
        - Accounts can be migrated between organizations
        - Must have root or IAM access to both the member and management account
        - Use AWS Organizations for just a few accounts
        - Use the API for many accounts