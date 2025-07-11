AWS WAF

- AWS Web application Firewall
- WAF lets you create rules to filter web traffic based on conditions
- Used for protecting against block common web exploits, SQL injection and cross site scripting
- Web ACLs
    
    - Web access control list used to protect resources
    - Rules
        
        - Each rule contains a statement that defines the inspection criteria
    - Rule groups
        
        - Used to group rules
    - IP sets
        
        - An IP set provides a collection of IP ranges that you want to use in a rule group
    - Rule Action
        
        - Tells WAF what to do when matches are made in a rule
        - Types
            
            - Count - Count types coming in
            - Allow - Forward Traffic
            - Block
- Match Statement
    
    - Compare the web request against conditions that you provide
    - Geo Matches
    - IP Matches
    - Regex Matches
    - Size Constraints
    - SQLi Attack
    - String Attack
    - XSS attacks