AWS ECS and IAM Roles

- Roles
    
    - ECS container instance IAM role - used by ECS to call ECS APIs
    - Task IAM Roles - provides permissions to containers running tasks
    - ECS task execution role - task grants ECS container and Fargate agents permissions to make API Calls
    - EC infrastructure role
    - ECS anywhere IAM role - requires AWS role to talk to services
    - ECS CodeDeploy for blue-green