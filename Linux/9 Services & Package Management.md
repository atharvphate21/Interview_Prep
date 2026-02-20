## How to manage services?
In Linux, we manage services using `systemctl`. To start a service: `systemctl start service_name`, stop it: `systemctl stop service_name`, enable it at boot: `systemctl enable service_name`, or check its status: `systemctl status service_name`. This controls background services efficiently.

## Difference between service and systemctl?
In Linux, `service` is an older command used to start, stop, or restart services on SysV init systems. `systemctl` is the modern command for managing services on `systemd` systems, offering more features like enabling at boot, checking status, and managing dependencies. `systemctl` is now preferred on most distributions.

## How to check service logs?
In Linux, we check service logs using `journalctl -u service_name`, which displays all logs related to that service. Adding `-f` shows live updates, and `--since "YYYY-MM-DD"` filters logs from a specific date. This helps troubleshoot and monitor service activity.

## What is journalctl?
In Linux, `journalctl` is a command used to view and manage logs collected by `systemd`. It allows you to see system, kernel, and service logs, filter by time, unit, or priority, and follow logs in real-time with `-f`, helping troubleshoot and monitor the system efficiently.

## What is yum, dnf, apt?
In Linux, **yum**, **dnf**, and **apt** are package managers used to install, update, and remove software. Yum and DNF are used on Red Hat–based systems (DNF is newer and faster), while Apt is used on Debian/Ubuntu systems. They handle dependencies automatically and simplify software management.

## How to install/remove package?
In Linux, we install packages using package managers like `yum install package_name` (RHEL/CentOS), `dnf install package_name` (Fedora), or `apt install package_name` (Debian/Ubuntu). To remove a package, use `yum remove package_name`, `dnf remove package_name`, or `apt remove package_name`. These commands handle dependencies automatically.

## What is repository?
In Linux, a repository is a storage location that contains software packages and updates. Package managers like `yum`, `dnf`, or `apt` use repositories to install, update, or remove software securely and efficiently from the system.

## How to configure repo?
In Linux, we configure a repository by adding its configuration file or URL to the system. For **RHEL/CentOS**, repo files go in `/etc/yum.repos.d/`. For **Debian/Ubuntu**, we add entries in `/etc/apt/sources.list` or `/etc/apt/sources.list.d/`. After adding, run `yum update` or `apt update` to refresh package metadata.

## How to check enabled/disabled services at boot (systemctl list-unit-files)?
In Linux, we can check which services are enabled or disabled at boot using `systemctl list-unit-files`. It lists all service unit files with their state (`enabled`, `disabled`, `static`, etc.), helping manage which services start automatically during system startup.

## How to reload service without restarting (systemctl reload)?
In Linux, we can reload a service without restarting it using `systemctl reload service_name`. This applies configuration changes without stopping the service, ensuring minimal disruption while updating settings.

## How to clean package cache? (yum clean all, apt clean)
In Linux, we can clean the package cache to free disk space. On Red Hat–based systems, use `yum clean all` or `dnf clean all`. On Debian/Ubuntu systems, use `apt clean`. This removes downloaded package files stored locally after installation.
