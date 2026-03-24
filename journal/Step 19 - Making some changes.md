#Step 19 - Making some changes

I want to continue my homelab further but I am facing resource issues to work efficiently, I have some bottlenecks with memory and HDD i/o. My host is running at 90+% memory and 100% HDD i/o with only the DC and the linux monitoring VMs on (plus host using resources).
I can't change my VMs volumes to an SSD for now, and I have reduced DC to 2gb memory down from 4gb, and the linux set to 4gb.
Main bottleneck right now is the HDD i/o though.

Trying things:
- Defragmented my HDD (from host) via powershell: Optimize-Volume -DriveLetter S -Defrag -Verbose
- Changed DC's hard disk type to SATA (from NVMe, which it wasn't on an NVMe I just picked NVMe by default via recommended when I installed it initially)
- None of this worked I am still hitting 100% HDD i/o with my wazuh machine on and DC alone, I have to either rethink my entire homelab and cut down fo the purpose I want to focus on or buy hardware which I can't right now.

Will re-think a solution and come back to it when I do
