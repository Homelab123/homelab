#Step 17 - Network changes

After all I've done before with this setup, I was able to explore routing via pfsense, firewall rules, VLANs, different types of features, DHCP on router interface, etc.

Due to VMware workstation pro, my main PC, and pfsense limitations, I will have to remove pfsense and bring everything on the same virtual network directly in VMware Worksation Pro so I can continue this homelab. The current setup causes many issues such as network interruptions, limitations in how NICs and the pfsense interact causing VMs to only be able to connect 1 at a time, etc.

Last recorded configurations were:

WAN: em0 -> DHCP/24
LAN: em1 -> 10.0.0.1/24 (Subnet 1 gateway interface)
OPT1 em2 -> 10.0.1.1/25 (Subnet 2 gateway interface)

VLAN10 on Subnet1
VLAN20 on Subnet20

Firewall rules allowing Subnet1 to Subnet 2 and Subnet1 to WAN
Firewall rules allowing Subnet2 to Subnet1 and Subnet2 to WAN

Now removing pfSense and changing network configuration on all the VMs:

- VMnet2 and 3 deleted
- VMnet8 (NAT) settings:
- Subnet IP: 192.168.202.0/24, Gateway: 192.168.202.2, DHCP on, range: 192.168.202.100 - 192.168.202.200
- Going through each VM to match the new network:
- DC01: 192.168.202.10/24 - done
- FS01: 192.168.202.20/24 - done
- BK01: 192.168.202.30/24 - done
- Added DHCP role to DC01 and configured scope
- WIN10-01: DHCP - done
- WIN11-01: DHCP - done
- LIN-WEBAPP-01 - done
- LIN-AUTLOGMON-01 - done
- Tested all pinging both gateway, internet and DC
