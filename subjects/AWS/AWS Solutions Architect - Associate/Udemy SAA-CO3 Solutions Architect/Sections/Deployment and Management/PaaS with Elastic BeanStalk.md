AWS BeanStalk

- You upload your code and data and create your application
- Write code and package it and then send it to BeanStalk
- BeanStalk will launch and manage the environment
- Supports Java, .NET, Node.js, PHP, Ruby, Python, Go, Docker
- Uses EC2, ECS, Auto Scaling, and ELB
- Provides UI to monitor and manage the health of apps
- Managed platform updates deploy the latest version of software and patches
- BeanStalk Layers
    
    - Applications
        
        - Contains environments, environment configurations, and app versions
        - You can have multiple app versions held within an app
    - App Versions
        
        - Reference top a section of deployable code
        - App version will point to an S3 bucket which contains the code
        - Versions are applied to an environment
    - Environment
        
        - An app version that has been deployed to AWS resources
        - Resources are configured and provisioned by AWS BeanStalk
        - Environment is comprised of all the resources created by BeanStalk and not just an EC2 instance with your code uploaded
- Web Servers
    
    - Standard applications that listen for and then process HTTP requests over port 80
- Workers
    
    - Specialized Apps that have background processing tasks that listens for messages on an Amazon SQS queue
    - Should be used for long running tasks
- Workflow
    
    - User submits traffic to Web Server
    - Web server places the message in an SQS queue
    - Worker polls the queue
    - When a queue message is found, the worker gets the message and processes it