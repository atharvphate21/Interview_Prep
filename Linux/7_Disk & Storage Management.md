## How to check disk space?
In Linux, we can check disk space using the `df -h` command, which shows total, used, and available space on mounted filesystems in a human-readable format. For detailed folder-level usage, we can use `du -h directory_name` to see how much space each directory or file is consuming.

## What is df and du?
In Linux, `df` shows the disk space usage of entire filesystems, including total, used, and available space. `du` shows the disk space used by specific files or directories. `df` is useful for overall storage, while `du` helps find which files or folders are taking up space.

## How to format a disk?
In Linux, we can format a disk using the `mkfs` command. For example, `mkfs.ext4 /dev/sdb1` formats the partition `/dev/sdb1` with the ext4 filesystem. Formatting prepares the disk for storing data by creating a new filesystem.

## How to add new disk?
In Linux, to add a new disk, first attach the disk to the system, then create a partition using `fdisk` or `parted`. Format it with a filesystem using `mkfs`, and finally mount it with `mount` or add it to `/etc/fstab` for automatic mounting. This makes the disk ready for use.

## What is LVM?
In Linux, LVM (Logical Volume Manager) is a system to manage disk storage more flexibly. It allows combining multiple physical disks into a single volume group and creating logical volumes that can be resized easily. LVM simplifies storage management, resizing, and snapshots.

## What is RAID?
In Linux, RAID (Redundant Array of Independent/Inexpensive Disks) is a technology that combines multiple physical disks into one logical unit for performance, redundancy, or both. Different levels (RAID 0, 1, 5, 10) provide options for speed, fault tolerance, or data protection.

## Difference between ext4 and xfs?
In Linux, **ext4** and **XFS** are both filesystems. Ext4 is stable, widely used, and good for general-purpose workloads with smaller files. XFS is designed for high-performance, large files, and parallel I/O, making it suitable for big data and enterprise storage. Ext4 is simpler, while XFS scales better on large systems.

## How to extend filesystem?
In Linux, we can extend a filesystem after increasing its underlying disk or logical volume. For example, for ext4: `resize2fs /dev/volume` and for XFS: `xfs_growfs /mountpoint`. This allows the filesystem to use the added space without losing data.

## What is UUID?
In Linux, a UUID (Universally Unique Identifier) is a unique identifier assigned to a disk partition. It ensures consistent mounting of disks, even if device names like `/dev/sdb1` change. UUIDs can be viewed using `blkid` and used in `/etc/fstab` for stable mounts.
