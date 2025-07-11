## COMPUTE PATTERN MATCHING

### Guidelines:

1. **Instance Type Pattern Recognition**
    
    - Create a decision matrix based on workload characteristics (memory-intensive, compute-intensive, balanced)
    - Map instance families to specific architectural challenges instead of memorizing all types
    - Identify repeating patterns in AWS recommendations for different workloads
2. **Auto Scaling Strategic Analysis**
    
    - Compare predictive vs. reactive scaling strategies based on business patterns
    - Synthesize connections between scaling patterns and business metrics
    - Evaluate cost implications of different scaling approaches as a decision framework
3. **Container vs. Serverless Conceptual Framework**
    
    - Create a comparison quadrant based on control needs, operational overhead, scaling characteristics, and cost models
    - Analyze specific use cases where the decision shifts from one to another
    - Connect choice to broader architectural goals rather than isolated requirements
4. **Placement Group Decision Tree**
    
    - Build a mental model of infrastructure distribution patterns and their impact on performance
    - Visualize network flow patterns for different placement strategies
    - Connect placement decisions to latency requirements and failure isolation needs
5. **Lambda Integration Patterns**
    
    - Map event sources to architectural patterns that trigger Lambda functions
    - Analyze concurrency models and their relationship to downstream system impacts
    - Develop a mental framework for when to choose Lambda within larger solution architectures

## STORAGE DECISION TREES

### Guidelines:

1. **Storage Service Selection Framework**
    
    - Create a decision tree based on access patterns, durability requirements, and performance needs
    - Map workload characteristics to optimal storage combinations
    - Analyze transition points where one storage service becomes more appropriate than another
2. **Storage Class Optimization Strategy**
    
    - Develop a mental model connecting data access frequency to storage class transitions
    - Create a framework for lifecycle policy design based on data value over time
    - Analyze cost breakpoints between storage classes for different access patterns
3. **Glacier Retrieval Analysis**
    
    - Map retrieval options to business time-sensitivity requirements
    - Develop a framework for balancing retrieval costs against storage savings
    - Synthesize compliance requirements with retrieval models
4. **Cache Placement Optimization**
    
    - Create a decision framework for cache placement based on data access patterns
    - Analyze the relationship between cache invalidation strategies and data consistency requirements
    - Map caching approaches to specific performance bottlenecks
5. **FSx Workload Mapping**
    
    - Develop a comparative framework for Windows vs. Lustre file systems based on workload patterns
    - Analyze integration points with existing workflows and migration paths
    - Create a decision matrix for when to use FSx vs. EFS vs. other storage options

## NETWORK MENTAL MODELS

### Guidelines:

1. **VPC Design Pattern Recognition**
    
    - Develop visual models of common VPC topologies and their use cases
    - Create a decision framework based on isolation requirements, connectivity patterns, and governance models
    - Analyze hybrid connectivity patterns and their impact on VPC design
2. **Subnet Strategy Framework**
    
    - Build a mental model connecting subnet design to security zones and traffic isolation
    - Create a framework for IP address allocation across complex environments
    - Analyze the relationship between subnet design and application deployment patterns
3. **Route 53 Routing Decision Matrix**
    
    - Map routing policies to specific architectural goals (failover, load balancing, geolocation)
    - Create a framework for multi-region availability design using Route 53
    - Analyze the impact of TTL settings on different routing strategies
4. **ELB Selection Framework**
    
    - Develop a comparative analysis of ALB vs. NLB vs. CLB based on protocol support, connection patterns, and performance characteristics
    - Create a decision tree for choosing the appropriate load balancer type
    - Map sticky session requirements to specific load balancer configurations
5. **CloudFront Strategic Implementation**
    
    - Build a mental model of global content delivery patterns
    - Analyze caching strategies based on content type and update frequency
    - Develop a framework for security implementation at the edge

## SECURITY FRAMEWORKS

### Guidelines:

1. **IAM Design Pattern Library**
    
    - Create conceptual models of permission delegation patterns
    - Develop a principle-based approach to role design rather than service-specific permissions
    - Analyze authentication flows across complex architectures
