# Step 2 - Windows Server

Choice: Windows Server 2022 from Microsoft's evaluation center
Reasoning:
- Free for a limited time but can reset activation with a checkpoint for the purposes of a homelab.
- Had to find a good balance between what is widely adopted in organizations currently and what is the most up to date (2025 is too recent, less people use it. 2019 is older than 2022 and not necessarily more used)
- Industry standard, widely adopted.

<br>Technical Steps taken:
- Downloaded Windows Server 2022 eval. 64-bit (english_US) ISO file from Microsoft's official website
- Changed VMware preferences so that VMs are stored in my storage disk and not my NVMe for resource allocation efficiency reasons (no need to store large virtual disks on my NVMe that I use on my main PC)
- Created VM with these settings for now:
![Homelab123](https://github.com/Homelab123/homelab/blob/main/screenshots%20/WindowsServer2022%20-%20Create%20VM.png?raw=true)
