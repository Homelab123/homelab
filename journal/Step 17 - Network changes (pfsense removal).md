#Step 17 - Network changes (pfsense removal)

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
- Subnet IP: 10.0.0.0/24, Gateway: 10.0.0.1, DHCP on, range: 10.0.0.20-10.0.0.100
- Going through each VM to match the new network
