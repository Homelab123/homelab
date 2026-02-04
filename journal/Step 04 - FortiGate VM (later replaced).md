#Step 04 - FortiGate VM

Since it's the first time I use FortiGate specifically I will go along this video series: https://www.youtube.com/watch?v=XcghOBrZANc&list=PLlEVCBdM7ELOSd9zLJNE3FrIMzZiWlSkm

- Created VM with:
  - 1 vCPU x 1 core (FortiGate license limit for free use)
  - 2gb RAM
  - Deleted all NIC except 3:
    - WAN (NAT)
    - Custom (VMnet2 aka VLAN1)
    - Custom (VMnet3 aka VLAN2)

Port config:

Port2: (VLAN1)
config system interface
edit port2
set ip 10.0.0.1/24
set allowaccess ping https ssh
set alias "VLAN1-Servers"
next

Port3: (VLAN2)
edit port3
set ip 10.0.1.1/25
set allowaccess ping
set alias "VLAN2-Clients"
next

Port1: (WAN, NAT with my host)
edit port1
set mode dhcp
set allowaccess ping
set alias "WAN"
next
end

Setting up DHCP on the interface of port 3 for dynamic addresses for clients:
config system dhcp server
edit 1
set interface port3
set netmask 255.255.255.128
set default-gateway 10.0.1.1
set dns-service specify
set dns-server1 10.0.0.10
set domain "corp.lab"
config ip-range
edit 1
set start-ip 10.0.1.20
set end-ip 10.0.1.100
next
end
next
end

Enabling VLAN2 to reach the internet (clients to internet):
config firewall policy
edit 1
set name "Clients_to_Internet"
set srcintf port3
set dstintf port1
set srcaddr all
set dstaddr all
set action accept
set schedule always
set service ALL
set nat enable
next
end

