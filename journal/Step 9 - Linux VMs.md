#Step 9 - Linux VMs

I have decided to finish setting up my VMs before I start troubleshooting network and make sure everything is talking to each other.
I will add 2 linux VMs:

LIN-WEBAPP-01: will be used for web services like (Nginx/Apache, apps, maybe Docker later).
LIN-AUTLOGMON-01: will be used for Automation (cron/Ansible later) / Logging & monitoring (rsyslog, Prometheus, Grafana, etc.)

Will create a template first:
- 2 vCPU x 2 cores
- 4gb ram
- 40gb storage

Installation:
- Default installation
- Leaving DHCP address for template
- No proxy and default mirror
- Default disk options (use entire disk + LVM group)
- Skipped Ubuntu Pro for now
- Installed OpenSSH server
- Skipped Featured server snaps
- Ran install
- Reboot
- Logged under administrator
- Ran updates: 
  - sudo apt update
  - sudo apt full-upgrade -y
  - sudo reboot
- Installed vmware tools:
  - sudo apt install -y open-vm-tools open-vm-tools-desktop
  - sudo reboot
- Installed basic common tools:
  - sudo apt install -y \
    -  vim curl wget git htop net-tools \
    -  unzip bash-completion \
    -  ca-certificates gnupg lsb-release
- timedatectl shows clock is synchronized and NTP service is active
- Enabled firewall // allowed SSH first:
  - sudo ufw allow OpenSSH
  - sudo ufw enable
  - sudo ufw status
  - confirmed it's active and at ALLOW / Anywhere
- Changed PermitRootLogin to no in /etc/ssh/sshd_config
- sudo systemctl restart ssh
- locked root account sudo passwd -l root

Cleanup:
- Reset machine identity:
  - sudo truncate -s 0 /etc/machine-id
  - sudo rm -f /var/lib/dbus/machine-id
- Removed SSH host keys: 
  - sudo rm -f /etc/ssh/ssh_host_*
- Clean cloud-init state:
  - sudo cloud-init clean
- Shutdown vm:
  - sudo shutdown -h now

- Cloned to LIN-WEBAPP-01 and LIN-AUTLOGMON-01 and stored LIN-TEMPLATE to VM template storage folder
- Adjusted VM hardware for each machines

LIN-WEBAPP-01:
- Changed hostname:
  - sudo hostnamectl set-hostname LIN-WEBAPP-01
  - changed hostname in /etc/hosts to 127.0.1.1 LIN-WEBAPP-01
- Rebooted
- Changed network config:
  - sudo nano /etc/netplan/00-installer-config.yaml:
    - network:
    - version: 2
    - ethernets:
    - ens18:
    - dhcp4: no
    - addresses:
    - - 10.0.0.40/24
    - gateway4: 10.0.0.1
    - nameservers:
    - addresses:
    - - 10.0.0.10
- Changed permissions: sudo chmod 600 /etc/netplan/00-installer-config.yaml

LIN-AUTLOGMON-01: did the same as above but changed its address for 10.0.0.50/24
