# Linux Fundamentals

## What is Linux?
Linux is an open-source, Unix-like operating system that manages computer hardware and software resources and allows users to interact with the system through a command-line or graphical interface. It is widely used in servers, cloud environments, and DevOps because it is secure, stable, and customizable.

## What is an Operating System?
An Operating System (OS) is system software that acts as an interface between the user and the computer hardware. It manages resources like CPU, memory, storage, and devices, and allows users to run applications smoothly and efficiently.

## Types of Operating Systems
There are several types of Operating Systems:
- **Batch OS** – executes tasks in batches without user interaction.
- **Time-Sharing OS** – allows multiple users to share system resources simultaneously.
- **Distributed OS** – manages multiple computers and makes them work as a single system.
- **Real-Time OS** – provides immediate response, used in critical systems.
- **Multiprocessing OS** – supports multiple CPUs.
- **Multi-User OS** – allows multiple users to access the system at the same time.

## Difference Between Linux and Unix
- Linux is open-source, developed by Linus Torvalds, and free to use, modify, and distribute.
- Unix is proprietary, developed at AT&T’s Bell Labs, and usually requires a license.
- Linux runs on a wide range of hardware including PCs and servers; Unix is mainly used in enterprise servers.
- Both are stable and secure, but Linux is more widely used today, especially in cloud and DevOps environments.

## Difference Between Linux and Windows
- Linux is open-source, free, highly customizable, mainly used in servers and cloud environments.
- Windows is proprietary, requires a license, and is widely used in personal computers and enterprise desktops.
- Linux is more secure and stable for servers; Windows is user-friendly and common for everyday applications.

## Linux Kernel
The Linux Kernel is the core component of the Linux operating system that directly interacts with the hardware. It manages system resources such as CPU, memory, devices, and processes, acting as a bridge between hardware and software applications.

## Basic Features of Linux
- Open-source
- Multi-user and multitasking
- Strong security and permission management
- Supports multiple file systems
- Command-line and graphical interfaces
- Stability, portability, and high performance

## Linux Distributions
Linux distributions are complete operating systems built using the Linux kernel along with system tools, libraries, and package managers.
- **Common Distros:** Ubuntu, CentOS, Red Hat Enterprise Linux (RHEL), Debian, Fedora

## Linux Architecture
Linux architecture is divided into layers:
1. **Hardware:** CPU, memory, disk, devices
2. **Kernel:** Core of Linux; manages processes, memory, device drivers, system calls
3. **Shell & System Libraries:** Interface between user applications and kernel
4. **User Applications:** Commands, tools, and software programs

## First Process in Linux (PID 1)
The first process is **init** (PID 1), parent of all processes, started by the kernel during system boot. In modern systems, **systemd** usually replaces init but still runs as PID 1.

## What is systemd?
systemd is a system and service manager that:
- Starts during boot (PID 1)
- Initializes the system
- Manages services and background processes
- Handles logging, device management, and scheduling

## Linux Boot Process
1. **BIOS/UEFI:** Initializes hardware, looks for bootable device
2. **Bootloader (GRUB):** Loads Linux kernel into memory
3. **Kernel:** Initializes hardware, mounts root filesystem, starts first process
4. **Init/Systemd (PID 1):** Starts system services and background processes
5. **User Login:** System ready for CLI or GUI login

## Runlevels / systemd Targets
- **Runlevels:** Predefined OS states (0-6), e.g., 0 = shutdown, 1 = single-user, 3 = multi-user, 5 = graphical, 6 = reboot
- **systemd Targets:** Modern equivalent, e.g., `multi-user.target` (runlevel 3), `graphical.target` (runlevel 5)

## GNU
GNU is a free and open-source project started by Richard Stallman to develop a complete Unix-like OS using free software (GCC, Bash, core utilities). Most Linux systems combine the Linux kernel and GNU tools → called **GNU/Linux**.

## Kernel Space vs User Space
- **Kernel Space:** Runs kernel, full access to hardware, privileged mode
- **User Space:** Runs user applications, limited access, communicates with kernel via system calls

## Daemon in Linux
A daemon is a background process that runs continuously without direct user interaction, providing system or application services (e.g., SSH daemon `sshd`).

## Shell and Types
A shell is a command-line interface to interact with Linux. Common types:
- Bash (Bourne Again Shell) – default
- sh (Bourne Shell)
- Zsh (Z Shell) – advanced features
- Ksh (Korn Shell)
- Csh (C Shell)

## Linux Process States
- **Running:** Executing or ready to run
- **Sleeping:** Waiting for a resource
- **Stopped:** Paused, can resume later
- **Zombie:** Finished execution, still in process table

## Linux vs UNIX Certification
- **Linux:** Open-source, no official certification required
- **UNIX:** Must be certified according to Single UNIX Specification (SUS)
- Linux is Unix-like but not officially UNIX-certified.
