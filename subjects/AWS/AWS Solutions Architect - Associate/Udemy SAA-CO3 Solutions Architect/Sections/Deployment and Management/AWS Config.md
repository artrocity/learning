AWS Config

- Evaluates resource configurations against desired settings
- Get snapshots of current config of resources
- Retrieve configs of resources that exist in your account and historical versions
- Receive a notification whenever a resource is created, modified, or deleted
- View relationships between resources
- Work flow
    
    - Applications send their config changes to AWS Config
    - Config stores those values in S3
    - Config can Send notifications with SNS
    - CloudWatch events can be configured to alert when changes occur
    - Systems Manager Automation can automatically remediate the problems