#Step 12 - Back to Network Planning

As mentioned in the previous step, I've decided to introduce VLANs for hands-on practice in the context of my homelab so I will review and change my network scheme:

Servers: Subnet 10.0.0.0/24
  - Core: VLAN 10
    - DC01
    - FS01
    - BK01

  - "Internet-facing": VLAN 20
    - LIN-WEBAPP-01

  - Admin tools: VLAN 30
    - LIN-AUTLOGMON-01

Clients: Subnet 10.1.0.0/25 & VLAN 100
  - WIN10-01
  - WIN11-01

pfSense:
-  
