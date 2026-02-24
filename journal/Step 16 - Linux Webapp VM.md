#Step 16 - Linux Webapp VM

- Linux VM was previously installed and joined to domain
- Ran sudo ssh-keygen -A to generate keys so I can connect via SSH
- Ran sudo apt update && sudo apt upgrade -y
- Ran sudo apt install apache2 mysql-server php libapache2-mod-php php-mysql -y

Troubleshoot section:
- Changed pfSense VM settings due to connection drops:
  - Increased RAM
  - ethernet0.virtualDev = "vmxnet3" (changed from e1000)
  - ethernet1.virtualDev = "vmxnet3" (changed from e1000)
  - ethernet2.virtualDev = "vmxnet3" (changed from e1000)
  - Disabled hardware checksum offload
  - Disabled hardware TCP segmentation offload
  - Disabled hardware large receive offload
- Ran sudo apt update && sudo apt upgrade -y again
- Ran sudo apt install apache2 mysql-server php libapache2-mod-php php-mysql -y again
- It was still too slow and causing problems, added a NAT NIC to the linux vm
- sudo ip link ens33 set down
- sudo ip link ens37 set up
- sudo dhclient ens37
- ping 8.8.8.8
- Ran sudo apt update && sudo apt upgrade -y, this time it was much faster and without issues
- Ran sudo apt install apache2 mysql-server php libapache2-mod-php php-mysql -y, this step was also faster and successful

Continuing:
- securing sql: sudo mysql_secure_installation
- allow SSH: sudo ufw allow OpenSSH
- allow Apache Full: sudo ufw allow 'Apache Full'
- enable firewall: sudo ufw --force enable
- checking status: sudo ufw status
- test web page: echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php
- ensure owner: sudo chown -R $USER:$USER /var/www/html
- ensure permissions: sudo chmod -R 755 /var/www/html
- restarted service: sudo systemctl restart apache2
- restarted service: sudo systemctl restart mysql
- Tested test-page http://192.168.91.137/info.php --- successful
- Reverting previous NIC changes
- sudo ip link set ens37 down
- sudo ip link set ens33 up
- ip a
- reboot
- reverted pfSense's NIC's back to e1000

Network troubleshooting:
- Noticed I can only ping my pfSense from 1 vm at a time after reboots, troubleshooting now
- Double checked my NICs of all VMs are correct
- Logged into pfSense > Enabled DHCP and static ARP for subnet 1 machines so that ARP table doesn't cause issues
- Enabled Static ARP and DHCP reservations for LAN, (DC01, FS01, BK01, LIN-WEBAPP-01, LIN-AUTOLOGMON-01). Linked their MAC address to a static address with static ARP
- Issue is gone so far

Continuing:
- Brought pfSense, DC01 and LIN-WEBAPP-01 on, tested if I could access the web page from DC01 - working
- Brought down DC01 and brought up WIN10-01 (different subnet), tested web page access - working
