#Step 3 - VM prep

For the purpose of this homelab I will need a domain controller (DC), fileshare server (FS), and a backup server (BK).
Since I have a Windows Server fully updated with general performance tweaked with snapshots, I will clone this VM to have 3.

- Cloned "Windows Server 2022" into 3 FULL clone VMs: DC01 (domain controller), FS01 (fileshare), BK01 (backup)
- Loaded the 3 VMs to make sure it works as intended
- Archived "Windows Server 2022" VM as a template for future use and removed it from my VM list (Removed from VMware list and moved the VM files to "S\Homelab\Virtual Machines\VM Templates"
- Downloaded Win10 and Win11 client ISO's from Microsoft and created 2 Windows client VMs
- Loaded Win10-01 and ran full updates/restarts + created snapshot
- Loaded Win11-01 and ran full updates/restarts + created snapshop


Current Vms:
DC01 (domain controller)
FS01 (fileshare)
BK01 (backup)
Win10-01 (Windows 10 Pro client)
Win11-01 (Windows 11 Pro client)
