IaaC with CloudFormation

- Similar to Terraform
- Allows you define template file using Code
- The code is formatted in either JSON or YAML formats
- CloudFormation will build your infrastructure according to the template
- Core Components
    
    - Templates - Text files that contain instructions to build the AWS environment
    - Stacks - The environment described by the template and created, updated, and deleted as a single unit
    - StackSets - Extends the functionality of stacks by enabling you to create, update, or delete, stacks across multiple accounts and regions
    - Change Sets - Summary of proposed changes to your stack and you will see how those changes might impact your existing resources