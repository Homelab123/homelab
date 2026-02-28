#Step 18 - Linux Automation/Logging/Monitoring server

Previously already installed Ubuntu and joined to domain, continuing:

- added NAT NIC for temporary convenience
- sudo ip link set ens33 down
- sudo ip link set ens37 up
- sudo dhclient ens37
- ping 8.8.8.8
- sudo apt update && sudo apt upgrade -y
- sudo ssh-keygen -A
- sudo apt install openssh-server -y
- sudo systemctl enable ssh
- sudo systemctl start ssh

Planning:
- Install Wazuh
- Setup Prometheus + Node exporter
- Connect Grafana to both
- Install Ansible

Wazuh:
- curl -sO https://packages.wazuh.com/4.10/wazuh-install.sh
- sudo bash wazuh-install.sh -a
- expanded VM storage disk due to not enough space error
- expanded volume to 100gb
- sudo lvextend -l +100%FREE /dev/ubuntu-vg/ubuntu-lv && sudo resize2fs /dev/ubuntu-vg/ubuntu-lv && df -h
- re-ran install
- You can access the web interface https://<wazuh-dashboard-ip>:443
- User: admin
- Password: avi9u?Wu?Da08qRkMCH1OpsXGf4X+A8o
- 28/02/2026 13:50:21 INFO: Installation finished.
