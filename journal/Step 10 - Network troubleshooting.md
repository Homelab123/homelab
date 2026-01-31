#Step 10 - Network troubleshooting

I currently have all my VMs setup but I am having communication issues due to fortigaet configuration most likely so I will go ahead to troubleshoot so that machines can talk to each other through different subnets and to the internet.

- Verified VMware network editor:
  - VMnet2: Host-only / Subnet IP:10.0.0.0  Subnet mask: 255.255.255.0 (VLAN1)
  - VMnet3: Host-only / Subnet IP:10.0.1.0  Subnet mask: 255.255.255.128 (VLAN2)
  - VMnet8: NAT (for fortigate to go through host to talk to internet) / Subnet IP 192.168.91.0 Subnet mask 255.255.255.0
- Verified all VM network adapter settings:
  - FGT01 (fortigate router vm):
    - Adapter 1: NAT (port1)
    - Adapter 2: VMnet2 (VLAN1) (port2)
    - Adapter 3: VMnet3 (VLAN2) (port3)
  - DC01, FS01, BK01, LIN-WEBAPP-01, LIN-AUTLOGMON-01: VMnet2 (VLAN1)
  - WIN10-01, WIN11-01: VMnet3 (VLAN2)
- Verified VMs can ping FGT01 and FGT01 can ping the internet but VMs can't reach internet or the other subnets

The problem is that FortiGate's free VM has a limit of 3 firewall policies, so I must broaden policies to match what I'm trying to do with a limit of 3 rules.

After exploring options, there is no way to get around the 3 policy limit and acheive what I am trying to acheive which is:
Clients to servers
Clients to WAN
Servers to Clients
Servesr to WAN

Therefore, I have decided to keep servers without a route to internet and keep them internal, and in the context of the homelab, if there ever was a need to update or reach internet, I can set servers to NAT with the vmware host directly while I run things like updates and revert to internal after updates.
