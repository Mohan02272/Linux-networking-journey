# Logical Volume Manager (LVM) in Linux

# Table of Contents

1. Introduction to Storage Management
2. What is LVM?
3. Why LVM is Used
4. Limitations of Traditional Partitions
5. LVM Architecture
6. Physical Volumes (PV)
7. Volume Groups (VG)
8. Logical Volumes (LV)
9. Understanding LVM Workflow
10. Installing LVM Tools
11. Checking Existing Storage Devices
12. Creating Partitions for LVM
13. Creating Physical Volumes
14. Managing Physical Volumes
15. Creating Volume Groups
16. Managing Volume Groups
17. Creating Logical Volumes
18. Managing Logical Volumes
19. Creating File Systems on LVM
20. Mounting Logical Volumes
21. Persistent Mounting Using fstab
22. Extending Logical Volumes
23. Reducing Logical Volumes
24. Adding New Disks to Existing Volume Groups
25. Removing Physical Volumes from LVM
26. LVM Snapshots
27. LVM Commands Cheat Sheet
28. Real-World Enterprise Usage
29. Troubleshooting LVM
30. Best Practices
31. Interview Questions and Answers
32. Practical Lab Exercises
33. Conclusion

---

# 1. Introduction to Storage Management

Storage management is one of the most important responsibilities of a Linux System Administrator.

Every Linux system stores:

* Operating system files
* User files
* Application data
* Logs
* Databases
* Backup data

Proper storage management ensures:

* Better performance
* Easy scalability
* Efficient disk utilization
* Data organization
* System reliability

Traditional disk partitions are fixed in size and difficult to resize dynamically. To solve this limitation, Linux uses a technology called Logical Volume Manager (LVM).

---

# 2. What is LVM?

LVM stands for:

Logical Volume Manager

LVM is an advanced storage management system in Linux that provides flexible disk management.

Instead of directly creating partitions from disks, LVM creates a virtual storage layer between the physical disks and file systems.

This allows administrators to:

* Resize storage dynamically
* Combine multiple disks
* Create snapshots
* Expand storage online
* Improve storage flexibility

---

# 3. Why LVM is Used

Traditional partitions have several limitations.

Example:

Suppose a server has:

* Partition A = 50GB
* Partition B = 100GB

If Partition A becomes full while Partition B still has free space, resizing is difficult.

LVM solves this problem by creating flexible storage pools.

Advantages of LVM:

| Feature           | Benefit                             |
| ----------------- | ----------------------------------- |
| Dynamic resizing  | Increase or decrease storage easily |
| Storage pooling   | Combine multiple disks              |
| Snapshots         | Backup before changes               |
| Online resizing   | Resize without reboot               |
| Better management | Easier administration               |
| Scalability       | Add new disks anytime               |

---

# 4. Limitations of Traditional Partitions

Traditional partitioning follows this structure:

Disk → Partition → File System

Problems:

1. Fixed partition sizes
2. Difficult resizing
3. Wasted storage space
4. Limited flexibility
5. Complex migration process

LVM introduces abstraction and flexibility.

---

# 5. LVM Architecture

LVM architecture contains three main layers.

## Structure

Physical Disk → Physical Volume → Volume Group → Logical Volume → File System

---

## Main Components

| Component            | Description                       |
| -------------------- | --------------------------------- |
| Physical Volume (PV) | Actual storage device             |
| Volume Group (VG)    | Storage pool created from PVs     |
| Logical Volume (LV)  | Virtual partition created from VG |

---

# 6. Physical Volumes (PV)

A Physical Volume is the first layer of LVM.

It can be:

* Entire disk
* Disk partition
* RAID device
* SAN storage

Examples:

```bash
/dev/sdb1
/dev/sdc1
```

When a partition is initialized for LVM, it becomes a Physical Volume.

---

## PV Responsibilities

* Store physical storage blocks
* Provide storage to Volume Groups
* Act as the base layer of LVM

---

