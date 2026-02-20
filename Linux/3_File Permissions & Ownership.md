## Explain file permissions.
In Linux, file permissions control access to files and directories. There are three permissions: read, write, and execute, and they apply to three types of users: owner, group, and others. We can view permissions using ls -l and modify them using the chmod command. Permissions can be set symbolically or using numeric values like 755.

## What are default file permissions?
In Linux, default file permissions are the permissions assigned to a file or directory when it is created. By default, files are created with 666 permissions and directories with 777, but the final permissions are determined by the umask value. The umask subtracts permissions from the default to set more secure access. We can check the umask using the `umask` command.

## What is umask?
In Linux, umask is a default permission mask that determines the permissions assigned to newly created files and directories. It removes certain permissions from the system default values of 666 for files and 777 for directories. The umask value ensures better security by restricting unwanted access. We can check or set it using the `umask` command.

## What is chmod?
In Linux, `chmod` is a command used to change the permissions of a file or directory. It allows us to set read, write, and execute permissions for the owner, group, and others. Permissions can be changed using symbolic mode like `u+x` or numeric mode like `755`. This command helps control access and improve security.

## Difference between chmod +x and chmod +t?
In Linux, `chmod +x` is used to add execute permission to a file or directory, allowing it to be run as a program or accessed in case of a directory. On the other hand, `chmod +t` sets the sticky bit on a directory, which means only the file owner can delete or rename files inside that directory, even if others have write permission. The sticky bit is commonly used on shared directories like `/tmp` for security.

## What is SUID, SGID, Sticky Bit?
In Linux, SUID, SGID, and Sticky Bit are special permissions that provide additional access control. SUID allows a user to execute a file with the permissions of the file owner, while SGID allows execution with the group’s permissions or ensures new files inherit the directory’s group. The Sticky Bit restricts file deletion in a directory so only the file owner can delete their files. These special permissions improve security and are set using the `chmod` command.

## Difference between sudo and root?
In Linux, root is the superuser account that has complete control over the system. Sudo is a command that allows a normal user to execute specific administrative tasks with root privileges. Root has full access by default, while sudo provides temporary elevated access based on permissions defined in the sudoers file. Using sudo is considered more secure than logging in directly as root.

## Difference between root and normal user?
In Linux, the root user is the superuser with complete control over the entire system, including system files, user management, and configuration. A normal user has limited permissions and can access only their own files and allowed resources. Root can install software, modify system settings, and manage other users, while a normal user cannot perform administrative tasks without sudo privileges.

## How to create a sudo user?
In Linux, we can create a sudo user by first adding a new user using `adduser username`. Then, we give sudo privileges by adding the user to the sudo group with `usermod -aG sudo username`. After this, the user can run commands with root privileges using `sudo`. This ensures administrative tasks can be done securely without logging in as root.

## Purpose of /etc/sudoers?
In Linux, the `/etc/sudoers` file defines which users or groups can run commands with sudo privileges. It controls who can perform administrative tasks and what commands they are allowed to execute. This file ensures secure and controlled access to root-level operations. It should be edited using the `visudo` command to avoid errors.

## How to change ownership (chown / chgrp)?
In Linux, we use `chown` to change the owner of a file or directory and `chgrp` to change its group. For example, `chown user filename` changes the owner, and `chgrp groupname filename` changes the group. Both commands help control who can access or modify files. You can also change owner and group together using `chown user:group filename`.

## Difference between ACL and standard permissions?
In Linux, standard permissions (read, write, execute for owner, group, others) provide basic access control. ACL (Access Control List) allows more fine-grained control, letting you set permissions for multiple users or groups on a single file or directory. ACLs give flexibility beyond standard permissions, and we can manage them using `setfacl` and view with `getfacl`.

## How to view ACL permissions (getfacl)?
In Linux, we can view ACL permissions using the `getfacl` command. It shows the file or directory’s owner, group, standard permissions, and any additional ACL rules for specific users or groups. For example, `getfacl filename` displays all detailed access controls beyond standard permissions.
