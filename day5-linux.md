# Linux Storage Management, Disk Partitioning, and Mounting

## Complete Professional Guide for Students

---

# Table of Contents

1. Introduction to Linux Storage Management
2. Understanding Storage Devices in Linux
3. Linux Disk Naming Convention
4. Types of Storage Devices
5. Understanding Block Devices
6. Understanding Partitions
7. Why Partitions are Used
8. Partition Table Types
9. MBR Partitioning
10. GPT Partitioning
11. File Systems in Linux
12. Common Linux File Systems
13. Storage Management Workflow
14. Checking Storage Devices
15. Understanding lsblk Command
16. Understanding fdisk Command
17. Understanding parted Command
18. Creating Disk Partitions Using fdisk
19. Deleting Disk Partitions
20. Viewing Partition Information
21. Creating File Systems
22. Formatting Partitions
23. Understanding UUID
24. Mounting in Linux
25. Temporary Mounting
26. Permanent Mounting Using fstab
27. Understanding Mount Points
28. Mount Options
29. Unmounting File Systems
30. Storage Usage Monitoring
31. Understanding df Command
32. Understanding du Command
33. Managing Swap Space
34. File System Checking and Repair
35. Storage Troubleshooting
36. Best Practices
37. Real-World Enterprise Usage
38. Interview Questions and Answers
39. Practical Lab Exercises
40. Conclusion

---

# 1. Introduction to Linux Storage Management

Storage management is a fundamental part of Linux system administration.

Every Linux system depends on storage for:

* Operating system files
* Applications
* User data
* Databases
* Logs
* Backups
* Virtual machines
* Containers

Linux administrators must know how to:

* Manage disks
* Create partitions
* Format file systems
* Mount drives
* Monitor storage usage
* Repair file systems
* Configure persistent storage

Proper storage management improves:

* System performance
* Reliability
* Scalability
* Data organization
* Security

---

# 2. Understanding Storage Devices in Linux

Linux treats storage devices as files.

These devices are located inside:

```bash
/dev/
```

Examples:

```bash
/dev/sda
/dev/sdb
/dev/nvme0n1
```

Storage devices can include:

* HDDs
* SSDs
* NVMe drives
* USB drives
* SAN storage
* RAID devices
* Virtual disks

---

# 3. Linux Disk Naming Convention

Linux follows specific naming rules for disks and partitions.

---

## SATA/SCSI Devices

| Device   | Meaning     |
| -------- | ----------- |
| /dev/sda | First disk  |
| /dev/sdb | Second disk |
| /dev/sdc | Third disk  |

---

## Partitions

| Device    | Meaning                        |
| --------- | ------------------------------ |
| /dev/sda1 | First partition                |
| /dev/sda2 | Second partition               |
| /dev/sdb1 | First partition of second disk |

---

## NVMe Devices

| Device         | Meaning         |
| -------------- | --------------- |
| /dev/nvme0n1   | NVMe disk       |
| /dev/nvme0n1p1 | First partition |

---

# 4. Types of Storage Devices

## Hard Disk Drive (HDD)

Traditional magnetic storage.

Advantages:

* Cheap
* Large storage

Disadvantages:

* Slower
* Mechanical parts

---

## Solid State Drive (SSD)

Flash-based storage.

Advantages:

* Faster
* More reliable
* Low latency

Disadvantages:

* More expensive

---

## NVMe SSD

High-speed SSD connected through PCIe.

Advantages:

* Extremely fast
* Better performance for servers and databases

---

# 5. Understanding Block Devices

Linux storage devices are called block devices.

Block devices store data in fixed-size blocks.

Examples:

```bash
/dev/sda
/dev/sdb1
```

Block devices support:

* Random access
* Read/write operations
* File system creation

---

# 6. Understanding Partitions

A partition divides a physical disk into multiple logical sections.

Example:

One 1TB disk can be divided into:

| Partition | Size  | Usage            |
| --------- | ----- | ---------------- |
| /dev/sda1 | 100GB | Operating System |
| /dev/sda2 | 500GB | User Data        |
| /dev/sda3 | 400GB | Backup           |

Linux treats each partition as a separate storage device.

---

# 7. Why Partitions are Used

Partitions help:

1. Separate operating system and data
2. Improve organization
3. Simplify backups
4. Improve security
5. Prevent full disk problems
6. Support multi-boot systems

---

# 8. Partition Table Types

A partition table stores information about disk partitions.

Linux mainly uses:

| Type | Full Name            |
| ---- | -------------------- |
| MBR  | Master Boot Record   |
| GPT  | GUID Partition Table |

---

# 9. MBR Partitioning

MBR is the older partitioning system.

---

## Features

* Maximum disk size: 2TB
* Maximum primary partitions: 4

---

## Limitations

* Limited scalability
* Less reliable
* Old technology

---

# 10. GPT Partitioning

GPT is the modern partitioning standard.

---

## Advantages

* Supports very large disks
* Supports many partitions
* Better reliability
* Used in modern servers

