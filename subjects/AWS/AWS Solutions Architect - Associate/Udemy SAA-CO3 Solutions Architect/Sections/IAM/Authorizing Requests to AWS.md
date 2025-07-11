Context

- Actions
    
    - Actions principal wants to perform
- Resources
    
    - The AWS resource
- Principal
    
    - The AWS user, role, federated user, or application that sent the request
- Environment Data
    
    - Information about: IP address, user agent, SSL status, timestamp
- Resource Data
    
    - Data related to the resource request
 
Steps to Authorize Requests to AWS

1. AWS Authenticates the principal that makes the request
2. Process the request context
3. Evaluate all policies within the account
    
    1. Identity
    2. Resource
    3. SCP
4. Determine whether a request is allowed or denied