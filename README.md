# linux-lvm-storage
# 💾 Linux LVM Storage Management

## Overview
Implemented LVM (Logical Volume Manager) on CentOS 7
to create, mount, extend, and snapshot logical volumes.

## What I Implemented
- ✅ Created partition using fdisk
- ✅ Created Physical Volume (PV)
- ✅ Created Volume Group (VG)
- ✅ Created Logical Volume (LV)
- ✅ Formatted with ext4 filesystem
- ✅ Mounted permanently via /etc/fstab
- ✅ Extended LV live (976MB → 1.5GB)
- ✅ Created LVM Snapshot

## Commands Used
```bash
# Partition banana
fdisk /dev/sdb

# LVM setup
pvcreate /dev/sdb1
vgcreate myvg /dev/sdb1
lvcreate -L 1G -n mydata myvg

# Filesystem aur mount
mkfs.ext4 /dev/myvg/mydata
mkdir /mnt/mydata
mount /dev/myvg/mydata /mnt/mydata

# Permanent mount
vi /etc/fstab

# Live extend
lvextend -L 1.5G /dev/myvg/mydata
resize2fs /dev/myvg/mydata

# Snapshot
lvcreate -L 200M -s -n mydata_snap /dev/myvg/mydata
```

## Verification
```bash
pvs    # Physical volumes
vgs    # Volume groups  
lvs    # Logical volumes
df -h /mnt/mydata  # Disk usage
```

## Screenshots
<img width="1267" height="954" alt="Screenshot 2026-03-05 165745" src="https://github.com/user-attachments/assets/7e029dd6-84dd-41be-b397-8cef2a21b939" />
<img width="1262" height="944" alt="Screenshot 2026-03-05 165715" src="https://github.com/user-attachments/assets/732f1c6f-edcd-450f-83a2-2f5058409a87" />
<img width="1257" height="951" alt="Screenshot 2026-03-05 165656" src="https://github.com/user-attachments/assets/e10cf73a-2594-4a92-80a8-fa34974a0687" />
<img width="1251" height="944" alt="Screenshot 2026-03-05 165636" src="https://github.com/user-attachments/assets/1a5edae7-78bb-44c3-a545-8d7c5e1ff851" />


## Environment
- OS: CentOS 7
- Hypervisor: VMware Workstation
- Disk Used: /dev/sdb (2GB)