2. **Encryption Strategy Framework**
    
    - Build a mental model of encryption points throughout the AWS infrastructure
    - Create a decision matrix for encryption requirements based on data classification
    - Analyze key management patterns for different security postures
3. **Network Control Selection**
    
    - Develop a layered security model connecting network controls to security goals
    - Create a decision framework for when to implement security groups vs. NACLs vs. WAF
    - Map network traffic patterns to appropriate control mechanisms
4. **KMS vs. HSM Decision Framework**
    
    - Build a comparative analysis based on control requirements, compliance needs, and operational models
    - Analyze the relationship between key management approaches and application integration
    - Create a framework for key rotation strategies based on security requirements
5. **Security Hub Integration Strategy**
    
    - Develop a conceptual model of security monitoring across multiple services
    - Create a framework for alert prioritization and response planning
    - Analyze integration patterns with third-party security tools

## DATABASE SELECTION FRAMEWORK

### Guidelines:

1. **ACID vs. BASE Decision Model**
    
    - Build a mental model connecting business requirements to consistency needs
    - Create a framework for evaluating transaction requirements against scale requirements
    - Analyze application patterns that benefit from different consistency models
2. **DynamoDB Design Patterns**
    
    - Develop a conceptual approach to access pattern analysis before table design
    - Create a framework for index selection based on query requirements
    - Analyze capacity planning approaches based on workload characteristics
3. **Aurora vs. RDS Comparative Analysis**
    
    - Build a decision framework based on scaling requirements, availability needs, and performance characteristics
    - Create a cost model for different database workloads
    - Analyze migration paths from RDS to Aurora
4. **ElastiCache Implementation Strategy**
    
    - Develop a framework for cache pattern selection (cache-aside, write-through, etc.)
    - Create a decision matrix for Redis vs. Memcached based on data structure needs
    - Analyze cache eviction strategies for different workload patterns
5. **DAX Access Pattern Optimization**
    
    - Build a mental model of DynamoDB access patterns that benefit from DAX
    - Create a framework for evaluating DAX against other caching options
    - Analyze throughput patterns and their relationship to DAX effectiveness

## INTEGRATION & DECOUPLING STRATEGIES

### Guidelines:

1. **SQS vs. SNS Pattern Recognition**
    
    - Develop a conceptual model of message delivery requirements and how they map to service selection
    - Create a framework for queue design based on message processing patterns
    - Analyze retry and error handling strategies for different messaging scenarios
2. **Event-Driven Architecture Patterns**
    
    - Build a mental model of event producers and consumers across AWS services
    - Create a framework for event filtering and routing strategies
    - Analyze state management approaches in event-driven systems
3. **API Gateway Implementation Strategy**
    
    - Develop a decision framework for API design based on consumer needs
    - Create a comparative analysis of REST vs. WebSocket API patterns
    - Analyze authorization and throttling strategies for different API consumers
4. **Step Functions Workflow Design**
    
    - Build a conceptual model of state machine patterns for different workflow types
    - Create a framework for error handling and retry strategies
    - Analyze service integration patterns within workflows
5. **EventBridge Integration Patterns**
    
    - Develop a mental model of event bus design for complex organizations
    - Create a framework for event filtering and routing based on business domains
    - Analyze cross-account event patterns and their security implications

## LEARNING STRATEGIES

### Guidelines:

1. **Pattern Recognition Enhancement**
    
    - Develop a template for identifying architectural patterns across different case studies
    - Create a catalog of common AWS solution patterns with their key characteristics
    - Practice rapid pattern matching with timed exercises on example architectures
2. **Compare & Contrast Methodology**
    
    - Build a structured approach to service comparison using consistent criteria
    - Create comparison matrices that highlight decision points between similar services
    - Practice explaining the rationale for choosing one service over another in specific contexts
3. **Decision Framework Construction**
    
    - Develop a template for creating decision trees for service selection
    - Create your own decision frameworks based on the Well-Architected pillars
    - Practice applying frameworks to ambiguous scenarios to test their effectiveness
