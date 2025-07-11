EventBridge

- Used to be known as CloudWatch Events
- Central Hub for routing events between Event Sources
    
    - Event Sources
        
        - AWS Services
        - Custom Apps
        - SaaS Apps
- Core Concepts
    
    - Events
        
        - Records of something happening in your system
    - Event Buses
        
        - Pipelines that receive events.
        - AWS Provides a default bus but you can create your own
    - Rules
        
        - These determine where events are sent.
        - Rules match incoming events based on their structure and route them to targets
    - Targets
        
        - AWS Services
        - Lambdas
        - SNS topics
        - Etc.
- Workflow
    
    - Source (AWS Service) generates an event and sends it to an AWS Bus
    - EventBridge evaluates the event against all rules on that bus
    - If the event matches a rule's pattern, EventBridge sends the event to the rule's targets
    - The target processes the event according to their configurations