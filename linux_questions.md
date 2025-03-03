# Linux Interview questions

## 1. Linux Basics
<details><summary>Click here to see questions</summary>

-   Define the basic components of Linux.
    - Linux consists of the Kernel, Shell, File System, System Utilities, and User Applications.
- What is the Linux Kernel?
    - The core part of Linux, managing hardware, processes, and memory.
- What is Shell in Linux? Name a few shells.
    - A command-line interpreter; common shells include Bash, Zsh, Korn, and C Shell.
- What is LILO? Explain LILO.
    - A legacy bootloader that loads Linux into memory before execution
- What are the differences between Unix and Linux?
    - Linux is open-source and widely used, while Unix is proprietary and used in enterprise environments.
- How do you check the Linux version and distribution?
    - Use `uname -a` or `cat /etc/os-release`
- What are the different types of Linux distributions?
    - Popular ones include Ubuntu, Debian, Fedora, and Arch Linux.
- What is the purpose of the /bin, /sbin, /usr/bin, and /usr/sbin directories?
    - Purpose of **/bin, /sbin, /usr/bin, /usr/sbin** – These contain essential system binaries and user commands
</details>

## 2. File System & Permissions

- Elaborate all the file permissions in Linux.
    - Read (r), Write (w), and Execute (x) for owner, group, and others.
- What is the chmod command in Linux, and how do you use it?
    - Changes file permissions using symbolic (chmod u+x file) or numeric (chmod 755 file) modes.
- What is the chown command in Linux?
    - chown command – Changes file ownership (chown user:group file).
- What is the difference between hard links and soft links?
    - Hard vs. Soft links – Hard links reference the same inode, while soft links (symlinks) point to a file path.
- What is the difference between absolute and relative paths in Linux?
    - Absolute vs. Relative paths – Absolute starts from /, relative is from the current directory.
- How do users create a symbolic link in Linux?
    - Create a symbolic link – `ln -s target link_name`
- What is the umask command, and how does it work?
- How do you change file permissions recursively in Linux?
    - umask command – Defines default file permissions (umask 022 means new files get 755).
- What is the sticky bit, and how is it used?
    - Sticky bit – Ensures only the file owner can delete a file in a shared directory (chmod +t /tmp).
- What is `/etc/passwd` and `/etc/shadow` files?
    - `/etc/passwd` stores user info, `/etc/shadow` stores encrypted passwords.
- What is /etc/resolv.conf file in Linux?
    - `/etc/resolv.conf` – Defines DNS nameservers for internet resolution

## 3. Storage & File Management
- How do you mount and unmount filesystems in Linux?
    - `mount /dev/sdX /mnt` and `umount /mnt`
- How do you format a disk in Linux?
    - Format disk – `mkfs.ext4 /dev/sdX`
- How do you check disk space usage? What is the difference between df vs du?
    - df shows total space, du shows per-file usage.
- What is Swap Space in Linux?
- How do you resize a partition using fdisk or parted?
    - Virtual memory on disk, used when RAM is full (swapon -s)
- What is the purpose of Logical Volume Manager (LVM)?
    - Allows dynamic resizing of partitions (lvextend and lvreduce).
- How do you find the size of a specific directory?
    - `du -sh directory/`
- How do you search for files in Linux using find and locate?
    - Use find (find / -name filename) or locate filename.
- How do you recover deleted files in Linux?
    - Use extundelete or testdisk for EXT file systems

    ### 3.1 `lsof` based questions
    - What is lsof in Linux? How do you list all open files on a Linux system? How do you find all open files by a specific user? How do you find all open files for a specific process?
        - lsof (List Open Files) is a command-line utility that displays information about open files and the processes using them
        - `lsof` shows all open files by all processes.
        - `lsof -u username` lists files opened by a particular user.
        - `lsof -p <PID>` displays all files opened by a process with the given Process ID (PID).

    - How do you check which process is using a specific file? How do you find which process is using a specific port?
        - `lsof /path/to/file` shows which process is currently using the given file.
        - `lsof -i :80` checks which process is using port 80.

    - How do you list all network connections with lsof
        - `lsof -i`

    - How can lsof help resolve "file in use" errors?
        - Use lsof /path/to/file to check which process is using the file, then kill the process if necessary.

    - How do you check for deleted files still in use?
        - `lsof | grep deleted` lists deleted files still being used by running processes.

    - How do you check which files are opened by a specific group of processes (e.g., Apache, MySQL)
        - `lsof -u apache,mysql` lists files opened by Apache and MySQL users.

    - How do you monitor changes in open files in real-time?
        - `watch -n 1 lsof -i` refreshes the open file list every second.

## 4. Process Management
- How do you list all the processes running in Linux?
    - ps aux or top
