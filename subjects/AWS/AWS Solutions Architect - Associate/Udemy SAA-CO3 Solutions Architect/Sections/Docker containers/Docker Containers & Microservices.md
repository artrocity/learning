Server Virtualization vs Containers

- Virtualization / EC2s
    
    - Every VM / Instance needs an operating system which uses significant resources
    - These resources require overhead - maintenance, patch management, etc.
    - Virtualization Characteristics
        
        - Creates complete virtual machines with their own Oss
        - Takes more resources and more time to start
        - Better isolation since each VM is separate
        - Good for running different Oss or when you need full system access
- Container
    
    - Containers are ran inside of a docker engine
    - A container shares the host machine's operating system but runs in its own isolated space
    - This makes containers much lighter and faster to start than virtual machines
    - A container includes all the code, settings, and dependencies for running the application
    - Each container is isolated from other containers
    - Containers are resource efficient
    - Container Characteristics:
        
        - Share the host OS
        - Start up quickly (seconds)
        - Use fewer resources
        - Perfect for deploying applications that need to scale quickly
        - Ensure consistent behavior across different environments
- Docker
    
    - Utilizes containerization to package an application and its dependencies into a single container image
    - Docker provides Docker Hub, a cloud based registry service for sharing container images and automating workflows
    - Ideal for cloud-native application