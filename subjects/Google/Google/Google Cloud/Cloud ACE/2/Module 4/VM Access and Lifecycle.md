VM Access

- Linux: SSH
    
    - SSH from the Google Cloud Console or Cloud Shell via SDK
    - SSH from computer
    - Requires firewall rule TCP: 22
- Windows: RDP
    
    - RDP Clients
    - PowerShell terminal
    - Requires Windows Password
    - Requires firewall rule TCP: 3389
 
VM Lifecycle

- Provisioning
    
    - CPU & memory and disks are being reserved
- Staging
    
    - Resources have been acquired, IP addresses have been assigned, system is booting
- Running
    
    - Preconfigured Startup scripts
    - SSH/RDP Enabled
- Stop
    
    - Goes through preconfigured shut down states
    - Option to reset, delete, or start
- Reset
    
    - Wipes machine and sets to initial state
- Repair state
    
    - Underlying machine is unable due to maintenance
    - Not billed during repair state