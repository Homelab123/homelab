#Step 16 - Linux Webapp VM

- Linux VM was previously installed and joined to domain
- Ran sudo ssh-keygen -A to generate keys so I can connect via SSH
- Ran sudo apt update && sudo apt upgrade -y
- Ran sudo apt install apache2 mysql-server php libapache2-mod-php php-mysql -y
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
- (to be continued)
