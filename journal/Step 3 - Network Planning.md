#Step 3 - Network Planning

As I was preparing VMs and making templates I realized I should do the network/address planning first in order to build templates which are pre-configured to point to the domain controller.
So, I saved where I was at on my template and decided to plan the network before continuing. At first I wanted to make a complex network with multiple subnets emulating a large international enterprise, but for the 
purposes of a homelab I decided to scale it down and keep it simple.

I will create 3 subnets and VLANs and a router VM with a trunked NIC:
- 10.0.0.0/24: VLAN10 // DC01, LIN-WEBAPP01, LIN-MONAUTLOG01
- 10.0.1.0/24: VLAN20 // FS01, BK01
- 10.0.2.0/25: VLAN30 // WIN10, WIN11 (clients)
