#Step 11 - pfSense VM (later modified)

- Downloaded ISO via Netgate
- Created VM and went through installation
- Added network adapters and configured interfaces:

WAN > em0 > v4/DHCP: 192.168.91.136/24
LAN > em1 > v4: 10.0.0.1/24
OPT1 > em2 > v4: 10.0.1.1/25

DHCP server is enabled on em2 for clients (range 10.0.1.20-10.0.1.100)

- Blocked RFC 1918 nework and bogon networks for the WAN interface

While doing this, I've thought and decided that I want to introduce VLANs in my homelab for practice purposes and will have to modify my network scheme.
