#Step 10 - Network troubleshooting

I currently have all my VMs setup but I am having communication issues due to fortigaet configuration most likely so I will go ahead to troubleshoot so that machines can talk to each other through different subnets and to the internet.

- Verified VMware network editor:
  - VMnet2: Host-only / Subnet IP:10.0.0.0  Subnet mask: 255.255.255.0 (VLAN1)
  - VMnet3: Host-only / Subnet IP:10.0.1.0  Subnet mask: 255.255.255.128 (VLAN2)
  - VMnet8: NAT (for fortigate to go through host to talk to internet) / Subnet IP 192.168.91.0 Subnet mask 255.255.255.0
- Verified all VM network adapter settings:
  - FGT01 (fortigate router vm):
    - Adapter 1: NAT
    - Adapter 2: VMnet2 (VLAN1)
    - Adapter 3: VMnet3 (VLAN2)
  - DC01, FS01, BK01, LIN-WEBAPP-01, LIN-AUTLOGMON-01: VMnet2 (VLAN1)
  - WIN10-01, WIN11-01: VMnet3 (VLAN2)
  - 
