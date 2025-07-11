AWS Elastic Container Registry

- Fully-managed container registry
- Integrated with ECS and EKS
- Docker CLI to push, pull, list, and tag
- Container Images stored on S3
- Access control only applies to private repos
- Components
    
    - Registry - Create repos for images and store them
    - Auth Token - Client must pull this to use ECR push pull
    - Repo - Contains docker images, OCI images and artifacts
    - Repo Policy - Control access to repos
    - Image - Push pull images to repos