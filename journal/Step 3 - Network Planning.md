#Step 3 - Network Planning

As I was preparing VMs and making templates I realized I should do the network/address planning first in order to build templates which are pre-configured to point to the domain controller.
So, I saved where I was at on my template and decided to plan the network before continuing. At first I wanted to make a complex network with multiple subnets emulating a large international enterprise, but for the 
purposes of a homelab I decided to scale it down and keep it simple.

I will create 2 VLANs and 2 subnets for servers and clients:

Subnet1:  10.0.0.0/24 (VMnet2)
Subnet2: 10.0.1.0/25 (VMnet3)

VLAN1: 10.0.0.0/24
VLAN2: 10.0.1.0/25

I will then have to create a router VM to route between subnets. It will use a trunked NIC so it can carry multiple VLANs using 802.1Q tagging and a 2nd NIC for default route to internet via host (VMware NAT).

eth0.10 → VLAN10 / 10.0.0.1/24
eth0.20 → VLAN20 / 10.0.1.1/25

These will be the default gateways for machines in thoese respective subnets
