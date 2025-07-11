S3 Encryption

- Few encryption options
    
    - Server-side (S3 Service - AWS Managed)
        
        - Secured at rest
        - Decrypted when you download it
    - Server Side Encryption - KMS
    - Server side Encryption with Client provided keys
    - Client-side encryption
- S3 Buckets have encryption enabled by default
- No additional cost
- Objects are automatically encrypted using AWS S3 Managed Keys SSE-S3
- You can encrypt via Copy API Command or Bucket Policies