# 7. Volume Groups (VG)

A Volume Group is a storage pool created by combining one or more Physical Volumes.

Example:

* PV1 = 100GB
* PV2 = 200GB

Combined into:

VG = 300GB storage pool

The Volume Group acts like a large virtual disk.

---

## VG Responsibilities

* Combine multiple disks
* Manage available storage
* Allocate space to Logical Volumes

---

# 8. Logical Volumes (LV)

Logical Volumes are virtual partitions created from Volume Groups.

Example:

VG Size = 300GB

Create:

* LV1 = 100GB
* LV2 = 50GB
* LV3 = 150GB

Logical Volumes behave like normal partitions.

They can:

* Store file systems
* Be mounted
* Be resized dynamically

---

# 9. Understanding LVM Workflow

Step-by-step process:

1. Create disk partition
2. Convert partition into Physical Volume
3. Create Volume Group
4. Create Logical Volume
5. Create file system
6. Mount Logical Volume

---

# 10. Installing LVM Tools

## Ubuntu/Debian

```bash
sudo apt install lvm2
```

## RHEL/Rocky/AlmaLinux

```bash
sudo dnf install lvm2
```

---

## Command Breakdown

| Command | Meaning         |
| ------- | --------------- |
| apt     | Package manager |
| install | Install package |
| lvm2    | LVM utilities   |

---

# 11. Checking Existing Storage Devices

## Display Block Devices

```bash
lsblk
```

---

## Example Output

```bash
NAME   SIZE TYPE MOUNTPOINT
sda    100G disk
├─sda1   1G part /boot
├─sda2  50G part /
sdb     50G disk
```

---

## Detailed Disk Information

```bash
sudo fdisk -l
```

---

## Check Existing LVM Information

```bash
sudo pvs
sudo vgs
sudo lvs
```

---

# 12. Creating Partitions for LVM

Suppose a new disk is available:

```bash
/dev/sdb
```

---

## Open fdisk

```bash
sudo fdisk /dev/sdb
```

---

## Create New Partition

Inside fdisk:

```bash
n
```

Then:

* Select primary partition
* Choose partition number
* Select first sector
* Select last sector

---

## Change Partition Type to LVM

```bash
t
```

Then choose:

```bash
8e
```

8e means Linux LVM partition type.

---

## Save Changes

```bash
w
```

---

## Verify

```bash
lsblk
```

---

# 13. Creating Physical Volumes

## Command

```bash
sudo pvcreate /dev/sdb1
```

---

## Command Breakdown

| Part      | Meaning                |
| --------- | ---------------------- |
| pvcreate  | Create physical volume |
| /dev/sdb1 | Target partition       |

---

## Verify PV

```bash
sudo pvs
```

OR

```bash
sudo pvdisplay
```

---

## Example Output

```bash
PV         VG     Fmt  Attr PSize  PFree
/dev/sdb1         lvm2 a--  50.00g 50.00g
```

---

# 14. Managing Physical Volumes

## Scan for PVs

```bash
sudo pvscan
```

---

## Remove Physical Volume

```bash
sudo pvremove /dev/sdb1
```

This removes LVM metadata from the partition.

---

# 15. Creating Volume Groups

## Command

```bash
sudo vgcreate vgdata /dev/sdb1
```

---

## Command Breakdown

| Part      | Meaning             |
| --------- | ------------------- |
| vgcreate  | Create volume group |
| vgdata    | Volume group name   |
| /dev/sdb1 | Physical volume     |

---

## Verify VG

```bash
sudo vgs
```

OR

```bash
sudo vgdisplay
```

---

## Example Output

```bash
VG     #PV #LV #SN Attr   VSize  VFree
vgdata   1   0   0 wz--n- 50.00g 50.00g
```

---

# 16. Managing Volume Groups

## Extend Volume Group

Add another Physical Volume:

```bash
sudo vgextend vgdata /dev/sdc1
```

---

## Reduce Volume Group

