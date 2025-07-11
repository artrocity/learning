Scenario 1

- Requirement
    
    - A select group of users should be allowed to change their IAM passwords
- Solution
    
    - Create a group for the users and apply permissions policy that grants the ability to change their password
    - Iam:ChangePassword API permission

￼Scenario 2

- Requirement
    
    - An AWS EC2 instance must be delegated with permissions to access an AWS DynamoDB table
- Solution
    
    - Create a role and assign a permissions policy to the role that will grant access to the DynamoDB table
 
Scenario 3

- Requirement
    
    - A company has created their first AWS account. They need to assign permissions to users based on job function
- Solution
    
    - Create groups for the users based on their job functions (HR, IT, Admins, etc.)
    - Use AWS Managed policies that are aligned with common job functions and assign the policies to the respective groups
 
Scenario 4

- Requirement
    
    - Solutions architect needs to restrict access to an AWS service based on the source IP address of the requester
- Solution
    
    - Create an IAM permissions policy and use the Condition Element to control access based on the source IP address
 
Scenario 5

- Requirement
    
    - A developer needs to make programmatic API calls from the AWS CLI
- Solution
    
    - Instruct the developer to create and use a set of access keys to use for access via the CLI
 
Scenario 6

- Requirement
    
    - A group of users require full access to all Amazon EC2 API actions
- Solution
    
    - Create a permissions policy that uses a wildcard for the action element relating to EC2 (ec2:*)