## 1. **What is GRUB?**

* **GRUB** (Grand Unified Bootloader) is the bootloader used in Linux systems to load the operating system. It allows users to select which operating system or kernel to boot from during system startup.

## 2. **Difference between GRUB and LILO?**

* **GRUB**: Supports multiple operating systems, allows boot-time editing, and is more flexible (e.g., supports booting from networks and various file systems).
* **LILO**: An older bootloader, less flexible, no boot-time editing, and requires reconfiguration when the kernel or boot files are updated.

## 3. **How to reset root password?**

* To reset the root password:

  1. Reboot the system and enter **GRUB menu**.
  2. Select the boot entry and press `e` to edit.
  3. Find the line starting with `linux` and append `init=/bin/bash`.
  4. Press `Ctrl + X` to boot.
  5. Once at the shell, type:

     ```bash
     mount -o remount,rw /   # Remount the root filesystem as read-write
     passwd root            # Change the root password
     ```
  6. Reboot using `exec /sbin/init`.

## 4. **What happens when Linux boots?**

* When Linux boots:

  1. **BIOS/UEFI** runs a POST (Power-On Self-Test) and loads the bootloader (GRUB).
  2. GRUB loads the **kernel** into memory and passes control to it.
  3. The kernel initializes the system, including hardware detection and mounting the root filesystem.
  4. The **init process** is started (or **systemd** in modern systems).
  5. System services (like networking, login, etc.) are started based on configuration files (e.g., `/etc/init.d`, `/etc/systemd`).
  6. Finally, the user login prompt is shown, and the system is ready for use.
