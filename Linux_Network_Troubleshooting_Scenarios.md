# Linux Network Troubleshooting Interview Scenarios (with Commands)

## 1. A Linux server cannot reach an external website (e.g., google.com).

**Troubleshooting Steps:**

- Check IP configuration: `ip a`
- Check default route: `ip r`
- Test DNS resolution: `dig google.com` or `nslookup google.com`
- Ping public IP to bypass DNS: `ping 8.8.8.8`
- If ping works with IP but not hostname, DNS is likely the issue.
- Check `/etc/resolv.conf` for DNS servers
- Try a traceroute: `traceroute google.com` to identify network hops

---

## 2. You suspect packet loss between two Linux machines on the same subnet.

**Troubleshooting Steps:**

- Ping test with count and timing: `ping -c 10 <peer-ip>`
- Check interface statistics: `ip -s link show <iface>`
- Use `ethtool <iface>` to check for link errors or speed/duplex mismatch
- Run `mtr <peer-ip>` to observe packet loss and latency at each hop
- Use `tcpdump -i <iface>` to capture and analyze packets

---

## 3. A web server is listening on port 80 but is inaccessible remotely.

**Troubleshooting Steps:**

- Check if the service is running: `systemctl status nginx` or `ps aux | grep nginx`
- Verify port is listening: `ss -tuln | grep :80`
- Confirm firewall rules: `iptables -L` or `ufw status`
- Check if interface has the expected IP: `ip a`
- Try connecting from another host using `curl <ip>` or `nc <ip> 80`

---

## 4. DNS resolution is slow on a Linux workstation.

**Troubleshooting Steps:**

- Test DNS resolution time: `dig example.com` and note the 'Query time'
- Try alternative DNS servers: `dig @8.8.8.8 example.com`
- Check local resolver configuration: `cat /etc/resolv.conf`
- Restart network services if needed: `systemctl restart NetworkManager`
- Check if `systemd-resolved` is interfering: `systemd-resolve --status`

---

## 5. A user reports 'connection reset by peer' when trying to SSH into a server.

**Troubleshooting Steps:**

- Verify SSH service: `systemctl status sshd`
- Check port listening: `ss -tuln | grep :22`
- Inspect SSH logs: `journalctl -u sshd` or `/var/log/auth.log`
- Ensure the firewall allows port 22: `iptables -L` or `ufw status`
- Run `tcpdump -i <iface> port 22` while the client connects to see if connection is attempted

---

## 6. Two servers on different subnets can’t communicate.

**Troubleshooting Steps:**

- Check IP and subnet mask: `ip a`
- Check routing tables: `ip r`
- Ping gateway from each server: `ping <gateway-ip>`
- Trace path: `traceroute <destination-ip>`
- Check if ICMP is allowed on both firewalls: `iptables -L`

---

## 7. Server cannot resolve internal domain names.

**Troubleshooting Steps:**

- Test with `dig internal.domain.local`
- Check DNS servers: `cat /etc/resolv.conf`
- Try alternative DNS: `dig @<internal-dns-ip> internal.domain.local`
- Ensure DNS port is open: `ss -tuln | grep :53`
- Use `tcpdump -i <iface> port 53` to see if DNS queries are being sent

---

## 8. Network interface shows high error or dropped packets.

**Troubleshooting Steps:**

- Show interface stats: `ip -s link show <iface>`
- Inspect with `ethtool <iface>` for errors or negotiation issues
- Check duplex/speed mismatch: `ethtool <iface>`
- Replace cable or change port if physical issue suspected
- Monitor over time with `vnstat` or `sar`

---

## 9. Application is listening on port, but unreachable from other hosts.

**Troubleshooting Steps:**

- Check `ss -tuln | grep <port>` to confirm binding
- Verify binding to 0.0.0.0 and not just 127.0.0.1
- Check firewall rules: `iptables -L` or `nft list ruleset`
- Try `curl` or `telnet` from another host to test
- Capture with `tcpdump -i <iface> port <port>` to see if packets arrive

---

## 10. DHCP client fails to get IP address.

**Troubleshooting Steps:**

- Restart network interface: `ip link set <iface> down && ip link set <iface> up`
- Check DHCP client logs: `journalctl -u NetworkManager` or `/var/log/syslog`
- Use `tcpdump -i <iface> port 67 or port 68` to see DHCP discover/request
- Try static IP assignment and test connectivity
- Ensure DHCP server is reachable and running

---

## 11. Unable to connect to a remote server using a specific port (e.g., 443).

**Troubleshooting Steps:**

- Check connectivity with `telnet <ip> 443` or `nc <ip> 443`
- Verify remote server is listening: `ss -tuln | grep :443`
- Check for firewalls or security groups blocking the port
- Use `traceroute -T -p 443 <ip>` to check TCP path
- Capture with `tcpdump -i <iface> port 443` during connection attempt

---

## 12. Linux server cannot access the internet but can ping local hosts.

**Troubleshooting Steps:**

- Check routing table: `ip route`
- Verify default gateway: `ping <gateway-ip>`
- Try `ping 8.8.8.8` and `dig google.com`
- Check `/etc/resolv.conf` and ensure gateway NATs traffic
- Use `tcpdump -i <iface>` to verify outbound traffic

---

## 13. Placeholder scenario for issue #13.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 14. Placeholder scenario for issue #14.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 15. Placeholder scenario for issue #15.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 16. Placeholder scenario for issue #16.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 17. Placeholder scenario for issue #17.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 18. Placeholder scenario for issue #18.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 19. Placeholder scenario for issue #19.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 20. Placeholder scenario for issue #20.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 21. Placeholder scenario for issue #21.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 22. Placeholder scenario for issue #22.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 23. Placeholder scenario for issue #23.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 24. Placeholder scenario for issue #24.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 25. Placeholder scenario for issue #25.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 26. Placeholder scenario for issue #26.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 27. Placeholder scenario for issue #27.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 28. Placeholder scenario for issue #28.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 29. Placeholder scenario for issue #29.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 30. Placeholder scenario for issue #30.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 31. Placeholder scenario for issue #31.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 32. Placeholder scenario for issue #32.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 33. Placeholder scenario for issue #33.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 34. Placeholder scenario for issue #34.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 35. Placeholder scenario for issue #35.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 36. Placeholder scenario for issue #36.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 37. Placeholder scenario for issue #37.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 38. Placeholder scenario for issue #38.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 39. Placeholder scenario for issue #39.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 40. Placeholder scenario for issue #40.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 41. Placeholder scenario for issue #41.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 42. Placeholder scenario for issue #42.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 43. Placeholder scenario for issue #43.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 44. Placeholder scenario for issue #44.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 45. Placeholder scenario for issue #45.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 46. Placeholder scenario for issue #46.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 47. Placeholder scenario for issue #47.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 48. Placeholder scenario for issue #48.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 49. Placeholder scenario for issue #49.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

## 50. Placeholder scenario for issue #50.

**Troubleshooting Steps:**

- Diagnose using standard commands: `ping`, `traceroute`, `ss`, `tcpdump`
- Inspect logs and interfaces
- Ensure correct routing and DNS resolution
- Check service and firewall status
- Use packet capture if needed

---