4. **Case-Based Reasoning Practice**
    
    - Build a library of reference architectures organized by problem domain
    - Create connections between different case studies to identify common principles
    - Practice applying solutions from one domain to problems in another domain

## EXAM STRATEGIES

### Guidelines:

1. **Pattern Identification Techniques**
    
    - Develop a rapid analysis method for identifying the architectural pattern being tested
    - Create a checklist of common patterns that appear in exam questions
    - Practice recognizing patterns from minimal information in the question
2. **Elimination Method Refinement**
    
    - Build a systematic approach to eliminating wrong answers based on AWS principles
    - Create a mental checklist of common wrong answer patterns
    - Practice finding disqualifying characteristics in answer options
3. **Cost-Efficiency Lens Application**
    
    - Develop a framework for quickly assessing relative costs of different solutions
    - Create a prioritized list of cost optimization principles to apply to questions
    - Practice identifying the most cost-effective option among technically valid solutions
4. **Well-Architected Framework Alignment**
    
    - Build a mental model of how exam questions map to the Well-Architected Framework
    - Create a quick reference for applying pillar principles to ambiguous questions
    - Practice identifying which pillars are being emphasized in specific questions

## SCENARIO: RESILIENT WEB APP

### Guidelines:

1. **Cross-Domain Integration Strategy**
    
    - Map compute services to networking concepts for high availability
    - Create a framework for balancing statelessness with user experience needs
    - Analyze failure scenarios across service boundaries
2. **Multi-AZ Implementation Patterns**
    
    - Develop a mental model of service-specific multi-AZ behaviors
    - Create a checklist for ensuring true AZ independence
    - Analyze recovery time objectives across different multi-AZ strategies
3. **Scaling Pattern Selection**
    
    - Build a decision framework for vertical vs. horizontal scaling based on application characteristics
    - Create a mental model of scaling bottlenecks beyond compute resources
    - Analyze data tier scaling in relation to web tier scaling

## SCENARIO: BIG DATA PIPELINE

### Guidelines:

1. **Data Flow Security Model**
    
    - Develop a conceptual framework for securing data at each stage of processing
    - Create a mental model of encryption requirements for data in different states
    - Analyze access patterns and permission requirements across the pipeline
2. **Storage Tier Optimization**
    
    - Build a decision framework for data storage throughout the processing pipeline
    - Create a mental model connecting data access patterns to storage selection
    - Analyze cost optimization strategies for large-scale data processing
3. **Processing Service Selection**
    
    - Develop a comparative analysis of batch vs. stream processing options
    - Create a framework for selecting the appropriate processing service based on data characteristics
    - Analyze integration patterns between processing and storage services

## SCENARIO: HYBRID ARCHITECTURE

### Guidelines:

1. **Connectivity Pattern Selection**
    
    - Build a decision framework for Direct Connect vs. VPN vs. Transit Gateway
    - Create a mental model of traffic patterns in hybrid environments
    - Analyze security and compliance requirements across connection boundaries
2. **Data Consistency Strategy**
    
    - Develop a framework for maintaining data consistency across environments
    - Create a mental model of replication patterns for different database types
    - Analyze latency impacts on application design in hybrid scenarios
3. **Identity Federation Implementation**
    
    - Build a conceptual model of authentication flows across hybrid environments
    - Create a decision matrix for different identity integration approaches
    - Analyze authorization patterns that span cloud and on-premises resources

## SCENARIO: MICROSERVICE PLATFORM

### Guidelines:

1. **Service Discovery Pattern Selection**
    
    - Develop a framework for service discovery based on deployment patterns
    - Create a mental model of service-to-service communication flows
    - Analyze failure modes in different service discovery approaches
2. **Data Partitioning Strategy**
    
    - Build a decision framework for data ownership across microservices
    - Create a mental model of consistency requirements between service boundaries
    - Analyze query patterns across distributed data stores
3. **Event Communication Implementation**
    
    - Develop a conceptual model of event flows between microservices
    - Create a framework for choosing synchronous vs. asynchronous communication
    - Analyze resilience patterns in event-driven microservices