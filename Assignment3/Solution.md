# **Assignment 3**

A client has a Linux server that has just paged you because of a high load average issue. Upon connecting and running uptime you see: 12:20:50 up 1 day, 10:52, 6 users, load average: 44.28, 33.34, 30.44 How would you troubleshoot this issue to find out what is the source of the load and what tools would you use? Please also list what you would look for in the output of the commands you would run.

# Solution

1. Check the %CPU in the Server and Identify processes consuming a high percentage of CPU and memory by following commands.

* `top `
* `htop`

2. Montor Linux average CPU load and disk utilization and average wait times

* `iostat`

    If iostat is not found, it can be installed with:`apt install sysstat`

3. Analyze System Processes, we can look for high CPU and memory usage by specific processes

* `ps aux --sort=-%cpu | head `
* `ps aux --sort=-%mem | head`

4. Check Virtual memory statistics, Memory and swap space statistics to identify issues with memory pressure and Swap usage and page faults

* `vmstat 3`
* `vmstat -a`

    Tool to display information about the system's memory usage

    `free -h`

5. Check Disk Space and Inodes

* `df -h`

6. Check network connections and statistics.

* `netstat -tulnp`

    if iostat is not found, it can be installed with:` apt install net-tools`

7. If a process is consuming excessive CPU, and it's not critical or malfunctioning, terminate it.

* `kill -9` `<PID>`
