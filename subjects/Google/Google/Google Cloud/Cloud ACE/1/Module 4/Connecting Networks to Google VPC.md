Cloud VPN

- Connecting networks to Google VPC
- Uses Cloud Router to make connections dynamic
- Allows other networks and Google VPC exchange route information over the VPN using the Border Gateway Protocol
 
Direct Peering

- Puts a router in the same public datacenter as a Google Point of Presence (PoP)
- Uses a router to exchange traffic between networks
- More than 100 POPs around the world

￼Carrier Peering

- Gives direct access from an on-premises network through a service provider network
- Not covered by Google Service Level Agreement
 
Dedicated Interconnect

- Allows one or more direct connections to Google
- Covered by 99.99% SLA
- Connection can be backed up by VPN
 
Partner Interconnect

- Useful is a physical location cant reach a Dedicated interconnect colocation facility
- Useful if data needs don’t warrant 10 Gigabytes Per Second connection
 
Cross-Cloud Interconnect

- Establish high-bandwidth connectivity between Google Cloud and another Cloud Service Provider
- 10 or 100 Gbps connection