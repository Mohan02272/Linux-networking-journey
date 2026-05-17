# Network Troubleshooting

## Complete Professional Notes

---

# Table of Contents

1. Introduction to Network Troubleshooting
2. Importance of Network Troubleshooting
3. Networking Troubleshooting Methodology
4. OSI Model and Troubleshooting
5. Common Network Problems
6. Physical Layer Troubleshooting
7. IP Addressing Issues
8. DNS Troubleshooting
9. Gateway and Routing Problems
10. Connectivity Troubleshooting
11. Performance Troubleshooting
12. Packet Loss and Latency
13. Network Troubleshooting Tools
14. ping Command
15. traceroute and tracepath
16. ip Command
17. ifconfig Command
18. netstat Command
19. ss Command
20. nslookup Command
21. dig Command
22. host Command
23. arp Command
24. tcpdump Command
25. Wireshark
26. curl Command
27. wget Command
28. nc (Netcat)
29. telnet Command
30. mtr Command
31. Diagnosing Slow Networks
32. Diagnosing DNS Issues
33. Diagnosing Routing Problems
34. Diagnosing Firewall Problems
35. Diagnosing Port Issues
36. Linux Log Files for Networking
37. Troubleshooting SSH Connectivity
38. Troubleshooting Web Servers
39. Troubleshooting VPN Connections
40. Enterprise Troubleshooting Practices
41. Best Practices
42. Interview Questions and Answers
43. Practical Labs
44. Conclusion

---

# 1. Introduction to Network Troubleshooting

Network troubleshooting is the process of identifying, analyzing, and resolving network-related problems.

Modern IT infrastructure depends heavily on reliable networks for:

* Internet access
* Cloud computing
* Communication
* Servers
* Databases
* Applications
* Virtualization
* DevOps environments

When network problems occur, services may become:

* Slow
* Unreachable
* Unstable
* Completely unavailable

Network troubleshooting is one of the most important skills for:

* Linux Administrators
* DevOps Engineers
* Network Engineers
* Cloud Engineers
* Cybersecurity Professionals

---

# 2. Importance of Network Troubleshooting

Proper troubleshooting helps:

* Reduce downtime
* Improve performance
* Identify security issues
* Restore connectivity
* Prevent future problems
* Maintain business operations

---

# 3. Networking Troubleshooting Methodology

Professional troubleshooting follows a structured process.

---

## Standard Methodology

1. Identify the problem
2. Gather information
3. Establish a theory
4. Test the theory
5. Implement solution
6. Verify functionality
7. Document findings

---

# 4. OSI Model and Troubleshooting

The OSI model helps isolate problems.

| Layer   | Function     |
| ------- | ------------ |
| Layer 7 | Application  |
| Layer 6 | Presentation |
| Layer 5 | Session      |
| Layer 4 | Transport    |
| Layer 3 | Network      |
| Layer 2 | Data Link    |
| Layer 1 | Physical     |

---

## Example

| Problem            | Likely Layer      |
| ------------------ | ----------------- |
| Cable disconnected | Physical          |
| Wrong IP address   | Network           |
| DNS failure        | Application       |
| Firewall block     | Transport/Network |

---

# 5. Common Network Problems

| Problem           | Description                |
| ----------------- | -------------------------- |
| No connectivity   | Cannot reach network       |
| Slow internet     | High latency or congestion |
| DNS failure       | Hostnames not resolving    |
| Packet loss       | Missing packets            |
| Routing issues    | Wrong network path         |
| Firewall blocking | Traffic denied             |
| Port issues       | Service unreachable        |
| VPN issues        | Tunnel failure             |

---

# 6. Physical Layer Troubleshooting

The Physical Layer includes:

* Cables
* Switch ports
* Network cards
* Wireless signals
* Power connections

---

## Common Physical Problems

* Loose cables
* Faulty NIC
* Broken switch port
* Weak Wi-Fi signal
* Hardware failure

---

## Checks

* Verify cable connections
* Check NIC LEDs
* Test another cable
* Verify switch status

---

# 7. IP Addressing Issues

Incorrect IP configuration is a very common problem.

---

## Common Problems

* Wrong IP address
* Wrong subnet mask
* Missing gateway
* Duplicate IP address

---

## Display IP Configuration

```bash
ip addr
```

OR

```bash
ifconfig
```

---

## Check Routing Table

```bash
ip route
```

---

# 8. DNS Troubleshooting

DNS converts domain names into IP addresses.

---

## Common DNS Problems

* Website not opening
* Slow name resolution
* Wrong DNS server
* DNS timeout

---

## Test DNS

```bash
nslookup google.com
```

OR

```bash
dig google.com
```

---

## Check DNS Configuration

```bash
cat /etc/resolv.conf
```

---

# 9. Gateway and Routing Problems

A gateway allows systems to communicate outside local networks.

---

## Check Gateway

```bash
ip route
```

---

## Example Output

```bash
default via 192.168.1.1 dev eth0
```

---

## Common Problems

* Wrong default gateway
* Missing routes
* Router failure

---

# 10. Connectivity Troubleshooting

Connectivity troubleshooting checks whether systems can communicate.

