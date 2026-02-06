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
  
- Setting up LIN-WEBAPP-01:
  - Enabled interace ens33:
    - sudo ip link set ens33 up
  - Configured netplan:
    - sudo nano /etc/netplan/01-netcfg.yaml:
    - network:
    - version: 2
    - renderer: networkd
    - ethernets:
    - ens33:
    - addresses:
      - 10.0.0.40/24
    - gateway4: 10.0.0.1
    - nameservers:
    - addresses:
      - 10.0.0.10
  - installed realmd:
    - sudo apt install realmd
  - discovered domain:
    - realm discover corp.lab
  - Joined domain:
    - sudo realm join corp.lab -U Administrator
    - prompted to install dependancies:
      - sudo apt update
      - sudo apt install -y ldap-utils libnss-sss libpam-sss sssd-ad adcli oddjob oddjob-mkhomedir packagekit
      - retried domain join
      - verified:
        - realm list
        - id corp\\administrator
      - tried logging with corp\administrator:
        - su - corp\\administrator
      - fixed some firewall issues cause linux VM wasn't pinging
      - installed krb5-user:
        - sudo apt install krb5-user
        - ran klist to confirm kerberos ticket
      - added administrator@corp.lab to sudoers:
        - sudo nano /etc/sudoers
        - added administrator@corp.lab ALL=(ALL:ALL) ALL
        
- Setting up LIN-AUTLOGMON-01: I did the same as above but the ip address is 10.0.0.50/24

Will continue later.
