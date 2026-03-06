# Operating Systems Basics

## Key Topics
- What an operating system is and what it does
- Windows basics
- Linux CLI basics
- Windows CLI basics
- OS security fundamentals

---

## Introduction — What Is an Operating System?

An **operating system (OS)** is the software that sits between the user and the hardware. It manages all the physical resources of a computer and provides an environment for applications to run.

### What the OS Does

| Function              | What It Means                                                               |
|-----------------------|-----------------------------------------------------------------------------|
| Process Management    | Runs, schedules, and stops programs                                         |
| Memory Management     | Allocates RAM to programs and frees it when done                            |
| File System Management| Organises how data is stored and retrieved on disk                          |
| Device Management     | Communicates with hardware via drivers                                      |
| User Interface        | Provides a GUI or CLI for the user to interact with the system              |
| Security & Access     | Controls who can log in and what they can access                            |

### Common Operating Systems

| OS            | Common Use                              |
|---------------|-----------------------------------------|
| Windows       | Personal computers, enterprise desktops |
| Linux         | Servers, cybersecurity, development     |
| macOS         | Apple devices, creative professionals   |
| Android / iOS | Mobile devices                          |

> The OS is the foundation everything else runs on — understanding it is essential for both development and security.

---

## Windows Basics

Windows is the most widely used desktop OS in the world, making it a key target and environment to understand.

### Key Components

| Component         | Purpose                                                                 |
|-------------------|-------------------------------------------------------------------------|
| Desktop           | The main graphical workspace                                            |
| File Explorer     | Browse and manage files and folders                                     |
| Task Manager      | View and manage running processes, CPU, and memory usage                |
| Control Panel     | Manage system settings, users, and hardware                             |
| Registry          | A database storing OS and application configuration settings            |
| Active Directory  | Manages users, devices, and permissions across a network (enterprise)   |

### Windows File System

