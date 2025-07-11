Metrics, Analysis, and Tracing

- AWS X-Ray
    
    - Used to visualize the components of your application, identify performance bottlenecks, and troubleshoot requests that resulted in an error
    - AWS services send trace data to X-Ray, and it processes the data to generate a service map and searchable trace summaries
    - To integrate you need to install the X-Ray agent and integrated the SDK with your application
        
        - X-Ray agent is a software app that gathers raw segment data and relays it to the X-Ray Service
        - SDK Captures metadata for requests made to databases
        - Captures metadata for SQS and SNS
- Prometheus
    
    - Open-source monitoring system and time series database
    - Uses Prometheus Query Language - PomrQL to monitor and alert on the performance of containerized workloads
    - Automatically scales the ingestion, storage, alerting, and querying of operational metrics as workloads grow and shrink
- Grafana
    
    - Open-source analytics and monitoring services for databases
    - Provides interactive data visualization for your monitoring and operational data
    - Integrates with SSO and SAML