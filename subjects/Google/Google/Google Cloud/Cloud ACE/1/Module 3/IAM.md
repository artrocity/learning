Identity and Access Management

- Admins can apply policies that define WHO can do WHAT on WHICH resource
- WHO - Principle
    
    - WHO is known as a principle which has an identifier usually an email address
    - Google Account
    - Google Group
    - Service Account
    - Cloud Identity Domain
- WHAT - Role
    
    - IAM Roles are a collection of permissions
    - 3 Kinds of roles in IAM
        
        - Basic IAM Role
            
            - Broad in scope
            - Affect all resources in a project
            - Affects
                
                - Owner - View, Change, setup billing, & roles
                - Editor - View & Change
                - Viewer - View but can't change
                - Billing Admin - Can setup billing but not interact with other roles
        - Predefined IAM Role
            
            - Specific services within Google Cloud offer Predefined roles
        - Custom IAM Role
            
            - Many companies conduct a least privilege role
            - You must manage the permissions that define the custom role you create
            - Custom roles can only be applied to either the project or organization level