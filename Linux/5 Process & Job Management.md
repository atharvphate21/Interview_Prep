# 1. Linux Fundamentals

## What is Linux?
->Linux is an open-source, Unix-like operating system that manages computer hardware and software resources and allows users to interact with the system through a command-line or graphical interface. It is widely used in servers, cloud environments, and DevOps because it is secure, stable, and customizable.

## What is an Operating System?
->An Operating System (OS) is system software that acts as an interface between the user and the computer hardware. It manages resources like CPU, memory, storage, and devices, and allows users to run applications smoothly and efficiently.

## What are types of Operating Systems?
There are several types of Operating Systems: Batch OS (executes tasks in batches without user interaction), Time-Sharing OS (allows multiple users to share system resources simultaneously), Distributed OS (manages multiple computers and makes them work as a single system), Real-Time OS (provides immediate response, used in critical systems), Multiprocessing OS (supports multiple CPUs), and Multi-User OS (allows multiple users to access the system at the same time).

## Differentiate between Linux and Unix.
Linux is an open-source, Unix-like operating system developed by Linus Torvalds, while Unix is a proprietary operating system originally developed at AT&T’s Bell Labs. Linux is free to use, modify, and distribute, whereas most Unix systems are commercial and require a license. Linux runs on a wide range of hardware including PCs and servers, while Unix is mainly used in enterprise servers and high-end systems. Both are stable and secure, but Linux is more widely used today, especially in cloud and DevOps environments.

## Difference between Linux and Windows.
Linux is an open-source operating system, while Windows is a proprietary operating system developed by Microsoft. Linux is free to use, highly customizable, and mainly used in servers and cloud environments, whereas Windows requires a license and is commonly used in personal computers and enterprise desktops. Linux is more secure and stable for server environments, while Windows is more user-friendly and widely used for everyday applications and gaming.

## Define Linux Kernel.
The Linux Kernel is the core component of the Linux operating system that directly interacts with the hardware. It manages system resources such as CPU, memory, devices, and processes, and acts as a bridge between hardware and software applications. Without the kernel, the operating system cannot function.

## What are the basic features of Linux?
The basic features of Linux are that it is open-source, multi-user, and multitasking. It provides strong security and permission management, supports multiple file systems, and offers both command-line and graphical interfaces. Linux is also known for its stability, portability, and high performance, which makes it widely used in servers and cloud environments.

## What are Linux distributions? Name common distros.
Linux distributions are complete operating systems built using the Linux kernel along with system tools, libraries, and package managers. They provide a ready-to-use environment for users.
Some common Linux distributions are Ubuntu, CentOS, Red Hat Enterprise Linux (RHEL), Debian, and Fedora.

## Explain Linux architecture.
Linux architecture is divided into layers. At the bottom is the Hardware (CPU, memory, disk, devices). Above that is the Kernel, which is the core of Linux and manages processes, memory, device drivers, and system calls. Above the kernel is the Shell and System Libraries, which allow users and applications to communicate with the kernel. At the top are User Applications, such as commands, tools, and software programs.
In simple terms, users interact with applications, applications communicate with the kernel, and the kernel controls the hardware.

## What is the first process in Linux? (PID 1)
The first process in Linux is init (PID 1). It is the parent of all processes and is started by the kernel during system boot. Its main responsibility is to initialize the system, start essential services, and manage other processes. In modern Linux systems, systemd usually replaces the traditional init process, but it still runs as PID 1.

## What is systemd?
systemd is a system and service manager in modern Linux systems. It is the first process started during boot (PID 1) and is responsible for initializing the system, starting and managing services, handling background processes, and maintaining system state. It also manages tasks like logging, device management, and scheduling services.

## Explain the Linux boot process.
The Linux boot process happens in the following steps:
- BIOS/UEFI – When the system is powered on, BIOS or UEFI initializes the hardware and looks for a bootable device.
- Bootloader (GRUB) – The bootloader loads the Linux kernel into memory.
- Kernel – The kernel initializes hardware, mounts the root file system, and starts the first process.
- Init/Systemd (PID 1) – systemd starts system services and background processes.
- User Login – The system becomes ready, and the user can log in through CLI or GUI.

In simple terms, the system powers on → bootloader loads the kernel → kernel starts system services → system becomes ready for use.

## What are runlevels / systemd targets?
Runlevels are predefined operating states in Linux that determine which services and processes are running. In older systems using init, runlevels ranged from 0 to 6, where each number represented a different system state (for example, 0 = shutdown, 1 = single-user mode, 3 = multi-user mode, 5 = graphical mode, 6 = reboot).
In modern Linux systems using systemd, runlevels are replaced by systemd targets. Targets serve the same purpose but are more flexible and descriptive, such as multi-user.target (similar to runlevel 3) and graphical.target (similar to runlevel 5).

## What is GNU?
GNU is a free and open-source project started by Richard Stallman to develop a complete Unix-like operating system made entirely of free software. It provides important tools like the GNU Compiler (GCC), shell (Bash), and core utilities. In most Linux systems, the operating system is actually a combination of the Linux kernel and GNU tools, which is why it is sometimes called GNU/Linux.

## Difference between kernel space and user space?
Kernel space and user space are two separate memory areas in an operating system.
Kernel space is where the kernel runs and has full access to hardware and system resources like CPU, memory, and devices. It operates in a privileged mode, so it can execute critical system operations.
User space is where user applications and programs run. It has limited access to hardware and cannot directly interact with system resources. Instead, it uses system calls to request services from the kernel.
In simple terms, user space runs applications, and kernel space controls the system and hardware securely.

## What is a daemon in Linux?
A daemon in Linux is a background process that runs continuously without direct user interaction and provides system or application services. It usually starts during system boot and runs in the background to handle tasks like web services, logging, or scheduling. For example, the SSH daemon (sshd) allows remote login to the system.

## What is a shell? Types of shells? (bash, sh, zsh, etc.)
A shell is a command-line interface that allows users to interact with the Linux operating system by entering commands. It acts as a bridge between the user and the kernel, interpreting commands and executing them.
Common types of shells are Bash (Bourne Again Shell), which is the default in most Linux systems; sh (Bourne Shell), the original Unix shell; Zsh (Z Shell), which offers advanced features and customization; Ksh (Korn Shell); and Csh (C Shell).

## Explain Linux process states (running, sleeping, zombie, stopped).
Linux processes go through different states during their lifecycle:
- Running – The process is either currently executing on the CPU or ready to run.
- Sleeping – The process is waiting for a resource, such as user input, file access, or I/O operation.
- Stopped – The process has been paused, usually by a signal, and can be resumed later.
- Zombie – The process has finished execution, but its entry still exists in the process table because the parent process has not yet read its exit status.
These states help the system manage processes efficiently.

## Difference between Linux and UNIX certification (Single UNIX Spec).
Linux is an open-source operating system built around the Linux kernel, and it does not require any official certification to be called Linux.
UNIX, on the other hand, is a trademarked operating system standard. To be officially called UNIX, an operating system must be certified according to the Single UNIX Specification (SUS), which ensures it follows specific standards and compliance rules.
In simple terms, Linux is Unix-like but not officially UNIX-certified, while UNIX systems must pass formal certification to use the UNIX name.
