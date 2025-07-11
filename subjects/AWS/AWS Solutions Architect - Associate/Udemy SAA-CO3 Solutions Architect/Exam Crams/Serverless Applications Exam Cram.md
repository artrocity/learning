Cheat Sheet:  
[https://digitalcloud.training/aws-lambda/](https://digitalcloud.training/aws-lambda/)  
[https://digitalcloud.training/amazon-api-gateway/](https://digitalcloud.training/amazon-api-gateway/)  
[https://digitalcloud.training/aws-application-integration/#amazon-simple-notification-service](https://digitalcloud.training/aws-application-integration/#amazon-simple-notification-service)
 
Exam Cram

- Serverless Services
    
    - No instances, OS, or software to manage
    - Don’t need to provision hardware
    - Capacity provisioning and patching is handled automatically
    - Provides automatic scaling and high availability
    - Can be very cheap
- AWS Lambda
    
    - Runs code as functions
    - Executes code when needed
    - Scales automatically
    - Pay only when code is running
    - Specify the amount of memory you need
    - Maximum execution timeout
    - Event-driven compute service
    - Event-sources trigger lambdas
    - Benefits:
        
        - Continuous scaling
        - Millisecond billing
        - No servers to manage
        - Integrates with all AWS services
    - Function invocations
        
        - Synchronous
            
            - CLI, SDK, API
            - Result returned immediately
            - Error happens client-side
        - Asynchronous
            
            - S3, SNS, CloudWatch
            - Lambda tries 3 times
            - Processing can be idempotent
        - Event Source Mapping
            
            - SQS, Data stream
            - Lambda does the polling
- Dead Letter Queue
    
    - Handles message failures
- SQS Long Vs Short Polling
    
    - Long Polling
        
        - Waits for messages to arrive
        - Can lower costs
        - Enabled at the queue level
        - In effect when receive message wait time is 0 - 20 seconds
    - Short Polling
        
        - Returns immediately even if message queue is empty
- SNS
    
    - Pub / Sub messaging service
    - Systems can fan out to a large number of subscriber endpoints
    - Endpoints can include
        
        - SQS
        - SMS
        - Lambda
        - HTTP/s webhooks
        - Mobile Push
        - Email
    - Topics
        
        - Multiple recipients can be grouped into Topics
        - Access point for allowing recipients to dynamically subscribe for identical copies of the same notification
        - One topic can support deliveries to multiple endpoint types
        - Simple APIs and easy integration with applications
        - Flexible message delivery over multiple transport protocols
    - AWS Step functions
        
        - Used to build applications in a series of steps in a visual workflow
    - AWS Event Bridge
        
        - Serverless event bus for building event-driven applications
    - API Gateway
        
        - Fully managed service for APIS
        - API endpoint type refers to hostname of API
        - All APIs created expose HTTPS endpoints only
        - Endpoint type can be:
            
            - Edge-optimized - global users
            - Regional - regional users
            - Private - VPC uses
        - Caching
        - Add API caching to API calls by activating API Gateway cache
        - Allows for the caching of the response
        - Reduce the number of overall calls to the backend
        - Throttling
            
            - Sets a limit on steady-state rate
            - Default is 10,000 requests per second or 5000 requests across all APIs within an account
            - 429 Error: Too many requests if gone over
          
          
          
          
        
          
- Application Integration Services
- |   |   |   |
    |---|---|---|
    |Service|What it does|Example use cases|
    |Simple Queue Service|Messaging queue, store and forward￼patterns|Building decoupled apps|
    |Simple Notification Service|Set up, operate, and send notifications￼from the cloud|Email notifications when￼CloudWatch alarms trigger|
    |Step Functions|Need to support external processes or specialized￼logic|Human enabled workflows|
    |Amazon MQ|Message broker service for Apache Active MQ|Message queue that supports standard APIs|
    |Amazon Kinesis|Collect, process, and analyze streaming data|Collect data from IoT devices for later processing|
    
- Queue Types
- |   |   |
    |---|---|
    |Standard Queue|FIFO Queue|
    |Unlimited Throughput|High Throughput|
    |Best-effort ordering|First In First Out|
    |At least once delivery, sometimes more|Exactly One processing|