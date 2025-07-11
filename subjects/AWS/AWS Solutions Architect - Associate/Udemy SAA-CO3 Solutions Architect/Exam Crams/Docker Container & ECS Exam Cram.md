Cheat Sheet:  
[https://digitalcloud.training/amazon-ecs-and-eks/](https://digitalcloud.training/amazon-ecs-and-eks/)
 
Exam Cram

- ECS
    
    - Serverless with Fargate
    - Fully managed container orchestration
        
        - Control plane is managed for you
    - Docker Support
        
        - Run and manage docker containers
    - Windows Container Support
    - ELB Integration
    - ECS Anywhere
        
        - Enables the use of ECS control planes to manage on-premises implementations
    - Components
        
        - Cluster - Logical grouping of EC2 instances
        - Container Instance - EC2 instance running the ECS agent
        - Task Definition - Blueprint for how a container should launch
        - Task - running container
        - Service - Auto Scaling, defines long running tasks
    - ECS Launch Type
        
        - ECS Launch types determines the type of infrastructure on which your tasks and services are hosted
        - ECS Launch Types
            
            - EC2
                
                - You control everything
            - Fargate
                
                - Limited control, serverless
    - ECS Images
        
        - Containers are created from a read-only template called an image
        - Images are built from a Dockerfile
        - Only docker containers are supported'
        - Image contains instruction for creating a Docker container
        - Images are stored in a registry such as DockerHub or ECR
        - ECR is a Managed AWS Docker Registry Service
    - ECS Tasks
        
        - Task definitions are required to run Docker containers in ECS
        - Task definition is a text file in a JSON
        - Task definitions use Docker images to launch containers
        - You specify the number of tasks to run
    - ECS Clusters
        
        - Logical grouping of container instances
        - ECS allows the definition of a desired count of tasks to run in cluster
        - Clusters contain tasks using Fargate and EC2 Launch type
        - Each container instance can only be apart of one cluster
        - IAM policies restrict access
    - ECS Container Agent
        
        - Allows container instances to connect to cluster
        - Runs on each resource in a cluster
        - Included in AWS ECS AMI
        - Linux and Windows Based
        - For now-AWS Linux instances, you have to manually install the agent
    - Scaling
        
        - Service Auto Scaling
            
            - Adjusts desired task count up or down
            - Supports target, step, and scheduled scaling
        - Cluster Auto Scaling
            
            - Uses a capacity provider to scaler instances
- EKS Use Cases
    
    - Standardize Container orchestration
    - Hybrid deployment
    - Batch Processing
    - Machine Learning
    - Web Apps
- |   |   |
    |---|---|
    |ECS|EKS|
    |AWS Specific - Supports Docker|Open Source|
    |Simpler to learn and use|Feature rich - steep learning curve|
    |Leverages Route53, ALB, CloudWatch|Uses internal services|
    |Tasks are instances of containers run on underlying compute|Pods are containers collocated with one another and can share access|
    |Limited Extensibility|Extensible with community third-party addons|