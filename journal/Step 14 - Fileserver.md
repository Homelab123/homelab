#Step 14 - Fileserver

I will now work on my fileserver:

- Previously already configured network adapter
- Changed time&date settings to match correct timezone
- Changed machine name to FS01 and rebooted
- Added a new disk because the fileshare should be on a seperate disk/volume (only 20gb for the sake of homelab)
- Added role:
  - File and Storage Services:
    - File Server
    - Data Deduplication
    - File Server Resource Manager
  - Storage Services (installed by default)
- No extra features chosen
- Installed and rebooted

New Disk:
- Brought the new disk online
- Initialized disk
- Created new volume (S: / NTFS / Default)

NTFS Permissions:
- Created example file structure (S:\Shares\Accounting, S:\Shares\HR, S:\Shares\IT for now)
- Disabled inheritence and converted into explicit permissions on subfolders to be able to remove unwanted groups like FS01\Users
- Changed all the folders permission:
  - Added corp.lab/GRP_Admins to all folders with full control
  - Removed FS01\Users from all folders (local users)
  - Added corp.lab/GRP_FileShare_IT_RW to the IT subfolder with read/write/execute rights
  - Other groups are not made yet for other departments like HR etc, will come back to it later.
- Shared \\FS01\Fielshare and adjusted permissions via Advanged Sharing...
  - Name: Fileshare
  - Removed "Everyone"
  - Added GRP_Admins with Full Control
  - Added GRP_FileShare_IT_RW with Change/Read permissions
 
Will adjust as needed as I develop homelab further

- Enabled Shadow Copies for S:
- Tested fileshare from a different machine and it works
- Enabled access-based enumeration (only files users have access to will be displayed)
- Mapped Fileshare to all users via GPO
- Tested it's working from a random user on a client VM

This part is complete at least for now.
