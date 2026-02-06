#Step 12 - Domain Join

I will now join each VMs to the domain and double check configs and makes sure everything is domain-joined before installing roles etc.

- Renamed DC pc name to DC01
- The DC machine name was a default windows machine name which I wanted to change, so I changed it to DC01 but I had to demote the DC and create a new one with the new name
- Logged on the local administrator accoutn and demoted DC
- Rebooted and confirmed I have the name I want (DC01)
- Created temporary firewall rule to allow clients to talk to DC:
  - Pass | IPv4 | Source: OPT1 subnets | Destination: LAN subnets | any ports
- Joined WIN10-01 to domain corp.lab and rebooted --- confirmed working by logging under corp\administrator account
- Did the same for WIN11-01
- Renamed the FS01 machine from default to FS01 and joined it to the domain in the same way
- Did the same for BK01
- 
