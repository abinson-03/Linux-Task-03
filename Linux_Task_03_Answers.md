# Linux Task 03: Process Management, System Monitoring & Basic Shell Scripting

Here are the solutions, explanations, and necessary scripts for the tasks outlined in your assignment. Since you are using Windows, you can either run these commands in a Linux environment (like WSL - Windows Subsystem for Linux, an Ubuntu VM, or a dedicated Linux machine) or use these provided answers directly for your assignment submission.

---

## Part A: Process Monitoring

When you run commands like `ps`, `ps aux`, `top`, and `htop`, you are interacting with process monitoring tools. 

**Answers:**

1. **What is a Process?**
   A process is an instance of a running computer program. When you execute a command or start an application in Linux, the kernel creates a process to track its execution state, memory allocation, and resource usage.

2. **What is a PID?**
   A PID (Process ID) is a unique numerical identifier assigned to each running process by the operating system kernel. PIDs are used by commands (like `kill` or `top`) to specify which process to manipulate.

3. **Which process is consuming the most CPU?**
   *To find this: Run `top` or `htop`. By default, processes are sorted by CPU usage. The process at the very top of the list is consuming the most CPU.*

4. **Which process is consuming the most Memory?**
   *To find this: In `top`, press `Shift + M` to sort the list by memory usage. In `htop`, you can click on the `MEM%` column header to sort by memory. The process at the top will be the one consuming the most RAM.*

---

## Part B: Process Management

**Steps:**
1. Open a new terminal and run: `sleep 300` (This creates a process that simply waits for 300 seconds).
2. Open another terminal and find the process using: `ps aux | grep sleep`
3. You will see an output showing the `sleep` process and its PID (e.g., `12345`).

**Documentation:**

* **PID found:** *(Example: 12345)* - *Note: You'll need to use the actual PID shown in your terminal.*
* **Command used:** `kill 12345` (or `kill -9 12345` for a forceful termination).
* **Result:** The process is terminated. If you used `kill`, it sends a `SIGTERM` signal asking the process to gracefully exit. If you used `kill -9`, it sends a `SIGKILL` signal, instantly destroying the process.

---

## Part C: System Monitoring

When you run `free -h`, `df -h`, `uptime`, and `uname -a`, you gather system information.

**Record (Example Output):**

* **Total RAM:** *Look at the `total` column in the `Mem:` row from `free -h`.* (e.g., `15Gi`)
* **Available RAM:** *Look at the `available` column in the `Mem:` row from `free -h`.* (e.g., `8.2Gi`)
* **Disk Usage:** *Look at the `Use%` and `Avail` columns for the root `/` filesystem from `df -h`.* (e.g., `45% used`)
* **System Uptime:** *From the `uptime` command.* (e.g., `up 2 days, 4:15`)
* **Kernel Version:** *From `uname -a`.* (e.g., `Linux ubuntu 5.15.0-76-generic`)

**Simple System Summary Report:**
```text
SYSTEM SUMMARY REPORT
---------------------
Kernel Version: Linux ubuntu 5.15.0-76-generic
System Uptime: up 2 days, 4:15
Total Memory: 15 GiB
Available Memory: 8.2 GiB
Root Disk Usage: 45% Used
```

---

## Part D: Service Monitoring

**Answers:**

1. **What is a Service?**
   A service (also known as a daemon in Linux) is a background process that runs continuously, waiting to perform specific tasks or handle requests. Examples include web servers, SSH servers, and networking managers.

2. **Why are services important?**
   They provide essential functionality without requiring manual user intervention. They run independently of user sessions, ensuring that core system functions (like networking, scheduling, or remote access) are always available.

3. **How can a stopped service affect a system?**
   Stopping a service breaks the functionality it provides. For example, if `NetworkManager` is stopped, the system might lose network connectivity. If `ssh` is stopped, remote users will be unable to log into the system.

---

## Part E: Shell Scripting

Here is the code for the `system_report.sh` script requested in the assignment.

### `system_report.sh`

```bash
#!/bin/bash

echo "==============================="
echo "        SYSTEM REPORT          "
echo "==============================="

# Display Current User
echo "Current User : $(whoami)"

# Display Hostname
echo "Hostname     : $(hostname)"

# Display Date & Time
echo "Date & Time  : $(date)"

echo "==============================="
```

### How to use it:
1. Create the file: `nano system_report.sh`
2. Paste the code above into the file and save it.
3. Make it executable: `chmod +x system_report.sh`
4. Run the script: `./system_report.sh`
