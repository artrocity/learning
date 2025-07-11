IP Addresses

- EC2 instances are similar to an apartment in a building. Just as an apartment can have different addresses and phone numbers, so can an instance
- EC2 instances have addresses called IP addresses which serve different functions
    
    - Public IP Addresses
        
        - These are like a publicly listed address and that anyone can use to find you
        - It's reachable from the internet
        - The address is drawn from a pool of Amazon's IPv4 addresses
        - If you start and stop your instance, the Public IP address will most likely change
        - There's no charge for public IP addresses when associated with a running instance
    - Private IP Addresses
        
        - These are like an internal apartment number that only other residents can use - a gated community
        - They only work within your VPC
        - They're assigned from the IP address range you chose for your VPC
        - They stay with the instance even when you stop and start it
        - They're essential for internal communication between AWS resources
        - They follow RFC 1918 standards
    - Elastic IP Addresses
        
        - These are like having your own dedicated phone number, when you move apartments, you can take the number with you
        - They're static public IPv4 addresses
        - Can associate them with any instance in your account
        - They remain yours until explicitly released by you
        - Small cost if they're not associated with an instance
        - Limited number of Elastic IP addresses per account
        - They're perfect for applications that need a fixed, reliable IP Address
    - Example
        
        - Users connect to your web server via a Public IPv4 Address (Either Public or Elastic)
        - The server will also have a network interface allowing it to have a Private IP Address so it can communicate with your database server
        - The database will only have a private IP address as it doesn't need to talk to the outside world