```bash
sudo vgreduce vgdata /dev/sdc1
```

---

## Scan Volume Groups

```bash
sudo vgscan
```

---

# 17. Creating Logical Volumes

## Command

```bash
sudo lvcreate -L 10G -n lvbackup vgdata
```

---

## Command Breakdown

| Part        | Meaning               |
| ----------- | --------------------- |
| lvcreate    | Create logical volume |
| -L 10G      | Size                  |
| -n lvbackup | LV name               |
| vgdata      | Volume group          |

---

## Verify LV

```bash
sudo lvs
```

OR

```bash
sudo lvdisplay
```

---

## Example Output

```bash
LV       VG     Attr       LSize
lvbackup vgdata -wi-a----- 10.00g
```

---

# 18. Managing Logical Volumes

## Activate LV

```bash
sudo lvchange -ay /dev/vgdata/lvbackup
```

---

## Deactivate LV

```bash
sudo lvchange -an /dev/vgdata/lvbackup
```

---

## Remove LV

```bash
sudo lvremove /dev/vgdata/lvbackup
```

---

# 19. Creating File Systems on LVM

After creating the Logical Volume, a file system must be created.

---

## ext4 File System

```bash
sudo mkfs.ext4 /dev/vgdata/lvbackup
```

---

## XFS File System

```bash
sudo mkfs.xfs /dev/vgdata/lvbackup
```

---

## Verify File System

```bash
lsblk -f
```

---

# 20. Mounting Logical Volumes

## Create Mount Point

```bash
sudo mkdir /backup
```

---

## Mount Logical Volume

```bash
sudo mount /dev/vgdata/lvbackup /backup
```

---

## Verify Mount

```bash
df -h
```

---

## Unmount

```bash
sudo umount /backup
```

---

# 21. Persistent Mounting Using fstab

Temporary mounts disappear after reboot.

Permanent mounts are configured in:

```bash
/etc/fstab
```

---

## Get UUID

```bash
sudo blkid
```

---

## Example Entry

```bash
UUID=123abc /backup ext4 defaults 0 2
```

---

## Test fstab

```bash
sudo mount -a
```

If no error appears, the configuration is correct.

---

# 22. Extending Logical Volumes

One major advantage of LVM is dynamic resizing.

---

## Extend LV Size

```bash
sudo lvextend -L +5G /dev/vgdata/lvbackup
```

---

## Extend Using Free Space

```bash
sudo lvextend -l +100%FREE /dev/vgdata/lvbackup
```

---

## Resize ext4 File System

```bash
sudo resize2fs /dev/vgdata/lvbackup
```

---

## Resize XFS File System

```bash
sudo xfs_growfs /backup
```

---

# 23. Reducing Logical Volumes

Reducing storage is dangerous and must be performed carefully.

---

## Steps for ext4

1. Unmount file system
2. Check file system
3. Reduce file system
4. Reduce logical volume
5. Mount again

---

## Check File System

```bash
sudo e2fsck -f /dev/vgdata/lvbackup
```

---

## Resize File System

```bash
sudo resize2fs /dev/vgdata/lvbackup 5G
```

---

## Reduce LV

```bash
sudo lvreduce -L 5G /dev/vgdata/lvbackup
```

---

# 24. Adding New Disks to Existing Volume Groups

Suppose a new disk is added:

```bash
/dev/sdc1
```

---

## Create Physical Volume

```bash
sudo pvcreate /dev/sdc1
```

---

## Extend VG

```bash
sudo vgextend vgdata /dev/sdc1
```

Now the Volume Group has additional storage.

---

# 25. Removing Physical Volumes from LVM

Before removing a PV, move data away from it.

---

## Move Data

```bash
sudo pvmove /dev/sdc1
```

---

## Remove from VG

```bash
sudo vgreduce vgdata /dev/sdc1
```

---

## Remove PV Metadata

```bash
sudo pvremove /dev/sdc1
```

---

