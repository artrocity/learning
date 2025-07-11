AWS Cloud Hardware Security Module

- Cloud HSM is a dedicated hardware device that you get access to that runs in your VPC
- Cloud based hardware security module
- Generate and use your own encryption keys
- Uses FIPS 140-2 level 3 validated HSMs
- Managed service, automatically scales
- Retain full control of your encryption keys
- Use Cases
    
    - Offload SSL/TLS processing from web servers
    - Protect private keys from an issuing certificate authority
    - Store the master key for Oracle DB
    - Custom key store for AWS KMS - retain control of the HSM that protects the master keys
- |   |   |   |
    |---|---|---|
    ||CloudHSM|AWS KMS|
    |Tenancy|Single-Tenant|Multi-Tenant|
    |Availability|Customer Managed|Highly available|
    |Root of Trust|Customer Managed|AWS Managed|
    |FIPS 140-2|Level 3|Level 2|
    |3rd Party Support|Broad 3rd party|Broad AWS|