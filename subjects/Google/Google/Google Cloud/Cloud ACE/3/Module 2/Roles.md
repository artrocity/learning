Roles

- There are 3 Types of roles in IAM
    
    - Basic
        
        - Allow you to define fixed, coarse-grained levels of access
            
            - Owner
            - Editor
            - Viewer
            - Billing Admin
    - Predefined
        
        - Apply to a particular Google Cloud Service in a project
            
            - Can do what on Compute Engine in this project
        - Role Example
            
            - Instance Admin Role
                
                - Compute Instances: Delete, Get, List, Set Machine Type, Start, Stop
    - Custom
        
        - When a basic or predefined role doesn't suite your needs you can use the custom role.
        - Most companies use the rule of least privileges
            
            - Grant a user the least amount of access they need to complete their job