---

## Recommendation

Modern Linux systems should use GPT.

---

# 11. File Systems in Linux

A file system organizes how data is stored and retrieved.

Without a file system, Linux cannot store files properly.

---

# 12. Common Linux File Systems

| File System | Usage                              |
| ----------- | ---------------------------------- |
| ext4        | Most common Linux file system      |
| XFS         | Enterprise and large-scale systems |
| Btrfs       | Advanced modern file system        |
| FAT32       | USB compatibility                  |
| NTFS        | Windows compatibility              |

---

## ext4

Advantages:

* Stable
* Reliable
* Widely supported

---

## XFS

Advantages:

* High performance
* Good for large storage
* Common in enterprise Linux

---

# 13. Storage Management Workflow

General workflow:

1. Detect disk
2. Create partition
3. Create file system
4. Create mount point
5. Mount partition
6. Configure permanent mounting

---

# 14. Checking Storage Devices

## Display Block Devices

```bash
lsblk
```

---

## Command Breakdown

| Part | Meaning       |
| ---- | ------------- |
| ls   | list          |
| blk  | block devices |

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

# 15. Understanding lsblk Command

The lsblk command displays:

* Disks
* Partitions
* Mount points
* File systems
* Storage hierarchy

---

## Display File Systems

```bash
lsblk -f
```

---

## Example Output

```bash
NAME   FSTYPE LABEL UUID MOUNTPOINT
sda
├─sda1 ext4         abc1 /boot
├─sda2 xfs          abc2 /
```

---

# 16. Understanding fdisk Command

fdisk is a partition management utility.

---

## List Disks

```bash
sudo fdisk -l
```

---

## Open Disk for Partitioning

```bash
sudo fdisk /dev/sdb
```

---

# 17. Understanding parted Command

parted is an advanced partitioning tool.

Supports:

* GPT
* Large disks
* Advanced management

---

## Start parted

```bash
sudo parted /dev/sdb
```

---

# 18. Creating Disk Partitions Using fdisk

Suppose a new disk exists:

```bash
/dev/sdb
```

---

## Step 1: Open Disk

```bash
sudo fdisk /dev/sdb
```

---

## Step 2: Create New Partition

Inside fdisk:

```bash
n
```

fdisk will ask:

* Partition type
* Partition number
* First sector
* Last sector

---

## Step 3: Save Changes

```bash
w
```

---

## Verify

```bash
lsblk
```

---

# 19. Deleting Disk Partitions

Open fdisk:

```bash
sudo fdisk /dev/sdb
```

Delete partition:

```bash
d
```

Save:

```bash
w
```

---

# 20. Viewing Partition Information

## Display UUID

```bash
sudo blkid
```

---

## Example Output

```bash
/dev/sdb1: UUID="abc123" TYPE="ext4"
```

---

# 21. Creating File Systems

After creating a partition, a file system must be created.

---

## Create ext4 File System

```bash
sudo mkfs.ext4 /dev/sdb1
```

---

## Create XFS File System

```bash
sudo mkfs.xfs /dev/sdb1
```

---

## Command Breakdown

| Command   | Meaning          |
| --------- | ---------------- |
| mkfs      | Make file system |
| ext4      | File system type |
| /dev/sdb1 | Target partition |

---

# 22. Formatting Partitions

Formatting means:

Preparing a partition with a file system.

Warning:

Formatting erases existing data.

---

# 23. Understanding UUID

UUID stands for:

Universally Unique Identifier

Each file system receives a unique ID.

Linux uses UUID for reliable mounting.

---

## Display UUID

```bash
sudo blkid
```

---

# 24. Mounting in Linux

Linux does not use drive letters like Windows.

Instead, file systems are attached to directories.

This process is called mounting.

---

## Example

Mount partition:

```bash
/dev/sdb1
```

onto:

```bash
/data
```

Files become accessible through:

```bash
/data
```

---

# 25. Temporary Mounting

## Create Mount Point

```bash
sudo mkdir /data
```

---

## Mount Partition

```bash
sudo mount /dev/sdb1 /data
```

---

## Verify Mount

```bash
df -h
```

---

## Unmount

```bash
sudo umount /data
```

OR

```bash
sudo umount /dev/sdb1
```

---

# 26. Permanent Mounting Using fstab

Temporary mounts disappear after reboot.

Permanent mounts are configured inside:

```bash
/etc/fstab
```

---

## View fstab

```bash
cat /etc/fstab
```

---

## Example Entry

```bash
UUID=abc123 /data ext4 defaults 0 2
```

---

## Field Breakdown

| Field    | Meaning                 |
| -------- | ----------------------- |
| UUID     | Unique identifier       |
| /data    | Mount point             |
| ext4     | File system type        |
| defaults | Mount options           |
| 0        | Dump backup setting     |
| 2        | File system check order |

---

## Test fstab

```bash
sudo mount -a
```

If no errors appear, configuration is correct.

---

# 27. Understanding Mount Points

A mount point is a directory where a file system is attached.