- What are various process states in Linux?
    -  Running, Sleeping, Stopped, Zombie.
- How do you find the process ID (PID) of a running process?
    - pidof process_name or ps aux | grep process_name
- How do you end up with a zombie process?
    - A finished process that hasn't been removed by the parent.
- How can we identify a zombie process? And how to kill it?
   - Use `ps aux | grep Z` and kill the parent process.
- What is a daemonized process in Linux?
    - A background service process (e.g., sshd).
- What is the difference between a process and a thread?
    - A process is independent; threads share memory within a process.
- What do you understand about process scheduling in Linux?
    - Linux prioritizes tasks with the Completely Fair Scheduler (CFS)
- How do you change process priority in Linux?
- How do you run a process in the background and bring it back to the foreground?
    - Use & (background), fg (foreground).
- What is the difference between nohup, screen, and tmux?
    - nohup prevents termination, screen/tmux provides persistent sessions.
- What is nice and renice in Linux?
    - Adjusts process priority; `nice -n 10` process lowers priority.


## 5. System Administration & Performance Monitoring
- What is a Linux virtual memory system?
- What is runlevel in Linux? How to switch between two runlevels?
- How do you get a list of logged-in users?
    - List logged-in users – who or w
- How do you monitor CPU and memory usage in Linux?
    - Monitor CPU/memory – Use top, htop, or free -h
- How do you check the uptime of a Linux server?
    - Check uptime – uptime command
- How do you track system logs in Linux? Where are logs stored?
    - Track system logs – Logs are in /var/log/, journalctl for systemd.
- What is top, htop, and how do they differ?
    - top vs htop – htop is interactive, top is basic
- How do you check open ports in Linux?
    - Check open ports – `netstat -tulnp` or `ss -tulnp` or `lsof -i -P -n` or `nmap -p- localhost`
    - -t → Show TCP ports
    -   -u → Show UDP ports
    -   -l → Show listening ports
    -   -n → Show numeric addresses instead of resolving hostnames
    -   -p → Show process using the port    

## 6. Networking & Security
- How to disable SSH?
    - `systemctl stop sshd && systemctl disable sshd`
- How do you create passwordless SSH access?
    - Create passwordless SSH – Generate SSH keys (ssh-keygen), copy with ssh-copy-id user@host
- After creating passwordless SSH access, whenever I try to log in to a server, it asks me for the password, while I have verified that my public key is placed on the remote server.
- How will you change the default login shell for all upcoming users on Linux?
- How to set a username and password never to expire?
    - Set username/password to never expire – `chage -E -1 -M -1 username`
- What is the difference between iptables and firewalld?
    - iptables vs firewalld – iptables is rule-based; firewalld is dynamic and easier to configure.
- How do you check network connectivity in Linux?
    - Check network connectivity – Use `ping`, `traceroute`, and `netstat`.
- What is the purpose of /etc/hosts and /etc/hostname files?
- How do you troubleshoot network issues using ping, netstat, and traceroute?
- How do you find the IP address of a Linux system?
    - use `ip a` or `ifconfig`

## 7. Automation & Scheduling
- What is a cron job? How do you set up a new cron job to run multiple times a day?
    -  Edit crontab (`crontab -e`) with */5 * * * * command.
- How do you view the current cron jobs for a user?
    - `crontab -l`
- How do you schedule a one-time task in Linux?
    - Use at (echo "command" | at now + 5 minutes)
- What is at and batch in Linux scheduling?
    - at runs at a specific time, batch runs when system load is low.
- How do you run a script at startup in Linux?
    - Add it to `/etc/rc.local` or a `systemd service`

## 8. Boot Process & System Startup
- What is the Linux booting process?
    - BIOS → Bootloader (GRUB) → Kernel → Init/Systemd → Runlevel → Login.
- What happens in Linux, on a kernel level, when you type in ls -l?
    - Shell → System Call → Kernel → Filesystem → Output.
- What are the different stages of the Linux boot process?
    - POST → Bootloader → Kernel → Init/Systemd → User Space.
- What is GRUB, and how does it work?
    - Loads the kernel and allows OS selection.
- How do you change the default boot target in systemd?
    - systemctl set-default multi-user.target.
- What are init systems in Linux (SysVinit vs systemd)?
    - Init systems (SysVinit vs Systemd) – SysVinit uses scripts (/etc/init.d/), Systemd uses units (systemctl).


## 9. Text processing utilities

- what are some of the text processing utilities in linux?
    - awk
    - sed
    - grep
    - cut

## 10. Command Chaining & Input Handling
- what are some of the Command Chaining & Input Handling tools/commands:
    - sort
    - uniq
    - wc
    - head
    - tail




