## How to check IP address?
In Linux, we can check the IP address using the `ip addr` or `ifconfig` command. It shows network interfaces, their IPv4 and IPv6 addresses, and status, helping identify how the system is connected to the network.

## What is ifconfig vs ip command?
In Linux, `ifconfig` is an older command used to view and configure network interfaces. The `ip` command is newer and more powerful, allowing you to manage IP addresses, routes, and links with more options. `ip` is preferred on modern systems.

## What is netstat?
In Linux, `netstat` is a command that displays network connections, routing tables, and interface statistics. It helps monitor active TCP/UDP connections, listening ports, and network activity, useful for troubleshooting and network monitoring.

## What is ss command?
In Linux, the `ss` command is used to display detailed information about network sockets, including TCP, UDP, and listening ports. It is faster and more powerful than `netstat`, helping monitor network connections and troubleshoot network issues efficiently.

## How to check open ports?
In Linux, we can check open ports using `ss -tuln` or `netstat -tuln`, which list all listening TCP and UDP ports. We can also use `lsof -i` or `nmap` to see active connections and services running on specific ports.

## What is ping?
In Linux, `ping` is a command used to check network connectivity between your system and another host. It sends ICMP echo requests and measures response time, helping verify if a host is reachable and the network is working properly.

## What is traceroute?
In Linux, `traceroute` is a command that shows the path packets take from your system to a destination host. It lists all intermediate routers and the time taken for each hop, helping diagnose network delays or connectivity issues.

## What is nslookup/dig?
In Linux, `nslookup` and `dig` are commands used to query DNS servers for domain name information. `nslookup` provides basic DNS resolution, while `dig` gives detailed information about DNS records, response time, and server used, useful for troubleshooting domain and network issues.

## What is DNS?
In Linux, DNS (Domain Name System) is a system that translates human-readable domain names like `example.com` into IP addresses. It allows computers to locate and communicate with each other over a network or the internet. DNS ensures users can access websites without remembering numeric IPs.

## What is /etc/hosts?
In Linux, `/etc/hosts` is a file that maps hostnames to IP addresses locally on the system. It is checked before DNS queries and is used to resolve names for network communication or testing without relying on external DNS servers.

## What is SSH?
In Linux, SSH (Secure Shell) is a protocol used to securely connect to remote systems over a network. It provides encrypted communication for logging in, executing commands, and transferring files, ensuring data and credentials remain safe from eavesdropping.

## How to troubleshoot network issue?
In Linux, to troubleshoot network issues, start by checking connectivity with `ping` or `traceroute`. Verify interface status with `ip addr` or `ifconfig`, check open ports with `ss` or `netstat`, and review routing using `ip route`. Logs, DNS tests (`nslookup`/`dig`), and firewall rules also help identify the problem.

## What is firewall?
In Linux, a firewall is a system that controls incoming and outgoing network traffic based on defined rules. It helps protect the system from unauthorized access, attacks, and unwanted connections. Tools like `iptables`, `firewalld`, or `ufw` are commonly used to manage firewalls.

## Difference between iptables and firewalld?
In Linux, `iptables` is a low-level tool to define detailed firewall rules manually, while `firewalld` is a higher-level, dynamic firewall manager that uses zones and services for easier rule management. `firewalld` provides flexibility without restarting the firewall, whereas `iptables` requires manual rule changes and reloads.

## How to change hostname temporarily and permanently?
In Linux, we can change the hostname temporarily using `hostname newname`, which lasts until the next reboot. To change it permanently, edit `/etc/hostname` with the new name and update `/etc/hosts` if needed, or use `hostnamectl set-hostname newname` for systems with `systemd`.

## How to restart network service (systemctl restart network)?
In Linux, we can restart the network service using `systemctl restart network` (or `NetworkManager` on some systems). This stops and starts network interfaces, applying any configuration changes without rebooting the system.

## What is netcat (nc) and its uses?
In Linux, `netcat` (or `nc`) is a networking utility used to read and write data over TCP or UDP connections. It is commonly used for testing open ports, troubleshooting network connectivity, transferring files, and creating simple client-server connections. It is a powerful tool for network debugging and scripting.

## Difference between TCP and UDP?
In Linux, TCP (Transmission Control Protocol) is connection-oriented, reliable, and ensures data arrives in order. UDP (User Datagram Protocol) is connectionless, faster, but does not guarantee delivery or order. TCP is used for applications like web browsing, while UDP is used for streaming or gaming where speed is more important than reliability.