Examples:

| Mount Point | Purpose          |
| ----------- | ---------------- |
| /           | Root file system |
| /home       | User data        |
| /boot       | Boot files       |
| /data       | Custom storage   |
| /mnt        | Temporary mounts |

---

# 28. Mount Options

Mount options control file system behavior.

---

## Common Options

| Option   | Meaning             |
| -------- | ------------------- |
| defaults | Standard options    |
| ro       | Read only           |
| rw       | Read/write          |
| noexec   | Disable execution   |
| nosuid   | Disable SUID        |
| noatime  | Improve performance |

---

## Example

```bash
UUID=abc123 /data ext4 defaults,noatime 0 2
```

---

# 29. Unmounting File Systems

Unmounting safely disconnects a file system.

---

## Command

```bash
sudo umount /data
```

---

## Why Unmount?

Prevents:

* Data corruption
* Incomplete writes
* File system damage

---

# 30. Storage Usage Monitoring

Linux provides multiple commands for monitoring storage.

---

# 31. Understanding df Command

Displays file system usage.

---

## Command

```bash
df -h
```

---

## Command Breakdown

| Part | Meaning        |
| ---- | -------------- |
| df   | Disk free      |
| -h   | Human readable |

---

## Example Output

```bash
Filesystem      Size Used Avail Use% Mounted on
/dev/sda2        50G   20G   30G  40% /
```

---

# 32. Understanding du Command

Displays directory size.

---

## Command

```bash
du -sh /var
```

---

## Breakdown

| Option | Meaning        |
| ------ | -------------- |
| -s     | Summary        |
| -h     | Human readable |

---

# 33. Managing Swap Space

Swap is disk space used as virtual memory.

When RAM becomes full, Linux may use swap.

---

## Display Swap

```bash
swapon --show
```

---

## Create Swap File

```bash
sudo fallocate -l 2G /swapfile
```

---

## Set Permissions

```bash
sudo chmod 600 /swapfile
```

---

## Format Swap

```bash
sudo mkswap /swapfile
```

---

## Enable Swap

```bash
sudo swapon /swapfile
```

---

# 34. File System Checking and Repair

Linux can repair damaged file systems.

---

## ext4 Repair

```bash
sudo fsck /dev/sdb1
```

---

## Force Check

```bash
sudo fsck -f /dev/sdb1
```

---

# 35. Storage Troubleshooting

## Problem 1: Disk Not Visible

Check:

```bash
lsblk
fdisk -l
```

---

## Problem 2: Mount Failure

Check:

* File system type
* Mount point existence
* UUID correctness

---

## Problem 3: Disk Full

Check:

```bash
df -h
du -sh /*
```

---

## Problem 4: fstab Errors

Boot into recovery mode.

Fix incorrect entries.

---

# 36. Best Practices

1. Use GPT partitioning
2. Use UUID in fstab
3. Separate OS and data partitions
4. Monitor storage regularly
5. Backup important data
6. Test fstab before reboot
7. Use meaningful mount points
8. Avoid sudden power loss

---

# 37. Real-World Enterprise Usage

Storage management is essential in:

* Cloud computing
* Virtualization
* Database servers
* DevOps environments
* Kubernetes clusters
* Enterprise Linux servers

---

## Common Enterprise Partitions

| Partition | Purpose           |
| --------- | ----------------- |
| /         | Operating system  |
| /boot     | Boot loader files |
| /home     | User data         |
| /var      | Logs and services |
| /tmp      | Temporary files   |
| /data     | Application data  |

---

# 38. Interview Questions and Answers

## What is a partition?

A partition is a logical division of a physical disk.

---

## Difference between MBR and GPT?

GPT supports larger disks and more partitions.

MBR is older and limited.

---

## What is mounting?

Mounting is attaching a file system to a directory.

---

## Why use UUID in fstab?

UUID ensures stable mounting even if device names change.

---

## Difference between df and du?

* df shows file system usage
* du shows directory usage

---

# 39. Practical Lab Exercises

## Lab 1: Partitioning Practice

Tasks:

1. Add virtual disk
2. Create partition
3. Verify partition

---

## Lab 2: File System Practice

Tasks:

1. Format partition
2. Verify file system
3. Check UUID

---

## Lab 3: Mounting Practice

Tasks:

1. Create mount point
2. Mount partition
3. Configure fstab
4. Verify persistent mount

---

## Lab 4: Storage Monitoring

Tasks:

1. Use df
2. Use du
3. Analyze disk usage

---

# 40. Conclusion

Linux storage management is a critical skill for every Linux administrator and DevOps engineer.

Understanding:

* Disk partitioning
* File systems
* Mounting
* Storage monitoring
* File system repair

is essential for managing Linux infrastructure professionally.

A strong foundation in storage management prepares students for:

* Linux Administration
* DevOps Engineering
* Cloud Infrastructure
* Cybersecurity
* Virtualization
* Enterprise System Management

Mastering these concepts is necessary for real-world Linux environments and professional system administration.

