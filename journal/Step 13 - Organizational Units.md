#Step 13 - Organizational Units

Now that I've joined all my VMs to my domain and verified it works and connects, I'm gonna create OU's on my DC.
- Created OU's
- Created Groups
- Created Users
- Joined users to their respective groups
- Moved machines to their respective OU

corp.lab:
- Domain Controllers (default one):
  - DC01
- OU_Users:
  - Office: (Bob Marc)
  - IT: (Alice Tyler)
  - ServiceAccounts: (Michael Patrick)
  - Disabled
- OU_Servers:
  - FileServers:
    - FS01
  - Backup:
    - BK01
  - Web:
    - LIN-WEBAPP-01
  - Infrastructure:
    - LIN-AUTMONLOG-01
- OU_Groups:
  - GRP_FileShare_Office_RW: (Bat Man, Bob Marc)
  - GRP_FileShare_IT_RW: (Alice Tyler, Bat Man)
  - GRP_Backup_Admins: (Bat Man, Michael Patrick)
  - GRP_Web_Admins: (Alice Tyler, Bat Man)
  - GRP_LocalAdmins: (Bat Man)
  - GRP_PrivilegedUsers: (Bat Man)
- OU_Admin: (Bat Man)
- OU_Computers:
  - Workstations:
    - WIN10-01
    - WIN11-01


Groups/Users:
- GRP_FileShare_Office_RW: (Bat Man, Bob Marc)
- GRP_FileShare_IT_RW: (Alice Tyler, Bat Man)
- GRP_Backup_Admins: (Bat Man, Michael Patrick)
- GRP_Web_Admins: (Alice Tyler, Bat Man)
- GRP_LocalAdmins: (Bat Man)
- GRP_PrivilegedUsers: (Bat Man)
