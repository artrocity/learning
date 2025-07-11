Amazon Elastic Container Service

- ECS Cluster
    
    - Logical grouping of tasks or services
- Tasks
    
    - Tasks are a running docker container
    - Tasks are creating from a definition
    - Definitions create Images
    - Images are stored inside of Amazon Elastic Container Registry
    - ECS Services (Similar to EC2 Autoscaling)
        
        - Services are used to maintain a desired count of tasks
- Features
    
    - Serverless Feature with AWS Fargate
        
        - No need to run services
    - Fully managed container orchestration
        
        - Control plane is managed for you
    - Docker support
        
        - Run and manage Docker containers with integration into the Docker Compose CLI
    - Windows container support
        
        - ECS supports management of windows containers
    - ELB integration
        
        - Distribute traffic across containers using ALB or NLB
    - AWS ECS Anywhere
        
        - Enables the use of ECS Control plane on-premises
- ECS Image
    
    - Containers are created from a read-only template called an image which has the instructions for creating a docker container
    - Images are built from a Dockerfile
    - Only Docker Containers are supported on ECS
    - Images are stored in a registry such as DockerHub or AWS ECR
    - ECR is a managed AWS Docker registry service that is secure, scalable and reliable
    - ECR supports private Docker repos with resource based permissions using AWS IAM
    - Docker CLI to push, pull images
- ECS Tasks and Definitions
    
    - Task definitions are required to run Docker containers in ECS
    - Task definitions are a text file in JSON format that describes one or more containers up to a max of 10
    - Task definitions use Docker images to launch containers
- Launch Types
    
    - EC2
    - Fargate
- ECS Components
    
    - Cluster
        
        - Logical grouping of tasks or services
    - Container instance
        
        - EC2 running ECS agent
    - Task Definition
        
        - Blueprint that describes how an container should launch
    - Task
        
        - Running container using settings from a task definition
    - Image
        
        - Docker image referenced in the task definition
    - Service
        
        - Defines long running tasks, can control task count with Autoscaling and attach and ELB