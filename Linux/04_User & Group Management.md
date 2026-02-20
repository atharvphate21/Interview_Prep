## Types of users in Linux?
In Linux, there are three types of users: **root**, **system**, and **normal users**. Root is the superuser with full system control, system users are created for running services and daemons, and normal users are regular accounts for daily tasks with limited permissions. This classification helps manage security and access efficiently.

## Difference between useradd and adduser?
In Linux, `useradd` is a low-level command to create a new user, usually requiring manual setup of home directory and password. `adduser` is a higher-level, user-friendly command that automatically creates the home directory, sets permissions, and prompts for a password. `adduser` is easier for interactive use, while `useradd` is more script-friendly.

## How to create/delete user?
In Linux, we create a user using `adduser username` or `useradd username`, which sets up the account and home directory. To delete a user, we use `userdel username`, and adding the `-r` option (`userdel -r username`) also removes the user’s home directory and files. These commands help manage system users efficiently.

## How to create/delete group?
In Linux, we create a group using `groupadd groupname` and delete a group using `groupdel groupname`. Groups help manage permissions for multiple users, allowing easier control over file and directory access.

## Explain fields of /etc/passwd, /etc/shadow, /etc/group, /etc/gshadow.
In Linux, these files store user and group information:

* **/etc/passwd** – Contains user account info: username, password placeholder (x), UID, GID, user info, home directory, and shell.
* **/etc/shadow** – Stores encrypted passwords and password settings like expiration, last change, and minimum/maximum days.
* **/etc/group** – Lists groups with group name, password placeholder, GID, and member users.
* **/etc/gshadow** – Stores secure group info, including group passwords, admins, and members.

These files together manage users, groups, and authentication securely.

## What is password aging?
In Linux, password aging is a feature that forces users to change their passwords after a certain period for security. It sets minimum, maximum, and warning days for passwords. We can view or set password aging using the `chage` command, helping prevent unauthorized access from old or compromised passwords.

## How to change user password?
In Linux, we can change a user’s password using the `passwd` command. For example, `passwd username` allows the admin to set a new password, while a normal user can change their own password by running `passwd`. This ensures secure authentication for each account.

## What is UID and GID?
In Linux, UID (User ID) is a unique number assigned to each user, and GID (Group ID) is a unique number assigned to each group. They are used by the system to identify users and groups for permissions and access control instead of using names. UID 0 is always reserved for the root user.

## How to add a user to multiple groups?
In Linux, we can add a user to multiple groups using the `usermod` command with the `-aG` option. For example: `usermod -aG group1,group2 username`. This appends the user to the listed groups without removing them from existing groups, allowing flexible access control.

## How to lock/unlock a user? (usermod -L/-U)
In Linux, we can lock a user account using `usermod -L username`, which prevents the user from logging in. To unlock the account, we use `usermod -U username`. This is useful for temporarily disabling accounts without deleting them.

## How to force password reset at next login?
In Linux, we can force a user to reset their password at the next login using the `chage -d 0 username` command. This sets the password’s last change date to 0, prompting the user to create a new password when they log in. It helps enforce security policies immediately.
