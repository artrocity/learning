Cloud Run

- Managed compute platform that runs stateless containers via web requests or hub sub events
- Serverless - All infrastructure management tasks are removed
- Built on Knative - open API and runtime environment built on Kubernetes
- Fully managed on Google Cloud or Kubernetes
- Fast, automatically scales up or down
- Charges only for resources used calculated down to the nearest 100 milliseconds
- Starts containers on demand to handle requests, and ensures all incoming requests are handled by dynamically adding or removing containers
- Can use
    
    - Source Based Workflow
        
        - Deploy source code instead of container image
        - Cloud Run builds source and packages the application into a container image
            
            - Achieved via Buildpacks
        - Cloud Run takes care of the HTTPs encryption
    - Container Based Workflow
        
        - See below
- Only pay for Startup, Shutdown, and Request Handling
    
    - Small fee for every 1 million served requests
    - Price increase with CPU and Memory
 
Cloud Run Developer Workflow

- 3 Step process
    
    - Write application in desired programming language
        
        - Application should start a server that listens for web requests
    - Build and package your application into a container image
    - Push container image to an artifact registry where Cloud Run will deploy it