#Step 17 - pfSense VM recap before deletion

Since I've explored pfSense enough to have my things work in comprtaments, I will be deleting the pfSense vm and putting everything on the same network in VMWare Workstation Pro because the limited features of workstation pro and how pfsense interacts with it and my machines makes it very hard to work with and I am fighting it most of the time due to limitations.

- NIC1/NAT: WAN - DHCP address given by host
- NIC2/VMnet2: LAN (VLAN10) - 10.0.0.1/24
- NIC3/VMnet3: OPT1 (VLAN20) - 10.0.1.1/25

- Disabled offload cheksum

Addresses:
- LAN:
- 10.0.0.10  (VM MAC)  DC01              Static  Reserved  Static ARP
- 10.0.0.20  (VM MAC)  FS01              Static  Reserved  Static ARP
- 10.0.0.30  (VM MAC)  BK01              Static  Reserved  Static ARP
- 10.0.0.40  (VM MAC)  LIN-WEBAPP-01     Static  Reserved  Static ARP
- 10.0.0.50  (VM MAC)  LIN-AUTLOGMON-10  Static  Reserved  Static ARP

- OPT1:
- DHCP Range: 10.0.1.20-10.0.1.100 /24

Firewall rules:
- LAN subnets > OPT1 subnets: pass
- LAN subnets > WAN: pass
- OPT1 subnets > LAN subnets: pass
- OPT1 subnets > WAN: pass
- VLAN10 > VLAN20: pass
- VLAN10 > WAN: pass
- VLAN20 > VLAN10: pass
- VLAN20 > WAN: pass

Specs:
- RAM: 1GB
- Processors: 4
- DISK: 20 GB

Lessons learned:
- VMware workstation pro limitations (no promiscuous mode, no inter subnet routing)
- GUI lockouts when assigning VLANs to interfaces
- Alterning ping issues due to dynamic ARP issues for VMs
