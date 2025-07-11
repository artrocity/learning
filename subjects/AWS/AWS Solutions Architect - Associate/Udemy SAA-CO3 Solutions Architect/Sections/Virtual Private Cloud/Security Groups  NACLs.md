Virtual Firewalls

- Security Groups
    
    - Apply at the instance level
    - Attached to the elastic network interface
    - Can be applied to any instance in a subnet
    - Stateful
        
        - Supports only allow rules
        - Allows the return traffic automatically
- NACLs
    
    - Applied at the subnet level
    - Only apply to traffic entering or leaving the subnet
    - Automatically applies to all instance in the subnet
    - Stateless
        
        - Checks for an allow rule for both source and destination connections