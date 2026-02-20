# 2. File System & Directory Structure

## What are the 19 important directories in Linux?
The important directories in Linux (under root `/`) are:
- `/` – Root directory (top-level directory)
- `/bin` – Essential user commands
- `/sbin` – System administration commands
- `/boot` – Boot loader files and kernel
- `/dev` – Device files
- `/etc` – Configuration files
- `/home` – User home directories
- `/lib` – Essential shared libraries
- `/lib64` – 64-bit libraries
- `/media` – Mount point for removable media
- `/mnt` – Temporary mount point
- `/opt` – Optional application software
- `/proc` – Virtual filesystem for process and system info
- `/root` – Home directory of root user
- `/run` – Runtime variable data
- `/srv` – Service data
- `/sys` – System and hardware information
- `/tmp` – Temporary files
- `/usr` – User programs and utilities
- `/var` – Variable data like logs and spool files

These directories follow the Linux Filesystem Hierarchy Standard (FHS) and organize the system structure properly.

## Explain the Linux directory structure
The Linux directory structure is organized in a hierarchical format starting from the root directory `/`. Everything in Linux is stored under this root directory.
- `/` – The top-level root directory.
- `/bin` – Basic user commands like `ls`, `cp`, `mv`.
- `/sbin` – System administration commands.
- `/etc` – Configuration files.
- `/home` – User home directories.
- `/root` – Home directory of the root user.
- `/usr` – User programs and applications.
- `/var` - Variable data like logs and spool files.
- `/tmp` – Temporary files.
- `/dev` – Device files.
- `/proc` – Process and system information (virtual files).
- `/boot` – Boot-related files and kernel.

In simple terms, Linux uses a tree-like structure where everything starts from `/`, and each directory has a specific purpose to keep the system organized.

## What is inode?
An inode is a data structure in Linux that stores metadata about a file. It contains information like file size, ownership, permissions, timestamps, and the location of the file on disk — but it does not store the file name.  
Each file in Linux has a unique inode number, which the system uses to identify and manage files internally.

## What fields does an inode store?
An inode stores the metadata of a file, including:
- File type (regular file, directory, etc.)
- File permissions
- Owner user ID (UID)
- Group ID (GID)
- File size
- Timestamps (creation, modification, access time)
- Number of hard links
- Pointers to data blocks (location of file data on disk)

It does not store the file name; the file name is stored in the directory entry.

## What is link count?
Link count is the number of hard links pointing to a file’s inode.  
It shows how many directory entries are associated with the same file data. When the link count becomes zero, and no process is using the file, the system deletes the file’s data from disk.

## Link count for file vs directory?
- For a regular file, the link count shows how many hard links point to that file. By default, it is 1, and it increases if you create additional hard links.
- For a directory, the link count is at least 2 — one for the directory itself `(.)` and one from its parent directory. It increases by 1 for each subdirectory inside it, because each subdirectory has a `..` entry pointing back to the parent directory.

## Difference between hard link and soft link?
- **Hard link** directly points to the same inode as the original file, meaning both files share the same data on disk. If the original file is deleted, the hard link still works because the data remains as long as at least one link exists. Hard links cannot be created for directories and cannot cross different file systems.
- **Soft link (symbolic link)** is a shortcut that points to the file name, not the inode. It has its own inode and simply stores the path of the original file. If the original file is deleted, the soft link becomes broken. Soft links can be created for directories and can cross different file systems.

## How to create a symbolic link?
### Creating a Symbolic Link (Soft Link)
A symbolic link is created using the `ln -s` command.

### Syntax
```bash
ln -s <target_file> <link_name>
```

## What is /proc file system?
The `/proc` file system is a virtual file system in Linux that provides real-time information about the system and running processes. It does not store actual files on disk; instead, it generates information dynamically from the kernel.  

It contains details like CPU usage, memory information, system configuration, and process-specific data (each process has a directory named with its PID). It is mainly used for monitoring and troubleshooting the system.

## What is /sys?
The `/sys` directory is a virtual file system in Linux that provides information about hardware devices and kernel subsystems. It is also known as **sysfs**.  

It allows users and applications to view and sometimes modify kernel and device settings through files. The data in `/sys` is generated dynamically by the kernel and helps in managing hardware, drivers, and system configuration.

## What is /dev?
The `/dev` directory contains device files in Linux. These files represent hardware and virtual devices such as hard disks, terminals, USB devices, and pseudo devices.  

In Linux, everything is treated as a file, so hardware devices are accessed through files in `/dev`. For example, `/dev/sda` represents a hard disk, and `/dev/tty` represents a terminal.

