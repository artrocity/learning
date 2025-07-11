Amazon Simple Queue Service

- Allows you to send, store, and receive messages between software components without losing messages or requiring other services to be available
- SQS Workflow
    
    - Application sends message into queue
    - User or service retrieves message from the queue
    - User or service processes it
    - User or service deletes it
- Contains a payload
    
    - Data contained within a message
- Where messages are placed until they are processed