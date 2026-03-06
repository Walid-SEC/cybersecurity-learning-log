# Linux Fundamentals Pt.2

## Key Topics
- Flags and man pages
- File and directory management
- File permissions (symbolic & numeric)
- Switching users with `su`
- Important Linux root directories

---

## Flags & Man Pages
- Flags like `-a`, `-h`, `-l` modify how a command behaves
- Use `man <command>` to read the full manual for any command
- Example: `man ls` shows all available flags for `ls`

---

## File & Directory Commands

| Command | Full Name       | Purpose                        |
|---------|-----------------|--------------------------------|
| `touch` | touch           | Create a file                  |
| `mkdir` | make directory  | Create a folder                |
| `cp`    | copy            | Copy a file or folder          |
| `mv`    | move            | Move or rename a file/folder   |
| `rm`    | remove          | Remove a file or folder        |
| `file`  | file            | Determine the type of a file   |

### Quick Examples
```bash
rm note                  # delete a file
rm -R mydirectory        # delete a directory recursively
cp note note2            # copy file
mv note2 note3           # rename/move file
file note                # check file type → note: ASCII text
ls -lh                   # list files with permissions in human-readable format
```

---

## File Permissions

Permissions are shown in symbolic format: `rwxrwxrwx`

| Section  | Applies To | Example |
|----------|------------|---------|
| First 3  | Owner      | `rwx`   |
| Next 3   | Group      | `rwx`   |
| Last 3   | Others     | `rwx`   |

### Permission Values
| Permission    | Value |
|---------------|-------|
| Read (`r`)    | 4     |
| Write (`w`)   | 2     |
| Execute (`x`) | 1     |

Add the values together per group to get the numeric representation.

### Common Permission Examples
| Symbolic    | Numeric | Meaning                                      |
|-------------|---------|----------------------------------------------|
| `rwxrwxrwx` | 777     | Everyone has full access                     |
| `rwxr-xr-x` | 755     | Owner full, others can read & execute        |
| `rw-r--r--` | 644     | Owner read/write, others read only           |
| `rwx------` | 700     | Only owner has any access                    |

### Changing Permissions with chmod
```bash
chmod 755 file.sh        # owner: full | group: r+x | others: r+x
chmod 750 secret.txt     # owner: full | group: r+x | others: none
```

---

## Switching Users

```bash
su user2          # switch to user2 (stays in current directory)
su -l user2       # switch to user2 and load their full environment/home dir
```

---

## Important Root Directories

| Directory | Purpose |
|-----------|---------|
| `/etc`    | System configuration files — critical for the OS |
| `/var`    | Data written by running services and applications |
| `/tmp`    | Temporary storage, wiped on reboot — any user can write here |

### `/tmp` in Pentesting
- Writable by all users by default
- Great place to store tools or scripts when you've accessed a machine
- Data doesn't persist after reboot, which can be useful for staying stealthy

---

## Takeaways
- Flags extend what commands can do — always check `man` pages
- File permissions control security at a granular level — know your numerics
- `chmod` is your go-to for setting permissions
- `/etc`, `/var`, and `/tmp` are key directories to understand for both admin and pentesting work
