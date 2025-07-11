AWS Secrets Manager

- Designed to store secrets and passwords
- Similar to SSM Parameter Store
- Store and rotate secrets without needing to manually do it for the following services:
    
    - RDS
    - RedShift
    - DocumentDB
- Any services not in that list will need to have custom code created in Lambda
- Charged per Secret