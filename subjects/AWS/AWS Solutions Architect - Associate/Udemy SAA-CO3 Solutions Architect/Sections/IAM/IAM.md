IAM

- Service used for authentication and authorization into your AWS Account
- There are 3 methods of accessing IAM
    
    - Console
    - CLI
    - API
    - SDK
- IAM operates on the principle known as Least Privilege Access
    
    - Users and entities should only have the minimum permissions needed to perform their tasks
- Identity Access Management
- Principals
    
    - Person or application that can make a request for an action or operation on an AWS resources
- Identities
    
    - Users
        
        - Individual Identities created for people or applications that need AWS Access
        - Each user has unique security credentials
        - Up to 5000 user accounts can be created
        - Users have no permissions by default
    - Groups
        
        - Collection of IAM users that share the same permissions
        - Groups are assigned permissions through the use of policies
    - Roles
        
        - Similar to users but grant temporary access, used for delegations
        - Roles can be assumed by AWS services, applications, or other AWS accounts
- Policies
    
    - Identity-based policies
        
        - Attached directly to users, groups, or roles
        - Specify what actions are allowed or denied for a specific AWS resource
    - Resource-based policy
        
        - Attached to AWS resources(S3 buckets, lambdas, etc.)
        - Controls who can access that resource and what actions they can perform
    - Permission Boundaries
        
        - Assigned to users and roles
        - Sets the maximum permissions and identity can have
        - Used to mitigate privilege escalation attacks
    - Organizations Service Control Policies
        
        - Specify the maximum permissions for an organization or OU
    - Session Policies
        
        - Used with the AssumeRole* API Actions
    
    - Resource policy and Identity policy
        
        - Gain all permissions listed in both policies
        - Permissions are evaluated using a logical OR - need permission in either policy
        - Example: If an S3 bucket policy allows s3:GetObject and the IAM user policy allows s3:PutObject, the user can perform both actions
        - Exception: For cross-account access, both policies must explicitly allow the action
    - Identity policy and Permissions Boundary
        
        - The permissions boundary acts as a guard rail - it sets the maximum allowed permissions
        - A permission must be allowed by BOTH the identity policy AND the permission boundary
        - If a permission is in the identity policy but not in the boundary, it's denied
        - Example: If identity policy allows all S3 actions but boundary only allows read actions, user can only perform read actions
    - Organization SCP and Identity Policy
        
        - SCPs act as an override at the organization level
        - Permissions must be allowed by BOTH the SCP AND the identity policy
        - SCPs can't grant permissions, they can only restrict them
        - Even if an identity policy allows an action, if the SCP denies or doesn't allow it, the action will be denied
        - Example: If SCP denies ec2:DeleteVpc but identity policy allows it, user cannot delete VPCs
- Best practices
    
    - Root account protection
        
        - Secure the root user with a strong password and MFA
        - Avoid using it for daily tasks and create IAM users for daily tasks
    - Regular Audits
        
        - Regularly review and audit AWS policies, roles and access patterns using AWS
            
            - AWS Cloudtrail
            - AWS IAM Access Analyzer
            - AWS Credential Reports
    - Policy Versioning
        
        - Maintain versions of IAM policies to track changes and rollback if necessary
      
    

Permissions