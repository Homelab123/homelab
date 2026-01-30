#Step 07 - Windows 10 client

Now that I can set network settings directly in my template, I will create a Win10 client template:

Steps taken:
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
- Disabled Windows Search service (don't need indexing)
- Disabled Sysmain service
- Settings → Privacy → Background apps → Turn off unneeded apps
- Settings → Privacy → Diagnostics & feedback → Basic only
- Turned Off News and Interest from taskbar
- Unpinned Microsoft Store from taskbar
- Disabled Cortana
- Required diagnostic data only
- Setup Network Settings:
  - Change Network Adapter Settings > IPv4 settings > Set preferred DNS to 10.0.0.10
  - Left IP addressing to DHCP/automatic
  - Disabled IPv6 addresses
  - Confirmed I can ping 10.0.1.1 (router vm)

Snapshotting and saving template as it is for now and cloning my first client. Then, I will remove the template and add it to my template VM folder.
