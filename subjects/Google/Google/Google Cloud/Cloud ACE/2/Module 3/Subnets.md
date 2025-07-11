Think of an IP address like a street address:

- /16 = City level (huge area, lots of addresses)
- /20 = Neighborhood level (medium area)
- /24 = Street level (smaller area)
- /29 = House level (very few addresses)

The bigger the number after /, the smaller the network:

- /16 = 65,536 IP addresses
- /20 = 4,096 IP addresses
- /24 = 256 IP addresses
- /29 = 8 IP addresses

Real-world analogy: Imagine a postal code system:

- /16 = First 2 digits (large area like "90---")
- /20 = First 3 digits (smaller area like "901--")
- /24 = First 4 digits (even smaller like "9011-")
- /29 = All 5 digits (very specific like "90112")

Common Uses:

- /16: Large corporate networks
- /20: Medium business networks
- /24: Small office networks
- /29: Tiny networks, like between few devices

**The key thing to remember: The bigger the number, the fewer IP addresses available.**
 
Subnet Calculation
 
There's a simple formula to calculate the number of available IP addresses in a subnet:  
Formula: 2^(32 - subnet mask) = Number of IP addresses  
Example calculations:
 
==/16: 2^(32-16) = 2^16 = 65,536 addresses====￼====/20: 2^(32-20) = 2^12 = 4,096 addresses====￼====/24: 2^(32-24) = 2^8 = 256 addresses====￼====/29: 2^(32-29) = 2^3 = 8 addresses==  
Simple way to think about it:

1. Start with 32 (total bits in IPv4)
2. Subtract the subnet number (like 16, 24, etc.)
3. The result is your power of 2

Quick reference:

- Each time you increase the subnet number by 1, you halve the available addresses
- Each time you decrease it by 1, you double the addresses