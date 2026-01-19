#Step 3 - Cloning Windows Server

For the purpose of this homelab I will need a domain controller (DC), fileshare server (FS), and a backup server (BK).
Since I have a Windows Server fully updated with general performance tweaked with snapshots, I will clone this VM to have 3.

1. Choose VM > clone
2. Choose FULL clone to make them independant
3. Will do this for 3 VMs: DC01, FS01 and BK01, and keep the original VM in its current clean state to save it as a "template".
