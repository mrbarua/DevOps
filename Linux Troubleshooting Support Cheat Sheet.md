---

# 🐧 Linux Troubleshooting Support Cheat Sheet

## 🔍 System Info & Health

```bash
uname -a              # Kernel & system info
hostnamectl           # Hostname, OS version
uptime                # How long system is running + load
top / htop             # Live CPU & memory usage
free -h               # Memory usage
vmstat 1               # CPU, memory, IO stats
```

---

## 💽 Disk & Storage

```bash
df -h                  # Disk usage by filesystem
du -sh /path           # Size of a directory
lsblk                  # Block devices (disks)
mount | column -t      # Mounted filesystems
find / -type f -size +1G   # Large files
```

---

## 🧠 CPU & Memory Troubleshooting

```bash
top                    # Check high CPU processes
ps aux --sort=-%mem    # Top memory users
ps aux --sort=-%cpu    # Top CPU users
kill -9 PID            # Kill stuck process
```

---

## 🌐 Network Troubleshooting

```bash
ip a                   # Network interfaces
ping google.com        # Connectivity test
traceroute google.com  # Trace network path
ss -tulnp              # Listening ports & services
netstat -rn            # Routes (older systems)
curl -I https://site   # Test web response
```

---

## 👤 Users & Permissions

```bash
whoami                 # Current user
id                     # User/group info
who                    # Logged-in users
last                   # Login history
chmod 755 file         # Change permissions
chown user:group file  # Change ownership
```

---

## 📁 File & Search

```bash
ls -lah                # List files (detailed)
cp -r src dst          # Copy
mv src dst             # Move/Rename
rm -rf dir             # Delete (⚠ careful)
find /path -name file  # Find files
grep -R "text" /path   # Search text
```

---

## 🧾 Logs & Debugging

```bash
journalctl -xe         # System errors
tail -f /var/log/syslog
dmesg | tail           # Kernel messages
```

---

## ⚙️ Services & Processes

```bash
systemctl status svc
systemctl restart svc
systemctl enable svc
```

---

## 📦 Package Management

### Debian / Ubuntu

```bash
apt update
apt upgrade
apt install pkg
apt remove pkg
```

### RHEL / CentOS / Fedora

```bash
yum install pkg
dnf update
```

---

## 🚨 Common Troubleshooting Checks

```bash
df -h                  # Disk full?
free -h                # Out of memory?
top                    # High CPU?
systemctl status       # Service down?
ping / curl            # Network working?
journalctl -xe         # Errors?
```

---

# 🐧 Linux Troubleshooting Support Cheat Sheet (with Explanations)

---

## 🔍 System Info & Health

### `uname -a`

Shows kernel version and system architecture.

```bash
uname -a
```

### `hostnamectl`

Displays hostname and OS details.

```bash
hostnamectl
```

### `uptime`

Shows how long the system has been running and load averages.

```bash
uptime
```

### `top / htop`

Live view of running processes and resource usage.

```bash
top
htop
```

👉 Look for processes consuming high CPU or memory.

### `free -h`

Shows memory usage in a human-readable format.

```bash
free -h
```

### `vmstat 1`

Displays CPU, memory, and IO stats every second.

```bash
vmstat 1
```

👉 Useful for spotting CPU waits and memory pressure.

---

## 💽 Disk & Storage

### `df -h`

Shows disk usage per filesystem.

```bash
df -h
```

### `du -sh /path`

Displays total size of a directory.

```bash
du -sh /var/log
```

### `lsblk`

Lists block devices and partitions.

```bash
lsblk
```

### `mount | column -t`

Shows mounted filesystems in readable columns.

```bash
mount | column -t
```

### `find / -type f -size +1G`

Finds files larger than 1GB.

```bash
find / -type f -size +1G 2>/dev/null
```

---

## 🧠 CPU & Memory Troubleshooting

### `top`

Identifies high CPU or memory processes.

```bash
top
```

### `ps aux --sort=-%mem`

Lists processes using the most memory.

```bash
ps aux --sort=-%mem | head
```

### `ps aux --sort=-%cpu`

Lists processes using the most CPU.

```bash
ps aux --sort=-%cpu | head
```

### `kill -9 PID`

Forcefully stops a stuck process.

```bash
kill -9 1234
```

⚠ Use only if normal `kill PID` does not work.

---

## 🌐 Network Troubleshooting

### `ip a`

Shows network interfaces and IP addresses.

```bash
ip a
```

### `ping`

Tests basic connectivity.

```bash
ping google.com
```

### `traceroute`

Shows the network path to a host.

```bash
traceroute google.com
```

### `ss -tulnp`

Lists listening ports and services.

```bash
ss -tulnp
```

### `netstat -rn`

Displays routing table (legacy systems).

```bash
netstat -rn
```

### `curl -I`

Checks HTTP response headers.

```bash
curl -I https://example.com
```

---

## 👤 Users & Permissions

### `whoami`

Shows current user.

```bash
whoami
```

### `id`

Displays user and group IDs.

```bash
id
```

### `who`

Lists logged-in users.

```bash
who
```

### `last`

Shows login history.

```bash
last
```

### `chmod`

Changes file permissions.

```bash
chmod 755 script.sh
```

👉 Owner can read/write/execute; others can read/execute.

### `chown`

Changes file ownership.

```bash
chown user:group file.txt
```

---

## 📁 File & Search

### `ls -lah`

Lists files with permissions and sizes.

```bash
ls -lah
```

### `cp -r`

Copies files or directories.

```bash
cp -r /src /backup
```

### `mv`

Moves or renames files.

```bash
mv old.txt new.txt
```

### `rm -rf`

Deletes files/directories recursively.

```bash
rm -rf /tmp/test
```

⚠ **Dangerous – double-check paths!**

### `find`

Searches for files.

```bash
find /etc -name "*.conf"
```

### `grep -R`

Searches text inside files.

```bash
grep -R "error" /var/log
```

---

## 🧾 Logs & Debugging

### `journalctl -xe`

Shows recent system errors.

```bash
journalctl -xe
```

### `tail -f`

Watches a log file in real time.

```bash
tail -f /var/log/syslog
```

### `dmesg | tail`

Displays recent kernel messages.

```bash
dmesg | tail
```

---

## ⚙️ Services & Processes

### `systemctl status`

Checks service status.

```bash
systemctl status nginx
```

### `systemctl restart`

Restarts a service.

```bash
systemctl restart nginx
```

### `systemctl enable`

Starts a service at boot.

```bash
systemctl enable nginx
```

---

## 📦 Package Management

### Debian / Ubuntu

```bash
apt update            # Refresh package list
apt upgrade           # Upgrade installed packages
apt install nginx     # Install package
apt remove nginx      # Remove package
```

### RHEL / CentOS / Fedora

```bash
yum install nginx
dnf update
```

---

## 🚨 Common Troubleshooting Flow

```bash
df -h                 # Disk full?
free -h               # Memory issue?
top                   # High CPU?
systemctl status svc  # Service down?
ping / curl           # Network issue?
journalctl -xe        # Errors?
```

---

