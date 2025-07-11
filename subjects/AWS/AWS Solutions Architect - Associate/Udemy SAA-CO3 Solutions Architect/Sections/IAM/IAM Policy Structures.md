AWS IAM Policy Structures

- Everything in AWS is an API action
    
    - When you stop an RDS instance via the CLI or Command Console, an API stops the instance
    - "Action": "rds:StopDBInstance"
- Each AWS service has its own set of actions that describes tasks you can perform with that service
- Policies are written in JavaScript Object Notation
- JSON Structure
    
    - Version - In an AWS policy JSON, the "Version" field is a required element that specifies the policy language version. Currently, there are two possible values:
        
        - "2012-10-17" - This is the current version and includes support for all modern policy features. You should always use this version.
        - "2008-10-17" - This is an earlier version that does not support newer features like policy variables. This version is now considered legacy.
    - Statement
        
        - A block of code
        - All properties are evaluated together
        - Policies can contain more than 1 permission statement
    - Effect:
        
        - Allow or Deny
    - Actions:
        
        - List specific resource operations that the policy affects
    - Resource
        
        - Lists the specific resources that the policy applies to
    !["version••: "2012-10-17", fect": "action": ["arn:aws: s3: : ' 'Resource": ](Exported%20image%2020250301231137-0.png)