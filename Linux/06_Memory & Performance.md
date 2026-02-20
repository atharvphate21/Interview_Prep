## What is virtual memory?
In Linux, virtual memory is a memory management technique that uses both RAM and disk space (swap) to give processes the illusion of having more memory than physically available. It allows the system to run large programs and multitask efficiently by temporarily storing inactive data on disk.

## Difference between buffer and cache?
In Linux, a **buffer** is memory used by the kernel to store data temporarily while moving it between devices (like disk or network). A **cache** is memory used to store frequently accessed data to speed up read operations. Buffers help with I/O operations, while cache improves overall system performance.

## Difference between free memory and available memory?
In Linux, **free memory** is the portion of RAM that is completely unused, while **available memory** includes free memory plus memory that can be reclaimed from caches and buffers. Available memory gives a more accurate idea of how much memory can be used by new processes.

## What is swap?
In Linux, swap is a portion of disk space used as an extension of RAM when physical memory is full. It allows the system to continue running by moving inactive pages from RAM to disk. Swap helps prevent out-of-memory errors but is slower than using actual RAM.

## How to check memory usage?
In Linux, we can check memory usage using commands like `free -h`, which shows total, used, and available memory and swap. We can also use `top` or `htop` for a real-time view of memory usage by processes.

## How to check swap usage (swapon -s)?
In Linux, we can check swap usage using the `swapon -s` command. It lists all active swap partitions and files, showing their size, used space, and priority. This helps monitor and manage virtual memory usage.

## What is vmstat?
In Linux, `vmstat` is a command that reports virtual memory, CPU, and system performance statistics. It shows information like memory usage, swap activity, I/O, and process activity, helping monitor system health and diagnose performance issues.

## What is iostat?
In Linux, `iostat` is a command that reports CPU and input/output (I/O) statistics for devices and partitions. It shows read/write rates, utilization, and throughput, helping monitor disk performance and identify I/O bottlenecks.

## How to troubleshoot high CPU usage?
In Linux, to troubleshoot high CPU usage, first use `top` or `htop` to identify processes consuming CPU. Check their PID, user, and command. You can then stop or renice heavy processes using `kill` or `renice`. Monitoring logs and system metrics helps find underlying causes like runaway scripts or misbehaving services.

## How to optimize Linux performance?
In Linux, we can optimize performance by monitoring CPU, memory, and disk usage using `top`, `htop`, `vmstat`, and `iostat`. Clean unnecessary services, manage swap efficiently, use caching, and tune system parameters. Also, remove unused files, optimize applications, and keep the system updated to ensure smooth performance.

## Difference between soft limit and hard limit (ulimit)?
In Linux, a **soft limit** is the current resource limit a user can reach, while a **hard limit** is the maximum allowed value that cannot be exceeded without root privileges. Soft limits can be increased up to the hard limit, and both are managed using the `ulimit` command to control system resource usage.

## How to monitor real-time system stats (htop, sar)?
In Linux, we can monitor real-time system stats using `htop` or `sar`. `htop` provides an interactive view of CPU, memory, and processes with sorting and filtering options. `sar` collects and reports historical and current performance data for CPU, memory, I/O, and network, helping track system health over time.
