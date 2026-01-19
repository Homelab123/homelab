#Step 3 - VM prep

For the purpose of this homelab I will create:
- DC01 (domain controller)
- FS01 (fileshare)
- BK01 (backup)
- Win10-01 (Windows 10 Pro client)
- Win11-01 (Windows 11 Pro client)
- LINUX01 (app/web server)
- LINUX02 (monitoring/automation server)

I have previously created a Windows Server 2022 VM, fully updated and tweaked it with a few performance tweaks and installed VMware Tools on it. Next steps taken:
- Cloned "Windows Server 2022" into 3 FULL clone VMs: DC01 (domain controller), FS01 (fileshare), BK01 (backup)
- Loaded the 3 VMs to make sure it works as intended
- Archived "Windows Server 2022" VM as a template for future use and removed it from my VM list (Removed from VMware list and moved the VM files to "S\Homelab\Virtual Machines\VM Templates"
- Downloaded Win10 and Win11 client ISO's from Microsoft and created 2 Windows client VMs
- Creating a base Win10 template for future use/deployment purposes:
  - Full updates + restarts until none left
  - Removed these bloatware packages via PowerShell:
    - Get-AppxPackage *3dbuilder* | Remove-AppxPackage
    - Get-AppxPackage *zunemusic* | Remove-AppxPackage
    - Get-AppxPackage *bingnews* | Remove-AppxPackage
    - Get-AppxPackage *bingsports* | Remove-AppxPackage
    - Get-AppxPackage *bingweather* | Remove-AppxPackage
    - Get-AppxPackage *officehub* | Remove-AppxPackage
    - Get-AppxPackage *solitairecollection* | Remove-AppxPackage
    - Get-AppxPackage *xboxapp* | Remove-AppxPackage
    - Get-AppxPackage *getstarted* | Remove-AppxPackage
  - Disabled Start-up apps:
    - Microsoft Edge
    - Microsoft OneDrive
  - This PC → Properties → Advanced System Settings → Performance → Settings → Custom (adjust for best performance but kept Smooth edges and Show thumbnails)
  - Turned off windows tips and such unnecessary notifications
  - Verified UAC setting (3, default)
  - 
