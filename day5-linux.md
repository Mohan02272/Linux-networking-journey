Linux Storage Management:

Storage management means:

Managing disks
Creating partitions
Formatting disks
Mounting drives
Expanding storage
Managing logical volumes

Understanding Linux Disk Naming :
Name	Meaning
sda	First disk
sdb	Second disk
sdc	Third disk

Partitions Meaning:
Partition	Meaning
sda1	Partition 1
sda2	Partition 2
sda3	Partition 3

To Check Available Disks: lsblk
Part	Meaning
ls	list
blk	block devices

To check Detailed Disk Information : sudo fdisk -l
Part	Meaning
fdisk	partition tool
-l	list all disks


Partition on LINUX :
A partition divides a disk into separate sections.

Two main type: 
MBR	Old system
GPT	Modern system

MBR Limitations
Max 2TB disk
Max 4 primary partitions

GPT Advantages
Huge disk support
Many partitions
Better reliability

Creating Partitions Using fdisk:

Step 01: Open Disk : sudo fdisk /dev/sdb
Step 02: Interactive Menu : m

Important fdisk Commands
Command	Meaning
m	help
p	print partition table
n	new partition
d	delete partition
w	write changes
q	quit without saving

Step 03 : Create New Partition : n
Step 04: Save Changes : w
Step 05 : Verify New Partition : lsblk


File System on LINUX:
A file system organizes files on storage.

File System	Usage
ext4	Most common
xfs	Enterprise servers
btrfs	Advanced features
vfat	USB compatibility

To create a file system: sudo mkfs.ext4 /dev/sdb1
To check File system type : lsblk -f


Mounting on LINUX: 
USB drive mounted at: /mnt/usb
To Create Mount Point: sudo mkdir /data
To mount a drive : sudo mount /dev/sdb1 /data
To Verify Mount : df -h

Unmounting on LINUX:
Before removing a drive we need to unmount.
Prevents:
corruption
data loss
incomplete writes

To umount a drive : sudo umount /data