---

## Basic Troubleshooting Flow

1. Check physical connection
2. Verify IP address
3. Test localhost
4. Test local network
5. Test gateway
6. Test internet
7. Test DNS

---

# 11. Performance Troubleshooting

Performance problems affect network speed and stability.

---

## Common Causes

* High latency
* Congestion
* Packet loss
* Bandwidth saturation
* Faulty hardware
* DNS delays

---

# 12. Packet Loss and Latency

## Packet Loss

Packets fail to reach destination.

Causes:

* Congestion
* Bad cables
* Firewall filtering
* Wireless interference

---

## Latency

Delay in communication.

Measured in milliseconds.

High latency causes:

* Slow browsing
* Lag
* Poor VoIP quality

---

# 13. Network Troubleshooting Tools

Linux provides many troubleshooting tools.

| Tool       | Purpose               |
| ---------- | --------------------- |
| ping       | Connectivity testing  |
| traceroute | Route tracking        |
| ip         | Network configuration |
| ifconfig   | Legacy interface tool |
| netstat    | Network statistics    |
| ss         | Socket statistics     |
| tcpdump    | Packet capture        |
| Wireshark  | Packet analysis       |
| dig        | DNS testing           |
| curl       | HTTP testing          |
| nc         | Port testing          |

---

# 14. ping Command

Used to test connectivity.

---

## Command

```bash
ping google.com
```

---

## What ping Tests

* DNS resolution
* Reachability
* Latency
* Packet loss

---

## Example Output

```bash
64 bytes from 142.250.190.14: icmp_seq=1 ttl=118 time=20 ms
```

---

## Important Options

| Option | Meaning           |
| ------ | ----------------- |
| -c     | Number of packets |
| -i     | Interval          |
| -s     | Packet size       |

---

## Example

```bash
ping -c 4 google.com
```

---

# 15. traceroute and tracepath

Used to identify the path packets take.

---

## traceroute

```bash
traceroute google.com
```

---

## tracepath

```bash
tracepath google.com
```

---

## Purpose

* Detect routing problems
* Identify slow hops
* Locate network failures

---

# 16. ip Command

Modern Linux networking utility.

---

## Show IP Addresses

```bash
ip addr
```

---

## Show Routes

```bash
ip route
```

---

## Show Interfaces

```bash
ip link
```

---

## Bring Interface Up

```bash
sudo ip link set eth0 up
```

---

## Bring Interface Down

```bash
sudo ip link set eth0 down
```

---

# 17. ifconfig Command

Legacy network configuration tool.

---

## Display Interfaces

```bash
ifconfig
```

---

## Enable Interface

```bash
sudo ifconfig eth0 up
```

---

## Disable Interface

```bash
sudo ifconfig eth0 down
```

---

# 18. netstat Command

Displays network statistics.

---

## Show Listening Ports

```bash
netstat -tulnp
```

---

## Breakdown

| Option | Meaning        |
| ------ | -------------- |
| -t     | TCP            |
| -u     | UDP            |
| -l     | Listening      |
| -n     | Numeric output |
| -p     | Process info   |

---

# 19. ss Command

Modern replacement for netstat.

---

## Show Listening Ports

```bash
ss -tulnp
```

---

## Advantages

* Faster
* More detailed
* Modern utility

---

# 20. nslookup Command

DNS troubleshooting tool.

---

## Command

```bash
nslookup google.com
```

---

## Query Specific DNS Server

```bash
nslookup google.com 8.8.8.8
```

---

# 21. dig Command

Advanced DNS query tool.

---

## Command

```bash
dig google.com
```

---

## Short Output

```bash
dig +short google.com
```

---

# 22. host Command

Simple DNS lookup utility.

---

## Command

```bash
host google.com
```

---

# 23. arp Command

Displays ARP cache.

---

## Command

```bash
arp -a
```

---

## Purpose

Maps:

* IP addresses
* MAC addresses

---

# 24. tcpdump Command

Command-line packet capture tool.

---

## Capture Packets

```bash
sudo tcpdump -i eth0
```

---

## Capture Specific Port

```bash
sudo tcpdump port 80
```

---

## Save Capture

```bash
sudo tcpdump -w capture.pcap
```

---

# 25. Wireshark

Graphical packet analyzer.

---

## Features

* Deep packet inspection
* Protocol analysis
* Traffic filtering
* Security investigation

---

## Common Usage

* Troubleshooting
* Security analysis
* Protocol learning

---

# 26. curl Command

Tests HTTP and HTTPS connectivity.

---

## Basic Request

```bash
curl https://google.com
```

---

## Show Headers

```bash
curl -I https://google.com
```

---

## Test APIs

```bash
curl https://api.example.com
```

---

# 27. wget Command

Downloads files over HTTP/HTTPS.

---

## Download File

```bash
wget https://example.com/file.zip
```

---

# 28. nc (Netcat)

Network testing utility.

---

## Test Port Connectivity

```bash
nc -zv google.com 443
```

---

## Listen on Port

```bash
nc -l 8080
```

---

# 29. telnet Command

Tests remote port connectivity.

