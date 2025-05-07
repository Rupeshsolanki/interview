# Linux Troubleshooting Command Examples

---

## System and Kernel Logs
- `dmesg | tail`  
  *Show the last few kernel messages (e.g., device plug-in logs).*
- `journalctl -xe`  
  *View recent system errors with extra context.*
- `journalctl -u sshd`  
  *Check logs for the SSH daemon.*

---

## Process and Resource Usage
- `top`  
  *Interactive real-time view of CPU and memory usage.*
- `htop`  
  *Enhanced version of `top` with a user-friendly interface.*
- `ps aux | grep nginx`  
  *See if nginx is running and check its resource usage.*
- `strace -p 1234`  
  *Trace system calls for process with PID 1234.*
- `lsof -i :80`  
  *Show which process is using port 80.*

---

## Disk and File System
- `df -h`  
  *Show available disk space in human-readable format.*
- `du -sh /var/log`  
  *Get size of `/var/log` directory.*
- `lsblk`  
  *List block devices and partitions.*
- `mount | grep sda1`  
  *Check if `/dev/sda1` is mounted.*
- `fsck /dev/sdb1`  
  *Check and repair the filesystem on `/dev/sdb1`.*

---

## Memory
- `free -m`  
  *Display memory usage in MB.*
- `vmstat 1 5`  
  *Print system performance metrics every second for 5 intervals.*
- `cat /proc/meminfo | grep MemFree`  
  *Check free memory from kernel statistics.*

---

## Network
- `ping 8.8.8.8`  
  *Check basic internet connectivity.*
- `traceroute google.com`  
  *Trace the route to Google's servers.*
- `mtr 8.8.8.8`  
  *Live combination of ping and traceroute.*
- `ss -tuln`  
  *List open TCP/UDP ports.*
- `ip a`  
  *Display all IP addresses and network interfaces.*
- `ip r`  
  *Show the routing table.*
- `tcpdump -i eth0 port 443`  
  *Capture HTTPS traffic on interface `eth0`.*

---

## Boot and Services
- `systemctl status nginx`  
  *Check if the nginx service is active or failed.*
- `systemctl restart network`  
  *Restart network services.*
- `chkconfig --list`  
  *List services and their runlevel status (SysVinit systems).*
- `grub-mkconfig -o /boot/grub/grub.cfg`  
  *Regenerate the GRUB bootloader configuration.*

---

## Files and Permissions
- `ls -l /etc/passwd`  
  *Show file permissions and ownership.*
- `chmod 755 script.sh`  
  *Set executable permissions for a script.*
- `chown root:root /etc/myfile`  
  *Change ownership of a file to root.*
- `stat /var/log/syslog`  
  *Get detailed metadata of a file.*
- `find / -name "*.log"`  
  *Locate all `.log` files on the system.*

---

## Package Management
- `apt install htop`  
  *Install `htop` on a Debian-based system.*
- `yum update`  
  *Update all packages on a RHEL-based system.*
- `dnf remove nginx`  
  *Remove nginx using DNF on Fedora/RHEL 8+.*
- `rpm -qa | grep nginx`  
  *Check if nginx is installed using RPM.*

---

## Advanced Monitoring Tools
- `iostat -x 1`  
  *Extended I/O statistics every second.*
- `iotop`  
  *Monitor disk I/O usage per process.*
- `dstat -cnd`  
  *Display CPU, network, and disk stats.*
- `glances`  
  *Overview of system health (install required).*
- `nmon`  
  *Graphical performance monitoring.*
- `atop`  
  *Log and display process activity over time.*
- `perf top`  
  *Real-time CPU performance counter display.*

---

## Kernel and Modules
- `uname -r`  
  *Display the current kernel version.*
- `lsmod | grep snd`  
  *List sound-related kernel modules.*
- `modinfo e1000`  
  *Display information about the e1000 NIC driver module.*
- `modprobe e1000`  
  *Load the Intel e1000 driver module.*
- `rmmod lp`  
  *Unload the parallel printer kernel module.*

---
