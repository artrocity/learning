Cheat Sheets:  
[https://digitalcloud.training/aws-cloudformation/](https://digitalcloud.training/aws-cloudformation/)  
[https://digitalcloud.training/aws-elastic-beanstalk/](https://digitalcloud.training/aws-elastic-beanstalk/)  
[https://digitalcloud.training/aws-config/](https://digitalcloud.training/aws-config/)  
[https://digitalcloud.training/aws-resource-access-manager/](https://digitalcloud.training/aws-resource-access-manager/)  
[https://digitalcloud.training/aws-systems-manager/](https://digitalcloud.training/aws-systems-manager/)  
[https://digitalcloud.training/aws-opsworks/](https://digitalcloud.training/aws-opsworks/)
 
Deployment Exam Cram

- AWS CloudFormation
    
    - CloudFormation deploys infrastructure using code (JSON or YAML templates)
    - Infrastructure is provisioned consistently, with fewer mistakes
    - Less time and effort than configuring resources manually
    - Version control and peer review is available
    - Free to use (Only charged for provisioned resources)
    - Can be used to manage updated and dependencies
    - Can be used to rollback and delete the entire stack
    - Components
        
        - Templates - text file to build environment
        - Stack File - Environment built
        - Stack Set - Transfer sets across account or region
        - Change Set - Changes made in a stack
- Elastic BeanStalk
    
    - PaaS Solution
    - Used to quickly deploy code in the cloud
    - Developers upload applications and Elastic Beanstalk handles the deployment details of capacity provisioning
    - Supports: Java, .NET, PHP, Python, Node.js, Ruby, GO, and Docker web apps
    - Layers
        
        - Applications - contain environments and config
        - App Version - reference to a section of deployable code located within an S3 bucket
        - Environment - A version that has been deployed, comprised of all resources created by Beanstalk
    - Web Servers and Workers
        
        - Web Servers
            
            - Standard apps that listen and then process HTTP requests
        - Workers
            
            - Specialized apps that have a background processing tasks that listens for messages on an Amazon SQS queue.
            - Should be used for long-running tasks.
- SSM Parameter Store
    
    - Secure hierarchical storage for secrets and data as parameter values
    - Highly scalable, available, and durable
    - Reference values by using the unique name specified when creating the value
    - No Native Key rotation
- Secrets Manager
    
    - Store Secrets through the use of automation, built in for:
        
        - RDS(SQL), RedShift, DocumentDB
        - Non-Hierarchical
        - Charged per secret
- AWS Config
    
    - Evaluates resource configurations for desired settings
    - Provides snapshot of current configuration
    - Retrieve current/historical configurations of your resources
- AWS RAM
    
    - Share resources
        
        - Across AWS Accounts, Ous, and IAM roles and users
    - Resource shares are created with
        
        - RAM console
        - RAM APIs
        - AWS CLI
        - AWS SDKs
- AWS OpsWork
    
    - Configuration Management service that provides managed instances of Chef and Puppet
    - Updates include patching, updating, backup, configuration, and compliance management