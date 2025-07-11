AWS IAM

- In AWS IAM, you can
    
    - Create users
        
        - Users as default can do nothing, all actions are denied
        - All actions must be specifically applied
- Least privilege principle
    
    - Only giving a user the bare minimum they need to complete their tasks and nothing more
- IAM Policy
    
    - JSON document that describes what API calls a user can or can not make
    - An IAM Policy JSON is made up of
        
        - Version
        - Statement - Object
        - Effect - Allow or Deny
        - Action - Which AWS API Call
        - Resource - What AWS Resource is the API Call used for
- IAM Groups
    
    - Grouping of users
    - IAM Policies can be applied to a group
- IAM Roles
    
    - Associated permissions that allow or deny specific actions
    - Can be assumed for temporary amounts of time
    - No username or password
    - Used to gain access to temporary permissions
 
IAM Core Features

- Root User
    
    - God Mode - Can do anything
- Users
    
    - Default denied everything off the rip
    - Has to specifically be allowed to do anything
- Groups
    
    - Group users together for common policies to be applied to a group instead of individual users
- Policies
    
    - Document describing permissions
- Roles
    
    - Temporary access to permissions
    - No username or password