---

## Example

```bash
telnet google.com 80
```

---

## Purpose

Verify whether ports are open.

---

# 30. mtr Command

Combines ping and traceroute.

---

## Command

```bash
mtr google.com
```

---

## Benefits

* Real-time monitoring
* Detect packet loss
* Identify unstable routes

---

# 31. Diagnosing Slow Networks

## Common Causes

* Congestion
* DNS delays
* Packet loss
* Bandwidth saturation
* Wireless interference

---

## Troubleshooting Steps

1. Test latency using ping
2. Check routes using traceroute
3. Verify DNS speed
4. Monitor bandwidth
5. Capture packets if needed

---

# 32. Diagnosing DNS Issues

## Symptoms

* Websites not loading
* Slow browsing
* Hostnames unresolved

---

## Commands

```bash
nslookup google.com
```

```bash
dig google.com
```

---

## Check DNS Server

```bash
cat /etc/resolv.conf
```

---

# 33. Diagnosing Routing Problems

## Symptoms

* Cannot reach remote networks
* Some websites unreachable
* High latency

---

## Commands

```bash
ip route
```

```bash
traceroute google.com
```

---

# 34. Diagnosing Firewall Problems

Firewalls may block traffic.

---

## Check Firewalld

```bash
sudo firewall-cmd --list-all
```

---

## Check iptables

```bash
sudo iptables -L
```

---

## Common Symptoms

* Port unreachable
* Connection timeout
* Service inaccessible

---

# 35. Diagnosing Port Issues

## Check Listening Ports

```bash
ss -tulnp
```

---

## Test Port Access

```bash
nc -zv server 443
```

---

# 36. Linux Log Files for Networking

Important log files:

| Log File          | Purpose             |
| ----------------- | ------------------- |
| /var/log/syslog   | General system logs |
| /var/log/messages | System events       |
| /var/log/auth.log | Authentication logs |
| /var/log/secure   | Security logs       |

---

## View Logs

```bash
sudo tail -f /var/log/syslog
```

---

# 37. Troubleshooting SSH Connectivity

## Common Problems

* SSH service down
* Firewall block
* Wrong credentials
* Port closed

---

## Check SSH Service

```bash
sudo systemctl status ssh
```

---

## Test SSH Port

```bash
nc -zv server 22
```

---

# 38. Troubleshooting Web Servers

## Common Problems

* Service stopped
* Port blocked
* DNS issue
* SSL certificate problem

---

## Check Web Service

```bash
sudo systemctl status nginx
```

OR

```bash
sudo systemctl status apache2
```

---

## Test HTTP

```bash
curl -I http://server
```

---

# 39. Troubleshooting VPN Connections

## Common Problems

* Authentication failure
* DNS problems
* Firewall blocking
* Tunnel issues

---

## Check VPN Interface

```bash
ip addr
```

---

## Test VPN Connectivity

```bash
ping remote_server
```

---

# 40. Enterprise Troubleshooting Practices

Enterprise environments use:

* Monitoring systems
* Centralized logging
* Packet analysis
* SIEM tools
* Network monitoring dashboards

---

## Common Enterprise Tools

| Tool       | Purpose                   |
| ---------- | ------------------------- |
| Nagios     | Monitoring                |
| Zabbix     | Infrastructure monitoring |
| Grafana    | Visualization             |
| ELK Stack  | Log analysis              |
| Prometheus | Metrics collection        |

---

# 41. Best Practices

1. Start from physical layer
2. Follow systematic troubleshooting
3. Document changes
4. Monitor logs regularly
5. Use multiple tools together
6. Verify DNS first
7. Test firewall rules carefully
8. Backup configurations

---

# 42. Interview Questions and Answers

## What is ping used for?

Connectivity testing and latency measurement.

---

## Difference between traceroute and ping?

* ping tests reachability
* traceroute shows packet path

---

## Difference between netstat and ss?

ss is modern and faster.

---

## What causes packet loss?

* Congestion
* Hardware issues
* Firewall filtering
* Wireless interference

---

## What is DNS troubleshooting?

Diagnosing domain name resolution problems.

---

# 43. Practical Labs

## Lab 1: Connectivity Testing

Practice:

* ping
* traceroute
* mtr

---

## Lab 2: DNS Troubleshooting

Practice:

* nslookup
* dig
* host

---

## Lab 3: Packet Capture

Practice:

* tcpdump
* Wireshark

---

## Lab 4: Port Troubleshooting

Practice:

* ss
* nc
* telnet

---

## Lab 5: Service Troubleshooting

Practice:

* SSH troubleshooting
* Web server troubleshooting

---

# 44. Conclusion

Network troubleshooting is a critical skill for Linux administrators, DevOps engineers, and cybersecurity professionals.

Understanding:

* Connectivity issues
* DNS problems
* Routing failures
* Firewall problems
* Performance bottlenecks
* Packet analysis

is essential for maintaining reliable network infrastructure.

Strong troubleshooting skills help reduce downtime, improve performance, and ensure stable IT operations in enterprise environments.

Continuous practice using real Linux tools is necessary to become highly skilled in network troubleshooting.
