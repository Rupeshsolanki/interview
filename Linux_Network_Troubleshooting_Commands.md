# Linux Network Troubleshooting Commands

## Connectivity
- `ping <host>`: Test network reachability
- `traceroute <host>`: Trace the route to a host
- `mtr <host>`: Real-time network diagnostics
- `telnet <host> <port>`: Test port connectivity
- `nc <host> <port>`: Netcat for port testing
- `curl <url>`: Test HTTP connectivity
- `wget <url>`: Download from a URL

## IP & Interface
- `ip a`: Show IP addresses
- `ifconfig`: Show interface configuration
- `ip r`: Show routing table
- `route`: View/modify routes
- `nmcli device show`: NetworkManager device details

## DNS
- `dig <domain>`: DNS resolution
- `nslookup <domain>`: Query DNS
- `host <domain>`: Simple DNS lookup
- `resolvectl query <domain>`: Systemd DNS query

## Port & Service Monitoring
- `ss -tuln`: Show listening ports
- `netstat -tuln`: View open ports
- `lsof -i :<port>`: List open files on port
- `fuser -n tcp <port>`: Find process using TCP port

## Packet Analysis
- `tcpdump -i <iface>`: Capture packets
- `tshark`: CLI packet analyzer
- `wireshark`: GUI packet capture tool

## Performance Testing
- `iperf3`: Network performance testing
- `vnstat`: Bandwidth monitoring
- `ethtool <iface>`: Show NIC settings

## Firewall
- `iptables -L`: List iptables rules
- `ufw status`: UFW firewall rules
- `firewall-cmd --list-all`: Firewalld settings

## Miscellaneous
- `arping <ip>`: Send ARP requests
- `systemd-resolve --status`: DNS resolver status
- `hostname -I`: Show IP addresses
- `whois <domain>`: Domain information
