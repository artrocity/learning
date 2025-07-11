IP Addressing

- Structure of an IPv4 address
    
    - Written in dotted decimal notation
        
        - 192.168.0.1
    - Each part of the address is a binary octet
- Network ID
    
    - 19.168.0
    - Provided by Subnet mask
- Host ID
    
    - The last octet of an IP address
    - In the above example it's a 1
- Subnet Mask
    
    - Masks the components of the IP address
    - Used to define the network and host ID
    - Most of the time the network and subnet mask are written in the following format
        
        - 192.168.0.0/24 - 24 stands for the bits used in the subnet mask
        - If the subnet mask is 255.255.255.0 then the first 3 octets are all 1s.
        - This means there are 24 bits
- IP Address Ranges
    
    - Private
        
        - 10.0.0.0 - 10.255.555.555
            
            - Allows for a significant amount of hosts
        - 172.16.0.0 - 172.31.255.255
        - 192.168.0.0 - 192.168.255.55