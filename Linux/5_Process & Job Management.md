## What is a process?
In Linux, a process is a running instance of a program. Each process has a unique PID (Process ID), uses system resources like CPU and memory, and can be managed using commands like `ps`, `top`, or `kill`. Processes can run in the foreground or background.

## What is PID and PPID?
In Linux, PID (Process ID) is a unique number assigned to each running process. PPID (Parent Process ID) is the PID of the process that started or spawned the current process. These IDs help track and manage process relationships in the system.

## What is Zombie process?
In Linux, a zombie process is a process that has finished execution but still has an entry in the process table. It occurs when the parent process has not read the child’s exit status using `wait()`. Zombies don’t use CPU but occupy system memory until cleared.

## What is orphan process?
In Linux, an orphan process is a running process whose parent has terminated. Orphan processes are automatically adopted by the `init` process (PID 1) to ensure they are properly managed and do not remain unmanaged in the system.

## Difference between process and thread?
In Linux, a process is an independent program running with its own memory and resources, while a thread is a smaller unit within a process that shares the same memory and resources with other threads of that process. Threads are lighter, faster, and used for concurrent execution inside a process.

## How to list running processes?
In Linux, we can list running processes using the `ps` command for a snapshot or `top`/`htop` for a dynamic view. `ps aux` shows all processes with details like PID, CPU, and memory usage, helping monitor and manage system activity.

## Difference between ps and top?
In Linux, `ps` shows a static snapshot of running processes at the moment you run it, while `top` provides a dynamic, real-time view of processes, updating continuously. `ps` is good for quick checks, and `top` is useful for monitoring system performance.

## Explain top command.
In Linux, the `top` command shows a real-time view of running processes and system resource usage, including CPU, memory, and load. It displays PID, user, CPU%, memory%, and process status. You can interact with it to sort, kill, or renice processes, making it useful for monitoring system performance.

## What is nice and renice?
In Linux, `nice` is used to start a process with a specific priority, affecting how the CPU schedules it. `renice` changes the priority of an already running process. Higher nice values lower priority, and lower values increase priority, helping manage CPU resources efficiently.

## How to change priority of process?
In Linux, we can change a process’s priority using `nice` when starting it, for example `nice -n 10 command`. For running processes, we use `renice`, for example `renice -n 5 -p PID`. Lower values increase priority, and higher values decrease it, controlling CPU allocation.

## What is load average?
In Linux, load average shows the average number of processes waiting to run over a period of time. It is displayed as three numbers representing 1, 5, and 15 minutes. Load average helps monitor system performance and CPU workload.

## How to kill a process?
In Linux, we can kill a process using the `kill` command followed by its PID, for example `kill 1234`. For forceful termination, we use `kill -9 1234`. We can also use `pkill process_name` or `killall process_name` to terminate by name instead of PID.

## How to run a job in background / foreground? (&, fg, bg)
In Linux, we can run a job in the background by adding `&` at the end of a command, like `command &`. To bring a background job to the foreground, we use `fg`, and to move a suspended job to the background, we use `bg`. These commands help manage multiple tasks in a terminal efficiently.

## How to stop a process temporarily? (Ctrl+Z)
In Linux, we can stop (suspend) a running process temporarily by pressing `Ctrl+Z`. This pauses the process and puts it in the background as a stopped job. We can later resume it in the foreground with `fg` or in the background with `bg`.

## How to list background jobs? (jobs)
In Linux, we can list background or suspended jobs in the current shell using the `jobs` command. It shows job IDs, status (running, stopped), and the command name, helping manage multiple tasks in the terminal.

## Difference between kill, kill -9, pkill, and killall
In Linux:

* `kill PID` – Sends a default termination signal (SIGTERM) to a specific process by PID.
* `kill -9 PID` – Forcefully kills a process using SIGKILL, which cannot be ignored.
* `pkill process_name` – Kills processes by name instead of PID.
* `killall process_name` – Terminates all processes with the given name.

These commands provide different ways to stop processes safely or forcefully.
