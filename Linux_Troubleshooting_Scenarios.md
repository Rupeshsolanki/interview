# 50 Linux Troubleshooting Scenarios with Answers

---

...(existing content remains unchanged)...

### Scenario 31

**Question:** A binary crashes with segmentation fault. How do you investigate?
**Answer:**
Use:

```bash
gdb /path/to/binary core
```

---

### Scenario 32

**Question:** A cron job is not running as expected. How do you debug it?
**Answer:**
Check logs:

```bash
tail -f /var/log/cron
crontab -l -u <user>
```

---

### Scenario 33

**Question:** System time is drifting. How to sync it?
**Answer:**
Use:

```bash
ntpdate <ntp-server>
timedatectl set-ntp true
```

---

### Scenario 34

**Question:** How to check for zombie processes?
**Answer:**
Run:

```bash
ps aux | grep 'Z'
```

---

### Scenario 35

**Question:** How to find which services failed during last boot?
**Answer:**
Use:

```bash
systemctl --failed
journalctl -b -1
```

---

### Scenario 36

**Question:** User can ping IP but not hostname. What do you check?
**Answer:**
Check DNS resolution:

```bash
dig <hostname>
cat /etc/resolv.conf
```

---

### Scenario 37

**Question:** How to list all open ports?
**Answer:**
Use:

```bash
ss -tuln
netstat -tulnp
```

---

### Scenario 38

**Question:** A user is locked out of SSH after multiple failed attempts. What do you check?
**Answer:**
Use:

```bash
faillock --user <username>
```

---

### Scenario 39

**Question:** CPU soft lockup observed in logs. What do you do?
**Answer:**
Check logs:

```bash
dmesg | grep -i "soft lockup"
journalctl -k
```

---

### Scenario 40

**Question:** NIC is flapping. How to debug?
**Answer:**
Check logs:

```bash
etstat -i
dmesg | grep -i eth0
```

---

### Scenario 41

**Question:** Kernel panic occurred. How to analyze?
**Answer:**
Use:

```bash
journalctl -k -b -1
```

---

### Scenario 42

**Question:** How to find which file descriptors are open by a process?
**Answer:**
Run:

```bash
ls -l /proc/<pid>/fd
```

---

### Scenario 43

**Question:** A mounted NFS share becomes unresponsive. What do you check?
**Answer:**
Use:

```bash
showmount -e <nfs-server>
mount | grep nfs
```

---

### Scenario 44

**Question:** A process is running but consuming no CPU. What do you check?
**Answer:**
Use:

```bash
strace -p <pid>
```

---

### Scenario 45

**Question:** High memory usage but no obvious process. What to check?
**Answer:**
Use:

```bash
top
cat /proc/meminfo
```

---

### Scenario 46

**Question:** How to test if a specific port is reachable on a remote server?
**Answer:**
Use:

```bash
nc -zv <host> <port>
telnet <host> <port>
```

---

### Scenario 47

**Question:** A user gets "Too many open files" error. How to resolve?
**Answer:**
Check and increase limits:

```bash
ulimit -n
lsof | wc -l
```

---

### Scenario 48

**Question:** A disk shows I/O errors. What next?
**Answer:**
Use:

```bash
dmesg | grep -i error
smartctl -a /dev/sdX
```

---

### Scenario 49

**Question:** A file was accidentally deleted but process is still using it. How to recover?
**Answer:**
Use:

```bash
ls -l /proc/<pid>/fd | grep deleted
```

---

### Scenario 50

**Question:** A background job is hung. How to debug it?
**Answer:**
Use:

```bash
ps aux | grep <job>
strace -p <pid>
```

---

