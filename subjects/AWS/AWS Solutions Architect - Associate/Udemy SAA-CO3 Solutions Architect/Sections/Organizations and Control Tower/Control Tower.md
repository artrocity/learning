AWS Control Tower

- Control Tower sits on top of Organizations
- With control tower you're able to create landing zones
- Landing Zone
    
    - A Landing Zone is a well architected multi-account baseline
- Guardrails
    
    - Preventive Guardrails
        
        - Preventive Guardrails which disallow API actions using SCP
        - Designed to proactively prevent policy violations before they occur.
        - Enforce compliance and security best practices by restricting actions
        - How they work:
            
            - Implemented by SCPs to limit what actions a user can perform
    - Detective Guardrails
        
        - Detective Guardrails are used for governance and compliance
        - Designed to monitor and report policy violations or non-compliant activities
        - Help Identify misconfigurations
        - How they work:
            
            - Implemented using Config Rules and Lambda functions.
            - They continuously evaluate the configuration of AWS resources and generate alerts when non-compliance is detected
- Directory Source
    
    - Can be:
        
        - IAM Identity Center
        - SAML 2.0
        - Microsoft AD
- Share Accounts
    
    - Management Account
        
        - The management account (root user) is used to launch AWS Control Tower
    - Log Archive Account
        
        - Contains central AWS S3 Bucket for storing a copy of all AWS CloudTrail and AWS Config Files for all other accounts in the landing zone
    - Audit Account
        
        - Aggregates and stores logs collected from other accounts. Secure account with restricted access