AWS Organizations

- Allows you to consolidate multiple AWS accounts into an organization that you create and manage
- Available in two feature sets:
    
    - Consolidated Billing
        
        - Have a single bill in the main - manage account
        - You can still see the costs for each account
        - Can enable you to have volume level discount - which is applied to all accounts
        - Includes
            
            - Paying account - Cannot Access resources of other accounts
            - Linked Account - All linked accounts are independent
    - All Features
        
        - Service Control Policies
        - Tag Policies
- Organizations Includes:
    
    - Root Accounts
        
        - Root / Master Account - The account responsible for all other accounts
        - Can enable CloudTrail in Management Account
            
            - It will apply to all members and accounts
    - Organizational Units
        
        - Can group accounts into Ous
        - SCP (service control policy) can be applied to Ous
            
            - Can control tagging
        - Can create accounts programmatically via Organizations API