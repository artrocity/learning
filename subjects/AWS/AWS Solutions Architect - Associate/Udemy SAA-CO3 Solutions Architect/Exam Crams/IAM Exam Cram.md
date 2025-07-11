IAM Cheat Sheet￼[https://digitalcloud.training/aws-iam/](https://digitalcloud.training/aws-iam/)
 
Exam Cram

- IAM
    
    - IAM is universal and doesn’t apply to regions - Its global
    - IAM is eventually consistent - may take time to replicate across the AWS environment
    - IAM is used to securely control individual and group access to AWS resources
    - IAM makes it easy to provide multiple users secure access to AWS resources
    - IAM can be used to manage:
        
        - Users
        - Groups
        - Access Policies
        - Roles
        - User credentials
        - User Password Policies
        - Enable MFA
        - API Keys for programmatic access
    - Authentication Methods
        
        - Console Password - used to login to AWS Management Console
        - Access Keys - used for programmatic access
        - Server Certificates - uses SSL/TLS certificates
    - Root User
        
        - Email address used when signing up for the AWS Account
        - MFA is highly recommended
        - Root user credentials are the email address and password
        - Root account has full administrative permissions and these can not be restricted
    - Users
        
        - IAM users are an entity that represents a person or service who have been granted access to an AWS account
        - By default, new users are created with NO access to any AWS services - they can only login to the AWS console
        - Permissions must be explicitly granted to allow a user access to an AWS service
        - You can have up to 5000 users per AWS account
    - "Service Accounts"
        
        - IAM Users can be created to represent applications, these are known as service accounts
    - Groups
        
        - Groups are collections of user and have policies attached to them
        - A group is not an identity and can't be identified as a principal in an IAM policy
        - Use groups to assign permissions to users
        - Use principal of least privilege
        - Can't next groups
    - Roles
        
        - Roles are created and then assumed by trusted entities
        - With IAM roles you can delegate resources for users and services
        - IAM users or AWS services can assume "Roles" to obtain temporary security credentials
        - Temporary security credentials are issued by the AWS Security Token Service
    - Policies
        
        - Policies are documents that define permissions and can be applied to users, groups, and roles
        - Policy documents are written in JSON (Key value pairs that consists of an attribute and a value)
        - All permissions are implicitly denied by default
        - If more than one policy affects a resource, the most restrictive policy is applied
        - Policy Types
            
            - Identity-based policies - attached to users, groups, or roles
            - Resource-based policies - attached to a resource (EC2, S3, etc.)
            - IAM permission-boundaries - Used to set the maximum permissions an identity-based policy can grant an IAM entity
            - AWS Organization service control policies - Used to specify the maximum permissions for an organization or OU
            - Session policies - used with AssumeRole* API actions
    - IAM Best Practices
        
        - Lock away AWS account root user access keys
        - Create individual IAM users
        - Use groups to assign permissions to users
        - Apply the principle of least privilege
        - Get started using permissions with AWS managed policies
        - Use Customer managed policies instead of inline policies
        - Use access levels to review IAM permissions
        - Configure a strong password policy for your users
        - Enable MFA
        - Use roles for applications that run on EC2 instances
        - Use roles to delegate permissions
        - Do not share access keys
        - Rotate credentials regularly
        - Remove unnecessary credentials
        - Use policy conditions for extra security
        - Monitor activity in your AWS account