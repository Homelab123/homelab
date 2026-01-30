#Step 03 - Network Planning

As I was preparing VMs and making templates I realized I should do the network/address planning first in order to build templates which are pre-configured to point to the domain controller.
So, I saved where I was at on my templates and decided to plan the network before continuing. At first I wanted to make a complex network with multiple subnets emulating a large international enterprise, but for the 
purposes of a homelab I decided to scale it down and keep it simple.

I will create 2 VLANs and 2 subnets for servers and clients:

Subnet1:  10.0.0.0/24 (VMnet2)
<br>
Subnet2: 10.0.1.0/25 (VMnet3)

VLAN1: 10.0.0.0/24
<br>
VLAN2: 10.0.1.0/25

Because I'm using VMware Workstation Pro 25h2, I will need an extra VM to do the routing between those subnets since I don't have a configurable inter-vm routing feature on workstation.

I've explored options for this purpose and chose to create a VM with a FortiGate image since it seems to be widely used in Quebec/Canada.

Downloaded FGT_VM64-v7.6.5.M-build3651-FORTINET.out.ovf from Fortigate's official website.

VMs:
- DC01 (DNS/AD):                        10.0.0.10/24  VLAN1
- DC02 (for replication):               10.0.0.11/24  VLAN1 (maybe later)
- FS01 (Fileshare):                     10.0.0.20/24  VLAN1
- BK01 (Backup server):                 10.0.0.30/24  VLAN1
- LIN-WEBAPP-01 (web/app serv):         10.0.0.40/24  VLAN1
- LIN-AUTLOGMON-01 (log/mon/auto):      10.0.0.50/24  VLAN1

- WIN10 (workstation):                  10.0.1.10/25  VLAN2
- WIN11 (workstation):                  10.0.1.11/25  VLAN2

- FGT01 (router):
  - port1 (WAN):        DHCP or static
  - port2 (VLAN1):      10.0.0.1/24
  - port3 (VLAN2):      10.0.1.1/25

The router VM will attribute static addresses to the servers and dynamic addresses to the workstations for the purpose of practicing both in this homelab.

This might change as I develop the homelab further but I will start with this.
