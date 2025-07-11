AWS Shared Controls

- Shared controls are controls which apply to both the infrastructure layer and customer layer
- In shared control:
    
    - AWS provides the requirements for the infrastructure
    - Customer must provide their own control implementation
- Examples
    
    - Patch Management
        
        - AWS is responsible for patching the underlying hosts
        - Customers are responsible for patching their OS
        - THINK EC2
    - Configuration Management
        
        - AWS maintains the configuration of its infrastructure devices
        - Customer is responsible for configuring their own guest operating systems and databases
    - Awareness and Training
        
        - AWS trains AWS Employees
        - Customer trains their own employees