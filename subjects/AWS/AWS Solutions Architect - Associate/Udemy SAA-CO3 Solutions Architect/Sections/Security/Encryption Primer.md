Encryption Overview

- Encryption In-transit
    
    - Encrypting data as it traverses a network
    - Example: HTTPS , data is encrypted and protected by SSL/TLS certificate in transit
    - It's only encrypted while it's in transit. The data itself may not be encrypted
- Encryption At-rest
    
    - Data is encrypted prior to storing
    - Example: Amazon S3 encrypts the data as it's written to the bucket
- Asymmetric Encryption
    
    - Known as public key cryptography
    - Messages encrypted with a public key and can only be decrypted with a private key
    - Messages encrypted with a private key can be decrypted with a public key
    - Examples include:
        
        - SSH
        - SSL/TLS
- Symmetric Encryption
    
    - Plain text data is passed through an encryption process and you receive data
    - The same key is used for both encryption and decryption