## What is swap space?
Swap space is a reserved area on the disk that is used as virtual memory when the system’s physical RAM is full.  

When RAM usage increases, inactive or less-used memory pages are moved from RAM to swap space to free up memory for active processes. Swap helps prevent system crashes due to memory shortage, but it is slower than RAM because it uses disk storage.

## What is fstab?
The `/etc/fstab` (File System Table) is a configuration file in Linux that defines how disk partitions, file systems, and swap space should be mounted at system boot.  

It contains details like the device name, mount point, file system type, mount options, and dump/pass values. The system reads this file during boot to automatically mount the required file systems.

## What is mount and unmount?
- **Mounting:** Attaching a file system (like a hard disk partition, USB drive, or network storage) to a directory in the Linux file system so that its data can be accessed.  
- **Unmounting:** Safely detaching that file system from the directory, ensuring that all data is properly written and no process is using it before removal.


## How to search files modified in last 2 days?

To search for files modified in the last 2 days, we use the `find` command.

**Command:**
```bash
find /path -type f -mtime -2
```

Here:
- `-type f` searches for regular files  
- `-mtime -2` means files modified within the last 2 days  

**Example:**
```bash
find /home -type f -mtime -2
```

This will list all files in `/home` that were modified in the last 2 days.

---

## How to find 10 largest files?

To find the 10 largest files in Linux, we use the `du`, `sort`, and `head` commands together.

**Command:**
```bash
du -ah /path | sort -rh | head -10
```

Here:
- `du -ah` shows size of all files and directories  
- `sort -rh` sorts them in reverse order (largest first)  
- `head -10` displays the top 10 results  

**Example:**
```bash
du -ah /home | sort -rh | head -10
```

---

## What permission is needed to delete a file?

To delete a file in Linux, you need **write (`w`) permission on the parent directory**, not on the file itself.

If you have write permission on the directory where the file exists, you can delete the file—even if you don’t have write permission on the file.

---

## How to check inode usage (`df -i`)?

To check inode usage in Linux, we use:

```bash
df -i
```

This command displays:
- Total number of inodes  
- Used inodes  
- Free inodes  
- Percentage of inode usage  

It helps identify if a system is running out of inodes, even if disk space is still available.

---

## What is a block device vs character device?

A **block device**:
- Stores and transfers data in fixed-size blocks  
- Allows random access (read/write at any location)  
- Examples: Hard disks, USB drives (e.g., `/dev/sda`)  

A **character device**:
- Transfers data one byte at a time  
- Works sequentially  
- Does not support random access  
- Examples: Keyboard, mouse, terminal devices (e.g., `/dev/tty`)  

**In simple terms:**  
Block devices are used for storage, and character devices are used for data stream devices.

---

## What is journaling in a filesystem (ext3/ext4)?

Journaling is a feature that keeps a **log (journal)** of changes before they are written to disk.

In `ext3` and `ext4` filesystems:
- It helps prevent data corruption during crashes or power failures  
- The journal allows faster recovery  
- Ensures filesystem consistency  

---

## Difference between soft mount and hard mount?

In Linux NFS mounts:

- **Soft mount**  
  - Stops retrying if the server is unavailable  
  - Returns an error after timeout  
  - Less reliable but prevents system hanging  

- **Hard mount**  
  - Keeps retrying until the server responds  
  - More reliable  
  - May cause the system to hang if the server is down  

---

## How to check filesystem type (`lsblk -f`, `blkid`)?

### 1. Using `lsblk -f`
```bash
lsblk -f
```
Lists:
- Block devices  
- Filesystem type  
- Label  
- UUID  

### 2. Using `blkid`
```bash
blkid
```
Displays detailed information about block devices including:
- Filesystem type  
- UUID  

Both commands help identify filesystem types (e.g., `ext4`, `xfs`, `vfat`).

---

## How to add/mount new swap space?

Follow these steps:

### 1. Create a swap file (Example: 2GB)
```bash
sudo fallocate -l 2G /swapfile
```

Or if `fallocate` is not available:
```bash
sudo dd if=/dev/zero of=/swapfile bs=1M count=2048
```

### 2. Set correct permissions
```bash
sudo chmod 600 /swapfile
```

### 3. Format the file as swap
```bash
sudo mkswap /swapfile
```

### 4. Enable the swap space
```bash
sudo swapon /swapfile
```

### 5. Verify swap is active
```bash
swapon --show
```

### 6. Make it permanent (add to `/etc/fstab`)
```
/swapfile swap swap defaults 0 0
```

This adds new swap space without requiring a reboot.