| Path                        | What's Stored There                                      |
|-----------------------------|----------------------------------------------------------|
| `C:\Windows\`               | Core OS files                                            |
| `C:\Windows\System32\`      | Critical system executables and DLLs                     |
| `C:\Users\<username>\`      | User-specific files, desktop, downloads, documents       |
| `C:\Program Files\`         | Installed 64-bit applications                            |
| `C:\Program Files (x86)\`   | Installed 32-bit applications                            |
| `C:\Temp\`                  | Temporary files                                          |

### Windows User Account Types

| Account Type   | Access Level                                              |
|----------------|-----------------------------------------------------------|
| Administrator  | Full control — install software, change settings, manage users |
| Standard User  | Limited — can use apps but can't make system changes      |
| Guest          | Minimal access, often disabled by default                 |
| SYSTEM         | Highest privilege — used internally by the OS             |

---

## Linux CLI Basics

The Linux command line is a powerful way to interact with the system — essential for cybersecurity work.

### Navigation & File Management

| Command              | Purpose                                      |
|----------------------|----------------------------------------------|
| `pwd`                | Print current working directory              |
| `ls`                 | List files in directory                      |
| `ls -la`             | List all files including hidden, with details|
| `cd <dir>`           | Change directory                             |
| `cd ..`              | Go up one directory                          |
| `mkdir <name>`       | Create a new directory                       |
| `touch <file>`       | Create a new empty file                      |
| `cp <src> <dst>`     | Copy a file                                  |
| `mv <src> <dst>`     | Move or rename a file                        |
| `rm <file>`          | Delete a file                                |
| `rm -R <dir>`        | Delete a directory and its contents          |
| `cat <file>`         | Print file contents to terminal              |
| `file <file>`        | Identify the file type                       |

### System & User Commands

| Command              | Purpose                                      |
|----------------------|----------------------------------------------|
| `whoami`             | Show current logged-in user                  |
| `id`                 | Show user ID and group memberships           |
| `uname -a`           | Display system and kernel information        |
| `ps aux`             | List all running processes                   |
| `top`                | Live view of processes and resource usage    |
| `sudo <command>`     | Run a command as root/administrator          |
| `su <user>`          | Switch to another user                       |
| `passwd`             | Change user password                         |
| `man <command>`      | Open the manual page for a command           |

### Networking Commands

| Command              | Purpose                                      |
|----------------------|----------------------------------------------|
| `ifconfig` / `ip a`  | Show network interfaces and IP addresses     |
| `ping <host>`        | Test connectivity to a host                  |
| `netstat -tulnp`     | Show open ports and listening services       |
| `curl <url>`         | Make an HTTP request from the terminal       |
| `wget <url>`         | Download a file from the internet            |
| `ssh user@host`      | Connect to a remote machine securely         |

### Key Directories

| Directory  | Contents                                                        |
|------------|-----------------------------------------------------------------|
| `/`        | Root — top of the file system                                   |
| `/etc`     | System configuration files                                     |
| `/home`    | User home directories                                           |
| `/var`     | Variable data — logs, databases, mail                           |
| `/tmp`     | Temporary files, writable by all users, cleared on reboot       |
| `/bin`     | Essential user binaries (ls, cp, cat, etc.)                     |
| `/root`    | Home directory for the root user                                |

---

## Windows CLI Basics

Windows has two main command-line interfaces: **Command Prompt (cmd)** and **PowerShell**.

### Command Prompt (cmd)

| Command                    | Purpose                                         |
|----------------------------|-------------------------------------------------|
| `dir`                      | List files in current directory                 |
| `cd <path>`                | Change directory                                |
| `mkdir <name>`             | Create a new folder                             |
| `del <file>`               | Delete a file                                   |
| `copy <src> <dst>`         | Copy a file                                     |
| `move <src> <dst>`         | Move or rename a file                           |
| `cls`                      | Clear the terminal screen                       |
| `ipconfig`                 | Show network interfaces and IP addresses        |
| `ipconfig /all`            | Detailed network information                    |
| `ping <host>`              | Test network connectivity                       |
| `netstat -ano`             | Show active connections and listening ports     |
| `tasklist`                 | List running processes                          |
| `taskkill /PID <id> /F`    | Force kill a process by its PID                 |
| `whoami`                   | Show current user                               |
| `net user`                 | List all local user accounts                    |
| `systeminfo`               | Display detailed system information             |

### PowerShell

PowerShell is more powerful than cmd — it uses **cmdlets** and can interact with the OS at a deeper level.

| Command                            | Purpose                                      |
|------------------------------------|----------------------------------------------|
| `Get-ChildItem` / `ls`             | List files in directory                      |
| `Set-Location <path>` / `cd`       | Change directory                             |
| `Get-Content <file>` / `cat`       | Print file contents                          |
| `Copy-Item <src> <dst>`            | Copy a file                                  |
| `Remove-Item <file>`               | Delete a file                                |
| `Get-Process`                      | List running processes                       |
| `Stop-Process -Id <id>`            | Kill a process by ID                         |
| `Get-NetIPAddress`                 | Show network IP addresses                    |
| `Invoke-WebRequest <url>`          | Make a web request (like curl)               |
| `Get-LocalUser`                    | List local user accounts                     |
| `whoami`                           | Show current user                            |

> PowerShell is widely used in both administration and offensive security — many attacks and scripts are PowerShell-based.

---

## OS Security

### Common OS Attack Vectors

| Attack Vector             | Description                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| Privilege Escalation      | Exploiting misconfigurations to gain higher access (e.g. user → admin)     |
| Unpatched Vulnerabilities | Exploiting known flaws in outdated OS versions                              |
| Weak Credentials          | Default or reused passwords on local/admin accounts                         |
| Malware                   | Malicious software that compromises the OS (ransomware, keyloggers, etc.)  |
| Misconfigured Permissions | Files or services with overly broad access                                  |
| Living off the Land       | Attackers using built-in OS tools (like PowerShell or cmd) to avoid detection |

### Windows Security Features

| Feature                     | Purpose                                                               |
|-----------------------------|-----------------------------------------------------------------------|
| Windows Defender            | Built-in antivirus and threat protection                              |
| Windows Firewall            | Controls inbound and outbound network traffic                         |
| UAC (User Account Control)  | Prompts for confirmation before allowing elevated actions             |
| BitLocker                   | Full disk encryption to protect data at rest                          |
| Windows Update              | Patches known vulnerabilities with security updates                   |
| Event Viewer                | Logs system, security, and application events for analysis            |

### Linux Security Features

| Feature           | Purpose                                                                     |
|-------------------|-----------------------------------------------------------------------------|
| File Permissions  | `rwx` model controls who can read, write, or execute each file              |
| sudo / root       | Limits which users can run privileged commands                              |
| UFW / iptables    | Firewall tools to control network traffic                                   |
| SSH Keys          | More secure than passwords for remote authentication                        |
| AppArmor / SELinux| Restrict what applications can access at the kernel level                   |
| Logs (`/var/log`) | Store system and auth events for monitoring and forensics                   |

### General OS Security Best Practices

- Keep the OS and software **fully patched and up to date**
- Follow the **principle of least privilege** — users only get the access they need
- **Disable unused services and ports** to reduce the attack surface
- Use **strong, unique passwords** and enable multi-factor authentication
- **Monitor logs** regularly for unusual activity
- Run **antivirus / EDR** software on endpoints
- Encrypt sensitive data at rest and in transit

---

## Takeaways
- The OS manages all hardware and software — it's the core of every system
- Windows dominates enterprise desktops, Linux dominates servers and security work
- CLI fluency in both Windows and Linux is essential for any security professional
- Most attacks target the OS layer — misconfigured permissions, unpatched flaws, weak credentials
- Security is built into modern OSes but requires correct configuration to be effective
