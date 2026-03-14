# Windows Command Prompt (CMD) Reference

## Key Topics
- System information commands
- Network commands
- File system navigation
- Output control
- File and directory management

---

## System Information

| Command      | Purpose                                              |
|--------------|------------------------------------------------------|
| `ver`        | Display the current Windows version                  |
| `systeminfo` | List detailed system info (OS, RAM, patches, etc.)   |
| `set`        | View environment variables including your PATH       |
| `driverquery`| List all installed drivers on the system             |
| `help`       | Get help information for a specific command          |
| `cls`        | Clear the Command Prompt screen                      |

```cmd
ver
systeminfo
set
help ipconfig
```

---

## Controlling Output — Piping with `more`

When a command produces a lot of output, pipe it through `more` to read it page by page.

```cmd
driverquery              :: all output at once (hard to read)
driverquery | more       :: output page by page
```

- Press `Space` to go to the next page
- Press `Enter` to scroll one line at a time
- Press `CTRL + C` to exit at any point

> This works with any command that produces long output — `systeminfo | more`, `netstat | more`, etc.

---

## Network Commands

### `ipconfig` — View Network Configuration

```cmd
ipconfig          :: basic IP info (IP, subnet, gateway)
ipconfig /all     :: full details including DNS servers, DHCP status, MAC address
```

### `ping` — Test Connectivity

```cmd
ping google.com
ping 10.10.10.10
```

Sends packets to the target and reports if it responds — useful for checking if a host is reachable.

### `tracert` — Trace Route

```cmd
tracert google.com
```

Traces the full network path (hops) taken to reach the target — useful for diagnosing where a connection breaks.

### `nslookup` — DNS Lookup

```cmd
nslookup example.com
```

Queries DNS to resolve a domain name to its IP address. You can also use it to query specific DNS servers:

```cmd
nslookup example.com 8.8.8.8
```

### `netstat` — Active Connections & Listening Ports

```cmd
netstat -a     :: all established connections and listening ports
netstat -b     :: show the program associated with each connection
netstat -o     :: show the Process ID (PID) associated with each connection
netstat -n     :: show addresses and ports in numerical form (faster)
netstat -abon  :: combine all of the above
```

| Flag | Purpose                                        |
|------|------------------------------------------------|
| `-a` | All connections and listening ports            |
| `-b` | Program/executable linked to each connection  |
| `-o` | PID associated with each connection            |
| `-n` | Numerical addresses (no DNS resolution)        |

> `netstat -abon` is the most useful combination — shows everything in one view.

---

## File System Navigation

### Where Am I?

```cmd
cd             :: print current drive and directory (equivalent of pwd in Linux)
```

### Listing Files & Directories

```cmd
dir            :: list files and folders in current directory
dir /a         :: include hidden and system files
dir /s         :: list files in current directory and all subdirectories
tree           :: visual tree view of all subdirectories
```

### Moving Around

```cmd
cd target_directory    :: move into a directory
cd ..                  :: go up one level
cd \                   :: go to the root of the current drive
cd C:\Users\Alice      :: navigate to a full path
```

### Creating & Deleting Directories

```cmd
mkdir folder_name      :: create a new directory
rmdir folder_name      :: delete an empty directory
rmdir /s folder_name   :: delete a directory and all its contents
```

---

## Reading Files

| Command               | Purpose                                              |
|-----------------------|------------------------------------------------------|
| `type filename.txt`   | Print file contents to the terminal (like `cat`)     |
| `more filename.txt`   | View file contents page by page (for longer files)   |

```cmd
type notes.txt
more longfile.txt
```

> `type` is the CMD equivalent of Linux's `cat`. Use `more` when the file is too long to read in one go.

---

## Quick Reference Summary

| Command            | Linux Equivalent | Purpose                                  |
|--------------------|------------------|------------------------------------------|
| `ver`              | `uname -r`       | Show OS version                          |
| `systeminfo`       | `uname -a`       | Detailed system information              |
| `cls`              | `clear`          | Clear the screen                         |
| `ipconfig`         | `ifconfig`/`ip a`| Show network interfaces                  |
| `ping`             | `ping`           | Test connectivity                        |
| `tracert`          | `traceroute`     | Trace network route to target            |
| `nslookup`         | `nslookup`/`dig` | DNS resolution                           |
| `netstat`          | `netstat`        | Active connections and open ports        |
| `cd`               | `pwd`            | Show current directory                   |
| `dir`              | `ls`             | List files                               |
| `mkdir`            | `mkdir`          | Create a directory                       |
| `rmdir`            | `rm -R`          | Delete a directory                       |
| `type`             | `cat`            | Print file contents                      |
| `more`             | `more`           | Page through long output                 |
| `command \| more`  | `command \| more`| Pipe output for paged reading            |

---

## Takeaways
- `systeminfo` and `ver` are your first commands when landing on a new Windows machine
- `ipconfig /all` gives the full network picture including DNS and DHCP — not just the IP
- `netstat -abon` is the most complete view of what's listening and connecting on the system
- `tracert` and `nslookup` are essential for diagnosing network and DNS issues
- `dir /a` reveals hidden files — always use it when enumerating a system
- Pipe any long command through `more` to read it comfortably — `CTRL+C` to exit
