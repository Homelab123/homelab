#Step 11 - pfSense VM

- Downloaded ISO via Netgate
- Created VM and went through installation
- Added network adapters, configured interfaces and added VLANs:

  - WAN > em0 > v4/DHCP: 192.168.91.136/24
  - LAN > em1 > v4: 10.0.0.1/24 --- (VLAN 10 - Servers)
  - OPT1 > em2 > v4: 10.0.1.1/25 --- (VLAN 20 - Clients)

DHCP server is enabled on em2 for clients (range 10.0.1.20-10.0.1.100)

- Blocked RFC 1918 nework and bogon networks for the WAN interface
- Logged to 10.0.0.1 via browser from DC from LAN and added VLANs via GUI to em1(VLAN10) and em2(VLAN20)
- Testing ping from different machines
- Added firewall rule to allow ICMP traffic from OPT1 subnets to OPT1 interface
- Confirmed I can ping from DC to WIN10 and vice versa
- Confirmed tracert is showing correct routing
- Confirmed I can ping 8.8.8.8 from DC and WIN10 vms
- Double checked VMs IP configurations to make sure everything is right