# 26. LVM Snapshots

Snapshots create temporary copies of Logical Volumes.

Useful for:

* Backups
* Testing
* Recovery
* Database maintenance

---

## Create Snapshot

```bash
sudo lvcreate -L 2G -s -n snap_backup /dev/vgdata/lvbackup
```

---

## Command Breakdown

| Part  | Meaning       |
| ----- | ------------- |
| -L 2G | Snapshot size |
| -s    | Snapshot      |
| -n    | Snapshot name |

---

## Restore Snapshot

Usually requires:

* Unmounting original volume
* Merging snapshot

---

# 27. LVM Commands Cheat Sheet

| Command    | Purpose               |
| ---------- | --------------------- |
| pvs        | List physical volumes |
| vgs        | List volume groups    |
| lvs        | List logical volumes  |
| pvcreate   | Create PV             |
| vgcreate   | Create VG             |
| lvcreate   | Create LV             |
| vgextend   | Extend VG             |
| lvextend   | Extend LV             |
| lvremove   | Remove LV             |
| pvremove   | Remove PV             |
| mount      | Mount storage         |
| umount     | Unmount storage       |
| resize2fs  | Resize ext4           |
| xfs_growfs | Resize XFS            |

---

# 28. Real-World Enterprise Usage

LVM is widely used in:

* Enterprise Linux servers
* Cloud infrastructure
* VMware virtual machines
* Database servers
* DevOps environments
* Kubernetes worker nodes
* Backup systems

---

## Why Enterprises Prefer LVM

1. Flexible resizing
2. Better storage utilization
3. Easier upgrades
4. Snapshot support
5. Minimal downtime

---

# 29. Troubleshooting LVM

## Problem 1: Volume Group Not Found

Solution:

```bash
sudo vgscan
sudo vgchange -ay
```

---

## Problem 2: Mount Failure

Check:

```bash
lsblk
blkid
```

---

## Problem 3: File System Corruption

Repair:

```bash
sudo fsck /dev/vgdata/lvbackup
```

---

## Problem 4: No Free Space in VG

Check:

```bash
sudo vgs
```

Add new disk if needed.

---

# 30. Best Practices

1. Always backup important data
2. Use UUID in fstab
3. Monitor disk usage regularly
4. Use meaningful VG/LV names
5. Test before production deployment
6. Avoid shrinking XFS file systems
7. Keep snapshot sizes sufficient
8. Document storage architecture

---

# 31. Interview Questions and Answers

## What is LVM?

LVM is a flexible storage management system that allows dynamic management of disk storage.

---

## What are the main components of LVM?

* Physical Volume (PV)
* Volume Group (VG)
* Logical Volume (LV)

---

## What is the advantage of LVM?

Dynamic resizing and flexible storage management.

---

## Difference between partition and logical volume?

Traditional partitions are fixed.

Logical Volumes are flexible and resizable.

---

## Which file systems support online resize?

* ext4
* XFS

---

# 32. Practical Lab Exercises

## Lab 1: Create Basic LVM

Tasks:

1. Add new virtual disk
2. Create partition
3. Create PV
4. Create VG
5. Create LV
6. Create file system
7. Mount LV

---

## Lab 2: Extend Storage

Tasks:

1. Add second disk
2. Extend VG
3. Extend LV
4. Resize file system

---

## Lab 3: Create Snapshot

Tasks:

1. Create snapshot
2. Modify files
3. Restore snapshot

---

# 33. Conclusion

Logical Volume Manager is one of the most powerful storage technologies available in Linux.

It provides:

* Flexibility
* Scalability
* Reliability
* Efficient storage management

Modern Linux environments heavily depend on LVM for enterprise-level storage administration.

A strong understanding of LVM is essential for:

* Linux Administrators
* DevOps Engineers
* Cloud Engineers
* System Engineers
* Cybersecurity Professionals

Mastering LVM will significantly improve your Linux administration skills and prepare you for real-world infrastructure management.
