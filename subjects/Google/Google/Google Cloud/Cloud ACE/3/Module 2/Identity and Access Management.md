Cloud IAM

- IAM identifies who can do what on each resource
    
    - Who
        
        - Person, group, or application
    - What
        
        - Specific privileges or actions
    - Resource
        
        - Any google cloud service
- IAM Objects
    
    - Organization
        
        - Root node for Google Cloud Resources
        - Organization Roles
            
            - Admin - Control over all cloud resources - useful for editing
            - Project Creator - Controls project creation
        - Created when a Google Workspace or Cloud Identity account creates a Google Cloud Project
        - Organization Admin
            
            - Define IAM Policies
            - Determine structure of the resource hierarchy
            - Delegate responsibility over components through IAM Roles
    - Folders
        
        - Additional grouping mechanism between projects
        - Used for:
            
            - Teams, Departments, Different legal entities
        - Folders allow delegation of administration rights
    - Projects
    - Resources
    - Roles
    - Members
- Policies inheritance
    
    - Policies applied to a level will be applied to that specific level and all objects that are children of that object