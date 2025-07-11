AWS KMS

- Used to create and manage encryption keys
- Keys can be symmetric or asymmetric
- Keys are protected by hardware security modules
- There are 2 main types of keys
    
    - Customer Managed - customer creates and manages
    - AWS Managed - AWS creates and manages
        
        - Can be used with certain services
        - AWS KMS integrates with several services such as:
            
            - SQS
            - ACM
            - EBS
            - FSx
        - You cannot manage these KMS keys, rotate them, or change them
        - You can't use AWS managed KMS keys in cryptographic operations directly. The service that creates them uses them on your behalf
- KMS key contains the key material used to encrypt and decrypt data
- By default, KMS creates the key material for a KMS key
- You can also import your own key material
- KMS can only encrypt data up to 4kb per second
- Data Encryption Keys
    
    - Data encryption keys are used to encrypt larger files
    - You can use KMS to generate, encrypt and decrypt data keys
    - KMS doesn't store, manage, or track these data keys
    - Data keys must be used and managed outside of KMS
- External Key Stores
    
    - Keys can be stored outside AWS
    - You can create a KMS key in AWS KMS external key store (XKS)
    - All keys are generated and stored in an external key manager
    - When using XKS, key material never leaves your HSM
- Custom Key Stores
    
    - Create KMS keys in AWS CloudHSM custom key store
    - All keys are generated and stored in an AWS CloudHSM cluster that you own and manage
    - Cryptographic operations are performed solely in the AWS CloudHSM cluster you own and manage
    - Custom Key Stores are not available for asymmetric KMS keys
- KMS Key Rotations
    
    - |   |   |   |   |   |
        |---|---|---|---|---|
        |Type of Key|Can View|Can Manage|Used Only for My AWS Account|Automatic Rotation|
        |Customer Manage Key|Yes|Yes|Yes|Optional - Every 365 Days|
        |AWS Managed Key|Yes|No|Yes|Required - Every 365 Days|
        |AWS Owned Key|No|No|No|Varies|
        
- Manual Key Rotation
    
    - Manual rotation is creating a new KMS key with a different ID
    - You must then update your apps with the new Key ID
    - You can use an alias to represent the keys
- KMS Key policies
    
    - Key policies define the management and usage permissions for KMS keys
    - Multiple policy statements can be combined to specify separate admin and usage permissions
    - Grants - Permissions can be specified for delegating use of the key to services.
- Exam Tips
    
    - To share snapshots with another account - you must specify the decrypt and create grant permissions
    - The kms Via Service condition key can be used to limit key usage
    - Cryptographic erasure means removing the ability to decrypt data
    - InvalidKeyId exception when using SSM parameter store indicated the key isn't enabled