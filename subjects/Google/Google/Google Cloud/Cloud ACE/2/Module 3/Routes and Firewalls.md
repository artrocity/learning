Every Google Network has

- Routes that let instances in a network send traffic to each other
- Default route that directs packets to destinations outside of the network
    
    - Has default rules to allow all resources to talk to each other
- Manually created networks do not come preconfigured
    
    - You must manually create all firewall rules to allow internal traffic to talk
- Routes map traffic to destination networks
- Firewall rules
    
    - Traffic is only delivered if it also matches a firewall rule
    - VPC networks function as a distributed firewall
    - Connections are allowed or denied at the instance level
    - Firewall rules are stateful
    - Firewall rules are applied to the network as a whole
- Firewall rule is comprised of
    
    - Direction
    - Source or destination
    - Protocol and Port
    - Action
    - Priority
    - Rule assignment