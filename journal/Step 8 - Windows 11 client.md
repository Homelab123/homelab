#Step 8 - Windows 11 client

Will do the same as I did with the Win10 client but for Win11 - just trying to emulate a multi version of Windows environment.

- Initial installation:
  - 2 vCPU x 2 cores
  - 4gb RAM
  - 64gb Disk space (volume as single file)
- Installed EN-US, EN-CAN, FR-CAN keyboard layouts
- Chose personal use option for the purpose of this homelab (simplicity)
- I had to bypass the Windows 11 out-of-box-experience somehow due to having to enter emails and other restrictions:
  - created a autounattend.xml with the configs I wanted
  - installed Windows ADK to create an ISO with that xml file in it
  - Added a CD/DVD drive to the VM (extra one) and had it load the autounattend.iso
  - Launched a clean boot with the initial win11 ISO and a 2nd drive with the autounattend.iso
  - Went through installation as normal this time and landed on desktop
  - Rad full updates+restarts until none left
  - sysdm.cpl > Advanced > Performance Settings > Adjusted for performance
  - Disabled unimportant apps from Startup Apps
  - Disabled Windows Search service (don't need indexing)
  - CMD > powercfg /h off (disabled hibernation mode)
  - Installed VMware Tools

- Running into communcation issues between the Win11 client and the FortiGate VM:
  - Ensured VM is on correct VMnet3
  - Ensured FortiGate port3 is running and has correct settings (10.0.1.1/25)
  - Ensured Win11 VM is on automatic and network is set to Private with discovery on
  - Tried reboots and ipconfig /release and /renew but it gets stuck
  - Tried setting manual network settings to test and it works but I must make it work in dhcp for template and not set a static ip
  - DHCP is not responding to the Win11 VM
  - Ran this on FGT01: diagnose sniffer packet port3 'udp port 67 or udp port 68' 4
  - Changed WIN11 vm back to DHCP
  - Confirmed DHCP requests are received on FGT01 but FGT01 is not responding to them
  - Problem:
    - FortiGate had DHCP vci-match set on
    - Ran unset vci-match for DHCP server and ran ipconfig /release and /renew on win11 VM and it worked.

- Ran Disk Cleanup
- Snapshotted VM before running sysprep
- Ran into issues with sysprep not wanting to launch which is apparently a known WIN11 issue, I have created a snapshot of the VM itself and will save it as it is as a template and go from there. This is not ideal or what should be done but for lab purposes it will have to do because it seems the windows install is at a dead end after trying multiple fixes there is stuck shared storage that prevents sysprep from running.
- Cloned VM to WIN11-01
